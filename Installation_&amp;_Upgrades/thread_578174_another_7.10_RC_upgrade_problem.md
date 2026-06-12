---
title: "another 7.10 RC upgrade problem"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by Hawk__0 on 2007-10-17
so im upgrading.. and it the end the update manager froze. done & done.
ubuntu freezes on boot.
all i remember is that it said 9Mins remaining and stuck like that for an hour

any help to repair plz?

---

### Post by ReyBrujo on 2007-10-17
Can you remember the error you got? Have you tried logging with an older kernel, or one of the safe ones? Or at least the last message before freezing?

---

### Post by Hawk__0 on 2007-10-17
there was no error. just hung.  do you know where the error log is located?

---

### Post by ReyBrujo on 2007-10-17
/var/log/dmesg for boot, /var/log/dist-upgrade/apt.log for upgrade

---

### Post by Hawk__0 on 2007-10-17
heres the log.. at the end it says something about losing connection.. 
(the upgrade log)
> 
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing kdelibs4c2a as dep of knetwalk
Installing libart-2.0-2 as dep of kdelibs4c2a
Installing libasound2 as dep of kdelibs4c2a
Installing libcupsys2 as dep of kdelibs4c2a
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libfreetype6 as dep of kdelibs4c2a
Installing libjasper1 as dep of kdelibs4c2a
Installing libstdc++6 as dep of kdelibs4c2a
Installing libxml2 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing libkdegames1 as dep of knetwalk
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libgnome-keyring0 as dep of libgnomeui-0
Installing liborbit2 as dep of libgnomeui-0
Installing libgnomeui-common as dep of libgnomeui-0
Installing libmono0 as dep of f-spot
Installing libglade2.0-cil as dep of f-spot
Installing libglib2.0-cil as dep of libglade2.0-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libgnome-vfs2.0-cil as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libsane as dep of libsane-dev
Installing libieee1284-3-dev as dep of libsane-dev
Installing libieee1284-3 as dep of libieee1284-3-dev
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libvorbisfile3 as dep of kolf
Installing libxine1 as dep of libxine-dev
Installing libflac8 as dep of libxine1
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing kdeedu-data as dep of blinken
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libsm6 as dep of libsm-dev
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libcaca0 as dep of libcaca-dev
Installing libcucul-dev as dep of libcaca-dev
Installing libcucul0 as dep of libcucul-dev
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libedataserver1.2-9 as dep of libecal1.2-7
Installing libnspr4-0d as dep of libedataserver1.2-9
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-10 as dep of libebook1.2-9
Installing libnss3-0d as dep of libcamel1.2-10
Installing libopal-2.2 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2
Installing libssl0.9.8 as dep of libpt-1.10.0
Installing libgtk2.0-dev as dep of libgnomeui-dev
Installing libxcomposite-dev as dep of libgtk2.0-dev
Installing libxcomposite1 as dep of libxcomposite-dev
Installing x11proto-composite-dev as dep of libxcomposite-dev
Installing libxdamage-dev as dep of libgtk2.0-dev
Installing x11proto-damage-dev as dep of libxdamage-dev
Installing libglib2.0-dev as dep of libgnomeui-dev
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing kdepimlibs5 as dep of kdepimlibs5-dev
Installing libqt4-core as dep of kdepimlibs5
Installing libqt4-gui as dep of kdepimlibs5
Installing libqt4-qt3support as dep of kdepimlibs5
Installing libqt4-sql as dep of libqt4-qt3support
Installing libsqlite3-0 as dep of libqt4-sql
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing libice6 as dep of libice-dev
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libaspell15 as dep of libaspell-dev
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing libmetacity0 as dep of metacity
Installing metacity-common as dep of libmetacity0
Installing libbeagle0 as dep of nautilus
Installing librsvg2-2 as dep of nautilus
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libtrackerclient0 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing libbind9-30 as dep of bind9-host
Installing libdns32 as dep of libbind9-30
Installing libisc32 as dep of libdns32
Installing libisccfg30 as dep of libbind9-30
Installing libisccc30 as dep of libisccfg30
Installing liblwres30 as dep of bind9-host
Installing libnotify1 as dep of python-notify
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing libsvg1 as dep of openoffice.org-draw
Installing libwpg-0.1-1 as dep of openoffice.org-draw
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing klettres-data as dep of klettres
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing o3read as dep of tracker
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing kdevelop-data as dep of kdevelop
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing libflac++6 as dep of libk3b2
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing libio-compress-zlib-perl as dep of libcompress-zlib-perl
Installing libcompress-raw-zlib-perl as dep of libio-compress-zlib-perl
Installing libio-compress-base-perl as dep of libio-compress-zlib-perl
Installing libiw29 as dep of wireless-tools
Installing libraptor1 as dep of librdf0
Installing libcurl3 as dep of libraptor1
Installing librasqal0 as dep of librdf0
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
Installing libgpg-error0 as dep of libgpg-error-dev
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libxv1 as dep of libxv-dev
Installing libdaemon0 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
Installing python-central as dep of python-apt
Installing dpkg as dep of python-central
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing libkdepim1a as dep of libkcal2b
Installing libgnome-desktop-2 as dep of libgnome-desktop-dev
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing kappfinder as dep of kdebase
Installing kate as dep of kdebase
Installing kdebase-bin as dep of kdebase
Installing kdebase-kio-plugins as dep of kdebase
Installing kdepasswd as dep of kdebase
Installing kdesktop as dep of kdebase
Installing kfind as dep of kdebase
Installing khelpcenter as dep of kdebase
Installing klipper as dep of kdebase
Installing kmenuedit as dep of kdebase
Installing konqueror-nsplugins as dep of kdebase
Installing konqueror as dep of kdebase
Installing konsole as dep of kdebase
Installing kpager as dep of kdebase
Installing kpersonalizer as dep of kdebase
Installing ksmserver as dep of kdebase
Installing ksplash as dep of kdebase
Installing ksysguard as dep of kdebase
Installing ksysguardd as dep of ksysguard
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing libpcre3 as dep of libpcre3-dev
Installing libpcrecpp0 as dep of libpcre3-dev
Installing libkdeedu3 as dep of klatin
Installing libapache2-mod-php5 as dep of php5
Installing php5-common as dep of libapache2-mod-php5
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libsoprano4 as dep of libsoprano-dev
Installing libsdl-image1.2 as dep of libsdl-image1.2-dev
Installing libjack0 as dep of audacity
Installing kstars-data as dep of kstars
Installing indi as dep of kstars
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libgcrypt11 as dep of libgcrypt11-dev
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing kdelibs5-data as dep of kdelibs5
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libx264-54 as dep of mplayer
Installing libstreams0 as dep of libstreams-dev
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing libxi6 as dep of libxi-dev
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing libkcddb1 as dep of kdemultimedia-kio-plugins
Installing libxrender1 as dep of libxrender-dev
Installing cupsys-client as dep of cupsys-bsd
Installing mysql-common as dep of mysql-client-5.0
Installing libmysqlclient15off as dep of mysql-client-5.0
Installing libcairo2 as dep of libcairo2-dev
Installing libfreetype6-dev as dep of libcairo2-dev
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing libhal-storage-dev as dep of libgnome-keyring-dev
Installing libhal-storage1 as dep of libhal-storage-dev
Installing fontconfig-config as dep of libfontconfig1
Installing kalzium-data as dep of kalzium
Installing libdb4.3 as dep of libdb4.3-dev
Installing libsvn1 as dep of subversion
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing emacs22-common as dep of emacs22-bin-common
Installing libxdmcp6 as dep of libxdmcp-dev
Installing unixodbc as dep of unixodbc-dev
Installing odbcinst1debian1 as dep of unixodbc-dev
Installing libdirectfb-0.9-25 as dep of libdirectfb-extra
Installing libkadm55 as dep of libkrb5-dev
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing libavahi-client3 as dep of libavahi-client-dev
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing apache2.2-common as dep of apache2-mpm-prefork
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing libraptor1-dev as dep of librdf0-dev
Installing libcurl4-openssl-dev as dep of libraptor1-dev
Installing librasqal0-dev as dep of librdf0-dev
Installing libdb4.4-dev as dep of librdf0-dev
Installing libdb4.4 as dep of libdb4.4-dev
Installing libkleopatra1 as dep of kalarm
Installing libkmime2 as dep of kalarm
Installing libkpimidentities1 as dep of kalarm
Installing e2fslibs as dep of e2fsprogs
Installing libldap2 as dep of libldap2-dev
Installing libpng12-0 as dep of libpng12-dev
Installing atlantik as dep of kdegames
Installing kasteroids as dep of kdegames
Installing kbattleship as dep of kdegames
Installing kbounce as dep of kdegames
Installing kfouleggs as dep of kdegames
Installing klines as dep of kdegames
Installing kmines as dep of kdegames
Installing konquest as dep of kdegames
Installing kreversi as dep of kdegames
Installing ksirtet as dep of kdegames
Installing ksmiletris as dep of kdegames
Installing ksnake as dep of kdegames
Installing kspaceduel as dep of kdegames
Installing ktron as dep of kdegames
Installing ktuberling as dep of kdegames
Installing kwin4 as dep of kdegames
Installing lskat as dep of kdegames
Installing upstart as dep of upstart-compat-sysv
Installing libsysfs-dev as dep of libdirectfb-dev
Installing libsysfs2 as dep of libsysfs-dev
Installing libgcj7-1 as dep of gij-4.1
Installing curl as dep of cogito
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libruby1.8 as dep of ruby1.8
Installing libgtop2-7 as dep of gnome-utils
Installing eyesapplet as dep of kdetoys
Installing fifteenapplet as dep of kdetoys
Installing kodo as dep of kdetoys
Installing kteatime as dep of kdetoys
Installing firefox as dep of firefox-dev
Installing libnss3-dev as dep of firefox-dev
Installing libnspr4-dev as dep of libnss3-dev
Installing compiz-core as dep of compiz-plugins
Installing libltdl3 as dep of libltdl3-dev
Installing dmz-cursor-theme as dep of human-theme
Installing libxcursor1 as dep of libxcursor-dev
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing libexif12 as dep of libexif-dev
Installing python-wxgtk2.8 as dep of python-wxtools
Installing belocs-locales-bin as dep of locales
Installing libbonobo2-0 as dep of libbonobo2-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing mysql-admin-common as dep of mysql-admin
Installing mysql-query-browser as dep of mysql-admin
Installing mysql-query-browser-common as dep of mysql-query-browser
Installing libgnutlsxx13 as dep of libgnutls-dev
Installing liblzo2-dev as dep of libgnutls-dev
Installing libclucene0 as dep of libclucene-dev
Installing gij-4.2 as dep of gij
Installing libqt3-mt as dep of libqt3-mt-dev
Installing libqt3-headers as dep of libqt3-mt-dev
Installing python-gtk2 as dep of python-glade2
Installing amarok as dep of amarok-xine
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing libxt6 as dep of libxt-dev
Installing language-selector-common as dep of language-selector
Installing wine as dep of wine-dev
Installing libxmu6 as dep of libxmu-dev
Installing libboost-python1.34.1 as dep of kig
Installing libxext6 as dep of libxext-dev
Installing libjpeg62 as dep of libjpeg62-dev
Installing libswscale1d as dep of ffmpeg
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing recordmydesktop as dep of gtk-recordmydesktop
Installing libsmpeg0 as dep of libsmpeg-dev
Installing libmagic1 as dep of file
Installing libungif4g as dep of libungif4-dev
Installing libtiff4 as dep of libtiff4-dev
Installing libtiffxx0c2 as dep of libtiff4-dev
Installing python-sexy as dep of gnome-app-install
Installing libmad0 as dep of libmad0-dev
Installing libgail-dev as dep of libgnomecanvas2-dev
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing libgpgme11 as dep of libgpgme11-dev
Installing gimp-data as dep of gimp
Installing ttf-dejavu-core as dep of ttf-dejavu
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing libgl1-mesa-glx as dep of libgl1-mesa-dev
Installing libpq5 as dep of libpq-dev
Installing dmidecode as dep of laptop-detect
Installing libxrandr2 as dep of libxrandr-dev
Installing wireshark-common as dep of wireshark
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libcegui-mk2-1 as dep of libcegui-mk2-dev
Installing libalut0 as dep of rss-glx
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing kgeography as dep of kdeedu
Installing kgeography-data as dep of kgeography
Installing kpercentage as dep of kdeedu
Installing kturtle as dep of kdeedu
Installing kverbos as dep of kdeedu
Installing libavahi-common3 as dep of libavahi-common-dev
Installing libxinerama1 as dep of libxinerama-dev
Installing libode0debian1 as dep of xmoto
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 121
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 26 as a solution to libwnck18 8
  Removing libwnck18 rather than change libwnck-common
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 1 as a solution to firefox 8
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 8 as a solution to libawn-bzr 7
  Removing libawn-bzr rather than change libwnck18
