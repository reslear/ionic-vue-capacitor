<template>
  <ion-page ref="page">
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button></ion-back-button>
        </ion-buttons>
        <ion-title>Ionic Vite - About</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>About</h1>
      <ion-modal
        ref="modal"
        trigger="open-modal"
        :presenting-element="presentingElement"
      >
        <ion-header>
          <ion-toolbar>
            <ion-title>Modal</ion-title>
            <ion-buttons slot="end">
              <ion-button @click="dismiss()">Close</ion-button>
            </ion-buttons>
          </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding"> About Modal </ion-content>
      </ion-modal>
      <ion-button id="open-modal" expand="block">Open</ion-button>
    </ion-content>
  </ion-page>
</template>

<script lang="ts" setup>
import { computed, onBeforeUnmount, ref } from 'vue'
import {
  IonContent,
  IonButton,
  IonButtons,
  IonBackButton,
  IonPage,
  IonHeader,
  IonTitle,
  IonToolbar,
  IonModal,
} from '@ionic/vue'

const page = ref<{ $el: HTMLElement } | null>(null)
const modal = ref<{ $el: HTMLIonModalElement } | null>(null)

const presentingElement = computed(() => page.value?.$el)

function dismiss() {
  modal.value?.$el.dismiss()
}

onBeforeUnmount(() => {
  modal.value?.$el.dismiss()
})
</script>

<style></style>
