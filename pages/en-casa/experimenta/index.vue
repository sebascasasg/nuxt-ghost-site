<template>
  <main class="container">
    <h1 class="title">Experimenta</h1>
    <p class="snippet">
      Hacemos, cada uno, a nuestro ritmo. Creamos, construimos, jugamos. Solos y
      con el otro. Hacemos para nosotros, también para compartir. Para retarnos,
      conversar y conocernos. En la mínima acción de vivir nos relacionamos con
      el mundo.
    </p>
    <div class="posts-container">
      <PostCard
        v-for="post in posts"
        :key="post.id"
        :title="post.title"
        :image="post.feature_image"
        :excerpt="post.excerpt"
        :link="`/en-casa/experimenta/${post.slug}`"
      />
    </div>
  </main>
</template>

<script>
import { getPostsByTag } from "~/api/posts";
export default {
  async asyncData() {
    const posts = await getPostsByTag("experimenta");
    return { posts: posts };
  },
};
</script>

<style scoped>
.posts-container {
  margin-top: 20px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-column-gap: 10px;
  grid-row-gap: 10px;
}
.title {
  margin: 2rem 0;
  font-size: 5rem;
  font-weight: bold;
  text-align: center;
}
.snippet {
  width: 70%;
  margin: 0 auto 4rem;
}
</style>