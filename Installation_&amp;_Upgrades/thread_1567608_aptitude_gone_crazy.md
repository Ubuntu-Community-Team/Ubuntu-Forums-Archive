---
title: "aptitude gone crazy?"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by judepereira on 2010-09-04
I had a clean shutdown last night, and have always had one, however, this morning, here's what happened:
```

$ sudo aptitude update
# worked great as usual
$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  acpi-support{u} acpid{u} adium-theme-ubuntu{u} aisleriot{u} alacarte{u} 
  alsa-base{u} alsa-utils{u} anacron{u} ant{u} ant-gcj{u} ant-optional{u} 
  ant-optional-gcj{u} app-install-data{u} app-install-data-partner{u} 
  apparmor{u} apparmor-utils{u} apport{u} apport-gtk{u} apport-symptoms{u} 
  apt-transport-https{u} aptdaemon{u} aria2{u} at{u} at-spi{u} 
  avahi-autoipd{u} avahi-daemon{u} avahi-utils{u} awoken-icon-theme{u} 
  bc{u} bcmwl-modaliases{u} bind9-host{u} binfmt-support{u} binutils{u} 
  bluez{u} bluez-alsa{u} bluez-cups{u} bluez-gstreamer{u} bogofilter{u} 
  bogofilter-bdb{u} bogofilter-common{u} branding-ubuntu{u} brasero{u} 
  brasero-common{u} bridge-utils{u} brltty{u} brltty-x11{u} 
  build-essential{u} busybox-static{u} byobu{u} bzip2{u} 
  ca-certificates-java{u} cabextract{u} cairo-clock{u} capplets-data{u} 
  cdparanoia{u} checkbox{u} checkbox-gtk{u} chkconfig{u} chromium{u} 
  chromium-bsu{u} chromium-bsu-data{u} cli-common{u} command-not-found{u} 
  command-not-found-data{u} compiz{u} compiz-core{u} 
  compiz-fusion-plugins-extra{u} compiz-fusion-plugins-main{u} 
  compiz-gnome{u} compiz-plugins{u} compizconfig-backend-gconf{u} 
  compizconfig-settings-manager{u} computer-janitor{u} 
  computer-janitor-gtk{u} console-setup{u} console-terminus{u} 
  couchdb-bin{u} cpu-checker{u} cpufreqd{u} cron{u} cups{u} cups-bsd{u} 
  cups-client{u} cups-common{u} cups-driver-gutenprint{u} cvs{u} dc{u} 
  dcraw{u} default-jdk{u} default-jre{u} default-jre-headless{u} 
  desktop-file-utils{u} desktopcouch{u} dhcp3-client{u} dhcp3-common{u} 
  dkms{u} dmidecode{u} dmz-cursor-theme{u} dnsmasq-base{u} dnsutils{u} 
  doc-base{u} dpkg-dev{u} dvd+rw-tools{u} eclipse{u} eclipse-jdt{u} 
  eclipse-pde{u} eclipse-platform{u} eclipse-platform-data{u} 
  eclipse-plugin-cvs{u} eclipse-rcp{u} eco-theme{u} ed{u} eject{u} 
  empathy{u} empathy-common{u} eog{u} erlang-base{u} erlang-crypto{u} 
  erlang-inets{u} erlang-mnesia{u} erlang-public-key{u} 
  erlang-runtime-tools{u} erlang-ssl{u} erlang-syntax-tools{u} 
  erlang-xmerl{u} espeak{u} espeak-data{u} espeak-gui{u} evince{u} 
  evolution{u} evolution-common{u} evolution-couchdb{u} 
  evolution-data-server{u} evolution-data-server-common{u} 
  evolution-exchange{u} evolution-indicator{u} evolution-plugins{u} 
  evolution-webcal{u} example-content{u} f-spot{u} fakeroot{u} 
  fancontrol{u} fastjar{u} fglrx-modaliases{u} file-roller{u} finger{u} 
  firefox-gnome-support{u} flashplugin-installer{u} foo2zjs{u} 
  foomatic-db{u} foomatic-db-engine{u} foomatic-filters{u} freepats{u} 
  friendly-recovery{u} ftp{u} g++{u} g++-4.4{u} gbrainy{u} gcalctool{u} 
  gcc{u} gcc-4.4{u} gcj-4.4-base{u} gcj-4.4-jre-lib{u} 
  gconf-defaults-service{u} gconf-editor{u} gdb{u} gdebi{u} gdebi-core{u} 
  gdm{u} gdm-guest-session{u} gedit{u} gedit-common{u} genisoimage{u} 
  geoip-database{u} ghostscript-cups{u} ghostscript-x{u} gimp{u} 
  gimp-data{u} gnome-about{u} gnome-accessibility-themes{u} 
  gnome-applets{u} gnome-applets-data{u} gnome-bluetooth{u} 
  gnome-codec-install{u} gnome-control-center{u} gnome-desktop-data{u} 
  gnome-disk-utility{u} gnome-doc-utils{u} gnome-eco-theme{u} 
  gnome-games-common{u} gnome-mag{u} gnome-mahjongg{u} gnome-media{u} 
  gnome-media-common{u} gnome-menus{u} gnome-nettool{u} gnome-orca{u} 
  gnome-panel{u} gnome-panel-data{u} gnome-power-manager{u} 
  gnome-screensaver{u} gnome-session{u} gnome-session-bin{u} 
  gnome-session-canberra{u} gnome-settings-daemon{u} gnome-sudoku{u} 
  gnome-system-monitor{u} gnome-system-tools{u} gnome-terminal{u} 
  gnome-terminal-data{u} gnome-themes-selected{u} gnome-themes-ubuntu{u} 
  gnome-user-guide{u} gnome-user-share{u} gnome-utils{u} gnomine{u} 
  groff-base{u} gstreamer0.10-alsa{u} gstreamer0.10-ffmpeg{u} 
  gstreamer0.10-fluendo-mp3{u} gstreamer0.10-gnonlin{u} 
  gstreamer0.10-nice{u} gstreamer0.10-plugins-bad{u} 
  gstreamer0.10-plugins-base{u} gstreamer0.10-plugins-base-apps{u} 
  gstreamer0.10-plugins-good{u} gstreamer0.10-plugins-ugly{u} 
  gstreamer0.10-pulseaudio{u} gstreamer0.10-tools{u} gstreamer0.10-x{u} 
  gtk-eco-theme{u} gtk2-engines{u} gtk2-engines-murrine{u} 
  gtk2-engines-pixbuf{u} gucharmap{u} guile-1.8-libs{u} gvfs-bin{u} 
  gvfs-fuse{u} gwibber-service{u} hal{u} hal-info{u} hpijs{u} hplip{u} 
  hplip-data{u} htop{u} humanity-icon-theme{u} ia32-libs{u} ibus{u} 
  ibus-gtk{u} ibus-m17n{u} ibus-table{u} icedtea-6-jre-cacao{u} 
  icon-eco-theme{u} im-switch{u} imagemagick{u} indicator-applet{u} 
  indicator-applet-session{u} indicator-me{u} indicator-messages{u} 
  indicator-session{u} indicator-sound{u} info{u} inputattach{u} 
  intel-gpu-tools{u} iotop{u} iproute{u} iptables{u} iputils-arping{u} 
  iputils-ping{u} iputils-tracepath{u} irqbalance{u} jarwrapper{u} 
  java-common{u} jockey-common{u} jockey-gtk{u} junit{u} junit4{u} kbd{u} 
  kerneloops-daemon{u} language-pack-en{u} language-pack-en-base{u} 
  language-pack-gnome-en{u} language-pack-gnome-en-base{u} 
  language-selector{u} language-selector-common{u} language-support-en{u} 
  language-support-writing-en{u} laptop-detect{u} less{u} lftp{u} 
  lib32asound2{u} lib32bz2-1.0{u} lib32gcc1{u} lib32ncurses5{u} 
  lib32nss-mdns{u} lib32stdc++6{u} lib32v4l-0{u} lib32z1{u} liba52-0.7.4{u} 
  libaa1{u} libaccess-bridge-java{u} libaccess-bridge-java-jni{u} 
  libaio1{u} libalut0{u} libanthy0{u} libapparmor-perl{u} libapparmor1{u} 
  libapr1{u} libaprutil1{u} libart2.0-cil{u} libasm3-java{u} 
  libasound2-plugins{u} libass4{u} libatm1{u} libatspi1.0-0{u} libaudio2{u} 
  libavahi-core6{u} libavahi-gobject0{u} libavahi-ui0{u} libavc1394-0{u} 
  libavcodec52{u} libavformat52{u} libavutil49{u} libbabl-0.0-0{u} 
  libbeagle1{u} libbind9-60{u} libbrasero-media0{u} libbrlapi0.5{u} 
  libbsd0{u} libc-ares2{u} libc-dev-bin{u} libc6-dev{u} libc6-i386{u} 
  libcaca0{u} libcairomm-1.0-1{u} libcamel1.2-14{u} 
  libcanberra-gtk-module{u} libcanberra-gtk0{u} libcanberra-pulse{u} 
  libcanberra0{u} libcap-ng0{u} libcdaudio1{u} libcdparanoia0{u} 
  libcelt0-0{u} libclutter-1.0-0{u} libclutter-gtk-0.10-0{u} 
  libcolamd2.7.1{u} libcommons-beanutils-java{u} libcommons-codec-java{u} 
  libcommons-collections3-java{u} libcommons-compress-java{u} 
  libcommons-digester-java{u} libcommons-el-java{u} 
  libcommons-httpclient-java{u} libcommons-logging-java{u} 
  libcompizconfig0{u} libcouchdb-glib-1.0-2{u} libcpufreq0{u} 
  libcryptui0{u} libcupscgi1{u} libcupsdriver1{u} libcupsmime1{u} 
  libcupsppdc1{u} libcurl3{u} libcurses-perl{u} libcurses-ui-perl{u} 
  libdaemon0{u} libdb-je-java{u} libdb4.7-java{u} libdb4.7-java-gcj{u} 
  libdc1394-22{u} libdca0{u} libdecoration0{u} 
  libdesktopcouch-glib-1.0-2{u} libdevkit-power-gobject1{u} 
  libdirac-encoder0{u} libdjvulibre-text{u} libdjvulibre21{u} libdns64{u} 
  libdotconf1.0{u} libdv4{u} libdvdnav4{u} libdvdread4{u} 
  libebackend1.2-0{u} libebml0{u} libebook1.2-9{u} libecal1.2-7{u} 
  libecj-java{u} libedata-book1.2-2{u} libedata-cal1.2-6{u} 
  libedataserver1.2-11{u} libedataserverui1.2-8{u} libedit2{u} 
  libegroupwise1.2-13{u} libelf1{u} libenca0{u} libequinox-osgi-java{u} 
  libespeak1{u} libevdocument2{u} libevent-1.4-2{u} libevview2{u} 
  libexchange-storage1.2-3{u} libexempi3{u} libfaad2{u} libfftw3-3{u} 
  libfile-copy-recursive-perl{u} libflac8{u} libflickrnet2.2-cil{u} 
  libflite1{u} libfont-afm-perl{u} libfreezethaw-perl{u} libfs6{u} 
  libgadu3{u} libgail-common{u} libgail-gnome-module{u} libgcj-bc{u} 
  libgcj-common{u} libgcj10{u} libgconf2.0-cil{u} libgd2-xpm{u} 
  libgdata-common{u} libgdata-google1.2-1{u} libgdata1.2-1{u} 
  libgdata1.4-cil{u} libgdata6{u} libgdict-1.0-6{u} libgdiplus{u} 
  libgdu-gtk0{u} libgegl-0.0-0{u} libgeoip1{u} libgif4{u} libgimp2.0{u} 
  libglade2.0-cil{u} libglc0{u} libglib2.0-cil{u} libglibmm-2.4-1c2a{u} 
  libglitz-glx1{u} libglitz1{u} libglpng{u} libglu1-mesa{u} libgme0{u} 
  libgmime-2.4-2{u} libgmime2.4-cil{u} libgnome-bluetooth7{u} 
  libgnome-desktop-2-17{u} libgnome-keyring1.0-cil{u} libgnome-mag2{u} 
  libgnome-media0{u} libgnome-menu2{u} libgnome-pilot2{u} 
  libgnome-vfs2.0-cil{u} libgnome-window-settings1{u} libgnome2.24-cil{u} 
  libgnomedesktop2.20-cil{u} libgnomekbd-common{u} libgnomekbd4{u} 
  libgnomepanel2.24-cil{u} libgoocanvas-common{u} libgoocanvas3{u} 
  libgpgme11{u} libgpod-common{u} libgpod4{u} libgraphite3{u} 
  libgraphviz4{u} libgsl0ldbl{u} libgsm1{u} libgssdp-1.0-2{u} 
  libgstfarsight0.10-0{u} libgtk-vnc-1.0-0{u} libgtk2.0-cil{u} 
  libgtkhtml-editor-common{u} libgtkhtml-editor0{u} libgtkhtml3.14-19{u} 
  libgtkmm-2.4-1c2a{u} libgtksourceview2.0-0{u} 
  libgtksourceview2.0-common{u} libgtkspell0{u} libgucharmap7{u} 
  libgupnp-1.0-3{u} libgupnp-igd-1.0-2{u} libgutenprint2{u} 
  libgweather-common{u} libgweather1{u} libhamcrest-java{u} libhpmud0{u} 
  libhtml-format-perl{u} libhtml-parser-perl{u} libhtml-tagset-perl{u} 
  libhtml-tree-perl{u} libhyphen0{u} libibus1{u} libical0{u} libice-dev{u} 
  libicu4j-java{u} libid3tag0{u} libido-0.1-0{u} libiec61883-0{u} 
  libieee1284-3{u} libijs-0.35{u} libilmbase6{u} libindicate-gtk2{u} 
  libindicate4{u} libiptcdata0{u} libisc60{u} libisccc60{u} libisccfg60{u} 
  libiw30{u} libjack0{u} libjasper-java{u} libjaxp1.3-java{u} 
  libjetty-java{u} libjline-java{u} libjs-jquery{u} libjsch-java{u} 
  libjtidy-java{u} libkate1{u} libkpathsea5{u} 
  liblaunchpad-integration1.0-cil{u} liblircclient0{u} liblockfile1{u} 
  libloudmouth1-0{u} liblouis-data{u} liblouis0{u} liblpint-bonobo0{u} 
  liblua5.1-0{u} liblucene2-java{u} liblwres60{u} liblzo2-2{u} libm17n-0{u} 
  libmad0{u} libmagickcore2-extra{u} libmailtools-perl{u} libmatroska0{u} 
  libmeanwhile1{u} libmetacity-private0{u} libmimic0{u} libmldbm-perl{u} 
  libmms0{u} libmng1{u} libmodplug0c2{u} libmono-addins-gui0.2-cil{u} 
  libmono-addins0.2-cil{u} libmono-cairo2.0-cil{u} libmono-corlib2.0-cil{u} 
  libmono-data-tds2.0-cil{u} libmono-i18n-west2.0-cil{u} 
  libmono-posix2.0-cil{u} libmono-security2.0-cil{u} 
  libmono-sharpzip2.84-cil{u} libmono-sqlite2.0-cil{u} 
  libmono-system-data2.0-cil{u} libmono-system-runtime2.0-cil{u} 
  libmono-system-web2.0-cil{u} libmono-system2.0-cil{u} libmono2.0-cil{u} 
  libmp3lame0{u} libmpcdec3{u} libmpeg2-4{u} libmtp8{u} 
  libmusicbrainz4c2a{u} libnautilus-extension1{u} libncurses5-dev{u} 
  libndesk-dbus-glib1.0-cil{u} libndesk-dbus1.0-cil{u} libneon27-gnutls{u} 
  libnet-dbus-perl{u} libnice0{u} libnl1{u} libnm-glib2{u} libnm-util1{u} 
  libnotify-bin{u} libnotify0.4-cil{u} libnotify1{u} libnss-mdns{u} 
  libnunit2.4-cil{u} libofa0{u} libogg0{u} liboil0.3{u} liboobs-1-4{u} 
  libopenal1{u} libopencore-amrnb0{u} libopencore-amrwb0{u} libopenexr6{u} 
  liborc-0.4-0{u} libotf0{u} libpanel-applet2-0{u} libpangomm-1.4-1{u} 
  libpcap0.8{u} libpci3{u} libpciaccess0{u} libpcsclite1{u} libperl5.10{u} 
  libpisock9{u} libpisync1{u} libpolkit-gtk-1-0{u} libpoppler-glib4{u} 
  libpoppler5{u} libportaudio2{u} libpostproc51{u} libprotobuf5{u} 
  libprotoc5{u} libpst4{u} libpth20{u} libpthread-stubs0{u} 
  libpthread-stubs0-dev{u} libpulse-browse0{u} libpulse-mainloop-glib0{u} 
  libpulse0{u} libpurple-bin{u} libpurple0{u} libraptor1{u} librasqal2{u} 
  libraw1394-11{u} librdf0{u} libregexp-java{u} librpc-xml-perl{u} 
  librsvg2-2.18-cil{u} libsamplerate0{u} libsane{u} 
  libschroedinger-1.0-0{u} libsctp1{u} libsdl-image1.2{u} 
  libsdl1.2debian{u} libsdl1.2debian-pulseaudio{u} libsensors3{u} 
  libsensors4{u} libservlet2.4-java{u} libservlet2.5-java{u} libshout3{u} 
  libsidplay1{u} libsilc-1.1-2{u} libsilcclient-1.1-3{u} libslf4j-java{u} 
  libslp1{u} libsm-dev{u} libsndfile1{u} libsnmp-base{u} libsnmp15{u} 
  libsoundtouch1c2{u} libspectre1{u} libspeechd2{u} libspeex1{u} 
  libspeexdsp1{u} libsqlite0{u} libstdc++6-4.4-dev{u} libsvga1{u} 
  libsvn1{u} libswscale0{u} libtag1-vanilla{u} libtag1c2a{u} libtdb1{u} 
  libtelepathy-farsight0{u} libtelepathy-glib0{u} libterm-readkey-perl{u} 
  libtheora0{u} libtie-ixhash-perl{u} libtotem-plparser17{u} libtwolame0{u} 
  libubuntuone-1.0-1{u} libuniconf4.6{u} libunique-1.0-0{u} 
  libupower-glib1{u} liburi-perl{u} libuuid-perl{u} libv4l-0{u} 
  libvisual-0.4-0{u} libvisual-0.4-plugins{u} libvorbis0a{u} 
  libvorbisenc2{u} libvorbisfile3{u} libwavpack1{u} libwildmidi0{u} 
  libwmf0.2-7{u} libwmf0.2-7-gtk{u} libwnck-common{u} libwnck2.20-cil{u} 
  libwnck22{u} libwpd8c2a{u} libwpg-0.1-1{u} libwps-0.1-1{u} libwrap0{u} 
  libwvstreams4.6-base{u} libwvstreams4.6-extras{u} libwww-perl{u} 
  libx11-dev{u} libx264-85{u} libx86-1{u} libxau-dev{u} libxcb1-dev{u} 
  libxdmcp-dev{u} libxerces2-java{u} libxkbfile1{u} libxklavier16{u} 
  libxml-libxml-perl{u} libxml-namespacesupport-perl{u} 
  libxml-parser-perl{u} libxml-sax-expat-perl{u} libxml-sax-perl{u} 
  libxml-twig-perl{u} libxml-xpath-perl{u} libxml2-utils{u} libxp6{u} 
  libxres1{u} libxt-dev{u} libxvidcore4{u} libxvmc1{u} libxxf86misc1{u} 
  libzephyr4{u} light-themes{u} linux-generic{u} linux-headers-2.6.32-24{u} 
  linux-headers-2.6.32-24-generic{u} linux-headers-generic{u} 
  linux-libc-dev{u} linux-sound-base{u} lksctp-tools{u} lm-sensors{u} 
  lockfile-progs{u} logrotate{u} lp-solve{u} lshw{u} lsof{u} ltrace{u} 
  m17n-contrib{u} m17n-db{u} man-db{u} manpages{u} manpages-dev{u} 
  media-player-info{u} memtest86+{u} menu{u} metacity{u} metacity-common{u} 
  metacity-eco-theme{u} min12xxw{u} mlocate{u} 
  mobile-broadband-provider-info{u} modemmanager{u} mono-2.0-gac{u} 
  mono-gac{u} mono-runtime{u} mousetweaks{u} mplayer{u} mscompress{u} 
  mtr-tiny{u} nano{u} nautilus{u} nautilus-data{u} nautilus-sendto{u} 
  nautilus-sendto-empathy{u} nautilus-share{u} netcat-openbsd{u} 
  network-manager{u} network-manager-gnome{u} network-manager-pptp{u} 
  network-manager-pptp-gnome{u} nmap{u} notify-osd{u} notify-osd-icons{u} 
  nspluginwrapper{u} ntp{u} ntpdate{u} nvidia-173-modaliases{u} 
  nvidia-96-modaliases{u} nvidia-common{u} nvidia-current{u} 
  nvidia-current-modaliases{u} nvidia-settings{u} obexd-client{u} 
  onboard{u} openjdk-6-jdk{u} openjdk-6-jre{u} openjdk-6-jre-headless{u} 
  openjdk-6-jre-lib{u} openoffice.org-base-core{u} openoffice.org-calc{u} 
  openoffice.org-common{u} openoffice.org-core{u} openoffice.org-draw{u} 
  openoffice.org-emailmerge{u} openoffice.org-gnome{u} 
  openoffice.org-gtk{u} openoffice.org-help-en-us{u} 
  openoffice.org-impress{u} openoffice.org-math{u} 
  openoffice.org-style-human{u} openoffice.org-writer{u} 
  openprinting-ppds{u} openssh-client{u} parted{u} patch{u} pciutils{u} 
  pcmciautils{u} pkg-config{u} plymouth-x11{u} pm-utils{u} 
  pm-utils-powersave-policy{u} pnm2ppa{u} policykit-desktop-privileges{u} 
  poppler-utils{u} popularity-contest{u} ppp{u} pppconfig{u} pppoeconf{u} 
  pptp-linux{u} protobuf-compiler{u} pulseaudio{u} 
  pulseaudio-esound-compat{u} pulseaudio-module-bluetooth{u} 
  pulseaudio-module-gconf{u} pulseaudio-module-x11{u} pulseaudio-utils{u} 
  pxljr{u} python-appindicator{u} python-apport{u} python-aptdaemon{u} 
  python-aptdaemon-gtk{u} python-avahi{u} python-brlapi{u} 
  python-compizconfig{u} python-configglue{u} python-configobj{u} 
  python-couchdb{u} python-crypto{u} python-cups{u} python-cupshelpers{u} 
  python-desktopcouch{u} python-desktopcouch-records{u} 
  python-egenix-mxdatetime{u} python-egenix-mxtools{u} python-espeak{u} 
  python-farsight{u} python-fstab{u} python-gconf{u} python-gdbm{u} 
  python-gmenu{u} python-gnome2{u} python-gnomeapplet{u} 
  python-gnomecanvas{u} python-gnomekeyring{u} python-gst0.10{u} 
  python-gtksourceview2{u} python-gtkspell{u} python-httplib2{u} 
  python-ibus{u} python-imaging{u} python-indicate{u} 
  python-launchpad-integration{u} python-launchpadlib{u} 
  python-lazr.restfulclient{u} python-lazr.uri{u} python-libxml2{u} 
  python-louis{u} python-mako{u} python-newt{u} python-notify{u} 
  python-oauth{u} python-openssl{u} python-pam{u} python-papyon{u} 
  python-pexpect{u} python-pkg-resources{u} python-problem-report{u} 
  python-protobuf{u} python-pyatspi{u} python-pycurl{u} 
  python-pygoocanvas{u} python-pyinotify{u} python-pyorbit{u} 
  python-rdflib{u} python-serial{u} python-simplejson{u} python-smbc{u} 
  python-speechd{u} python-telepathy{u} python-twisted-bin{u} 
  python-twisted-core{u} python-twisted-names{u} python-twisted-web{u} 
  python-ubuntuone{u} python-ubuntuone-client{u} 
  python-ubuntuone-storageprotocol{u} python-uno{u} python-virtkey{u} 
  python-wadllib{u} python-wnck{u} python-xdg{u} python-xkit{u} 
  python-zope.interface{u} qemu-common{u} qemu-kvm{u} quadrapassel{u} 
  radeontool{u} rcconf{u} rdesktop{u} realpath{u} rhythmbox{u} 
  rhythmbox-plugin-cdrecorder{u} rhythmbox-plugins{u} 
  rhythmbox-ubuntuone-music-store{u} rsync{u} rsyslog{u} rtkit{u} 
  samba-common{u} samba-common-bin{u} sane-utils{u} sat4j{u} screen{u} 
  screen-resolution-extra{u} screensaver-default-images{u} seabios{u} 
  seahorse{u} smartdimmer{u} smbclient{u} software-center{u} 
  speech-dispatcher{u} splix{u} ssh-askpass-gnome{u} ssl-cert{u} strace{u} 
  subversion{u} syslinux{u} system-config-printer-common{u} 
  system-config-printer-gnome{u} system-config-printer-udev{u} 
  system-tools-backends{u} sysv-rc-conf{u} tasksel{u} tasksel-data{u} 
  tcl8.4{u} tcpd{u} tcpdump{u} telepathy-butterfly{u} telepathy-gabble{u} 
  telepathy-haze{u} telepathy-idle{u} telepathy-mission-control-5{u} 
  telepathy-salut{u} telnet{u} time{u} tk8.4{u} tomboy{u} toshset{u} 
  totem{u} totem-common{u} totem-mozilla{u} totem-plugins{u} traceroute{u} 
  transmission-common{u} transmission-gtk{u} tsclient{u} 
  ttf-dejavu-extra{u} ttf-indic-fonts-core{u} ttf-kacst-one{u} 
  ttf-khmeros-core{u} ttf-lao{u} ttf-liberation{u} 
  ttf-mscorefonts-installer{u} ttf-opensymbol{u} ttf-punjabi-fonts{u} 
  ttf-symbol-replacement{u} ttf-takao-pgothic{u} ttf-thai-tlwg{u} 
  ttf-unfonts-core{u} ttf-uralic{u} ttf-wqy-microhei{u} tzdata-java{u} 
  ubuntu-artwork{u} ubuntu-desktop{u} ubuntu-docs{u} ubuntu-minimal{u} 
  ubuntu-mono{u} ubuntu-sounds{u} ubuntu-standard{u} 
  ubuntu-system-service{u} ubuntu-tweak{u} ubuntu-wallpapers{u} 
  ubuntuone-client{u} ubuntuone-client-gnome{u} ufw{u} uno-libs3{u} 
  unzip{u} update-inetd{u} update-manager{u} update-manager-core{u} 
  update-notifier{u} update-notifier-common{u} upower{u} ure{u} 
  ureadahead{u} usb-creator-common{u} usb-creator-gtk{u} usbutils{u} 
  vbetool{u} vgabios{u} vim{u} vim-common{u} vim-runtime{u} vim-tiny{u} 
  vinagre{u} vino{u} wallpaper-eco-theme{u} wamerican{u} wbritish{u} 
  whois{u} winbind{u} wine{u} wine1.2{u} wine1.2-gecko{u} wireless-tools{u} 
  wodim{u} wpasupplicant{u} wvdial{u} x11-apps{u} x11-session-utils{u} 
  x11-xfs-utils{u} x11-xkb-utils{u} x11proto-core-dev{u} 
  x11proto-input-dev{u} x11proto-kb-dev{u} xbitmaps{u} xcursor-themes{u} 
  xdg-user-dirs{u} xdg-user-dirs-gtk{u} xfonts-100dpi{u} xfonts-75dpi{u} 
  xfonts-base{u} xfonts-mathml{u} xfonts-scalable{u} xinit{u} xinput{u} 
  xkb-data{u} xorg{u} xorg-docs-core{u} xscreensaver-data{u} 
  xscreensaver-gl{u} xserver-common{u} xserver-xorg{u} xserver-xorg-core{u} 
  xserver-xorg-input-all{u} xserver-xorg-input-evdev{u} 
  xserver-xorg-input-mouse{u} xserver-xorg-input-synaptics{u} 
  xserver-xorg-input-vmmouse{u} xserver-xorg-input-wacom{u} 
  xserver-xorg-video-all{u} xserver-xorg-video-apm{u} 
  xserver-xorg-video-ark{u} xserver-xorg-video-ati{u} 
  xserver-xorg-video-chips{u} xserver-xorg-video-cirrus{u} 
  xserver-xorg-video-fbdev{u} xserver-xorg-video-i128{u} 
  xserver-xorg-video-intel{u} xserver-xorg-video-mach64{u} 
  xserver-xorg-video-mga{u} xserver-xorg-video-neomagic{u} 
  xserver-xorg-video-nouveau{u} xserver-xorg-video-nv{u} 
  xserver-xorg-video-openchrome{u} xserver-xorg-video-r128{u} 
  xserver-xorg-video-radeon{u} xserver-xorg-video-rendition{u} 
  xserver-xorg-video-s3{u} xserver-xorg-video-s3virge{u} 
  xserver-xorg-video-savage{u} xserver-xorg-video-siliconmotion{u} 
  xserver-xorg-video-sis{u} xserver-xorg-video-sisusb{u} 
  xserver-xorg-video-tdfx{u} xserver-xorg-video-trident{u} 
  xserver-xorg-video-tseng{u} xserver-xorg-video-v4l{u} 
  xserver-xorg-video-vesa{u} xserver-xorg-video-vmware{u} 
  xserver-xorg-video-voodoo{u} xsltproc{u} xterm{u} xtrans-dev{u} 
  xulrunner-1.9.2{u} xz-utils{u} yelp{u} zenity{u} zenmap{u} zip{u} 
0 packages upgraded, 0 newly installed, 1085 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3,183MB will be freed.
Do you want to continue? [Y/n/?] # are you serious?

```
Now, what on earth is going on?
All this while it ran just fine, I always use it.
apt-get seems to be clean:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Someone kindly shed some light on this, 

Thanks in advance

---

### Post by akoskm on 2010-09-04
Is
```

sudo apt-get upgrade

```
showing the same list?

---

### Post by judepereira on 2010-09-04
No, apt-get upgrade shows no upgrades at all, as I update the machine in the morning.

It's only with aptitude that this problem is faced, do the two use different package databases?

---

