---
title: "Upgrading with alternative cd problem"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by tranalbert on 2007-10-24
I'm upgrading to 7.10 using the alternative cd get this error everytime I try to upgrade:
[COLOR="Red"]
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.[/COLOR]

I've attached these files

The upgrader just exits after this. I also get this message when I try and update via internet connection. I have seen this thread:

[http://ubuntuforums.org/showthread.php?t=583990&highlight=An+unresolvable+problem+occurred+while+calculating+the+upgrade]("http://ubuntuforums.org/showthread.php?t=583990&highlight=An+unresolvable+problem+occurred+while+calculating+the+upgrade")

, however, it doesnt really provide a specific answer. Help would be greatly be appreciated! thanks

---

### Post by tranalbert on 2007-10-24
Here is the content of my apt.log:
> gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libnss3 as dep of gaim
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3471 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2443 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 638 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 372 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1802 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1898 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1402 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1156 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 877 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1740 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 1 as a solution to firefox 11
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 747 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1049 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 982 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 995 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1019 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 996 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 1008 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1008 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1393 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 843 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 689 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 838 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 397 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 518 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 443 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 267 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 259 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 163 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 126 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 290 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 345 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 214 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 430 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 900 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 870 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libnss3 as dep of gaim
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3471 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2443 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 638 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 372 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1802 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1898 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1402 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1156 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 877 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1740 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 1 as a solution to firefox 11
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 747 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1049 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 982 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 995 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1019 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 996 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 1008 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1008 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1393 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 843 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 689 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 838 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 397 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 518 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 443 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 267 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 259 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 163 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 126 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 290 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 345 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 214 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 430 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 900 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 870 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libnss3 as dep of gaim
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3471 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2443 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 638 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 372 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1802 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1898 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1402 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1156 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 877 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1740 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 1 as a solution to firefox 11
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 747 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1049 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 982 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 995 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1019 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 996 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 1008 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1008 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1393 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 843 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 689 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 838 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 397 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 518 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 443 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 267 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 259 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 163 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 126 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 290 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 345 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 214 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 430 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 900 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 870 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3450 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2437 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 635 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 371 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1798 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1880 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1385 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1152 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 875 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1731 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 743 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1045 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 978 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 984 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1018 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 985 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 997 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1005 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1388 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 840 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 687 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 835 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 394 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 517 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 441 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 266 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 257 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 164 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 125 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 288 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 343 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 213 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 429 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 889 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 859 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3450 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2437 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 635 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 371 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1798 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1880 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1385 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1152 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 875 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1731 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 743 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1045 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 978 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 984 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1018 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 985 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 997 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1005 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1388 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 840 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 687 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 835 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 394 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 517 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 441 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 266 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 257 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 164 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 125 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 288 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 343 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 213 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 429 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 889 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 859 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3450 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2437 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 635 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 371 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1798 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1880 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1385 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1152 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 875 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1731 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 743 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1045 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 978 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 984 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1018 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 985 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 997 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1005 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1388 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 840 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 687 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 835 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 394 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 517 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 441 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 266 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 257 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 164 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 125 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 288 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 343 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 213 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 429 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 889 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 859 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3450 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2437 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 635 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 371 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1798 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1880 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1385 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1152 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 875 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1731 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 743 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1045 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 978 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 984 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1018 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 985 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 997 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1005 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1388 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 840 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 687 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 835 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 394 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 517 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 441 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 266 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 257 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 164 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 125 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 288 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 343 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 213 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 429 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 889 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 859 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3450 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2437 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 635 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 371 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1798 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1880 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1385 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1152 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 875 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1731 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 743 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1045 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 978 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 984 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1018 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 985 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 997 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1005 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1388 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 840 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 687 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 835 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 394 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 517 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 441 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 266 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 257 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 164 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 125 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 288 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 343 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 213 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 429 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 889 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 859 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3450 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2437 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 635 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 371 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1798 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1880 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1385 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1152 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 875 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1731 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 743 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1045 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 978 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 984 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1018 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 985 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 997 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1005 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1388 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 840 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 687 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 835 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 394 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 517 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 441 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 266 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 257 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 164 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 125 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 288 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 343 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 213 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 429 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 889 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 859 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done
ERROR:root:Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
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
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
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
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing fuse-utils as dep of ntfs-3g
Installing libfuse2 as dep of fuse-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
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
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libsqlite3-0 as dep of librpm4
Installing cupsys-client as dep of cupsys-bsd
Installing libcupsimage2 as dep of cupsys-client
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpoppler-glib2 as dep of evince
Installing libpoppler2 as dep of libpoppler-glib2
Installing ghostscript-x as dep of evince
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing openoffice.org-core as dep of openoffice.org-base
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 108
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 3450 as a solution to libx11-dev 42
  Removing libx11-dev rather than change libx11-6
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2437 as a solution to libglib2.0-dev 38
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 635 as a solution to libxau-dev 17
  Removing libxau-dev rather than change libxau6
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 371 as a solution to libxdmcp-dev 15
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 1798 as a solution to zlib1g-dev 15
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 1880 as a solution to libxext-dev 13
  Removing libxext-dev rather than change libxext6
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1385 as a solution to libxfixes-dev 13
  Removing libxfixes-dev rather than change libxfixes3
Investigating libcairo2-dev
Package libcairo2-dev has broken dep on libcairo2
  Considering libcairo2 1152 as a solution to libcairo2-dev 12
  Removing libcairo2-dev rather than change libcairo2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 875 as a solution to libgtk2.0-dev 12
  Removing libgtk2.0-dev rather than change libgtk2.0-0
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 1731 as a solution to libxrender-dev 11
  Removing libxrender-dev rather than change libxrender1
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 743 as a solution to libfreetype6-dev 11
  Removing libfreetype6-dev rather than change libfreetype6
Investigating libpango1.0-dev
Package libpango1.0-dev has broken dep on libpango1.0-0
  Considering libpango1.0-0 1045 as a solution to libpango1.0-dev 10
  Removing libpango1.0-dev rather than change libpango1.0-0
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 10
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 10
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating libatk1.0-dev
Package libatk1.0-dev has broken dep on libatk1.0-0
  Considering libatk1.0-0 978 as a solution to libatk1.0-dev 9
  Removing libatk1.0-dev rather than change libatk1.0-0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 984 as a solution to libxcursor-dev 9
  Removing libxcursor-dev rather than change libxcursor1
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1018 as a solution to libxml2-dev 9
  Removing libxml2-dev rather than change libxml2
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin 9
  Added gaim to the remove list
  Fixing pidgin via remove of gaim
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 17 as a solution to x11proto-xext-dev 8
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 985 as a solution to libxi-dev 7
  Removing libxi-dev rather than change libxi6
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 997 as a solution to libxrandr-dev 7
  Removing libxrandr-dev rather than change libxrandr2
Investigating libgconf2-dev
Package libgconf2-dev has broken dep on libgconf2-4
  Considering libgconf2-4 691 as a solution to libgconf2-dev 7
  Removing libgconf2-dev rather than change libgconf2-4
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libxinerama1
  Considering libxinerama1 1005 as a solution to libxinerama-dev 7
  Removing libxinerama-dev rather than change libxinerama1
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1388 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 6
  Removing libwnck18 rather than change libwnck-common
Investigating liborbit2-dev
Package liborbit2-dev has broken dep on liborbit2
  Considering liborbit2 840 as a solution to liborbit2-dev 5
  Removing liborbit2-dev rather than change liborbit2
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 411 as a solution to libdbus-1-dev 5
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 8 as a solution to x11proto-fixes-dev 5
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 687 as a solution to libsm-dev 4
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 835 as a solution to libice-dev 4
  Removing libice-dev rather than change libice6
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 6 as a solution to emerald 4
  Removing emerald rather than change libwnck18
Investigating libstartup-notification0-dev
Package libstartup-notification0-dev has broken dep on libx11-dev
  Considering libx11-dev 42 as a solution to libstartup-notification0-dev 3
  Removing libstartup-notification0-dev rather than change libx11-dev
Investigating libart-2.0-dev
Package libart-2.0-dev has broken dep on libart-2.0-2
  Considering libart-2.0-2 394 as a solution to libart-2.0-dev 3
  Removing libart-2.0-dev rather than change libart-2.0-2
Investigating libgnomevfs2-dev
Package libgnomevfs2-dev has broken dep on libgnomevfs2-0
  Considering libgnomevfs2-0 457 as a solution to libgnomevfs2-dev 3
  Removing libgnomevfs2-dev rather than change libgnomevfs2-0
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 110 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating libpng12-dev
Package libpng12-dev has broken dep on libpng12-0
  Considering libpng12-0 517 as a solution to libpng12-dev 2
  Removing libpng12-dev rather than change libpng12-0
Investigating libbonobo2-dev
Package libbonobo2-dev has broken dep on libbonobo2-0
  Considering libbonobo2-0 441 as a solution to libbonobo2-dev 2
  Removing libbonobo2-dev rather than change libbonobo2-0
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 404 as a solution to libgnutls-dev 2
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 266 as a solution to libexpat1-dev 2
  Removing libexpat1-dev rather than change libexpat1
Investigating libselinux1-dev
Package libselinux1-dev has broken dep on libselinux1
  Considering libselinux1 641 as a solution to libselinux1-dev 2
  Removing libselinux1-dev rather than change libselinux1
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 257 as a solution to libxft-dev 2
  Removing libxft-dev rather than change libxft2
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libavahi-glib-dev
Package libavahi-glib-dev has broken dep on libavahi-glib1
  Considering libavahi-glib1 93 as a solution to libavahi-glib-dev 2
  Removing libavahi-glib-dev rather than change libavahi-glib1
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 4 as a solution to beryl 2
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 2
  Or group remove for beryl
Investigating python-gtk2-dev
Package python-gtk2-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 38 as a solution to python-gtk2-dev 1
  Removing python-gtk2-dev rather than change libglib2.0-dev
Investigating libgnomeui-dev
Package libgnomeui-dev has broken dep on libgnomeui-0
  Considering libgnomeui-0 164 as a solution to libgnomeui-dev 1
  Removing libgnomeui-dev rather than change libgnomeui-0
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 69 as a solution to libgpg-error-dev 1
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 80 as a solution to libgcrypt11-dev 1
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating smbfs
Package smbfs has broken dep on samba-common
  Considering samba-common 6 as a solution to smbfs 1
  Removing smbfs rather than change samba-common
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 160 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating x11proto-composite-dev
Package x11proto-composite-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-composite-dev 1
  Removing x11proto-composite-dev rather than change x11proto-fixes-dev
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 2 as a solution to beryl-manager 1
  Removing beryl-manager rather than change beryl
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating x11proto-damage-dev
Package x11proto-damage-dev has broken dep on x11proto-fixes-dev
  Considering x11proto-fixes-dev 5 as a solution to x11proto-damage-dev 1
  Removing x11proto-damage-dev rather than change x11proto-fixes-dev
Investigating libidl-dev
Package libidl-dev has broken dep on libidl0
  Considering libidl0 125 as a solution to libidl-dev 1
  Removing libidl-dev rather than change libidl0
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 116 as a solution to libesd0-dev 1
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Investigating libgnomecanvas2-dev
Package libgnomecanvas2-dev has broken dep on libgnomecanvas2-0
  Considering libgnomecanvas2-0 288 as a solution to libgnomecanvas2-dev 1
  Removing libgnomecanvas2-dev rather than change libgnomecanvas2-0
Investigating libcroco3-dev
Package libcroco3-dev has broken dep on libcroco3
  Considering libcroco3 15 as a solution to libcroco3-dev 1
  Removing libcroco3-dev rather than change libcroco3
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating libgsf-1-dev
Package libgsf-1-dev has broken dep on libgsf-1-114
  Considering libgsf-1-114 15 as a solution to libgsf-1-dev 1
  Removing libgsf-1-dev rather than change libgsf-1-114
Investigating libxres-dev
Package libxres-dev has broken dep on libxres1
  Considering libxres1 11 as a solution to libxres-dev 1
  Removing libxres-dev rather than change libxres1
Investigating libgnome2-dev
Package libgnome2-dev has broken dep on libgnome2-0
  Considering libgnome2-0 333 as a solution to libgnome2-dev 1
  Removing libgnome2-dev rather than change libgnome2-0
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 133 as a solution to libavahi-common-dev 1
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libawn-bzr
Package libawn-bzr has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libawn-bzr 1
  Removing libawn-bzr rather than change libwnck18
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 1 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 43 as a solution to libtasn1-3-dev 0
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 39 as a solution to libopencdk8-dev 0
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating libglade2-dev
Package libglade2-dev has broken dep on libglade2-0
  Considering libglade2-0 343 as a solution to libglade2-dev 0
  Removing libglade2-dev rather than change libglade2-0
Investigating libgnome-keyring-dev
Package libgnome-keyring-dev has broken dep on libgnome-keyring0
  Considering libgnome-keyring0 133 as a solution to libgnome-keyring-dev 0
  Removing libgnome-keyring-dev rather than change libgnome-keyring0
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 0
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating libbonoboui2-dev
Package libbonoboui2-dev has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 213 as a solution to libbonoboui2-dev 0
  Removing libbonoboui2-dev rather than change libbonoboui2-0
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 0
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating libjpeg62-dev
Package libjpeg62-dev has broken dep on libjpeg62
  Considering libjpeg62 429 as a solution to libjpeg62-dev 0
  Removing libjpeg62-dev rather than change libjpeg62
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
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
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem 0
  Holding Back totem rather than change totem-gstreamer
Package totem has broken dep on totem-xine
  Or group keep for totem
Investigating libsepol1-dev
Package libsepol1-dev has broken dep on libsepol1
  Considering libsepol1 179 as a solution to libsepol1-dev 0
  Removing libsepol1-dev rather than change libsepol1
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 72 as a solution to libbz2-dev 0
  Removing libbz2-dev rather than change libbz2-1.0
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 4 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating smb4k
Package smb4k has broken dep on smbfs
  Considering smbfs 1 as a solution to smb4k -1
  Removing smb4k rather than change smbfs
Investigating libgnome-desktop-dev
Package libgnome-desktop-dev has broken dep on libgnome-desktop-2
  Considering libgnome-desktop-2 39 as a solution to libgnome-desktop-dev -1
  Removing libgnome-desktop-dev rather than change libgnome-desktop-2
Investigating libgtop2-dev
Package libgtop2-dev has broken dep on libgtop2-7
  Considering libgtop2-7 16 as a solution to libgtop2-dev -1
  Removing libgtop2-dev rather than change libgtop2-7
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 572 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating libwnck-dev
Package libwnck-dev has broken dep on libwnck18
  Considering libwnck18 6 as a solution to libwnck-dev -1
  Removing libwnck-dev rather than change libwnck18
Investigating libawn-bzr-dev
Package libawn-bzr-dev has broken dep on libawn-bzr
  Considering libawn-bzr 1 as a solution to libawn-bzr-dev -1
  Removing libawn-bzr-dev rather than change libawn-bzr
Investigating libgnome-menu-dev
Package libgnome-menu-dev has broken dep on libgnome-menu2
  Considering libgnome-menu2 29 as a solution to libgnome-menu-dev -1
  Removing libgnome-menu-dev rather than change libgnome-menu2
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 118 as a solution to libssl-dev -1
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxdamage-dev
Package libxdamage-dev has broken dep on libxdamage1
  Considering libxdamage1 889 as a solution to libxdamage-dev -1
  Removing libxdamage-dev rather than change libxdamage1
Investigating libdbus-glib-1-dev
Package libdbus-glib-1-dev has broken dep on libdbus-glib-1-2
  Considering libdbus-glib-1-2 211 as a solution to libdbus-glib-1-dev -1
  Removing libdbus-glib-1-dev rather than change libdbus-glib-1-2
Investigating libsexy-dev
Package libsexy-dev has broken dep on libsexy2
  Considering libsexy2 7 as a solution to libsexy-dev -1
  Removing libsexy-dev rather than change libsexy2
Investigating libxcomposite-dev
Package libxcomposite-dev has broken dep on libxcomposite1
  Considering libxcomposite1 859 as a solution to libxcomposite-dev -1
  Removing libxcomposite-dev rather than change libxcomposite1
Investigating screenlets
Package screenlets has broken dep on xcompmgr
Package screenlets has broken dep on compiz
  Considering compiz 1 as a solution to screenlets -1
Package screenlets has broken dep on beryl
  Considering beryl 2 as a solution to screenlets -1
  Or group remove for screenlets
Investigating python-gnome2-desktop-dev
Package python-gnome2-desktop-dev has broken dep on python-gtk2-dev
  Considering python-gtk2-dev 1 as a solution to python-gnome2-desktop-dev -1
  Removing python-gnome2-desktop-dev rather than change python-gtk2-dev
Investigating librsvg2-dev
Package librsvg2-dev has broken dep on librsvg2-2
  Considering librsvg2-2 35 as a solution to librsvg2-dev -1
  Removing librsvg2-dev rather than change librsvg2-2
Investigating libxss-dev
Package libxss-dev has broken dep on libxss1
  Considering libxss1 22 as a solution to libxss-dev -1
  Removing libxss-dev rather than change libxss1
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 9
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 9
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to openoffice.org-help-zh-cn 8
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to openoffice.org-help-zh-tw 8
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 5
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 5
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to openoffice.org-help-ja 4
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to openoffice.org-help-ko 4
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
 Try to Re-Instate rhythmbox
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 0
  Removing libwrap0-dev rather than change libwrap0
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 8 as a solution to language-support-zh 12
  Added openoffice.org-help-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-cn to the remove list
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 9 as a solution to language-support-zh 12
  Added openoffice.org-l10n-zh-tw to the remove list
  Fixing language-support-zh via keep of openoffice.org-help-zh-cn
  Fixing language-support-zh via keep of openoffice.org-help-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-cn
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
  Fixing language-support-zh via keep of openoffice.org-l10n-zh-tw
Investigating openoffice.org-l10n-zh-cn
Package openoffice.org-l10n-zh-cn has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-cn 12
  Removing openoffice.org-l10n-zh-cn rather than change openoffice.org-core
Investigating openoffice.org-l10n-zh-tw
Package openoffice.org-l10n-zh-tw has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-zh-tw 12
  Removing openoffice.org-l10n-zh-tw rather than change openoffice.org-core
Investigating openoffice.org-help-zh-cn
Package openoffice.org-help-zh-cn has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to openoffice.org-help-zh-cn 12
  Removing openoffice.org-help-zh-cn rather than change openoffice.org-l10n-zh-cn
Investigating openoffice.org-help-zh-tw
Package openoffice.org-help-zh-tw has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to openoffice.org-help-zh-tw 12
  Removing openoffice.org-help-zh-tw rather than change openoffice.org-l10n-zh-tw
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 4 as a solution to language-support-ja 6
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 5 as a solution to language-support-ja 6
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 4 as a solution to language-support-ko 6
  Added openoffice.org-help-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-help-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 5 as a solution to language-support-ko 6
  Added openoffice.org-l10n-ko to the remove list
  Fixing language-support-ko via keep of openoffice.org-help-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
  Fixing language-support-ko via keep of openoffice.org-l10n-ko
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ja 6
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating openoffice.org-l10n-ko
Package openoffice.org-l10n-ko has broken dep on openoffice.org-core
  Considering openoffice.org-core 51 as a solution to openoffice.org-l10n-ko 6
  Removing openoffice.org-l10n-ko rather than change openoffice.org-core
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to openoffice.org-help-ja 6
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating openoffice.org-help-ko
Package openoffice.org-help-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to openoffice.org-help-ko 6
  Removing openoffice.org-help-ko rather than change openoffice.org-l10n-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 0 as a solution to liborbit-dev 1
  Added libwrap0-dev to the remove list
  Fixing liborbit-dev via keep of libwrap0-dev
Investigating libwrap0-dev
Package libwrap0-dev has broken dep on libwrap0
  Considering libwrap0 39 as a solution to libwrap0-dev 1
  Removing libwrap0-dev rather than change libwrap0
Investigating language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-cn
  Considering openoffice.org-help-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-cn
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-help-zh-tw
  Considering openoffice.org-help-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-help-zh-tw
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-cn
  Considering openoffice.org-l10n-zh-cn 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Package language-support-zh has broken dep on openoffice.org-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
Package language-support-zh has broken dep on openoffice.org2-l10n-zh-tw
  Considering openoffice.org-l10n-zh-tw 51 as a solution to language-support-zh 12
  Or group remove for language-support-zh
Investigating thunderbird-locale-zh-cn
Package thunderbird-locale-zh-cn has broken dep on mozilla-thunderbird
Package thunderbird-locale-zh-cn has broken dep on language-support-zh
  Considering language-support-zh 12 as a solution to thunderbird-locale-zh-cn 8
  Or group remove for thunderbird-locale-zh-cn
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-help-ja
  Or group remove for language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 51 as a solution to language-support-ja 6
  Or group remove for language-support-ja
Investigating language-support-ko
Package language-support-ko has broken dep on openoffice.org-help-ko
  Considering openoffice.org-help-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-help-ko
  Or group remove for language-support-ko
Package language-support-ko has broken dep on openoffice.org-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
Package language-support-ko has broken dep on openoffice.org2-l10n-ko
  Considering openoffice.org-l10n-ko 51 as a solution to language-support-ko 6
  Or group remove for language-support-ko
Investigating thunderbird-locale-ja
Package thunderbird-locale-ja has broken dep on mozilla-thunderbird
Package thunderbird-locale-ja has broken dep on language-support-ja
  Considering language-support-ja 6 as a solution to thunderbird-locale-ja 4
  Or group remove for thunderbird-locale-ja
Investigating thunderbird-locale-ko
Package thunderbird-locale-ko has broken dep on mozilla-thunderbird
Package thunderbird-locale-ko has broken dep on language-support-ko
  Considering language-support-ko 6 as a solution to thunderbird-locale-ko 4
  Or group remove for thunderbird-locale-ko
Investigating liborbit-dev
Package liborbit-dev has broken dep on libwrap0-dev
  Considering libwrap0-dev 39 as a solution to liborbit-dev 1
  Removing liborbit-dev rather than change libwrap0-dev
Investigating liboaf-dev
Package liboaf-dev has broken dep on liborbit-dev
  Considering liborbit-dev 39 as a solution to liboaf-dev 2
  Removing liboaf-dev rather than change liborbit-dev
Investigating libgconf-dev
Package libgconf-dev has broken dep on liboaf-dev
  Considering liboaf-dev 39 as a solution to libgconf-dev 1
  Removing libgconf-dev rather than change liboaf-dev
Investigating libgnome-vfs-dev
Package libgnome-vfs-dev has broken dep on libgconf-dev
  Considering libgconf-dev 39 as a solution to libgnome-vfs-dev -1
  Removing libgnome-vfs-dev rather than change libgconf-dev
Done
Starting
Starting 2
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-help-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on thunderbird-locale-ja
  Considering thunderbird-locale-ja 1 as a solution to language-support-ja 10000
  Added thunderbird-locale-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-help-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of thunderbird-locale-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 1
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 1 as a solution to language-support-ja 10000
  Added openoffice.org-l10n-ja to the remove list
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
  Fixing language-support-ja via keep of openoffice.org-l10n-ja
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-ja 10000
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-ja via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-evolution 0
  Holding Back openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-evolution
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org
Investigating openoffice.org-l10n-ja
Package openoffice.org-l10n-ja has broken dep on openoffice.org-core
  Considering openoffice.org-core 10000 as a solution to openoffice.org-l10n-ja 10000
  Removing openoffice.org-l10n-ja rather than change openoffice.org-core
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done

---

