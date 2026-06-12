---
title: "error while upgrading to 7.10"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by joereith on 2007-10-25
here is my log files

main.log

2007-10-25 22:43:25,319 INFO release-upgrader version '0.81' started
2007-10-25 22:43:27,498 DEBUG lsb-release: 'feisty'
2007-10-25 22:43:27,498 DEBUG _pythonSymlinkCheck run
2007-10-25 22:43:29,342 DEBUG checkViewDepends()
2007-10-25 22:43:29,343 DEBUG getRequiredBackports()
2007-10-25 22:44:11,120 DEBUG cancelClicked
2007-10-25 22:44:11,142 ERROR IOError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2) 
'. Retrying (currentRetry: 0)
2007-10-25 22:44:11,193 ERROR IOError in cache.update(): 'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/feisty/Release.gpg) 
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2) 
'. Retrying (currentRetry: 1)
2007-10-25 22:44:11,241 ERROR IOError in cache.update(): 'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2) 
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/feisty/Release.gpg) 
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2) 
'. Retrying (currentRetry: 2)
2007-10-25 22:44:11,241 ERROR doUpdate() failed complettely
2007-10-25 22:44:16,269 DEBUG marking 'release-upgrader-apt' for install
2007-10-25 22:44:16,382 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-25 22:44:16,558 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 1 Complete: 0 Local: 0 IsTrusted: 0 FileSize: 1924684 DestFile:'/tmp/tmpV-qmQD/backports/partial/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ub' 
2007-10-25 22:44:16,558 ERROR pre-requists item 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' is NOT trusted



apt.log

 Installing libc6 as dep of mcpp
