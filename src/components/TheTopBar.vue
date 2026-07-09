<script setup lang="ts">
defineProps<{
  menuOpen: boolean
}>()

const emit = defineEmits<{
  (event: 'toggle-menu'): void
}>()

const brandIconUrl = `${import.meta.env.BASE_URL}icons/hungry-codex-page-logo-master.svg`
</script>

<template>
  <header class="topbar border-bottom">
    <div class="container-fluid d-flex align-items-center justify-content-between gap-3 px-3 px-lg-4">
      <div class="brand-lockup d-flex align-items-center gap-2">
        <span class="brand-logo-frame" aria-hidden="true">
          <img class="brand-mark" :src="brandIconUrl" alt="" />
        </span>
        <h1 class="brand-title mb-0">
          <span>Hungry Codex</span>
        </h1>
      </div>

      <button
        class="btn btn-link icon-button d-lg-none"
        type="button"
        :aria-expanded="menuOpen"
        :aria-label="menuOpen ? 'Close categories' : 'Open categories'"
        aria-controls="mobile-category-menu"
        @click="emit('toggle-menu')"
      >
        <span class="material-icons" aria-hidden="true">{{ menuOpen ? 'close' : 'menu' }}</span>
      </button>
    </div>
  </header>
</template>

<style scoped>
.topbar {
  --topbar-height: var(--hc-topbar-content-height);
  align-items: stretch;
  background: var(--hc-topbar-safe);
  border-bottom-color: var(--hc-border) !important;
  box-shadow: 0 1px 4px var(--hc-shadow-soft);
  color: var(--hc-text);
  display: flex;
  min-height: var(--hc-topbar-total-height);
  padding-top: var(--hc-safe-area-top);
  position: sticky;
  top: 0;
  z-index: 1040;
}

.topbar > .container-fluid {
  min-height: var(--topbar-height);
  position: relative;
  z-index: 1;
}

.brand-logo-frame {
  align-items: center;
  background: var(--hc-text);
  border: 1px solid var(--hc-text);
  border-radius: 10px;
  box-shadow: 0 1px 4px var(--hc-shadow-soft);
  display: inline-flex;
  flex: 0 0 auto;
  height: 52px;
  justify-content: center;
  width: 52px;
}

.brand-mark {
  display: block;
  height: 47px;
  object-fit: contain;
  width: 47px;
}

.brand-lockup {
  min-width: 0;
}

.brand-title {
  display: inline-flex;
  min-width: 0;
}

.brand-title span {
  color: var(--hc-text);
  display: block;
  font-family: "Fraunces Variable", Georgia, serif;
  font-size: 1.5rem;
  font-optical-sizing: auto;
  font-weight: 750;
  letter-spacing: -0.035em;
  line-height: 1.15;
  padding-block: 0.08em;
  white-space: nowrap;
}

.icon-button {
  align-items: center;
  color: var(--hc-text);
  display: inline-flex;
  height: 40px;
  justify-content: center;
  margin-left: auto;
  padding: 0;
  text-decoration: none;
  width: 40px;
}

.btn .material-icons {
  font-size: 20px;
}

@media (max-width: 991.98px) {
  .brand-lockup {
    left: 50%;
    position: absolute;
    transform: translateX(-50%);
  }
}

@media (max-width: 359.98px) {
  .brand-lockup {
    gap: 0.375rem !important;
  }

  .brand-logo-frame {
    height: 46px;
    width: 46px;
  }

  .brand-mark {
    height: 41px;
    width: 41px;
  }

  .brand-title span {
    font-size: 1.35rem;
  }
}

@media (min-width: 576px) {
  .brand-title span {
    font-size: 2.25rem;
  }
}
</style>
