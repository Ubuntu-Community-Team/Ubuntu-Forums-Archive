---
title: "On upgrade to 12.10 from 12.04 - E: Internal Error, No file name for zlib1g"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by jjmatt on 2012-11-03
I just started the upgrade to 12.10 from 12.04 (64 bit) and about 10% of the way in I started getting this error:

> E: Internal Error, No file name for zlib1g


Then I tried the following:

> $ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libatk-adaptor-schemas libebook-1.2-12 libedata-book-1.2-11
  libedataserverui-3.0-1 libevince3-3 libexttextcat0 libgnome-desktop-3-2
  libgwibber-gtk2 libgwibber2 libindicator-messages-status-provider1
  libmetacity-private0 liboverlay-scrollbar-0.2-0
  liboverlay-scrollbar3-0.2-0 libunity-core-5.0-5 libupnp3 nvidia-current
  python-aptdaemon.pkcompat python-speechd ubuntu-sso-client-gtk
  ubuntuone-control-panel-common ubuntuone-control-panel-gtk
  ubuntuone-installer xz-lzma
The following NEW packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-icons account-plugin-identica
  account-plugin-jabber account-plugin-salut account-plugin-twitter
  account-plugin-windows-live account-plugin-yahoo aptitude-common cpp-4.7
  cracklib-runtime dconf-tools diffstat finger fonts-freefont-ttf
  fonts-lklug-sinhala fonts-sil-abyssinica fonts-sil-padauk
  fonts-tibetan-machine freerdp-x11 gcc-4.7 gcc-4.7-base gcc-4.7-base:i386
  gcr gettext gir1.2-accounts-1.0 gir1.2-gdata-0.0 gir1.2-goa-1.0
  gir1.2-messagingmenu-1.0 gir1.2-signon-1.0 gir1.2-syncmenu-0.1
  gnome-contacts gnome-control-center-signon gnome-mahjongg
  hardening-includes intltool-debian libaccount-plugin-1.0-0
  libaccounts-glib0 libaccounts-qt1 libapt-inst1.5 libapt-pkg-perl
  libarchive-zip-perl libasprintf0c2 libatk-adaptor-data
  libatk-bridge2.0-0 libblas3 libboost-date-time1.49.0
  libboost-filesystem1.49.0 libboost-iostreams1.49.0 libboost-regex1.49.0
  libboost-system1.49.0 libcamel-1.2-40 libclone-perl libclutter-1.0-0
  libclutter-1.0-common libclutter-gst-1.0-0 libclutter-gtk-1.0-0
  libcmis-0.2-2 libcogl-common libcogl-pango0 libcogl9 libcrack2 libdconf1
  libdigest-hmac-perl libdpkg-perl libebackend-1.2-5 libebook-1.2-14
  libecal-1.2-15 libedata-book-1.2-15 libedata-cal-1.2-18
  libedataserver-1.2-17 libemail-valid-perl libevdocument3-4 libevview3-3
  libexiv2-12 libexttextcat-1.0-0 libfile-fcntllock-perl libfontembed1
  libgdata2.1-cil libglew1.8 libglewmx1.8 libgnome-bluetooth11
  libgnome-desktop-3-4 libgnomekbd8 libgusb2 libgweather-3-1
  libgwibber-gtk3 libgwibber3 libgxps2 libimobiledevice3 libio-pty-perl
  libipc-run-perl libitm1 libjbig0 libjbig0:i386 libkpathsea6
  liblensfun-data liblensfun0 liblinear-tools liblinear1 liblzma5:i386
  libmagickcore5 libmagickcore5-extra libmagickwand5 libmessaging-menu0
  libmetacity-private0a libmono-data-tds4.0-cil libmono-system-data4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-runtime-serialization4.0-cil
  libmono-system-transactions4.0-cil libmono-system-xml-linq4.0-cil
  libmusicbrainz5-0 libmx-1.0-2 libmx-bin libmx-common libnet-dns-perl
  libnet-domain-tld-perl libnet-ip-perl libnewtonsoft-json4.5-cil
  libnss-winbind libnuma1 libnux-3.0-0 libnux-3.0-common libopus0
  libpam-freerdp libpam-xdg-support libpoppler28 libprocps0 libpwquality1
  libpython3.2 libqjson0 libqpdf8 libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer
  libreoffice-presenter-console librhythmbox-core6 libsecret-1-0
  libsecret-common libsignon-extension1 libsignon-glib1
  libsignon-plugins-common1 libsignon-qt1 libssh2-1 libsync-menu1
  libtaglib2.1-cil libtbb2 libtiff5 libtiff5:i386 libudisks2-0
  libufe-xidgetter0 libunity-core-6.0-5 libunity-protocol-private0
  libunity-webapps0 libupnp6 libusb-1.0-0:i386 libusbmuxd2 libwebp2
  libwhoopsie0 libx264-123 libyajl2 lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure lintian linux-headers-3.5.0-18
  linux-headers-3.5.0-18-generic linux-image-3.5.0-18-generic
  linux-image-extra-3.5.0-18-generic mcp-account-manager-uoa ncurses-term
  nmap overlay-scrollbar-gtk2 overlay-scrollbar-gtk3
  packagekit-backend-aptcc patchutils python-lxml python-six python3
  python3-apport python3-apt python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi
  python3-cairo python3-crypto python3-dbus python3-defer
  python3-distupgrade python3-gdbm python3-gi python3-gi-cairo
  python3-httplib2 python3-louis python3-lxml python3-minimal
  python3-oauthlib python3-pkg-resources python3-problem-report
  python3-pyatspi2 python3-pycurl python3-software-properties
  python3-speechd python3-update-manager python3-virtkey python3-xkit
  python3.2 python3.2-minimal qpdf remote-login-service session-migration
  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password
  signon-ui signond thin-client-config-agent ubuntu-drivers-common
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-settings
  ubuntu-wallpapers-quantal udisks2 unity-lens-gwibber unity-lens-photos
  unity-lens-shopping unity-scope-gdocs unity-webapps-common
  unity-webapps-service xserver-xorg-video-modesetting xul-ext-unity
  xul-ext-websites-integration
