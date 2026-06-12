---
title: "language-pack-en gnome-cards-data Conflict"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by sysrivets on 2007-07-15
There were conflicts between the language-pack-en and gnome-cards-data packages on my system that I resolved with the force-overwrite option to the dpkg command. The installation management team probably already knows about this.  I'll paste the log from the forced overwrite install just in case anyone else needs to deal with this situation similarly in the near term.

/var/cache/apt/archives$ sudo dpkg -i --force-overwrite language-pack-en_1%3a7.04+20070601_all.deb
(Reading database ... 108896 files and directories currently installed.)
Preparing to replace language-pack-en 1:7.04+20070412 (using language-pack-en_1%3a7.04+20070601_all.deb) ...
Unpacking replacement language-pack-en ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_AU/LC_MESSAGES/adduser.mo', which is also in package gnome-cards-data
Replacing files in old package language-pack-en-base ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_AU/LC_MESSAGES/xfce4-session.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_AU/LC_MESSAGES/restricted-manager.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_AU/LC_MESSAGES/command-not-found.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_AU/LC_MESSAGES/gcc-4.1.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_AU/LC_MESSAGES/skim-scim-hangul.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_AU/LC_MESSAGES/skim-scim-tables.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/apt.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/libapt-pkg3.53.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/coreutils.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/dpkg.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/gettext-tools.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/gimp20-script-fu.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/minicom.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/synaptic.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/update-manager.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/xfce4-session.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/xfdesktop.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/language-selector.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/libexo-0.3.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/gdebi.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/Thunar.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/restricted-manager.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/command-not-found.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/compiz.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/upstart.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_GB/LC_MESSAGES/hello.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/en_NZ/LC_MESSAGES/launchpad-integration.mo', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/doc/language-pack-en/copyright', which is also in package gnome-cards-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/doc/language-pack-en/changelog.gz', which is also in package gnome-cards-data
Setting up language-pack-en (7.04+20070601) ...

---