Investigating kdelibs5
Package kdelibs5 has broken dep on dbus-x11
  Considering dbus-x11 1 as a solution to kdelibs5 4
Package kdelibs5 has broken dep on dbus
  Considering dbus 121 as a solution to kdelibs5 4
  Or group remove for kdelibs5
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 -1 as a solution to libmtp6 3
  Added libmtp5 to the remove list
  Fixing libmtp6 via remove of libmtp5
Investigating libsoprano4
Package libsoprano4 has broken dep on libsoprano3
  Considering libsoprano3 -2 as a solution to libsoprano4 2
  Added libsoprano3 to the remove list
  Fixing libsoprano4 via remove of libsoprano3
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 8 as a solution to emerald 2
  Removing emerald rather than change libwnck18
Investigating libcurl4-openssl-dev
Package libcurl4-openssl-dev has broken dep on libcurl-dev
  Considering libcurl3-openssl-dev -1 as a solution to libcurl4-openssl-dev 2
  Added libcurl3-openssl-dev to the remove list
  Considering libcurl4-gnutls-dev 0 as a solution to libcurl4-openssl-dev 2
  Fixing libcurl4-openssl-dev via remove of libcurl3-openssl-dev
Investigating kdelibs5-dev
Package kdelibs5-dev has broken dep on kdelibs5
  Considering kdelibs5 4 as a solution to kdelibs5-dev 1
  Removing kdelibs5-dev rather than change kdelibs5
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating libcegui-mk2-1
Package libcegui-mk2-1 has broken dep on libcegui-mk2-0c2a
  Considering libcegui-mk2-0c2a 3 as a solution to libcegui-mk2-1 1
  Holding Back libcegui-mk2-1 rather than change libcegui-mk2-0c2a
