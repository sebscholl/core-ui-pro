<template>
  <CHeader position="sticky" class="mb-4">
    <CContainer fluid>
      <CHeaderToggler class="ps-1" @click="$store.commit('toggleSidebar')">
        <CIcon icon="cil-menu" size="lg" />
      </CHeaderToggler>
      <CHeaderBrand class="mx-auto d-lg-none" to="/">
        <CIcon :icon="logo" height="48" alt="Logo" />
      </CHeaderBrand>
      <CHeaderNav class="d-none d-md-flex me-auto">
        <CNavItem>
          <CNavLink href="/dashboard"> Dashboard </CNavLink>
        </CNavItem>
        <CNavItem>
          <CNavLink href="#">Users</CNavLink>
        </CNavItem>
        <CNavItem>
          <CNavLink href="#">Settings</CNavLink>
        </CNavItem>
      </CHeaderNav>
      <CHeaderNav class="ms-auto me-4">
        <CButtonGroup aria-label="Theme switch">
          <CFormCheck
            type="radio"
            :button="{ color: 'primary' }"
            name="theme-switch"
            id="btn-light-theme"
            autoComplete="off"
            :checked="$store.state.theme === 'default'"
            @change="
              (event) =>
                $store.commit({
                  type: 'toggleTheme',
                  value: 'default',
                })
            "
          >
            <template #label><CIcon icon="cil-sun" /></template>
          </CFormCheck>
          <CFormCheck
            type="radio"
            :button="{ color: 'primary' }"
            name="theme-switch"
            id="btn-dark-theme"
            autoComplete="off"
            :checked="$store.state.theme === 'dark'"
            @change="
              (event) =>
                $store.commit({
                  type: 'toggleTheme',
                  value: 'dark',
                })
            "
          >
            <template #label><CIcon icon="cil-moon" /></template>
          </CFormCheck>
        </CButtonGroup>
      </CHeaderNav>
      <CHeaderNav class="ms-3 me-4">
        <AppHeaderDropdownAccnt />
      </CHeaderNav>
      <CHeaderToggler class="px-md-0 me-md-3">
        <CIcon
          icon="cil-applications-settings"
          size="lg"
          @click="$store.commit('toggleAside')"
        />
      </CHeaderToggler>
    </CContainer>
    <CHeaderDivider />
    <CContainer fluid>
      <AppBreadcrumb />
    </CContainer>
  </CHeader>
</template>

<script lang="ts">
import AppBreadcrumb from './AppBreadcrumb.vue'
import AppHeaderDropdownAccnt from './AppHeaderDropdownAccnt.vue'
import { logo } from '@/assets/brand/logo'

export default {
  name: 'AppHeader',
  components: {
    AppBreadcrumb,
    AppHeaderDropdownAccnt,
  },
  // eslint-disable-next-line @typescript-eslint/explicit-module-boundary-types
  setup() {
    return {
      logo,
    }
  },
}
</script>
