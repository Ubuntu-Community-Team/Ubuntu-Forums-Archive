---
title: "Upgrading breezy-&gt;dapper wants to remove half the desktop"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by supermihi on 2006-06-02
Hi,
I'm administrating a few ubuntu (actually kubuntu) boxes and now wanted to test dapper on some of them.

So I followed the recommendation and changed all appereances of "breezy" to "dapper" in sources.list, also commenting out all non-official repositories.

Now if I update & dist-upgrade, I get the following:

```

root@remus:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  adept akode akregator amarok amarok-arts amarok-gstreamer ark artsbuilder base-config busybox-cvs-initramfs cupsys-driver-gimpprint-data dbus
  dbus-1-utils dcoprss dia-gnome evolution evolution-data-server evolution-plugins gnome-pilot gnome-pilot-conduits gstreamer0.8-jack gstreamer0.8-plugins
  gtk2-engines-gtk-qt gtkhtml3.8 gwenview hal hal-device-manager hotplug hplip-base ifrename ivman k3b k3blibs kaddressbook kaffeine kaffeine-gstreamer
  kalarm kamera kandy kappfinder karm katapult kate kaudiocreator kcharselect kcontrol kcron kde-guidance kde-i18n-de kde-style-lipstik kde-systemsettings
  kdeadmin-kfile-plugins kdeartwork kdeartwork-style kdeartwork-theme-window kdebase-bin kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins
  kdelibs-bin kdelibs4c2 kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim kdepim-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdessh kdevelop3
  kdevelop3-data kdevelop3-plugins kdict kdissert kdm kdnssd kdvi kfind kget kghostview kgpg khelpcenter kicker kile kile-i18n kio-apt kio-locate
  kitchensync klaptopdaemon kleopatra klipper kmail kmailcvt kmenuedit kmilo kmix knetworkconf knewsticker knode knotes koffice-libs konq-plugins
  konqueror konqueror-nsplugins konserve konsole konsolekalendar kontact konversation kooka kopete korganizer korn kpdf kpersonalizer kpf kpilot kppp krdc
  kregexpeditor krfb krita kscd kscreensaver kscreensaver-xsavers ksirc ksmserver ksnapshot ksplash ksvg ksync ksysguard ksystemlog ktalkd kteatime ktnef
  kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kviewshell kwalletmanager kweather kwifimanager kwin
  libaiksaurus0 libarts1c2 libavahi-client1 libbonoboui2-0 libcamel1.2-6 libcvsservice0 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-4 libedataserverui1.2-6 libegroupwise1.2-8 libexchange-storage1.2-0 libgcj6-common libgnome2-0 libgnomeui-0 libgtkhtml3.8-15
  libid3-3.8.3c2 libjack0.80.0-0 libkcal2b libkcddb1 libkdepim1a libkgantt0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1
  libkscan1 libksieve0 libktnef1 liblpint-bonobo0 libmusicbrainz4c2 libnautilus-burn2 libopenexr2c2 libpanel-applet2-0 librss1 libtag1c2 libtunepimp2c2
  libwine-cil lisa lyx lyx-common lyx-qt mozilla-browser mozilla-psm mozilla-thunderbird-offline mysql-common-4.1 netcdfg3 networkstatus
  openoffice.org-bin openoffice.org-debian-files openoffice.org-kde openoffice.org-l10n-en openoffice.org-mimelnk openoffice.org1-debian-files
  openoffice.org2-common openoffice.org2-core openoffice.org2-java-common openoffice.org2-kde openoffice.org2-l10n-en-us python-kde3 python2.4-gnome2
  python2.4-gnome2-extras python2.4-kde3 sanekonsole vim-gnome vimpart x-common xmkmf xorg-common xorg-driver-synaptics xserver-common ytalk
The following NEW packages will be installed:
  app-install-data belocs-locales-bin brltty busybox-initramfs cupsys-driver-gutenprint example-content foomatic-db-gutenprint gcj-4.0-base gcj-4.1-base
  gconf2-common gfortran gfortran-4.0 gij-4.1 ijsgutenprint inputattach irssi krita-data landscape-client language-selector-common laptop-mode-tools
  libarts1c2a libbeecrypt6 libbrlapi1 libcamel1.2-8 libcdio6 libcln4 libcupsys2 libcurl3-gnutls libdbus-1-2 libdbus-glib-1-2 libdevmapper1.02 libdmx1
  libdns21 libdrm2 libedataserver1.2-7 libegroupwise1.2-9 libgcj6-jar libgcj7 libgcj7-jar libgfortran0 libgfortran0-dev libginac1.3c2a libgnutls12
  libgsf-1-113 libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgutenprint2 libhsqldb-java libicu34 libid3-3.8.3c2a libisc11
  libiso9660-4 libjack0.100.0-0 libjline-java libkpathsea4 liblwres9 libmagick9 libmail-spf-query-perl libmdbtools libmpfr1 libmusicbrainz4c2a
  libmysqlclient15off libneon25 libnet-cidr-lite-perl libnet-ip-perl libnetcdf3 libnotify1 libnss-mdns libopenexr2c2a libosp5 libpam-foreground
  libparted1.6-13 libpoppler1 libpoppler1-qt librsync1 libscim8c2a libsepol1 libservlet2.3-java libsigc++-2.0-0c2a libsnmp9 libsocket6-perl libssl0.9.8
  libsysfs2 libtag1c2a libtunepimp2c2a libuniconf4.2 liburi-perl libwavpack0 libwpd8c2a libwvstreams4.2-base libwvstreams4.2-extras libxfont1
  libxine-extracodecs libxine-main1 libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxplc0.3.13 libxvmc1 linux-image-2.6.15-23-k7
  linux-restricted-modules-2.6.15-23-k7 lsb-desktop mcpp mdetect min12xxw mysql-common nagios-plugins-basic nagios-plugins-standard openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-common openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer pcmciautils pykdeextensions python-uno python2.4-gobject
  python2.4-soappy rdiff-backup readline-common scim-qtimm tex-common thunderbird-locale-de ttf-arphic-uming ttf-gentium ttf-lao ttf-thai-tlwg
  vim-gui-common vim-runtime wpasupplicant x11-common xcursor-themes xserver-xorg-driver-all xserver-xorg-driver-sisusb xserver-xorg-driver-voodoo
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-synaptics
The following packages have been kept back:
  gstreamer0.8-gnomevfs k3b-i18n libgnomevfs2-0 libgnomevfs2-common
The following packages will be upgraded:
  acpi-support acpid adduser alien alsa-base alsa-utils appres apt apt-listchanges apt-utils apticron aptitude arj arts aspell aspell-de at auctex
  autoconf autotools-dev base-files base-passwd bash bc beforelight bicyclerepair bind9-host binutils binutils-static bitmap bluez-cups
  bluez-pcmcia-support bluez-utils bogofilter bogofilter-bdb bogofilter-common bsdmainutils bsdutils bsh bzip2 ca-certificates cdrdao cdrecord
  console-common console-data console-tools coreutils cpio cpp cpp-3.3 cpp-3.4 cpp-4.0 cron cupsys cupsys-bsd cupsys-client cupsys-driver-gimpprint cvs
  dash dc debconf debconf-i18n debconf-utils debhelper debianutils debtags devscripts dhcp3-client dhcp3-common dia dia-common dia-libs
  dictionaries-common diff dirmngr discover1 discover1-data dmidecode dmsetup dnsutils doc-debian dosfstools dpatch dpkg dpkg-dev dselect dvd+rw-tools
  dvipng e2fslibs e2fsprogs editres eject emacs21 emacs21-bin-common emacs21-common emacsen-common esound-clients esound-common ethtool evms evms-cli
  evms-gui evms-ncurses fakeroot fastjar fdutils fetchmail fftw3 fftw3-dev fglrx-control file findutils finger firefox firefox-dom-inspector flac
  fontconfig foo2zjs foomatic-db foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod
  fortunes-min fping freeglut3 fstobdf ftp g++ g++-3.3 g++-3.4 g++-4.0 g77 g77-3.4 gamin gcc gcc-3.3 gcc-3.3-base gcc-3.4 gcc-3.4-base gcc-4.0
  gcc-4.0-base gcj-4.0 gconf2 gdb gettext gettext-base gij gij-4.0 gimp gimp-data gimp-gap gimp-help-common gimp-help-de gimp-help-en gimp-helpbrowser
  gimp-svg gimp-texturize gimp-ufraw gnome-desktop-data gnome-icon-theme gnome-keyring gnuhtml2latex gnupg gnupg-agent gnupg2 gpgsm grep grepmap groff
  groff-base grub grub-splashimages gs gs-common gs-esp gs-gpl gsfonts-x11 gsl-bin gsl-ref-html gsl-ref-psdoc gstreamer0.8-a52dec gstreamer0.8-aa
  gstreamer0.8-alsa gstreamer0.8-artsd gstreamer0.8-audiofile gstreamer0.8-caca gstreamer0.8-cdio gstreamer0.8-cdparanoia gstreamer0.8-dv gstreamer0.8-dvd
  gstreamer0.8-esd gstreamer0.8-festival gstreamer0.8-flac gstreamer0.8-gsm gstreamer0.8-gtk gstreamer0.8-hermes gstreamer0.8-jpeg gstreamer0.8-mad
  gstreamer0.8-mikmod gstreamer0.8-misc gstreamer0.8-mms gstreamer0.8-mpeg2dec gstreamer0.8-musepack gstreamer0.8-oss gstreamer0.8-plugin-apps
  gstreamer0.8-sdl gstreamer0.8-sid gstreamer0.8-speex gstreamer0.8-swfdec gstreamer0.8-theora gstreamer0.8-tools gstreamer0.8-vorbis gstreamer0.8-x gzip
  hdparm hermes1 hfsplus hfsutils hicolor-icon-theme hostname hotkey-setup hpijs hplip-data hplip-ppds html2text hwdata iceauth ico ifupdown ijsgimpprint
  imagemagick imake info ingerman initramfs-tools initscripts intltool-debian iogerman iproute iptables iputils-arping iputils-ping iputils-tracepath
  irssi-text jackd java-common java-gcj-compat kdeartwork-emoticons kdeartwork-misc kdeartwork-theme-icon kdebase-data kdelibs-data kdevelop3-doc
  kdewallpapers kernel-package kernel-source-2.4.27 klibc-utils klogd koffice-data ksysguardd kubuntu-artwork-usplash language-pack-de
  language-pack-de-base language-pack-kde-de language-pack-kde-de-base laptop-detect latex-beamer launchpad-integration less lftp libaa1 libacl1 libadns1
  libadns1-bin libao2 libartsc0 libasound2 libaspell15 libatk1.0-0 libatk1.0-data libattr1 libaudio2 libaudiofile0 libavc1394-0 libbind9-0 libblkid1
  libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-common libbz2-1.0 libc6 libc6-dev libc6-i686 libcairo2 libccid libcomerr2
  libcompress-zlib-perl libconsole libcroco3 libcsiro0 libcupsimage2 libcupsys2-gnutls10 libcurl3 libdb1-compat libdb3 libdb4.2 libdb4.3 libdbus-qt-1-1c2
  libdiscover1 libdv-bin libdv4 libdvdread3 libedit2 libelfg0 libesd0 libevms-2.5 libflac++5c2 libflac7 libfontconfig1 libfontenc1 libfreetype6
  libfribidi0 libfs6 libg2c0 libg2c0-dev libgadu3 libgail-common libgail17 libgamin0 libgc1c2 libgcc1 libgcj-common libgcj6 libgcj6-awt libgcj6-dev
  libgcj6-src libgconf2-4 libgcrypt11 libgd2-noxpm libgda2-3 libgda2-common libgeoip1 libgimp2.0 libgl1-mesa libgl1-mesa-dri libglade2-0 libglib1.2
  libglib2.0-0 libglib2.0-data libglu1-mesa libgmp3c2 libgmpxx3 libgnokii2 libgnome-keyring0 libgnome-pilot2 libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-common
  libgnucrypto-java libgnujaxp-java libgnujaxp-jni libgnutls11 libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1 libgsl0 libgsl0-dev
  libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgstreamer0.8-0 libgtk1.2 libgtk1.2-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0
  libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libhal-storage1 libhal1 libhdf5-serial-1.6.4-0c2 libhdf5-serial-dev libhfsp0
  libhtml-parser-perl libhtml-tagset-perl libice6 libid3tag0 libidl0 libidn11 libijs-0.35 libindex0 libio-socket-ssl-perl libisccc0 libisccfg1 libiw28
  libjessie-java libjpeg-progs libjpeg62 libjpeg62-dev libklibc libkpathsea3 libkrb53 libksba8 liblaunchpad-integration0 libldap2 liblockdev1 liblockfile1
  libltdl3 liblzo1 libmagic1 libmail-sendmail-perl libmimelib1c2a libmms0 libmodplug0c2 libmpcdec3 libmpeg2-4 libmudflap0 libmudflap0-dev libmyspell3c2
  libmysqlclient14 libmysqlclient14-dev libncurses5 libncurses5-dev libncursesw5 libneon24 libnet-dns-perl libnet-ssleay-perl libnetpbm10 libnspr4 libnss3
  libogg0 liboggflac3 liboil0.3 libopencdk8 libopenct1 liborbit2 libostyle1c2 libpam-modules libpam-runtime libpam0g libpango1.0-0 libpango1.0-common
  libpcap0.8 libpcre3 libpcsclite1 libperl5.8 libpisock8 libpisync0 libplplot9 libpng12-0 libpng3 libportaudio0 libpq4 libpth2 libpvm3 libpythonize0
  libqca1c2 libqt-perl libqt3-mt libraptor1 librasqal0 libraw1394-5 librdf0 libreadline4 libreadline5 libreadline5-dev librecode0 libreiserfs0.3-0 librpm4
  librrd2 librsvg2-2 librsvg2-bin librsvg2-common libruby1.8 libsamplerate0 libsane libsasl2 libsasl2-modules libscrollkeeper0 libsdl1.2debian
  libsdl1.2debian-oss libselinux1 libsensors3 libshout3 libsidplay1 libslang2 libslp1 libsm6 libsmbclient libsmokeqt1 libsndfile1 libsnmp-base
  libsoup2.2-8 libsp1c2 libspeex1 libsqlite0 libsqlite3-0 libss2 libssl0.9.7 libstartup-notification0 libstdc++2.10-glibc2.2 libstdc++5 libstdc++5-3.3-dev
  libstdc++6 libstdc++6-4.0-dev libstdc++6-dev libswfdec0.3 libt1-5 libtasn1-2 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libtheora0
  libtiff-tools libtiff4 libttf2 libungif4g libunicode-string-perl libusb-0.1-4 libuuid1 libvcdinfo0 libvorbis0a libvorbisenc2 libvorbisfile3 libwine
  libwmf0.2-7 libwnck-common libwnck18 libwrap0 libwww-ssl0 libx11-6 libxalan2-java libxau6 libxaw7 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxerces2-java libxext6 libxfixes3 libxft2 libxi6 libxine1c2 libxinerama1 libxkbfile1 libxml2 libxmu6 libxmuu1 libxosd2 libxp6 libxpm4 libxrandr2
  libxrender1 libxres1 libxslt1.1 libxss1 libxt-java libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-image-k7 linux-k7
  linux-kernel-headers linux-restricted-modules-common linux-restricted-modules-k7 linux-sound-base linuxdoc-tools listres lm-sensors locales logcheck
  logcheck-database login logrotate logtail lsb lsb-base lsb-core lsb-cxx lsb-graphics lsb-release lshw lshw-common lsof lvm-common lvm2 m4 mailx make
  makedepend makedev manpages mawk mdadm memtest86+ menu menu-xdg mime-support miscfiles mkisofs module-init-tools mount mozilla-firefox-locale-de-de
  mozilla-firefox-locale-en-gb mozilla-thunderbird mozilla-thunderbird-enigmail mozilla-thunderbird-locale-de mozilla-thunderbird-typeaheadfind
  msttcorefonts myspell-de-at myspell-de-ch myspell-de-de myspell-en-us nagios-nrpe-server nagios-plugins nano ncurses-base ncurses-bin ncurses-term
  net-tools netbase netcat netpbm nfs-common nis ntp ntp-server ntp-simple ntpdate nvidia-kernel-common oclock ocrad octave octave-forge octave-gpc
  octave-plplot octave-sp octave-statdataml octave2.1 octave2.1-headers octave2.1-htmldoc octave2.1-info openclipart-openoffice.org openclipart-png
  openclipart-svg openjade openoffice.org openoffice.org-evolution openoffice.org-help-de openoffice.org-l10n-de openoffice.org2 openssh-client
  openssh-server openssl parted passwd pciutils pcmcia-cs pcscd perl perl-base perl-doc perl-modules perl-suid perl-tk pgf pinentry-curses pinentry-qt
  pkg-config pmount po-debconf popularity-contest portmap poster powermanagement-interface powermgmt-base powernowd ppp pppconfig prelink preview-latex
  preview-latex-style procps psi psmisc psutils pvm python python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxdatetime
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly
  python-gd python-gdbm python-geoip python-glade2 python-gtk2 python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane
  python-jabber python-kjbuckets python-launchpad-integration python-ldap python-minimal python-mysqldb python-netcdf python-numeric python-opengl
  python-osd python-pam python-parted python-pexpect python-pgsql python-pisock python-pylibacl python-pyopenssl python-pyorbit python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-syck python-tk python-unit python-xdg python-xml python2.4 python2.4-adns
  python2.4-apt python2.4-cairo python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-dev python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs python2.4-examples python2.4-gadfly
  python2.4-gd python2.4-gdbm python2.4-geoip python2.4-glade2 python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib python2.4-imaging
  python2.4-imaging-sane python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-minimal
  python2.4-mysqldb python2.4-numeric python2.4-opengl python2.4-osd python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl
  python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-qt3 python2.4-reportlab python2.4-reportlab-accel python2.4-simpletal
  python2.4-sip4-qt3 python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml qca-tls qobex qt3-qtconfig raptor-utils rdesktop readahead
  redland-utils reiser4progs reportbug rpm rsync ruby1.8 samba-common sane-utils screen scribus scrollkeeper sed sensord sessreg shared-mime-info slocate
  smartdimmer smartmontools smbclient smbfs smproxy snmp sox sp spamassassin spamc speedcrunch ssh ssmtp sudo sysklogd sysv-rc sysvinit tar tcl8.4 tcpd
  tcpdump telnet tetex-base tetex-bin tetex-doc tetex-extra tex4ht texi2html texinfo tk8.4 toshset ttf-arabeyes ttf-arphic-bkai00mp ttf-bengali-fonts
  ttf-dejavu ttf-devanagari-fonts ttf-freefont ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-malayalam-fonts ttf-mgopen ttf-opensymbol
  ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ubuntu-base ubuntu-minimal ubuntu-standard ucf udev unzip usbutils usplash util-linux
  vbetool vcdimager viewres vim vim-common vorbis-tools w3m wamerican wget wine wireless-tools wngerman wogerman wswiss wvdial x-ttcidfont-conf
  x-window-system-core x11perf xauth xaw3dg xbase-clients xbiff xcalc xclipboard xclock xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga
  xfd xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils xfontsel xfsprogs xgamma xgc xhost xinit xkbutils xkeyboard-config xkill xli
  xload xlogo xlsatoms xlsclients xlsfonts xmag xman xmessage xmodmap xmore xorg-driver-fglrx xpdf-common xpdf-utils xpmutils xprop xrandr xrdb xrefresh
  xresprobe xrgb xscreensaver xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-driver-apm xserver-xorg-driver-ark
  xserver-xorg-driver-ati xserver-xorg-driver-chips xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix xserver-xorg-driver-dummy
  xserver-xorg-driver-fbdev xserver-xorg-driver-glint xserver-xorg-driver-i128 xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt
  xserver-xorg-driver-mga xserver-xorg-driver-neomagic xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3 xserver-xorg-driver-s3virge xserver-xorg-driver-savage xserver-xorg-driver-siliconmotion
  xserver-xorg-driver-sis xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident xserver-xorg-driver-tseng xserver-xorg-driver-v4l
  xserver-xorg-driver-vesa xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware xserver-xorg-input-acecad xserver-xorg-input-aiptek
  xserver-xorg-input-calcomp xserver-xorg-input-citron xserver-xorg-input-digitaledge xserver-xorg-input-dmc xserver-xorg-input-dynapro
  xserver-xorg-input-elographics xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-kbd xserver-xorg-input-magellan
  xserver-xorg-input-microtouch xserver-xorg-input-mouse xserver-xorg-input-mutouch xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa xserver-xorg-input-tek4957 xserver-xorg-input-void xserver-xorg-input-wacom xset xsetmode
  xsetpointer xsetroot xsm xstdcmap xterm xtrap xutils xvidtune xvinfo xwd xwininfo xwud zlib1g zlib1g-dev zoo
1038 upgraded, 145 newly installed, 229 to remove and 4 not upgraded.
Need to get 0B/992MB of archives.
After unpacking 129MB disk space will be freed.
Do you want to continue [Y/n]?  

```