Investigating kdepimlibs5
Package kdepimlibs5 has broken dep on kdelibs5
  Considering kdelibs5 4 as a solution to kdepimlibs5 1
  Removing kdepimlibs5 rather than change kdelibs5
Investigating libxine1-plugins
Package libxine1-plugins has broken dep on libxine1-kde
  Considering libxine1-kde -1 as a solution to libxine1-plugins 1
  Added libxine1-kde to the remove list
  Fixing libxine1-plugins via remove of libxine1-kde
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 8 as a solution to libemeraldengine0 1
  Removing libemeraldengine0 rather than change libwnck18
Investigating kdepimlibs5-dev
Package kdepimlibs5-dev has broken dep on kdepimlibs5
  Considering kdepimlibs5 1 as a solution to kdepimlibs5-dev 0
  Removing kdepimlibs5-dev rather than change kdepimlibs5
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating libnspr4-dev
Package libnspr4-dev has broken dep on libnspr4
  Considering libnspr4 1 as a solution to libnspr4-dev 0
  Holding Back libnspr4-dev rather than change libnspr4
Investigating libopal-2.2
Package libopal-2.2 has broken dep on libopal-2.2.0
  Considering libopal-2.2.0 -1 as a solution to libopal-2.2 0
  Added libopal-2.2.0 to the remove list
  Fixing libopal-2.2 via remove of libopal-2.2.0
