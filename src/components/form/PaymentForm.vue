<template>
  <CardPaymentForm
    v-if="paymentMethod.code === 'card'"
    :translate="translate"
    :paymentMethod="paymentMethod"
    @pay="$emit('pay', $event)"
  />
  <BasePaymentForm
    v-else
    :translate="translate"
    :paymentMethod="paymentMethod"
    @pay="$emit('pay', $event)"
  />
</template>

<script setup lang="ts">
import type { Translate } from "orchestrator-pp-core";
import type { PaymentMethod } from "orchestrator-pp-payment-method";
import CardPaymentForm from './CardPaymentForm.vue';
import BasePaymentForm from './BasePaymentForm.vue';

defineProps<{
  paymentMethod: PaymentMethod,
  translate: Translate
}>();

defineEmits<{
  (event: 'pay', data: Record<string, unknown>): void;
}>();
</script>
