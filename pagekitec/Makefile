#
# Copyright (C) 2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pagekitec
PKG_REV:=e79bf00c4efd4e37e4941a054e1e6d8fbce5d00a
PKG_VERSION:=121207C-$(PKG_REV)
PKG_RELEASE:=1
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=git@github.com:pagekite/libpagekite.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)
# jow says also try PKG_SOURCE_VERSION:=origin/branchname... (gets HEAD?)

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Make localhost servers publicly visible.
  URL:=https://pagekite.net/wiki/Floss/LibPageKite/
  DEPENDS:=+libopenssl +libpthread +libev
endef

define Package/$(PKG_NAME)/description
PageKite is a system for running publicly visible servers (generally
 web servers) on machines without a direct connection to the Internet,
 such as mobile devices or computers behind restrictive firewalls.
 PageKite works around NAT, firewalls and IP-address limitations by
 using a combination of tunnels and reverse proxies.

 This package provides an implementation of the PageKite Protocol in C,
 optimized for high-performance or embedded applications.

 Basic UCI support for HTTP and SSH servers is also included in this package.

 https://pagekite.net/wiki/Floss/LibPageKite/
endef

define Package/$(PKG_NAME)/conffiles
/etc/config/$(PKG_NAME)
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/$(PKG_NAME).init $(1)/etc/init.d/$(PKG_NAME)
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/$(PKG_NAME).config $(1)/etc/config/$(PKG_NAME)
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/$(PKG_NAME).uci-defaults $(1)/etc/uci-defaults/$(PKG_NAME)
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