Investigating libgnome-speech7
Package libgnome-speech7 has broken dep on libgnome-speech3
  Considering libgnome-speech3 -1 as a solution to libgnome-speech7 0
  Added libgnome-speech3 to the remove list
  Fixing libgnome-speech7 via remove of libgnome-speech3
Investigating libuniconf4.3
Package libuniconf4.3 has broken dep on libuniconf4.2
  Considering libuniconf4.2 -1 as a solution to libuniconf4.3 0
  Added libuniconf4.2 to the remove list
  Fixing libuniconf4.3 via remove of libuniconf4.2
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 2 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating libdb4.3-dev
Package libdb4.3-dev has broken dep on libdb-dev
  Considering libdb-dev 0 as a solution to libdb4.3-dev -1
  Removing libdb4.3-dev rather than change libdb-dev
Investigating libnss-dev
Package libnss-dev has broken dep on libnss3
  Considering libnss3 1 as a solution to libnss-dev -1
  Removing libnss-dev rather than change libnss3
Investigating awn-core-applets-bzr
Package awn-core-applets-bzr has broken dep on libawn-bzr
  Considering libawn-bzr 7 as a solution to awn-core-applets-bzr -1
  Removing awn-core-applets-bzr rather than change libawn-bzr
Investigating avant-window-navigator-bzr
Package avant-window-navigator-bzr has broken dep on libawn-bzr
  Considering libawn-bzr 7 as a solution to avant-window-navigator-bzr -1
  Removing avant-window-navigator-bzr rather than change libawn-bzr
Investigating libcegui-mk2-dev
Package libcegui-mk2-dev has broken dep on libcegui-mk2-1
  Considering libcegui-mk2-1 1 as a solution to libcegui-mk2-dev 2
  Holding Back libcegui-mk2-dev rather than change libcegui-mk2-1
Investigating libnss3-dev
Package libnss3-dev has broken dep on libnspr4-dev
  Considering libnspr4-dev 0 as a solution to libnss3-dev 1
  Holding Back libnss3-dev rather than change libnspr4-dev
Investigating firefox-dev
Package firefox-dev has broken dep on libnss3-dev
  Considering libnss3-dev 1 as a solution to firefox-dev 2
  Removing firefox-dev rather than change libnss3-dev
 Try to Re-Instate libcegui-mk2-dev
