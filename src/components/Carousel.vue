<template>
  <div class="container-fluid min-vh-100 p-2" id="nowShowing">
    <div class="text-center">
      <span class="section-header">NOW SHOWING</span>
    </div>
    <div
      id="carouselIndicators"
      class="carousel slide mt-3"
      data-bs-ride="true"
    >
      <div class="carousel-indicators d-none text-center d-lg-inline pb-0 mb-0">
        <template v-for="movie in MOVIES" :key="movie.id">
          <button
            type="button"
            data-bs-target="#carouselIndicators"
            :data-bs-slide-to="movie.id"
            :class="getClass(movie.id)"
            :aria-current="movie.id === 0 ? 'true' : 'false'"
            :aria-label="'Slide' + movie.id"
          ></button>
        </template>
      </div>

      <div class="carousel-inner">
        <template v-for="movie in MOVIES" :key="movie.id">
          <div
            :class="movie.id === 0 ? 'carousel-item active' : 'carousel-item'"
          >
            <MovieCard :movie="movie" />
          </div>
        </template>
      </div>
      <button
        class="carousel-control-prev"
        type="button"
        data-bs-target="#carouselIndicators"
        data-bs-slide="prev"
      >
        <span
          class="carousel-control-prev-icon d-none d-lg-block"
          aria-hidden="true"
        ></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button
        class="carousel-control-next"
        type="button"
        data-bs-target="#carouselIndicators"
        data-bs-slide="next"
      >
        <span
          class="carousel-control-next-icon d-none d-lg-block"
          aria-hidden="true"
        ></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </div>
</template>

<script>
import MovieCard from "./MovieCard.vue";
import { MOVIES } from "../data/movies.js";
export default {
  components: {
    MovieCard,
  },
  data() {
    return {
      MOVIES: MOVIES,
    };
  },
  methods: {
    getClass(index) {
      console.log(index);
      const cls = index === 0 ? "active" : "";
      console.log(cls);
      return cls;
    },
  },
};
</script>
