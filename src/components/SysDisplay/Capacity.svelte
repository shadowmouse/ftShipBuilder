<script lang="ts">
    import { ship } from "../../stores/writeShip";

    interface ISystem {
        name: string;
        [k: string]: unknown;
    };

    export let prop: string;
    export let idx: number;
    export let min = 0;
    export let max = 0;

    let sys: ISystem;
    $: sys = $ship[prop][idx];
</script>

<div class="field">
    <label class="label" for="capacity">Capacity</label>
    <div class="control">
    {#if max > 0}
        <input id="capacity" class="input" type="number" placeholder="Capacity" min="{min}" max ="{max}" bind:value={sys.capacity} on:change="{() => $ship = $ship}">
    {:else}
        <input id="capacity" class="input" type="number" placeholder="Capacity" min="{min}" bind:value={sys.capacity} on:change="{() => $ship = $ship}">
    {/if}
    </div>
</div>
