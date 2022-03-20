<template>
  <path
    :d="link(data)"
    :stroke-width="data.width - 1"
    :stroke="`url(#${gradientId})`"
    fill="none"
    stroke-opacity="0.8"
  />
</template>
<style>
path:hover {
  opacity: 0.5;
}
</style>

<script>
import { sankeyLinkHorizontal } from "d3-sankey";
import sankeyMixin from "@/mixins/sankey-mixin";

export default {
  name: "LinkItem",
  props: {
    data: Object,
    length: Number,
    colors: Function,
  },
  mixins: [sankeyMixin],
  computed: {
    link() {
      console.log(this.data);
      return sankeyLinkHorizontal();
    },
    gradientId() {
      // console.log(this.data.source.name);
      return this.getGradientId(this.data.source.name, this.data.target.name);
    },
  },
};
</script>