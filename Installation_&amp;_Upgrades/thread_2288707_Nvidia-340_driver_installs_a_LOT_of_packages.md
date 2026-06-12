---
title: "Nvidia-340 driver installs a LOT of packages"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by Sren_Riisom on 2015-07-29
Hi! 

I tried searching for any answers to my problem, but came up empty handed. 
I'm on a minimal install running openbox, no login manager and so forth. I'm trying to install the nvidia driver so I can extract a couple of things to conky, but when I try to install the recommended nvidia-340 it wants to install a literal shitload of packages with it, along with a lot of stuff I really don't want which isn't included in the nvidia-304. Is there any way to minimize the 340 installation? 

```
sudo apt-get install nvidia-304
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  acpid build-essential dkms dpkg-dev fakeroot g++ g++-4.9 gcc gcc-4.9
  lib32gcc1 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libasan1 libatomic1 libc-dev-bin libc6-dev
  libc6-i386 libcilkrts5 libcuda1-304 libfakeroot libgcc-4.9-dev libitm1
  libjansson4 liblsan0 libstdc++-4.9-dev libtsan0 libubsan0 libxnvctrl0
  linux-libc-dev manpages-dev nvidia-opencl-icd-304 nvidia-settings
  ocl-icd-libopencl1 pkg-config screen-resolution-extra
Suggested packages:
  debian-keyring g++-multilib g++-4.9-multilib gcc-4.9-doc libstdc++6-4.9-dbg
  gcc-multilib autoconf automake libtool flex bison gdb gcc-doc
  gcc-4.9-multilib gcc-4.9-locales libgcc1-dbg libgomp1-dbg libitm1-dbg
  libatomic1-dbg libasan1-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg
  libcilkrts5-dbg libquadmath0-dbg glibc-doc libstdc++-4.9-doc opencl-icd
The following NEW packages will be installed
  acpid build-essential dkms dpkg-dev fakeroot g++ g++-4.9 gcc gcc-4.9
  lib32gcc1 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libasan1 libatomic1 libc-dev-bin libc6-dev
  libc6-i386 libcilkrts5 libcuda1-304 libfakeroot libgcc-4.9-dev libitm1
  libjansson4 liblsan0 libstdc++-4.9-dev libtsan0 libubsan0 libxnvctrl0
  linux-libc-dev manpages-dev nvidia-304 nvidia-opencl-icd-304 nvidia-settings
  ocl-icd-libopencl1 pkg-config screen-resolution-extra
0 to upgrade, 37 to newly install, 0 to remove and 41 not to upgrade.
Need to get 83.8 MB of archives.
After this operation, 320 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

```
sudo apt-get install nvidia-340
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  acpid adwaita-icon-theme apg avahi-daemon avahi-utils bbswitch-dkms bluez
  build-essential cgmanager cheese-common cracklib-runtime
  cups-filters-ippusbxd cups-pk-helper dconf-cli dialog dkms dns-root-data
  dnsmasq-base dpkg-dev evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts fakeroot g++ g++-4.9 gcc gcc-4.9
  geoclue geoclue-ubuntu-geoip gir1.2-gnomebluetooth-1.0
  gir1.2-gnomekeyring-1.0 gir1.2-ibus-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gkbd-capplet gnome-bluetooth
  gnome-control-center-shared-data gnome-desktop3-data gnome-menus
  gnome-power-manager gnome-screensaver gnome-session-bin
  gnome-settings-daemon-schemas gnome-user-share gsettings-ubuntu-schemas
  gstreamer1.0-clutter gvfs-backends humanity-icon-theme hwdata ibus ibus-gtk
  ibus-gtk3 im-config indicator-applet indicator-bluetooth indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-session
  indicator-sound iputils-arping lib32gcc1 libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0
  libaccounts-qt5-1 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libarchive13 libasan1 libatomic1 libavahi-core7
  libbluetooth3 libc-dev-bin libc6-dev libc6-i386 libcamel-1.2-49
  libcanberra-pulse libcdio-paranoia1 libcgmanager0 libcheese-gtk23 libcheese7
  libcilkrts5 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcogl-common libcogl-pango20 libcogl-path20 libcogl20
  libcrack2 libcuda1-340 libdaemon0 libdouble-conversion1 libebackend-1.2-7
  libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libfakeroot libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libgcc-4.9-dev libgdata-common libgdata19
  libgee2 libgeocode-glib0 libglib2.0-0 libglib2.0-bin libgnome-bluetooth11
  libgnome-desktop-3-10 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgweather-3-6 libgweather-common
  libibus-1.0-5 libical1a libido3-0.1-0 libimobiledevice4 libinput7 libitm1
  libjansson4 libjson0 liblightdm-gobject-1-0 liblsan0 liblzo2-2 libmbim-glib4
  libmbim-proxy libmm-glib0 libmnl0 libndp0 libnetfilter-conntrack3
  libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0
  libnm-util2 libnss-mdns liboauth0 libopenobex1 libpackagekit-glib2-16
  libpanel-applet0 libplist2 libpulse-mainloop-glib0 libpulsedsp
  libpwquality-common libpwquality1 libqmi-glib1 libqmi-proxy libqt5core5a
  libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5printsupport5
  libqt5qml5 libqt5quick5 libqt5sql5 libqt5sql5-sqlite libqt5webkit5
  libqt5widgets5 libqt5xml5 libsignon-extension1 libsignon-glib1
  libsignon-plugins-common1 libsignon-qt5-1 libstdc++-4.9-dev
  libtimezonemap-data libtimezonemap1 libtsan0 libubsan0
  libunity-control-center1 libunity-settings-daemon1 libupower-glib3
  liburl-dispatcher1 libusbmuxd2 libwacom-bin libwacom-common libwacom2
  libwayland-egl1-mesa libwebrtc-audio-processing-0 libxcb-icccm4
  libxcb-image0 libxcb-render-util0 libxcb-xkb1 libxkbcommon-x11-0
  libxklavier16 libxnvctrl0 lightdm linux-libc-dev manpages-dev
  mobile-broadband-provider-info modemmanager mousetweaks nautilus-data
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome nvidia-opencl-icd-340 nvidia-prime
  nvidia-settings obex-data-server obexd-client ocl-icd-libopencl1 pkg-config
  pptp-linux pulseaudio pulseaudio-module-x11 pulseaudio-utils
  python3-aptdaemon.pkcompat python3-bs4 python3-chardet python3-cups
  python3-cupshelpers python3-html5lib python3-lxml python3-requests
  python3-six python3-smbc python3-urllib3 python3-xdg qttranslations5-l10n
  rtkit screen-resolution-extra session-migration signon-keyring-extension
  signon-plugin-oauth2 signon-ui signon-ui-service signon-ui-x11 signond
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev systemd-shim ubuntu-mono ubuntu-system-service
  ubuntu-touch-sounds unity-control-center unity-control-center-signon
  unity-greeter unity-settings-daemon upower upstart upstart-bin
  usb-modeswitch usb-modeswitch-data usbmuxd wamerican
