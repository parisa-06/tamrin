<template >
 <v-app id="inspire" >
    <v-system-bar 
     app
     height="40"
     color="#F5F5F5"
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
    
      <v-spacer></v-spacer>
    
      <div class="ma-12">
         <v-icon>mdi-square</v-icon>
         <v-icon>mdi-circle</v-icon>
         <v-icon>mdi-triangle</v-icon>
      </div>
      
    </v-system-bar>

    <v-app-bar app  >
       <p class="font"> صفحه اصلی | کاربری </p>

       <v-spacer></v-spacer>
    
       <template >
        <div class="ma-5 ">
         <v-menu offset-y z-index="10" internal-activator color="#E1F5FE"  >
         <template v-slot:activator="{ on, attrs }">
          <v-btn
          plain
          v-bind="attrs"
          v-on="on"
          color="#616161"
          >
           <p class="font ma-2"> علی زارعی </p>
            <v-img 
               lazy-src="https://picsum.photos/id/11/10/6"
               max-height="40"
               max-width="55"
               src="https://picsum.photos/id/11/500/300"
               class="img-circle"
               ></v-img> 
    
          </v-btn>
          </template>
        <v-list
         right
         class="font"
         >
         <v-list-item-group
            v-model="selectedItem"
            color="primary"
            right
          >
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
          >
          <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item-content>
            
          </v-list-item>
        </v-list-item-group>
      </v-list>

    </v-menu>
</div>
</template>
</v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      fixed
      temporary
      right
      class="font"
    >
     <v-sheet
        color="grey lighten-4"
        class="pa-4"
      >
        <v-avatar
          class="mb-4"
          color="grey darken-1"
          size="64"
        ></v-avatar>

        <div> byd@talash.com</div>
      </v-sheet>

      <v-divider></v-divider>


  <v-card
    class="mx-auto"
    width="300"
  >
    <v-list>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-home</v-icon>
        </v-list-item-icon>

        <v-list-item-title>خانه</v-list-item-title>
      </v-list-item>

      <v-list-group
        :value="true"
        prepend-icon="mdi-account-circle"
      >
        <template v-slot:activator>
          <v-list-item-title>مدیریت</v-list-item-title>
        </template>

        <v-list-group
          :value="true"
          no-action
          sub-group
        >
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title>کاربر</v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item
            v-for="([title, icon], i) in admins"
            :key="i"
            link
          >
              <v-list-item-icon>
              <v-icon v-text="icon"></v-icon>
            </v-list-item-icon>

            <v-list-item-title v-text="title"></v-list-item-title>

        
          </v-list-item>
        </v-list-group>

        <v-list-group
          no-action
          sub-group
        >
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title>عملیات</v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item
            v-for="([title, icon], i) in cruds"
            :key="i"
            link
          >
          <v-list-item-icon>
              <v-icon v-text="icon"></v-icon>
            </v-list-item-icon>

            <v-list-item-title v-text="title"></v-list-item-title>

            
          </v-list-item>
        </v-list-group>
      </v-list-group>
    </v-list>
  </v-card>




     
    </v-navigation-drawer>

    <v-main >
   
    </v-main>
  </v-app>
</template>


<style>

.img-circle {
    border-radius: 50%;
}
 .font{
       font-family: 'Vazir';
       font-size   : .80rem;
    }


</style>


<script>
  export default {
    data: () => ({ drawer: null ,
     
       selectedItem: 1,
    items: [
      {  icon: 'mdi-clock'  , text: 'آیتم'},
      {  icon: 'mdi-account' , text: 'آیتم' },
      {  icon: 'mdi-flag' , text: 'آیتم'},
    ],
     admins: [
        ['آیتم', 'mdi-account-multiple-outline'],
        ['آیتم', 'mdi-cog-outline'],
      ],
      cruds: [
        ['آیتم', 'mdi-plus-outline'],
        ['آیتم', 'mdi-file-outline'],
        ['آیتم', 'mdi-update'],
        ['آیتم', 'mdi-delete'],
      ],
    
    }),
  }
</script>