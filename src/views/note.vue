<template>
  <div class="note" v-on:click="showhide">
    <titlebar v-bind:close="close" v-bind:note="note"/>
    <editor/>
    <colors/>
    <choosecolor/>
  </div>
</template>

<script>
import { remote, ipcRenderer } from "electron";
import editor from "../components/note/editor.vue";
import titlebar from "../components/note/titlebar.vue";
import colors from "../components/note/colors.vue";
import choosecolor from "../components/note/choosecolor.vue";
export default {
  components: {
    titlebar,
    editor,
    colors,
    choosecolor
  },
  methods: {
    close: function() {
      remote.getCurrentWindow().close();
    },
    note: function() {
      ipcRenderer.send("create-new-instance");
    },
    showhide: function() {
      document.addEventListener(
        "focus",
        () => {
          document.getElementById("titlebar").style.height = "32px";
          if (
            document.querySelector(".ql-snow.ql-toolbar").style.display !=
              "block"
          ) {
            document.getElementById("color").style.height = "40px";
          }
          document.getElementById("lock").style.display = "flex";
          document.getElementById("lock").style.display = "flex";
          document.getElementById("add").style.display = "flex";
          document.getElementById("more").style.display = "flex";
          document.getElementById("close").style.display = "flex";
        },
        true
      );
      document.addEventListener(
        "click",
        () => {
          document.getElementById("titlebar").style.height = "32px";
          if (
            document.querySelector(".ql-snow.ql-toolbar").style.display !=
              "block"
          ) {
            document.getElementById("color").style.height = "40px";
          }
          document.getElementById("lock").style.display = "flex";
          document.getElementById("lock").style.display = "flex";
          document.getElementById("add").style.display = "flex";
          document.getElementById("more").style.display = "flex";
          document.getElementById("close").style.display = "flex";
        },
        true
      );
      document.addEventListener(
        "blur",
        () => {
          document.getElementById("titlebar").style.height = "0";
          document.getElementById("color").style.height = "0";
          document.getElementById("lock").style.display = "none";
          document.getElementById("add").style.display = "none";
          document.getElementById("more").style.display = "none";
          document.getElementById("close").style.display = "none";
        },
        true
      );
    }
  }
};
</script>