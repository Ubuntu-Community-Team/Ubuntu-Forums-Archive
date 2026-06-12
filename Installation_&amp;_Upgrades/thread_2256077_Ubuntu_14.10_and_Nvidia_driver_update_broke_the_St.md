---
title: "Ubuntu 14.10 and Nvidia driver update broke the Steam"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by j0sk on 2014-12-09
Hi,

OS and hardware details:
```
Ubuntu 14.10 64-bit
GeForce GTX760
Installed GPU driver: Nvidia binary driver - version 331.89
```

When I launch Steam I got this:

```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
```

After I set the root password:

 ```
 bluez-cups bluez-gstreamer brasero brasero-cdrkit brasero-common brltty
  bsdmainutils bsdutils busybox-initramfs bzip2 ca-certificates cabextract
  cgmanager checkbox checkbox-gui checkbox-ng checkbox-ng-service checkbox-qt
  cheese cheese-common chromium-codecs-ffmpeg-extra cli-common colord
  command-not-found compiz compiz-core compiz-gnome compiz-plugins-default
  compiz-plugins-main-default compizconfig-backend-gconf
  compizconfig-settings-manager console-setup consolekit coreutils cpio cpp
  cpp-4.6 cpp-4.7 cpp-4.8 cpp-4.9 cracklib-runtime crda cron cryptsetup-bin
  cups cups-browsed cups-bsd cups-client cups-core-drivers cups-daemon
  cups-filters cups-filters-core-drivers cups-filters-ippusbxd cups-pk-helper
  cups-ppdc curl dash dbus dbus-x11 dc dconf-cli dconf-gsettings-backend
  dconf-service debconf debconf-i18n debianutils deja-dup
  deja-dup-backend-gvfs desktop-file-utils dh-python dialog
  dictionaries-common diffstat diffutils dkms dmidecode dmsetup dnsmasq-base
  dnsutils doc-base docbook-xml docbook-xsl dolphin dosfstools dpkg dpkg-dev
  duplicity dvd+rw-tools e2fslibs e2fsprogs ed eject empathy enchant eog
  espeak ethtool evince evince-common evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts fakeroot
  fancontrol file file-roller findutils finger firefox firefox-globalmenu
  folks-common fontconfig fontconfig-config fonts-droid fonts-kacst
  fonts-kacst-one fonts-nanum fonts-sil-abyssinica fonts-takao-pgothic
  foomatic-db-compressed-ppds foomatic-db-engine freerdp-x11 friendly-recovery
  friends friends-dispatcher friends-facebook friends-identica friends-twitter
  ftp fuse fusefat fuseiso fuseiso9660 gcalctool gcc gcc-4.6 gcc-4.7 gcc-4.8
  gcc-4.9 gconf-service gconf-service-backend gconf2 gconf2-common gcr gdb
  gdbserver gdisk gedit gedit-common genisoimage geoclue geoclue-ubuntu-geoip
  gettext gettext-base ghostscript ghostscript-x ginn gir1.2-accounts-1.0
  gir1.2-appindicator3-0.1 gir1.2-atk-1.0 gir1.2-atspi-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk-0.4 gir1.2-dee-1.0
  gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2
  gir1.2-freedesktop gir1.2-gdata-0.0 gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0
  gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekeyring-1.0
  gir1.2-goa-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-0.10 gir1.2-gstreamer-1.0 gir1.2-gtk-2.0 gir1.2-gtk-3.0
  gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-indicate-0.7
  gir1.2-json-1.0 gir1.2-messagingmenu-1.0 gir1.2-networkmanager-1.0
  gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0
  gir1.2-rb-3.0 gir1.2-secret-1 gir1.2-signon-1.0 gir1.2-soup-2.4
  gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-udisks-2.0
  gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0
  gkbd-capplet gksu glib-networking glib-networking-services gnome-bluetooth
  gnome-calculator gnome-contacts gnome-control-center gnome-disk-utility
  gnome-font-viewer gnome-icon-theme gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-media
  gnome-menus gnome-mines gnome-nettool gnome-online-accounts gnome-orca
  gnome-power-manager gnome-screensaver gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-settings-daemon
  gnome-settings-daemon-schemas gnome-sudoku gnome-system-log
  gnome-system-monitor gnome-terminal gnome-terminal-data
  gnome-themes-standard gnome-user-guide gnome-user-share gnome-video-effects
  gnomine gnupg gparted gpgv grep groff-base grooveoff growisofs grub-common
  grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
  gsettings-desktop-schemas gsettings-ubuntu-schemas gstreamer0.10-alsa
  gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gconf
  gstreamer0.10-nice gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter
  gstreamer1.0-fluendo-mp3 gstreamer1.0-libav gstreamer1.0-nice
  gstreamer1.0-plugins-bad gstreamer1.0-plugins-bad-faad
  gstreamer1.0-plugins-bad-videoparsers gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good
  gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-tools
  gstreamer1.0-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gtk3-engines-unico gucharmap guile-1.8-libs guile-2.0-libs gvfs
  gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs
  gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter gzip handbrake hardening-includes hddtemp hdparm
  hostname hplip hplip-data hud humanity-icon-theme hunspell-en-us hwdata
  hyphen-en-us i965-va-driver ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table
  icoutils ifupdown im-config indicator-application indicator-appmenu
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-multiload indicator-power indicator-printers indicator-sensors
  indicator-session indicator-sound info init-system-helpers initramfs-tools
  initramfs-tools-bin initscripts inputattach insserv install-info
  intel-gpu-tools intltool-debian iproute iproute2 iptables iputils-arping
  iputils-ping iputils-tracepath irqbalance isc-dhcp-client isc-dhcp-common iw
  katepart kbd kde-runtime kde-runtime-data kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools kerneloops-daemon keyboard-configuration kmod
  kubuntu-debug-installer landscape-client-ui-install language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector-common language-selector-gnome laptop-detect less
  lib32gcc1 liba52-0.7.4 libaa1 libaacs0 libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0
  libaccounts-qt5-1 libaccountsservice0 libacl1 libalgorithm-c3-perl
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libapparmor-perl libapparmor1 libappindicator1 libappindicator3-1
  libapt-inst1.5 libapt-pkg-perl libapt-pkg4.12 libarchive-extract-perl
  libarchive-zip-perl libarchive13 libart-2.0-2 libasan0 libasan1
  libasn1-8-heimdal libasound2 libasound2-plugins libaspell15 libasprintf-dev
  libasprintf0c2 libass5 libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatkmm-1.6-1 libatm1 libatomic1
  libatspi2.0-0 libattica0.4 libattr1 libaudio2 libaudit1 libauthen-sasl-perl
  libautodie-perl libav-tools libavahi-client3 libavahi-common3 libavahi-core7
  libavahi-glib1 libavahi-gobject0 libavahi-ui-gtk3-0 libavc1394-0
  libavcodec-extra-53 libavcodec56 libavdevice55 libavfilter5 libavformat53
  libavformat56 libavresample2 libavutil-extra-51 libavutil52 libavutil54
  libbabeltrace-ctf1 libbabeltrace1 libbaloocore4 libbaloofiles4
  libbalooqueryparser4 libbaloowidgets4 libbalooxapian4 libbamf3-2
  libbasicusageenvironment0 libbind9-90 libblas3 libblkid1 libbluetooth3
  libbluray1 libboost-date-time1.55.0 libboost-filesystem1.55.0
  libboost-iostreams1.55.0 libboost-system1.55.0 libbrasero-media3-1
  libbrlapi0.6 libbsd0 libburn4 libbz2-1.0 libc-bin libc-dev-bin libc6
  libc6-dbg libc6-dev libc6-i386 libcaca0 libcairo-gobject2 libcairo-perl
  libcairo2 libcairomm-1.0-1 libcamel-1.2-49 libcanberra-gtk-module
  libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module
  libcanberra-pulse libcanberra0 libcap-ng0 libcap2 libcap2-bin libcdaudio1
  libcddb2 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0
  libcdr-0.1-1 libcgi-fast-perl libcgi-pm-perl libcgmanager0 libcheese-gtk23
  libcheese7 libchromaprint0 libcilkrts5 libck-connector0
  libclass-accessor-perl libclass-c3-perl libclass-c3-xs-perl libclone-perl
  libcloog-isl4 libcloog-ppl1 libclucene-contribs1 libclucene-core1
  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-pango20 libcogl-path20 libcogl20 libcolamd2.8.0 libcolord-gtk1
  libcolord1 libcolord2 libcolorhug2 libcolumbus1 libcomerr2 libcompizconfig0
  libcpan-meta-perl libcrack2 libcroco3 libcrypt-passwdmd5-perl libcryptsetup4
  libcrystalhd3 libcuda1-331-updates libcups2 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls
  libcurl3-nss libcwidget3 libdaemon0 libdata-optlist-perl
  libdata-section-perl libdatrie1 libdb5.1 libdb5.3 libdbus-1-3
  libdbus-glib-1-2 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4
  libdbusmenu-qt2 libdbusmenu-qt5 libdc1394-22 libdca0 libdconf-dbus-1-0
  libdconf-qt0 libdconf1 libdebconfclient0 libdecoration0 libdee-1.0-4
  libdevmapper-event1.02.1 libdevmapper1.02.1 libdigest-hmac-perl
  libdirac-encoder0 libdirectfb-1.2-9 libdiscid0 libdjvulibre21
  libdlrestrictions1 libdmapsharing-3.0-2 libdns100 libdotconf0 libdotconf1.0
  libdpkg-perl libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libdv4
  libdvbpsi9 libdvdnav4 libdvdread4 libebackend-1.2-7 libebml4 libebook-1.2-14
  libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libedit2 libegl1-mesa
  libegl1-mesa-drivers libelf1 libelfg0 libemail-valid-perl libenca0
  libenchant1c2a libencode-locale-perl libepoxy0 libept1.4.12 libepub0
  libespeak1 libestr0 libevdev2 libevdocument3-4 libevent-2.0-5 libevview3-3
  libexempi3 libexif12 libexiv2-13 libexpat1 libexttextcat-2.0-0 libfaac0
  libfaad2 libfakeroot libfarstream-0.1-0 libfarstream-0.2-2 libfcgi-perl
  libffi6 libffms2-3 libfftw3-double3 libfftw3-single3 libfile-basedir-perl
  libfile-copy-recursive-perl libfile-desktopentry-perl libfile-fcntllock-perl
  libfile-listing-perl libfile-mimeinfo-perl libflac8 libflite1 libfluidsynth1
  libfolks-eds25 libfolks-telepathy25 libfolks25 libfont-afm-perl
  libfontconfig1 libfontembed1 libfontenc1 libframe6
  libfreerdp-plugins-standard libfreerdp1 libfreetype6 libfribidi0 libfs6
  libfuse2 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.7-dev libgcc-4.8-dev libgcc-4.9-dev libgcc1 libgck-1-0 libgconf-2-4
  libgconf2-4 libgconf2.0-cil libgcr-3-1 libgcr-base-3-1 libgcr-ui-3-1
  libgcrypt11 libgcrypt20 libgd3 libgdata13 libgdata19 libgdbm3 libgdiplus
  libgdk-pixbuf2.0-0 libgee-0.8-2 libgee2 libgeis1 libgeoclue0 libgeoip1
  libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgirepository-1.0-1
  libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglade2.0-cil
  libglapi-mesa libgles1-mesa libgles2-mesa libglew1.10 libglewmx1.10
  libglib-perl libglib2.0-0 libglib2.0-bin libglib2.0-cil libglibmm-2.4-1c2a
  libglu1-mesa libgme0 libgmime-2.6-0 libgmp10 libgmpxx4ldbl
  libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-10
  libgnome-keyring0 libgnome-media-profiles-3.0-0 libgnome-menu-3-0
  libgnome-menu2 libgnome2-common libgnomekbd-common libgnomekbd8
  libgnutls-deb0-28 libgnutls-openssl27 libgnutls26 libgoa-1.0-0b
  libgoa-backend-1.0-1 libgomp1 libgpac3 libgpg-error0 libgpgme11 libgphoto2-6
  libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3
  libgrilo-0.2-1 libgrip0 libgroupsock1 libgs9 libgsettings-qt1 libgsm1
  libgssapi-krb5-2 libgssapi3-heimdal libgssdp-1.0-3
  libgstreamer-plugins-bad0.10-0 libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-cil libgtkglext1 libgtkmm-2.4-1c2a libgtkmm-3.0-1
  libgtksourceview-3.0-1 libgtop2-10 libgucharmap-2-90-7 libgudev-1.0-0
  libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2 libgutenprint2 libgweather-3-6
  libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b
  libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal libhogweed2
  libhpmud0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhud2 libhunspell-1.3-0 libhx509-5-heimdal
  libhyphen0 libibus-1.0-5 libical1 libice6 libicu48 libicu52 libidl-common
  libidl0 libidn11 libido3-0.1-0 libiec61883-0 libieee1284-3 libijs-0.35
  libilmbase6 libimobiledevice4 libindicate-gtk3 libindicate5 libindicator3-7
  libindicator7 libinput0 libio-html-perl libio-pty-perl
  libio-socket-inet6-perl libio-socket-ssl-perl libio-string-perl
  libipc-run-perl libipc-system-simple-perl libisc95 libisccc90 libisccfg90
  libisl10 libiso9660-8 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1
  libjavascriptcoregtk-3.0-0 libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8
  libjson-c2 libjson-glib-1.0-0 libjson0 libjte1 libk5crypto3
  libkactivities-bin libkactivities6 libkate1 libkatepartinterfaces4
  libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkeyutils1 libkfile4
  libkfilemetadata4 libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libkmod2 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common
  libkonq5abi1 libkparts4 libkpathsea6 libkpty4 libkrb5-26-heimdal libkrb5-3
  libkrb5support0 libkrosscore4 libktexteditor4 libkubuntu0 libkxmlrpcclient4
  liblangtag1 liblcms1 liblcms2-2 liblcms2-utils libldap-2.4-2 libldb1
  liblightdm-gobject-1-0 liblinear-tools liblinear1 liblircclient0
  liblist-moreutils-perl liblivemedia23 libllvm3.0 libllvm3.5
  liblocale-gettext-perl liblockfile-bin liblockfile1 liblog-message-perl
  liblog-message-simple-perl liblouis2 liblsan0 libltdl7 liblua5.1-0
  liblua5.2-0 liblvm2app2.2 liblwp-mediatypes-perl liblwp-protocol-https-perl
  liblwres90 liblzma5 liblzo2-2 libmad0 libmagic1 libmailtools-perl
  libmatroska6 libmbim-glib0 libmeanwhile1 libmessaging-menu0
  libmetacity-private1 libmhash2 libmimic0 libminiupnpc8 libmirclient8
  libmirclient8driver-mesa libmircommon2 libmission-control-plugins0
  libmjpegutils-2.1-0 libmm-glib0 libmms0 libmng1 libmnl0 libmodplug1
  libmodule-build-perl libmodule-pluggable-perl libmodule-signature-perl
  libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-corlib4.5-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-security4.0-cil
  libmono-system-configuration4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libmount1 libmp3lame0 libmpc2 libmpc3 libmpcdec6
  libmpdec2 libmpeg2-4 libmpeg2encpp-2.1-0 libmpfr4 libmpg123-0
  libmplex2-2.1-0 libmro-compat-perl libmspub-0.1-1 libmtdev1 libmtp-runtime
  libmtp9 libmusicbrainz3-6 libmythes-1.2-0 libnatpmp1 libnautilus-extension1a
  libncurses5 libncursesw5 libneon27-gnutls libnet-dns-perl
  libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnet-smtp-ssl-perl
  libnet-ssleay-perl libnetfilter-conntrack3 libnettle4 libnewt0.52
  libnfnetlink0 libnice10 libnih-dbus1 libnih1 libnl-3-200 libnl-genl-3-200
  libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk0 libnm-util2
  libnotify-bin libnotify4 libnspr4 libnspr4-0d libnss-mdns libnss3 libnss3-1d
  libnss3-nssdb libntdb1 libntrack-qt4-1 libntrack0 libnuma1 libnux-4.0-0
  liboauth0 libofa0 libogg0 libopenal1 libopencc1 libopencore-amrnb0
  libopencore-amrwb0 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libopenexr6
  libopenjpeg2 libopenjpeg5 libopenobex1 libopenvg1-mesa libopts25 libopus0
  liborbit-2-0 liborbit2 liborc-0.4-0 liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libp11-kit-gnome-keyring libp11-kit0
  libpackage-constants-perl libpackagekit-glib2-16 libpam-cap
  libpam-ck-connector libpam-freerdp libpam-gnome-keyring libpam-modules
  libpam-modules-bin libpam-runtime libpam-systemd libpam0g libpango-1.0-0
  libpango-perl libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1
  libparams-util-perl libparse-debianchangelog-perl libparted-fs-resize0
  libparted2 libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1
  libpeas-1.0-0 libperl5.20 libperlio-gzip-perl libphonon4 libpipeline1
  libpixman-1-0 libplasma3 libplist1 libplist2 libplymouth2 libplymouth4
  libpng12-0 libpocketsphinx1 libpod-latex-perl libpod-readme-perl
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0
  libpolkit-qt-1-1 libpoppler-glib8 libpoppler-qt4-4 libpoppler46 libpopt0
  libportaudio2 libpostproc52 libppl-c4 libppl13 libprocps3 libprotobuf7
  libprotobuf8 libprotoc7 libprotoc8 libproxy-tools libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpth20
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libpwquality1 libpython-stdlib libpython2.7 libpython2.7-stdlib
  libpython3-stdlib libpython3.4 libpython3.4-minimal libpython3.4-stdlib
  libpyzy-1.0-0 libqapt2 libqapt2-runtime libqca2 libqjson0 libqmi-glib1
  libqmi-proxy libqmobipocket1 libqpdf13 libqt4-core libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-gui libqt4-help libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5
  libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5
  libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libqtassistantclient4 libqtbamf1 libqtcore4
  libqtdbus4 libqtdee2 libqtgconf1 libqtgui4 libqtwebkit4 libquadmath0
  libquvi7 libraptor2-0 librarian0 librasqal3 libraw10 libraw1394-11 librdf0
  libreadline5 libreadline6 libregexp-common-perl
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-writer libresid-builder0c2a librest-0.7-0 librevenge-0.0-0
  librhythmbox-core8 libroken18-heimdal librsvg2-2 librsvg2-common librsync1
  librtmp1 libruby2.1 libsamplerate0 libsane libsane-hpaio libsasl2-2
  libsasl2-modules libsasl2-modules-db libsbc1 libschroedinger-1.0-0
  libsdl-image1.2 libsdl1.2debian libsecret-1-0 libselinux1 libsemanage1
  libsensors4 libsepol1 libsgutils2-2 libshine3 libshout3 libsidplay1
  libsidplay2 libsigc++-2.0-0c2a libsignon-extension1 libsignon-glib1
  libsignon-plugins-common1 libsignon-qt5-1 libslang2 libslp1 libslv2-9 libsm6
  libsmartcols1 libsmbclient libsndfile1 libsnmp30 libsocket6-perl
  libsoftware-license-perl libsolid4 libsonic0 libsoundtouch0
  libsoup-gnome2.4-1 libsoup2.4-1 libspandsp2 libspectre1 libspeechd2
  libspeex1 libspeexdsp1 libsphinxbase1 libspice-server1 libsqlite3-0 libsrtp0
  libss2 libssh-4 libssl1.0.0 libstartup-notification0 libstdc++6
  libstreamanalyzer0 libstreams0 libsub-exporter-perl libsub-identify-perl
  libsub-install-perl libsub-name-perl libswitch-perl libswscale2 libswscale3
  libsysfs2 libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libt1-5
  libtag1-vanilla libtag1c2a libtalloc2 libtasn1-3 libtasn1-6 libtbb2
  libtcl8.6 libtdb1 libtelepathy-farstream2 libtelepathy-farstream3
  libtelepathy-glib0 libtelepathy-logger3 libterm-ui-perl libtevent0
  libtext-charwidth-perl libtext-iconv-perl libtext-levenshtein-perl
  libtext-soundex-perl libtext-template-perl libtext-wrapi18n-perl libthai0
  libtheora0 libthreadweaver4 libthumbnailer0 libtiff4 libtiff5
  libtimedate-perl libtimezonemap1 libtinfo5 libtk8.6 libtotem-plparser17
  libtotem-plparser18 libtotem0 libts-0.0-0 libtsan0 libtwolame0
  libtxc-dxtn-s2tc0 libubsan0 libudev1 libudisks2-0 libufe-xidgetter0
  libunique-3.0-0 libunistring0 libunity-2d-private0 libunity-action-qt1
  libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-misc4 libunity-protocol-private0
  libunity-settings-daemon1 libunity-webapps0 libunity9 libunityvoice1
  libupnp6 libupower-glib1 libupstart1 liburi-perl liburl-dispatcher1
  libusageenvironment1 libusb-0.1-4 libusb-1.0-0 libusbmuxd2 libustr-1.0-1
  libutempter0 libuuid-perl libuuid1 libv4l-0 libv4lconvert0 libva-drm1
  libva-x11-1 libva1 libvcdinfo0 libvdpau1 libvisio-0.1-1 libvisual-0.4-0
  libvisual-0.4-plugins libvlc5 libvlccore8 libvncclient0 libvncserver0
  libvo-aacenc0 libvo-amrwbenc0 libvorbis0a libvorbisenc2 libvorbisfile3
  libvpx1 libvte-2.90-9 libwacom2 libwavpack1 libwayland-client0
  libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0
  libwebkitgtk-3.0-0 libwebp5 libwebpmux1 libwhoopsie-preferences0
  libwhoopsie0 libwildmidi1 libwind0-heimdal libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck22 libwpd-0.10-10 libwpd-0.9-9 libwpg-0.2-2 libwpg-0.3-3
  libwps-0.3-3 libwrap0 libwww-perl libwww-robotrules-perl libx11-6
  libx11-xcb1 libx264-123 libx264-142 libx86-1 libxapian22 libxatracker1
  libxatracker2 libxau6 libxaw7 libxcb-composite0 libxcb-dri2-0 libxcb-dri3-0
  libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0
  libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-sync1 libxcb-util0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxcb1
  libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3
  libxfont1 libxft2 libxi6 libxinerama1 libxkbcommon-x11-0 libxkbcommon0
  libxkbfile1 libxklavier16 libxml2 libxml2-utils libxmu6 libxmuu1 libxp6
  libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1 libxss1
  libxt6 libxtables10 libxtst6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1
  libxxf86vm1 libyajl2 libyaml-0-2 libyaml-tiny-perl libyelp0 libzbar0
  libzeitgeist-1.0-1 libzeitgeist-2.0-0 libzephyr4 libzip2 libzvbi0
  light-themes lightdm lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure lintian linux-headers-3.11.0-14
  linux-headers-3.11.0-14-generic linux-headers-3.11.0-15
  linux-headers-3.11.0-15-generic linux-headers-3.11.0-17
  linux-headers-3.11.0-17-generic linux-headers-3.11.0-18
  linux-headers-3.11.0-18-generic linux-headers-3.11.0-20
  linux-headers-3.11.0-20-generic linux-headers-3.11.0-26
  linux-headers-3.11.0-26-generic linux-headers-3.13.0-36
  linux-headers-3.13.0-36-generic linux-headers-3.13.0-38
  linux-headers-3.13.0-38-generic linux-headers-3.16.0-25
  linux-headers-3.16.0-25-generic linux-headers-3.16.0-26
  linux-headers-3.16.0-26-generic linux-headers-generic
  linux-image-3.11.0-14-generic linux-image-3.11.0-15-generic
  linux-image-3.11.0-17-generic linux-image-3.11.0-18-generic
  linux-image-3.11.0-20-generic linux-image-3.11.0-26-generic
  linux-image-3.13.0-37-generic linux-image-3.13.0-38-generic
  linux-image-3.13.0-40-generic linux-image-3.16.0-25-generic
  linux-image-3.16.0-26-generic linux-image-3.5.0-31-generic
  linux-image-3.8.0-33-generic linux-image-extra-3.11.0-14-generic
  linux-image-extra-3.11.0-15-generic linux-image-extra-3.11.0-17-generic
  linux-image-extra-3.11.0-18-generic linux-image-extra-3.11.0-20-generic
  linux-image-extra-3.11.0-26-generic linux-image-extra-3.13.0-37-generic
  linux-image-extra-3.13.0-40-generic linux-image-extra-3.16.0-25-generic
  linux-image-extra-3.16.0-26-generic linux-image-extra-3.5.0-31-generic
  linux-image-extra-3.8.0-33-generic linux-image-generic linux-sound-base
  lm-sensors locales lockfile-progs login logrotate lp-solve lsb-release lshw
  lsof ltrace mahjongg make makedev man-db mawk mcp-account-manager-uoa
  media-player-info memtest86+ metacity metacity-common mlocate modemmanager
  module-init-tools mono-4.0-gac mono-gac mono-runtime mono-runtime-common
  mono-runtime-sgen mount mountall mousetweaks mscompress mtools mtr-tiny
  multiarch-support myspell-en-au myspell-en-gb myspell-en-za mythes-en-us
  nano nautilus nautilus-data nautilus-sendto nautilus-share ncurses-bin ndiff
  net-tools netcat-openbsd network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome nmap notify-osd ntfs-3g
  ntfs-config ntp ntpdate ntrack-module-libnl-0 nux-tools nvidia-331-updates
  nvidia-331-updates-uvm nvidia-common nvidia-opencl-icd-331-updates
  nvidia-prime nvidia-settings obex-data-server obexd-client
  ocl-icd-libopencl1 onboard onboard-data oneconf oneconf-common
  openoffice.org-hyphenation openprinting-ppds openssh-client openssl
  os-prober overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3
  oxideqt-codecs-extra p11-kit p11-kit-modules p7zip-full parted passwd patch
  patchutils pavucontrol pciutils pcmciautils perl perl-base perl-modules
  phonon phonon-backend-gstreamer pkg-config plainbox-provider-checkbox
  plainbox-provider-resource-generic plasma-scriptengine-javascript plymouth
  plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
  policykit-1 policykit-1-gnome poppler-data poppler-utils popularity-contest
  ppp pppconfig pppoeconf pptp-linux printer-driver-brlaser
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common
  printer-driver-gutenprint printer-driver-hpcups printer-driver-hpijs
  printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp
  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix procps protobuf-compiler psmisc pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python python-appindicator python-apport python-apt
  python-apt-common python-aptdaemon python-aptdaemon.gtk3widgets python-cairo
  python-characteristic python-chardet python-commandnotfound
  python-compizconfig python-configglue python-crypto python-cups
  python-dateutil python-dbus python-debian python-debtagshw python-defer
  python-dirspec python-egenix-mxdatetime python-egenix-mxtools python-gconf
  python-gdbm python-gi python-gi-cairo python-glade2 python-gnomekeyring
  python-gnupginterface python-gobject python-gobject-2 python-gst0.10
  python-gtk2 python-httplib2 python-ibus python-idna python-imaging
  python-keyring python-launchpadlib python-lazr.restfulclient python-lazr.uri
  python-ldb python-libproxy python-libxml2 python-lockfile python-lxml
  python-mako python-markupsafe python-minimal python-notify python-ntdb
  python-oauth python-oauthlib python-oneconf python-openssl python-pam
  python-pexpect python-pil python-piston-mini-client python-pkg-resources
  python-problem-report python-protobuf python-pyasn1 python-pyasn1-modules
  python-pyatspi python-pyatspi2 python-pycurl python-pyinotify python-qt4
  python-qt4-dbus python-renderpm python-reportlab python-reportlab-accel
  python-samba python-secretstorage python-serial python-service-identity
  python-simplejson python-sip python-six python-smbc
  python-software-properties python-talloc python-tdb python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web
  python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol
  python-virtkey python-wadllib python-xapian python-xdg python-xkit
  python-zeitgeist python-zope.interface python2.7 python2.7-minimal python3
  python3-apport python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet
  python3-checkbox python3-checkbox-ng python3-checkbox-support
  python3-commandnotfound python3-crypto python3-cups python3-cupshelpers
  python3-dbus python3-debian python3-defer python3-dirspec
  python3-distupgrade python3-feedparser python3-gdbm python3-gi
  python3-gi-cairo python3-httplib2 python3-louis python3-lxml python3-mako
  python3-markupsafe python3-minimal python3-oauthlib python3-oneconf
  python3-piston-mini-client python3-pkg-resources python3-plainbox
  python3-problem-report python3-pyatspi python3-pycurl python3-pyparsing
  python3-requests python3-six python3-smbc python3-software-properties
  python3-speechd python3-uno python3-update-manager python3-urllib3
  python3-xdg python3-xkit python3.4 python3.4-minimal qapt-batch qdbus
  qml-module-qtgraphicaleffects qml-module-qtquick-dialogs
  qml-module-qtquick-localstorage qml-module-qtquick-privatewidgets
  qml-module-qtquick-window2 qml-module-qtquick2 qml-module-qtwebkit qpdf
  qt-at-spi qtchooser qtdeclarative5-accounts-plugin
  qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-ubuntu-web-plugin
  qtdeclarative5-unity-action-plugin qtdeclarative5-window-plugin radeontool
  rarian-compat readline-common realmd remmina remmina-plugin-rdp
  remmina-plugin-vnc remote-login-service rename resolvconf rfkill rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone rsync rsyslog rtkit ruby ruby2.1 samba-common
  samba-common-bin samba-libs sane-utils screen-resolution-extra seahorse sed
  session-migration sessioninstaller sgml-base sgml-data shared-mime-info
  shotwell shotwell-common signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signon-ui-x11 signond simple-scan smbclient
  sni-qt software-center software-center-aptdaemon-plugins
  software-properties-common software-properties-gtk speech-dispatcher
  speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert steam-launcher
  strace sudo synaptic sysinfo syslinux syslinux-legacy
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev systemd systemd-shim sysv-rc sysvinit-utils
  t1utils tar tcl tcl8.6 tcpd tcpdump telepathy-gabble telepathy-haze
  telepathy-idle telepathy-indicator telepathy-logger
  telepathy-mission-control-5 telepathy-salut telnet thermald
  thin-client-config-agent thunderbird thunderbird-globalmenu
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
  time tk tk8.6 toshset totem totem-common totem-mozilla totem-plugins
  transmageddon transmission-gtk ttf-mscorefonts-installer tzdata
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-minimal ubuntu-mono
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-session
  ubuntu-settings ubuntu-sso-client ubuntu-sso-client-qt ubuntu-standard
  ubuntu-system-service ubuntu-ui-toolkit-theme ucf udev udisks udisks2 ufw
  unattended-upgrades unity unity-2d unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-asset-pool unity-control-center
  unity-control-center-signon unity-greeter unity-gtk-module-common
  unity-gtk2-module unity-gtk3-module unity-lens-applications unity-lens-files
  unity-lens-music unity-lens-photos unity-lens-video unity-schemas
  unity-scope-audacious unity-scope-calculator unity-scope-chromiumbookmarks
  unity-scope-clementine unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-gmusicbrowser
  unity-scope-gourmet unity-scope-guayadeque unity-scope-home
  unity-scope-manpages unity-scope-musicstores unity-scope-musique
  unity-scope-openclipart unity-scope-texdoc unity-scope-tomboy
  unity-scope-video-remote unity-scope-virtualbox unity-scope-yelp
  unity-scope-zotero unity-services unity-settings-daemon unity-voice-service
  unity-webapps-common unity-webapps-qml unity-webapps-service uno-libs3 unrar
  unzip update-inetd update-manager update-manager-core update-notifier
  update-notifier-common upower upstart upstart-bin ure ureadahead
  usb-creator-common usb-creator-gtk usb-modeswitch usbmuxd usbutils
  util-linux uuid-runtime va-driver-all vbetool vdpau-va-driver vim-common
  vim-tiny vino vlc vlc-nox vlc-plugin-notify vlc-plugin-samba wamerican
  wbritish webaccounts-extension-common webapp-container webbrowser-app wget
  whiptail whois whoopsie whoopsie-preferences wireless-tools wodim
  wpasupplicant x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils
  x11-xkb-utils x11-xserver-utils x264 xauth xbrlapi xdg-user-dirs
  xdg-user-dirs-gtk xdiagnose xfonts-base xfonts-encodings xfonts-mathml
  xfonts-scalable xfonts-utils xinit xinput xml-core xorg xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware xterm xul-ext-ubufox xul-ext-unity
  xul-ext-webaccounts xul-ext-websites-integration xz-utils yelp zeitgeist
  zeitgeist-core zeitgeist-datahub zenity zip zlib1g
The following NEW packages will be installed:
  libc6:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386
  libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386
  libgcc1:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libllvm3.5:i386 libpciaccess0:i386 libpcre3:i386 libselinux1:i386
  libstdc++6:i386 libtinfo5:i386 libudev1:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxshmfence1:i386
  libxxf86vm1:i386 multiarch-support:i386 zlib1g:i386
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libapt-pkg4.12 (due to apt) libc6 (due to apt) libgcc1 (due to apt)
  libstdc++6 (due to apt) gnupg (due to apt) base-files base-passwd
  libdebconfclient0 (due to base-passwd) bash debianutils (due to bash) dash
  (due to bash) libtinfo5 (due to bash) bsdutils libsystemd-journal0 (due to
  bsdutils) coreutils libacl1 (due to coreutils) libattr1 (due to coreutils)
  libselinux1 (due to coreutils) dpkg (due to dash) diffutils libbz2-1.0 (due
  to dpkg) liblzma5 (due to dpkg) zlib1g (due to dpkg) tar (due to dpkg)
  e2fsprogs e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs)
  libcomerr2 (due to e2fsprogs) libss2 (due to e2fsprogs) libuuid1 (due to
  e2fsprogs) util-linux (due to e2fsprogs) findutils grep install-info (due to
  grep) gzip hostname libc-bin libcap2 (due to libc-bin) login libpam0g (due
  to login) libpam-runtime (due to login) libpam-modules (due to login) mount
  libmount1 (due to mount) libsmartcols1 (due to mount) ncurses-bin perl-base
  sed initscripts (due to util-linux) tzdata (due to util-linux) libncurses5
  (due to util-linux) libslang2 (due to util-linux)
0 upgraded, 37 newly installed, 2156 to remove and 0 not upgraded.
Need to get 14.3 MB/18.6 MB of archives.
After this operation, 6,130 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 
```


