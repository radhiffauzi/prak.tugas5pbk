<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-grey-8 text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          <q-avatar>
            <img src="./assets/29566214d5dc09d681489c758b938e13.jpg" />
          </q-avatar>
          Vespa Store
        </q-toolbar-title>
        <q-btn dense flat round icon="menu" @click="toggleRightDrawer" />
      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/vespas" label="Vespas" />
        <q-route-tab to="/accessories" label="Accessories" />
        <q-route-tab to="/services" label="Services" />
      </q-tabs>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <q-list>
        <q-item clickable v-ripple>
          <q-item-section>
            <q-item-label>Home</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section>
            <q-item-label>About Us</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section>
            <q-item-label>Contact</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
      <q-list>
        <q-item clickable v-ripple>
          <q-item-section>
            <q-item-label>My Cart</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section>
            <q-item-label>Wishlist</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section>
            <q-item-label>Order History</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card" flat bordered>
          <q-img src="./assets/S7.png" />

          <q-card-section>
            <div class="text-overline text-orange-9">paket restorasi vespa</div>
            <div class="text-h5 q-mt-sm q-mb-xs">10.000.000 - 13.000.000</div>
            <div class="text-caption text-grey">
              jadikan vespa kamu seperti baru kembali dengan body yang mulus dan mesin yang sehat
            </div>
          </q-card-section>

          <q-card-actions>
            <q-btn flat color="primary" label="beli sekarang" />
            <q-btn flat color="secondary" label="masukkan ke keranjang" />

            <q-space />

            <q-btn
              color="grey"
              round
              flat
              dense
              :icon="expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
              @click="expanded = !expanded"
            />
          </q-card-actions>

          <q-slide-transition>
            <div v-show="expanded">
              <q-separator />
              <q-card-section class="text-subtitle2">
                {{ lorem }}
              </q-card-section>
            </div>
          </q-slide-transition>
        </q-card>
      </div>

      <div class="q-pa-md">
        <q-carousel arrows animated v-model="slide" height="400px">
          <q-carousel-slide name="first" img-src="./assets/40479895654_262d668ee1_b.jpg">
            <div class="absolute-bottom custom-caption">
              <div class="text-h2">Sparepart Vespa</div>
              <div class="text-subtitle1">Berbagai suku cadang vespa anda</div>
            </div>
          </q-carousel-slide>
          <q-carousel-slide name="second" img-src="./assets/de152522-3a73-48cf-849c-2cd7915b1faa.jpg">
            <div class="absolute-bottom custom-caption">
              <div class="text-h2">restorasi body</div>
              <div class="text-subtitle1">restorasi dan modifikasi</div>
            </div>
          </q-carousel-slide>
          <q-carousel-slide name="third" img-src="./assets/d32255abb39ffc5ed8ff2c42f2fcfbba.jpg">
            <div class="absolute-bottom custom-caption">
              <div class="text-h2">tune up</div>
              <div class="text-subtitle1">menambah peforma vespa</div>
            </div>
          </q-carousel-slide>
        </q-carousel>
      </div>
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="./assets/29566214d5dc09d681489c758b938e13.jpg" />
          </q-avatar>
          <div>Vespa Store</div>
        </q-toolbar-title>
        <q-btn flat icon="facebook" />
        <q-btn flat icon="twitter" />
        <q-btn flat icon="instagram" />
      </q-toolbar>
      <div class="text-center q-mt-sm">
        © 2024 Vespa Store. All rights reserved.
      </div>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue';
import {
  QLayout,
  QHeader,
  QToolbar,
  QBtn,
  QToolbarTitle,
  QAvatar,
  QTabs,
  QRouteTab,
  QDrawer,
  QList,
  QItem,
  QItemSection,
  QItemLabel,
  QPageContainer,
  QFooter,
  QCarousel,
  QCarouselSlide,
  QCard,
  QCardSection,
  QCardActions,
  QSpace,
  QSeparator,
  QSlideTransition,
  QImg
} from 'quasar';

export default {
  components: {
    QLayout,
    QHeader,
    QToolbar,
    QBtn,
    QToolbarTitle,
    QAvatar,
    QTabs,
    QRouteTab,
    QDrawer,
    QList,
    QItem,
    QItemSection,
    QItemLabel,
    QPageContainer,
    QFooter,
    QCarousel,
    QCarouselSlide
  },
  setup() {
    const leftDrawerOpen = ref(false);
    const rightDrawerOpen = ref(false);
    const slide = ref('first');

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    };

    const toggleRightDrawer = () => {
      rightDrawerOpen.value = !rightDrawerOpen.value;
    };

    return {
      leftDrawerOpen,
      rightDrawerOpen,
      slide,
      toggleLeftDrawer,
      toggleRightDrawer
    };
  }
};
</script>

<style lang="sass" scoped>
.custom-caption
  text-align: center
  padding: 12px
  color: white
  background-color: rgba(0, 0, 0, .3)

.q-footer
  display: flex
  flex-direction: column
  justify-content: center
  align-items: center

.q-footer .q-toolbar
  width: 100%
  justify-content: space-between
</style>
