<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
   
  
    <splitpanes :push-other-panes="false" class="default-theme" vertical style="height: 400px">
      <span>1</span>
      <splitpanes horizontal @resize="paneResize($event)">
        <span>
          <div id="flowpane" style="background-color: lightblue">
            2
          </div>
        </span>
        <span>
          <p>3</p>
          <p>divHeight: {{ divHeight }}</p>
        </span>
      </splitpanes>
    </splitpanes>
  </div>
</template>

<script>
import Splitpanes from "splitpanes";
import "splitpanes/dist/splitpanes.css";

export default {
  name: "HelloWorld",
  components: {
    Splitpanes
  },
  data () {
    return {
      divHeight: null
    }
  },
  props: {
    msg: String
  },
  methods: {
    paneResize(event) {
      // console.log("event :", event);
      let div = document.getElementById("flowpane");
      div.style.height = (400 / 100) * event[0].width + "px";
      // console.log("Calculated height :", (400 / 100) * event[0].width);

      // console.log("div.clientHeight :", div.clientHeight);

      this.divHeight = document.getElementById("flowpane").clientHeight.toString();
      // console.log("this.divHeight :", this.divHeight);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