Investigating miro
Package miro has broken dep on firefox-dev
  Considering firefox-dev 2 as a solution to miro -1
  Removing miro rather than change firefox-dev
Done
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing kdelibs4c2a as dep of knetwalk
Installing libart-2.0-2 as dep of kdelibs4c2a
Installing libasound2 as dep of kdelibs4c2a
Installing libcupsys2 as dep of kdelibs4c2a
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libfreetype6 as dep of kdelibs4c2a
Installing libjasper1 as dep of kdelibs4c2a
Installing libstdc++6 as dep of kdelibs4c2a
Installing libxml2 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing libkdegames1 as dep of knetwalk
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libgnome-keyring0 as dep of libgnomeui-0
Installing liborbit2 as dep of libgnomeui-0
Installing libgnomeui-common as dep of libgnomeui-0
Installing libmono0 as dep of f-spot
Installing libglade2.0-cil as dep of f-spot
Installing libglib2.0-cil as dep of libglade2.0-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libgnome-vfs2.0-cil as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libsane as dep of libsane-dev
Installing libieee1284-3-dev as dep of libsane-dev
Installing libieee1284-3 as dep of libieee1284-3-dev
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libvorbisfile3 as dep of kolf
Installing libxine1 as dep of libxine-dev
Installing libflac8 as dep of libxine1
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing kdeedu-data as dep of blinken
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libsm6 as dep of libsm-dev
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libcaca0 as dep of libcaca-dev
Installing libcucul-dev as dep of libcaca-dev
Installing libcucul0 as dep of libcucul-dev
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libedataserver1.2-9 as dep of libecal1.2-7
Installing libnspr4-0d as dep of libedataserver1.2-9
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-10 as dep of libebook1.2-9
Installing libnss3-0d as dep of libcamel1.2-10
Installing libopal-2.2 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2
Installing libssl0.9.8 as dep of libpt-1.10.0
Installing libgtk2.0-dev as dep of libgnomeui-dev
Installing libxcomposite-dev as dep of libgtk2.0-dev
Installing libxcomposite1 as dep of libxcomposite-dev
Installing x11proto-composite-dev as dep of libxcomposite-dev
Installing libxdamage-dev as dep of libgtk2.0-dev
Installing x11proto-damage-dev as dep of libxdamage-dev
Installing libglib2.0-dev as dep of libgnomeui-dev
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing kdepimlibs5 as dep of kdepimlibs5-dev
Installing libqt4-core as dep of kdepimlibs5
Installing libqt4-gui as dep of kdepimlibs5
Installing libqt4-qt3support as dep of kdepimlibs5
Installing libqt4-sql as dep of libqt4-qt3support
Installing libsqlite3-0 as dep of libqt4-sql
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing libice6 as dep of libice-dev
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libaspell15 as dep of libaspell-dev
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing libmetacity0 as dep of metacity
Installing metacity-common as dep of libmetacity0
Installing libbeagle0 as dep of nautilus
Installing librsvg2-2 as dep of nautilus
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libtrackerclient0 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing libbind9-30 as dep of bind9-host
Installing libdns32 as dep of libbind9-30
Installing libisc32 as dep of libdns32
Installing libisccfg30 as dep of libbind9-30
Installing libisccc30 as dep of libisccfg30
Installing liblwres30 as dep of bind9-host
Installing libnotify1 as dep of python-notify
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing libsvg1 as dep of openoffice.org-draw
Installing libwpg-0.1-1 as dep of openoffice.org-draw
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing klettres-data as dep of klettres
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing o3read as dep of tracker
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing kdevelop-data as dep of kdevelop
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing libflac++6 as dep of libk3b2
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing libio-compress-zlib-perl as dep of libcompress-zlib-perl
Installing libcompress-raw-zlib-perl as dep of libio-compress-zlib-perl
Installing libio-compress-base-perl as dep of libio-compress-zlib-perl
Installing libiw29 as dep of wireless-tools
Installing libraptor1 as dep of librdf0
Installing libcurl3 as dep of libraptor1
Installing librasqal0 as dep of librdf0
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
Installing libgpg-error0 as dep of libgpg-error-dev
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libxv1 as dep of libxv-dev
Installing libdaemon0 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
Installing python-central as dep of python-apt
Installing dpkg as dep of python-central
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing libkdepim1a as dep of libkcal2b
Installing libgnome-desktop-2 as dep of libgnome-desktop-dev
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing kappfinder as dep of kdebase
Installing kate as dep of kdebase
Installing kdebase-bin as dep of kdebase
Installing kdebase-kio-plugins as dep of kdebase
Installing kdepasswd as dep of kdebase
Installing kdesktop as dep of kdebase
Installing kfind as dep of kdebase
Installing khelpcenter as dep of kdebase
Installing klipper as dep of kdebase
Installing kmenuedit as dep of kdebase
Installing konqueror-nsplugins as dep of kdebase
Installing konqueror as dep of kdebase
Installing konsole as dep of kdebase
Installing kpager as dep of kdebase
Installing kpersonalizer as dep of kdebase
Installing ksmserver as dep of kdebase
Installing ksplash as dep of kdebase
Installing ksysguard as dep of kdebase
Installing ksysguardd as dep of ksysguard
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing libpcre3 as dep of libpcre3-dev
Installing libpcrecpp0 as dep of libpcre3-dev
Installing libkdeedu3 as dep of klatin
Installing libapache2-mod-php5 as dep of php5
Installing php5-common as dep of libapache2-mod-php5
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libsoprano4 as dep of libsoprano-dev
Installing libsdl-image1.2 as dep of libsdl-image1.2-dev
Installing libjack0 as dep of audacity
Installing kstars-data as dep of kstars
Installing indi as dep of kstars
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libgcrypt11 as dep of libgcrypt11-dev
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing kdelibs5-data as dep of kdelibs5
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libx264-54 as dep of mplayer
Installing libstreams0 as dep of libstreams-dev
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing libxi6 as dep of libxi-dev
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing libkcddb1 as dep of kdemultimedia-kio-plugins
Installing libxrender1 as dep of libxrender-dev
Installing cupsys-client as dep of cupsys-bsd
Installing mysql-common as dep of mysql-client-5.0
Installing libmysqlclient15off as dep of mysql-client-5.0
Installing libcairo2 as dep of libcairo2-dev
Installing libfreetype6-dev as dep of libcairo2-dev
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing libhal-storage-dev as dep of libgnome-keyring-dev
Installing libhal-storage1 as dep of libhal-storage-dev
Installing fontconfig-config as dep of libfontconfig1
Installing kalzium-data as dep of kalzium
Installing libdb4.3 as dep of libdb4.3-dev
Installing libsvn1 as dep of subversion
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing emacs22-common as dep of emacs22-bin-common
Installing libxdmcp6 as dep of libxdmcp-dev
Installing unixodbc as dep of unixodbc-dev
Installing odbcinst1debian1 as dep of unixodbc-dev
Installing libdirectfb-0.9-25 as dep of libdirectfb-extra
Installing libkadm55 as dep of libkrb5-dev
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing libavahi-client3 as dep of libavahi-client-dev
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing apache2.2-common as dep of apache2-mpm-prefork
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing libraptor1-dev as dep of librdf0-dev
Installing libcurl4-openssl-dev as dep of libraptor1-dev
Installing librasqal0-dev as dep of librdf0-dev
Installing libdb4.4-dev as dep of librdf0-dev
Installing libdb4.4 as dep of libdb4.4-dev
Installing libkleopatra1 as dep of kalarm
Installing libkmime2 as dep of kalarm
Installing libkpimidentities1 as dep of kalarm
Installing e2fslibs as dep of e2fsprogs
Installing libldap2 as dep of libldap2-dev
Installing libpng12-0 as dep of libpng12-dev
Installing atlantik as dep of kdegames
Installing kasteroids as dep of kdegames
Installing kbattleship as dep of kdegames
Installing kbounce as dep of kdegames
Installing kfouleggs as dep of kdegames
Installing klines as dep of kdegames
Installing kmines as dep of kdegames
Installing konquest as dep of kdegames
Installing kreversi as dep of kdegames
Installing ksirtet as dep of kdegames
Installing ksmiletris as dep of kdegames
Installing ksnake as dep of kdegames
Installing kspaceduel as dep of kdegames
Installing ktron as dep of kdegames
Installing ktuberling as dep of kdegames
Installing kwin4 as dep of kdegames
Installing lskat as dep of kdegames
Installing upstart as dep of upstart-compat-sysv
Installing libsysfs-dev as dep of libdirectfb-dev
Installing libsysfs2 as dep of libsysfs-dev
Installing libgcj7-1 as dep of gij-4.1
Installing curl as dep of cogito
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libruby1.8 as dep of ruby1.8
Installing libgtop2-7 as dep of gnome-utils
Installing eyesapplet as dep of kdetoys
Installing fifteenapplet as dep of kdetoys
Installing kodo as dep of kdetoys
Installing kteatime as dep of kdetoys
Installing firefox as dep of firefox-dev
Installing libnss3-dev as dep of firefox-dev
Installing libnspr4-dev as dep of libnss3-dev
Installing compiz-core as dep of compiz-plugins
Installing libltdl3 as dep of libltdl3-dev
Installing dmz-cursor-theme as dep of human-theme
Installing libxcursor1 as dep of libxcursor-dev
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing libexif12 as dep of libexif-dev
Installing python-wxgtk2.8 as dep of python-wxtools
Installing belocs-locales-bin as dep of locales
Installing libbonobo2-0 as dep of libbonobo2-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing mysql-admin-common as dep of mysql-admin
Installing mysql-query-browser as dep of mysql-admin
Installing mysql-query-browser-common as dep of mysql-query-browser
Installing libgnutlsxx13 as dep of libgnutls-dev
Installing liblzo2-dev as dep of libgnutls-dev
Installing libclucene0 as dep of libclucene-dev
Installing gij-4.2 as dep of gij
Installing libqt3-mt as dep of libqt3-mt-dev
Installing libqt3-headers as dep of libqt3-mt-dev
Installing python-gtk2 as dep of python-glade2
Installing amarok as dep of amarok-xine
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing libxt6 as dep of libxt-dev
Installing language-selector-common as dep of language-selector
Installing wine as dep of wine-dev
Installing libxmu6 as dep of libxmu-dev
Installing libboost-python1.34.1 as dep of kig
Installing libxext6 as dep of libxext-dev
Installing libjpeg62 as dep of libjpeg62-dev
Installing libswscale1d as dep of ffmpeg
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing recordmydesktop as dep of gtk-recordmydesktop
Installing libsmpeg0 as dep of libsmpeg-dev
Installing libmagic1 as dep of file
Installing libungif4g as dep of libungif4-dev
Installing libtiff4 as dep of libtiff4-dev
Installing libtiffxx0c2 as dep of libtiff4-dev
Installing python-sexy as dep of gnome-app-install
Installing libmad0 as dep of libmad0-dev
Installing libgail-dev as dep of libgnomecanvas2-dev
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing libgpgme11 as dep of libgpgme11-dev
Installing gimp-data as dep of gimp
Installing ttf-dejavu-core as dep of ttf-dejavu
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing libgl1-mesa-glx as dep of libgl1-mesa-dev
Installing libpq5 as dep of libpq-dev
Installing dmidecode as dep of laptop-detect
Installing libxrandr2 as dep of libxrandr-dev
Installing wireshark-common as dep of wireshark
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libcegui-mk2-1 as dep of libcegui-mk2-dev
Installing libalut0 as dep of rss-glx
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing kgeography as dep of kdeedu
Installing kgeography-data as dep of kgeography
Installing kpercentage as dep of kdeedu
Installing kturtle as dep of kdeedu
Installing kverbos as dep of kdeedu
Installing libavahi-common3 as dep of libavahi-common-dev
Installing libxinerama1 as dep of libxinerama-dev
Installing libode0debian1 as dep of xmoto
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 121
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 26 as a solution to libwnck18 8
  Removing libwnck18 rather than change libwnck-common
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 1 as a solution to firefox 8
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 8 as a solution to libawn-bzr 7
  Removing libawn-bzr rather than change libwnck18
