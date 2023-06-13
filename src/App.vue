<template>
  <div class="container" id="project-list">
      <h1>{{ title }}</h1>
      <div class="row gy-4 mb-4">
          <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="(project, index) in projects" :key="project.id">
              <div class="card">
                  <div class="card-title">
                      <h3>{{ project.title }}</h3>
                  </div>
                  <!-- <div class="card-img-top">
                      <img :src="imgBasePath + product.cover_image" :alt="project.name">
                  </div> -->
                  <div class="card-body d-flex justify-content-between align-items-end">
                      <div>
                          <h6>{{ project.technology }}</h6>
                          <span>{{ project.category }}</span>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';
export default{
  'name': 'App',
  data() {
      return {
          title: 'Projects List',
          projects: [],
          apiUrl: 'http://127.0.0.1:8000/api',
      }
  },
  methods: {
      getData() {
          axios.get(`${this.apiUrl}/projects`).then((res) => {
              //console.log(res);
              this.projects = res.data.results;
              console.log(this.projects);
          })
      }
  },
  mounted() {
      this.getData();
  }
}
</script>

<style lang="scss" scoped></style>