Installing xkb-data as dep of xkeyboard-config
Installing libatk1.0-0 as dep of gnome-keyring
Installing libglib2.0-0 as dep of libatk1.0-0
Installing libcairo2 as dep of gnome-keyring
Installing libfontconfig1 as dep of libcairo2
Installing fontconfig-config as dep of libfontconfig1
Installing libpng12-0 as dep of libcairo2
Installing libdbus-1-3 as dep of gnome-keyring
Installing libpango1.0-0 as dep of gnome-keyring
Installing libpango1.0-common as dep of libpango1.0-0
Installing libdatrie0 as dep of libpango1.0-0
Installing libthai0 as dep of libpango1.0-0
Installing libthai-data as dep of libthai0
Installing libxrandr2 as dep of gnome-keyring
Installing libgnome-keyring0 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libgnomevfs2-0 as dep of libgnomeui-0
Installing libdbus-glib-1-2 as dep of libgnomevfs2-0
Installing libselinux1 as dep of libgnomevfs2-0
Installing libsepol1 as dep of libselinux1
Installing libxml2 as dep of libgnomevfs2-0
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomeui-common as dep of libgnomeui-0
Installing libmono0 as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-sharpzip2.84-cil as dep of f-spot
Installing libmono-system2.0-cil as dep of libmono-sharpzip2.84-cil
Installing libmono-security2.0-cil as dep of libmono-system2.0-cil
Installing libmono-sqlite2.0-cil as dep of f-spot
Installing libmono-system-data2.0-cil as dep of libmono-sqlite2.0-cil
Installing libmono-data-tds2.0-cil as dep of libmono-system-data2.0-cil
Installing libsqlite3-0 as dep of libmono-sqlite2.0-cil
Installing libmono-system-web2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libndesk-dbus-glib1.0-cil as dep of f-spot
Installing libndesk-dbus1.0-cil as dep of libndesk-dbus-glib1.0-cil
Installing libcupsys2 as dep of libgnomecupsui1.0-1c2a
Installing libgcc1 as dep of libgnomecupsui1.0-1c2a
Installing gcc-4.1-base as dep of libgcc1
Installing libstdc++6 as dep of libgnomecupsui1.0-1c2a
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libnautilus-extension1 as dep of totem-gstreamer
Installing libtotem-plparser1 as dep of totem-gstreamer
Installing gstreamer0.10-plugins-base as dep of totem-gstreamer
Installing gstreamer0.10-plugins-bad as dep of gstreamer0.10-plugins-bad-dbg
Installing libcdaudio1 as dep of gstreamer0.10-plugins-bad
Installing libjack0.100.0-0 as dep of gstreamer0.10-plugins-bad
Installing libfreebob0 as dep of libjack0.100.0-0
Installing libiec61883-0 as dep of libfreebob0
Installing libmusicbrainz4c2a as dep of gstreamer0.10-plugins-bad
Installing libsoundtouch1c2 as dep of gstreamer0.10-plugins-bad
Installing libwavpack1 as dep of gstreamer0.10-plugins-bad
Installing gstreamer0.10-sdl as dep of gstreamer0.10-plugins-bad-dbg
Installing gstreamer0.10-gl as dep of gstreamer0.10-plugins-bad-dbg
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdirectfb-0.9-25 as dep of libsdl1.2debian-alsa
Installing xserver-xorg-core as dep of xserver-xorg-video-rendition
Installing libdrm2 as dep of xserver-xorg-core
Installing libgail-common as dep of libgtkhtml3.8-15
Installing libgail18 as dep of libgail-common
Installing libgnomeprint2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing libgnomeprintui2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libqt3-mt as dep of libarts1c2a
Installing libxslt1.1 as dep of libxmlsec1
Installing libgpg-error0 as dep of libxslt1.1
Installing gcc-3.3-base as dep of libstdc++5
Installing libpanel-applet2-0 as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libedataserver1.2-9 as dep of libecal1.2-7
Installing libsoup2.2-8 as dep of evolution-webcal
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-10 as dep of libebook1.2-9
Installing libopal-2.2.0 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2.0
Installing libsasl2-2 as dep of libpt-1.10.0
Installing libdb4.2 as dep of libsasl2-2
Installing libsasl2-modules as dep of libsasl2-2
Installing libssl0.9.8 as dep of libsasl2-modules
Installing liblua50 as dep of kdelibs4c2a
Installing liblualib50 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing openoffice.org-style-human as dep of openoffice.org-common
Installing openoffice.org-hyphenation as dep of openoffice.org-core
Installing libcurl3 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libicu36 as dep of openoffice.org-core
Installing libstlport5.1 as dep of openoffice.org-core
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing python-central as dep of python-gst0.10
Installing gstreamer0.10-gnomevfs as dep of gstreamer0.10-plugins-base-dbg
Installing python2.5 as dep of update-manager
Installing python2.5-minimal as dep of python2.5
Installing libreadline5 as dep of python2.5
Installing update-manager-core as dep of update-manager
Installing libwps-0.1-1 as dep of openoffice.org-writer
Installing python-uno as dep of openoffice.org-writer
Installing python as dep of python-uno
Installing python-minimal as dep of python
Installing libgs-esp8 as dep of gs-esp
Installing libcupsimage2 as dep of libgs-esp8
Installing gnome-media-common as dep of gnome-media
Installing libgcj-common as dep of libgcj7-0
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
Installing metacity-common as dep of metacity
Installing libbeagle0 as dep of nautilus
Installing libeel2-2 as dep of nautilus
Installing libeel2-data as dep of libeel2-2
Installing nautilus-data as dep of nautilus
Installing libgnome2-common as dep of libgnome2-0
Installing libdns22 as dep of bind9-host
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing gnome-user-guide as dep of ubuntu-docs
Installing linux-headers-2.6.20-15-generic as dep of linux-headers-generic
Installing linux-headers-2.6.20-15 as dep of linux-headers-2.6.20-15-generic
Installing dhcp3-common as dep of dhcp3-client
Installing libatspi1.0-0 as dep of python-at-spi
Installing libgl1-mesa-dev as dep of nvidia-glx-dev
Installing mesa-common-dev as dep of libgl1-mesa-dev
Installing libx11-dev as dep of mesa-common-dev
Installing libx11-6 as dep of libx11-dev
Installing libxau-dev as dep of libx11-dev
Installing libxau6 as dep of libxau-dev
Installing x11proto-core-dev as dep of libxau-dev
Installing libxdmcp-dev as dep of libx11-dev
Installing libxdmcp6 as dep of libxdmcp-dev
Installing x11proto-input-dev as dep of libx11-dev
Installing x11proto-kb-dev as dep of libx11-dev
Installing xtrans-dev as dep of libx11-dev
Installing libgl1-mesa-glx as dep of libgl1-mesa-dev
Installing libgl1-mesa-dri as dep of libgl1-mesa-dev
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: command-not-found
Installing command-not-found as dep of ubuntu-standard
Installing command-not-found-data as dep of command-not-found
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
Installing libopenobex1 as dep of libbtctl4
Installing libavahi-core5 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing python-gnome2-desktop as dep of gnome-games
Installing wodim as dep of cdrecord
Installing hwdb-client-common as dep of hwdb-client-gnome
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt as dep of python-apt
Installing gksu as dep of gdebi
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgnome-pilot2 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing libnm-glib0 as dep of evolution
Installing evolution-common as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing gtkhtml3.14 as dep of evolution
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing binutils as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.20-15-generic as dep of linux-image-generic
Installing libportaudio2 as dep of audacity
Installing libsamplerate0 as dep of audacity
Installing libgnomekbd1 as dep of gnome-screensaver
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libgnomekbdui1 as dep of gnome-screensaver
Installing libxcomposite1 as dep of gnome-mag
Installing libgpod1 as dep of rhythmbox
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing gnome-panel-data as dep of gnome-panel
Installing libsnmp9 as dep of hpijs
Installing libsnmp-base as dep of libsnmp9
Installing genisoimage as dep of dvd+rw-tools
Installing libcaca0 as dep of mplayer
Installing libcucul0 as dep of libcaca0
Installing libpulse0 as dep of mplayer
Installing feisty-gdm-themes as dep of ubuntu-artwork
Installing feisty-session-splashes as dep of ubuntu-artwork
Installing feisty-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libslab0 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing avahi-autoipd as dep of ubuntu-desktop
Installing dcraw as dep of ubuntu-desktop
Installing desktop-effects as dep of ubuntu-desktop
Installing compiz as dep of desktop-effects
Installing compiz-core as dep of compiz
Installing compiz-plugins as dep of compiz
Installing libdecoration0 as dep of compiz-plugins
Installing compiz-gtk as dep of compiz
Installing compiz-gnome as dep of compiz
Installing gs-esp-x as dep of ubuntu-desktop
Installing gtk2-engines-pixbuf as dep of ubuntu-desktop
Installing libnss-mdns as dep of ubuntu-desktop
Installing openprinting-ppds as dep of ubuntu-desktop
new important dependency: espeak
Installing espeak as dep of ubuntu-desktop
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
new important dependency: network-manager-gnome
Installing network-manager-gnome as dep of ubuntu-desktop
Installing libnm-util0 as dep of network-manager-gnome
Installing network-manager as dep of network-manager-gnome
Installing libnl1-pre6 as dep of network-manager
Installing dhcdbd as dep of network-manager
new important dependency: restricted-manager
Installing restricted-manager as dep of ubuntu-desktop
Installing python-notify as dep of restricted-manager
new important dependency: scim-tables-additional
Installing scim-tables-additional as dep of ubuntu-desktop
Installing scim-modules-table as dep of scim-tables-additional
Installing pouetchess-data as dep of pouetchess
Installing cupsys-client as dep of cupsys-bsd
Installing update-inetd as dep of cupsys-bsd
Installing ntp as dep of ntp-simple
Installing dmsetup as dep of libdevmapper1.02
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing python-apport as dep of apport
Installing python-problem-report as dep of python-apport
Installing python-launchpad-bugs as dep of python-apport
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing libvte9 as dep of gnome-terminal
Installing libvte-common as dep of libvte9
Installing gnome-terminal-data as dep of gnome-terminal
Installing myspell-en-za as dep of language-support-en
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libpoppler1 as dep of libpoppler1-glib
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libx86-1 as dep of vbetool
Installing python-orca-brlapi as dep of gnome-orca
Installing libgail-gnome-module as dep of gnome-orca
Installing libxml-twig-perl as dep of libnet-dbus-perl
Installing gnome-mount as dep of gnome-volume-manager
Installing libgdiplus as dep of libmono-system1.0-cil
Installing libdvdnav4 as dep of vlc-nox
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing python-gtk2 as dep of python-glade2
Installing gstreamer0.10-esd as dep of gstreamer0.10-plugins-good-dbg
Installing libgii1-target-x as dep of libgii1
Installing python-bittorrent as dep of bittorrent
Installing stellarium-data as dep of stellarium
Installing language-selector-common as dep of language-selector
Installing openoffice.org-filter-mobiledev as dep of openoffice.org
Installing cupsys as dep of cupsys-driver-gutenprint
Installing libjaxp1.3-java as dep of libxerces2-java
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing software-properties-gtk as dep of gnome-app-install
Installing python-software-properties as dep of software-properties-gtk
Installing debconf as dep of tasksel
Installing gimp-data as dep of gimp
Installing mscompress as dep of foo2zjs
Installing libgda2-common as dep of libgda2-3
Installing liboobs-1-3 as dep of gnome-applets
Installing gnome-applets-data as dep of gnome-applets
Installing linux-restricted-modules-2.6.20-15-generic as dep of linux-restricted-modules-generic
Installing libusplash0 as dep of usplash
Installing gpgv as dep of gnupg
Starting
Starting 2
WARNING: Failed to read mirror file
Investigating libvolume-id0
Package libvolume-id0 has broken dep on libvolumeid0
  Considering libvolumeid0 4 as a solution to libvolume-id0 20
  Added libvolumeid0 to the remove list
  Fixing libvolume-id0 via remove of libvolumeid0
