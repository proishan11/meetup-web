/*eslint-disable*/
<template>
  <v-app>

    <!--Upper Toolbar which is common in all pages-->
    <!-- dark allows to whiten text if color (pink here) is dark-->
    <v-toolbar dark class = "pink">

      <!--hidden-sm-and-up and hidden-xs-only used to show navigation drawer
        only on small devices like mobile-->
      <v-toolbar-side-icon
      @click = "sideNav=!sideNav"
      class = "hidden-sm-and-up"></v-toolbar-side-icon>

      <v-toolbar-title>DevMeetup</v-toolbar-title>
      <!-- due to spacer the meetup button will be on right in toolbar -->
      <!--v-toolbar-side-icon> @click = "sideNav=!sideNav"</v-toolbar-side-icon -->
      <v-spacer></v-spacer>
      <v-toolbar-items class = "hidden-xs-only">
        <v-btn flat v-for="item in menuItems" :key="item.title">
            <!-- left adds some spaces to the name -->
            <!-- list of icons can be found on vuetify website-->
            <v-icon left dark>{{ item.icon }}</v-icon>
            {{item.title}}
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>

    <!--Adds a navigation drawer-->
    <v-navigation-drawer v-model = "sideNav">
        <v-list>
            <v-list-tile v-for="item in menuItems" :key="item.title">
                <v-list-tile-action>
                    <v-icon>{{item.icon}}</v-icon>
                </v-list-tile-action>
                <v-list-title-content>{{item.title}}</v-list-title-content>
            </v-list-tile>
        </v-list>
    </v-navigation-drawer>
    <!-- for dynamic content -->
    <main>
      <router-view></router-view>
    </main>

  </v-app>
</template>

<script>

export default {
  data () {
    return {
        sideNav : false,
        //Note: Unauthenticated users should only see the Signup and Signin icon
        //menuItems will go into v-list-tile in navigation drawer
        menuItems: [
          {icon: 'supervisor_account', title: 'View Meetups'},
          {icon: 'room', title: 'Organize Meetup'},
          {icon: 'person', title: 'Profile'},
          {icon: 'face', title: 'Sign up'},
          {icon: 'lock-open', title: 'Sign in'}
        ]
    }
  },
  name: 'App'
}
</script>
