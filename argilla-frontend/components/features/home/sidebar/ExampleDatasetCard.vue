<template>
  <BaseButton
    class="example-dataset"
    @click="$emit('on-import-dataset', dataset.repoId)"
  >
    <div class="example-dataset__content">
      <p class="example-dataset__title">{{ dataset.repoId }}</p>
      <div class="example-dataset__tags">
        <DatasetBadge
          :text="dataset.task"
          :icon="dataset.icon"
          :color="dataset.color"
        />
        <DatasetBadge v-for="tag in dataset.tags" :text="tag" :key="tag" />
      </div>
      <p class="example-dataset__rows">
        <svgicon name="rows" height="10" />{{ dataset.rows }} rows
      </p>
    </div>
  </BaseButton>
</template>

<script>
import "assets/icons/rows";
export default {
  props: {
    dataset: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.example-dataset {
  &.button {
    width: 100%;
    max-width: 75%;
    padding: $base-space * 2;
    border: 1px solid var(--bg-opacity-6);
    border-radius: $border-radius-m;
    background: var(--bg-accent-grey-2);
    color: var(--fg-primary);
    text-align: left;
    @include media("<desktop") {
      max-width: 100%;
    }
    &:hover {
      background: var(--bg-accent-grey-3);
      border: 1px solid var(--bg-opacity-10);
    }
  }
  &__content {
    display: flex;
    flex-direction: column;
    gap: $base-space * 2;
  }
  &__title {
    margin: 0;
    color: var(--fg-primary);
    white-space: pre-line;
    @include line-height(18px);
  }
  &__tags {
    display: flex;
    gap: $base-space;
    flex-wrap: wrap;
  }
  &__rows {
    display: flex;
    align-items: center;
    gap: calc($base-space / 2);
    margin: 0;
    color: var(--fg-tertiary);
    @include font-size(12px);
  }
}
</style>
