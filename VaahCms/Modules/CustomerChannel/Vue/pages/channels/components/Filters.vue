<script setup>

import {useChannelStore} from '../../../stores/store-channels'
import VhFieldVertical from './../../../vaahvue/vue-three/primeflex/VhFieldVertical.vue'

const store = useChannelStore();

</script>

<template>
    <div>

        <Sidebar v-model:visible="store.show_filters"
                 position="right">
            <VhFieldVertical>
                <template #label>
                    <b>Sort By:</b>
                </template>
                <MultiSelect placeholder="Select Customer"
                             :options="store.assets.customers.data"
                             optionLabel="name"
                             option-value="slug"
                             v-model="store.query.filter.customer"
                />
            </VhFieldVertical>

            <VhFieldVertical>
                <template #label>
                    <b>Sort By:</b>
                </template>

                <div class="field-radiobutton">
                    <RadioButton name="sort-none"
                                 inputId="sort-none"
                                 data-testid="channels-filters-sort-none"
                                 value=""
                                 v-model="store.query.filter.sort"/>
                    <label for="sort-none" class="cursor-pointer">None</label>
                </div>
                <div class="field-radiobutton">
                    <RadioButton name="sort-ascending"
                                 inputId="sort-ascending"
                                 data-testid="channels-filters-sort-ascending"
                                 value="updated_at"
                                 v-model="store.query.filter.sort"/>
                    <label for="sort-ascending" class="cursor-pointer">Updated (Ascending)</label>
                </div>
                <div class="field-radiobutton">
                    <RadioButton name="sort-descending"
                                 inputId="sort-descending"
                                 data-testid="channels-filters-sort-descending"
                                 value="updated_at:desc"
                                 v-model="store.query.filter.sort"/>
                    <label for="sort-descending" class="cursor-pointer">Updated (Descending)</label>
                </div>

            </VhFieldVertical>

            <Divider/>

            <VhFieldVertical>
                <template #label>
                    <b>Is Active:</b>
                </template>

                <div class="field-radiobutton">
                    <RadioButton name="active-all"
                                 inputId="active-all"
                                 value="null"
                                 data-testid="channels-filters-active-all"
                                 v-model="store.query.filter.is_active"/>
                    <label for="active-all" class="cursor-pointer">All</label>
                </div>
                <div class="field-radiobutton">
                    <RadioButton name="active-true"
                                 inputId="active-true"
                                 data-testid="channels-filters-active-true"
                                 value="true"
                                 v-model="store.query.filter.is_active"/>
                    <label for="active-true" class="cursor-pointer">Only Active</label>
                </div>
                <div class="field-radiobutton">
                    <RadioButton name="active-false"
                                 inputId="active-false"
                                 data-testid="channels-filters-active-false"
                                 value="false"
                                 v-model="store.query.filter.is_active"/>
                    <label for="active-false" class="cursor-pointer">Only Inactive</label>
                </div>

            </VhFieldVertical>

            <VhFieldVertical>
                <template #label>
                    <b>Trashed:</b>
                </template>

                <div class="field-radiobutton">
                    <RadioButton name="trashed-exclude"
                                 inputId="trashed-exclude"
                                 data-testid="channels-filters-trashed-exclude"
                                 value=""
                                 v-model="store.query.filter.trashed"/>
                    <label for="trashed-exclude" class="cursor-pointer">Exclude Trashed</label>
                </div>
                <div class="field-radiobutton">
                    <RadioButton name="trashed-include"
                                 inputId="trashed-include"
                                 data-testid="channels-filters-trashed-include"
                                 value="include"
                                 v-model="store.query.filter.trashed"/>
                    <label for="trashed-include" class="cursor-pointer">Include Trashed</label>
                </div>
                <div class="field-radiobutton">
                    <RadioButton name="trashed-only"
                                 inputId="trashed-only"
                                 data-testid="channels-filters-trashed-only"
                                 value="only"
                                 v-model="store.query.filter.trashed"/>
                    <label for="trashed-only" class="cursor-pointer">Only Trashed</label>
                </div>

            </VhFieldVertical>


        </Sidebar>

    </div>
</template>
