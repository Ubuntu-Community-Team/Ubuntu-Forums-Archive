---
title: "[SOLVED] Problem With libc6"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by alsamman on 2008-02-01
I am not sure what to do right now so here is the problem
For some reason the version of my libc6 is 2.7 when it should be 2.6.
This version is causing a lot of problems with me because a lot of things I cannot install.
Is there a way that I can downgrade this version without it removing all of the programs that depend on it (there's alot!)?
```

kenan@kenan-desktop:~$ sudo apt-get remove libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnustep-base-common libgda3-common mplayer-skins gnustep-gui-common
  kdelibs-data update-notifier-common mysql-common pidgin-data gcc-3.4-base
  gutsy-wallpapers gcj-4.2-base autotools-dev libzvbi-common gnustep-common
  freepats libgii1-target-x xdg-utils maxima-doc libgtk1.2-common
  discover1-data dmz-cursor-theme skype-common dpatch gnustep-ppd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpi acpi-support acpid adduser agenda.app alacarte alien alltray alsa-base
  alsa-oss alsa-utils amsn anacron apmd apparmor apparmor-utils apport
  apport-gtk appres apt apt-utils aptitude apturl ardour ark aspell aspell-en
  at at-spi audacity autoconf automake1.9 avahi-autoipd avahi-daemon
  avant-window-navigator awn-manager base-files base-passwd bash bc
  beforelight belocs-locales-bin bind9-host binfmt-support binutils
  binutils-static bitmap bittorrent blender bluez-cups bluez-gnome bluez-utils
  bogofilter bogofilter-bdb brltty brltty-x11 bsdmainutils bsdutils bsh
  bug-buddy bzip2 bzr ca-certificates cabextract capplets-data cdparanoia
  cdrdao cdrecord cinelerra cli-common command-not-found compiz compiz-core
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome
  compiz-kde compiz-plugins compizconfig-settings-manager console-setup
  console-terminus console-tools consolekit contact-lookup-applet coreutils
  cpio cpp cpp-3.4 cpp-4.1 cron cups-pdf cupsddk cupsddk-drivers cupsys
  cupsys-bsd cupsys-client cupsys-common cupsys-driver-gimpprint
  cupsys-driver-gutenprint cupsys-pt dash dbus dbus-x11 dc dcraw debconf
  debconf-i18n debhelper debianutils defoma deskbar-applet desktop-file-utils
  devilspie dhcdbd dhcp3-client dhcp3-common dictionaries-common diff
  discover1 displayconfig-gtk diveintopython dmidecode dmsetup dnsutils
  doc-base docbook-xml docker dosfstools dpkg dpkg-dev dselect dvd+rw-tools
  dvdauthor e2fslibs e2fsprogs ed editres eject ekiga emerald eog esound
  espeak ethtool evince evolution evolution-data-server evolution-exchange
  evolution-plugins evolution-webcal f-spot fakeroot fast-user-switch-applet
  fdutils fftw3 file file-roller findutils finger firefox
  firefox-gnome-support flashplugin-nonfree fontconfig fontconfig-config
  foo2zjs foomatic-db-engine foomatic-filters fortune-mod fortunes-min fping
  freeglut3 fstobdf ftp fuse-utils gaim gamin gcalctool gcc gcc-3.4 gcc-4.1
  gconf-editor gconf2 gconf2-common gdb gdebi gdebi-core gdesklets
  gdesklets-data gdm gedit genisoimage gettext gettext-base ghostscript
  ghostscript-x gij gij-4.1 gij-4.2 gimp gimp-print gimp-python git git-core
  gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-btdownload gnome-compiz-manager
  gnome-control-center gnome-cups-manager gnome-doc-utils gnome-games
  gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager
  gnome-mag gnome-media gnome-media-common gnome-menus gnome-mount
  gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data
  gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver
  gnome-session gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils
  gnome-volume-manager gnupg gnuplot-nox gnustep-back-common gnustep-back0.11
  gnustep-base-runtime gnustep-gpbs gnustep-gui-runtime gpgv grep groff-base
  grub gs-common gs-esp gs-esp-x gsfonts gstreamer0.10-alsa gstreamer0.10-esd
  gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gnomevfs
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-schroedinger
  gstreamer0.10-tools gstreamer0.10-x gthumb gtk-sharp gtk-sharp-examples
  gtk-sharp-gapi gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks
  gtkhtml3.14 gucharmap guidance-backends guile-1.6-libs gzip hal
  hal-cups-utils hal-device-manager hdparm hostname hotkey-setup html2text
  human-theme hwdb-client-common hwdb-client-gnome iceauth ico ifupdown
  imagemagick info initramfs-tools initscripts inkscape inputattach
  intltool-debian iproute iptables iputils-arping iputils-ping
  iputils-tracepath ircii jackd k9copy kdelibs4c2a kernel-wedge kiba-dock
  kiba-dock-dev kiba-plugins kiba-plugins-gnome kiba-settings kino klogd
  kooldock kwin language-pack-ar language-pack-ar-base language-pack-en
  language-pack-en-base language-pack-gnome-ar language-pack-gnome-ar-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common laptop-detect laptop-mode-tools
  launchpad-integration less lftp liba52-0.7.4 libaa1 libacl1 libakamaru0
  libalut0 libao2 libapm1 libapr1 libaprutil1 libart-2.0-2 libart2.0-cil
  libarts1-mpeglib libarts1c2a libartsc0 libasound2 libaspell15 libatk1.0-0
  libatm1 libatspi1.0-0 libattr1 libaudio2 libaudiofile0 libavahi-client3
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1
  libavahi-qt3-1 libavc1394-0 libavcodec1d libavformat1d libavutil1d libawn0
  libbeagle0 libbeecrypt6 libbind9-30 libblkid1 libbluetooth2 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libboost-filesystem1.34.1 libbrlapi1
  libbz2-1.0 libc6 libcaca0 libcairo-perl libcairo2 libcairomm-1.0-1
  libcamel1.2-10 libcap1 libcdaudio1 libcdio-cdda0 libcdio6 libcdparanoia0
  libcomerr2 libcompizconfig-backend-gconf libcompizconfig-backend-kconfig
  libcompizconfig0 libconsole libcroco3 libcucul0 libcupsimage2 libcupsys2
  libcurl3 libcurl3-gnutls libdaemon0 libdatrie0 libdb4.2 libdb4.3 libdb4.4
  libdb4.5 libdbus-1-3 libdbus-glib-1-2 libdbus-qt-1-1c2 libdc1394-13
  libdecoration0 libdeskbar-tracker libdevmapper1.02.1 libdigest-sha1-perl
  libdirectfb-0.9-25 libdiscid0 libdiscover1 libdjvulibre15 libdmx1 libdns32
  libdrm2 libdv4 libdvbpsi4 libdvdcss2 libdvdnav4 libdvdread3 libdynamite0
  libebml0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libedit2 libeel2-2
  libegroupwise1.2-13 libelfg0 libemeraldengine0 libenchant1c2a liberror-perl
  libesd-alsa0 libespeak1 libexchange-storage1.2-3 libexif12 libexpat1
  libfaac0 libfaad2-0 libffcall1 libflac8 libfontconfig1 libfontenc1
  libfreebob0 libfreetype6 libfribidi0 libfs6 libfuse2 libgadu3 libgail-common
  libgail-gnome-module libgail18 libgamin0 libgc1c2 libgcc1 libgcj-bc
  libgcj7-1 libgcj8-1 libgconf-cil libgconf2-4 libgconf2.0-cil libgcrypt11
  libgd2-noxpm libgda2-3 libgda3-3 libgdbm3 libgdiplus libgdl-1-0
  libgdl-gnome-1-0 libggi2 libgii1 libgimp2.0 libgksu1.2-1 libgksu2-0
  libgksuui1.0-1 libgl1-mesa-dri libgl1-mesa-glx libglade-cil libglade2-0
  libglade2.0-cil libglew1.4 libglib-cil libglib-perl libglib1.2 libglib2.0-0
  libglib2.0-cil libglib2.0-dev libglibmm-2.4-1c2a libglitz-glx1 libglitz1
  libglu1-mesa libglut3 libgmime-2.0-2 libgmime2.2-cil libgmp3c2 libgnome-cil
  libgnome-compiz-manager0 libgnome-desktop-2 libgnome-keyring0 libgnome-mag2
  libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7
  libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnome2-wnck-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecups1.0-1
  libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1
  libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgnustep-base1.13
  libgnustep-gui0.11 libgnutls13 libgpg-error0 libgphoto2-2 libgphoto2-port0
  libgpmg1 libgpod2 libgs8 libgsf-1-114 libgsl0 libgsm1
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-cil libgtk1.2
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkhtml2-0
  libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtkmm-2.4-1c2a
  libgtksourceview1.0-0 libgtksourceview2.0-0 libgtkspell0 libgtop2-7
  libgtop2-dev libgucharmap6 libguicast libguile-ltdl-1 libgutenprint2
  libgutenprintui2-1 libhal-storage1 libhal1 libhesiod0 libhsqldb-java
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhunspell-1.1-0
  libice6 libicu36 libid3tag0 libidl0 libidn11 libiec61883-0 libieee1284-3
  libisc32 libisccc30 libisccfg30 libiso9660-4 libiw29 libjack0
  libjack0.100.0-0 libjasper1 libjaxp1.3-java libjline-java libjpeg62
  libkeyutils1 libkpathsea4 libkrb53 liblame0 liblaunchpad-integration0
  liblcms1 libldap2 liblircclient0 liblo0 liblocale-gettext-perl
  liblpint-bonobo0 liblrdf0 libltdl3 liblua50 liblualib50 liblwres30 liblzo1
  liblzo2-2 libmad0 libmagic1 libmagick9 libmatroska0 libmcs1 libmdbtools
  libmeanwhile1 libmetacity0 libmikmod2 libmjpegtools0c2a libmms0 libmng1
  libmodplug0c2 libmono-cairo1.0-cil libmono-corlib1.0-cil
  libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil
  libmono-peapi1.0-cil libmono-relaxng1.0-cil libmono-security1.0-cil
  libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil
  libmono-system-runtime1.0-cil libmono-system-web1.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono0 libmono1.0-cil libmono2.0-cil libmp4v2-0 libmpcdec3 libmpeg1
  libmpeg2-4 libmpeg3-1 libmpeg3-dev libmpeg3hv libmpeg3hv-dev libmtp6
  libmusicbrainz4c2a libmysqlclient15off libnautilus-burn4
  libnautilus-extension1 libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libndesk-dbus1.0-cil libneon25 libneon26 libnet-dbus-perl libnewt0.52
  libnl1-pre6 libnm-glib0 libnm-util0 libnotify1 libnspr4-0d libnss-mdns
  libnss3-0d libntfs-3g12 libobjc1 libode0debian1 libofa0 libogg0 liboil0.3
  liboobs-1-3 libopal-2.2 libopenal0a libopencdk8 libopenexr2c2a libopenspc0
  liborange0 liborbit2 libpam-foreground libpam-gnome-keyring libpam-modules
  libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0 libpango1.0-common
  libpaper-utils libpaper1 libparted1.7-1 libpcap0.8 libpci2 libpcre3
  libpcrecpp0 libperl5.8 libpisock9 libpisync0 libpng12-0 libpoppler-glib2
  libpoppler2 libpopt0 libportaudio0 libpostproc1d libpq5 libpt-1.10.0
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libpulse0 libpurple0
  libqt3-mt libqt4-core libqt4-gui libqt4-sql libqthreads-12 libquicktime1
  libquicktimehv libquicktimehv-dev libraptor1 librarian0 libraw1394-8
  libreadline5 librecode0 libresid-builder0c2a librpc-xml-perl librpm4
  librsvg2-2 librsvg2-bin librsvg2-common librsvg2.0-cil libsamplerate0
  libsane libsasl2-2 libsasl2-modules libschroedinger-0.1-0 libscim8c2a
  libscrollkeeper0 libsdl-gfx1.2-4 libsdl-image1.2 libsdl-mixer1.2
  libsdl-net1.2 libsdl-ttf2.0-0 libsdl1.2debian libsdl1.2debian-alsa
  libselinux1 libsensors3 libsepol1 libservlet2.3-java libservlet2.4-java
  libsexy2 libshout3 libsidplay1 libsidplay2 libsigc++-2.0-0c2a libslang2
  libslp1 libsm6 libsmbclient libsmpeg0 libsnack2 libsndfile1 libsnmp-perl
  libsnmp10 libsoundtouch1c2 libsoup2.2-8 libspeex1 libsqlite0 libsqlite3-0
  libss2 libssl0.9.8 libstartup-notification0 libstdc++5 libstdc++6
  libstlport5.1 libsvg1 libsvga1 libsvn1 libswt3.2-gtk-java libswt3.2-gtk-jni
  libsynce0 libsysfs2 libtag1c2a libtar libtasn1-3 libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libthai0
  libtheora0 libtiff4 libtotem-plparser7 libtracker-gtk0 libtrackerclient0
  libtwolame0 libungif4g libuniconf4.3 libunshield0 liburi-perl libusb-0.1-4
  libusplash0 libuuid1 libvcdinfo0 libvisual-0.4-0 libvlc0 libvolume-id0
  libvorbis0a libvorbisenc2 libvorbisfile3 libvte-cil libvte9 libwavpack1
  libwmf0.2-7 libwnck22 libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libwrap0
  libwvstreams4.3-base libwvstreams4.3-extras libwww-perl libwxbase2.6-0
  libwxbase2.8-0 libwxgtk2.6-0 libwxgtk2.8-0 libx11-6 libx11-data libx11-dev
  libx264-54 libx86-1 libxalan2-java libxau-dev libxau6 libxaw7
  libxcomposite-dev libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev
  libxdmcp6 libxerces2-java libxevie1 libxext-dev libxext6 libxfixes-dev
  libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 libxklavier11
  libxml++2.6c2a libxml-libxml-common-perl libxml-libxml-perl
  libxml-namespacesupport-perl libxml-parser-perl libxml-sax-perl
  libxml-twig-perl libxml2 libxml2-utils libxmu6 libxmuu1 libxosd2 libxp6
  libxplc0.3.13 libxpm4 libxrandr2 libxrender1 libxres1 libxslt1.1 libxss1
  libxt6 libxtrap6 libxtst-dev libxtst6 libxv1 libxvidcore4 libxvmc1
  libxxf86dga1 libxxf86misc-dev libxxf86misc1 libxxf86vm-dev libxxf86vm1
  libzephyr3 libzvbi0 limewire-basic linux-generic linux-headers-2.6.22-14
  linux-headers-2.6.22-14-generic linux-headers-generic
  linux-image-2.6.20-16-generic linux-image-2.6.22-14-generic
  linux-image-generic linux-restricted-modules-2.6.20-16-generic
  linux-restricted-modules-2.6.22-14-generic linux-restricted-modules-common
  linux-restricted-modules-generic linux-sound-base
  linux-ubuntu-modules-2.6.22-14-generic listres locales login logrotate
  lsb-base lsb-release lshw lsof ltrace m4 make makedev man-db mawk maxima
  mcpp mencoder mesa-utils metacity metacity-common mii-diag min12xxw mkisofs
  mktemp module-init-tools mono mono-common mono-gac mono-jit mono-mcs
  mono-runtime mount mozilla-firefox-locale-ar mozilla-firefox-locale-en-gb
  mozilla-mplayer mpeglib mplayer mplayer-fonts mscompress msttcorefonts
  mtr-tiny myspell-en-gb myspell-en-us myspell-en-za nano nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto ncurses-base ncurses-bin
  net-tools netbase netcat network-manager network-manager-gnome
  notification-daemon ntfs-3g ntpdate nvidia-glx-new
  nvidia-kernel-2.6.20-16-generic nvidia-kernel-common
  nvidia-new-kernel-source o3read oclock odbcinst1debian1 odf-converter
  onboard openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-style-human
  openoffice.org-writer openssh-client openssl orange parted passwd patch
  pciutils pcmciautils perl perl-base perl-modules pia pidgin pkg-config
  pnm2ppa po-debconf poppler-utils popularity-contest
  powermanagement-interface powermgmt-base powernowd ppp pppconfig pppoeconf
  procps psmisc pxljr python python-apport python-apt python-at-spi
  python-bittorrent python-cairo python-central python-compizconfig
  python-crypto python-cups python-dbus python-gconf python-gdbm python-glade2
  python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras
  python-gnomecanvas python-gnupginterface python-gobject python-gst0.10
  python-gtk2 python-gtkhtml2 python-imaging python-launchpad-bugs
  python-launchpad-integration python-libxml2 python-minimal python-notify
  python-numeric python-orca-brlapi python-problem-report
  python-pygtksourceview python-pyorbit python-qt3 python-reportlab
  python-sexy python-sip4 python-software-properties python-support
  python-twisted python-twisted-bin python-twisted-conch python-twisted-core
  python-twisted-lore python-twisted-mail python-twisted-names
  python-twisted-news python-twisted-runner python-twisted-web
  python-twisted-words python-uno python-virtkey python-vte python-xdg
  python-xml python-zopeinterface python2.5 python2.5-dev python2.5-minimal
  qorganizer quicktime-utils quicktime-x11utils radeontool rdesktop readahead
  reiserfsprogs restricted-manager restricted-manager-core rhythmbox rpm
  rss-glx rsync samba-common scantv scim scim-gtk2-immodule
  scim-modules-socket scim-modules-table scim-tables-additional screen
  screensaver-default-images scrollkeeper sed serpentine sessreg sgml-base
  sgml-data shared-mime-info sharutils skype slocate smartdimmer smbclient
  smproxy software-properties-gtk sound-juicer splix ssh-askpass-gnome
  ssl-cert startup-tasks strace subversion sudo sun-java5-bin sun-java5-jre
  sun-java6-bin sun-java6-jre sun-java6-plugin sunbird synaptic sysklogd
  system-config-printer system-services system-tools-backends sysvutils
  tangerine-icon-theme tango-generator tango-icon-theme-common tar tasksel
  tasksel-data tcl8.4 tcltls tcpd tcpdump telnet tennix time timidity tk8.4
  tomboy toshset totem totem-gstreamer totem-mozilla tracker
  tracker-search-tool tsclient ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming
  ttf-baekmuk ttf-bengali-fonts ttf-bitstream-vera ttf-dejavu ttf-dejavu-core
  ttf-dejavu-extra ttf-devanagari-fonts ttf-freefont ttf-gentium
  ttf-gujarati-fonts ttf-indic-fonts ttf-indic-fonts-core ttf-kannada-fonts
  ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen
  ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts
  ttf-thai-tlwg ttf-unfonts-core tuxguitar tuxguitar-alsa tzdata ubufox
  ubuntu-artwork ubuntu-docs ubuntu-keyring ubuntu-standard ucf udev
  unattended-upgrades unixodbc unrar unzip update-inetd update-manager
  update-manager-core update-notifier upstart upstart-compat-sysv upstart-logd
  usbutils usplash usplash-theme-ubuntu util-linux util-linux-locales v4l-conf
  vamps vbetool viewres vim-common vim-tiny vino vlc vlc-nox vnc-common
  volumeid w32codecs w3m wamerican wbritish wget whiptail whois wine
  wine-doors wireless-tools wodim wormux wormux-data wpasupplicant wvdial
  wx-common wxmaxima x-ttcidfont-conf x11-common x11perf
  x11proto-composite-dev x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-record-dev x11proto-xext-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev xauth xaw3dg xawtv
  xawtv-plugins xbase-clients xbiff xbitmaps xcalc xchat-gnome
  xchat-gnome-common xclipboard xclock xconsole xcursorgen xdg-user-dirs
  xdg-user-dirs-gtk xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable
  xfonts-utils xfontsel xgamma xgc xhost xinit xkbutils xkill xload xlogo
  xlsatoms xlsclients xlsfonts xmag xman xmessage xml-core xmms xmms-infopipe
  xmodmap xmore xmoto xorg xpmutils xprop xrandr xrdb xrefresh xresprobe xrgb
  xsane xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-elographics
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-amd
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-i810
  xserver-xorg-video-imstt xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-newport
  xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-psb
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xset xsetmode
  xsetpointer xsetroot xsltproc xsm xstdcmap xterm xtrans-dev xtrap xutils
  xutils-dev xvidtune xvinfo xvnc4viewer xvncviewer xwd xwininfo xwud yelp
  zenity zip zlib1g
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt)
  base-files base-passwd (due to base-files) libpam-modules (due to
  base-files) bash debianutils (due to bash) libncurses5 (due to bash)
  bsdutils coreutils libacl1 (due to coreutils) libselinux1 (due to coreutils)
  diff dpkg e2fsprogs e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs)
  libcomerr2 (due to e2fsprogs) libss2 (due to e2fsprogs) libuuid1 (due to
  e2fsprogs) findutils grep gzip hostname login libpam0g (due to login)
  libpam-runtime (due to login) mktemp mount ncurses-base ncurses-bin
  perl-base python-minimal python2.5-minimal (due to python-minimal) sed
  sysvutils libsepol1 (due to sysvutils) tar util-linux lsb-base (due to
  util-linux) tzdata (due to util-linux) libslang2 (due to util-linux) zlib1g
  (due to util-linux)
0 upgraded, 0 newly installed, 1392 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 3119MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

```

removing this would screw up my whole OS!

---

### Post by alsamman on 2008-02-01
bump

---

### Post by zvacet on 2008-02-01
You can find it [here](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libc6&searchon=names&subword=1&version=gutsy&release=all).Be sure that you have dependencies installed.Download package and install it like this

```
sudo dpkg -i **packagename**
```

---

### Post by alsamman on 2008-02-01
thank you so much, everything works great:)

---

### Post by NickEvans on 2008-03-14
Worked fine for me too. Saved my whole system :)

---

