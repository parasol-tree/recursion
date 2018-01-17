<template>
  <li>
    <span @click="toggle">
      <i v-if="isFolder" class="icon" :class="[open ? 'folder-open': 'folder']"></i>
      <i v-if="!isFolder" class="icon file-text"></i>
      {{ model.menuName }}
    </span>
    <ul v-show="open" v-if="isFolder">
      <tree-menu v-for="(item, index) in model.children" :model="item" :key="index"></tree-menu>
    </ul>
  </li>
</template>

<script>
export default {
  name: 'treeMenu',
  props: ['model'],
  data () {
    return {
      open: false,
      isFolder: true
    }
  },
  computed: {
    isShowFolder: function () {
      return this.model.children && this.model.children.length
    }
  },
  methods: {
    toggle: function () {
      if (this.isShowFolder) {
        this.open = !this.open
      }
    }
  }
}
</script>

<style>
ul {
  list-style: none;
}
i.icon {
  display: inline-block;
  width: 15px;
  height: 15px;
  background-repeat: no-repeat;
  vertical-align: middle;
}
.icon.folder {
  background-color: red
  /*background-image: url(/src/assets/folder.png);*/
}
.icon.folder-open {
  background-color: red
  /*background-image: url(/src/assets/folder-open.png);*/
}
.icon.file-text {
  background-color: red
  /*background-image: url(/src/assets/file-text.png);*/
}
.tree-menu li {
  line-height: 1.5;
}
</style>
