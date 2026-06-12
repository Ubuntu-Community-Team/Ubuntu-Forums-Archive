---
title: "Kubuntu Breezy -&gt; Dapper"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by iball on 2006-06-03
Hi,
I am trying to upgrade Kubuntu Breezy to Dapper.

From various other threads, it appears that I simply have to change breezy to dapper in /etc/apt/sources.list, uncomment any unofficial repos, and then run "sudo apt-get update && sudo apt-get dist-upgrade".  This is my sources.list:
```
 deb http://au.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu dapper-updates main restricted


 deb http://au.archive.ubuntu.com/ubuntu dapper universe multiverse
 deb-src http://au.archive.ubuntu.com/ubuntu dapper universe multiverse

 deb http://au.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
 deb-src http://au.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

```

Unfortunately, it wants to remove every KDE app.  I tried installing "kubuntu-desktop", but that has dependency problems:
```
The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: kaffeine-xine but it is not going to be installed
                   Depends: kdnssd but it is not going to be installed
                   Depends: keep but it is not going to be installed
                   Depends: kmailcvt but it is not going to be installed
                   Depends: kmplayer-konq-plugins but it is not going to be installed
                   Depends: ksplash-engine-moodin but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: libarts1-akode but it is not going to be installed
                   Depends: openoffice.org-kde but it is not going to be installed
                   Depends: skim but it is not going to be installed
                   Depends: wlassistant but it is not going to be installed
                   Depends: xserver-xorg-input-synaptics but it is not going to be installed
E: Broken packages

```

Trying to manually resolve these just makes the list longer :)

Does anyone know how to successfully upgrade from Breezy to Dapper, without losing KDE.

Thanks in advance
--Ian

---

### Post by blackjack6.21.91 on 2006-06-03
i dont think you have to modify your sources.list, just the dist-upgrade
and it may want to reinstall most everything, but i dont see why upgrading would want to remove anything..

---

