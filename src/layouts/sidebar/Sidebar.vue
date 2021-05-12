<template>


  <v-navigation-drawer
    v-model="Sidebar_drawer"
    :dark="SidebarColor !== 'white'"
    :color="SidebarColor"
    mobile-break-point="960"
    clipped
    :right="$vuetify.rtl"
    mini-variant-width="70"
    :expand-on-hover="expandOnHover"
    app
    id="main-sidebar"
  >


    <v-list dense nav>
      <!---USer Area -->
      <v-list-item two-line class="px-0">
        <v-list-item-avatar>
          <img src="../../assets/background/user1.jpg" />
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title>Test_user</v-list-item-title>
          <v-list-item-subtitle class="caption">Editor</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <!---USer Area -->
      <!---Sidebar Items -->
      <v-list-item
        v-for="item in items"
        :key="item.title"
        :to="item.to"
        :active-class="`success white--text`"
        link
      >
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <!---Sidebar Items -->

  <!-- accrodian menu -->

  <v-expansion-panels>
    <v-expansion-panel
      v-for="(item,i) in 2"
      :key="i"
    >
      <v-expansion-panel-header>
        Item
      </v-expansion-panel-header>
      <v-expansion-panel-content>

<!-- sub menus --> 

     <v-list-item
        v-for="item in items"
        :key="item.title"
        :to="item.to"
        :active-class="`success white--text`"
        link
      >
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

<!-- end of sub menu --> 

      </v-expansion-panel-content>
    </v-expansion-panel>
  </v-expansion-panels>
<!-- end of accordian menu -->


    </v-list>



  </v-navigation-drawer>

</template>

<script>
import { mapState } from "vuex";

export default {
  name: "Sidebar",
  props: {
    expandOnHover: {
      type: Boolean,
      default: false
    }
  },
  
  data: () => ({
    // icons http://code.meta-platform.com/assets/mdi/preview.html
    items: [
      {
        title: "Dashboard",
        icon: "mdi-view-dashboard",
        to: "/dashboard/basic-dashboard"
      },
      {
        title: "Advocate Info",
        icon: "mdi mdi-information-outline",
        to: "/pages/Advocate"
      },
      {
        title: "Setage info ",
        icon: "mdi mdi-layers",
        to: "/dashboard/basic-dashboard1"
      },
      {
        title: "Entrance exam info",
        icon: "mdi mdi-bell",
        to: "/dashboard/basic-dashboard2"
      },
      {
        title: "Certificate info ",
        icon: "mdi mdi-auto-fix",
        to: "/dashboard/basic-dashboard3"
      },
      {
        title: "Report",
        icon: "mdi mdi-pencil",
        to: "/dashboard/basic-dashboard4"
      },
      {
        title: "Settings",
        icon: "mdi-view-dashboard",
        to: "/dashboard/basic-dashboard4"
      },

      {
        title: "Profile",
        icon: "mdi-account-circle",
        to: "/pages/profile"
      },

      {
        title: "Alerts",
        icon: "mdi-alert",
        to: "/pages/alerts"
      },

      {
        title: "Icons",
        icon: "mdi mdi-account-multiple",
        to: "/pages/icons"
      },

      {
        title: "Basic Table",
        icon: "mdi-table-column-width",
        to: "/pages/tables-simple"
      },

      {
        title: "Test",
        icon: "mdi-table-column-width",
        to: "/pages/test"
      }
    ]
  }),
  computed: {
    ...mapState(["SidebarColor", "SidebarBg"]),
    Sidebar_drawer: {
      get() {
        return this.$store.state.Sidebar_drawer;
      },
      set(val) {
        this.$store.commit("SET_SIDEBAR_DRAWER", val);
      }
    }
  },
  watch: {
    "$vuetify.breakpoint.smAndDown"(val) {
      this.$emit("update:expandOnHover", !val);
    }
  },

  methods: {}
};
</script>
<style lang="scss">
#main-sidebar{
  box-shadow:1px 0 20px rgba(0,0,0,.08);
  -webkit-box-shadow:1px 0 20px rgba(0,0,0,.08);
  .v-navigation-drawer__border{
    display: none;
  }
  .v-list{
    padding: 8px 15px;
  }
  .v-list-item{
      &__icon--text,
      &__icon:first-child{
        justify-content: center;
        text-align: center;
        width: 20px;
        
      }
      
  }    
}
</style>