<script>
  import { fade } from "svelte/transition";

  export let size;

  let hasChild = false;
</script>

<style>
  [container] {
    display: flex;
    flex-flow: row wrap;

    justify-content: space-evenly;
    align-content: space-evenly;
    align-items: center;
  }
  .round {
    height: 100%;
    width: 100%;
    border-radius: 100%;
    background-color: black;
  }
</style>

<div in:fade out:fade container style="width: {size}%; height: {size}%;">
  {#if !hasChild}
    <div on:mouseenter|preventDefault={() => (hasChild = true)} class="round" />
  {:else}
    {#each Array(4) as _}
      <svelte:self size={50} />
    {/each}
  {/if}
</div>
