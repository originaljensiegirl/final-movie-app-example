<template>
  <v-card class="fill-height">
    <v-img :src="movie.img" />
    <v-card-title>
      <h2 class="caption text-truncate">{{movie.title}}</h2>
    </v-card-title>
    <v-card-text pa-3>
      <v-rating small v-model="editRating"></v-rating>
      <span class="caption">{{`${movie.rating}/5 `}}</span>
    </v-card-text>
  </v-card>
</template>

<style scoped>
</style>

<script>
export default {
  props: {
    movie: Object
  },
  data: () => ({
    editRating: 0
  }),
  created() {
    this.editRating = this.$props.movie.rating;
  },
  watch: {
    editRating: function() {
      this.$emit("change-rating", this.editRating);
    }
  },
};
</script>