Investigating ntp
Package ntp has broken dep on ntp-server
  Considering ntp-server 0 as a solution to ntp 3
  Added ntp-server to the remove list
  Fixing ntp via remove of ntp-server
Investigating human-theme
Package human-theme has broken dep on human-gtk-theme
  Considering human-gtk-theme 0 as a solution to human-theme 2
  Added human-gtk-theme to the remove list
  Fixing human-theme via remove of human-gtk-theme
Investigating python-apport
Package python-apport has broken dep on python-apport-utils
  Considering python-apport-utils 0 as a solution to python-apport 2
  Added python-apport-utils to the remove list
  Fixing python-apport via remove of python-apport-utils
Done
Installing linux-image-2.6.20-15-386 as dep of linux-image-386
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 2, in <module>
    import gobject, gtk, gtk.glade
ImportError: No module named gobject
Installing libmono0 as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-sharpzip2.84-cil as dep of f-spot
Installing libmono-system2.0-cil as dep of libmono-sharpzip2.84-cil
Installing libmono-security2.0-cil as dep of libmono-system2.0-cil
Installing libmono-sqlite2.0-cil as dep of f-spot
Installing libmono-system-data2.0-cil as dep of libmono-sqlite2.0-cil
Installing libmono-data-tds2.0-cil as dep of libmono-system-data2.0-cil
Installing libmono-system-web2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libndesk-dbus-glib1.0-cil as dep of f-spot
Installing libndesk-dbus1.0-cil as dep of libndesk-dbus-glib1.0-cil
Installing libgnomeprint2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing libgnomeprintui2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libqt3-mt as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libecal1.2-7 as dep of evolution-webcal
Installing libsoup2.2-8 as dep of evolution-webcal
Installing libopal-2.2.0 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2.0
Installing liblua50 as dep of kdelibs4c2a
Installing liblualib50 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing gnome-media-common as dep of gnome-media
Installing metacity-common as dep of metacity
Installing libbeagle0 as dep of nautilus
Installing libeel2-2 as dep of nautilus
Installing libeel2-data as dep of libeel2-2
Installing nautilus-data as dep of nautilus
Installing libgnome2-common as dep of libgnome2-0
Installing libdns22 as dep of bind9-host
Installing language-pack-en as dep of language-pack-en-base
Installing gnome-user-guide as dep of ubuntu-docs
Installing dhcp3-common as dep of dhcp3-client
Installing libgl1-mesa-dev as dep of nvidia-glx-dev
Installing mesa-common-dev as dep of libgl1-mesa-dev
Installing samba-common as dep of smbclient
new important dependency: command-not-found
Installing command-not-found as dep of ubuntu-standard
Installing command-not-found-data as dep of command-not-found
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
Installing libopenobex1 as dep of libbtctl4
Installing libavahi-core5 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing python-gnome2-desktop as dep of gnome-games
Installing wodim as dep of cdrecord
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt as dep of python-apt
Installing gksu as dep of gdebi
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgnome-pilot2 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing libnm-glib0 as dep of evolution
Installing evolution-common as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing gtkhtml3.14 as dep of evolution
Installing esound-common as dep of esound
Installing libportaudio2 as dep of audacity
Installing libsamplerate0 as dep of audacity
Installing libxcomposite1 as dep of gnome-mag
Installing libgpod1 as dep of rhythmbox
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing gnome-panel-data as dep of gnome-panel
Installing genisoimage as dep of dvd+rw-tools
Installing libpulse0 as dep of mplayer
Installing feisty-gdm-themes as dep of ubuntu-artwork
Installing feisty-session-splashes as dep of ubuntu-artwork
Installing feisty-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libslab0 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing avahi-autoipd as dep of ubuntu-desktop
Installing dcraw as dep of ubuntu-desktop
Installing desktop-effects as dep of ubuntu-desktop
Installing compiz as dep of desktop-effects
Installing compiz-core as dep of compiz
Installing compiz-plugins as dep of compiz
Installing libdecoration0 as dep of compiz-plugins
Installing compiz-gtk as dep of compiz
Installing compiz-gnome as dep of compiz
Installing gs-esp-x as dep of ubuntu-desktop
Installing gtk2-engines-pixbuf as dep of ubuntu-desktop
Installing libnss-mdns as dep of ubuntu-desktop
Installing openprinting-ppds as dep of ubuntu-desktop
new important dependency: espeak
Installing espeak as dep of ubuntu-desktop
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
new important dependency: network-manager-gnome
Installing network-manager-gnome as dep of ubuntu-desktop
Installing libnm-util0 as dep of network-manager-gnome
Installing network-manager as dep of network-manager-gnome
Installing libnl1-pre6 as dep of network-manager
Installing dhcdbd as dep of network-manager
new important dependency: restricted-manager
Installing restricted-manager as dep of ubuntu-desktop
Installing python-notify as dep of restricted-manager
new important dependency: scim-tables-additional
Installing scim-tables-additional as dep of ubuntu-desktop
Installing scim-modules-table as dep of scim-tables-additional
Installing pouetchess-data as dep of pouetchess
Installing cupsys-client as dep of cupsys-bsd
Installing update-inetd as dep of cupsys-bsd
Installing ntp as dep of ntp-simple
Installing python-apport as dep of apport
Installing python-problem-report as dep of python-apport
Installing python-launchpad-bugs as dep of python-apport
Installing gcc as dep of g++
Installing gnome-terminal-data as dep of gnome-terminal
Installing myspell-en-za as dep of language-support-en
Installing upstart as dep of upstart-compat-sysv
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libxml-twig-perl as dep of libnet-dbus-perl
Installing gnome-mount as dep of gnome-volume-manager
Installing libgdiplus as dep of libmono-system1.0-cil
Installing libdvdnav4 as dep of vlc-nox
Installing libgii1-target-x as dep of libgii1
Installing python-bittorrent as dep of bittorrent
Installing stellarium-data as dep of stellarium
Installing language-selector-common as dep of language-selector
Installing libjaxp1.3-java as dep of libxerces2-java
Installing libmagic1 as dep of file
Installing software-properties-gtk as dep of gnome-app-install
Installing python-software-properties as dep of software-properties-gtk
Installing gimp-data as dep of gimp
Installing mscompress as dep of foo2zjs
Installing libusplash0 as dep of usplash
Installing gpgv as dep of gnupg
Starting
Starting 2
Investigating python-apport
Package python-apport has broken dep on python-apport-utils
  Considering python-apport-utils 0 as a solution to python-apport 2
  Added python-apport-utils to the remove list
  Fixing python-apport via remove of python-apport-utils