Investigating kdelibs5
Package kdelibs5 has broken dep on dbus-x11
  Considering dbus-x11 1 as a solution to kdelibs5 4
Package kdelibs5 has broken dep on dbus
  Considering dbus 121 as a solution to kdelibs5 4
  Or group remove for kdelibs5
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 -1 as a solution to libmtp6 3
  Added libmtp5 to the remove list
  Fixing libmtp6 via remove of libmtp5
Investigating libsoprano4
Package libsoprano4 has broken dep on libsoprano3
  Considering libsoprano3 -2 as a solution to libsoprano4 2
  Added libsoprano3 to the remove list
  Fixing libsoprano4 via remove of libsoprano3
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 8 as a solution to emerald 2
  Removing emerald rather than change libwnck18
Investigating libcurl4-openssl-dev
Package libcurl4-openssl-dev has broken dep on libcurl-dev
  Considering libcurl3-openssl-dev -1 as a solution to libcurl4-openssl-dev 2
  Added libcurl3-openssl-dev to the remove list
  Considering libcurl4-gnutls-dev 0 as a solution to libcurl4-openssl-dev 2
  Fixing libcurl4-openssl-dev via remove of libcurl3-openssl-dev
Investigating kdelibs5-dev
Package kdelibs5-dev has broken dep on kdelibs5
  Considering kdelibs5 4 as a solution to kdelibs5-dev 1
  Removing kdelibs5-dev rather than change kdelibs5
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating libcegui-mk2-1
Package libcegui-mk2-1 has broken dep on libcegui-mk2-0c2a
  Considering libcegui-mk2-0c2a 3 as a solution to libcegui-mk2-1 1
  Holding Back libcegui-mk2-1 rather than change libcegui-mk2-0c2a
