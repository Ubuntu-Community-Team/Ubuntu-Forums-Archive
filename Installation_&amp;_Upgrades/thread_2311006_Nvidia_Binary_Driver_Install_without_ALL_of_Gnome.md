---
title: "Nvidia Binary Driver Install without ALL of Gnome?"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2016-01-23
Hey all,

I am doing a dedicated HTPC install with XBMC Kodi using the ubuntu 14.04 mini image.

In my setup I am running Kodi/XBMC directly on top of X without Unity/Gnome/KDE etc.

I need the Nvidia binary drivers in oder to get properly working VDPAU support.   The problem is, when I go to install them, the dependencies are such, that it wants to install ALL of gnome and a ton of other stuff.   See below:

```

htpc@HTPC-Virtual-01:~$ sudo apt-get install nvidia-352
[sudo] password for htpc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acl acpid apg aptdaemon aspell aspell-en at-spi2-core avahi-utils
  bbswitch-dkms bluez cheese-common colord cracklib-runtime cups-pk-helper
  dbus-x11 dconf-cli dconf-gsettings-backend dconf-service desktop-file-utils
  dialog diffstat dkms dnsmasq-base enchant evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts fakeroot
  fontconfig gconf-service gconf-service-backend gconf2 gconf2-common gcr
  gdisk geoclue geoclue-ubuntu-geoip gettext gir1.2-atk-1.0 gir1.2-freedesktop
  gir1.2-gdkpixbuf-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-ibus-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0
  gkbd-capplet glib-networking glib-networking-common glib-networking-services
  gnome-bluetooth gnome-control-center-shared-data gnome-desktop3-data
  gnome-icon-theme gnome-icon-theme-symbolic gnome-keyring gnome-menus
  gnome-power-manager gnome-screensaver gnome-session-bin
  gnome-settings-daemon-schemas gnome-user-guide gnome-user-share
  gsettings-desktop-schemas gsettings-ubuntu-schemas gstreamer0.10-pulseaudio
  gstreamer1.0-clutter gstreamer1.0-plugins-base gstreamer1.0-plugins-good
  gstreamer1.0-x gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-libs
  hardening-includes hicolor-icon-theme humanity-icon-theme hunspell-en-us
  hwdata ibus ibus-gtk ibus-gtk3 im-config indicator-applet
  indicator-application indicator-bluetooth indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-session
  indicator-sound intltool-debian iputils-arping lib32gcc1 libaa1
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1
  libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13
  libasound2-plugins libaspell15 libasprintf-dev libatk-bridge2.0-0
  libatk1.0-0 libatk1.0-data libatspi2.0-0 libauthen-sasl-perl libautodie-perl
  libavahi-glib1 libavc1394-0 libc6-i386 libcaca0 libcairo-gobject2 libcairo2
  libcamel-1.2-45 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse
  libcanberra0 libcdio-cdda1 libcdio-paranoia1 libcdparanoia0 libcheese-gtk23
  libcheese7 libclone-perl libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango15
  libcogl15 libcolord1 libcolorhug1 libcrack2 libcroco3 libcuda1-352
  libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1
  libdigest-hmac-perl libdpkg-perl libdv4 libebackend-1.2-7 libebook-1.2-14
  libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libelfg0 libemail-valid-perl
  libenchant1c2a libexif12 libfakeroot libfftw3-single3 libfile-basedir-perl
  libfile-fcntllock-perl libgbm1 libgconf-2-4 libgcr-ui-3-1 libgd3
  libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common
  libgee2 libgeoclue0 libgettextpo-dev libgettextpo0 libglib2.0-bin
  libgnome-bluetooth11 libgnome-desktop-3-7 libgnome-keyring-common
  libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgphoto2-6 libgphoto2-l10n
  libgphoto2-port10 libgraphite2-3 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0
  libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common
  libgusb2 libgweather-3-6 libgweather-common libharfbuzz-icu0 libharfbuzz0b
  libhunspell-1.3-0 libibus-1.0-5 libical1 libido3-0.1-0 libiec61883-0
  libieee1284-3 libindicator3-7 libio-pty-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libipc-run-perl libipc-system-simple-perl libjasper1
  libjavascriptcoregtk-3.0-0 libjson-glib-1.0-0 libjson-glib-1.0-common
  liblightdm-gobject-1-0 liblist-moreutils-perl libltdl7 libmailtools-perl
  libmbim-glib0 libmm-glib0 libmnl0 libmtp-common libmtp-runtime libmtp9
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libnet-libidn-perl
  libnet-smtp-ssl-perl libnet-ssleay-perl libnetfilter-conntrack3
  libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0
  libnm-util2 libnotify4 libnspr4 libnss3 libnss3-nssdb liboauth0 libopenobex1
  liborc-0.4-0 libp11-kit-gnome-keyring libpackagekit-glib2-16
  libpam-gnome-keyring libpanel-applet-4-0 libpango-1.0-0 libpango1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangox-1.0-0 libpangoxft-1.0-0
  libpcsclite1 libperlio-gzip-perl libproxy1 libpulse-mainloop-glib0
  libpulsedsp libpwquality-common libpwquality1 libqmi-glib0 libqt5core5a
  libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5positioning5
  libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5
  libraw1394-11 libreadline5 librest-0.7-0 librsvg2-2 librsvg2-common libsane
  libsane-common libsecret-1-0 libsecret-common libshout3 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsocket6-perl
  libsoup-gnome2.4-1 libsoup2.4-1 libspeex1 libspeexdsp1 libsub-identify-perl
  libsystemd-journal0 libtext-levenshtein-perl libthai-data libthai0
  libtheora0 libtimezonemap1 libudisks2-0 libunistring0
  libunity-control-center1 liburi-perl liburl-dispatcher1 libv4l-0
  libv4lconvert0 libvisual-0.4-0 libvisual-0.4-plugins libvpx1 libwacom-common
  libwacom2 libwavpack1 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-randr0
  libxcb-render-util0 libxcb-render0 libxcb-shm0 libxcb-xkb1
  libxkbcommon-x11-0 libxklavier16 libyelp0 lightdm lintian
  mobile-broadband-provider-info modemmanager mousetweaks nautilus-data
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notification-daemon nvidia-opencl-icd-352
  nvidia-prime nvidia-settings obex-data-server obexd-client
  ocl-icd-libopencl1 p11-kit p11-kit-modules patchutils pkg-config
  policykit-1-gnome pptp-linux pulseaudio pulseaudio-module-x11
  pulseaudio-utils python-cairo python-cups python-cupshelpers python-dbus
  python-dbus-dev python-gi python-gnomekeyring python-gobject
  python-gobject-2 python-gtk2 python-libxml2 python-notify python-smbc
  python3-aptdaemon python3-aptdaemon.pkcompat python3-defer
  python3-pkg-resources python3-xdg python3-xkit rtkit screen-resolution-extra
  session-migration signon-keyring-extension signon-plugin-oauth2 signon-ui
  signond sound-theme-freedesktop system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils
  ubuntu-system-service udisks2 unity-control-center
  unity-control-center-signon unity-greeter unity-settings-daemon
  usb-modeswitch usb-modeswitch-data wpasupplicant yelp yelp-xsl zenity
  zenity-common
Suggested packages:
  aspell-doc spellutils bumblebee bluez-hcidump dpkg-dev debhelper evolution
  evolution-data-server-dbg gconf-defaults-service gettext-doc apache2.2-bin
  libapache2-mod-dnssd gvfs-backends-goa samba-common hunspell
  openoffice.org-hunspell openoffice.org-core ibus-clutter ibus-doc ibus-qt4
  click apport unity-greeter-session-broadcast lrzip libgssapi-perl
  libcanberra-gtk0 debian-keyring libdv-bin oss-compat libenchant-voikko
  libfftw3-bin libfftw3-dev libgd-tools gphoto2 gtkam gstreamer-codec-install
  gnome-codec-install gstreamer0.10-tools gstreamer0.10-plugins-base
  gstreamer1.0-tools libjasper-runtime ttf-baekmuk ttf-arphic-gbsn00lp
  ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pcscd
  libraw1394-doc librsvg2-bin hplip hpoj libsane-extras sane-utils speex
  libwww-perl url-dispatcher binutils-multiarch libhtml-parser-perl
  libtext-template-perl libyaml-perl gnome-control-center nautilus
  avahi-autoipd network-manager-openconnect-gnome
  network-manager-openvpn-gnome network-manager-vpnc-gnome opencl-icd
  pavumeter paman pavucontrol paprefs pulseaudio-module-raop
  pulseaudio-esound-compat python-dbus-doc python-dbus-dbg python-gi-cairo
  python-gobject-2-dbg python-gtk2-doc python3-setuptools xfsprogs
  reiserfsprogs exfat-utils btrfs-tools mdadm libcanberra-gtk-module
  x11-xserver-utils lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure remote-login-service metacity
  x-window-manager comgt wvdial wpagui libengine-pkcs11-openssl
The following NEW packages will be installed:
  acl acpid apg aptdaemon aspell aspell-en at-spi2-core avahi-utils
  bbswitch-dkms bluez cheese-common colord cracklib-runtime cups-pk-helper
  dbus-x11 dconf-cli dconf-gsettings-backend dconf-service desktop-file-utils
  dialog diffstat dkms dnsmasq-base enchant evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts fakeroot
  fontconfig gconf-service gconf-service-backend gconf2 gconf2-common gcr
  gdisk geoclue geoclue-ubuntu-geoip gettext gir1.2-atk-1.0 gir1.2-freedesktop
  gir1.2-gdkpixbuf-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-ibus-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0
  gkbd-capplet glib-networking glib-networking-common glib-networking-services
  gnome-bluetooth gnome-control-center-shared-data gnome-desktop3-data
  gnome-icon-theme gnome-icon-theme-symbolic gnome-keyring gnome-menus
  gnome-power-manager gnome-screensaver gnome-session-bin
  gnome-settings-daemon-schemas gnome-user-guide gnome-user-share
  gsettings-desktop-schemas gsettings-ubuntu-schemas gstreamer0.10-pulseaudio
  gstreamer1.0-clutter gstreamer1.0-plugins-base gstreamer1.0-plugins-good
  gstreamer1.0-x gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-libs
  hardening-includes hicolor-icon-theme humanity-icon-theme hunspell-en-us
  hwdata ibus ibus-gtk ibus-gtk3 im-config indicator-applet
  indicator-application indicator-bluetooth indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-session
  indicator-sound intltool-debian iputils-arping lib32gcc1 libaa1
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1
  libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13
  libasound2-plugins libaspell15 libasprintf-dev libatk-bridge2.0-0
  libatk1.0-0 libatk1.0-data libatspi2.0-0 libauthen-sasl-perl libautodie-perl
  libavahi-glib1 libavc1394-0 libc6-i386 libcaca0 libcairo-gobject2 libcairo2
  libcamel-1.2-45 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse
  libcanberra0 libcdio-cdda1 libcdio-paranoia1 libcdparanoia0 libcheese-gtk23
  libcheese7 libclone-perl libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango15
  libcogl15 libcolord1 libcolorhug1 libcrack2 libcroco3 libcuda1-352
  libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1
  libdigest-hmac-perl libdpkg-perl libdv4 libebackend-1.2-7 libebook-1.2-14
  libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libelfg0 libemail-valid-perl
  libenchant1c2a libexif12 libfakeroot libfftw3-single3 libfile-basedir-perl
  libfile-fcntllock-perl libgbm1 libgconf-2-4 libgcr-ui-3-1 libgd3
  libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common
  libgee2 libgeoclue0 libgettextpo-dev libgettextpo0 libglib2.0-bin
  libgnome-bluetooth11 libgnome-desktop-3-7 libgnome-keyring-common
  libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgphoto2-6 libgphoto2-l10n
  libgphoto2-port10 libgraphite2-3 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0
  libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common
  libgusb2 libgweather-3-6 libgweather-common libharfbuzz-icu0 libharfbuzz0b
  libhunspell-1.3-0 libibus-1.0-5 libical1 libido3-0.1-0 libiec61883-0
  libieee1284-3 libindicator3-7 libio-pty-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libipc-run-perl libipc-system-simple-perl libjasper1
  libjavascriptcoregtk-3.0-0 libjson-glib-1.0-0 libjson-glib-1.0-common
  liblightdm-gobject-1-0 liblist-moreutils-perl libltdl7 libmailtools-perl
  libmbim-glib0 libmm-glib0 libmnl0 libmtp-common libmtp-runtime libmtp9
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libnet-libidn-perl
  libnet-smtp-ssl-perl libnet-ssleay-perl libnetfilter-conntrack3
  libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0
  libnm-util2 libnotify4 libnspr4 libnss3 libnss3-nssdb liboauth0 libopenobex1
  liborc-0.4-0 libp11-kit-gnome-keyring libpackagekit-glib2-16
  libpam-gnome-keyring libpanel-applet-4-0 libpango-1.0-0 libpango1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangox-1.0-0 libpangoxft-1.0-0
  libpcsclite1 libperlio-gzip-perl libproxy1 libpulse-mainloop-glib0
  libpulsedsp libpwquality-common libpwquality1 libqmi-glib0 libqt5core5a
  libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5positioning5
  libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5
  libraw1394-11 libreadline5 librest-0.7-0 librsvg2-2 librsvg2-common libsane
  libsane-common libsecret-1-0 libsecret-common libshout3 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsocket6-perl
  libsoup-gnome2.4-1 libsoup2.4-1 libspeex1 libspeexdsp1 libsub-identify-perl
  libsystemd-journal0 libtext-levenshtein-perl libthai-data libthai0
  libtheora0 libtimezonemap1 libudisks2-0 libunistring0
  libunity-control-center1 liburi-perl liburl-dispatcher1 libv4l-0
  libv4lconvert0 libvisual-0.4-0 libvisual-0.4-plugins libvpx1 libwacom-common
  libwacom2 libwavpack1 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-randr0
  libxcb-render-util0 libxcb-render0 libxcb-shm0 libxcb-xkb1
  libxkbcommon-x11-0 libxklavier16 libyelp0 lightdm lintian
  mobile-broadband-provider-info modemmanager mousetweaks nautilus-data
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notification-daemon nvidia-352
  nvidia-opencl-icd-352 nvidia-prime nvidia-settings obex-data-server
  obexd-client ocl-icd-libopencl1 p11-kit p11-kit-modules patchutils
  pkg-config policykit-1-gnome pptp-linux pulseaudio pulseaudio-module-x11
  pulseaudio-utils python-cairo python-cups python-cupshelpers python-dbus
  python-dbus-dev python-gi python-gnomekeyring python-gobject
  python-gobject-2 python-gtk2 python-libxml2 python-notify python-smbc
  python3-aptdaemon python3-aptdaemon.pkcompat python3-defer
  python3-pkg-resources python3-xdg python3-xkit rtkit screen-resolution-extra
  session-migration signon-keyring-extension signon-plugin-oauth2 signon-ui
  signond sound-theme-freedesktop system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils
  ubuntu-system-service udisks2 unity-control-center
  unity-control-center-signon unity-greeter unity-settings-daemon
  usb-modeswitch usb-modeswitch-data wpasupplicant yelp yelp-xsl zenity
  zenity-common
0 upgraded, 414 newly installed, 0 to remove and 0 not upgraded.
Need to get 160 MB of archives.
After this operation, 751 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```

I have temporarily worked around this by downloading the Nvidia binary blob directly from Nvidias webpage, and installed it by running their script.

The problem with this is that every time I upgrade the kernel (and sometimes this happens automatically through unattended security upgrades) I need to manually go back, and reinstall the driver, in order for it to recompile the module for the new kernel.

When you install the driver through the package manager, the module gets recompiled automatically when needed...

Is there any way to install the nvidia driver in apt, without having it pull in this horrendously long list of dependencies?

Much obliged,
Matt

---

### Post by ubfan1 on 2016-01-23
But most of those packages are not dependencies of the nvidia-352 package.  What does the --no-install-recommends switch produce on the apt-get install ?

---

### Post by mattlach on 2016-01-24
> **ubfan1 said:**
> But most of those packages are not dependencies of the nvidia-352 package.  What does the --no-install-recommends switch produce on the apt-get install ?

You are correct.  That resulted in far fewer dependencies.  

Thanks for the suggestion.

---

