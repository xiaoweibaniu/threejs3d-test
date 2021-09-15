<template>
  <div class="home-page">
    <canvas id="three" class="home-three"></canvas>
  </div>
</template>

<script>
import * as THREE from "three";

export default {
  components: {},
  props: {},
  data() {
    return {
      scene: null,
      canvas: null,
      renderer: null,
      camera: null
    };
  },
  computed: {},
  watch: {},
  created() {},
  mounted() {
    this.scene = new THREE.Scene();
    this.scene.background = new THREE.Color("#eeeeee");

    this.canvas = document.getElementById("three");
    this.renderer = new THREE.WebGLRenderer({
      canvas: this.canvas,
      antialias: true
    });
    this.camera = new THREE.PerspectiveCamera(
      50,
      window.innerWidth / window.innerHeight,
      0.1,
      1000
    );
    this.camera.position.z = 10;
  },
  methods: {
    animate() {
      this.renderer.render(this.scene, this.camera);
      requestAnimationFrame(this.animate);
    }
  }
};
</script>
<style lang="scss" scoped>
.home-three {
  width: 100%;
  height: 100%;
  position: fixed;
  left: 0;
  top: 0;
}
</style>
