---
title: "apt-get upgrade breaks system, system won't stay online for more then 5 min"
date: 2017-01-11
forum: Installation &amp; Upgrades
---

### Post by Superdude_123 on 2017-01-11
After doing a fresh install, and after running apt-get update and apt-get upgrade, my system goes offline randomly or hangs within minutes of coming online. The following packages were the ones were upgraded:

```
accountsservice adium-theme-ubuntu adwaita-icon-theme apparmor apport apport-gtk appstream apt apt-transport-https apt-utils apturl apturl-common bamfdaemon
  base-files bash bash-completion bind9-host binutils brltty bsdutils command-not-found command-not-found-data compiz compiz-core compiz-gnome
  compiz-plugins-default console-setup console-setup-linux cpp-5 cups-browsed cups-filters cups-filters-core-drivers curl dbus dbus-x11 deja-dup dh-python
  distro-info-data dmidecode dnsmasq-base dnsutils dosfstools dpkg dpkg-dev eog file-roller firefox fontconfig fontconfig-config fonts-noto-cjk fonts-opensymbol
  fuse fwupd g++-5 gcc-5 gcc-5-base gdb gdbserver ghostscript ghostscript-x gir1.2-dbusmenu-glib-0.4 gir1.2-gdkpixbuf-2.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-javascriptcoregtk-4.0 gir1.2-packagekitglib-1.0 gir1.2-soup-2.4 gir1.2-unity-5.0 gir1.2-webkit2-4.0 glib-networking
  glib-networking-common glib-networking-services gnome-calculator gnome-calendar gnome-font-viewer gnome-menus gnome-session-bin gnome-session-common
  gnome-settings-daemon-schemas gnome-sudoku gnome-system-monitor gnupg gpgv grep grub-common grub-pc grub-pc-bin grub2-common gstreamer1.0-alsa
  gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-tools gstreamer1.0-x
  gtk2-engines-murrine gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs ifupdown im-config imagemagick imagemagick-6.q16
  imagemagick-common indicator-bluetooth init init-system-helpers initramfs-tools initramfs-tools-bin initramfs-tools-core isc-dhcp-client isc-dhcp-common kbd
  keyboard-configuration klibc-utils kpartx kpartx-boot language-selector-common language-selector-gnome less libaccountsservice0 libapparmor-perl libapparmor1
  libappstream-glib8 libappstream3 libapt-inst2.0 libapt-pkg5.0 libarchive13 libasan2 libatomic1 libbamf3-2 libbind9-140 libblkid1 libboost-date-time1.58.0
  libboost-filesystem1.58.0 libboost-iostreams1.58.0 libboost-system1.58.0 libbrlapi0.6 libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev libcc1-0 libcilkrts5
  libcompizconfig0 libcupsfilters1 libcurl3 libcurl3-gnutls libdbus-1-3 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdecoration0 libdfu1
  libdns-export162 libdns162 libdpkg-perl libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libegl1-mesa libexpat1 libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libfdisk1 libfontconfig1 libfontembed1 libframe6 libfuse2 libfwupd1 libgail-3-0 libgbm1 libgcc-5-dev libgcrypt20 libgd3
  libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-0 libglib2.0-bin libglib2.0-data libgnome-menu-3-0
  libgnutls-openssl27 libgnutls30 libgomp1 libgs9 libgs9-common libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer1.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgweather-3-6 libgweather-common libharfbuzz-icu0 libharfbuzz0b libidn11 libimobiledevice6 libisc-export160 libisc160 libisccc140
  libisccfg140 libitm1 libjavascriptcoregtk-4.0-18 libklibc libksba8 libldap-2.4-2 liblightdm-gobject-1-0 libllvm3.8 liblsan0 liblwres141 libmagickcore-6.q16-2
  libmagickcore-6.q16-2-extra libmagickwand-6.q16-2 libmetacity-private3a libmount1 libmpx0 libnautilus-extension1a libndp0 libnm-glib-vpn1 libnm-glib4
  libnm-gtk-common libnm-gtk0 libnm-util2 libnm0 libnma-common libnma0 libnspr4 libnss3 libnss3-nssdb libnux-4.0-0 libnux-4.0-common libp11-kit0
  libpackagekit-glib2-16 libpam-systemd libplymouth4 libpoppler-glib8 libpoppler58 libprocps4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpython2.7
  libpython2.7-minimal libpython2.7-stdlib libpython3.5 libpython3.5-minimal libpython3.5-stdlib libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5
  libqt5printsupport5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5widgets5 libqt5xml5 libquadmath0 libsmartcols1 libsmbclient libsoup-gnome2.4-1 libsoup2.4-1
  libssl1.0.0 libstdc++-5-dev libstdc++6 libsystemd0 libtasn1-6 libtevent0 libtracker-sparql-1.0-0 libtsan0 libubsan0 libudev1 libunity-control-center1
  libunity-core-6.0-9 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity-settings-daemon1 libunity9 libupower-glib3 libusbmuxd4 libuuid1
  libvncclient1 libwayland-egl1-mesa libwbclient0 libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2 libwhoopsie0 libxatracker2 libxml2 light-themes lightdm
  linux-firmware linux-libc-dev locales lsb-base lsb-release lshw metacity-common mount mtools mtr-tiny multiarch-support nautilus nautilus-data network-manager
  network-manager-gnome nux-tools openssl p11-kit p11-kit-modules plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text poppler-utils
  printer-driver-brlaser procps pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python2.7 python2.7-minimal python3-apport
  python3-brlapi python3-commandnotfound python3-cryptography python3-distupgrade python3-problem-report python3-pyparsing python3-software-properties
  python3-update-manager python3-urllib3 python3.5 python3.5-minimal samba-libs sbsigntool shared-mime-info software-properties-common software-properties-gtk
  sudo suru-icon-theme systemd systemd-sysv tar thermald tzdata ubuntu-artwork ubuntu-docs ubuntu-drivers-common ubuntu-mobile-icons ubuntu-mono
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-session udev unattended-upgrades unity unity-control-center unity-control-center-faces
  unity-lens-applications unity-schemas unity-scopes-runner unity-services unity-settings-daemon uno-libs3 update-manager update-manager-core update-notifier
  update-notifier-common upower upstart ure util-linux uuid-runtime vim-common vim-tiny vino wget whoopsie xbrlapi xdiagnose xinit xserver-common
  xserver-xorg-core xserver-xorg-video-intel

```

The only way to get the system back online is to do a hard shutdown and pray that it stays online for more then 15 min. Any ideas?

---

### Post by Superdude_123 on 2017-01-12
For anyone that finds this useful later, uninstalling xserver-xorg-video-intel proved to solve the problem.

---

### Post by lisati on 2017-01-12
I've added [noparse]```
 and 
```[/noparse] tags to your first post, because it can make copied terminal output easier to read.

---

