<template>
  <v-app id="365daysofcode">
    <v-app-bar app clipped-left fixed>
      <v-toolbar-title>365 Days of Code</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-menu v-if="$vuetify.breakpoint.smAndDown">
        <template v-slot:activator="{ on }">
          <v-btn icon v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item to="/">
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>Index</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/about">
            <v-list-item-icon>
              <v-icon>mdi-information-outline</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>About</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-btn icon v-if="$vuetify.breakpoint.mdAndUp" to="/">
        <v-icon>mdi-home</v-icon>
      </v-btn>

      <v-btn icon v-if="$vuetify.breakpoint.mdAndUp" to="/about">
        <v-icon>mdi-information-outline</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <v-container class="fill-height" fluid>
        <v-row>
          <v-col>
            <router-view></router-view>
          </v-col>
        </v-row>
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; {{ year }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  props: {
    source: String,
    year: {
      type: Number,
      default: new Date().getFullYear()
    }
  },

  data: () => ({
    drawer: null
  }),

  created() {
    this.$vuetify.theme.dark = true;
  }
};
</script>