Done
Installing libmono0 as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-sharpzip2.84-cil as dep of f-spot
Installing libmono-system2.0-cil as dep of libmono-sharpzip2.84-cil
Installing libmono-security2.0-cil as dep of libmono-system2.0-cil
Installing libmono-sqlite2.0-cil as dep of f-spot
Installing libmono-system-data2.0-cil as dep of libmono-sqlite2.0-cil
Installing libmono-data-tds2.0-cil as dep of libmono-system-data2.0-cil
Installing libmono-system-web2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libndesk-dbus-glib1.0-cil as dep of f-spot
Installing libndesk-dbus1.0-cil as dep of libndesk-dbus-glib1.0-cil
Installing libgnomeprint2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing libgnomeprintui2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libqt3-mt as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libecal1.2-7 as dep of evolution-webcal
Installing libsoup2.2-8 as dep of evolution-webcal
Installing libopal-2.2.0 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2.0
Installing liblua50 as dep of kdelibs4c2a
Installing liblualib50 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing gnome-media-common as dep of gnome-media
Installing metacity-common as dep of metacity
Installing libbeagle0 as dep of nautilus
Installing libeel2-2 as dep of nautilus
Installing libeel2-data as dep of libeel2-2
Installing nautilus-data as dep of nautilus
Installing libgnome2-common as dep of libgnome2-0
Installing libdns22 as dep of bind9-host
Installing language-pack-en as dep of language-pack-en-base
Installing gnome-user-guide as dep of ubuntu-docs
Installing dhcp3-common as dep of dhcp3-client
Installing libgl1-mesa-dev as dep of nvidia-glx-dev
Installing mesa-common-dev as dep of libgl1-mesa-dev
Installing samba-common as dep of smbclient
new important dependency: command-not-found
Installing command-not-found as dep of ubuntu-standard
Installing command-not-found-data as dep of command-not-found
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
Installing libopenobex1 as dep of libbtctl4
Installing libavahi-core5 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing python-gnome2-desktop as dep of gnome-games
Installing wodim as dep of cdrecord
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt as dep of python-apt
Installing gksu as dep of gdebi
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgnome-pilot2 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing libnm-glib0 as dep of evolution
Installing evolution-common as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing gtkhtml3.14 as dep of evolution
Installing esound-common as dep of esound
Installing libportaudio2 as dep of audacity
Installing libsamplerate0 as dep of audacity
Installing libxcomposite1 as dep of gnome-mag
Installing libgpod1 as dep of rhythmbox
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing gnome-panel-data as dep of gnome-panel
Installing genisoimage as dep of dvd+rw-tools
Installing libpulse0 as dep of mplayer
Installing feisty-gdm-themes as dep of ubuntu-artwork
Installing feisty-session-splashes as dep of ubuntu-artwork
Installing feisty-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libslab0 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing avahi-autoipd as dep of ubuntu-desktop
Installing dcraw as dep of ubuntu-desktop
Installing desktop-effects as dep of ubuntu-desktop
Installing compiz as dep of desktop-effects
Installing compiz-core as dep of compiz
Installing compiz-plugins as dep of compiz
Installing libdecoration0 as dep of compiz-plugins
Installing compiz-gtk as dep of compiz
Installing compiz-gnome as dep of compiz
Installing gs-esp-x as dep of ubuntu-desktop
Installing gtk2-engines-pixbuf as dep of ubuntu-desktop
Installing libnss-mdns as dep of ubuntu-desktop
Installing openprinting-ppds as dep of ubuntu-desktop
new important dependency: espeak
Installing espeak as dep of ubuntu-desktop
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
new important dependency: network-manager-gnome
Installing network-manager-gnome as dep of ubuntu-desktop
Installing libnm-util0 as dep of network-manager-gnome
Installing network-manager as dep of network-manager-gnome
Installing libnl1-pre6 as dep of network-manager
Installing dhcdbd as dep of network-manager
new important dependency: restricted-manager
Installing restricted-manager as dep of ubuntu-desktop
Installing python-notify as dep of restricted-manager
new important dependency: scim-tables-additional
Installing scim-tables-additional as dep of ubuntu-desktop
Installing scim-modules-table as dep of scim-tables-additional
Installing pouetchess-data as dep of pouetchess
Installing cupsys-client as dep of cupsys-bsd
Installing update-inetd as dep of cupsys-bsd
Installing ntp as dep of ntp-simple
Installing python-apport as dep of apport
Installing python-problem-report as dep of python-apport
Installing python-launchpad-bugs as dep of python-apport
Installing gcc as dep of g++
Installing gnome-terminal-data as dep of gnome-terminal
Installing myspell-en-za as dep of language-support-en
Installing upstart as dep of upstart-compat-sysv
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libxml-twig-perl as dep of libnet-dbus-perl
Installing gnome-mount as dep of gnome-volume-manager
Installing libgdiplus as dep of libmono-system1.0-cil
Installing libdvdnav4 as dep of vlc-nox
Installing libgii1-target-x as dep of libgii1
Installing python-bittorrent as dep of bittorrent
Installing stellarium-data as dep of stellarium
Installing language-selector-common as dep of language-selector
Installing libjaxp1.3-java as dep of libxerces2-java
Installing libmagic1 as dep of file
Installing software-properties-gtk as dep of gnome-app-install
Installing python-software-properties as dep of software-properties-gtk
Installing gimp-data as dep of gimp
Installing mscompress as dep of foo2zjs
Installing libusplash0 as dep of usplash
Installing gpgv as dep of gnupg
Starting
Starting 2
Investigating python-apport
Package python-apport has broken dep on python-apport-utils
  Considering python-apport-utils 0 as a solution to python-apport 2
  Added python-apport-utils to the remove list
  Fixing python-apport via remove of python-apport-utils
Done
ERROR:root:got an error from dpkg for pkg: '/var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb': 'subprocess pre-installation script returned error exit status 2
'
Traceback (most recent call last):
  File "/usr/share/apport/package_hook", line 15, in <module>
    import apport, apport.fileutils
ImportError: No module named apport
ERROR:root:SystemError from cache.commit(): installArchives() failed
Could not import module, is a package upgrade in progress? Error: No module named apport.ui

---

