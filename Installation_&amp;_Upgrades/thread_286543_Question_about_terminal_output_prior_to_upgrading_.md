---
title: "Question about terminal output prior to upgrading Xubuntu"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Cable on 2006-10-27
I'm about to upgrade Xubuntu 6.06.1 to 6.10.  I edited sources.list and changed all instances of dapper to edgy, I have the alternate CD so I added that as well.  Then, I did
```

sudo aptitude update && sudo aptitude dist-upgrade && sudo aptitude dist-upgrade

```as instructed [here]("https://help.ubuntu.com/community/EdgyUpgrades").  Then aptitude outputs everything as follows (it's long, my apologies)
```

user@user:~$ sudo aptitude update && sudo aptitude dist-upgrade & & sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Get:2 http://security.ubuntu.com edgy-security Release.gpg [189B]
Hit http://www.getautomatix.com edgy Release
Hit http://security.ubuntu.com edgy-security Release
Hit http://www.getautomatix.com edgy/main Packages
Get:3 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Get:4 http://us.archive.ubuntu.com edgy-updates Release.gpg [189B]
Get:5 http://deb.opera.com stable Release.gpg [189B]
Hit http://security.ubuntu.com edgy-security/main Packages
Get:6 http://us.archive.ubuntu.com edgy-backports Release.gpg [189B]
Hit http://deb.opera.com stable Release
Hit http://us.archive.ubuntu.com edgy Release
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Ign http://deb.opera.com stable/non-free Packages
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://deb.opera.com stable/non-free Packages
Hit http://us.archive.ubuntu.com edgy-backports Release
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-backports/main Packages
Hit http://us.archive.ubuntu.com edgy-backports/restricted Packages
Hit http://us.archive.ubuntu.com edgy-backports/universe Packages
Hit http://us.archive.ubuntu.com edgy-backports/multiverse Packages
Fetched 6B in 3s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gamin hpijs libgnutls-dev libvte4 upstart
The following packages are unused and will be REMOVED:
  ethereal-common x-dev
The following NEW packages will be automatically installed:
  acroread-escript alacarte app-install-data app-install-data-commercial apport apport-gtk capplets-data console-setup console-terminus cpp-4.1
  cupsys-common dash deskbar-applet desktop-base edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes edgy-wallpapers evolution-data-server
  evolution-data-server-common fam fontconfig-config g++-4.1 gcalctool-gtk gcc-4.1 gcc-4.1-base gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-control-center gnome-desktop-data gnome-media-common gnome-menus gnome-netstatus-applet gnome-panel gnome-panel-data
  gnome-power-manager gnome-session gnome-system-monitor gnome-utils gnome2-user-guide gray-theme gstreamer0.10-alsa gtk2-engines gxine
  human-cursors-theme human-gtk-theme human-icon-theme human-theme hwdb-client-common hwdb-client-gnome imagemagick industrial-cursor-theme
  industrialtango-theme legacyhuman-theme libavcodec0d libavformat0d libcairo-perl libcairomm-1.0-1 libcamel1.2-8 libchewing3 libchewing3-data libdb4.4
  libdbus-1-3 libdbus-glib-1-dev libdirectfb-0.9-24 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libegroupwise1.2-12 libgadu3 libgail18 libgcj7-0 libgii1 libgii1-target-x libgksu2-0 libgl1-mesa-glx libgnome-media0
  libgnome-window-settings1 libgnomevfs2-extra libgnutls13 libgoffice-0-common libgoffice-gtk-0-3 libgsf-1-114 libgtop2-common libgucharmap5
  libiec61883-0 libjasper-1.701-1 liblpint-bonobo0 liblzo-dev libmagick9 libmeanwhile1 libmyspell3c2 libnautilus-burn4 libnet-dbus-perl libnewt0.52
  liboobs-1-2 libparted1.7-1 libpci2 libpostproc0d libraw1394-8 libselinux1-dev libsensors-dev libsensors3 libsepol1-dev libstdc++6-4.1-dev libtasn1-3
  libtasn1-3-bin libthunar-vfs-1-2 libvisual-0.4-0 libvisual-0.4-plugins libvlc0 libvolumeid0 libvte9 libwxbase2.6-0 libx11-data libxine1 libxklavier11
  libxml-grove-perl libxml-perl libxosd2 linux-generic linux-image-2.6.17-10-generic linux-image-generic linux-libc-dev
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-generic menu-xdg metacity metacity-common mktemp music-applet nautilus
  nautilus-cd-burner nautilus-data onboard openoffice.org-style-industrial outdoors-theme portmap python-apport-utils python-beagle python-cairo
  python-central python-cups python-dbus python-exo python-gconf python-gdbm python-gmenu python-gnome2 python-gnome2-extras python-gnomecanvas
  python-gobject python-gtkhtml2 python-imaging python-numeric python-problem-report python-pyorbit python-soappy python-support python-virtkey
  python-xdg python-xml resilience-theme silicon-theme startup-tasks system-config-printer system-services sysvutils tasksel tasksel-data
  thunar-archive-plugin tshark tzdata update-notifier upstart-compat-sysv upstart-logd util-linux-locales vim-tiny vlc-nox volumeid wireshark-common
  xbitmaps xfce4-dict-plugin xfce4-notes-plugin xfce4-smartbookmark-plugin xfonts-encodings xkb-data xorg xtrans-dev xutils-dev
The following packages will be automatically REMOVED:
  imake libgcj7 libgii0 libgii0-target-x libgl1-mesa libnewt0.51 linux-kernel-headers makedepend python2.4-apt python2.4-cairo python2.4-dbus
  python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 python2.4-imaging
  python2.4-libxml2 python2.4-numeric python2.4-pyorbit
The following NEW packages will be installed:
  acroread-escript alacarte app-install-data app-install-data-commercial apport apport-gtk capplets-data console-setup console-terminus cpp-4.1
  cupsys-common dash deskbar-applet desktop-base edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes edgy-wallpapers evolution-data-server
  evolution-data-server-common fam fontconfig-config g++-4.1 gcalctool-gtk gcc-4.1 gcc-4.1-base gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-control-center gnome-desktop-data gnome-media-common gnome-menus gnome-netstatus-applet gnome-panel gnome-panel-data
  gnome-power-manager gnome-session gnome-system-monitor gnome-utils gnome2-user-guide gray-theme gstreamer0.10-alsa gtk2-engines gxine
  human-cursors-theme human-gtk-theme human-icon-theme human-theme hwdb-client-common hwdb-client-gnome imagemagick industrial-cursor-theme
  industrialtango-theme legacyhuman-theme libavcodec0d libavformat0d libcairo-perl libcairomm-1.0-1 libcamel1.2-8 libchewing3 libchewing3-data libdb4.4
  libdbus-1-3 libdbus-glib-1-dev libdirectfb-0.9-24 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libegroupwise1.2-12 libgadu3 libgail18 libgcj7-0 libgii1 libgii1-target-x libgksu2-0 libgl1-mesa-glx libgnome-media0
  libgnome-window-settings1 libgnomevfs2-extra libgnutls13 libgoffice-0-common libgoffice-gtk-0-3 libgsf-1-114 libgtop2-common libgucharmap5
  libiec61883-0 libjasper-1.701-1 liblpint-bonobo0 liblzo-dev libmagick9 libmeanwhile1 libmyspell3c2 libnautilus-burn4 libnet-dbus-perl libnewt0.52
  liboobs-1-2 libparted1.7-1 libpci2 libpostproc0d libraw1394-8 libselinux1-dev libsensors-dev libsensors3 libsepol1-dev libstdc++6-4.1-dev libtasn1-3
  libtasn1-3-bin libthunar-vfs-1-2 libvisual-0.4-0 libvisual-0.4-plugins libvlc0 libvolumeid0 libvte9 libwxbase2.6-0 libx11-data libxine1 libxklavier11
  libxml-grove-perl libxml-perl libxosd2 linux-generic linux-image-2.6.17-10-generic linux-image-generic linux-libc-dev
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-generic menu-xdg metacity metacity-common mktemp music-applet nautilus
  nautilus-cd-burner nautilus-data onboard openoffice.org-style-industrial outdoors-theme portmap python-apport-utils python-beagle python-cairo
  python-central python-cups python-dbus python-exo python-gconf python-gdbm python-gmenu python-gnome2 python-gnome2-extras python-gnomecanvas
  python-gobject python-gtkhtml2 python-imaging python-numeric python-problem-report python-pyorbit python-soappy python-support python-virtkey
  python-xdg python-xml resilience-theme silicon-theme startup-tasks system-config-printer system-services sysvutils tasksel tasksel-data
  thunar-archive-plugin tshark tzdata update-notifier upstart-compat-sysv upstart-logd util-linux-locales vim-tiny vlc-nox volumeid wireshark-common
  xbitmaps xfce4-dict-plugin xfce4-notes-plugin xfce4-smartbookmark-plugin xfonts-encodings xkb-data xorg xtrans-dev xutils-dev
The following packages will be REMOVED:
  imake libgcj7 libgii0 libgii0-target-x libgl1-mesa libnewt0.51 linux-kernel-headers makedepend python2.4-apt python2.4-cairo python2.4-dbus
  python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 python2.4-imaging
  python2.4-libxml2 python2.4-numeric python2.4-pyorbit
The following packages will be upgraded:
  abiword abiword-common abiword-plugins acpi-support acpid acroread adduser alsa-base alsa-oss alsa-utils anacron anthy apmd apt apt-file apt-utils
  aptitude aspell at autoconf automake1.9 autotools-dev avahi-daemon base-files bash belocs-locales-bin bind9-host binutils binutils-static bitmap
  bomberclone bomberclone-data bsdmainutils bsdutils bsh build-essential bum busybox-initramfs bzip2 cdda2wav cdparanoia cdrdao cdrecord checkinstall
  console-common console-data console-tools coreutils cpio cpp cpp-4.0 cron cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dbus-1-utils
  debconf debconf-i18n debconf-utils debhelper debianutils defoma desktop-file-utils dhcp3-client dhcp3-common dictionaries-common discover1
  discover1-data dmidecode dmsetup dnsutils doc-base docbook-xml dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs eject epiphany-browser
  epiphany-extensions evince-gtk evms evms-ncurses example-content fastjar fdutils ffmpeg file findutils finger firefox flashplugin-nonfree fontconfig
  foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fping freeglut3 fstobdf g++
  g++-4.0 g-wrap gaim gaim-data gaim-extendedprefs gaim-guifications gcc gcc-3.3-base gcc-4.0 gcc-4.0-base gcj-4.1-base gconf2 gconf2-common gdebi gdm
  gedit-common gettext gettext-base giblib1 gij-4.1 gimp gimp-data gimp-print gksu gnome-doc-utils gnome-games gnome-games-data gnome-games-extra-data
  gnome-icon-theme gnome-keyring gnome-media gnome-mime-data gnome-sudoku gnumeric-common gnumeric-gtk gnupg gparted grep groff-base grub gs-esp
  gsfonts-other gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gtk2-engines-clearlooks
  gtk2-engines-industrial gtk2-engines-mist gtk2-engines-smooth gtk2-engines-ubuntulooks gtk2-engines-xfce guile-1.6 guile-1.6-dev guile-1.6-libs
  guile-1.6-slib guile-g-wrap gwget gzip hal hal-device-manager hdparm hostname hotkey-setup hplip hplip-data hwdata icewm icewm-common
  icewm-gnome-support ijsgutenprint imlib-base imlib11 info initramfs-tools initscripts intltool intltool-debian iproute iptables iputils-arping
  iputils-ping iputils-tracepath irssi iso-codes jackd java-common java-gcj-compat klibc-utils klogd lame language-pack-en language-pack-en-base
  language-selector language-selector-common laptop-mode-tools launchpad-integration less lftp liba52-0.7.4 libacl1 libaiksaurus-1.2-0c2a
  libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a liballegro4.2 liballegro4.2-plugin-jack libanthy0 libao2 libapm1 libapt-pkg-perl libartsc0 libasound2
  libaspell15 libatk1.0-0 libatk1.0-dev libattr1 libaudio2 libavahi-client-dev libavahi-client3 libavahi-common-data libavahi-common-dev
  libavahi-common3 libavahi-core4 libavahi-glib-dev libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbind9-0 libblkid1 libbonobo2-0
  libbonobo2-common libbonobo2-dev libbonoboui2-0 libbonoboui2-common libbonoboui2-dev libbz2-1.0 libc6 libc6-dev libc6-i686 libcairo2 libcairo2-dev
  libcdparanoia0 libcomerr2 libconsole libcupsimage2 libcupsys2 libcupsys2-dev libcurl3 libcurl3-gnutls libcurses-ui-perl libdb3 libdbus-1-dev
  libdbus-glib-1-2 libdc1394-13 libdevmapper1.02 libdiscover1 libdjvulibre15 libdmx1 libdns21 libdrm2 libdv4 libdvbpsi4 libdvdplay0 libdvdread3
  libeel2-2 libeel2-data libelfg0 libevms-2.5 libexif12 libexo-0.3-0 libexpat1 libexpat1-dev libffi4 libffi4-dev libflac7 libfltk1.1 libfontconfig1
  libfontconfig1-dev libfontenc1 libfreetype6 libfreetype6-dev libfribidi0 libfs6 libgail-common libgail-dev libgamin0 libgc1c2 libgcc1 libgcj-common
  libgcj7-jar libgconf2-4 libgconf2-dev libgcrypt11 libgcrypt11-dev libgda2-3 libgda2-common libgdbm3 libgdl-1-0 libgdl-1-common libgdome2-0
  libgdome2-cpp-smart0c2a libggi2 libgimp2.0 libgksu1.2-1 libgl1-mesa-dri libglade2-0 libglade2-dev libglib-perl libglib2.0-0 libglib2.0-data
  libglib2.0-dev libglibmm-2.4-1c2a libglu1-mesa libgnome-desktop-2 libgnome-keyring-dev libgnome-keyring0 libgnome-menu2 libgnome2-0 libgnome2-common
  libgnome2-dev libgnomecanvas2-0 libgnomecanvas2-common libgnomecanvas2-dev libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprint2.2-dev libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeprintui2.2-dev libgnomeui-0 libgnomeui-common libgnomeui-dev
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-dev libgnucrypto-java libgnutls12 libgpg-error-dev libgpg-error0 libgphoto2-2 libgphoto2-port0
  libgpmg1 libgpod-common libgpod0 libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgstreamer0.8-0 libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libgtkhtml2-0 libgtkhtml2-dev libgtkhtml3.8-15 libgtkhtml3.8-dev libgtkmathview0c2a libgtkmm-2.4-1c2a
  libgtksourceview-common libgtksourceview1.0-0 libgtop2-7 libguile-ltdl-1 libgutenprint2 libgutenprintui2-1 libgwrap-runtime0 libgwrap-runtime0-dev
  libhal-storage1 libhal1 libhsqldb-java libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libice-dev libice6 libidl-dev libidl0 libidn11
  libieee1284-3 libijs-0.35 libimlib2 libisc11 libisccc0 libisccfg1 libiw28 libjack0.100.0-0 libjaxp1.2-java libjessie-java libjline-java libjpeg-progs
  libjpeg62 libjpeg62-dev libklibc libkpathsea4 libkrb53 liblame0 liblaunchpad-integration0 liblcms1 libldap2 liblircclient0 liblockfile1
  liblog4j1.2-java libltdl3 libltdl3-dev liblwres9 libmagic1 libmailtools-perl libmdbtools libmetacity0 libmjpegtools0c2a libmms0 libmng1 libmudflap0
  libmudflap0-dev libmusicbrainz4c2a libnautilus-extension1 libncurses5 libncurses5-dev libncursesw5 libnotify1 libnspr4 libnss3 libogg0 liboggflac3
  liboil0.3 libopencdk8 libopencdk8-dev liborbit2 liborbit2-dev libosp5 libpam-modules libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpango1.0-dev libpaper1 libpcap0.8 libpcre3 libperl5.8 libpng12-0 libpng12-dev libpoppler1 libpoppler1-glib libpopt-dev libpopt0
  libqt3-mt libqthreads-12 libquicktime0 librpm4 librsvg2-2 librsvg2-common libsane libsasl2 libsasl2-modules libscim8c2a libsdl-image1.2 libsdl-net1.2
  libsdl-ttf2.0-0 libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsepol1 libservlet2.3-java libsexy2 libshout3 libslang2 libsm-dev libsm6
  libsmbclient libsmpeg0 libsndfile1 libsnmp-base libsnmp-perl libsnmp9 libsnmp9-dev libsoup2.2-8 libspeex1 libsqlite3-0 libss2 libssl-dev libssl0.9.8
  libstdc++5 libstdc++6 libstdc++6-4.0-dev libstlport4.6c2 libswfdec0.3 libsysfs2 libtag1c2a libtagc0 libtasn1-2 libtasn1-2-dev libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libtheora0 libtiff4 libtool libtotem-plparser1 libungif4g libuniconf4.2 liburi-perl
  libusb-0.1-4 libusb-dev libuuid1 libvcdinfo0 libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common libwmf0.2-7 libwnck-common libwnck18
  libwpd-stream8c2a libwpd8c2a libwrap0 libwrap0-dev libwvstreams4.2-base libwvstreams4.2-extras libwww-perl libwxgtk2.6-0 libx11-6 libx11-dev
  libxalan2-java libxau-dev libxau6 libxaw7 libxcomposite1 libxcursor-dev libxcursor1 libxdamage1 libxdmcp-dev libxdmcp6 libxerces2-java libxext-dev
  libxext6 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxfixes-dev libxfixes3 libxfont1 libxft-dev libxft2 libxi-dev libxi6
  libxine-extracodecs libxine-main1 libxinerama-dev libxinerama1 libxkbfile1 libxml1 libxml2 libxml2-dev libxml2-utils libxmlsec1 libxmlsec1-nss
  libxmlsec1-openssl libxmu6 libxmuu1 libxp6 libxpm4 libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxslt1.1 libxss1 libxt-java libxt6
  libxtrap6 libxtst6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-686 linux-image-686 linux-restricted-modules-686
  linux-restricted-modules-common linux-sound-base locales login logrotate lsb lsb-base lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-release lshw lsof
  ltrace lvm-common lvm2 maelstrom make makedev manpages mawk mcpp mdadm memtest86+ mencoder menu mesa-utils mii-diag mime-support mjpegtools mkisofs
  module-init-tools mount mousepad mozilla-acroread mozilla-firefox-locale-en-gb mozilla-mplayer mozilla-thunderbird mplayer mtr-tiny myspell-en-gb
  myspell-en-us nano ncurses-base ncurses-bin ncurses-term net-tools netbase netcat njam notification-daemon ntp ntp-server ntp-simple ntpdate numlockx
  nvidia-glx nvidia-kernel-common odbcinst1debian1 openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-us openoffice.org-l10n-en-za openoffice.org-math openoffice.org-thesaurus-en-us
  openoffice.org-writer openssh-client openssh-server openssl orage orbit2 p7zip parted passwd patch pciutils pcmciautils perl perl-base perl-modules
  pioneers-ai pioneers-client pioneers-help pioneers-meta-server pioneers-server-console pioneers-server-data pioneers-server-gtk pipenightdreams
  pipenightdreams-data planetpenguin-racer planetpenguin-racer-data planetpenguin-racer-extras plib1.8.4c2 pmount pnm2ppa po-debconf poppler-utils
  popularity-contest postfix powermgmt-base powernowd ppp pppconfig pppoeconf procps psmisc python python-apt python-glade2 python-gnome2-desktop
  python-gnupginterface python-gtk-1.2 python-gtk2 python-launchpad-integration python-libxml2 python-minimal python-pyao python-uno python-vte
  python2.4 python2.4-dev python2.4-minimal rar readahead reiserfsprogs reportbug rhythmbox rhythmbox-applet rpm rsync samba-common sane-utils scim
  scim-anthy scim-chewing scim-gtk2-immodule scim-hangul scim-modules-socket scim-pinyin scorched3d scorched3d-data scorched3d-doc sed shared-mime-info
  slib slocate smbclient ssh strace sudo sun-java5-bin sun-java5-jre sun-java5-plugin supertux supertux-data synaptic sysklogd system-tools-backends
  sysv-rc sysv-rc-conf sysvinit tango-icon-theme tango-icon-theme-common tar tcl8.4 tcpd tcpdump tethereal thunar thunar-media-tags-plugin tofrodos
  toshset totem-xine ttf-arabeyes ttf-arphic-ukai ttf-bengali-fonts ttf-bitstream-vera ttf-dejavu ttf-devanagari-fonts ttf-freefont ttf-gentium
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-larabie-deco ttf-larabie-straight
  ttf-larabie-uncommon ttf-malayalam-fonts ttf-opensymbol ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts tuxkart tuxkart-data
  ubuntu-artwork ubuntu-minimal ubuntu-sounds ubuntu-standard ucf udev unattended-upgrades unixodbc unzip update-manager usbutils usplash util-linux
  vbetool videolan-doc vim vim-common vim-runtime vlc vlc-plugin-alsa vlc-plugin-esd vorbis-tools wget whiptail wing wing-data wireless-tools
  wpasupplicant wvdial wxvlc x-ttcidfont-conf x-window-system-core x11-common x11perf x11proto-core-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xarchiver xbase-clients xcursor-themes xcursorgen
  xdriinfo xev xfburn xfce4-appfinder xfce4-battery-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager
  xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-panel xfce4-screenshooter-plugin xfce4-session xfce4-taskmanager xfce4-terminal xfce4-utils
  xfdesktop4 xfmedia xfonts-100dpi xfonts-75dpi xfonts-base xfonts-intl-european xfonts-scalable xfonts-utils xfprint4 xfsprogs xfwm4 xfwm4-themes
  xhost xinit xkbutils xkeyboard-config xml-core xmodmap xpmutils xprop xrandr xrdb xrefresh xresprobe xsane xsane-common xscorch xscreensaver
  xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-elographics xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-wacom xset xsltproc xterm xtrap
  xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-system-tools xutils yelp zenity zip zlib1g zlib1g-dev
930 packages upgraded, 196 newly installed, 23 to remove and 0 not upgraded.
Need to get 355MB/808MB of archives. After unpacking 458MB will be used.
The following packages have unmet dependencies:
  gamin: Conflicts: fam but 2.7.0-10ubuntu1 is to be installed.
  hpijs: Conflicts: hplip-ppds (< 1.6.9-0ubuntu2) but 0.9.7-4ubuntu1 is installed.
  libgnutls-dev: Depends: libtasn1-3-dev (>= 0.3.4) but it is not installable
  libvte4: Depends: libvte-common (= 1:0.12.2-0ubuntu1) but 1:0.14.1-0ubuntu1 is to be installed.
  upstart: Conflicts: sysvinit but 2.86.ds1-14.1ubuntu16 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libvte4

Install the following packages:
gnome-themes [2.16.1.1-0ubuntu1 (edgy)]
linuxprinting.org-ppds [20060918-0ubuntu2 (edgy)]
openoffice.org-style-crystal [2.0.4-0ubuntu2 (edgy)]
openoffice.org-style-default [2.0.4-0ubuntu2 (edgy, edgy)]
openoffice.org-style-hicontrast [2.0.4-0ubuntu2 (edgy)]
python-reportlab [2.0dfsg-1 (edgy)]

Keep the following packages at their current version:
fam [Not Installed]
hpijs [2.1.7+0.9.7-4ubuntu1 (now)]
laptop-mode-tools [1.11-1ubuntu3 (now)]
libgda2-3 [1.2.2-1ubuntu2 (now)]
libgnutls-dev [1.2.9-2ubuntu1.1 (now)]
libgnutls12 [1.2.9-2ubuntu1.1 (now)]
p7zip [4.30.dfsg-1 (now)]
rhythmbox [0.9.3.1-0ubuntu9 (now)]
startup-tasks [Not Installed]
system-services [Not Installed]
totem-xine [1.4.3-0ubuntu1 (now)]
ubuntu-minimal [0.120 (now)]
upstart [Not Installed]
upstart-compat-sysv [Not Installed]
upstart-logd [Not Installed]
xubuntu-desktop [1.32 (now)]

Leave the following dependencies unresolved:
nautilus recommends fam
Score is -1376

Accept this solution? [Y/n/q/?]

```A couple things here worry me:
This...
```

The following packages are BROKEN:
  gamin hpijs libgnutls-dev libvte4 upstart

```and this...
```

The following packages have unmet dependencies:
  gamin: Conflicts: fam but 2.7.0-10ubuntu1 is to be installed.
  hpijs: Conflicts: hplip-ppds (< 1.6.9-0ubuntu2) but 0.9.7-4ubuntu1 is installed.
  libgnutls-dev: Depends: libtasn1-3-dev (>= 0.3.4) but it is not installable
  libvte4: Depends: libvte-common (= 1:0.12.2-0ubuntu1) but 1:0.14.1-0ubuntu1 is to be installed.
  upstart: Conflicts: sysvinit but 2.86.ds1-14.1ubuntu16 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libvte4

Install the following packages:
gnome-themes [2.16.1.1-0ubuntu1 (edgy)]
linuxprinting.org-ppds [20060918-0ubuntu2 (edgy)]
openoffice.org-style-crystal [2.0.4-0ubuntu2 (edgy)]
openoffice.org-style-default [2.0.4-0ubuntu2 (edgy, edgy)]
openoffice.org-style-hicontrast [2.0.4-0ubuntu2 (edgy)]
python-reportlab [2.0dfsg-1 (edgy)]

Keep the following packages at their current version:
fam [Not Installed]
hpijs [2.1.7+0.9.7-4ubuntu1 (now)]
laptop-mode-tools [1.11-1ubuntu3 (now)]
libgda2-3 [1.2.2-1ubuntu2 (now)]
libgnutls-dev [1.2.9-2ubuntu1.1 (now)]
libgnutls12 [1.2.9-2ubuntu1.1 (now)]
p7zip [4.30.dfsg-1 (now)]
rhythmbox [0.9.3.1-0ubuntu9 (now)]
startup-tasks [Not Installed]
system-services [Not Installed]
totem-xine [1.4.3-0ubuntu1 (now)]
ubuntu-minimal [0.120 (now)]
upstart [Not Installed]
upstart-compat-sysv [Not Installed]
upstart-logd [Not Installed]
xubuntu-desktop [1.32 (now)]

Leave the following dependencies unresolved:
nautilus recommends fam
Score is -1376

Accept this solution? [Y/n/q/?]

```I don't really know how to interpret these messages.  I don't know if they're bad, or if it's just part of the upgrade and will fix itself.  I'm going to hold off on saying yes until I get an answer about this.

What do you think?  Does it look okay or no?

EDIT:  Another thing....I just noticed that it's installing a **bunch** of GNOME stuff (gnome-applets, gnome-panel, nautilus, etc.).  Why?  This computer is running Xubuntu.

---

### Post by Cable on 2006-10-27
This is interesting.  If I remove the alternate CD from sources.list, the terminal outputs different stuff.  Here it is...
```

user@user:~$ sudo aptitude update && sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Get:2 http://deb.opera.com stable Release.gpg [189B]
Hit http://www.getautomatix.com edgy Release
Get:3 http://security.ubuntu.com edgy-security Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Hit http://security.ubuntu.com edgy-security Release
Hit http://deb.opera.com stable Release
Hit http://www.getautomatix.com edgy/main Packages
Hit http://security.ubuntu.com edgy-security/main Packages
Ign http://deb.opera.com stable/non-free Packages
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Hit http://deb.opera.com stable/non-free Packages
Get:5 http://us.archive.ubuntu.com edgy-updates Release.gpg [189B]
Get:6 http://us.archive.ubuntu.com edgy-backports Release.gpg [189B]
Hit http://us.archive.ubuntu.com edgy Release
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://us.archive.ubuntu.com edgy-backports Release
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-backports/main Packages
Hit http://us.archive.ubuntu.com edgy-backports/restricted Packages
Hit http://us.archive.ubuntu.com edgy-backports/universe Packages
Hit http://us.archive.ubuntu.com edgy-backports/multiverse Packages
Fetched 6B in 5s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gamin hpijs libgnutls-dev libvte4 upstart
The following packages are unused and will be REMOVED:
  ethereal-common x-dev
The following NEW packages will be automatically installed:
  acroread-escript alacarte app-install-data app-install-data-commercial apport apport-gtk capplets-data console-setup console-terminus cpp-4.1
  cupsys-common dash deskbar-applet desktop-base edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes edgy-wallpapers evolution-data-server
  evolution-data-server-common fam fontconfig-config g++-4.1 gcalctool-gtk gcc-4.1 gcc-4.1-base gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-control-center gnome-desktop-data gnome-media-common gnome-menus gnome-netstatus-applet gnome-panel gnome-panel-data
  gnome-power-manager gnome-session gnome-system-monitor gnome-utils gnome2-user-guide gray-theme gstreamer0.10-alsa gtk2-engines gxine
  human-cursors-theme human-gtk-theme human-icon-theme human-theme hwdb-client-common hwdb-client-gnome imagemagick industrial-cursor-theme
  industrialtango-theme legacyhuman-theme libavcodec0d libavformat0d libcairo-perl libcairomm-1.0-1 libcamel1.2-8 libchewing3 libchewing3-data libdb4.4
  libdbus-1-3 libdbus-glib-1-dev libdirectfb-0.9-24 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libegroupwise1.2-12 libgadu3 libgail18 libgcj7-0 libgii1 libgii1-target-x libgksu2-0 libgl1-mesa-glx libgnome-media0
  libgnome-window-settings1 libgnomevfs2-extra libgnutls13 libgoffice-0-common libgoffice-gtk-0-3 libgsf-1-114 libgtop2-common libgucharmap5
  libiec61883-0 libjasper-1.701-1 liblpint-bonobo0 liblzo-dev libmagick9 libmeanwhile1 libmyspell3c2 libnautilus-burn4 libnet-dbus-perl libnewt0.52
  liboobs-1-2 libparted1.7-1 libpci2 libpostproc0d libraw1394-8 libselinux1-dev libsensors-dev libsensors3 libsepol1-dev libstdc++6-4.1-dev libtasn1-3
  libtasn1-3-bin libthunar-vfs-1-2 libvisual-0.4-0 libvisual-0.4-plugins libvlc0 libvolumeid0 libvte9 libwxbase2.6-0 libx11-data libxine1 libxklavier11
  libxml-grove-perl libxml-perl libxosd2 linux-generic linux-image-2.6.17-10-generic linux-image-generic linux-libc-dev
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-generic menu-xdg metacity metacity-common mktemp music-applet nautilus
  nautilus-cd-burner nautilus-data onboard openoffice.org-style-industrial outdoors-theme portmap python-apport-utils python-beagle python-cairo
  python-central python-cups python-dbus python-exo python-gconf python-gdbm python-gmenu python-gnome2 python-gnome2-extras python-gnomecanvas
  python-gobject python-gtkhtml2 python-imaging python-numeric python-problem-report python-pyorbit python-soappy python-support python-virtkey
  python-xdg python-xml resilience-theme silicon-theme startup-tasks system-config-printer system-services sysvutils tasksel tasksel-data
  thunar-archive-plugin tshark tzdata update-notifier upstart-compat-sysv upstart-logd util-linux-locales vim-tiny vlc-nox volumeid wireshark-common
  xbitmaps xfce4-dict-plugin xfce4-notes-plugin xfce4-smartbookmark-plugin xfonts-encodings xkb-data xorg xtrans-dev xutils-dev
The following packages will be automatically REMOVED:
  imake libgcj7 libgii0 libgii0-target-x libgl1-mesa libnewt0.51 linux-kernel-headers makedepend python2.4-apt python2.4-cairo python2.4-dbus
  python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 python2.4-imaging
  python2.4-libxml2 python2.4-numeric python2.4-pyorbit
The following NEW packages will be installed:
  acroread-escript alacarte app-install-data app-install-data-commercial apport apport-gtk capplets-data console-setup console-terminus cpp-4.1
  cupsys-common dash deskbar-applet desktop-base edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes edgy-wallpapers evolution-data-server
  evolution-data-server-common fam fontconfig-config g++-4.1 gcalctool-gtk gcc-4.1 gcc-4.1-base gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-control-center gnome-desktop-data gnome-media-common gnome-menus gnome-netstatus-applet gnome-panel gnome-panel-data
  gnome-power-manager gnome-session gnome-system-monitor gnome-utils gnome2-user-guide gray-theme gstreamer0.10-alsa gtk2-engines gxine
  human-cursors-theme human-gtk-theme human-icon-theme human-theme hwdb-client-common hwdb-client-gnome imagemagick industrial-cursor-theme
  industrialtango-theme legacyhuman-theme libavcodec0d libavformat0d libcairo-perl libcairomm-1.0-1 libcamel1.2-8 libchewing3 libchewing3-data libdb4.4
  libdbus-1-3 libdbus-glib-1-dev libdirectfb-0.9-24 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libegroupwise1.2-12 libgadu3 libgail18 libgcj7-0 libgii1 libgii1-target-x libgksu2-0 libgl1-mesa-glx libgnome-media0
  libgnome-window-settings1 libgnomevfs2-extra libgnutls13 libgoffice-0-common libgoffice-gtk-0-3 libgsf-1-114 libgtop2-common libgucharmap5
  libiec61883-0 libjasper-1.701-1 liblpint-bonobo0 liblzo-dev libmagick9 libmeanwhile1 libmyspell3c2 libnautilus-burn4 libnet-dbus-perl libnewt0.52
  liboobs-1-2 libparted1.7-1 libpci2 libpostproc0d libraw1394-8 libselinux1-dev libsensors-dev libsensors3 libsepol1-dev libstdc++6-4.1-dev libtasn1-3
  libtasn1-3-bin libthunar-vfs-1-2 libvisual-0.4-0 libvisual-0.4-plugins libvlc0 libvolumeid0 libvte9 libwxbase2.6-0 libx11-data libxine1 libxklavier11
  libxml-grove-perl libxml-perl libxosd2 linux-generic linux-image-2.6.17-10-generic linux-image-generic linux-libc-dev
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-generic menu-xdg metacity metacity-common mktemp music-applet nautilus
  nautilus-cd-burner nautilus-data onboard openoffice.org-style-industrial outdoors-theme portmap python-apport-utils python-beagle python-cairo
  python-central python-cups python-dbus python-exo python-gconf python-gdbm python-gmenu python-gnome2 python-gnome2-extras python-gnomecanvas
  python-gobject python-gtkhtml2 python-imaging python-numeric python-problem-report python-pyorbit python-soappy python-support python-virtkey
  python-xdg python-xml resilience-theme silicon-theme startup-tasks system-config-printer system-services sysvutils tasksel tasksel-data
  thunar-archive-plugin tshark tzdata update-notifier upstart-compat-sysv upstart-logd util-linux-locales vim-tiny vlc-nox volumeid wireshark-common
  xbitmaps xfce4-dict-plugin xfce4-notes-plugin xfce4-smartbookmark-plugin xfonts-encodings xkb-data xorg xtrans-dev xutils-dev
The following packages will be REMOVED:
  imake libgcj7 libgii0 libgii0-target-x libgl1-mesa libnewt0.51 linux-kernel-headers makedepend python2.4-apt python2.4-cairo python2.4-dbus
  python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 python2.4-imaging
  python2.4-libxml2 python2.4-numeric python2.4-pyorbit
The following packages will be upgraded:
  abiword abiword-common abiword-plugins acpi-support acpid acroread adduser alsa-base alsa-oss alsa-utils anacron anthy apmd apt apt-file apt-utils
  aptitude aspell at autoconf automake1.9 autotools-dev avahi-daemon base-files bash belocs-locales-bin bind9-host binutils binutils-static bitmap
  bomberclone bomberclone-data bsdmainutils bsdutils bsh build-essential bum busybox-initramfs bzip2 cdda2wav cdparanoia cdrdao cdrecord checkinstall
  console-common console-data console-tools coreutils cpio cpp cpp-4.0 cron cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dbus-1-utils
  debconf debconf-i18n debconf-utils debhelper debianutils defoma desktop-file-utils dhcp3-client dhcp3-common dictionaries-common discover1
  discover1-data dmidecode dmsetup dnsutils doc-base docbook-xml dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs eject epiphany-browser
  epiphany-extensions evince-gtk evms evms-ncurses example-content fastjar fdutils ffmpeg file findutils finger firefox flashplugin-nonfree fontconfig
  foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fping freeglut3 fstobdf g++
  g++-4.0 g-wrap gaim gaim-data gaim-extendedprefs gaim-guifications gcc gcc-3.3-base gcc-4.0 gcc-4.0-base gcj-4.1-base gconf2 gconf2-common gdebi gdm
  gedit-common gettext gettext-base giblib1 gij-4.1 gimp gimp-data gimp-print gksu gnome-doc-utils gnome-games gnome-games-data gnome-games-extra-data
  gnome-icon-theme gnome-keyring gnome-media gnome-mime-data gnome-sudoku gnumeric-common gnumeric-gtk gnupg gparted grep groff-base grub gs-esp
  gsfonts-other gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gtk2-engines-clearlooks
  gtk2-engines-industrial gtk2-engines-mist gtk2-engines-smooth gtk2-engines-ubuntulooks gtk2-engines-xfce guile-1.6 guile-1.6-dev guile-1.6-libs
  guile-1.6-slib guile-g-wrap gwget gzip hal hal-device-manager hdparm hostname hotkey-setup hplip hplip-data hwdata icewm icewm-common
  icewm-gnome-support ijsgutenprint imlib-base imlib11 info initramfs-tools initscripts intltool intltool-debian iproute iptables iputils-arping
  iputils-ping iputils-tracepath irssi iso-codes jackd java-common java-gcj-compat klibc-utils klogd lame language-pack-en language-pack-en-base
  language-selector language-selector-common laptop-mode-tools launchpad-integration less lftp liba52-0.7.4 libacl1 libaiksaurus-1.2-0c2a
  libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a liballegro4.2 liballegro4.2-plugin-jack libanthy0 libao2 libapm1 libapt-pkg-perl libartsc0 libasound2
  libaspell15 libatk1.0-0 libatk1.0-dev libattr1 libaudio2 libavahi-client-dev libavahi-client3 libavahi-common-data libavahi-common-dev
  libavahi-common3 libavahi-core4 libavahi-glib-dev libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbind9-0 libblkid1 libbonobo2-0
  libbonobo2-common libbonobo2-dev libbonoboui2-0 libbonoboui2-common libbonoboui2-dev libbz2-1.0 libc6 libc6-dev libc6-i686 libcairo2 libcairo2-dev
  libcdparanoia0 libcomerr2 libconsole libcupsimage2 libcupsys2 libcupsys2-dev libcurl3 libcurl3-gnutls libcurses-ui-perl libdb3 libdbus-1-dev
  libdbus-glib-1-2 libdc1394-13 libdevmapper1.02 libdiscover1 libdjvulibre15 libdmx1 libdns21 libdrm2 libdv4 libdvbpsi4 libdvdplay0 libdvdread3
  libeel2-2 libeel2-data libelfg0 libevms-2.5 libexif12 libexo-0.3-0 libexpat1 libexpat1-dev libffi4 libffi4-dev libflac7 libfltk1.1 libfontconfig1
  libfontconfig1-dev libfontenc1 libfreetype6 libfreetype6-dev libfribidi0 libfs6 libgail-common libgail-dev libgamin0 libgc1c2 libgcc1 libgcj-common
  libgcj7-jar libgconf2-4 libgconf2-dev libgcrypt11 libgcrypt11-dev libgda2-3 libgda2-common libgdbm3 libgdl-1-0 libgdl-1-common libgdome2-0
  libgdome2-cpp-smart0c2a libggi2 libgimp2.0 libgksu1.2-1 libgl1-mesa-dri libglade2-0 libglade2-dev libglib-perl libglib2.0-0 libglib2.0-data
  libglib2.0-dev libglibmm-2.4-1c2a libglu1-mesa libgnome-desktop-2 libgnome-keyring-dev libgnome-keyring0 libgnome-menu2 libgnome2-0 libgnome2-common
  libgnome2-dev libgnomecanvas2-0 libgnomecanvas2-common libgnomecanvas2-dev libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprint2.2-dev libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeprintui2.2-dev libgnomeui-0 libgnomeui-common libgnomeui-dev
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-dev libgnucrypto-java libgnutls12 libgpg-error-dev libgpg-error0 libgphoto2-2 libgphoto2-port0
  libgpmg1 libgpod-common libgpod0 libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgstreamer0.8-0 libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libgtkhtml2-0 libgtkhtml2-dev libgtkhtml3.8-15 libgtkhtml3.8-dev libgtkmathview0c2a libgtkmm-2.4-1c2a
  libgtksourceview-common libgtksourceview1.0-0 libgtop2-7 libguile-ltdl-1 libgutenprint2 libgutenprintui2-1 libgwrap-runtime0 libgwrap-runtime0-dev
  libhal-storage1 libhal1 libhsqldb-java libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libice-dev libice6 libidl-dev libidl0 libidn11
  libieee1284-3 libijs-0.35 libimlib2 libisc11 libisccc0 libisccfg1 libiw28 libjack0.100.0-0 libjaxp1.2-java libjessie-java libjline-java libjpeg-progs
  libjpeg62 libjpeg62-dev libklibc libkpathsea4 libkrb53 liblame0 liblaunchpad-integration0 liblcms1 libldap2 liblircclient0 liblockfile1
  liblog4j1.2-java libltdl3 libltdl3-dev liblwres9 libmagic1 libmailtools-perl libmdbtools libmetacity0 libmjpegtools0c2a libmms0 libmng1 libmudflap0
  libmudflap0-dev libmusicbrainz4c2a libnautilus-extension1 libncurses5 libncurses5-dev libncursesw5 libnotify1 libnspr4 libnss3 libogg0 liboggflac3
  liboil0.3 libopencdk8 libopencdk8-dev liborbit2 liborbit2-dev libosp5 libpam-modules libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpango1.0-dev libpaper1 libpcap0.8 libpcre3 libperl5.8 libpng12-0 libpng12-dev libpoppler1 libpoppler1-glib libpopt-dev libpopt0
  libqt3-mt libqthreads-12 libquicktime0 librpm4 librsvg2-2 librsvg2-common libsane libsasl2 libsasl2-modules libscim8c2a libsdl-image1.2 libsdl-net1.2
  libsdl-ttf2.0-0 libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsepol1 libservlet2.3-java libsexy2 libshout3 libslang2 libsm-dev libsm6
  libsmbclient libsmpeg0 libsndfile1 libsnmp-base libsnmp-perl libsnmp9 libsnmp9-dev libsoup2.2-8 libspeex1 libsqlite3-0 libss2 libssl-dev libssl0.9.8
  libstdc++5 libstdc++6 libstdc++6-4.0-dev libstlport4.6c2 libswfdec0.3 libsysfs2 libtag1c2a libtagc0 libtasn1-2 libtasn1-2-dev libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libtheora0 libtiff4 libtool libtotem-plparser1 libungif4g libuniconf4.2 liburi-perl
  libusb-0.1-4 libusb-dev libuuid1 libvcdinfo0 libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common libwmf0.2-7 libwnck-common libwnck18
  libwpd-stream8c2a libwpd8c2a libwrap0 libwrap0-dev libwvstreams4.2-base libwvstreams4.2-extras libwww-perl libwxgtk2.6-0 libx11-6 libx11-dev
  libxalan2-java libxau-dev libxau6 libxaw7 libxcomposite1 libxcursor-dev libxcursor1 libxdamage1 libxdmcp-dev libxdmcp6 libxerces2-java libxext-dev
  libxext6 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxfixes-dev libxfixes3 libxfont1 libxft-dev libxft2 libxi-dev libxi6
  libxine-extracodecs libxine-main1 libxinerama-dev libxinerama1 libxkbfile1 libxml1 libxml2 libxml2-dev libxml2-utils libxmlsec1 libxmlsec1-nss
  libxmlsec1-openssl libxmu6 libxmuu1 libxp6 libxpm4 libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxslt1.1 libxss1 libxt-java libxt6
  libxtrap6 libxtst6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-686 linux-image-686 linux-restricted-modules-686
  linux-restricted-modules-common linux-sound-base locales login logrotate lsb lsb-base lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-release lshw lsof
  ltrace lvm-common lvm2 maelstrom make makedev manpages mawk mcpp mdadm memtest86+ mencoder menu mesa-utils mii-diag mime-support mjpegtools mkisofs
  module-init-tools mount mousepad mozilla-acroread mozilla-firefox-locale-en-gb mozilla-mplayer mozilla-thunderbird mplayer mtr-tiny myspell-en-gb
  myspell-en-us nano ncurses-base ncurses-bin ncurses-term net-tools netbase netcat njam notification-daemon ntp ntp-server ntp-simple ntpdate numlockx
  nvidia-glx nvidia-kernel-common odbcinst1debian1 openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-us openoffice.org-l10n-en-za openoffice.org-math openoffice.org-thesaurus-en-us
  openoffice.org-writer openssh-client openssh-server openssl orage orbit2 p7zip parted passwd patch pciutils pcmciautils perl perl-base perl-modules
  pioneers-ai pioneers-client pioneers-help pioneers-meta-server pioneers-server-console pioneers-server-data pioneers-server-gtk pipenightdreams
  pipenightdreams-data planetpenguin-racer planetpenguin-racer-data planetpenguin-racer-extras plib1.8.4c2 pmount pnm2ppa po-debconf poppler-utils
  popularity-contest postfix powermgmt-base powernowd ppp pppconfig pppoeconf procps psmisc python python-apt python-glade2 python-gnome2-desktop
  python-gnupginterface python-gtk-1.2 python-gtk2 python-launchpad-integration python-libxml2 python-minimal python-pyao python-uno python-vte
  python2.4 python2.4-dev python2.4-minimal rar readahead reiserfsprogs reportbug rhythmbox rhythmbox-applet rpm rsync samba-common sane-utils scim
  scim-anthy scim-chewing scim-gtk2-immodule scim-hangul scim-modules-socket scim-pinyin scorched3d scorched3d-data scorched3d-doc sed shared-mime-info
  slib slocate smbclient ssh strace sudo sun-java5-bin sun-java5-jre sun-java5-plugin supertux supertux-data synaptic sysklogd system-tools-backends
  sysv-rc sysv-rc-conf sysvinit tango-icon-theme tango-icon-theme-common tar tcl8.4 tcpd tcpdump tethereal thunar thunar-media-tags-plugin tofrodos
  toshset totem-xine ttf-arabeyes ttf-arphic-ukai ttf-bengali-fonts ttf-bitstream-vera ttf-dejavu ttf-devanagari-fonts ttf-freefont ttf-gentium
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-larabie-deco ttf-larabie-straight
  ttf-larabie-uncommon ttf-malayalam-fonts ttf-opensymbol ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts tuxkart tuxkart-data
  ubuntu-artwork ubuntu-minimal ubuntu-sounds ubuntu-standard ucf udev unattended-upgrades unixodbc unzip update-manager usbutils usplash util-linux
  vbetool videolan-doc vim vim-common vim-runtime vlc vlc-plugin-alsa vlc-plugin-esd vorbis-tools wget whiptail wing wing-data wireless-tools
  wpasupplicant wvdial wxvlc x-ttcidfont-conf x-window-system-core x11-common x11perf x11proto-core-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xarchiver xbase-clients xcursor-themes xcursorgen
  xdriinfo xev xfburn xfce4-appfinder xfce4-battery-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager
  xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-panel xfce4-screenshooter-plugin xfce4-session xfce4-taskmanager xfce4-terminal xfce4-utils
  xfdesktop4 xfmedia xfonts-100dpi xfonts-75dpi xfonts-base xfonts-intl-european xfonts-scalable xfonts-utils xfprint4 xfsprogs xfwm4 xfwm4-themes
  xhost xinit xkbutils xkeyboard-config xml-core xmodmap xpmutils xprop xrandr xrdb xrefresh xresprobe xsane xsane-common xscorch xscreensaver
  xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-elographics xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-wacom xset xsltproc xterm xtrap
  xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-system-tools xutils yelp zenity zip zlib1g zlib1g-dev
930 packages upgraded, 196 newly installed, 23 to remove and 0 not upgraded.
Need to get 794MB/808MB of archives. After unpacking 458MB will be used.
The following packages have unmet dependencies:
  gamin: Conflicts: fam but 2.7.0-10ubuntu1 is to be installed.
  hpijs: Conflicts: hplip-ppds (< 1.6.9-0ubuntu2) but 0.9.7-4ubuntu1 is installed.
  libgnutls-dev: Depends: libtasn1-3-dev (>= 0.3.4) but it is not installable
  libvte4: Depends: libvte-common (= 1:0.12.2-0ubuntu1) but 1:0.14.1-0ubuntu1 is to be installed.
  upstart: Conflicts: sysvinit but 2.86.ds1-14.1ubuntu16 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libvte4

Install the following packages:
gnome-themes [2.16.1.1-0ubuntu1 (edgy)]
linuxprinting.org-ppds [20060918-0ubuntu2 (edgy)]
openoffice.org-style-crystal [2.0.4-0ubuntu2 (edgy)]
openoffice.org-style-default [2.0.4-0ubuntu2 (edgy)]
openoffice.org-style-hicontrast [2.0.4-0ubuntu2 (edgy)]
python-reportlab [2.0dfsg-1 (edgy)]

Keep the following packages at their current version:
capplets-data [Not Installed]
fam [Not Installed]
gnome-applets [Not Installed]
gnome-control-center [Not Installed]
gnome-panel [Not Installed]
gnome-panel-data [Not Installed]
gnome-session [Not Installed]
hpijs [2.1.7+0.9.7-4ubuntu1 (now)]
laptop-mode-tools [1.11-1ubuntu3 (now)]
libgda2-3 [1.2.2-1ubuntu2 (now)]
libgnutls-dev [1.2.9-2ubuntu1.1 (now)]
libgnutls12 [1.2.9-2ubuntu1.1 (now)]
music-applet [Not Installed]
nautilus [Not Installed]
nautilus-cd-burner [Not Installed]
nautilus-data [Not Installed]
p7zip [4.30.dfsg-1 (now)]
rhythmbox [0.9.3.1-0ubuntu9 (now)]
rhythmbox-applet [0.1.7-1ubuntu2 (now)]
startup-tasks [Not Installed]
system-services [Not Installed]
totem-xine [1.4.3-0ubuntu1 (now)]
ubuntu-minimal [0.120 (now)]
upstart [Not Installed]
upstart-compat-sysv [Not Installed]
upstart-logd [Not Installed]
xubuntu-desktop [1.32 (now)]

Score is -1136

Accept this solution? [Y/n/q/?]

```Any idea why this is happening?

---