Suggested packages:
  avahi-autoipd bumblebee bluez-hcidump debian-keyring evolution
  evolution-data-server-dbg g++-multilib g++-4.9-multilib gcc-4.9-doc
  libstdc++6-4.9-dbg gcc-multilib autoconf automake libtool flex bison gdb
  gcc-doc gcc-4.9-multilib gcc-4.9-locales libgcc1-dbg libgomp1-dbg
  libitm1-dbg libatomic1-dbg libasan1-dbg liblsan0-dbg libtsan0-dbg
  libubsan0-dbg libcilkrts5-dbg libquadmath0-dbg apache2.2-bin
  libapache2-mod-dnssd samba-common ibus-clutter ibus-doc ibus-qt4 click
  powerd unity-system-compositor apport unity-greeter-session-broadcast lrzip
  glibc-doc fcitx libusbmuxd-tools libstdc++-4.9-doc url-dispatcher nautilus
  network-manager-openconnect-gnome network-manager-openvpn-gnome
  network-manager-vpnc-gnome opencl-icd pavumeter pavucontrol paman paprefs
  python3-genshi python3-lxml-dbg python-lxml-doc python3-ndg-httpsclient
  python3-openssl python3-pyasn1 pm-utils gstreamer0.10-pulseaudio
  libcanberra-gtk-module lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure remote-login-service graphviz
  upstart-monitor comgt wvdial