### Post by iball on 2006-06-03
I don't actually have any unofficial repos, so this is the sources.list that I actually use.  This is the output from "sudo apt-get dist-upgrade":
```
ian@iball:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  adept akode akregator amarok amarok-gstreamer ark artsbuilder base-config
  busybox-cvs-initramfs cervisia cupsys-driver-gimpprint-data dbus evolution
  evolution-data-server gnat-3.4 gtk2-engines-gtk-qt gtkhtml3.8 gwenview hal
  hotplug hplip-base ifrename ivman k3b k3blibs kaddressbook kaffeine
  kaffeine-gstreamer kamera kappfinder karbon karm katapult kate kaudiocreator
  kbabel kbugbuster kcachegrind kcalc kchart kcontrol kcron kde-core kde-devel
  kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins
  kdebase kdebase-bin kdebase-dev kdebase-kio-plugins kdebluetooth
  kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs4-dev kdelibs4c2
  kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint
  kdesdk kdesdk-kfile-plugins kdesdk-kio-plugins kdesdk-misc kdesktop
  kdevelop3 kdevelop3-data kdevelop3-dev kdevelop3-plugins kdm kfind kformula
  kghostview khelpcenter kicker kio-apt kio-locate kivio klaptopdaemon klipper
  kmail kmenuedit kmilo kmix kmtrace knetworkconf knotes koffice koffice-libs
  kompare konq-plugins konqueror konqueror-nsplugins konserve konsole kontact
  konversation kooka kopete korganizer koshell kpager kpdf kpersonalizer kpf
  kppp kpresenter krdc krename krfb krita krusader kscd kscreensaver ksmserver
  ksnapshot ksplash kspread kspy ksvg ksysguard ksystemlog kthesaurus ktip
  ktorrent kubuntu-default-settings kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kugar kuickshow kuiviewer kunittest kuser kview
  kwalletmanager kwifimanager kwin kwin-baghira kword libarts1c2
  libbonoboui2-0 libcamel1.2-6 libcvsservice0 libebook1.2-5 libecal1.2-3
  libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4
  libedataserverui1.2-6 libegroupwise1.2-8 libevolution-cil libgnome2-0
  libgnome2.0-cil libgnomeui-0 libgtkhtml3.8-15 libgtksourceview2.0-cil
  libid3-3.8.3c2 libjack0.80.0-0 libkcal2b libkcddb1 libkdepim1a libkipi0
  libkleopatra1 libkmime2 libkonq4 libkonq4-dev libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 liblpint-bonobo0
  libmusicbrainz4c2 libopenexr2c2 libpanel-applet2-0 libtag1c2 libtunepimp2c2
  libwpd8c2 monodevelop monodoc-manual mysql-common-4.1 netcdfg3 nvidia-glx
  openoffice.org2 openoffice.org2-base openoffice.org2-calc
  openoffice.org2-common openoffice.org2-core openoffice.org2-draw
  openoffice.org2-help-en-us openoffice.org2-impress openoffice.org2-kde
  openoffice.org2-math openoffice.org2-writer python-kde3 python-uno
  python2.4-kde3 sanekonsole superkaramba umbrello x-common xmkmf xorg-common
  xorg-driver-synaptics xserver-common
The following NEW packages will be installed:
  app-install-data belocs-locales-bin brltty busybox-initramfs ca-certificates
  cdrdao cupsys-driver-gutenprint example-content foo2zjs
  foomatic-db-gutenprint gcj-4.0-base gcj-4.1-base gconf2-common gettext-kde
  gij-4.1 ijsgutenprint inputattach irssi kpresenter-data krita-data
  kword-data landscape-client language-selector-common laptop-mode-tools
  libarts1c2a libbeecrypt6 libbrlapi1 libcamel1.2-8 libcln4 libcupsys2
  libcurl3-gnutls libdbus-1-2 libdbus-1-dev libdbus-glib-1-2 libdevmapper1.02
  libdmx1 libdns21 libdrm2 libedataserver1.2-7 libegroupwise1.2-9 libfaac0
  libgcj7 libgcj7-jar libgfortran0 libginac1.3c2a libgnutls12 libgsf-1-113
  libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgutenprint2 libicu34 libid3-3.8.3c2a libisc11 libjack0.100.0-0
  libjline-java liblame0 liblog4net-cil liblwres9 libmagick9
  libmono-cecil0.3-cil libmp4v2-0 libmusicbrainz4c2a libmysqlclient15off
  libneon25 libnetcdf3 libnotify1 libnss-mdns libopenexr2c2a libpam-foreground
  libparted1.6-13 libpcrecpp0 libpoppler1 libpoppler1-qt libpopt-dev librsync1
  libruby1.8 libscim8c2a libsepol1 libsigc++-2.0-0c2a libsnmp9 libssl0.9.8
  libsysfs2 libtag1c2a libtunepimp2c2a libuniconf4.2 libwavpack0 libwpd8c2a
  libwvstreams4.2-base libwvstreams4.2-extras libxdmcp-dev libxfixes-dev
  libxfont1 libxine-extracodecs libxine-main1 libxmlsec1 libxmlsec1-nss
  libxmlsec1-openssl libxplc0.3.13 libxvmc1 linux-image-2.6.15-23-386
  linux-restricted-modules-2.6.15-23-386 mcpp mdetect mesa-common-dev min12xxw
  mplayer mplayer-skins mysql-common openoffice.org-help-en-us
  openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-thesaurus-en-us openssl pcmciautils
  perl-suid poppler-utils pykdeextensions python2.4-gobject python2.4-soappy
  radeontool rdiff-backup readline-common scim-qtimm smartdimmer tex-common
  thunderbird-locale-en-gb ttf-arphic-uming ttf-gentium ttf-lao ttf-thai-tlwg
  vim-gui-common vim-runtime wpasupplicant x11-common x11proto-fixes-dev
  xcursor-themes xserver-xorg-driver-all xserver-xorg-driver-sisusb
  xserver-xorg-driver-voodoo xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-synaptics
The following packages have been kept back:
  libavahi-client-dev libavahi-common-dev libavahi-qt3-dev libgnomevfs2-0
  libgnomevfs2-common
The following packages will be upgraded:
  acpi-support acpid adduser alien alsa-base alsa-utils appres apt apt-utils
  aptitude arts aspell at autoconf autotools-dev base-files base-passwd bash
  bc beforelight bicyclerepair bind9-host binfmt-support binutils
  binutils-static bison bitmap bittornado bittornado-gui bluez-cups
  bluez-pcmcia-support bluez-utils bogofilter bogofilter-bdb bogofilter-common
  bsdmainutils bsdutils bsh bzip2 cdrecord comerr-dev console-common
  console-data console-tools coreutils cpio cpp cpp-3.4 cpp-4.0 cron cupsys
  cupsys-bsd cupsys-client cupsys-driver-gimpprint cvs dash db4.2-util dc
  debconf debconf-i18n debconf-utils debhelper debianutils debtags
  dhcp3-client dhcp3-common dia dia-common dia-libs dictionaries-common diff
  discover1 discover1-data dmidecode dmsetup dnsutils doc-debian dosfstools
  dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs editres eject
  esound-common ethtool evms evms-ncurses fakeroot fastjar fdutils fetchmail
  fftw3 file findutils finger firefox flex fontconfig foomatic-db
  foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters
  foomatic-filters-ppds fortune-mod fortunes-min freeglut3 fstobdf ftp g++
  g++-4.0 gamin gcc gcc-3.3-base gcc-3.4 gcc-3.4-base gcc-4.0 gcc-4.0-base
  gconf2 gdb gettext gettext-base gij gij-4.0 gnome-icon-theme gnome-keyring
  gnupg gnuplot-doc gnuplot-nox gnuplot-x11 grep grepmap groff-base grub
  gs-common gs-esp gstreamer0.8-alsa gstreamer0.8-audiofile
  gstreamer0.8-cdparanoia gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-flac
  gstreamer0.8-gsm gstreamer0.8-hermes gstreamer0.8-jpeg gstreamer0.8-mad
  gstreamer0.8-misc gstreamer0.8-musepack gstreamer0.8-oss
  gstreamer0.8-plugin-apps gstreamer0.8-sdl gstreamer0.8-speex
  gstreamer0.8-theora gstreamer0.8-tools gstreamer0.8-vorbis gstreamer0.8-x
  gzip hdparm hermes1 hicolor-icon-theme hostname hotkey-setup hpijs
  hplip-data hplip-ppds hspell html2text hwdata iceauth ico ifupdown
  ijsgimpprint imagemagick imake imlib-base info initramfs-tools initscripts
  installation-report intltool-debian iproute iptables iputils-arping
  iputils-ping iputils-tracepath irssi-text jackd java-common java-gcj-compat
  java-package kapptemplate kdebase-data kdelibs-data kdesdk-scripts
  kdevelop3-doc kivio-data klibc-utils klogd kmatplot koffice-data
  koffice-doc-html ksysguardd kubuntu-artwork-usplash language-pack-en
  language-pack-en-base language-pack-kde-en language-pack-kde-en-base
  language-support-en laptop-detect launchpad-integration less lftp libaa1
  libacl1 libacl1-dev libadns1 libao2 libapr0 libarts1-dev libartsc0
  libartsc0-dev libasound2 libasound2-dev libaspell-dev libaspell15
  libatk1.0-0 libattr1 libattr1-dev libaudio-dev libaudio2 libaudiofile-dev
  libaudiofile0 libavc1394-0 libbind9-0 libblkid1 libbluetooth1 libbonobo2-0
  libbonobo2-common libbonoboui2-common libbz2-1.0 libbz2-dev libc6 libc6-dev
  libc6-i686 libcomerr2 libconsole libcroco3 libcupsimage2 libcupsys2-dev
  libcupsys2-gnutls10 libcurl3 libdb1-compat libdb3 libdb4.2 libdb4.3
  libdbus-qt-1-1c2 libdirectfb-0.9-22 libdiscover1 libdv4 libdvdread3 libedit2
  libelfg0 libesd0 libesd0-dev libevms-2.5 libfaad2-0 libflac++5c2 libflac7
  libflash-mozplugin libflash0c2 libfontconfig1 libfontconfig1-dev libfontenc1
  libfribidi0 libfs6 libg2c0 libgadu3 libgail-common libgail17 libgamin-dev
  libgamin0 libgc1c2 libgcc1 libgcj-common libgcj6 libgconf2-4 libgconf2.0-cil
  libgcrypt11 libgcrypt11-dev libgd2-noxpm libgecko2.0-cil libgeoip1 libggi2
  libgii0 libgii0-target-x libgl1-mesa libgl1-mesa-dev libgl1-mesa-dri
  libglade2-0 libglade2.0-cil libglib1.2 libglib2.0-0 libglib2.0-cil
  libglib2.0-dev libglu1-mesa libglu1-mesa-dev libgmime2.1 libgmime2.1-cil
  libgmp3c2 libgmpxx3 libgnokii2 libgnome-keyring0 libgnome-pilot2
  libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-common libgnucrypto-java
  libgnujaxp-java libgnujaxp-jni libgnutls11 libgnutls11-dev libgpg-error-dev
  libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1 libgsl0
  libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgstreamer0.8-0
  libgtk1.2 libgtk1.2-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil
  libgtk2.0-common libgtksourceview-common libgtksourceview1.0-0
  libhal-storage1 libhal1 libhdf5-serial-1.6.4-0c2 libhsqldb-java libice-dev
  libice6 libice6-dbg libidl0 libidn11 libidn11-dev libijs-0.35 libisccc0
  libisccfg1 libiw28 libjessie-java libjpeg-progs libjpeg62 libjpeg62-dev
  libkadm55 libklibc libkrb5-dev libkrb53 liblaunchpad-integration0 libldap2
  liblircclient0 liblockdev1 libltdl3 liblua50 liblua50-dev liblualib50
  liblualib50-dev liblzo1 libmagic1 libmdbtools libmhash2 libmimelib1c2a
  libmodplug0c2 libmono-dev libmono0 libmpcdec3 libmyspell3c2 libmysqlclient14
  libncurses5 libncurses5-dev libncursesw5 libneon24 libnetpbm10 libnspr4
  libnss3 libogg-dev libogg0 liboggflac3 liboil0.3 libopencdk8 libopencdk8-dev
  libopenexr-dev liborbit2 libpam-modules libpam-runtime libpam0g
  libpango1.0-0 libpango1.0-common libpcap0.8 libpcre3 libpcre3-dev libperl5.8
  libpisock8 libpisync0 libpng12-0 libpng12-dev libportaudio0 libpq3 libpq4
  libpythonize0 libqcad0 libqt3-headers libqt3-mt libqt3-mt-dev libraptor1
  librasqal0 libraw1394-5 librdf0 libreadline4 libreadline5 libreadline5-dev
  librecode0 libreiserfs0.3-0 librpm4 librsvg2-2 librsvg2-common
  libsamplerate0 libsane libsasl2 libsasl2-dev libsasl2-modules
  libscrollkeeper0 libsdl1.2debian libsdl1.2debian-oss libselinux1 libsensors3
  libservlet2.3-java libshout3 libslang2 libslp1 libsm-dev libsm6 libsm6-dbg
  libsmbclient libsndfile1 libsnmp-base libsoup2.2-8 libspeex1 libsqlite0
  libsqlite3-0 libss2 libssl-dev libssl0.9.7 libstartup-notification0
  libstdc++5 libstdc++6 libstdc++6-4.0-dev libsvn0 libtasn1-2 libtasn1-2-dev
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libtheora0
  libtiff4 libtiff4-dev libtiffxx0c2 libungif4g libunicode-string-perl
  libusb-0.1-4 libuuid1 libvorbis-dev libvorbis0a libvorbisenc2 libvorbisfile3
  libwrap0 libwv2-1c2 libwxgtk2.6-0 libx11-6 libx11-6-dbg libx11-dev
  libxalan2-java libxau-dev libxau6 libxaw-headers libxaw7 libxaw7-dbg
  libxaw7-dev libxcomposite1 libxcursor-dev libxcursor1 libxdamage1 libxdmcp6
  libxerces2-java libxext-dev libxext6 libxext6-dbg libxfixes3 libxft-dev
  libxft2 libxi-dev libxi6 libxi6-dbg libxine1c2 libxinerama-dev libxinerama1
  libxkbfile1 libxml2 libxml2-dev libxml2-utils libxmu-dev libxmu-headers
  libxmu6 libxmu6-dbg libxmuu-dev libxmuu1 libxmuu1-dbg libxosd2 libxp6
  libxpm-dev libxpm4 libxpm4-dbg libxrandr-dev libxrandr2 libxrandr2-dbg
  libxrender-dev libxrender1 libxslt1-dev libxslt1.1 libxss1 libxt-dev
  libxt-java libxt6 libxt6-dbg libxtrap-dev libxtrap6 libxtrap6-dbg
  libxtst-dev libxtst6 libxtst6-dbg libxv-dev libxv1 libxv1-dbg libxvidcore4
  libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-386 linux-image-386
  linux-kernel-headers linux-restricted-modules-386
  linux-restricted-modules-common linux-sound-base listres lm-sensors locales
  login logrotate lsb-base lsb-release lshw lshw-common lsof lua50 lvm-common
  lvm2 m4 make makedepend makedev manpages manpages-dev mawk mdadm memtest86+
  menu-xdg mime-support mkisofs module-init-tools mono mono-classlib-1.0
  mono-common mono-devel mono-gac mono-jay mono-jit mono-mcs mono-utils
  monodoc-base mount mozilla-firefox mozilla-firefox-locale-en-gb mplayer-386
  mplayer-doc msttcorefonts myspell-en-gb myspell-en-us mzscheme nano
  ncurses-base ncurses-bin net-tools netbase netcat netpbm nfs-common
  nfs-kernel-server ntpdate nvidia-kernel-common nvidia-settings oclock
  octave-forge octave2.1 octave2.1-doc odbcinst1debian1 openssh-client
  openssh-server parted passwd pciutils pcmcia-cs perl perl-base perl-modules
  pkg-config pmount po-debconf popularity-contest portmap poster
  powermanagement-interface powermgmt-base powernowd poxml ppp pppconfig
  procps psmisc psutils python python-adns python-apt python-cddb
  python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-epydoc python-eunuchs python-examples python-gadfly python-gd
  python-gdbm python-geoip python-gtk2 python-htmlgen python-htmltmpl
  python-id3lib python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-ldap python-minimal python-mysqldb python-netcdf
  python-numeric python-opengl python-osd python-pam python-parted
  python-pexpect python-pgsql python-pisock python-pylibacl python-pyopenssl
  python-pyorbit python-pyxattr python-reportlab python-simpletal
  python-soappy python-sqlite python-syck python-tk python-unit
  python-wxgtk2.6 python-wxversion python-xdg python-xml python2.4
  python2.4-adns python2.4-apt python2.4-cairo python2.4-clientcookie
  python2.4-crypto python2.4-dbus python2.4-dev python2.4-egenix-mxdatetime
  python2.4-egenix-mxproxy python2.4-egenix-mxstack
  python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc
  python2.4-eunuchs python2.4-examples python2.4-gadfly python2.4-gd
  python2.4-gdbm python2.4-geoip python2.4-gtk2 python2.4-htmlgen
  python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane
  python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf
  python2.4-libxml2 python2.4-libxslt1 python2.4-minimal python2.4-mysqldb
  python2.4-numeric python2.4-opengl python2.4-osd python2.4-pam
  python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl
  python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-qt3
  python2.4-reportlab python2.4-simpletal python2.4-sip4-qt3 python2.4-sqlite
  python2.4-syck python2.4-tk python2.4-unit python2.4-xml pythoncad qca-tls
  qcad qobex qt3-designer qt3-dev-tools readahead reiser4progs reportbug rpm
  rsync samba-common sane-utils screen scrollkeeper sed sessreg
  shared-mime-info slocate smbclient smproxy speedcrunch ssh subversion sudo
  sysklogd sysv-rc sysvinit tar tcl8.4 tcpd tcpdump telnet texinfo tk8.4
  toshset ttf-arabeyes ttf-arphic-bkai00mp ttf-bengali-fonts ttf-dejavu
  ttf-devanagari-fonts ttf-freefont ttf-gujarati-fonts ttf-indic-fonts
  ttf-kannada-fonts ttf-malayalam-fonts ttf-mgopen ttf-opensymbol
  ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts
  ubuntu-minimal ubuntu-standard ucf udev unzip usbutils usplash util-linux
  vbetool viewres vim vim-common vim-gtk vorbis-tools w3m wamerican wbritish
  wget whois wireless-tools wvdial x-dev x-ttcidfont-conf x-window-system-core
  x11perf x11proto-core-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-trap-dev
  x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev xauth
  xbase-clients xbiff xcalc xclipboard xclock xconsole xcursorgen xditview
  xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-scalable xfonts-utils xfontsel xfsprogs xgamma xgc xhost
  xinit xkbutils xkeyboard-config xkill xload xlogo xlsatoms xlsclients
  xlsfonts xmag xman xmessage xmms xmodmap xmore xpmutils xprop xrandr xrdb
  xrefresh xresprobe xrgb xserver-xorg xserver-xorg-core
  xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati
  xserver-xorg-driver-chips xserver-xorg-driver-cirrus
  xserver-xorg-driver-cyrix xserver-xorg-driver-dummy
  xserver-xorg-driver-fbdev xserver-xorg-driver-glint xserver-xorg-driver-i128
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt
  xserver-xorg-driver-mga xserver-xorg-driver-neomagic
  xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident
  xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa
  xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-input-acecad xserver-xorg-input-aiptek
  xserver-xorg-input-calcomp xserver-xorg-input-citron
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc
  xserver-xorg-input-dynapro xserver-xorg-input-elographics
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-kbd
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mouse xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void xserver-xorg-input-wacom
  xset xsetmode xsetpointer xsetroot xsm xstdcmap xterm xtrap xutils xvidtune
  xvinfo xwd xwininfo xwud zlib1g zlib1g-dev
965 upgraded, 144 newly installed, 214 to remove and 5 not upgraded.
```

It wants to remove every KDE package installed on my system...

Anyone got any ideas?

TIA
--Ian

---

### Post by sisooktom on 2006-06-03
Same thing happened to me, except I actually did the upgrade and now X wont start :(

---

### Post by iball on 2006-06-03
[QUOTE=sisooktom]Same thing happened to me, except I actually did the upgrade and now X wont start :([/QUOTE]

I "bit the bullet", and did the upgrade and installed kubuntu-desktop afterwards.  Then X wouldn't start.  I then got fed up, downloaded the Dapper CD and did a fresh install.

Did you have the Proprietry Nvidia or ATI drivers installed?  I tried to install the Nvidia drivers on my fresh Dapper install, following the instructions that worked for Breezy, and it stopped X from starting.  I had to go back to the Open Source Drivers.  Try ```
sudo dpkg-reconfigure xserver-xorg
``` and restart X.  

--Ian

---

