<template>
<q-layout view="lHh Lpr lFf">
  <q-header>
    <q-toolbar>
      <q-btn flat dense round icon="menu" aria-label="Menu" @click="leftDrawerOpen = !leftDrawerOpen" />
    </q-toolbar>
    <div class="q-px-lg q-pt-xl q-mb-md">
      <div class="text-h3">Todo</div>
      <div class="text-subtitle1">{{ todaysDate }}</div>
    </div>
    <q-img src="statics/chalk.jpg" class="header-image absolute-top" />

  </q-header>

  <q-drawer v-model="leftDrawerOpen" show-if-above :width="250" :breakpoint="600">
    <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
      <q-list padding>

        <q-item to="/" exact clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="list" />
          </q-item-section>

          <q-item-section>
            Todo
          </q-item-section>
        </q-item>

        <q-item to="/help" exact clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="help" />
          </q-item-section>

          <q-item-section>
            Help
          </q-item-section>
        </q-item>

      </q-list>
    </q-scroll-area>

    <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png" style="height: 192px; filter:grayscale(100%);">
      <div class="absolute-bottom bg-transparent">
        <div class="text-weight-bold">Razvan Stoenescu</div>
        <div>@rstoenescu</div>
      </div>
    </q-img>
  </q-drawer>

  <q-page-container>
    <keep-alive>
      <router-view />
    </keep-alive>
  </q-page-container>
</q-layout>
</template>

<script>
import {
  date
} from 'quasar'

export default {
  name: 'MainLayout',

  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: [{
        title: 'Docs',
        caption: 'quasar.dev',
        icon: 'school',
        link: 'https://quasar.dev'
      },
      {
        title: 'Github',
        caption: 'github.com/quasarframework',
        icon: 'code',
        link: 'https://github.com/quasarframework'
      },
      {
        title: 'Discord Chat Channel',
        caption: 'chat.quasar.dev',
        icon: 'chat',
        link: 'https://chat.quasar.dev'
      },
      {
        title: 'Forum',
        caption: 'forum.quasar.dev',
        icon: 'record_voice_over',
        link: 'https://forum.quasar.dev'
      },
      {
        title: 'Twitter',
        caption: '@quasarframework',
        icon: 'rss_feed',
        link: 'https://twitter.quasar.dev'
      },
      {
        title: 'Facebook',
        caption: '@QuasarFramework',
        icon: 'public',
        link: 'https://facebook.quasar.dev'
      }
      ]
    }
  },
  computed: {
    todaysDate () {
      return date.formatDate(Date.now(), 'dddd D MMMM')
    }
  }
}
</script>

<style lang="scss">
.header-image {
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter: grayscale(100%);
}
</style>