The following NEW packages will be installed
  acpid adwaita-icon-theme apg avahi-daemon avahi-utils bbswitch-dkms bluez
  build-essential cgmanager cheese-common cracklib-runtime
  cups-filters-ippusbxd cups-pk-helper dconf-cli dialog dkms dns-root-data
  dnsmasq-base dpkg-dev evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts fakeroot g++ g++-4.9 gcc gcc-4.9
  geoclue geoclue-ubuntu-geoip gir1.2-gnomebluetooth-1.0
  gir1.2-gnomekeyring-1.0 gir1.2-ibus-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gkbd-capplet gnome-bluetooth
  gnome-control-center-shared-data gnome-desktop3-data gnome-menus
  gnome-power-manager gnome-screensaver gnome-session-bin
  gnome-settings-daemon-schemas gnome-user-share gsettings-ubuntu-schemas
  gstreamer1.0-clutter gvfs-backends humanity-icon-theme hwdata ibus ibus-gtk
  ibus-gtk3 im-config indicator-applet indicator-bluetooth indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-session
  indicator-sound iputils-arping lib32gcc1 libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0
  libaccounts-qt5-1 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libarchive13 libasan1 libatomic1 libavahi-core7
  libbluetooth3 libc-dev-bin libc6-dev libc6-i386 libcamel-1.2-49
  libcanberra-pulse libcdio-paranoia1 libcgmanager0 libcheese-gtk23 libcheese7
  libcilkrts5 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcogl-common libcogl-pango20 libcogl-path20 libcogl20
  libcrack2 libcuda1-340 libdaemon0 libdouble-conversion1 libebackend-1.2-7
  libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libfakeroot libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libgcc-4.9-dev libgdata-common libgdata19
  libgee2 libgeocode-glib0 libglib2.0-bin libgnome-bluetooth11
  libgnome-desktop-3-10 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgweather-3-6 libgweather-common
  libibus-1.0-5 libical1a libido3-0.1-0 libimobiledevice4 libinput7 libitm1
  libjansson4 libjson0 liblightdm-gobject-1-0 liblsan0 liblzo2-2 libmbim-glib4
  libmbim-proxy libmm-glib0 libmnl0 libndp0 libnetfilter-conntrack3
  libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0
  libnm-util2 libnss-mdns liboauth0 libopenobex1 libpackagekit-glib2-16
  libpanel-applet0 libplist2 libpulse-mainloop-glib0 libpulsedsp
  libpwquality-common libpwquality1 libqmi-glib1 libqmi-proxy libqt5core5a
  libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5printsupport5
  libqt5qml5 libqt5quick5 libqt5sql5 libqt5sql5-sqlite libqt5webkit5
  libqt5widgets5 libqt5xml5 libsignon-extension1 libsignon-glib1
  libsignon-plugins-common1 libsignon-qt5-1 libstdc++-4.9-dev
  libtimezonemap-data libtimezonemap1 libtsan0 libubsan0
  libunity-control-center1 libunity-settings-daemon1 libupower-glib3
  liburl-dispatcher1 libusbmuxd2 libwacom-bin libwacom-common libwacom2
  libwayland-egl1-mesa libwebrtc-audio-processing-0 libxcb-icccm4
  libxcb-image0 libxcb-render-util0 libxcb-xkb1 libxkbcommon-x11-0
  libxklavier16 libxnvctrl0 lightdm linux-libc-dev manpages-dev
  mobile-broadband-provider-info modemmanager mousetweaks nautilus-data
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome nvidia-340 nvidia-opencl-icd-340 nvidia-prime
  nvidia-settings obex-data-server obexd-client ocl-icd-libopencl1 pkg-config
  pptp-linux pulseaudio pulseaudio-module-x11 pulseaudio-utils
  python3-aptdaemon.pkcompat python3-bs4 python3-chardet python3-cups
  python3-cupshelpers python3-html5lib python3-lxml python3-requests
  python3-six python3-smbc python3-urllib3 python3-xdg qttranslations5-l10n
  rtkit screen-resolution-extra session-migration signon-keyring-extension
  signon-plugin-oauth2 signon-ui signon-ui-service signon-ui-x11 signond
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev systemd-shim ubuntu-mono ubuntu-system-service
  ubuntu-touch-sounds unity-control-center unity-control-center-signon
  unity-greeter unity-settings-daemon upower upstart upstart-bin
  usb-modeswitch usb-modeswitch-data usbmuxd wamerican
The following packages will be upgraded:
  libglib2.0-0
1 to upgrade, 261 to newly install, 0 to remove and 40 not to upgrade.
Need to get 162 MB of archives.
After this operation, 654 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Also, first post! Let me know if I've let something out ](*,)

---

### Post by euphoria42 on 2015-07-29
I'd have to admit that a fair bit of those dependencies for the 340 package don't seem to make sense, but it beats me as to why nvidia would want them.

---