As you can see lots of KDE programs would be removed, also kubuntu-desktop. I would try just to do an upgrade and then manually reinstall those apps, but the affected computer is used all the time so I can't risk a timeout of a few hours.

---

### Post by ubuntu_demon on 2006-06-02
If you can't risk it wait until you have more time.

It happens quite often that a dist-upgrade want to remove kubuntu-desktop or ubuntu-desktop. Just reinstall it after dist-upgrading.

take a look here : [http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

### Post by supermihi on 2006-06-02
Thanks.
What I did now is to upgrade kubuntu-desktop with aptitude. This way there are only few packages removed that I need, the whole KDE stuff updated correctly.
dpkg is still working with this but it seems to work.
Probably my problem was caused by an unofficial KDE 3.5 repository in my sources.list.

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=supermihi]Thanks.
What I did now is to upgrade kubuntu-desktop with aptitude. This way there are only few packages removed that I need, the whole KDE stuff updated correctly.
dpkg is still working with this but it seems to work.
Probably my problem was caused by an unofficial KDE 3.5 repository in my sources.list.[/QUOTE]
Yeah you should always uncomment unofficial repositories  prior to dist-upgrading :)

---

### Post by supermihi on 2006-06-02
Damn, now the system doesn't even start up. If I select the new kernel, it says something like "loading kernel, initialising linux" and then does nothing.