The following packages have been kept back:
  nautilus-dropbox unity-scope-musicstores
The following packages will be upgraded:
  accountsservice acl acpi-support acpid activity-log-manager-common
  activity-log-manager-control-center adduser aisleriot alsa-base
  alsa-utils anacron apg app-install-data app-install-data-partner
  apparmor appmenu-gtk appmenu-gtk3 appmenu-qt apport apport-gtk
  apport-symptoms apt apt-transport-https apt-utils apt-xapian-index
  aptdaemon aptdaemon-data aptitude apturl apturl-common aspell aspell-en
  at at-spi2-core avahi-autoipd avahi-daemon avahi-utils bamfdaemon
  banshee banshee-extension-soundmenu baobab base-passwd bash
  bash-completion bc bind9-host binfmt-support binutils bluez bluez-alsa
  bluez-cups bluez-gstreamer brasero brasero-cdrkit brasero-common brltty
  bsdmainutils bsdutils busybox-initramfs busybox-static bzip2 c2esp
  ca-certificates cabextract checkbox checkbox-gtk checkbox-qt colord
  command-not-found command-not-found-data compiz compiz-core compiz-gnome
  compiz-plugins-default compiz-plugins-main-default
  compizconfig-backend-gconf console-setup consolekit coreutils cpio cpp
  cpp-4.6 crda cron cryptsetup cryptsetup-bin cups cups-bsd cups-client
  cups-common cups-driver-gutenprint cups-filters cups-ppdc dash dbus
  dbus-x11 dc dconf-gsettings-backend dconf-service ddclient debconf
  debconf-i18n debianutils deja-dup desktop-file-utils devede
  dictionaries-common diffutils dkms dmidecode dmsetup dnsmasq-base
  dnsutils doc-base dosfstools dpkg duplicity dvd+rw-tools dvdauthor
  e2fslibs e2fsprogs ecryptfs-utils ed eject empathy empathy-common
  enchant eog esound-common espeak espeak-data evince evince-common
  evolution-data-server evolution-data-server-common exiv2 faad fakeroot
  file file-roller findutils firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-en flashplugin-installer
  folks-common fontconfig fontconfig-config fonts-droid
  fonts-horai-umefont fonts-kacst fonts-kacst-one fonts-liberation
  fonts-nanum fonts-opensymbol fonts-thai-tlwg fonts-tlwg-garuda
  fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi
  fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree
  fonts-unfonts-core foo2zjs foomatic-db-compressed-ppds
  foomatic-db-engine foomatic-filters fotoxx ftp fuse fuse-utils gamin
  gbrainy gcalctool gcc gcc-4.6 gcc-4.6-base gcc-4.6-base:i386
  gconf-service gconf-service-backend gconf2 gconf2-common gdb gedit
  gedit-common genisoimage geoclue geoclue-ubuntu-geoip geoip-database
  gettext-base ghostscript ghostscript-cups ghostscript-x ginn
  gir1.2-appindicator3-0.1 gir1.2-atk-1.0 gir1.2-atspi-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk-0.4 gir1.2-dee-1.0
  gir1.2-freedesktop gir1.2-gconf-2.0 gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0
  gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekeyring-1.0
  gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 gir1.2-gtk-2.0
  gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-indicate-0.7
  gir1.2-javascriptcoregtk-3.0 gir1.2-launchpad-integration-3.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0
  gir1.2-soup-2.4 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gksu
  glib-networking glib-networking-common glib-networking-services gmtp
  gnome-accessibility-themes gnome-bluetooth gnome-control-center
  gnome-control-center-data gnome-desktop-data gnome-desktop3-data
  gnome-disk-utility gnome-font-viewer gnome-games-data gnome-icon-theme
  gnome-icon-theme-symbolic gnome-keyring gnome-media gnome-menus
  gnome-nettool gnome-online-accounts gnome-orca gnome-power-manager
  gnome-screensaver gnome-screenshot gnome-search-tool gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-user-share
  gnomine gnupg gparted gpgv grep groff-base growisofs grub-common grub-pc
  grub-pc-bin grub2-common gsettings-desktop-schemas gstreamer0.10-alsa
  gstreamer0.10-ffmpeg gstreamer0.10-gconf gstreamer0.10-nice
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk3-engines-unico
  gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter gzip hdparm hostname hpijs hplip hplip-cups
  hplip-data humanity-icon-theme hwdata ibus ibus-gtk ibus-gtk3
  ibus-pinyin ibus-pinyin-db-android ibus-table icoutils ifupdown
  im-switch imagemagick imagemagick-common indicator-application
  indicator-appmenu indicator-datetime indicator-messages indicator-power
  indicator-printers indicator-session indicator-sound info inputattach
  install-info installation-report intel-gpu-tools iproute iptables
  iputils-arping iputils-ping iputils-tracepath irqbalance isc-dhcp-client
  isc-dhcp-common iso-codes iw java-common jockey-common jockey-gtk kbd
  kerneloops-daemon keyboard-configuration keyutils krb5-locales
  landscape-client-ui-install language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base
  language-selector-common language-selector-gnome launchpad-integration
  less lftp libaa1 libaacs0 libaccountsservice0 libacl1 libao-common
  libao4 libappindicator0.1-cil libappindicator1 libappindicator3-1
  libapt-pkg4.12 libarchive12 libart-2.0-2 libasn1-8-heimdal
  libasn1-8-heimdal:i386 libasound2 libasound2:i386 libasound2-plugins
  libaspell15 libasyncns0 libasyncns0:i386 libatasmart4 libatk-adaptor
  libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatspi2.0-0 libattr1
  libaudio2 libaudiofile1 libavahi-client3 libavahi-client3:i386
  libavahi-common-data libavahi-common-data:i386 libavahi-common3
  libavahi-common3:i386 libavahi-core7 libavahi-glib1 libavahi-gobject0
  libavahi-ui-gtk3-0 libavc1394-0 libbamf0 libbamf3-0 libbind9-80
  libblkid1 libbluetooth3 libbluray1 libbrasero-media3-1 libbrlapi0.5
  libbsd0 libburn4 libbz2-1.0 libcaca0 libcairo-gobject2 libcairo-perl
  libcairo2 libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0
  libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse
  libcanberra0 libcap-ng0 libcap2 libcap2-bin libcdaudio1 libcdio-cdda1
  libcdio-paranoia1 libcdio13 libcdparanoia0 libcdt4 libck-connector0
  libcolord1 libcomerr2 libcomerr2:i386 libcompizconfig0 libcroco3
  libcryptsetup4 libcrystalhd3 libcups2 libcups2:i386 libcupscgi1
  libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3
  libcurl3-gnutls libcurl3-nss libcwidget3 libdaemon0 libdatrie1 libdb5.1
  libdb5.1:i386 libdbus-1-3 libdbus-1-3:i386 libdbus-glib-1-2
  libdbus-glib1.0-cil libdbus1.0-cil libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdbusmenu-qt2 libdc1394-22 libdconf-dbus-1-0
  libdecoration0 libdee-1.0-4 libdevmapper-event1.02.1 libdevmapper1.02.1
  libdirac-encoder0 libdirectfb-1.2-9 libdiscid0 libdjvulibre-text
  libdjvulibre21 libdmapsharing-3.0-2 libdns81 libdotconf1.0 libdrm2
  libdv4 libdvdnav4 libdvdread4 libecryptfs0 libedit2 libelf1 libelf1:i386
  libenca0 libenchant1c2a libencode-locale-perl libept1.4.12 libesd0
  libespeak1 libevent-2.0-5 libexempi3 libexif12 libexif12:i386
  libexttextcat-data libfaad2 libfarstream-0.1-0 libffi6 libffi6:i386
  libfftw3-3 libfile-listing-perl libfile-mimeinfo-perl libflac8
  libflac8:i386 libflite1 libfolks-eds25 libfolks-telepathy25 libfolks25
  libfontconfig1 libfontconfig1:i386 libfontenc1 libframe6
  libfreerdp-plugins-standard libfreerdp1 libfreetype6 libfreetype6:i386
  libfribidi0 libfs6 libfuse2 libgail-3-0 libgail-common libgail18
  libgamin0 libgcc1 libgcc1:i386 libgck-1-0 libgconf-2-4 libgconf2-4
  libgconf2.0-cil libgcr-3-1 libgcr-3-common libgcrypt11 libgcrypt11:i386
  libgd2-xpm libgd2-xpm:i386 libgdata-common libgdata13 libgdbm3
  libgdiplus libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgee2 libgeis1
  libgeoclue0 libgeoip1 libgettextpo0 libgexiv2-1 libgif4 libgif4:i386
  libgirepository-1.0-1 libgkeyfile1.0-cil libgksu2-0 libgl1-mesa-dri
  libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386 libglade2-0
  libglapi-mesa libglib-perl libglib2.0-0 libglib2.0-0:i386 libglib2.0-bin
  libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa
  libglu1-mesa:i386 libgmime-2.6-0 libgmime2.6-cil libgmp10
  libgnome-control-center1 libgnome-keyring-common libgnome-keyring0
  libgnome-media-profiles-3.0-0 libgnome-menu-3-0 libgnome-menu2
  libgnome2-common libgnomekbd-common libgnomevfs2-0 libgnomevfs2-common
  libgnutls26 libgnutls26:i386 libgoa-1.0-0 libgoa-1.0-common libgomp1
  libgpg-error0 libgpg-error0:i386 libgpgme11 libgphoto2-2
  libgphoto2-2:i386 libgphoto2-l10n libgphoto2-port0 libgphoto2-port0:i386
  libgpm2 libgpm2:i386 libgpod-common libgpod4 libgrail5 libgraph4
  libgrip0 libgs9 libgs9-common libgsm1 libgssapi-krb5-2
  libgssapi-krb5-2:i386 libgssapi3-heimdal libgssapi3-heimdal:i386
  libgssdp-1.0-3 libgstreamer-plugins-bad0.10-0
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0 libgstreamer0.10-0:i386 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk-sharp-beans-cil libgtk-vnc-2.0-0 libgtk2-perl
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common
  libgtkmm-2.4-1c2a libgtkmm-3.0-1 libgtksourceview-3.0-0
  libgtksourceview-3.0-common libgtkspell-3-0 libgtkspell0 libgtop2-7
  libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgudev1.0-cil
  libgupnp-1.0-4 libgupnp-igd-1.0-4 libgutenprint2 libgvc5 libgvnc-1.0-0
  libgweather-common libhcrypto4-heimdal libhcrypto4-heimdal:i386
  libheimbase1-heimdal libheimbase1-heimdal:i386 libheimntlm0-heimdal
  libheimntlm0-heimdal:i386 libhpmud0 libhtml-form-perl
  libhtml-parser-perl libhtml-tree-perl libhttp-daemon-perl
  libhttp-date-perl libhttp-message-perl libhunspell-1.3-0
  libhx509-5-heimdal libhx509-5-heimdal:i386 libhyphen0 libibus-1.0-0
  libical0 libice6 libice6:i386 libicu48 libid3tag0 libidl-common libidl0
  libidn11 libido3-0.1-0 libiec61883-0 libieee1284-3 libieee1284-3:i386
  libijs-0.35 libilmbase6 libindicate-gtk3 libindicate5 libindicator3-7
  libindicator7 libio-socket-ssl-perl libisc83 libisccc80 libisccfg82
  libiso9660-8 libisofs6 libiw30 libjack-jackd2-0 libjasper1
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libjbig2dec0
  libjpeg-turbo8 libjpeg-turbo8:i386 libjpeg62 libjs-jquery
  libjson-glib-1.0-0 libjson0 libjson0:i386 libjte1 libk5crypto3
  libk5crypto3:i386 libkeyutils1 libkeyutils1:i386 libkrb5-26-heimdal
  libkrb5-26-heimdal:i386 libkrb5-3 libkrb5-3:i386 libkrb5support0
  libkrb5support0:i386 liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblcms1 liblcms1:i386 liblcms2-2
  libldap-2.4-2 libldap-2.4-2:i386 liblightdm-gobject-1-0 liblircclient0
  libllvm2.9 libllvm3.0 libllvm3.0:i386 libllvm3.1 libllvm3.1:i386
  liblocale-gettext-perl liblockfile-bin liblockfile1 liblouis-data
  liblouis2 liblqr-1-0 libltdl7 libltdl7:i386 liblua5.1-0 liblvm2app2.2
  liblwp-mediatypes-perl liblwp-protocol-https-perl liblwres80 liblzma5
  liblzo2-2 libmagic1 libmailtools-perl libmatroska5 libmeanwhile1
  libmhash2 libminiupnpc8 libmission-control-plugins0 libmms0 libmng1
  libmodplug1 libmono-cairo4.0-cil libmono-corlib4.0-cil
  libmono-csharp4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmono-zeroconf1.0-cil
  libmount1 libmp3lame0 libmpc2 libmpeg2-4 libmpfr4 libmpg123-0
  libmpg123-0:i386 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libmysqlclient18 libmythes-1.2-0 libnatpmp1 libnautilus-extension1a
  libncurses5 libncurses5:i386 libncursesw5 libneon27-gnutls
  libnet-http-perl libnet-ssleay-perl libnetfilter-conntrack3 libnetpbm10
  libnettle4 libnewt0.52 libnfnetlink0 libnice10 libnih-dbus1 libnih1
  libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin
  libnotify0.4-cil libnotify4 libnspr4 libnspr4-0d libnss-mdns libnss3
  libnss3-1d liboauth0 libodbc1 libofa0 libogg0 libogg0:i386
  libopenal-data libopenal1 libopenal1:i386 libopencc1 libopencore-amrnb0
  libopencore-amrwb0 libopencv-core2.3 libopencv-highgui2.3
  libopencv-imgproc2.3 libopenexr6 libopenjpeg2 libopenobex1 liborc-0.4-0
  liborc-0.4-0:i386 libosmesa6 libosmesa6:i386 libp11-kit0
  libp11-kit0:i386 libpackagekit-glib2-14 libpam-cap libpam-ck-connector
  libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime
  libpam-winbind libpam0g libpango-perl libpangomm-1.4-1 libpaper-utils
  libpaper1 libparted0debian1 libpathplan4 libpcap0.8 libpci3
  libpciaccess0 libpciaccess0:i386 libpcre3 libpcre3:i386 libpcsclite1
  libpeas-1.0-0 libpeas-common libperl5.14 libpipeline1 libpixman-1-0
  libplist1 libpng12-0 libpng12-0:i386 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpoppler-glib8 libpopt0
  libportaudio2 libprotobuf7 libprotoc7 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpth20
  libpulse-mainloop-glib0 libpulse0 libpulse0:i386 libpulsedsp
  libpurple-bin libpurple0 libpython2.7 libqt4-dbus libqt4-declarative
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite
  libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns
  libqtassistantclient4 libqtbamf1 libqtcore4 libqtgui4 libqtwebkit4
  libquadmath0 libquicktime2 libquvi-scripts libquvi7 libraptor2-0
  librarian0 librasqal3 libraw1394-11 libraw5 librdf0 libreadline6
  libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us
  libreoffice-impress libreoffice-math libreoffice-style-human
  libreoffice-style-tango libreoffice-writer libresid-builder0c2a
  librest-0.7-0 libroken18-heimdal libroken18-heimdal:i386 librsvg2-2
  librsvg2-common librsync1 librtmp0 libsamplerate0 libsane libsane:i386
  libsane-common libsane-hpaio libsasl2-2 libsasl2-2:i386 libsasl2-modules
  libsasl2-modules:i386 libschroedinger-1.0-0 libsdl-image1.2
  libsdl1.2debian libselinux1 libselinux1:i386 libsensors4 libsgutils2-2
  libshout3 libsidplay2 libsigc++-2.0-0c2a libslang2 libslp1 libslv2-9
  libsm6 libsm6:i386 libsmbclient libsndfile1 libsndfile1:i386
  libsnmp-base libsnmp15 libsocket6-perl libsonic0 libsoundtouch0
  libsoup-gnome2.4-1 libsoup2.4-1 libspandsp2 libspectre1 libspeechd2
  libspeex1 libspeexdsp1 libsqlite3-0 libsqlite3-0:i386 libss2 libssh-4
  libssl1.0.0 libssl1.0.0:i386 libstartup-notification0 libstdc++6
  libstdc++6:i386 libsub-name-perl libsvga1 libsyncdaemon-1.0-1 libsysfs2
  libt1-5 libtag1-vanilla libtag1c2a libtalloc2 libtar0 libtasn1-3
  libtasn1-3:i386 libtdb1 libtelepathy-farstream2 libtelepathy-glib0
  libtelepathy-logger2 libtext-charwidth-perl libtext-iconv-perl
  libthai-data libthai0 libtheora0 libtiff4 libtiff4:i386 libtimezonemap1
  libtinfo5 libtinfo5:i386 libtotem-plparser17 libtotem0 libts-0.0-0
  libtxc-dxtn-s2tc0 libtxc-dxtn-s2tc0:i386 libudev0 libunique-1.0-0
  libunique-3.0-0 libunistring0 libunity-2d-private0 libunity-misc4
  libunity9 libupower-glib1 liburi-perl libusb-0.1-4 libusb-0.1-4:i386
  libusb-1.0-0 libusb-dev libutempter0 libuuid-perl libuuid1 libuuid1:i386
  libv4l-0 libv4l-0:i386 libv4lconvert0 libv4lconvert0:i386 libva-x11-1
  libva1 libvcdinfo0 libvdpau1 libvisual-0.4-0 libvisual-0.4-plugins
  libvlc5 libvlccore5 libvncserver0 libvo-aacenc0 libvo-amrwbenc0
  libvorbis0a libvorbis0a:i386 libvorbisenc2 libvorbisenc2:i386
  libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common libvte-common
  libvte9 libwacom-common libwacom2 libwavpack1 libwbclient0
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libwind0-heimdal libwind0-heimdal:i386
  libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwnck-common
  libwnck22 libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0 libwrap0:i386
  libwww-perl libwxbase2.8-0 libwxgtk2.8-0 libx11-6 libx11-6:i386
  libx11-data libx11-xcb1 libx11-xcb1:i386 libx86-1 libxapian22 libxau6
  libxau6:i386 libxaw7 libxcb-composite0 libxcb-dri2-0 libxcb-glx0
  libxcb-glx0:i386 libxcb-keysyms1 libxcb-randr0 libxcb-render0
  libxcb-shape0 libxcb-shm0 libxcb-util0 libxcb-xv0 libxcb1 libxcb1:i386
  libxcomposite1 libxcomposite1:i386 libxcursor1 libxcursor1:i386
  libxdamage1 libxdamage1:i386 libxdmcp6 libxdmcp6:i386 libxext6
  libxext6:i386 libxfixes3 libxfixes3:i386 libxfont1 libxft2 libxi6
  libxi6:i386 libxinerama1 libxinerama1:i386 libxkbfile1 libxklavier16
  libxml2 libxml2:i386 libxmu6 libxmuu1 libxp6 libxpm4 libxpm4:i386
  libxrandr2 libxrandr2:i386 libxrender1 libxrender1:i386 libxres1
  libxslt1.1 libxslt1.1:i386 libxss1 libxt6 libxt6:i386 libxtst6 libxv1
  libxvidcore4 libxvmc1 libxxf86dga1 libxxf86vm1 libxxf86vm1:i386
  libyaml-tiny-perl libyelp0 libzbar0 libzephyr4 libzvbi-common libzvbi0
  light-themes lightdm linux-firmware linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev linux-sound-base lockfile-progs login
  logrotate lsb-base lsb-release lshw lsof ltrace mahjongg make makedev
  man-db manpages manpages-dev media-player-info memtest86+ mencoder
  metacity metacity-common mime-support min12xxw mkvtoolnix mkvtoolnix-gui
  mlocate mobile-broadband-provider-info modemmanager mono-4.0-gac
  mono-gac mono-runtime mount mousetweaks mpg123 mplayer mscompress mtools
  mtp-tools mtpfs mtr-tiny multiarch-support mysql-common nano nautilus
  nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share
  ncurses-base ncurses-bin net-tools netbase netcat-openbsd netpbm
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notify-osd ntfs-3g ntpdate nux-tools
  nvidia-common obex-data-server obexd-client odbcinst odbcinst1debian2
  onboard oneconf openprinting-ppds openssh-client openssh-server openssl
  os-prober overlay-scrollbar parted passwd patch pciutils pcmciautils
  perl perl-base perl-modules pidgin pidgin-data pidgin-libnotify
  pkg-config plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pnm2ppa
  policykit-1 policykit-1-gnome policykit-desktop-privileges poppler-utils
  powermgmt-base ppp pptp-linux printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-gutenprint printer-driver-hpcups
  printer-driver-hpijs printer-driver-min12xxw printer-driver-pnm2ppa
  printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr
  printer-driver-splix procps protobuf-compiler psmisc ptouch-driver
  pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr
  python python-appindicator python-apport python-apt python-apt-common
  python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-cairo python-crypto python-cups
  python-cupshelpers python-dateutil python-dbus python-dbus-dev
  python-debian python-debtagshw python-defer python-dirspec
  python-egenix-mxdatetime python-egenix-mxtools python-gconf python-gdbm
  python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gpgme python-gst0.10 python-gtk2 python-httplib2
  python-ibus python-imaging python-indicate python-keyring
  python-launchpadlib python-lazr.restfulclient python-libproxy
  python-libxml2 python-mako python-markupsafe python-minimal
  python-notify python-openssl python-packagekit python-pam python-pexpect
  python-piston-mini-client python-pkg-resources python-problem-report
  python-protobuf python-pyatspi2 python-pycurl python-pyinotify
  python-qt4 python-qt4-dbus python-renderpm python-reportlab
  python-reportlab-accel python-serial python-simplejson python-sip
  python-smbc python-software-properties python-support python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web
  python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol
  python-uno python-virtkey python-vte python-webkit python-wnck
  python-xapian python-xdg python-xkit python-zeitgeist
  python-zope.interface python2.7 python2.7-minimal qdbus qt-at-spi
  radeontool rarian-compat rdesktop readline-common remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc resolvconf rfkill rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rsync rsyslog rtkit samba-common samba-common-bin sane-utils
  screen-resolution-extra seahorse sed sensible-utils sessioninstaller
  sgml-base sgml-data shared-mime-info shotwell simple-scan smbclient
  sni-qt software-center software-center-aptdaemon-plugins
  software-properties-common software-properties-gtk speech-dispatcher
  splix ssh ssh-askpass-gnome ssh-import-id sshfs ssl-cert strace sudo
  syslinux syslinux-common system-config-printer-common
  system-config-printer-gnome system-config-printer-udev sysvinit-utils
  tasksel tasksel-data tcpd tcpdump telepathy-gabble telepathy-haze
  telepathy-idle telepathy-indicator telepathy-logger
  telepathy-mission-control-5 telepathy-salut telnet thunderbird
  thunderbird-globalmenu thunderbird-gnome-support tilda time tomboy
  toshset totem totem-common totem-mozilla totem-plugins
  transmission-common transmission-gtk tsconf ttf-droid ttf-freefont
  ttf-kacst-one ttf-liberation ttf-thai-tlwg ttf-ubuntu-font-family
  ttf-umefont ttf-unfonts-core tzdata ubuntu-artwork ubuntu-desktop
  ubuntu-docs ubuntu-keyring ubuntu-minimal ubuntu-mono ubuntu-sso-client
  ubuntu-sso-client-qt ubuntu-standard ubuntu-system-service
  ubuntu-wallpapers ubuntu-wallpapers-precise ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel
  ubuntuone-control-panel-qt ubuntuone-couch ucf udev udisks ufraw-batch
  ufw unattended-upgrades unity unity-2d unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-asset-pool unity-common
  unity-greeter unity-lens-applications unity-lens-files unity-lens-music
  unity-lens-video unity-scope-video-remote unity-services unixodbc
  uno-libs3 unrar unzip update-inetd update-manager update-manager-core
  update-notifier update-notifier-common upower ure ureadahead
  usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data
  usbmuxd usbutils util-linux uuid-runtime vcdimager vim vim-common
  vim-runtime vim-tiny vinagre vino vlc vlc-data vlc-nox vlc-plugin-notify
  vlc-plugin-pulse vorbis-tools wavpack wget whiptail whois whoopsie
  winbind winetricks wireless-tools wodim wpasupplicant x11-apps
  x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils
  x11-xserver-utils xauth xdg-user-dirs xdg-user-dirs-gtk xdiagnose
  xfonts-mathml xfonts-utils xinit xinput xkb-data xml-core xorg
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware xterm xul-ext-ubufox xz-utils yelp yelp-xsl
  zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip
1609 upgraded, 236 newly installed, 23 to remove and 2 not upgraded.
21 not fully installed or removed.
Need to get 0 B/822 MB of archives.
After this operation, 247 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for zlib1g


And

> $ sudo apt-get remove zlib1g 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libblkid1 : Depends: libuuid1 (>= 2.16) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

And finally:

> $ sudo dpkg -r zlib1g 
dpkg: dependency problems prevent removal of zlib1g:
 libid3tag0 depends on zlib1g (>= 1:1.1.4).
 libglib2.0-0 depends on zlib1g (>= 1:1.2.2).
 binutils depends on zlib1g (>= 1:1.2.0).
 libreoffice-core depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 rsyslog depends on zlib1g (>= 1:1.1.4).
 libfontenc1 depends on zlib1g (>= 1:1.1.4).
 libopencv-core2.3 depends on zlib1g (>= 1:1.1.4).
 libreoffice-draw depends on zlib1g (>= 1:1.1.4).
 xfonts-utils depends on zlib1g (>= 1:1.1.4).
 netpbm depends on zlib1g (>= 1:1.1.4).
 util-linux depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 printer-driver-c2esp depends on zlib1g (>= 1:1.1.4).
 libpng12-0 depends on zlib1g (>= 1:1.1.4).
 gstreamer0.10-plugins-good depends on zlib1g (>= 1:1.1.4).
 mplayer depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 vlc depends on zlib1g (>= 1:1.2.3.3.dfsg); however:
  Package zlib1g is to be removed.
 openssh-client depends on zlib1g (>= 1:1.1.4).
 wine1.5-amd64 depends on zlib1g (>= 1:1.1.4).
 libarchive1 depends on zlib1g (>= 1:1.1.4).
 libnss3 depends on zlib1g (>= 1:1.1.4).
 libexiv2-11 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libexiv2-10 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libpciaccess0 depends on zlib1g (>= 1:1.1.4).
 python-imaging depends on zlib1g (>= 1:1.1.4).
 mkvtoolnix depends on zlib1g (>= 1:1.1.4).
 libavformat53 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libgvc5 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libcamel-1.2-29 depends on zlib1g (>= 1:1.1.4).
 libcaca0 depends on zlib1g (>= 1:1.1.4).
 libevince3-3 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 perl depends on zlib1g (>= 1:1.2.3.3.dfsg).
 samba-common-bin depends on zlib1g (>= 1:1.1.4).
 vino depends on zlib1g (>= 1:1.1.4).
 libept1 depends on zlib1g (>= 1:1.1.4).
 dpkg depends on zlib1g (>= 1:1.1.4).
 libjte1 depends on zlib1g (>= 1:1.1.4).
 libgnutls26 depends on zlib1g (>= 1:1.1.4).
 libssh-4 depends on zlib1g (>= 1:1.1.4).
 openssh-server depends on zlib1g (>= 1:1.1.4).
 ufraw-batch depends on zlib1g (>= 1:1.1.4).
 nvidia-current depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libgmime-2.4-2 depends on zlib1g (>= 1:1.1.4).
 libgnomevfs2-0 depends on zlib1g (>= 1:1.1.4).
 mencoder depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libisofs6 depends on zlib1g (>= 1:1.2.0).
 vlc-nox depends on zlib1g (>= 1:1.2.0.2); however:
  Package zlib1g is to be removed.
 libmng1 depends on zlib1g (>= 1:1.1.4).
 libmysqlclient18 depends on zlib1g (>= 1:1.1.4).
 libmysqlclient16 depends on zlib1g (>= 1:1.1.4).
 libcurl3 depends on zlib1g (>= 1:1.1.4).
 libopenexr6 depends on zlib1g (>= 1:1.1.4).
 smbclient depends on zlib1g (>= 1:1.1.4).
 handbrake-gtk depends on zlib1g (>= 1:1.2.3.3.dfsg); however:
  Package zlib1g is to be removed.
 google-chrome-stable depends on zlib1g (>= 1:1.2.3.3.dfsg); however:
  Package zlib1g is to be removed.
 libgmime-2.6-0 depends on zlib1g (>= 1:1.1.4).
 gnupg depends on zlib1g (>= 1:1.1.4).
 libvncserver0 depends on zlib1g (>= 1:1.1.4).
 consolekit depends on zlib1g (>= 1:1.1.4).
 transmission-gtk depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libgs9 depends on zlib1g (>= 1:1.1.4).
 flashplugin-installer depends on zlib1g; however:
  Package zlib1g is to be removed.
 librtmp0 depends on zlib1g (>= 1:1.1.4).
 libtiff4 depends on zlib1g (>= 1:1.1.4).
 python2.7-minimal depends on zlib1g (>= 1:1.2.0).
 genisoimage depends on zlib1g (>= 1:1.1.4).
 usbutils depends on zlib1g (>= 1:1.1.4).
 cups-filters depends on zlib1g (>= 1:1.1.4).
 simple-scan depends on zlib1g (>= 1:1.1.4).
 libarchive12 depends on zlib1g (>= 1:1.1.4).
 libqt4-network depends on zlib1g (>= 1:1.1.4).
 libcups2 depends on zlib1g (>= 1:1.1.4).
 mkvtoolnix-gui depends on zlib1g (>= 1:1.1.4).
 libsmbclient depends on zlib1g (>= 1:1.1.4).
 libwxbase2.8-0 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libneon27-gnutls depends on zlib1g (>= 1:1.1.4).
 libwmf0.2-7 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libcurl3-nss depends on zlib1g (>= 1:1.1.4).
 winbind depends on zlib1g (>= 1:1.1.4).
 libqtcore4 depends on zlib1g (>= 1:1.1.4).
 gcc-4.6 depends on zlib1g (>= 1:1.1.4).
 libreoffice-writer depends on zlib1g (>= 1:1.1.4).
 libept1.4.12 depends on zlib1g (>= 1:1.1.4).
 libtag1-vanilla depends on zlib1g (>= 1:1.1.4).
 libgstreamer-plugins-base0.10-0 depends on zlib1g (>= 1:1.1.4).
 libenchant1c2a depends on zlib1g (>= 1:1.1.4).
 libxfont1 depends on zlib1g (>= 1:1.1.4).
 libapt-pkg4.11 depends on zlib1g (>= 1:1.2.2.3).
 libapt-pkg4.12 depends on zlib1g (>= 1:1.2.2.3).
 libqt4-svg depends on zlib1g (>= 1:1.1.4).
 libwebkitgtk-3.0-0 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libmagic1 depends on zlib1g (>= 1:1.1.4).
 libboost-iostreams1.46.1 depends on zlib1g (>= 1:1.1.4).
 libquicktime2 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libdmapsharing-3.0-2 depends on zlib1g (>= 1:1.1.4).
 gnome-system-log depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 libssl0.9.8 depends on zlib1g (>= 1:1.1.4).
 libqt3-mt depends on zlib1g (>= 1:1.1.4).
 libgpod4 depends on zlib1g (>= 1:1.2.0).
 libavcodec-extra-53 depends on zlib1g (>= 1:1.2.0).
 libxapian22 depends on zlib1g (>= 1:1.1.4).
 libpython2.7 depends on zlib1g (>= 1:1.2.0).
 libpci3 depends on zlib1g (>= 1:1.1.4).
 libqtgui4 depends on zlib1g (>= 1:1.1.4).
 libgvnc-1.0-0 depends on zlib1g (>= 1:1.1.4).
 libgeoip1 depends on zlib1g (>= 1:1.1.4).
 cpp-4.6 depends on zlib1g (>= 1:1.1.4).
 libcurl3-gnutls depends on zlib1g (>= 1:1.1.4).
 libgd2-xpm depends on zlib1g (>= 1:1.1.4).
 libwebkitgtk-1.0-0 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
 eog depends on zlib1g (>= 1:1.1.4).
 libcairo2 depends on zlib1g (>= 1:1.1.4).
 man-db depends on zlib1g (>= 1:1.1.4).
 libssl1.0.0 depends on zlib1g (>= 1:1.1.4).
 gpgv depends on zlib1g (>= 1:1.1.4).
 libxml2 depends on zlib1g (>= 1:1.2.3.3.dfsg).
 libprotobuf7 depends on zlib1g (>= 1:1.1.4).
 gdb depends on zlib1g (>= 1:1.2.0); however:
  Package zlib1g is to be removed.
 libfreetype6 depends on zlib1g (>= 1:1.1.4).
 libmagickcore4 depends on zlib1g (>= 1:1.1.4).
 mono-runtime depends on zlib1g (>= 1:1.1.4).
 libexempi3 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is to be removed.
dpkg: error processing zlib1g (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 zlib1g

Anyone have any suggestions as to where to go next?

---

### Post by critin on 2012-11-03
I would download the iso and install fresh.

12.04 is the stable one, the  LTS.  12.10 is not as stable.  Upgrading is always hazardous.   If this is your main system and you must depend on it, why upgrade?  none of my business, but...

---

### Post by jjmatt on 2012-11-09
Does anyone have any positive suggestions rather than "quit and start over"?

---