It asks me to remove 2156 packages. No way! I have done: 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

And I don't held any broken packages.

My sources list should be ok

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu utopic main restricted
deb-src http://archive.ubuntu.com/ubuntu utopic restricted multiverse main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu utopic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu utopic-updates restricted multiverse main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu utopic universe
deb http://archive.ubuntu.com/ubuntu utopic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu utopic multiverse
deb http://archive.ubuntu.com/ubuntu utopic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu utopic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu utopic-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu utopic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu utopic-security restricted multiverse main universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu utopic-security universe
deb http://archive.ubuntu.com/ubuntu utopic-security multiverse

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu utopic main
deb-src http://extras.ubuntu.com/ubuntu utopic main
deb http://archive.ubuntu.com/ubuntu utopic-proposed multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu utopic-proposed multiverse universe main restricted #Added by software-properties
```



How I can solve this issue depedency issue? I have tested both binary nVidia drivers and the same thing. nVidia driver can be installed just fine. I don't got any issues with that.

---

### Post by j0sk on 2014-12-09
Ok, I was able to fix it using the aptitude but after that this libc6:i386 is held back. I know the aptitude is not the right solution so if you know what is the reason for this dependency hell please tell me. If I try to update that libc6:i386 it will remove all those 2156 packages.

> sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libc6:i386
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


---

### Post by j0sk on 2014-12-09
Solved, I found that proposed repository was enabled. I disabled that and purge removed all the nvidia files:

sudo apt-get remove --purge nvidia-* 

Then I installed nvidia binary driver again and everything is working now like should be.

---