But, I just received an Email from this computer from a few hours ago with a S.M.A.R.T. error, so I assume the hard disc is corrupt, so dapper would be innocent. ;)
I'll try a complete new install with the Dapper CD, but I assume I'll have to change the disc.

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=supermihi]Damn, now the system doesn't even start up. If I select the new kernel, it says something like "loading kernel, initialising linux" and then does nothing.

But, I just received an Email from this computer from a few hours ago with a S.M.A.R.T. error, so I assume the hard disc is corrupt, so dapper would be innocent. ;)
I'll try a complete new install with the Dapper CD, but I assume I'll have to change the disc.[/QUOTE]
try booting into recovery mode.

If that doesn't work boot from a live cd. Mount your Ubuntu Dapper partition, chroot and work from there.

$sudo mkdir /mnt/dapper
use the correct device here .. for example /dev/hda6 :
$sudo mount */dev/hda6* /mnt/dapper
$sudo chroot /mnt/dapper

Now you can work again from dapper.

If you can't solve it and you don't want to try anymore you could always reinstall ofcourse .. but that's not very exciting is it ? :)

---

### Post by supermihi on 2006-06-02
Well, I did now indeed reinstall, because the hard disc was definitely defective - I saw that somebody already wrote the word "corrupt" onto it with a pen. ;)

