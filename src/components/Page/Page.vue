<template>
  <div class="pt-10">
    <template v-if="allPagesLoaded">
      <h1 class="text-3xl mb-5">{{ pageContent.title.rendered }}</h1>
      <div class="page-content" v-html="pageContent.content.rendered"></div>
    </template>
    <Loader v-else />
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import Loader from '../partials/Loader.vue'

export default {
  computed: {
    ...mapGetters({
      page: 'page',
      allPagesLoaded: 'allPagesLoaded'
    }),

    pageContent () {
      return this.page(this.$route.params.pageSlug)
    }
  },

  components: {
    Loader
  }
}
</script>

<style scoped>
/* .page-content {
  & >>> p {
    margin-bottom: 1rem;
  }
} */
</style>
