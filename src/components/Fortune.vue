<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="6"
        ><v-btn block color="primary" @click="drawFortune"
          >Draw Fortune</v-btn
        ></v-col
      >
    </v-row>
    <v-row justify="center">
      <v-col cols="6">
        <v-card class="pa-4">
          <v-card-title class="text-h2 justify-center">{{
            fortune
          }}</v-card-title>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { API, graphqlOperation } from 'aws-amplify'
import { drawFortune } from '../graphql/queries'

export default {
  data: function() {
    return {
      fortune: '',
    }
  },
  methods: {
    async drawFortune() {
      const result = await API.graphql(graphqlOperation(drawFortune))
      this.fortune = result.data.drawFortune
    },
  },
}
</script>

<style></style>