The new Installation went without major problems, although I ran into various problems with the graphical installer (it really sucks and has lots of bugs). Do I get the old debian-like installer if I download the alternative-CD? Is there any way to install ubuntu with a root account from the beginning? I have about 30 computers that are NIS'ed so I'm afraid sudo isn't the right option here.

What I also didn't like was the automatically generated xorg.conf, but that's another story, too. For this thread's subject, I suppose I'm done. There are about 10 breezy computers left with that custom KDE packages, so I assume an upgrade would run into problems there as it did on the first one, but it seems to me that rsync-ing the OS over SSH is faster than the dist-upgrade anyway.

Regards
Michael

---

### Post by ubuntu_demon on 2006-06-02
> **supermihi]Well, I did now indeed reinstall, because the hard disc was definitely defective - I saw that somebody already wrote the word "corrupt" onto it with a pen.  said:**
> 

You should make sure your hardrive isn't broken.

[QUOTE=supermihi]
The new Installation went without major problems, although I ran into various problems with the graphical installer (it really sucks and has lots of bugs). Do I get the old debian-like installer if I download the alternative-CD? 


Yeah just as with breezy.

[QUOTE=supermihi]
Is there any way to install ubuntu with a root account from the beginning? I have about 30 computers that are NIS'ed so I'm afraid sudo isn't the right option here.
[/QUOTE]