Investigating kdepimlibs5
Package kdepimlibs5 has broken dep on kdelibs5
  Considering kdelibs5 4 as a solution to kdepimlibs5 1
  Removing kdepimlibs5 rather than change kdelibs5
Investigating libxine1-plugins
Package libxine1-plugins has broken dep on libxine1-kde
  Considering libxine1-kde -1 as a solution to libxine1-plugins 1
  Added libxine1-kde to the remove list
  Fixing libxine1-plugins via remove of libxine1-kde
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 8 as a solution to libemeraldengine0 1
  Removing libemeraldengine0 rather than change libwnck18
Investigating kdepimlibs5-dev
Package kdepimlibs5-dev has broken dep on kdepimlibs5
  Considering kdepimlibs5 1 as a solution to kdepimlibs5-dev 0
  Removing kdepimlibs5-dev rather than change kdepimlibs5
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating libnspr4-dev
Package libnspr4-dev has broken dep on libnspr4
  Considering libnspr4 1 as a solution to libnspr4-dev 0
  Holding Back libnspr4-dev rather than change libnspr4
Investigating libopal-2.2
Package libopal-2.2 has broken dep on libopal-2.2.0
  Considering libopal-2.2.0 -1 as a solution to libopal-2.2 0
  Added libopal-2.2.0 to the remove list
  Fixing libopal-2.2 via remove of libopal-2.2.0
