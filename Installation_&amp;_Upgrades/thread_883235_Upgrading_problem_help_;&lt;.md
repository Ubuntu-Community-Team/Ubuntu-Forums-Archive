---
title: "Upgrading problem help ;&lt;"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Vamp381 on 2008-08-07
I have many problems...
1.I run the upgrade in update manager and update process just stopped and exited and now there 800+ Updates in Update manager,where they come from ? My system is still 7.10.

2. Now there is something when i enter update manager "Partial Upgrade and Close" whats that ?

3.I tried via Alternate cd same problem the upgrade process just exit ?

What is the problem and what do to with 800+ updates that appeared from nowhere....

---

### Post by iaculallad on 2008-08-07
Does it display an error when you issue the command below on your terminal: If so, post whatever error message it displays:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Vamp381 on 2008-08-07
I get

```
W: Duplicate sources.list entry http://archive.ubuntu.com hardy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  abiword abiword-plugins acpi-support amarok amarok-xine amule amule-common
  amule-daemon anjuta anjuta-common apt apt-utils aptitude at-spi audacity
  avidemux bind9-host bluefish bluez-gnome bluez-utils bogofilter-bdb brasero
  brltty brltty-x11 bug-buddy capplets-data clive compiz compiz-core
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome
  compiz-plugins consolekit cpp cupsys cupsys-bsd cupsys-client
  cupsys-driver-gutenprint d4x d4x-common dbus dbus-x11 debhelper
  deskbar-applet devhelp-common dnsutils dpkg dpkg-dev dvdauthor ekiga enblend
  eog evince evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins
  evolution-webcal f-spot faac faad fast-user-switch-applet file-roller
  firefox firefox-3.0 firefox-gnome-support g++ gcalctool gcc gconf-editor
  gconf2 gconf2-common gdesklets gdhcpd gdm gedit gedit-common gettext
  gftp-common gftp-gtk gimp gimp-data gimp-python gksu gnome-app-install
  gnome-applets gnome-applets-data gnome-cards-data gnome-control-center
  gnome-games gnome-games-data gnome-keyring gnome-mag gnome-media
  gnome-media-common gnome-mount gnome-nettool gnome-orca gnome-panel
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager
  gnome-screensaver gnome-session gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-utils gnome-volume-manager
  gnomebaker gnumeric-common gnumeric-gtk gnupg gnutls-bin gqview grub
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-x gthumb
  gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gtk2-engines-ubuntulooks gtk2-engines-xfce gtkhtml3.14 gucharmap hal
  hal-cups-utils hal-info hardinfo hpijs hplip hplip-data hugin hugin-bin
  hugin-data hugin-tools icedax imagemagick initramfs-tools inkscape iproute
  k3b k9copy kaffeine kdebase-bin kdebase-data kdebase-kio-plugins
  kdebluetooth kdelibs-data kdelibs4c2a kdesktop kdevelop kget kicker kmid
  konversation kwifimanager language-support-en language-support-sr lftp
  libaiksaurusgtk-1.2-0c2a libapache2-mod-php5 libaprutil1 libatk1-ruby1.8
  libatspi1.0-0 libbind9-30 libbonoboui2-0 libbonoboui2-common
  libbonoboui2-dev libcairo-ruby1.8 libcairo2 libcairo2-dev
  libcommons-cli-java libcupsimage2 libcupsys2 libcupsys2-dev libcurl3
  libcurl3-gnutls libcvsservice0 libdevhelp-1-0 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libeel2-2 libegroupwise1.2-13 libexchange-storage1.2-3
  libexo-0.3-0 libfaad2-0 libgail-common libgail-dev libgail-gnome-module
  libgail18 libgbf-1-1 libgbf-1-common libgconf2-4 libgconf2-dev libgdiplus
  libgdk-pixbuf2-ruby1.8 libgdl-1-0 libgdl-1-common libgdl-gnome-1-0
  libgimp2.0 libgksu2-0 libglade2.0-cil libglademm-2.4-1c2a libglib2-ruby1.8
  libgnome-desktop-2 libgnome-desktop-dev libgnome-media0 libgnome-speech7
  libgnome-window-settings1 libgnome2-canvas-perl libgnome2.0-cil
  libgnomecanvas2-0 libgnomecanvas2-dev libgnomecups1.0-1 libgnomekbd-common
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomeui-dev
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-dev libgnomevfs2-extra
  libgnutls-dev libgnutls13 libgnutlsxx13 libgs8 libgtk1.2 libgtk2-ruby1.8
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtk2.0-dev
  libgtkhtml2-0 libgtkhtml3.14-19 libgtkhtml3.8-15 libgtkmathview0c2a
  libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common
  libgtkspell0 libgucharmap6 libgutenprintui2-1 libhsqldb-java libimlib2
  libimlib2-dev libisccfg30 libk3b2 libkbluetooth0 libkonq4 liblpint-bonobo0
  libmetacity0 libmp4v2-0 libmp4v2-dev libnss3-0d libofa0 libopal-2.2
  libpam-modules libpanel-applet2-0 libpango1-ruby1.8 libpango1.0-0
  libpango1.0-dev libperl5.8 libpoppler-glib2 libpurple0 libqt4-core
  libqt4-gui libqt4-qt3support libqt4-sql libquicktime1 librarian0 librsvg2-2
  librsvg2-common libsasl2-2 libsasl2-modules libsdl1.2-dev libsdl1.2debian
  libsdl1.2debian-alsa libsmbclient libsoup2.2-8 libsvn1 libswt3.2-gtk-java
  libswt3.2-gtk-jni libthunar-vfs-1-2 libtracker-gtk0 libtunepimp5
  libungif4-dev libungif4g libvcdinfo0 libvte-common libvte9 libwnck-common
  libwnck-dev libwnck22 libwxgtk2.6-0 libwxgtk2.8-0 libx11-6 libx11-6-dbg
  libx11-dev libx264-dev libxfcegui4-4 libxine1 libxine1-bin libxine1-console
  libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x
  linux-headers-generic linux-image-generic listen lm-sensors mencoder
  metacity metacity-common mousepad mozilla-plugin-vlc mplayer nautilus
  nautilus-actions nautilus-cd-burner nautilus-data nautilus-sendto netcat
  network-manager network-manager-gnome network-manager-kde networkstatus
  notification-daemon ntfs-3g openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-human openoffice.org-writer orage perl perl-base
  perl-modules php5-common pidgin pidgin-data python python-apt python-cairo
  python-cups python-exo python-glade2 python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnomecanvas python-gobject python-gtk2
  python-gtkhtml2 python-launchpad-integration python-minimal python-notify
  python-qt4 python-qt4-dbus python-soya python-uno python-vte python2.4
  python2.4-minimal python2.5 python2.5-minimal qjackctl rhythmbox rpm rss-glx
  samba samba-common scim scim-gtk2-immodule scim-modules-socket
  scim-modules-table scim-tables-additional serpentine smbclient sound-juicer
  sox splix ssh-askpass-gnome subversion synaptic system-tools-backends thunar
  thunar-data thunar-volman thunderbird timidity timidity-interfaces-extra
  tomboy totem totem-mozilla totem-xine tracker tracker-search-tool
  ttf-gentium ttf-opensymbol tuxguitar-alsa ubuntu-artwork ubuntu-desktop
  ubuntu-standard ubuntustudio-look udev update-manager update-manager-core
  update-notifier vino vlc vlc-nox warzone2100 warzone2100-data wine wpagui
  wvdial xbase-clients xchat xchat-common xchat-gnome xchat-gnome-common xchm
  xfce4 xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin
  xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer
  xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin
  xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-session
  xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal
  xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin
  xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xorg xsane
  xsane-common xserver-xorg xserver-xorg-core xserver-xorg-dev
  xserver-xorg-input-all xserver-xorg-input-elographics
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-amd xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-cyrix xserver-xorg-video-dummy xserver-xorg-video-fbdev
  xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-imstt xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-newport
  xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xubuntu-desktop
  xulrunner-1.9 xutils xvidcap yelp zenity
The following packages will be upgraded:
  abiword-common acpid adduser alacarte alien alien-arena alien-arena-data
  alien-arena-server alsa-base alsa-oss alsa-utils anacron apache2
  apache2-mpm-prefork apache2-utils apache2.2-common app-install-data
  app-install-data-commercial apparmor apparmor-utils apport apport-gtk apturl
  arj aspell autopano-sift autotools-dev avahi-autoipd avahi-daemon balazar
  base-files base-passwd bash bc belocs-locales-bin binutils binutils-static
  bittorrent blt bluez-cups bogofilter bogofilter-common bsdmainutils bsdutils
  bsh busybox-initramfs bzip2 ca-certificates cdparanoia cdrdao checkinstall
  cli-common comerr-dev command-not-found command-not-found-data console-setup
  console-terminus console-tools coreutils cpio cpp-3.4 cpp-4.1 cron cups-pdf
  cupsys-common cvs dash dc dcraw debconf debconf-i18n debianutils defoma
  desktop-file-utils dh-make dhcdbd dhcp3-client dhcp3-common dhcp3-server
  dictionaries-common diffstat discover1 discover1-data displayconfig-gtk
  dmsetup doc-base docbook-xml dosbox dosfstools dpatch dselect dvd+rw-tools
  e2fslibs e2fsprogs ed eject esound esound-common espeak espeak-data ethtool
  example-content fakeroot feisty-gdm-themes ffmpeg file findutils fontconfig
  fontconfig-config foo2zjs foomatic-db foomatic-db-hpijs foomatic-filters
  freeglut3 fuse-utils g++-4.1 gaim gajim gamin gawk gcc-3.3-base gcc-3.4
  gcc-3.4-base gcc-4.1 gcc-4.1-base gcc-4.2-base gcj-4.1-base gcj-4.2-base gdb
  gdebi gdebi-core gdesklets-data genisoimage gettext-base ghostscript
  ghostscript-x gij gij-4.1 gij-4.2 glest-data gnome-about
  gnome-accessibility-themes gnome-btdownload gnome-common gnome-desktop-data
  gnome-doc-utils gnome-icon-theme gnome-menus gnome-themes gnome-user-guide
  gpgv grep groff-base gs-common gs-esp gs-esp-x gsfonts gsfonts-x11
  gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-ugly-multiverse
  gstreamer0.10-sdl gstreamer0.10-tools gtk-recordmydesktop guidance-backends
  gutsy-wallpapers gzip hdparm hostname hotkey-setup html2text
  human-icon-theme human-theme hwdb-client-common hwdb-client-gnome info
  initscripts intltool iptables iputils-arping iputils-ping iputils-tracepath
  iso-codes jack jackd java-common kdevelop-data klibc-utils klogd
  knetworkmanager language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-pack-gnome-sr
  language-pack-gnome-sr-base language-pack-kde-sr language-pack-kde-sr-base
  language-pack-sr language-pack-sr-base language-selector
  language-selector-common laptop-mode-tools launchpad-integration less lha
  liba52-0.7.4 liba52-0.7.4-dev libaa1 libacl1 libaiksaurus-1.2-0c2a
  libaiksaurus-1.2-data libao2 libapr1 libarchive-tar-perl libarchive1
  libart-2.0-2 libart-2.0-dev libart2.0-cil libarts1c2a libartsc0 libasound2
  libaspell15 libatk1.0-0 libatk1.0-dev libattr1 libaudio-dev libaudio2
  libaudiofile-dev libaudiofile0 libavahi-client-dev libavahi-client3
  libavahi-common-data libavahi-common-dev libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib-dev libavahi-glib1
  libavahi-qt3-1 libavcodec1d libavformat1d libavutil1d libblkid1
  libbluetooth2 libbonobo2-0 libbonobo2-common libbonobo2-dev
  libboost-iostreams1.34.1 libboost-thread1.34.1 libbz2-1.0 libc6 libc6-dev
  libc6-i686 libcaca0 libcairo-perl libcairomm-1.0-1 libcal3d12 libcdparanoia0
  libchm1 libcomerr2 libcompizconfig0 libcompress-raw-zlib-perl
  libcompress-zlib-perl libconsole libcucul0 libdatrie0 libdb4.2 libdb4.3
  libdb4.4 libdb4.5 libdbus-1-3 libdbus-1-dev libdbus-glib-1-2
  libdbus-glib-1-dev libdc1394-13 libdc1394-13-dev libdecoration0
  libdeskbar-tracker libdevmapper1.02.1 libdiscover1 libdjvulibre15 libdns32
  libdvdread3 libebml0 libedit2 libeel2-data libenchant1c2a libesd-alsa0
  libesd0-dev libespeak1 libevent1 libexif12 libexpat1 libexpat1-dev
  libfaac-dev libfaac0 libflac++6 libflac8 libfontconfig1 libfontconfig1-dev
  libfreebob0 libfribidi0 libfuse2 libgamin0 libgc1c2 libgcc1 libgcj-bc
  libgcj-common libgcj7-1 libgcj8-1 libgconf2.0-cil libgcrypt11
  libgcrypt11-dev libgda2-3 libgda2-common libgda3-3 libgda3-common
  libgdome2-cpp-smart0c2a libgksu1.2-1 libgl1-mesa-dev libgl1-mesa-dri
  libgl1-mesa-glx libglib-perl libglib2.0-0 libglib2.0-cil libglib2.0-data
  libglib2.0-dev libglibmm-2.4-1c2a libglu1-mesa libglu1-mesa-dev
  libglu1-xorg-dev libgmime-2.0-2 libgmime2.2-cil libgnome-keyring-dev
  libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2
  libgnome-vfs2.0-cil libgnome2-0 libgnome2-common libgnome2-dev
  libgnome2-vfs-perl libgnomecanvas2-common libgnomevfs2-bin
  libgoffice-0-common libgpg-error-dev libgpg-error0 libgphoto2-2
  libgphoto2-port0 libgpmg1 libgsf-1-114 libgsf-1-common libgsm1 libgsm1-dev
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk1.2-common
  libgtk2-perl libgtk2-ruby libgtop2-7 libgtop2-common libgutenprint2
  libhal-dev libhal-storage-dev libhal-storage1 libhal1 libhunspell-1.1-0
  libice-dev libice6 libid3-3.8.3c2a libidl-dev libidl0 libidn11 libieee1284-3
  libio-compress-base-perl libio-compress-zlib-perl libisc32 libisccc30
  libitext-java libiw29 libjack0 libjack0.100.0-0 libjaxp1.3-java
  libjline-java libkadm55 libkeyutils1 libklibc libkpathsea4 libkrb5-dev
  libkrb53 liblcms1 liblcms1-dev liblink-grammar4 liblircclient0
  liblocale-gettext-perl liblog4j1.2-java libltdl3 libltdl3-dev liblua5.1-0
  liblua50 liblualib50 liblwres30 libmagic1 libmms0 libmodplug0c2
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono0 libmono2.0-cil libmozjs0d libmysqlclient15off libnautilus-burn4
  libnautilus-extension1 libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libndesk-dbus1.0-cil libneon26 libnet-dbus-perl libnewt0.52 libnm-glib0
  libnm-util0 libnspr4-0d libnss-mdns libode0debian1 libogg-dev libogg0
  liboil0.3 libopenal0a liborbit2 liborbit2-dev libots0 libpam-gnome-keyring
  libpam-runtime libpam0g libpango1.0-common libpano12-0 libpano12-bin
  libpaper-utils libpaper1 libparted1.7-1 libpcap0.8 libpcre3 libpcrecpp0
  libpisock9 libpng12-0 libpng12-dev libpoppler2 libpostproc1d libpulse0
  libqt3-headers libqt3-mt libqt3-mt-dev libraw1394-8 libraw1394-dev
  librecode0 librpc-xml-perl libruby1.8 libsamplerate0 libsane libscim8c2a
  libscrollkeeper0 libsdl-image1.2 libsdl-mixer1.2 libsdl-net1.2 libselinux1
  libselinux1-dev libsensors3 libsepol1 libsepol1-dev libservlet2.3-java
  libshout3 libsigc++-2.0-0c2a libslang2 libslp1 libsnack2 libsnmp-base
  libsoundtouch1c2 libspeex1 libsqlite0 libsqlite3-0 libss2 libssl0.9.8
  libstdc++5 libstdc++6 libstdc++6-4.1-dev libsvg1 libswscale1d libsysfs2
  libt1-5 libtag1c2a libtagc0 libtaglib2.0-cil libtasn1-3 libtasn1-3-dev
  libtheora-dev libtheora0 libtiff4 libtiff4-dev libtiffxx0c2 libtool
  libtrackerclient0 libusb-0.1-4 libusplash0 libuuid1 libvisual-0.4-0 libvlc0
  libvolume-id0 libvorbis-dev libvorbis0a libvorbisenc2 libvorbisfile3
  libwpd-stream8c2a libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libwww-perl
  libwxbase2.6-0 libwxbase2.8-0 libx11-data libx86-1 libxalan2-java libxaw7
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxcomposite-dev
  libxcomposite1 libxcursor-dev libxcursor1 libxerces2-java
  libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfont1 libxft-dev
  libxft2 libxi-dev libxi6 libxml++2.6c2a libxml-twig-perl libxml2 libxml2-dev
  libxml2-utils libxmu-dev libxmu-headers libxmu6 libxmuu1 libxosd2 libxpm4
  libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxslt1.1 libxtst-dev
  libxtst6 libxvidcore4 libxvidcore4-dev libxxf86dga1
  link-grammar-dictionaries-en linux-libc-dev linux-restricted-modules-common
  linux-sound-base locales login lsb-base lsb-release lshw lsof ltrace m4
  makedev man-db manpages mcpp mesa-common-dev mesa-utils mime-support mktemp
  module-assistant module-init-tools mono-common mono-gac mono-jit
  mono-runtime mount mozilla-firefox-locale-en-gb mozilla-thunderbird mpg321
  msttcorefonts mtr-tiny myspell-en-gb myspell-en-us myspell-en-za
  mysql-common nano ncurses-base ncurses-bin net-tools netbase ntp ntpdate
  nvidia-glx nvidia-glx-dev nvidia-kernel-common nvidia-kernel-source
  odbcinst1debian1 onboard openarena openarena-data openoffice.org-hyphenation
  openoffice.org-thesaurus-en-us openprinting-ppds openssh-client openssl
  openssl-blacklist opera p7zip p7zip-full parted passwd pciutils pcmciautils
  po-debconf poppler-utils popularity-contest powermanagement-interface
  powernowd pppoeconf procps psmisc python-apport python-bittorrent
  python-central python-crypto python-dbus python-eyed3 python-gconf
  python-gdbm python-gmenu python-gst0.10 python-imaging python-imaging-tk
  python-launchpad-bugs python-libxml2 python-mutagen python-numeric
  python-problem-report python-pyorbit python-pysqlite2 python-sip4
  python-software-properties python-support python-tk python-tofu
  python-twisted python-twisted-bin python-twisted-conch python-twisted-core
  python-twisted-lore python-twisted-mail python-twisted-names
  python-twisted-news python-twisted-runner python-twisted-web
  python-twisted-words python-virtkey python-xdg python-xml
  python-zopeinterface qt3-dev-tools quilt rar rdesktop readahead
  recordmydesktop rsync ruby ruby1.8 screen scrollkeeper sdlmame sed
  shared-mime-info slocate software-properties-gtk soundconverter ssl-cert
  startup-tasks strace sudo sun-java5-bin sun-java5-jre sun-java5-plugin
  sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin sysfsutils
  sysinfo sysklogd system-services sysv-rc sysvutils tango-icon-theme tar
  tasksel tasksel-data tcl8.3 tcl8.4 tcl8.4-dev tcl8.5 tcpdump texi2html
  thunar-archive-plugin tk8.4 tk8.5 tor toshset tsclient ttf-arabeyes
  ttf-arphic-ukai ttf-arphic-uming ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
  ttf-mgopen ttf-thai-tlwg tzdata ubufox ubuntu-docs ubuntu-keyring
  ubuntu-minimal ubuntu-restricted-extras ubuntustudio-gdm-theme
  ubuntustudio-icon-theme ubuntustudio-theme ubuntustudio-wallpapers ucf unace
  unattended-upgrades unixodbc unrar unzip update-inetd update-notifier-common
  upstart upstart-compat-sysv upstart-logd usbutils usplash
  usplash-theme-ubuntu usplash-theme-ubuntustudio util-linux
  util-linux-locales vbetool vim-common vim-runtime vim-tiny vlc-plugin-esd
  vorbis-tools wamerican wbritish wesnoth wesnoth-data whiptail whois
  wireless-tools wodim wpasupplicant x-ttcidfont-conf x11-common
  x11proto-composite-dev x11proto-core-dev x11proto-render-dev xauth
  xdg-user-dirs xdg-user-dirs-gtk xdg-utils xfce4-icon-theme xfonts-100dpi
  xfonts-75dpi xfonts-base xfonts-cyrillic xfonts-encodings xfonts-utils
  xine-ui xinetd xinit xkb-data xkeyboard-config xmoto xmoto-data xpmutils
  xscreensaver-data xscreensaver-gl xserver-xorg-video-i810 xsltproc xterm
  xtrans-dev xubuntu-default-settings xubuntu-docs xvnc4viewer zlib1g
  zlib1g-dev
825 upgraded, 0 newly installed, 0 to remove and 543 not upgraded.
Need to get 873MB/1089MB of archives.
After unpacking 63.0MB disk space will be freed.
Do you want to continue [Y/n]? 

```


This updates come when upgrading failed,,

---

### Post by Vamp381 on 2008-08-08
Anyone help..................?

---

### Post by PmDematagoda on 2008-08-08
Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by Vamp381 on 2008-08-08
```
# deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt feisty main




deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
deb http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse #Added by software-properties

deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
#AUTOMATIX REPOS END
# deb http://repository.debuntu.org/ feisty multiverse
# deb-src http://repository.debuntu.org/ feisty multiverse


# LG3D repsoitories
# deb http://javadesktop.org/lg3d/debian stable contrib
# deb http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/ ./

# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy



```

Thanks for reply ! (-;

---

### Post by PmDematagoda on 2008-08-08
Hmm, the sources list looks a little strange, can you post the output of:-
```
cat /etc/lsb-release
```

---

### Post by Vamp381 on 2008-08-08
```
pavle@pavlee:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

```

---

### Post by Vamp381 on 2008-08-09
Help ? (Sorry for double posts ...)

---