IMHO sudo rules.
AFAIK booting the alternate install cd with "expert" will automatically give you a root account.

[QUOTE=supermihi]
What I also didn't like was the automatically generated xorg.conf, but that's another story, too. For this thread's subject, I suppose I'm done. There are about 10 breezy computers left with that custom KDE packages, so I assume an upgrade would run into problems there as it did on the first one, but it seems to me that rsync-ing the OS over SSH is faster than the dist-upgrade anyway.

Regards
Michael[/QUOTE]

good luck! :)

---

### Post by supermihi on 2006-06-03
[QUOTE=ubuntu_demon]
IMHO sudo rules.
AFAIK booting the alternate install cd with "expert" will automatically give you a root account.
[/QUOTE]

So do you think it also rules in a mixed windows/linux[ubuntu,debian,gentoo] environment? Well, maybe you're right, I read the wiki entry about sudo. ATM I don't have time to change all the systems, but I'll think about that again when I have more.
The option to give someone root access without giving him the root password seems very interesting to me, e.g. if I am in vacation.

---

### Post by ubuntu_demon on 2006-06-03
The first time you sudo you have to enter the passwords. If the following command is entered within a preset time(which can be changed) then you won't have to type your password again. In this way you have never open root terminals running which you have forgotten abou and it also forces you to think "do I have to be superuser to do this?".

---

### Post by supermihi on 2006-06-03
Yeah, I understand this is a great thing especially for home users with little experience. But as a network administrator, I see less advantage, because normally I know which things have to be done as root. On the other hand it's attractive to have a locked root account which cannot be cracked. But since in my case all usernames are authenticated via NIS, with sudo I have a problem if there are networking problems. 

I'll give it a try, anyway.

---

