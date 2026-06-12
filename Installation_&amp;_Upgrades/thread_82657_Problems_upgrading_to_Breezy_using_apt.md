---
title: "Problems upgrading to Breezy using apt"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by infinito on 2005-10-26
Hello everyone!

I'm trying to upgrade from Hoary to Breezy using apt, but i've got some strange depencies problems. For example, apt wants to remove totem, ubuntu-desktop and doesn't want to upgrade rhythmbox.

I don'tknow if this is normal in this process, but i don't think so...
I will really appreciate any kind of help with this issue.

This is the output from sudo apt-get dist-upgrade:
```
infinito@munster:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  acroread-debian-files aspell-bin capplets dbus-1 dbus-glib-1 kdelibs4 libarts1 libbtctl1 libcamel1.2-3 libebook1.2-3 libedataserverui1.2-4 libesd0 libgc1 libhal-storage0 libhal0
  libid3-3.8.3 libmusicbrainz2 libmusicbrainz4 libmyspell3 libnautilus-burn1 libopenexr2 libopenh323-1.15.2 libostyle1 libpt-1.8.3 libqt3c102-mt libsigc++-1.2-5c102 libsmpeg0
  libstlport4.6 libxine1 mozilla-firefox-gnome-support openoffice.org-thesaurus-en-us postfix-tls redhat-artwork totem totem-xine ubuntu-desktop ubuntu-quickguide xlibmesa-dri
  xlibmesa-gl xlibmesa-glu
The following NEW packages will be installed:
  appres beforelight bitmap bluez-cups bluez-pcmcia-support bogofilter-bdb bogofilter-common bsh busybox-cvs-initramfs cpp-4.0 dbus editres evince evolution-plugins fastjar firefox
  firefox-gnome-support fstobdf g++-4.0 gcc-3.4-base gcc-4.0 gcc-4.0-base gij-4.0 gnome-terminal-data gstreamer0.8-musepack gtk2-engines-crux gtk2-engines-lighthouseblue gtkhtml3.8
  hotkey-setup hplip-base hplip-data hplip-ppds hwdata iceauth ico imake initramfs-tools java-gcj-compat kdelibs4c2 klibc-utils language-pack-kde-es language-pack-kde-es-base
  language-selector lapack3 launchpad-integration lesstif1 libaa1 libarts1c2 libatm1 libbind9-0 libbtctl2 libcairo2 libcamel1.2-6 libcdio3 libcompfaceg1 libdbus-1-1
  libdbus-glib-1-1 libdbus-qt-1-1c2 libdevmapper1.01 libdjvulibre15 libdns20 libdrm1 libebook1.2-5 libecal1.2-3 libedataserverui1.2-6 libedit2 libegroupwise1.2-8 libesd-alsa0
  libexchange-storage1.2-0 libexif12 libflac++5c2 libflac7 libfontenc1 libg2c0 libgamin-dev libgc1c2 libgcj-common libgcj6 libgcj6-common libgda2-3 libgda2-common libgl1-mesa
  libgl1-mesa-dri libglib2.0-dev libglide2 libglu1-mesa libgnome-menu2 libgnucrypto-java libgnujaxp-java libgnujaxp-jni libgtkhtml3.8-15 libhal-storage1 libhal1 libhsqldb-java
  libid3-3.8.3c2 libisc9 libisccc0 libisccfg1 libiso9660-3 libiw28 libjaxp1.2-java libjessie-java libklibc libkpathsea3 liblaunchpad-integration0 liblpint-bonobo0 libltdl3
  libmdbtools libmpcdec3 libmusicbrainz2c2 libmusicbrainz4c2 libmyspell3c2 libmysqlclient14 libnautilus-burn2 libneon24 libnotify0 liboggflac3 liboil0.3 libopenexr2c2
  libopenh323-1.15.3c2 libostyle1c2 libpoppler0c2 libpoppler0c2-glib libportaudio0 libpq4 libpt-1.8.3c2 libqt3-mt libservlet2.3-java libsigc++-1.2-5c2 libslang2 libsmpeg0c2
  libsndfile1 libsnmp-base libsnmp5 libsoup2.2-8 libsqlite3-0 libstdc++6 libstdc++6-4.0-dev libstlport4.6c2 libtag1c2 libtotem-plparser0 libwnck18 libwpd8c2 libwvstreams4.0c2-base
  libwvstreams4.0c2-extras libwxgtk2.6-0 libxalan2-java libxerces2-java libxplc0.3.11c2 libxres1 libxt-java linux-headers-2.6.12-9 linux-headers-2.6.12-9-386
  linux-headers-2.6.12-9-686 linux-image-2.6.12-9-386 linux-image-2.6.12-9-686 linux-sound-base listres lsb-core lsb-cxx lsb-graphics lshw-common makedepend mesa-utils
  notification-daemon oclock odbcinst1debian1 openoffice.org1-debian-files openoffice.org2 openoffice.org2-base openoffice.org2-calc openoffice.org2-common openoffice.org2-core
  openoffice.org2-draw openoffice.org2-evolution openoffice.org2-gnome openoffice.org2-help-en-us openoffice.org2-help-es openoffice.org2-impress openoffice.org2-java-common
  openoffice.org2-l10n-en-us openoffice.org2-l10n-es openoffice.org2-math openoffice.org2-writer python-gmenu python-launchpad-integration python-uno python-zopeinterface
  python2.4-apt python2.4-cairo python2.4-epydoc python2.4-zopeinterface refblas3 serpentine sessreg smeg smproxy toshset ttf-bengali-fonts ttf-devanagari-fonts ttf-gujarati-fonts
  ttf-kannada-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ubuntu-minimal ubuntu-standard usplash viewres wamerican wbritish wspanish
  x-common x11perf xauth xbiff xcalc xclipboard xclock xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-utils xfontsel xgamma xgc xhost xinit xkbutils
  xkeyboard-config xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman xmessage xmkmf xmodmap xmore xpmutils xprop xrandr xrdb xrefresh xrgb xscreensaver-data
  xserver-xorg-core xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati xserver-xorg-driver-chips xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix
  xserver-xorg-driver-dummy xserver-xorg-driver-fbdev xserver-xorg-driver-glide xserver-xorg-driver-glint xserver-xorg-driver-i128 xserver-xorg-driver-i740 xserver-xorg-driver-i810
  xserver-xorg-driver-imstt xserver-xorg-driver-mga xserver-xorg-driver-neomagic xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3 xserver-xorg-driver-s3virge xserver-xorg-driver-savage xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga
  xserver-xorg-driver-via xserver-xorg-driver-vmware xserver-xorg-input-acecad xserver-xorg-input-aiptek xserver-xorg-input-calcomp xserver-xorg-input-citron
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc xserver-xorg-input-dynapro xserver-xorg-input-elographics xserver-xorg-input-fpit xserver-xorg-input-hyperpen
  xserver-xorg-input-kbd xserver-xorg-input-magellan xserver-xorg-input-microtouch xserver-xorg-input-mouse xserver-xorg-input-mutouch xserver-xorg-input-palmax
  xserver-xorg-input-penmount xserver-xorg-input-spaceorb xserver-xorg-input-summa xserver-xorg-input-tek4957 xserver-xorg-input-void xserver-xorg-input-wacom xset xsetmode
  xsetpointer xsetroot xsm xstdcmap xtrap xvidtune xvinfo xwd xwininfo xwud
The following packages have been kept back:
  rhythmbox
The following packages will be upgraded:
  aalib1 acpi acpi-support acpid acroread adduser alien alsa-base alsa-utils amule anacron apmd apt apt-utils aptitude aspell aspell-en aspell-es at base-config base-files
  base-passwd bash bc bind9-host binutils bittorrent bluez-pin bluez-utils bogofilter bsdmainutils bsdutils bug-buddy build-essential bzip2 capplets-data cdrdao cdrecord
  console-common console-data console-tools contact-lookup-applet coreutils cpio cpp cpp-3.3 cron cupsys cupsys-bsd cupsys-client cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data cvs dash dbus-1-utils dc debconf debconf-i18n debconf-utils debhelper debianutils desktop-file-utils dhcp3-client dhcp3-common dictionaries-common
  diff discover1 discover1-data diveintopython dmidecode dmsetup dnsutils doc-base doc-debian docbook docbook-dsssl docbook-xml dosfstools dpkg dpkg-dev dselect dvd+rw-tools
  e2fslibs e2fsprogs easytag eject eog esound esound-common evms evms-ncurses evolution evolution-data-server evolution-exchange evolution-webcal fakeroot fdutils fetchmail
  fglrx-control file file-roller findutils finger fontconfig foomatic-db foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters foomatic-filters-ppds
  fortune-mod fortunes-min fping freeglut3 ftp g++ g++-3.3 gaim gaim-data gamin gcalctool gcc gcc-3.3 gcc-3.3-base gconf-editor gconf2 gdb gdm gedit gedit-common gettext
  gettext-base gftp-common gftp-gtk gimp gimp-data gimp-python gksu gnome-about gnome-app-install gnome-applets gnome-applets-data gnome-bluetooth gnome-btdownload
  gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-gv gnome-icon-theme gnome-keyring gnome-media gnome-menus
  gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnomemeeting gnupg grep grepmap groff-base grub gs-common gs-esp gsfonts gstreamer0.8-alsa
  gstreamer0.8-audiofile gstreamer0.8-cdparanoia gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-esd gstreamer0.8-flac gstreamer0.8-gnomevfs gstreamer0.8-gsm gstreamer0.8-hermes
  gstreamer0.8-jpeg gstreamer0.8-mad gstreamer0.8-misc gstreamer0.8-oss gstreamer0.8-plugin-apps gstreamer0.8-sdl gstreamer0.8-speex gstreamer0.8-theora gstreamer0.8-tools
  gstreamer0.8-vorbis gstreamer0.8-x gthumb gtk2-engines-clearlooks gtk2-engines-industrial gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth
  gtk2-engines-thinice gtkhtml3.6 gtkpod gucharmap guile-1.6-libs gzip hal hal-device-manager hdparm hermes1 hicolor-icon-theme hotplug hpijs html2text hwdb-client i810switch
  ifrename ifupdown ijsgimpprint imagemagick imlib-base imlib1 info initrd-tools initscripts iproute iptables iputils-arping iputils-ping iputils-tracepath irda-utils irssi-text
  iso-codes jfsutils k3b k3b-i18n k3blibs kcontrol kde-i18n-es kdebase-bin kdebase-data kdelibs-bin kdelibs-data klogd language-pack-de language-pack-de-base language-pack-en
  language-pack-en-base language-pack-es language-pack-es-base language-support-en language-support-es laptop-detect lesstif2 lftp libacl1 libadns1 libao2 libapm1
  libarchive-tar-perl libartsc0 libasound2 libaspell15 libatk1.0-0 libattr1 libaudio2 libaudiofile0 libavc1394-0 libblkid1 libbluetooth1 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libbz2-1.0 libc6 libc6-dev libc6-i686 libcomerr2 libcompress-zlib-perl libconsole libcupsimage2 libcupsys2-gnutls10 libcurl3 libdb3 libdb4.2
  libdb4.3 libdiscover1 libdmx1 libdv4 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4 libeel2-2 libeel2-data libevms-2.5 libexpat1 libfontconfig1 libfreetype6 libfribidi0
  libfs6 libgail-common libgail17 libgal2.4-0 libgal2.4-common libgamin0 libgcc1 libgconf2-4 libgcrypt11 libgd1-noxpm libgdchart-gd1-noxpm libgdk-pixbuf2 libgeoip1 libgimp2.0
  libgimpprint1 libgksu1.2-0 libgksuui1.0-0 libglade2-0 libgle3 libglib-perl libglib1.2 libglib2.0-0 libglib2.0-data libgmime2.1 libgnome-desktop-2 libgnome-keyring0
  libgnome-menu-dev libgnome-pilot2 libgnome2-0 libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1
  libgnomecupsui1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnutls11 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1 libgsf-1 libgsl0 libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgstreamer0.8-0 libgtk1.2 libgtk1.2-common
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml3.6-18 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-5 libgucharmap4 libguile-ltdl-1
  libhtml-parser-perl libice6 libid3tag0 libidl0 libidn11 libieee1284-3 libjpeg62 libkrb53 libldap2 liblircclient0 liblocale-gettext-perl liblwres1 libmad0 libmagic1 libmagick6
  libmetacity0 libmysqlclient10 libmysqlclient12 libnautilus-extension1 libncurses5 libncurses5-dev libncursesw5 libneon23 libnetpbm10 libnewt0.51 libnspr4 libnss3 libogg0
  libopenal0 liborbit2 libosp4 libpam-modules libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpaper1 libparted1.6-12 libpcap0.8 libpcre3 libperl5.8
  libpisock8 libpisync0 libpng10-0 libpng12-0 libpq3 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 libraptor1 librasqal0 librdf0 libreadline5 librpm4
  librsvg2-2 librsvg2-common libruby libruby1.8 libsane libsasl2 libsasl2-modules libscrollkeeper0 libsdl1.2debian libsdl1.2debian-oss libselinux1 libshout3 libslp1 libsm6
  libsmbclient libspeex1 libsqlite0 libss2 libssl0.9.7 libstartup-notification0 libstdc++5 libstdc++5-3.3-dev libsysfs1 libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libtheora0 libtiff4 libungif4g libunicode-string-perl liburi-perl libusb-0.1-4 libuuid1 libvcdinfo0 libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common
  libvte4 libwmf0.2-7 libwnck-common libwrap0 libwww-perl libx11-6 libxau6 libxaw7 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxkbfile1
  libxkbui1 libxklavier10 libxml-namespacesupport-perl libxml-simple-perl libxml2 libxml2-utils libxmu6 libxmuu1 libxosd2 libxp6 libxpm4 libxrandr2 libxrender1 libxslt1.1 libxss1
  libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-headers-386 linux-headers-686 linux-image-386 linux-image-686 linux-kernel-headers locales login
  logrotate lsb lsb-base lsb-release lshw lsof lvm2 m4 mailx makedev man-db manpages mdadm memtest86+ menu metacity mii-diag mime-support mkisofs module-init-tools mount
  mozilla-firefox mozilla-firefox-locale-en-gb mozilla-firefox-locale-es-ar mozilla-firefox-locale-es-es mtr-tiny mutt myspell-en-gb myspell-en-us myspell-es mysql-common nano
  nautilus nautilus-cd-burner nautilus-data nautilus-sendto ncurses-base ncurses-bin ncurses-term net-tools netapplet netbase netkit-inetd netpbm nmap normalize-audio ntp ntpdate
  nvidia-kernel-common openjade openoffice.org openoffice.org-bin openoffice.org-debian-files openoffice.org-gtk-gnome openoffice.org-help-en openoffice.org-help-es
  openoffice.org-l10n-en openoffice.org-l10n-es openssh-client parted passwd pcmcia-cs perl perl-base perl-modules pkg-config pmount pnm2ppa po-debconf popularity-contest postfix
  powermanagement-interface powermgmt-base powernowd ppp pppconfig pppoeconf procmail procps psmisc pwgen python python-apt python-egenix-mxproxy python-egenix-mxstack
  python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gdbm python-gdchart python-geoip python-glade2 python-gnome2
  python-gnome2-extras python-gnupginterface python-gst python-gtk2 python-id3lib python-imaging python-imaging-sane python-minimal python-musicbrainz python-mysqldb python-netcdf
  python-newt python-numarray python-numeric python-opengl python-parted python-pexpect python-pgsql python-pisock python-pyopenssl python-pyorbit python-reportlab python-simpletal
  python-sqlite python-syck python-tk python-twisted python-xdg python-xml python-xmpp python2.4 python2.4-dbus python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-eunuchs python2.4-examples python2.4-gdbm python2.4-geoip python2.4-glade2
  python2.4-gnome2 python2.4-gnome2-extras python2.4-gtk2 python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-libbtctl python2.4-librdf python2.4-libxml2
  python2.4-libxslt1 python2.4-minimal python2.4-musicbrainz python2.4-mysqldb python2.4-numarray python2.4-numeric python2.4-opengl python2.4-pexpect python2.4-pgsql
  python2.4-pycurl python2.4-pyopenssl python2.4-pyorbit python2.4-reportlab python2.4-samba python2.4-simpletal python2.4-sqlite python2.4-syck python2.4-tk python2.4-twisted
  python2.4-twisted-bin python2.4-xml python2.4-xmpp rdesktop readahead reiser4progs reportbug rpm rss-glx rsync ruby ruby1.8 samba-common sane-utils scrollkeeper seahorse sed
  setserial sgml-data shared-mime-info smbclient sound-juicer sox ssh-askpass-gnome strace sudo synaptic sysklogd system-tools-backends sysv-rc sysvinit tar tcl8.4 tcpd tcpdump
  telnet time tk8.4 tree tsclient ttf-indic-fonts ttf-malayalam-fonts ttf-opensymbol ubuntu-artwork ubuntu-base ubuntu-docs ucf udev unrar-nonfree unzip update-manager
  update-notifier usbutils util-linux vbetool vcdimager vim vim-common vino vnc-common vorbis-tools w3m wget whiptail whois wireless-tools wvdial x-ttcidfont-conf
  x-window-system-core xbase-clients xchat xchat-common xchat-systray xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfsprogs xlibs xlibs-data xmms xorg-common
  xorg-driver-fglrx xorg-driver-synaptics xpdf xpdf-common xpdf-reader xpdf-utils xresprobe xsane xsane-common xscreensaver xscreensaver-gl xserver-common xserver-xorg xsltproc
  xterm xutils xvncviewer yelp zenity zip zlib1g
783 upgraded, 326 newly installed, 40 to remove and 1 not upgraded.
Need to get 261MB/695MB of archives.
After unpacking 663MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Thank you all!

---

### Post by John.Michael.Kane on 2005-10-27
You may have to let it upgrade like it's doing. then upon reboot re-run apt-get update then apt-get dist-upgrade. i think the issue stems from the reconfig of the sources.list and some other files. i have had to run the codes i posted twice when i went form 5.04 to 5.10. this how ever is just a guess.

---