Investigating libgnome-speech7
Package libgnome-speech7 has broken dep on libgnome-speech3
  Considering libgnome-speech3 -1 as a solution to libgnome-speech7 0
  Added libgnome-speech3 to the remove list
  Fixing libgnome-speech7 via remove of libgnome-speech3
Investigating libuniconf4.3
Package libuniconf4.3 has broken dep on libuniconf4.2
  Considering libuniconf4.2 -1 as a solution to libuniconf4.3 0
  Added libuniconf4.2 to the remove list
  Fixing libuniconf4.3 via remove of libuniconf4.2
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 2 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating libdb4.3-dev
Package libdb4.3-dev has broken dep on libdb-dev
  Considering libdb-dev 0 as a solution to libdb4.3-dev -1
  Removing libdb4.3-dev rather than change libdb-dev
Investigating libnss-dev
Package libnss-dev has broken dep on libnss3
  Considering libnss3 1 as a solution to libnss-dev -1
  Removing libnss-dev rather than change libnss3
Investigating awn-core-applets-bzr
Package awn-core-applets-bzr has broken dep on libawn-bzr
  Considering libawn-bzr 7 as a solution to awn-core-applets-bzr -1
  Removing awn-core-applets-bzr rather than change libawn-bzr
Investigating avant-window-navigator-bzr
Package avant-window-navigator-bzr has broken dep on libawn-bzr
  Considering libawn-bzr 7 as a solution to avant-window-navigator-bzr -1
  Removing avant-window-navigator-bzr rather than change libawn-bzr
Investigating libcegui-mk2-dev
Package libcegui-mk2-dev has broken dep on libcegui-mk2-1
  Considering libcegui-mk2-1 1 as a solution to libcegui-mk2-dev 2
  Holding Back libcegui-mk2-dev rather than change libcegui-mk2-1
Investigating libnss3-dev
Package libnss3-dev has broken dep on libnspr4-dev
  Considering libnspr4-dev 0 as a solution to libnss3-dev 1
  Holding Back libnss3-dev rather than change libnspr4-dev
Investigating firefox-dev
Package firefox-dev has broken dep on libnss3-dev
  Considering libnss3-dev 1 as a solution to firefox-dev 2
  Removing firefox-dev rather than change libnss3-dev
 Try to Re-Instate libcegui-mk2-dev
Investigating miro
Package miro has broken dep on firefox-dev
  Considering firefox-dev 2 as a solution to miro -1
  Removing miro rather than change firefox-dev
Done
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
WARNING:root:no activity on terminal for 240 seconds (Configuring nfs-common)
The application 'update-manager' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.


and the other log, does not exist.

and now i remember where it was hung cuz of the log.  at nf-common

---

### Post by Sturmeh on 2007-10-18
> WARNING:root:no activity on terminal for 240 seconds (Configuring nfs-common)
The application 'update-manager' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

An error? lol.

---

