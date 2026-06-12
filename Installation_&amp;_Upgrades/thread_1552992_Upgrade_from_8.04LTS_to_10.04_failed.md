---
title: "Upgrade from 8.04LTS to 10.04 failed"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by teanick on 2010-08-14
In using update manager to go from 8.04LTS to 10.04 LTS, I received the following error message.

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:

The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist.

 This can be caused by:

 * Upgrading to a pre-release version of Ubuntu

 * Running the current pre-release version of Ubuntu

 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.&#148;

The log contents are as follows:

Log time: 2010-08-08 10:27:55.962371
Log time: 2010-08-08 10:27:58.160105
Log time: 2010-08-08 10:28:21.481186
Installing xserver-xorg-core as dep of xserver-xorg
Installing xserver-common as dep of xserver-xorg-core
Installing udev as dep of xserver-xorg-core
Installing libc6 as dep of udev
Installing libc-bin as dep of libc6
Installing findutils as dep of libc6
Installing upstart as dep of udev
Installing libdbus-1-3 as dep of upstart
Installing libnih-dbus1 as dep of upstart
Installing libnih1 as dep of libnih-dbus1
Installing libudev0 as dep of upstart
Installing sysvinit-utils as dep of upstart
Installing mountall as dep of upstart
Installing plymouth as dep of mountall
Installing libdrm-intel1 as dep of plymouth
Installing libdrm2 as dep of libdrm-intel1
Installing libdrm-nouveau1 as dep of plymouth
Installing libdrm-radeon1 as dep of plymouth
Installing libplymouth2 as dep of plymouth
Installing plymouth-theme-ubuntu-text as dep of plymouth
Installing libatk1.0-0 as dep of gdm
Installing libcanberra-gtk0 as dep of gdm
Installing libcanberra0 as dep of libcanberra-gtk0
Installing libasound2 as dep of libcanberra0
Installing libpython2.6 as dep of libasound2
Installing python2.6 as dep of libpython2.6
Installing python2.6-minimal as dep of python2.6
Installing libssl0.9.8 as dep of python2.6-minimal
Installing libdb4.8 as dep of python2.6
Installing libreadline6 as dep of python2.6
Installing libsqlite3-0 as dep of python2.6
Installing libltdl7 as dep of libcanberra0
Installing libtdb1 as dep of libcanberra0
Installing libgtk2.0-0 as dep of libcanberra-gtk0
Installing libcairo2 as dep of libgtk2.0-0
Installing libdirectfb-1.2-0 as dep of libcairo2
Installing libts-0.0-0 as dep of libdirectfb-1.2-0
Installing tsconf as dep of libts-0.0-0
Installing libfontconfig1 as dep of libcairo2
Installing fontconfig-config as dep of libfontconfig1
Installing libpixman-1-0 as dep of libcairo2
Installing libxcb-render-util0 as dep of libcairo2
Installing libxcb-render0 as dep of libxcb-render-util0
Installing libcups2 as dep of libgtk2.0-0
Installing libgnutls26 as dep of libcups2
Installing libgcrypt11 as dep of libgnutls26
Installing libgpg-error0 as dep of libgcrypt11
Installing libtasn1-3 as dep of libgnutls26
Installing libgssapi-krb5-2 as dep of libcups2
Installing libk5crypto3 as dep of libgssapi-krb5-2
Installing libkrb5support0 as dep of libk5crypto3
Installing libkrb5-3 as dep of libgssapi-krb5-2
Installing libglib2.0-0 as dep of libgtk2.0-0
Installing libpcre3 as dep of libglib2.0-0
Installing libxrandr2 as dep of libgtk2.0-0
Installing libcanberra-gtk-module as dep of libcanberra-gtk0
Installing libdbus-glib-1-2 as dep of gdm
Installing libdevkit-power-gobject1 as dep of gdm
Installing libgconf2-4 as dep of gdm
Installing libxml2 as dep of libgconf2-4
Installing gconf2-common as dep of libgconf2-4
Installing libpolkit-gobject-1-0 as dep of gdm
Installing libeggdbus-1-0 as dep of libpolkit-gobject-1-0
Installing libpopt0 as dep of gdm
Installing libxklavier16 as dep of gdm
Installing gnome-session-bin as dep of gdm
Installing policykit-1-gnome as dep of gnome-session-bin
Installing libappindicator0 as dep of policykit-1-gnome
Installing libdbusmenu-glib1 as dep of libappindicator0
Installing libdbusmenu-gtk1 as dep of libappindicator0
Installing libindicator0 as dep of libappindicator0
Installing libjson-glib-1.0-0 as dep of libappindicator0
Installing indicator-application as dep of libappindicator0
Installing libpolkit-agent-1-0 as dep of policykit-1-gnome
Installing policykit-1 as dep of policykit-1-gnome
Installing libpolkit-backend-1-0 as dep of policykit-1
Installing gnome-settings-daemon as dep of gnome-session
Installing libgnome-desktop-2-17 as dep of gnome-settings-daemon
Installing libstartup-notification0 as dep of libgnome-desktop-2-17
Installing libxcb-atom1 as dep of libstartup-notification0
Installing libxcb-aux0 as dep of libstartup-notification0
Installing libxcb-event1 as dep of libstartup-notification0
Installing libebook1.2-9 as dep of gnome-control-center
Installing libcamel1.2-14 as dep of libebook1.2-9
Installing libedataserver1.2-11 as dep of libcamel1.2-14
Installing libbluetooth3 as dep of evolution
Installing libebackend1.2-0 as dep of evolution
Installing libecal1.2-7 as dep of evolution
Installing libical0 as dep of libecal1.2-7
Installing libedataserverui1.2-8 as dep of evolution
Installing evolution-data-server-common as dep of libedataserverui1.2-8
Installing libegroupwise1.2-13 as dep of evolution
Installing libenchant1c2a as dep of evolution
Installing libhunspell-1.2-0 as dep of libenchant1c2a
Installing hunspell-en-us as dep of libhunspell-1.2-0
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgdata-google1.2-1 as dep of evolution
Installing libgdata1.2-1 as dep of libgdata-google1.2-1
Installing libgtkhtml-editor0 as dep of evolution
Installing libgtkhtml3.14-19 as dep of libgtkhtml-editor0
Installing libgtkhtml-editor-common as dep of libgtkhtml-editor0
Installing libgweather1 as dep of evolution
Installing libsoup-gnome2.4-1 as dep of libgweather1
Installing libproxy0 as dep of libsoup-gnome2.4-1
Installing libsoup2.4-1 as dep of libsoup-gnome2.4-1
Installing libgweather-common as dep of libgweather1
Installing libnotify1 as dep of evolution
Installing evolution-common as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing libgnome-menu2 as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libgnomekbd4 as dep of gnome-control-center
Installing libpango1.0-0 as dep of libgnomekbd4
Installing libpango1.0-common as dep of libpango1.0-0
Installing libthai0 as dep of libpango1.0-0
Installing libdatrie1 as dep of libthai0
Installing libthai-data as dep of libthai0
Installing libgnomekbd-common as dep of libgnomekbd4
Installing libmetacity-private0 as dep of gnome-control-center
Installing metacity-common as dep of libmetacity-private0
Installing librsvg2-2 as dep of gnome-control-center
Installing libcroco3 as dep of librsvg2-2
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libunique-1.0-0 as dep of gnome-control-center
Installing libxi6 as dep of gnome-control-center
Installing libx11-6 as dep of libxi6
Installing libxcb1 as dep of libx11-6
Installing capplets-data as dep of gnome-control-center
Installing gnome-icon-theme as dep of gnome-control-center
Installing ubuntu-system-service as dep of gnome-control-center
Installing python-central as dep of ubuntu-system-service
new important dependency: screen-resolution-extra
Installing screen-resolution-extra as dep of gnome-control-center
Installing python as dep of screen-resolution-extra
Installing python-minimal as dep of python
Installing python-xkit as dep of screen-resolution-extra
Installing libpulse-mainloop-glib0 as dep of gnome-settings-daemon
Installing libpulse0 as dep of libpulse-mainloop-glib0
Installing libsndfile1 as dep of libpulse0
Installing coreutils as dep of mountall
Installing ifupdown as dep of upstart
Installing netbase as dep of ifupdown
Installing initramfs-tools as dep of udev
Installing initramfs-tools-bin as dep of initramfs-tools
Installing klibc-utils as dep of initramfs-tools
Installing libklibc as dep of klibc-utils
Installing busybox-initramfs as dep of initramfs-tools
Installing util-linux as dep of initramfs-tools
Installing dpkg as dep of util-linux
Installing kdebase-runtime as dep of konqueror
Installing kdelibs5 as dep of kdebase-runtime
Installing libattica0 as dep of kdelibs5
Installing libqt4-network as dep of libattica0
Installing libqtcore4 as dep of libqt4-network
Installing libdbusmenu-qt2 as dep of kdelibs5
Installing libqt4-dbus as dep of libdbusmenu-qt2
Installing libqt4-xml as dep of libqt4-dbus
Installing libqtgui4 as dep of libdbusmenu-qt2
Installing libilmbase6 as dep of kdelibs5
Installing liblzma1 as dep of kdelibs5
Installing libopenexr6 as dep of kdelibs5
Installing libphonon4 as dep of kdelibs5
Installing libqt4-designer as dep of libphonon4
Installing libqt4-script as dep of libqt4-designer
Installing libpolkit-qt-1-0 as dep of kdelibs5
Installing libqt4-qt3support as dep of kdelibs5
Installing libqt4-sql as dep of libqt4-qt3support
Installing libqt4-svg as dep of kdelibs5
Installing libqt4-webkit as dep of kdelibs5
Installing libqt4-xmlpatterns as dep of libqt4-webkit
Installing libsoprano4 as dep of kdelibs5
Installing libclucene0ldbl as dep of libsoprano4
Installing soprano-daemon as dep of libsoprano4
Installing libiodbc2 as dep of soprano-daemon
Installing libraptor1 as dep of soprano-daemon
Installing librdf0 as dep of soprano-daemon
Installing librasqal2 as dep of librdf0
Installing virtuoso-nepomuk as dep of soprano-daemon
Installing libstdc++6 as dep of kdelibs5
Installing gcc-4.4-base as dep of libstdc++6
Installing libstreamanalyzer0 as dep of kdelibs5
Installing libexiv2-6 as dep of libstreamanalyzer0
Installing exiv2 as dep of libexiv2-6
Installing libstreams0 as dep of libstreamanalyzer0
Installing kdelibs5-data as dep of kdelibs5
Installing kdelibs-bin as dep of kdelibs5
Installing shared-desktop-ontologies as dep of kdelibs5
Installing libplasma3 as dep of kdebase-runtime
Installing libqca2 as dep of libplasma3
Installing libqt4-opengl as dep of libplasma3
Installing libsmbclient as dep of kdebase-runtime
Installing libcap2 as dep of libsmbclient
Installing libtalloc2 as dep of libsmbclient
Installing libwbclient0 as dep of libsmbclient
Installing libssh-4 as dep of kdebase-runtime
Installing kdebase-runtime-data as dep of kdebase-runtime
Installing oxygen-icon-theme as dep of kdebase-runtime
Installing phonon-backend-xine as dep of kdebase-runtime
Installing plasma-scriptengine-javascript as dep of kdebase-runtime
new important dependency: icoutils
Installing icoutils as dep of kdebase-runtime
new important dependency: kubuntu-debug-installer
Installing kubuntu-debug-installer as dep of kdebase-runtime
Installing kpackagekit as dep of kubuntu-debug-installer
Installing libpackagekit-qt-12 as dep of kpackagekit
Installing apt as dep of libpackagekit-qt-12
Installing polkit-kde-1 as dep of kpackagekit
Installing software-properties-kde as dep of kpackagekit
Installing python-qt4 as dep of software-properties-kde
Installing libqt4-assistant as dep of python-qt4
Installing libqt4-help as dep of python-qt4
Installing libqt4-scripttools as dep of python-qt4
Installing libqt4-test as dep of python-qt4
Installing python-support as dep of python-qt4
Installing python-sip as dep of python-qt4
Installing python-kde4 as dep of software-properties-kde
Installing kdepimlibs5 as dep of python-kde4
Installing libakonadiprivate1 as dep of kdepimlibs5
Installing libboost-program-options1.40.0 as dep of libakonadiprivate1
Installing libgpgme11 as dep of kdepimlibs5
Installing kdepimlibs-data as dep of kdepimlibs5
Installing phonon as dep of python-kde4
Installing install-package as dep of software-properties-kde
Installing gdebi-kde as dep of install-package
Installing gdebi-core as dep of gdebi-kde
Installing python-debian as dep of gdebi-core
Installing kdesudo as dep of gdebi-kde
Installing packagekit as dep of kpackagekit
Installing libnm-glib2 as dep of packagekit
Installing libgudev-1.0-0 as dep of libnm-glib2
Installing libnm-util1 as dep of libnm-glib2
Installing libuuid1 as dep of libnm-util1
Installing libgnome-bluetooth7 as dep of network-manager-gnome
Installing network-manager as dep of network-manager-gnome
Installing wpasupplicant as dep of network-manager
Installing libpcsclite1 as dep of wpasupplicant
new important dependency: dnsmasq-base
Installing dnsmasq-base as dep of network-manager
Installing libidn11 as dep of dnsmasq-base
new important dependency: modemmanager
Installing modemmanager as dep of network-manager
new important dependency: network-manager-pptp
Installing network-manager-pptp as dep of network-manager
Installing pptp-linux as dep of network-manager-pptp
Installing ppp as dep of network-manager-pptp
Installing network-manager-pptp-gnome as dep of network-manager-pptp
Installing mobile-broadband-provider-info as dep of network-manager-gnome
Installing libpackagekit-glib2-12 as dep of packagekit
Installing packagekit-backend-apt as dep of packagekit
Installing python-packagekit as dep of packagekit-backend-apt
Installing python-apt as dep of packagekit-backend-apt
Installing apt-utils as dep of python-apt
Installing apt-xapian-index as dep of packagekit-backend-apt
Installing python-xapian as dep of apt-xapian-index
Installing libxapian15 as dep of python-xapian
Installing update-manager-kde as dep of kpackagekit
Installing libkonq5 as dep of konqueror
Installing libkonq5-templates as dep of libkonq5
Installing libkonqsidebarplugin4 as dep of konqueror
Installing kdebase-data as dep of konqueror
Installing kdebase-bin as dep of konqueror
Installing libblkid1 as dep of util-linux
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libpciaccess0 as dep of xserver-xorg-core
new important dependency: libgl1-mesa-dri
Installing libgl1-mesa-dri as dep of xserver-xorg-core
Installing xserver-xorg-input-evdev as dep of xserver-xorg
Installing xkb-data as dep of xserver-xorg
Installing libglib2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libmono-system2.0-cil as dep of libglib2.0-cil
Installing libmono-security2.0-cil as dep of libmono-system2.0-cil
Installing mono-runtime as dep of libmono-system2.0-cil
Installing mono-gac as dep of mono-runtime
Installing mono-2.0-gac as dep of mono-gac
new important dependency: binfmt-support
Installing binfmt-support as dep of mono-runtime
Installing libgtk2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libmono-cairo2.0-cil as dep of libgtk2.0-cil
Installing libmono-addins0.2-cil as dep of libmono-addins-gui0.2-cil
Installing libmono-posix2.0-cil as dep of libmono-addins-gui0.2-cil
Installing update-inetd as dep of sane-utils
Installing libfile-copy-recursive-perl as dep of update-inetd
Installing libgcr0 as dep of gnome-keyring
Installing libgp11-0 as dep of libgcr0
Installing libiec61883-0 as dep of mythtv-frontend
Installing libraw1394-11 as dep of libiec61883-0
Installing libmyth-0.23-0 as dep of mythtv-frontend
Installing libfaad2 as dep of libmyth-0.23-0
Installing libjack0 as dep of libmyth-0.23-0
Installing libmp3lame0 as dep of libmyth-0.23-0
Installing libvdpau1 as dep of libmyth-0.23-0
Installing libqt4-sql-mysql as dep of libmyth-0.23-0
Installing libmysqlclient16 as dep of libqt4-sql-mysql
Installing mysql-common as dep of libmysqlclient16
Installing wmctrl as dep of mythtv-frontend
Installing libflickrnet2.2-cil as dep of f-spot
Installing libmono-system-web2.0-cil as dep of libflickrnet2.2-cil
Installing libmono2.0-cil as dep of libmono-system-web2.0-cil
Installing libgdiplus as dep of libmono-system-web2.0-cil
Installing libgconf2.0-cil as dep of f-spot
Installing libglade2.0-cil as dep of f-spot
Installing libglitz-glx1 as dep of f-spot
Installing libglitz1 as dep of libglitz-glx1
Installing libgnome-keyring1.0-cil as dep of f-spot
Installing libgnome-vfs2.0-cil as dep of f-spot
Installing libgnome2.24-cil as dep of f-spot
Installing libart2.0-cil as dep of libgnome2.24-cil
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libnunit2.4-cil as dep of f-spot
Installing libmono-system-runtime2.0-cil as dep of libnunit2.4-cil
Installing libbsd0 as dep of libedit2
Installing libftdi1 as dep of lirc
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libxfce4util-common as dep of libxfce4util4
new important dependency: libxfce4util-bin
Installing libxfce4util-bin as dep of libxfce4util4
Installing libxfconf-0-2 as dep of libxfcegui4-4
Installing xfconf as dep of libxfconf-0-2
Installing xfce-keyboard-shortcuts as dep of libxfcegui4-4
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing linux-image-386 as dep of linux-386
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing linux-image-2.6.32-24-386 as dep of linux-image-386
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing wireless-crda as dep of linux-image-2.6.32-24-386
Installing linux-firmware as dep of linux-image-386
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libgadu3 as dep of libpurple0
Installing libgstfarsight0.10-0 as dep of libpurple0
Installing libgssdp-1.0-2 as dep of libgstfarsight0.10-0
Installing libgupnp-1.0-3 as dep of libgstfarsight0.10-0
Installing libgupnp-igd-1.0-2 as dep of libgstfarsight0.10-0
Installing libnice0 as dep of libgstfarsight0.10-0
Installing gstreamer0.10-plugins-base as dep of libgstfarsight0.10-0
Installing libcdparanoia0 as dep of gstreamer0.10-plugins-base
Installing libtheora0 as dep of gstreamer0.10-plugins-base
Installing gstreamer0.10-plugins-good as dep of libgstfarsight0.10-0
Installing libcaca0 as dep of gstreamer0.10-plugins-good
Installing libspeex1 as dep of gstreamer0.10-plugins-good
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libtag1-vanilla as dep of libtag1c2a
Installing libv4l-0 as dep of gstreamer0.10-plugins-good
Installing gstreamer0.10-nice as dep of libgstfarsight0.10-0
Installing libperl5.10 as dep of libpurple0
Installing perl-base as dep of libperl5.10
Installing libuuid-perl as dep of doc-base
Installing perl as dep of libuuid-perl
Installing perl-modules as dep of perl
Installing libmldbm-perl as dep of doc-base
Installing libfreezethaw-perl as dep of libmldbm-perl
Installing libsilcclient-1.1-3 as dep of libpurple0
Installing libzephyr4 as dep of libpurple0
Installing libgmime2.4-cil as dep of tomboy
Installing libgmime-2.4-2 as dep of libgmime2.4-cil
Installing libgnomepanel2.24-cil as dep of tomboy
Installing liblaunchpad-integration1.0-cil as dep of tomboy
Installing libbz2-1.0 as dep of bzip2
Installing libespeak1 as dep of espeak
Installing libportaudio2 as dep of libespeak1
Installing espeak-data as dep of libespeak1
Installing kdelibs-data as dep of kdelibs4c2a
new important dependency: libgpm2
Installing libgpm2 as dep of libncurses5
Installing libiso9660-7 as dep of libiso9660-dev
Installing libcdio10 as dep of libiso9660-7
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing ttf-droid as dep of mythtv-common
Installing cups-common as dep of cupsys-common
Installing libprotobuf5 as dep of libcompizconfig0
Installing compiz-core as dep of libcompizconfig0
Installing update-manager-core as dep of update-manager
new important dependency: libpam-modules
Installing libpam-modules as dep of update-manager-core
Installing base-files as dep of libpam-modules
Installing libselinux1 as dep of libpam-modules
new important dependency: software-properties-gtk
Installing software-properties-gtk as dep of update-manager
Installing python-gobject as dep of python-gnome2
Installing libffi5 as dep of python-gobject
Installing python-gnomecanvas as dep of python-gnome2
Installing python-gtk2 as dep of python-gnome2
Installing python-cairo as dep of python-gtk2
Installing python-pyorbit as dep of python-gnome2
Installing python-gconf as dep of python-gnome2
Installing gnome-media-common as dep of gnome-media
Installing compiz-plugins as dep of compiz-gnome
Installing mysql-client-5.1 as dep of mysql-client
Installing mysql-client-core-5.1 as dep of mysql-client-5.1
Installing libexempi3 as dep of nautilus
Installing libnautilus-extension1 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing gvfs as dep of nautilus
Installing libgdu0 as dep of gvfs
Installing udisks as dep of libgdu0
Installing libatasmart4 as dep of udisks
Installing libparted0debian1 as dep of udisks
Installing libsgutils2-2 as dep of udisks
Installing mtools as dep of udisks
Installing ntfsprogs as dep of udisks
Installing libfuse2 as dep of ntfsprogs
Installing libntfs10 as dep of ntfsprogs
Installing libgvfscommon0 as dep of gvfs
Installing libglib2.0-data as dep of nautilus
Installing libtotem-plparser17 as dep of rhythmbox
Installing media-player-info as dep of rhythmbox
new important dependency: rhythmbox-plugins
Installing rhythmbox-plugins as dep of rhythmbox
Installing libgpod4 as dep of rhythmbox-plugins
Installing libimobiledevice0 as dep of libgpod4
Installing libplist1 as dep of libimobiledevice0
Installing libusbmuxd1 as dep of libimobiledevice0
Installing usbmuxd as dep of libimobiledevice0
Installing libusb-1.0-0 as dep of usbmuxd
Installing libmtp8 as dep of rhythmbox-plugins
Installing python-webkit as dep of rhythmbox-plugins
Installing libwebkit-1.0-2 as dep of python-webkit
Installing libicu42 as dep of libwebkit-1.0-2
Installing libwebkit-1.0-common as dep of libwebkit-1.0-2
Installing python-mako as dep of rhythmbox-plugins
new important dependency: rhythmbox-plugin-cdrecorder
Installing rhythmbox-plugin-cdrecorder as dep of rhythmbox
Installing libbrasero-media0 as dep of rhythmbox-plugin-cdrecorder
Installing brasero-common as dep of libbrasero-media0
Installing libesd0 as dep of libgnome2-0
Installing esound-common as dep of libesd0
new important dependency: esound-clients
Installing esound-clients as dep of esound-common
Installing libgnome2-common as dep of libgnome2-0
Installing system-config-printer-udev as dep of hal-cups-utils
Installing python-cups as dep of system-config-printer-udev
Installing python-cupshelpers as dep of system-config-printer-udev
Installing libbind9-60 as dep of bind9-host
Installing libdns64 as dep of libbind9-60
Installing libgeoip1 as dep of libdns64
Installing geoip-database as dep of libgeoip1
Installing libisc60 as dep of libdns64
Installing libisccfg60 as dep of libbind9-60
Installing libisccc60 as dep of libisccfg60
Installing liblwres60 as dep of bind9-host
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing gimp-help-common as dep of gimp-help-en
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing linux-headers-2.6.32-24-generic as dep of linux-headers-generic
Installing linux-headers-2.6.32-24 as dep of linux-headers-2.6.32-24-generic
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing xserver-xorg-video-geode as dep of xserver-xorg-video-amd
new important dependency: xserver-xorg-video-cyrix
Installing xserver-xorg-video-cyrix as dep of xserver-xorg-video-geode
Installing libuniconf4.6 as dep of wvdial
Installing libwvstreams4.6-base as dep of libuniconf4.6
Installing libwvstreams4.6-extras as dep of libuniconf4.6
Installing libtommath0 as dep of klamav
Installing xserver-xorg-video-apm as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ark as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ati as dep of xserver-xorg-video-all
Installing xserver-xorg-video-r128 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-mach64 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-radeon as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-chips as dep of xserver-xorg-video-all
Installing xserver-xorg-video-cirrus as dep of xserver-xorg-video-all
Installing xserver-xorg-video-fbdev as dep of xserver-xorg-video-all
Installing xserver-xorg-video-i128 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-i740 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
new important dependency: intel-gpu-tools
Installing intel-gpu-tools as dep of xserver-xorg-video-intel
Installing xserver-xorg-video-mga as dep of xserver-xorg-video-all
Installing xserver-xorg-video-neomagic as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nouveau as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nv as dep of xserver-xorg-video-all
Installing xserver-xorg-video-s3 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-savage as dep of xserver-xorg-video-all
Installing xserver-xorg-video-siliconmotion as dep of xserver-xorg-video-all
Installing xserver-xorg-video-sis as dep of xserver-xorg-video-all
Installing xserver-xorg-video-sisusb as dep of xserver-xorg-video-all
Installing xserver-xorg-video-tdfx as dep of xserver-xorg-video-all
Installing xserver-xorg-video-trident as dep of xserver-xorg-video-all
Installing xserver-xorg-video-tseng as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vesa as dep of xserver-xorg-video-all
Installing xserver-xorg-video-openchrome as dep of xserver-xorg-video-all
Installing xserver-xorg-video-voodoo as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vmware as dep of xserver-xorg-video-all
Installing xserver-xorg-video-v4l as dep of xserver-xorg-video-all
Installing libdvdread4 as dep of gstreamer0.10-plugins-ugly
Installing libmad0 as dep of gstreamer0.10-plugins-ugly
Installing libopencore-amrnb0 as dep of gstreamer0.10-plugins-ugly
Installing libopencore-amrwb0 as dep of gstreamer0.10-plugins-ugly
Installing libtwolame0 as dep of gstreamer0.10-plugins-ugly
Installing libpoppler-glib4 as dep of tracker
Installing libpoppler5 as dep of libpoppler-glib4
new important dependency: odt2txt
Installing odt2txt as dep of tracker
Installing libzip1 as dep of odt2txt
Installing libxine1-bin as dep of libxine1-x
Installing libanyevent-perl as dep of libevent-execflow-perl
Installing libasync-interrupt-perl as dep of libanyevent-perl
Installing libcommon-sense-perl as dep of libasync-interrupt-perl
Installing gtk-sharp2-gapi as dep of gtk-sharp2
Installing libglib2.0-cil-dev as dep of gtk-sharp2
Installing libgtk2.0-cil-dev as dep of gtk-sharp2
Installing libglade2.0-cil-dev as dep of gtk-sharp2
Installing monodoc-gtk2.0-manual as dep of gtk-sharp2
Installing libsnmp-base as dep of libsnmp15
Installing libmagickcore2 as dep of obex-data-server
Installing libmagickwand2 as dep of obex-data-server
Installing libiw30 as dep of wireless-tools
Installing samba-common-bin as dep of smb4k
Installing samba-common as dep of samba-common-bin
Installing glabels-data as dep of glabels
Installing libnewt0.52 as dep of whiptail
new important dependency: ttf-sazanami-mincho
Installing ttf-sazanami-mincho as dep of ttf-kochi-mincho
Installing liblua5.1-0 as dep of nmap
Installing libpcap0.8 as dep of nmap
Installing busybox-static as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: apt-transport-https
Installing apt-transport-https as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: irqbalance
Installing irqbalance as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcap-ng0 as dep of irqbalance
Installing foomatic-filters as dep of pxljr
new important dependency: poppler-utils
Installing poppler-utils as dep of foomatic-filters
Installing cups as dep of pxljr
Installing libcupscgi1 as dep of cups
Installing libcupsdriver1 as dep of cups
Installing libcupsimage2 as dep of cups
Installing libcupsmime1 as dep of cups
Installing libcupsppdc1 as dep of cups
Installing libijs-0.35 as dep of cups
Installing cups-client as dep of cups
Installing cups-driver-gutenprint as dep of cups
Installing libgutenprint2 as dep of cups-driver-gutenprint
Installing ghostscript-cups as dep of cups-driver-gutenprint
Installing ghostscript as dep of ghostscript-cups
Installing libgs8 as dep of ghostscript
Installing libgucharmap7 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libboost-filesystem1.40.0 as dep of encfs
Installing libboost-system1.40.0 as dep of libboost-filesystem1.40.0
Installing libboost-serialization1.40.0 as dep of encfs
Installing librlog5 as dep of encfs
Installing libavahi-core6 as dep of avahi-daemon
Installing dbus as dep of avahi-daemon
Installing tk as dep of x11vnc
Installing tcl as dep of tk
Installing sun-java6-bin as dep of sun-java6-plugin
Installing sun-java6-jre as dep of sun-java6-bin
Installing librrd4 as dep of sensord
Installing libspeexdsp1 as dep of pulseaudio
Installing libasound2-plugins as dep of pulseaudio
new important dependency: rtkit
Installing rtkit as dep of pulseaudio
Installing libclamav6 as dep of clamav
Installing cups-ppdc as dep of cupsddk
Installing libggi2 as dep of vlc-plugin-ggi
Installing libvlccore2 as dep of vlc-plugin-ggi
Installing vlc-data as dep of libvlccore2
Installing upower as dep of gnome-power-manager
Installing libupower-glib1 as dep of upower
Installing exim4-base as dep of exim4-daemon-light
Installing libglibmm-2.4-1c2a as dep of gparted
Installing libgtkmm-2.4-1c2a as dep of gparted
Installing libcairomm-1.0-1 as dep of libgtkmm-2.4-1c2a
Installing libpangomm-1.4-1 as dep of libgtkmm-2.4-1c2a
Installing libapache2-mod-php5 as dep of php5
Installing php5-common as dep of libapache2-mod-php5
Installing totem as dep of totem-plugins
Installing totem-common as dep of totem
new important dependency: totem-mozilla
Installing totem-mozilla as dep of totem
Installing libgdata6 as dep of totem-plugins
Installing libgdata-common as dep of libgdata6
Installing python-rdflib as dep of totem-plugins
Installing python-pkg-resources as dep of python-rdflib
Installing python-httplib2 as dep of totem-plugins
Installing linux-image-2.6.32-24-generic as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libnet-dns-perl as dep of clamtk
Installing libdigest-hmac-perl as dep of libnet-dns-perl
Installing libdigest-sha1-perl as dep of libdigest-hmac-perl
Installing libnet-ip-perl as dep of libnet-dns-perl
Installing clamav-base as dep of clamav-freshclam
Installing python-gnomeapplet as dep of gnome-mag
Installing libx264-85 as dep of gstreamer0.10-plugins-ugly-multiverse
new important dependency: libmono-i18n-west1.0-cil
Installing libmono-i18n-west1.0-cil as dep of libmono-corlib1.0-cil
Installing python-gmenu as dep of alacarte
Installing python-xdg as dep of python-gmenu
Installing gnome-menus as dep of alacarte
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-gtksourceview2 as dep of gedit
Installing libcryptui0 as dep of seahorse
Installing gnupg as dep of seahorse
new important dependency: gnupg-curl
Installing gnupg-curl as dep of gnupg
Installing libexo-0.3-0 as dep of xfce4-panel
Installing libexo-common as dep of libexo-0.3-0
Installing exo-utils as dep of xfce4-panel
Installing xserver-xorg-input-mouse as dep of xserver-xorg-input-vmmouse
Installing readahead-fedora as dep of readahead
Installing e2fslibs as dep of readahead-fedora
Installing libaudit0 as dep of readahead-fedora
Installing rarian-compat as dep of scrollkeeper
Installing xml-core as dep of rarian-compat
Installing libhpmud0 as dep of hpijs
new important dependency: keyutils
Installing keyutils as dep of smbfs
Installing libgtk2-imageview-perl as dep of gscan2pdf
Installing libgtkimageview0 as dep of libgtk2-imageview-perl
Installing libsane-perl as dep of gscan2pdf
Installing libconfig-general-perl as dep of gscan2pdf
Installing libset-intspan-perl as dep of gscan2pdf
Installing libforks-perl as dep of gscan2pdf
Installing libsys-sigaction-perl as dep of libforks-perl
Installing liblist-moreutils-perl as dep of libforks-perl
Installing libacme-damn-perl as dep of libforks-perl
Installing libruby1.8 as dep of libatk1-ruby1.8
Installing libglib2-ruby1.8 as dep of libatk1-ruby1.8
Installing mysql-client-5.0 as dep of mysql-server-5.0
Installing libavcodec52 as dep of mplayer
Installing libavutil49 as dep of libavcodec52
Installing libgsm1 as dep of libavcodec52
Installing libschroedinger-1.0-0 as dep of libavcodec52
Installing liboil0.3 as dep of libschroedinger-1.0-0
Installing libavformat52 as dep of mplayer
Installing libopenal1 as dep of mplayer
Installing libpostproc51 as dep of mplayer
Installing libswscale0 as dep of mplayer
Installing light-themes as dep of ubuntu-artwork
Installing ubuntu-mono as dep of light-themes
Installing humanity-icon-theme as dep of ubuntu-mono
Installing gtk2-engines-murrine as dep of light-themes
Installing adium-theme-ubuntu as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
new important dependency: byobu
Installing byobu as dep of screen
Installing python-newt as dep of byobu
Installing libsasl2-2 as dep of libsasl2-modules
Installing python-pexpect as dep of hplip
Installing hplip-data as dep of hplip
Installing libbit-vector-perl as dep of libdate-calc-perl
Installing openssl as dep of openssl-blacklist
Installing gtk2-engines as dep of gnome-themes
Installing gnome-themes-selected as dep of gnome-themes
Installing cpu-checker as dep of update-notifier-common
Installing checkbox-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing checkbox as dep of checkbox-gtk
Installing cups-bsd as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing gnome-session-canberra as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcanberra-pulse as dep of gnome-session-canberra
Installing gnome-themes-ubuntu as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing indicator-applet-session as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing indicator-applet as dep of indicator-applet-session
Installing indicator-messages as dep of indicator-applet
Installing libindicate4 as dep of indicator-messages
Installing indicator-sound as dep of indicator-applet
Installing libido-0.1-0 as dep of indicator-sound
Installing indicator-session as dep of indicator-applet-session
Installing indicator-me as dep of indicator-applet-session
Installing libtelepathy-glib0 as dep of indicator-me
Installing gwibber as dep of indicator-me
Installing python-egenix-mxdatetime as dep of gwibber
Installing python-egenix-mxtools as dep of python-egenix-mxdatetime
Installing python-simplejson as dep of gwibber
Installing libjs-jquery as dep of python-simplejson
Installing python-gtkspell as dep of gwibber
Installing python-wnck as dep of gwibber
Installing python-desktopcouch-records as dep of gwibber
Installing python-couchdb as dep of python-desktopcouch-records
Installing python-desktopcouch as dep of python-desktopcouch-records
Installing desktopcouch as dep of python-desktopcouch
Installing couchdb-bin as dep of desktopcouch
Installing erlang-base as dep of couchdb-bin
Installing libsctp1 as dep of erlang-base
Installing lksctp-tools as dep of libsctp1
Installing erlang-crypto as dep of erlang-base
Installing erlang-syntax-tools as dep of erlang-base
Installing erlang-inets as dep of couchdb-bin
Installing erlang-mnesia as dep of erlang-inets
Installing erlang-runtime-tools as dep of erlang-inets
Installing erlang-ssl as dep of erlang-inets
Installing erlang-public-key as dep of erlang-ssl
Installing erlang-xmerl as dep of couchdb-bin
Installing xulrunner-1.9.2 as dep of couchdb-bin
Installing python-twisted-core as dep of desktopcouch
Installing python-twisted-bin as dep of python-twisted-core
Installing python-zope.interface as dep of python-twisted-core
Installing python-openssl as dep of python-twisted-core
Installing python-pam as dep of python-twisted-core
Installing python-serial as dep of python-twisted-core
Installing python-avahi as dep of desktopcouch
Installing python-gnomekeyring as dep of python-desktopcouch
Installing python-oauth as dep of python-desktopcouch-records
Installing gwibber-service as dep of gwibber
Installing python-pycurl as dep of gwibber-service
Installing libcurl3-gnutls as dep of python-pycurl
Installing python-indicate as dep of gwibber-service
Installing libindicate-gtk2 as dep of python-indicate
Installing ubuntuone-client-gnome as dep of indicator-me
Installing ubuntuone-client as dep of ubuntuone-client-gnome
Installing python-ubuntuone-client as dep of ubuntuone-client
Installing python-ubuntuone-storageprotocol as dep of python-ubuntuone-client
Installing python-protobuf as dep of python-ubuntuone-storageprotocol
Installing protobuf-compiler as dep of python-protobuf
Installing libprotoc5 as dep of protobuf-compiler
Installing python-twisted-web as dep of python-ubuntuone-client
Installing python-pyinotify as dep of python-ubuntuone-client
Installing python-twisted-names as dep of python-ubuntuone-client
Installing python-configglue as dep of ubuntuone-client
Installing libgd2-xpm as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libpam-ck-connector as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libsdl1.2debian-pulseaudio as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing notify-osd as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing notify-osd-icons as dep of notify-osd
Installing software-center as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing python-aptdaemon as dep of software-center
Installing aptdaemon as dep of python-aptdaemon
Installing python-aptdaemon-gtk as dep of software-center
new important dependency: aisleriot
Installing aisleriot as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing guile-1.8-libs as dep of aisleriot
Installing gnome-games-common as dep of aisleriot
new important dependency: app-install-data-partner
Installing app-install-data-partner as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: bluez
Installing bluez as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: bluez-alsa
Installing bluez-alsa as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: bluez-gstreamer
Installing bluez-gstreamer as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: branding-ubuntu
Installing branding-ubuntu as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: computer-janitor-gtk
Installing computer-janitor-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing computer-janitor as dep of computer-janitor-gtk
Installing python-fstab as dep of computer-janitor
new important dependency: empathy
Installing empathy as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libtelepathy-farsight0 as dep of empathy
Installing empathy-common as dep of empathy
Installing telepathy-mission-control-5 as dep of empathy
Installing telepathy-gabble as dep of empathy
Installing libloudmouth1-0 as dep of telepathy-gabble
Installing telepathy-salut as dep of empathy
Installing libavahi-gobject0 as dep of telepathy-salut
Installing telepathy-haze as dep of empathy
Installing telepathy-butterfly as dep of empathy
Installing python-telepathy as dep of telepathy-butterfly
Installing python-papyon as dep of telepathy-butterfly
Installing python-farsight as dep of python-papyon
Installing python-crypto as dep of python-papyon
Installing nautilus-sendto-empathy as dep of empathy
new important dependency: evolution-couchdb
Installing evolution-couchdb as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcouchdb-glib-1.0-2 as dep of evolution-couchdb
Installing libdesktopcouch-glib-1.0-2 as dep of evolution-couchdb
new important dependency: evolution-indicator
Installing evolution-indicator as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: gbrainy
Installing gbrainy as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: gdm-guest-session
Installing gdm-guest-session as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: gnome-bluetooth
Installing gnome-bluetooth as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing obexd-client as dep of gnome-bluetooth
Installing gnome-user-share as dep of gnome-bluetooth
new important dependency: gnome-codec-install
Installing gnome-codec-install as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: gnome-disk-utility
Installing gnome-disk-utility as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libgdu-gtk0 as dep of gnome-disk-utility
new important dependency: gnome-mahjongg
Installing gnome-mahjongg as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: gnome-sudoku
Installing gnome-sudoku as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: gnomine
Installing gnomine as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: ibus
Installing ibus as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libibus1 as dep of ibus
Installing python-ibus as dep of ibus
Installing python-dbus as dep of python-ibus
Installing ibus-gtk as dep of ibus
Installing python-appindicator as dep of ibus
new important dependency: ibus-m17n
Installing ibus-m17n as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libm17n-0 as dep of ibus-m17n
Installing libanthy0 as dep of libm17n-0
Installing libotf0 as dep of libm17n-0
Installing m17n-db as dep of libm17n-0
Installing m17n-contrib as dep of libm17n-0
new important dependency: ibus-table
Installing ibus-table as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: kerneloops-daemon
Installing kerneloops-daemon as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: libwmf0.2-7-gtk
Installing libwmf0.2-7-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: openoffice.org-help-en-us
Installing openoffice.org-help-en-us as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing openoffice.org-writer as dep of openoffice.org-help-en-us
Installing openoffice.org-core as dep of openoffice.org-writer
Installing openoffice.org-common as dep of openoffice.org-core
Installing openoffice.org-style-galaxy as dep of openoffice.org-common
Installing ure as dep of openoffice.org-common
Installing uno-libs3 as dep of ure
Installing libstlport4.6ldbl as dep of uno-libs3
Installing xfonts-mathml as dep of openoffice.org-common
Installing ttf-opensymbol as dep of openoffice.org-core
Installing libgraphite3 as dep of openoffice.org-core
Installing libhyphen0 as dep of openoffice.org-core
Installing libneon27-gnutls as dep of openoffice.org-core
Installing openoffice.org-base-core as dep of openoffice.org-writer
Installing openoffice.org-emailmerge as dep of openoffice.org-writer
Installing python-uno as dep of openoffice.org-emailmerge
Installing openoffice.org-math as dep of openoffice.org-writer
new important dependency: openoffice.org-style-human
Installing openoffice.org-style-human as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: pitivi
Installing pitivi as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing gstreamer0.10-gnonlin as dep of pitivi
Installing python-pygoocanvas as dep of pitivi
Installing libgoocanvas3 as dep of python-pygoocanvas
Installing libgoocanvas-common as dep of libgoocanvas3
new important dependency: plymouth-theme-ubuntu-logo
Installing plymouth-theme-ubuntu-logo as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing plymouth-label as dep of plymouth-theme-ubuntu-logo
new important dependency: plymouth-x11
Installing plymouth-x11 as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: pm-utils-powersave-policy
Installing pm-utils-powersave-policy as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: policykit-desktop-privileges
Installing policykit-desktop-privileges as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: pulseaudio-module-bluetooth
Installing pulseaudio-module-bluetooth as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: quadrapassel
Installing quadrapassel as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libclutter-1.0-0 as dep of quadrapassel
Installing libclutter-gtk-0.10-0 as dep of quadrapassel
new important dependency: rhythmbox-ubuntuone-music-store
Installing rhythmbox-ubuntuone-music-store as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libubuntuone-1.0-1 as dep of rhythmbox-ubuntuone-music-store
Installing python-ubuntuone as dep of rhythmbox-ubuntuone-music-store
new important dependency: simple-scan
Installing simple-scan as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: speech-dispatcher
Installing speech-dispatcher as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libdotconf1.0 as dep of speech-dispatcher
Installing libspeechd2 as dep of speech-dispatcher
new important dependency: telepathy-idle
Installing telepathy-idle as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: ttf-kacst-one
Installing ttf-kacst-one as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: ttf-khmeros-core
Installing ttf-khmeros-core as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: ttf-punjabi-fonts
Installing ttf-punjabi-fonts as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: ttf-takao-pgothic
Installing ttf-takao-pgothic as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: ttf-wqy-microhei
Installing ttf-wqy-microhei as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: usb-creator-gtk
Installing usb-creator-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing usb-creator-common as dep of usb-creator-gtk
Installing syslinux as dep of usb-creator-common
Installing libggz2 as dep of libggzmod4
Installing libggzcore9 as dep of libggzmod4
Installing libept0 as dep of aptitude
Installing liblame0 as dep of libmyth-0.21-0
Installing libscim8c2a as dep of scim-modules-socket
Installing libmjpegtools-1.9 as dep of gstreamer0.10-plugins-bad-multiverse
Installing libquicktime1 as dep of libmjpegtools-1.9
Installing libvte9 as dep of vinagre
Installing monodoc-browser as dep of monodoc-manual
Installing libwebkit1.1-cil as dep of monodoc-browser
Installing monodoc-base as dep of monodoc-browser
Installing libmono-cecil-private-cil as dep of monodoc-base
Installing python-apport as dep of apport
Installing python-launchpadlib as dep of python-apport
Installing python-wadllib as dep of python-launchpadlib
Installing python-lazr.uri as dep of python-wadllib
Installing python-lazr.restfulclient as dep of python-launchpadlib
new important dependency: apport-symptoms
Installing apport-symptoms as dep of apport
Installing libmythtv-perl as dep of mythtv-backend
Installing libwww-perl as dep of librpc-xml-perl
Installing libxml-libxml-perl as dep of librpc-xml-perl
Installing usplash as dep of usplash-theme-ubuntu
Installing apache2.2-common as dep of apache2-mpm-prefork
Installing apache2.2-bin as dep of apache2.2-common
Installing libaprutil1 as dep of apache2.2-bin
Installing libaprutil1-dbd-sqlite3 as dep of apache2.2-bin
Installing libaprutil1-ldap as dep of apache2.2-bin
Installing gnome-terminal-data as dep of gnome-terminal
Installing mono-jit as dep of desktop-data-manager
Installing libpci3 as dep of toshset
Installing libpolkit-gtk-1-0 as dep of gnome-system-tools
Installing libpolkit2 as dep of policykit
Installing libsdl1.2debian-alsa as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: dvb-apps
Installing dvb-apps as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: firefox-gnome-support
Installing firefox-gnome-support as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing firefox as dep of firefox-gnome-support
Installing firefox-branding as dep of firefox
new important dependency: hdhomerun-config
Installing hdhomerun-config as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: hdhomerun-config-gui
Installing hdhomerun-config-gui as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libhdhomerun1 as dep of hdhomerun-config-gui
new important dependency: mytharchive
Installing mytharchive as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing mjpegtools as dep of mytharchive
Installing dvdauthor as dep of mytharchive
new important dependency: mythbuntu-log-grabber
Installing mythbuntu-log-grabber as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: mythgallery
Installing mythgallery as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: mythmovies
Installing mythmovies as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: mythmusic
Installing mythmusic as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing fftw2 as dep of mythmusic
Installing libmpich1.0gf as dep of fftw2
Installing libgfortran3 as dep of libmpich1.0gf
new important dependency: mythtv
Installing mythtv as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: mythweather
Installing mythweather as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libimage-size-perl as dep of mythweather
Installing libsoap-lite-perl as dep of mythweather
Installing libossp-uuid-perl as dep of libsoap-lite-perl
Installing libossp-uuid16 as dep of libossp-uuid-perl
Installing libcrypt-ssleay-perl as dep of libsoap-lite-perl
Installing libfcgi-perl as dep of libsoap-lite-perl
Installing libtask-weaken-perl as dep of libsoap-lite-perl
new important dependency: openssh-server
Installing openssh-server as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing openssh-client as dep of openssh-server
new important dependency: thunar-volman
Installing thunar-volman as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libthunar-vfs-1-2 as dep of thunar-volman
Installing thunar as dep of thunar-volman
Installing thunar-data as dep of thunar
new important dependency: xmltv
Installing xmltv as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libxmltv-perl as dep of xmltv
Installing libxml-writer-perl as dep of libxmltv-perl
Installing libfile-slurp-perl as dep of libxmltv-perl
Installing xmltv-util as dep of libxmltv-perl
Installing libarchive-zip-perl as dep of xmltv-util
Installing libhtml-tableextract-perl as dep of xmltv-util
Installing libhttp-cache-transparent-perl as dep of xmltv-util
Installing libwww-mechanize-perl as dep of xmltv-util
Installing libhttp-server-simple-perl as dep of libwww-mechanize-perl
Installing libtext-bidi-perl as dep of xmltv-util
Installing libxml-dom-perl as dep of xmltv-util
Installing libxml-perl as dep of libxml-dom-perl
Installing libxml-regexp-perl as dep of libxml-dom-perl
Installing libxml-libxslt-perl as dep of xmltv-util
Installing libdatetime-format-strptime-perl as dep of xmltv-util
Installing libdatetime-perl as dep of libdatetime-format-strptime-perl
Installing libdatetime-locale-perl as dep of libdatetime-perl
Installing libparams-validate-perl as dep of libdatetime-locale-perl
Installing libdatetime-timezone-perl as dep of libdatetime-perl
Installing libclass-singleton-perl as dep of libdatetime-timezone-perl
Installing libterm-progressbar-perl as dep of xmltv-util
Installing libclass-methodmaker-perl as dep of libterm-progressbar-perl
Installing liblingua-preferred-perl as dep of xmltv-util
Installing liblog-tracemessages-perl as dep of liblingua-preferred-perl
Installing libhtml-fromtext-perl as dep of liblog-tracemessages-perl
Installing libemail-find-perl as dep of libhtml-fromtext-perl
Installing libemail-address-perl as dep of libemail-find-perl
Installing libemail-valid-perl as dep of libemail-find-perl
Installing libnet-domain-tld-perl as dep of libemail-valid-perl
Installing libexporter-lite-perl as dep of libhtml-fromtext-perl
Installing libregexp-common-perl as dep of libhtml-fromtext-perl
Installing libunicode-string-perl as dep of xmltv-util
Installing xmltv-gui as dep of xmltv
Installing perl-tk as dep of xmltv-gui
Installing libtk-tablematrix-perl as dep of xmltv-gui
new important dependency: xscreensaver
Installing xscreensaver as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libjpeg-progs as dep of xscreensaver
Installing miscfiles as dep of xscreensaver
Installing vlc-nox as dep of mozilla-plugin-vlc
Installing libass4 as dep of vlc-nox
Installing libcddb2 as dep of vlc-nox
Installing libdca0 as dep of vlc-nox
Installing libdvbpsi5 as dep of vlc-nox
Installing libupnp3 as dep of vlc-nox
Installing libvlc2 as dep of vlc-nox
new important dependency: nvidia-common
Installing nvidia-common as dep of jockey-common
Installing nvidia-current-modaliases as dep of nvidia-common
Installing nvidia-173-modaliases as dep of nvidia-common
Installing nvidia-96-modaliases as dep of nvidia-common
new important dependency: fglrx-modaliases
Installing fglrx-modaliases as dep of jockey-common
new important dependency: bcmwl-modaliases
Installing bcmwl-modaliases as dep of jockey-common
Installing libgdict-1.0-6 as dep of gnome-utils
Installing kdesktop as dep of kdebase-kio-plugins
new important dependency: libmath-round-perl
Installing libmath-round-perl as dep of mythweb
Installing samba as dep of samba-dbg
Installing bluetooth as dep of bluez-utils
Installing python-speechd as dep of gnome-orca
Installing python-louis as dep of gnome-orca
Installing liblouis0 as dep of python-louis
Installing liblouis-data as dep of liblouis0
Installing at-spi as dep of python-pyatspi
Installing tcl8.5 as dep of python-tk
Installing tk8.5 as dep of python-tk
Installing cpp-4.4 as dep of cpp
Installing libmpfr1ldbl as dep of cpp-4.4
Installing xserver-xorg-input-synaptics as dep of xserver-xorg-input-all
Installing diffutils as dep of diff
Installing gcc-4.4 as dep of gcc
Installing binutils as dep of gcc-4.4
Installing odbcinst as dep of odbcinst1debian1
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing feh as dep of mythbuntu-gdm-theme
Installing giblib1 as dep of feh
new important dependency: xfce4-settings
Installing xfce4-settings as dep of mythbuntu-gdm-theme
Installing aumix as dep of xfce4-settings
Installing aumix-common as dep of aumix
Installing oss-compat as dep of aumix-common
Installing libgtk2-ex-formfactory-perl as dep of gtk2-ex-formfactory-perl
Installing libelf1 as dep of bug-buddy
new important dependency: gnome-dbg
Installing gnome-dbg as dep of bug-buddy
Installing libatk1.0-dbg as dep of gnome-dbg
Installing libatspi-dbg as dep of gnome-dbg
Installing libglib2.0-0-dbg as dep of gnome-dbg
Installing gnome-applets-dbg as dep of gnome-dbg
Installing gnome-applets as dep of gnome-applets-dbg
Installing gnome-applets-data as dep of gnome-applets
Installing gnome-panel-dbg as dep of gnome-dbg
Installing gnome-panel as dep of gnome-panel-dbg
Installing gnome-panel-data as dep of gnome-panel
Installing libgnomevfs2-0-dbg as dep of gnome-dbg
Installing libgtk2.0-0-dbg as dep of gnome-dbg
Installing libgnome2-dbg as dep of gnome-dbg
Installing libgnomecanvas2-dbg as dep of gnome-dbg
Installing libgnomeui-0-dbg as dep of gnome-dbg
Installing libgnomeui-0 as dep of libgnomeui-0-dbg
Installing libpango1.0-0-dbg as dep of gnome-dbg
Installing librsvg2-dbg as dep of gnome-dbg
Installing totem-dbg as dep of gnome-dbg
Installing evolution-data-server-dbg as dep of gnome-dbg
Installing evolution-dbg as dep of gnome-dbg
Installing python-gtk2-dbg as dep of gnome-dbg
Installing python-dbg as dep of python-gtk2-dbg
Installing python2.6-dbg as dep of python-dbg
Installing python-numpy-dbg as dep of python-gtk2-dbg
Installing python-numpy as dep of python-numpy-dbg
Installing libblas3gf as dep of python-numpy
Installing liblapack3gf as dep of python-numpy
Installing python-cairo-dbg as dep of python-gtk2-dbg
Installing python-gobject-dbg as dep of python-gtk2-dbg
Installing libgsf-gnome-1-114-dbg as dep of gnome-dbg
Installing libgsf-gnome-1-114 as dep of libgsf-gnome-1-114-dbg
Installing libgsf-1-114-dbg as dep of libgsf-gnome-1-114-dbg
Installing gstreamer0.10-plugins-base-dbg as dep of gnome-dbg
Installing gstreamer0.10-plugins-good-dbg as dep of gnome-dbg
Installing gstreamer0.10-pulseaudio as dep of gstreamer0.10-plugins-good-dbg
Installing gstreamer0.10-esd as dep of gstreamer0.10-plugins-good-dbg
Installing gstreamer0.10-plugins-ugly-dbg as dep of gnome-dbg
Installing libgstreamer0.10-0-dbg as dep of gnome-dbg
Installing libgtkhtml3.14-dbg as dep of gnome-dbg
Installing anjuta-dbg as dep of gnome-dbg
Installing anjuta as dep of anjuta-dbg
Installing libdevhelp-1-1 as dep of anjuta
Installing devhelp-common as dep of libdevhelp-1-1
Installing libgda-4.0-4 as dep of anjuta
Installing libgda-4.0-common as dep of libgda-4.0-4
Installing libgdl-1-3 as dep of anjuta
Installing libgdl-1-common as dep of libgdl-1-3
Installing libgladeui-1-9 as dep of anjuta
Installing libsvn1 as dep of anjuta
Installing libvala0 as dep of anjuta
Installing anjuta-common as dep of anjuta
Installing exuberant-ctags as dep of anjuta
Installing automake as dep of anjuta
Installing autoconf as dep of automake
Installing m4 as dep of autoconf
Installing autotools-dev as dep of automake
Installing autogen as dep of anjuta
Installing libopts25 as dep of autogen
Installing libopts25-dev as dep of autogen
Installing intltool as dep of anjuta
Installing gettext as dep of intltool
Installing cvs as dep of gettext
Installing patch as dep of intltool
Installing libtool as dep of anjuta
Installing libltdl-dev as dep of libtool
Installing evince-dbg as dep of gnome-dbg
Installing evince as dep of evince-dbg
Installing libdjvulibre21 as dep of evince
Installing libdjvulibre-text as dep of libdjvulibre21
Installing libevdocument2 as dep of evince
Installing libevview2 as dep of evince
Installing libkpathsea5 as dep of evince
Installing libspectre1 as dep of evince
Installing epiphany-browser-dbg as dep of gnome-dbg
Installing epiphany-browser as dep of epiphany-browser-dbg
Installing epiphany-browser-data as dep of epiphany-browser
Installing libgirepository1.0-0 as dep of epiphany-browser
Installing libseed0 as dep of epiphany-browser
Installing gnome-js-common as dep of libseed0
Installing gir1.0-glib-2.0 as dep of libseed0
Installing gir1.0-clutter-1.0 as dep of libseed0
Installing gir1.0-freedesktop as dep of gir1.0-clutter-1.0
Installing gir1.0-pango-1.0 as dep of gir1.0-clutter-1.0
Installing gir1.0-gstreamer-0.10 as dep of libseed0
Installing gir1.0-gtk-2.0 as dep of libseed0
Installing gir1.0-atk-1.0 as dep of gir1.0-gtk-2.0
Installing libwebkit-1.0-2-dbg as dep of epiphany-browser-dbg
Installing eog-dbg as dep of gnome-dbg
Installing libgdl-1-dbg as dep of gnome-dbg
Installing libgda3-3-dbg as dep of gnome-dbg
Installing libgda3-3 as dep of libgda3-3-dbg
Installing libgda3-common as dep of libgda3-3
Installing libgda3-bin as dep of libgda3-3
Installing libloudmouth1-0-dbg as dep of gnome-dbg
Installing gimp-dbg as dep of gnome-dbg
Installing gimp as dep of gimp-dbg
Installing libgimp2.0 as dep of gimp
Installing gimp-data as dep of gimp
Installing libbabl-0.0-0 as dep of gimp
Installing libgegl-0.0-0 as dep of gimp
Installing libfontconfig1-dbg as dep of gnome-dbg
Installing libgail-gnome-dbg as dep of gnome-dbg
Installing libgoffice-dbg as dep of gnome-dbg
Installing libgoffice-0.8-8 as dep of libgoffice-dbg
Installing libgoffice-0.8-8-common as dep of libgoffice-0.8-8
Installing libnspr4-0d-dbg as dep of gnome-dbg
Installing libnss3-1d-dbg as dep of gnome-dbg
Installing libnss3-1d as dep of libnss3-1d-dbg
Installing liboobs-1-4-dbg as dep of gnome-dbg
Installing liboobs-1-4 as dep of liboobs-1-4-dbg
Installing libxft2-dbg as dep of gnome-dbg
Installing libxml2-dbg as dep of gnome-dbg
Installing rhythmbox-dbg as dep of gnome-dbg
Installing language-selector-common as dep of language-selector
Installing mysql-server-5.1 as dep of mysql-server
Installing mysql-client-5.1 as dep of mysql-server-5.1
Installing mysql-server-core-5.1 as dep of mysql-server-5.1
Installing libhtml-template-perl as dep of mysql-server-5.1
Installing libpango-perl as dep of libgtk2-perl
new important dependency: libxml-sax-expat-perl
Installing libxml-sax-expat-perl as dep of libxml-sax-perl
Installing libmono-posix1.0-cil as dep of libmono1.0-cil
new important dependency: fancontrol
Installing fancontrol as dep of lm-sensors
new important dependency: ttf-mscorefonts-installer
Installing ttf-mscorefonts-installer as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: libavcodec-extra-52
Installing libavcodec-extra-52 as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libavutil-extra-49 as dep of libavcodec-extra-52
Installing libdirac-encoder0 as dep of libavcodec-extra-52
Installing libopenjpeg2 as dep of libavcodec-extra-52
new important dependency: icedtea6-plugin
Installing icedtea6-plugin as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing openjdk-6-jre as dep of icedtea6-plugin
Installing openjdk-6-jre-headless as dep of openjdk-6-jre
Installing openjdk-6-jre-lib as dep of openjdk-6-jre-headless
Installing ca-certificates-java as dep of openjdk-6-jre-headless
Installing tzdata-java as dep of openjdk-6-jre-headless
Installing tzdata as dep of tzdata-java
Installing icedtea-6-jre-cacao as dep of openjdk-6-jre-headless
Installing libaccess-bridge-java-jni as dep of openjdk-6-jre
Installing libaccess-bridge-java as dep of libaccess-bridge-java-jni
new important dependency: libmp4v2-0
Installing libmp4v2-0 as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing python-smbc as dep of system-config-printer-common
new important dependency: avahi-utils
Installing avahi-utils as dep of system-config-printer-common
Installing libavdevice52 as dep of ffmpeg
Installing libdc1394-22 as dep of libavdevice52
Installing libavfilter0 as dep of ffmpeg
Installing kbd as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing netcat-openbsd as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing rsyslog as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing ureadahead as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libbonobo2-common as dep of libbonobo2-0
Installing zlib1g as dep of zlib1g-dev
new important dependency: twolame
Installing twolame as dep of transcode
Installing sensible-utils as dep of debianutils
Installing libmagic1 as dep of file
Installing apturl-common as dep of apturl
Installing libpst4 as dep of evolution-plugins
Installing libyaml-syck-perl as dep of libdate-manip-perl
Installing khelpcenter4 as dep of khelpcenter
Installing landscape-common as dep of landscape-client
Installing python-smartpm as dep of landscape-common
new important dependency: libmono-i18n-west2.0-cil
Installing libmono-i18n-west2.0-cil as dep of libmono-corlib2.0-cil
Installing libcelt0-0 as dep of gstreamer0.10-plugins-bad
Installing libflite1 as dep of gstreamer0.10-plugins-bad
Installing libgme0 as dep of gstreamer0.10-plugins-bad
Installing libkate1 as dep of gstreamer0.10-plugins-bad
Installing libmimic0 as dep of gstreamer0.10-plugins-bad
Installing libofa0 as dep of gstreamer0.10-plugins-bad
Installing liborc-0.4-0 as dep of gstreamer0.10-plugins-bad
new important dependency: xinput
Installing xinput as dep of acpi-support
Installing libxcb-keysyms1 as dep of vlc
Installing libxfce4menu-0.1-0 as dep of xfdesktop4
Installing xfdesktop4-data as dep of xfdesktop4
Installing libgksu2-0 as dep of gksu
Installing gnash-common as dep of gnash
Installing libboost-date-time1.40.0 as dep of gnash-common
Installing libboost-thread1.40.0 as dep of gnash-common
Installing libc-dev-bin as dep of libc6-dev
Installing manpages-dev as dep of libc-dev-bin
new important dependency: xserver-xorg-video-cyrix
Installing xserver-xorg-video-cyrix as dep of xserver-xorg-video-geode
new important dependency: pidgin-libnotify
Installing pidgin-libnotify as dep of pidgin
Installing libconfig-auto-perl as dep of mythtv-status
Installing libconfig-inifiles-perl as dep of libconfig-auto-perl
Installing libyaml-perl as dep of libconfig-auto-perl
Installing xorg-docs-core as dep of xorg
Installing python-imdbpy as dep of mythvideo
Installing python-lxml as dep of python-imdbpy
Installing libpango1-ruby1.8 as dep of libgtk2-ruby1.8
new important dependency: lockfile-progs
Installing lockfile-progs as dep of ntpdate
Installing mythtv-theme-arclight as dep of mythtv-themes
Installing mythtv-theme-blootube-osd as dep of mythtv-themes
Installing mythtv-theme-blueosd as dep of mythtv-themes
Installing mythtv-theme-graphite as dep of mythtv-themes
Installing mythtv-theme-iulius-osd as dep of mythtv-themes
Installing mythtv-theme-metallurgy as dep of mythtv-themes
Installing mythtv-theme-mono-osd as dep of mythtv-themes
Installing mythtv-theme-projectgrayhem-osd as dep of mythtv-themes
Installing mythtv-theme-retro-osd as dep of mythtv-themes
Installing mythtv-theme-titivillus-osd as dep of mythtv-themes
new important dependency: libmagickcore2-extra
Installing libmagickcore2-extra as dep of imagemagick
Installing libgraphviz4 as dep of libmagickcore2-extra
Installing gconf-defaults-service as dep of gconf-editor
Installing grub-common as dep of grub
Installing os-prober as dep of grub-common
new important dependency: audacious
Installing audacious as dep of streamtuner
Installing audacious-plugins as dep of audacious
Installing libaudcore1 as dep of audacious-plugins
Installing libmowgli1 as dep of libaudcore1
Installing libaudid3tag2 as dep of audacious-plugins
Installing libbinio1ldbl as dep of audacious-plugins
Installing libcue1 as dep of audacious-plugins
Installing libfluidsynth1 as dep of audacious-plugins
Installing liblash2 as dep of libfluidsynth1
Installing libmcs1 as dep of audacious-plugins
Installing libresid-builder0c2a as dep of audacious-plugins
Installing libsidplay2 as dep of audacious-plugins
Installing libaudclient2 as dep of audacious
new important dependency: streamripper
Installing streamripper as dep of streamtuner
Installing libvcdinfo0 as dep of libvcdinfo-dev
Installing libapparmor-perl as dep of apparmor-utils
Installing libapparmor1 as dep of libapparmor-perl
new important dependency: libnet-libidn-perl
Installing libnet-libidn-perl as dep of libio-socket-ssl-perl
Installing install-info as dep of info
Installing insserv as dep of sysv-rc
Installing python-bugbuddy as dep of python-gnome2-desktop
Installing python-evince as dep of python-gnome2-desktop
Installing python-evolution as dep of python-gnome2-desktop
Installing python-gnomedesktop as dep of python-gnome2-desktop
Installing python-gnomeprint as dep of python-gnome2-desktop
Installing python-gtop as dep of python-gnome2-desktop
Installing python-mediaprofiles as dep of python-gnome2-desktop
Installing python-metacity as dep of python-gnome2-desktop
Installing python-rsvg as dep of python-gnome2-desktop
Installing python-totem-plparser as dep of python-gnome2-desktop
Installing transcode-utils as dep of dvdrip
Installing dvdrip-utils as dep of dvdrip
Installing libntfs-3g75 as dep of ntfs-3g
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libntlm0 as dep of gkrellm
Starting
Starting 2
Investigating libc6
Package libc6 has broken dep on belocs-locales-bin
  Considering belocs-locales-bin -2 as a solution to libc6 14824
  Added belocs-locales-bin to the remove list
  Fixing libc6 via remove of belocs-locales-bin
Investigating libxcb1
Package libxcb1 has broken dep on libxcb-xlib0
  Considering libxcb-xlib0 -1 as a solution to libxcb1 565
  Added libxcb-xlib0 to the remove list
  Fixing libxcb1 via remove of libxcb-xlib0
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 1 as a solution to libcups2 376
  Added libcupsys2 to the remove list
  Fixing libcups2 via remove of libcupsys2
Investigating libthai0
Package libthai0 has broken dep on libdatrie0
  Considering libdatrie0 -1 as a solution to libthai0 249
  Added libdatrie0 to the remove list
  Fixing libthai0 via remove of libdatrie0
Investigating mono-runtime
Package mono-runtime has broken dep on mono-common
  Considering mono-common 0 as a solution to mono-runtime 230
  Added mono-common to the remove list
Package mono-runtime has broken dep on mono-jit
  Considering mono-jit 1 as a solution to mono-runtime 230
  Added mono-jit to the remove list
  Fixing mono-runtime via remove of mono-common
  Fixing mono-runtime via remove of mono-jit
Investigating xserver-xorg-core
Package xserver-xorg-core has broken dep on xserver-xorg-input-2
  Considering xserver-xorg-input-kbd -1 as a solution to xserver-xorg-core 96
  Added xserver-xorg-input-kbd to the remove list
  Considering xserver-xorg-input-mouse 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-input-synaptics 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-input-evdev 5 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-input-wacom 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-input-vmmouse 2 as a solution to xserver-xorg-core 96
Package xserver-xorg-core has broken dep on xserver-xorg-video-2
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-siliconmotion 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-ati 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-i740 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-geode 3 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-via 0 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-nv 2 as a solution to xserver-xorg-core 96
  Considering nvidia-glx-new -1 as a solution to xserver-xorg-core 96
  Added nvidia-glx-new to the remove list
  Considering xserver-xorg-video-i810 -1 as a solution to xserver-xorg-core 96
  Added xserver-xorg-video-i810 to the remove list
  Considering xserver-xorg-video-intel 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-chips 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-tga -1 as a solution to xserver-xorg-core 96
  Added xserver-xorg-video-tga to the remove list
  Considering xserver-xorg-video-trident 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-s3 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-vga -1 as a solution to xserver-xorg-core 96
  Added xserver-xorg-video-vga to the remove list
  Considering xserver-xorg-video-i128 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-mga 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-nsc -1 as a solution to xserver-xorg-core 96
  Added xserver-xorg-video-nsc to the remove list
  Considering xserver-xorg-video-newport -1 as a solution to xserver-xorg-core 96
  Added xserver-xorg-video-newport to the remove list
  Considering xserver-xorg-video-neomagic 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-cirrus 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-ark 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-tdfx 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-sisusb 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-dummy 0 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-rendition 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-vesa 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-cyrix -1 as a solution to xserver-xorg-core 96
  Added xserver-xorg-video-cyrix to the remove list
  Considering xserver-xorg-video-imstt -1 as a solution to xserver-xorg-core 96
  Added xserver-xorg-video-imstt to the remove list
  Considering xserver-xorg-video-glint 0 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-fbdev 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-savage 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-vmware 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-openchrome 3 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-s3virge 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-voodoo 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-apm 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-sis 2 as a solution to xserver-xorg-core 96
  Considering xserver-xorg-video-v4l 2 as a solution to xserver-xorg-core 96
  Fixing xserver-xorg-core via remove of xserver-xorg-input-kbd
  Fixing xserver-xorg-core via remove of nvidia-glx-new
  Fixing xserver-xorg-core via remove of xserver-xorg-video-i810
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tga
  Fixing xserver-xorg-core via remove of xserver-xorg-video-vga
  Fixing xserver-xorg-core via remove of xserver-xorg-video-nsc
  Fixing xserver-xorg-core via remove of xserver-xorg-video-newport
  Fixing xserver-xorg-core via remove of xserver-xorg-video-cyrix
  Fixing xserver-xorg-core via remove of xserver-xorg-video-imstt
Investigating upstart
Package upstart has broken dep on startup-tasks
  Considering startup-tasks 2 as a solution to upstart 63
  Added startup-tasks to the remove list
Package upstart has broken dep on system-services
  Considering system-services 2 as a solution to upstart 63
  Added system-services to the remove list
Package upstart has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 5 as a solution to upstart 63
  Added upstart-compat-sysv to the remove list
  Fixing upstart via remove of startup-tasks
  Fixing upstart via remove of system-services
  Fixing upstart via remove of upstart-compat-sysv
Investigating kdebase-runtime
Package kdebase-runtime has broken dep on kdebase-bin-kde3
  Considering kdebase-bin-kde3 -1 as a solution to kdebase-runtime 41
  Added kdebase-bin-kde3 to the remove list
  Fixing kdebase-runtime via remove of kdebase-bin-kde3
Investigating libmp3lame0
Package libmp3lame0 has broken dep on liblame0
  Considering liblame0 2 as a solution to libmp3lame0 40
  Added liblame0 to the remove list
  Fixing libmp3lame0 via remove of liblame0
Investigating mysql-client-5.1
Package mysql-client-5.1 has broken dep on mysql-client-5.0
  Considering mysql-client-5.0 29 as a solution to mysql-client-5.1 31
  Added mysql-client-5.0 to the remove list
  Fixing mysql-client-5.1 via remove of mysql-client-5.0
Investigating kdebase-bin
Package kdebase-bin has broken dep on kcontrol
  Considering kcontrol -1 as a solution to kdebase-bin 26
  Added kcontrol to the remove list
Package kdebase-bin has broken dep on kdesktop
  Considering kdesktop 1 as a solution to kdebase-bin 26
  Added kdesktop to the remove list
  Fixing kdebase-bin via remove of kcontrol
  Fixing kdebase-bin via remove of kdesktop
Investigating libnautilus-extension1
Package libnautilus-extension1 has broken dep on gnome-mount
  Considering gnome-mount 1 as a solution to libnautilus-extension1 25
  Added gnome-mount to the remove list
  Fixing libnautilus-extension1 via remove of gnome-mount
Investigating kbd
Package kbd has broken dep on console-utilities
  Considering console-tools 8 as a solution to kbd 24
  Considering console-tools 8 as a solution to kbd 24
  Added console-tools to the remove list
Package kbd has broken dep on open
  Considering console-tools 8 as a solution to kbd 24
  Considering console-tools 8 as a solution to kbd 24
  Added console-tools to the remove list
  Fixing kbd via remove of console-tools
  Fixing kbd via remove of console-tools
Investigating cups
Package cups has broken dep on cupsddk-drivers
  Considering cupsddk-drivers -1 as a solution to cups 19
  Added cupsddk-drivers to the remove list
  Fixing cups via remove of cupsddk-drivers
Investigating plymouth
Package plymouth has broken dep on usplash
  Considering usplash 3 as a solution to plymouth 17
  Added usplash to the remove list
  Considering usplash 3 as a solution to plymouth 17
  Fixing plymouth via remove of usplash
Investigating libxml-libxml-perl
Package libxml-libxml-perl has broken dep on libxml-libxml-common-perl
  Considering libxml-libxml-common-perl -1 as a solution to libxml-libxml-perl 16
  Added libxml-libxml-common-perl to the remove list
  Fixing libxml-libxml-perl via remove of libxml-libxml-common-perl
Investigating exo-utils
Package exo-utils has broken dep on xfce4-mcs-manager
  Considering xfce4-mcs-manager 1 as a solution to exo-utils 12
  Added xfce4-mcs-manager to the remove list
  Fixing exo-utils via remove of xfce4-mcs-manager
Investigating gnome-games-common
Package gnome-games-common has broken dep on gnome-cards-data
  Considering gnome-cards-data 3 as a solution to gnome-games-common 11
  Added gnome-cards-data to the remove list
  Fixing gnome-games-common via remove of gnome-cards-data
Investigating libmetacity-private0
Package libmetacity-private0 has broken dep on libmetacity0
  Considering libmetacity0 -1 as a solution to libmetacity-private0 9
  Added libmetacity0 to the remove list
  Fixing libmetacity-private0 via remove of libmetacity0
Investigating rsyslog
Package rsyslog has broken dep on linux-kernel-log-daemon
  Considering klogd 0 as a solution to rsyslog 8
  Considering syslog-ng 0 as a solution to rsyslog 8
  Considering socklog-run 0 as a solution to rsyslog 8
  Considering klogd 0 as a solution to rsyslog 8
  Added klogd to the remove list
  Considering inetutils-syslogd 0 as a solution to rsyslog 8
  Considering dsyslog 0 as a solution to rsyslog 8
Package rsyslog has broken dep on system-log-daemon
  Considering sysklogd 0 as a solution to rsyslog 8
  Considering syslog-ng 0 as a solution to rsyslog 8
  Considering sysklogd 0 as a solution to rsyslog 8
  Added sysklogd to the remove list
  Considering socklog-run 0 as a solution to rsyslog 8
  Considering inetutils-syslogd 0 as a solution to rsyslog 8
  Considering dsyslog 0 as a solution to rsyslog 8
  Fixing rsyslog via remove of klogd
  Fixing rsyslog via remove of sysklogd
Investigating ureadahead
Package ureadahead has broken dep on readahead
  Considering readahead 0 as a solution to ureadahead 8
  Added readahead to the remove list
  Considering readahead 0 as a solution to ureadahead 8
  Considering readahead-fedora 1 as a solution to ureadahead 8
  Fixing ureadahead via remove of readahead
Investigating gimp-data
Package gimp-data has broken dep on gimp-python
  Considering gimp-python -1 as a solution to gimp-data 8
  Added gimp-python to the remove list
  Fixing gimp-data via remove of gimp-python
Investigating nautilus
Package nautilus has broken dep on gnome-volume-manager
  Considering gnome-volume-manager -1 as a solution to nautilus 7
  Added gnome-volume-manager to the remove list
  Fixing nautilus via remove of gnome-volume-manager
Investigating python-zope.interface
Package python-zope.interface has broken dep on python-zopeinterface
  Considering python-zopeinterface 0 as a solution to python-zope.interface 7
  Added python-zopeinterface to the remove list
  Fixing python-zope.interface via remove of python-zopeinterface
Investigating gimp
Package gimp has broken dep on gimp-gnomevfs
  Considering gimp-gnomevfs -1 as a solution to gimp 7
  Added gimp-gnomevfs to the remove list
  Fixing gimp via remove of gimp-gnomevfs
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet -1 as a solution to gdm 6
  Added fast-user-switch-applet to the remove list
  Fixing gdm via remove of fast-user-switch-applet
Investigating openoffice.org-common
Package openoffice.org-common has broken dep on openoffice.org-debian-menus
  Considering openoffice.org-debian-menus 0 as a solution to openoffice.org-common 6
  Added openoffice.org-debian-menus to the remove list
  Fixing openoffice.org-common via remove of openoffice.org-debian-menus
Investigating libokularcore1-kde4
Package libokularcore1-kde4 has broken dep on libgs8
  Considering libgs8 11 as a solution to libokularcore1-kde4 4
  Removing libokularcore1-kde4 rather than change libgs8
Investigating classpath-common
Package classpath-common has broken dep on gcjwebplugin
  Considering gcjwebplugin -1 as a solution to classpath-common 4
  Added gcjwebplugin to the remove list
  Fixing classpath-common via remove of gcjwebplugin
Investigating libmythtv-perl
Package libmythtv-perl has broken dep on libmyth-perl
  Considering libmyth-perl 0 as a solution to libmythtv-perl 3
  Added libmyth-perl to the remove list
  Considering libmyth-perl 0 as a solution to libmythtv-perl 3
  Fixing libmythtv-perl via remove of libmyth-perl
Investigating mysql-server-5.1
Package mysql-server-5.1 has broken dep on mysql-server-5.0
  Considering mysql-server-5.0 0 as a solution to mysql-server-5.1 3
  Added mysql-server-5.0 to the remove list
  Fixing mysql-server-5.1 via remove of mysql-server-5.0
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken dep on libchromexvmc1
  Considering libchromexvmc1 -1 as a solution to xserver-xorg-video-openchrome 3
  Added libchromexvmc1 to the remove list
Package xserver-xorg-video-openchrome has broken dep on libchromexvmcpro1
  Considering libchromexvmcpro1 -1 as a solution to xserver-xorg-video-openchrome 3
  Added libchromexvmcpro1 to the remove list
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmc1
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmcpro1
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 63 as a solution to upstart-logd 2
  Removing upstart-logd rather than change upstart
Investigating libgtkhtml-editor-common
Package libgtkhtml-editor-common has broken dep on gtkhtml3.14
  Considering gtkhtml3.14 -1 as a solution to libgtkhtml-editor-common 2
  Added gtkhtml3.14 to the remove list
  Fixing libgtkhtml-editor-common via remove of gtkhtml3.14
Investigating libgnomekbd2
Package libgnomekbd2 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 4 as a solution to libgnomekbd2 1
  Removing libgnomekbd2 rather than change libgnomekbd-common
Investigating guidance-backends
Package guidance-backends has broken dep on python
  Considering python 1322 as a solution to guidance-backends 1
  Removing guidance-backends rather than change python
Investigating gnome-bluetooth
Package gnome-bluetooth has broken dep on bluez-gnome
  Considering bluez-gnome -1 as a solution to gnome-bluetooth 1
  Added bluez-gnome to the remove list
  Fixing gnome-bluetooth via remove of bluez-gnome
Investigating libanyevent-perl
Package libanyevent-perl has broken dep on anyevent-perl
  Considering anyevent-perl -1 as a solution to libanyevent-perl 1
  Added anyevent-perl to the remove list
  Fixing libanyevent-perl via remove of anyevent-perl
Investigating kicker
Package kicker has broken dep on kdebase-data
  Considering kdebase-data 16 as a solution to kicker 1
  Removing kicker rather than change kdebase-data
Investigating xfce4-settings
Package xfce4-settings has broken dep on xfce4-mcs-plugins
  Considering xfce4-mcs-plugins -1 as a solution to xfce4-settings 1
  Added xfce4-mcs-plugins to the remove list
  Fixing xfce4-settings via remove of xfce4-mcs-plugins
Investigating libavcodec1d
Package libavcodec1d has broken dep on liblame0
  Considering liblame0 2 as a solution to libavcodec1d 1
  Removing libavcodec1d rather than change liblame0
Investigating mythbuntu-default-settings
Package mythbuntu-default-settings has broken dep on mythbuntu-artwork-usplash
  Considering mythbuntu-artwork-usplash -1 as a solution to mythbuntu-default-settings 1
  Added mythbuntu-artwork-usplash to the remove list
  Fixing mythbuntu-default-settings via remove of mythbuntu-artwork-usplash
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgd2-xpm
  Considering libgd2-xpm 3 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgd2-xpm
Investigating usplash-theme-ubuntu
Package usplash-theme-ubuntu has broken dep on usplash
  Considering usplash 3 as a solution to usplash-theme-ubuntu 0
  Removing usplash-theme-ubuntu rather than change usplash
Investigating human-theme
Package human-theme has broken dep on gtk2-engines-ubuntulooks
  Considering gtk2-engines-ubuntulooks -1 as a solution to human-theme 0
  Added gtk2-engines-ubuntulooks to the remove list
  Fixing human-theme via remove of gtk2-engines-ubuntulooks
Investigating mythtv-themes
Package mythtv-themes has broken dep on mythtv-theme-projectgrayhem
  Considering mythtv-theme-projectgrayhem -1 as a solution to mythtv-themes 0
  Added mythtv-theme-projectgrayhem to the remove list
  Fixing mythtv-themes via remove of mythtv-theme-projectgrayhem
Investigating libuniconf4.6
Package libuniconf4.6 has broken dep on libuniconf4.4
  Considering libuniconf4.4 -1 as a solution to libuniconf4.6 0
  Added libuniconf4.4 to the remove list
  Fixing libuniconf4.6 via remove of libuniconf4.4
Investigating aisleriot
Package aisleriot has broken dep on gnome-games-data
  Considering gnome-games-data -1 as a solution to aisleriot -1
  Holding Back aisleriot rather than change gnome-games-data
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5435 as a solution to libperl5.8 -1
  Removing libperl5.8 rather than change perl-base
Investigating quadrapassel
Package quadrapassel has broken dep on gnome-games-data
  Considering gnome-games-data -1 as a solution to quadrapassel -1
  Holding Back quadrapassel rather than change gnome-games-data
Investigating gnome-mahjongg
Package gnome-mahjongg has broken dep on gnome-games-data
  Considering gnome-games-data -1 as a solution to gnome-mahjongg -1
  Holding Back gnome-mahjongg rather than change gnome-games-data
Investigating libmyth-0.21-0
Package libmyth-0.21-0 has broken dep on liblame0
  Considering liblame0 2 as a solution to libmyth-0.21-0 -1
  Removing libmyth-0.21-0 rather than change liblame0
Investigating pm-utils-powersave-policy
Package pm-utils-powersave-policy has broken dep on laptop-mode-tools
  Considering laptop-mode-tools 0 as a solution to pm-utils-powersave-policy -1
  Holding Back pm-utils-powersave-policy rather than change laptop-mode-tools
Investigating desktop-data-manager
Package desktop-data-manager has broken dep on mono-jit
  Considering mono-jit 1 as a solution to desktop-data-manager -1
  Removing desktop-data-manager rather than change mono-jit
Investigating libavformat1d
Package libavformat1d has broken dep on libavcodec1d
  Considering libavcodec1d 1 as a solution to libavformat1d -1
  Removing libavformat1d rather than change libavcodec1d
Investigating python-gtkhtml2
Package python-gtkhtml2 has broken dep on python
  Considering python 1322 as a solution to python-gtkhtml2 -1
  Removing python-gtkhtml2 rather than change python
Investigating kdebase-kio-plugins
Package kdebase-kio-plugins has broken dep on kdesktop
  Considering kdesktop 1 as a solution to kdebase-kio-plugins -1
  Removing kdebase-kio-plugins rather than change kdesktop
Investigating libgnomekbdui2
Package libgnomekbdui2 has broken dep on libgnomekbd2
  Considering libgnomekbd2 1 as a solution to libgnomekbdui2 -1
  Removing libgnomekbdui2 rather than change libgnomekbd2
Investigating python-xml
Package python-xml has broken dep on python
  Considering python 1322 as a solution to python-xml -1
  Removing python-xml rather than change python
Investigating ttf-mscorefonts-installer
Package ttf-mscorefonts-installer has broken dep on msttcorefonts
  Considering msttcorefonts -1 as a solution to ttf-mscorefonts-installer -1
  Holding Back ttf-mscorefonts-installer rather than change msttcorefonts
Investigating gnome-games-data
Package gnome-games-data has broken dep on gnome-cards-data
  Considering gnome-cards-data 3 as a solution to gnome-games-data -1
  Removing gnome-games-data rather than change gnome-cards-data
Investigating displayconfig-gtk
Package displayconfig-gtk has broken dep on guidance-backends
  Considering guidance-backends 1 as a solution to displayconfig-gtk -1
  Removing displayconfig-gtk rather than change guidance-backends
Investigating xulrunner-1.9-gnome-support
Package xulrunner-1.9-gnome-support has broken dep on xulrunner-1.9
  Considering xulrunner-1.9 3 as a solution to xulrunner-1.9-gnome-support -1
  Removing xulrunner-1.9-gnome-support rather than change xulrunner-1.9
Investigating kde4libs-bin
Package kde4libs-bin has broken dep on kdelibs5
  Considering kdelibs5 69 as a solution to kde4libs-bin -1
  Removing kde4libs-bin rather than change kdelibs5
Investigating okular-kde4
Package okular-kde4 has broken dep on libokularcore1-kde4
  Considering libokularcore1-kde4 4 as a solution to okular-kde4 -2
  Removing okular-kde4 rather than change libokularcore1-kde4
Investigating okular-extra-backends-kde4
Package okular-extra-backends-kde4 has broken dep on libokularcore1-kde4
  Considering libokularcore1-kde4 4 as a solution to okular-extra-backends-kde4 -2
  Removing okular-extra-backends-kde4 rather than change libokularcore1-kde4
Done
Installing dkms as dep of nvidia-current
Installing fakeroot as dep of dkms
Starting
Starting 2
Investigating libdeskbar-tracker
Package libdeskbar-tracker has broken dep on deskbar-applet
  Considering deskbar-applet 10001 as a solution to libdeskbar-tracker 0
    Reinst Failed because of protected deskbar-applet
  Removing libdeskbar-tracker rather than change deskbar-applet
Done
Starting
Starting 2
Investigating tracker-search-tool
Package tracker-search-tool has broken dep on tracker
  Considering tracker 10001 as a solution to tracker-search-tool 0
    Reinst Failed because of protected tracker
  Removing tracker-search-tool rather than change tracker
Done
Starting
Starting 2
Investigating linux-restricted-modules-2.6.24-28-generic
Package linux-restricted-modules-2.6.24-28-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-28-generic 1
  Removing linux-restricted-modules-2.6.24-28-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-28-386
Package linux-restricted-modules-2.6.24-28-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-28-386 1
  Removing linux-restricted-modules-2.6.24-28-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-25-386
Package linux-restricted-modules-2.6.24-25-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-25-386 -1
  Removing linux-restricted-modules-2.6.24-25-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-23-generic
Package linux-restricted-modules-2.6.24-23-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-23-generic -1
  Removing linux-restricted-modules-2.6.24-23-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-18-generic
Package linux-restricted-modules-2.6.24-18-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-18-generic -1
  Removing linux-restricted-modules-2.6.24-18-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-17-386
Package linux-restricted-modules-2.6.24-17-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-17-386 -1
  Removing linux-restricted-modules-2.6.24-17-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-22-386
Package linux-restricted-modules-2.6.24-22-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-22-386 -1
  Removing linux-restricted-modules-2.6.24-22-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-26-generic
Package linux-restricted-modules-2.6.24-26-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-26-generic -1
  Removing linux-restricted-modules-2.6.24-26-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-26-386
Package linux-restricted-modules-2.6.24-26-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-26-386 -1
  Removing linux-restricted-modules-2.6.24-26-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-21-generic
Package linux-restricted-modules-2.6.24-21-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-21-generic -1
  Removing linux-restricted-modules-2.6.24-21-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-16-generic
Package linux-restricted-modules-2.6.24-16-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-16-generic -1
  Removing linux-restricted-modules-2.6.24-16-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-18-386
Package linux-restricted-modules-2.6.24-18-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-18-386 -1
  Removing linux-restricted-modules-2.6.24-18-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-23-386
Package linux-restricted-modules-2.6.24-23-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-23-386 -1
  Removing linux-restricted-modules-2.6.24-23-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-19-generic
Package linux-restricted-modules-2.6.24-19-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-19-generic -1
  Removing linux-restricted-modules-2.6.24-19-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-24-generic
Package linux-restricted-modules-2.6.24-24-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-24-generic -1
  Removing linux-restricted-modules-2.6.24-24-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-27-generic
Package linux-restricted-modules-2.6.24-27-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-27-generic -1
  Removing linux-restricted-modules-2.6.24-27-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-27-386
Package linux-restricted-modules-2.6.24-27-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-27-386 -1
  Removing linux-restricted-modules-2.6.24-27-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-22-generic
Package linux-restricted-modules-2.6.24-22-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-22-generic -1
  Removing linux-restricted-modules-2.6.24-22-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-17-generic
Package linux-restricted-modules-2.6.24-17-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-17-generic -1
  Removing linux-restricted-modules-2.6.24-17-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-24-386
Package linux-restricted-modules-2.6.24-24-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-24-386 -1
  Removing linux-restricted-modules-2.6.24-24-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-19-386
Package linux-restricted-modules-2.6.24-19-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-19-386 -1
  Removing linux-restricted-modules-2.6.24-19-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-25-generic
Package linux-restricted-modules-2.6.24-25-generic has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-25-generic -1
  Removing linux-restricted-modules-2.6.24-25-generic rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-21-386
Package linux-restricted-modules-2.6.24-21-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-21-386 -1
  Removing linux-restricted-modules-2.6.24-21-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-2.6.24-16-386
Package linux-restricted-modules-2.6.24-16-386 has broken dep on linux-restricted-modules-common
  Considering linux-restricted-modules-common 24 as a solution to linux-restricted-modules-2.6.24-16-386 -1
  Removing linux-restricted-modules-2.6.24-16-386 rather than change linux-restricted-modules-common
Investigating linux-restricted-modules-generic
Package linux-restricted-modules-generic has broken dep on linux-restricted-modules-2.6.24-28-generic
  Considering linux-restricted-modules-2.6.24-28-generic 1 as a solution to linux-restricted-modules-generic -1
  Removing linux-restricted-modules-generic rather than change linux-restricted-modules-2.6.24-28-generic
Investigating linux-restricted-modules-386
Package linux-restricted-modules-386 has broken dep on linux-restricted-modules-2.6.24-28-386
  Considering linux-restricted-modules-2.6.24-28-386 1 as a solution to linux-restricted-modules-386 -1
  Removing linux-restricted-modules-386 rather than change linux-restricted-modules-2.6.24-28-386
Done
Installing libgd2-xpm as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libsdl1.2debian-pulseaudio as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: aisleriot
Installing aisleriot as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: gnome-mahjongg
Installing gnome-mahjongg as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: pm-utils-powersave-policy
Installing pm-utils-powersave-policy as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: quadrapassel
Installing quadrapassel as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Starting
Starting 2
Investigating mythbuntu-desktop
Package mythbuntu-desktop has broken dep on libsdl1.2debian-alsa
  Considering libsdl1.2debian-alsa 2 as a solution to mythbuntu-desktop 0
  Re-Instated libsdl1.2debian-alsa
  Re-Instated mythbuntu-desktop
Investigating libsdl1.2debian-pulseaudio
Package libsdl1.2debian-pulseaudio has broken dep on libsdl1.2debian-alsa
  Considering libsdl1.2debian-alsa 2 as a solution to libsdl1.2debian-pulseaudio 14
  Added libsdl1.2debian-alsa to the remove list
  Considering libsdl1.2debian-alsa 2 as a solution to libsdl1.2debian-pulseaudio 14
  Considering libsdl1.2debian-alsa 2 as a solution to libsdl1.2debian-pulseaudio 14
  Fixing libsdl1.2debian-pulseaudio via remove of libsdl1.2debian-alsa
Investigating mythbuntu-desktop
Package mythbuntu-desktop has broken dep on libsdl1.2debian-alsa
  Considering libsdl1.2debian-alsa 2 as a solution to mythbuntu-desktop 0
  Removing mythbuntu-desktop rather than change libsdl1.2debian-alsa
Done
Installing libsdl1.2debian-alsa as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: xscreensaver
Installing xscreensaver as dep of mythbuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Starting
Starting 2
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libsdl1.2debian-pulseaudio
  Considering libsdl1.2debian-pulseaudio 2 as a solution to ubuntu-desktop 0
  Re-Instated libsdl1.2debian-pulseaudio
  Re-Instated ubuntu-desktop
Investigating libsdl1.2debian-alsa
Package libsdl1.2debian-alsa has broken dep on libsdl1.2debian-pulseaudio
  Considering libsdl1.2debian-pulseaudio 2 as a solution to libsdl1.2debian-alsa 15
  Added libsdl1.2debian-pulseaudio to the remove list
  Considering libsdl1.2debian-pulseaudio 2 as a solution to libsdl1.2debian-alsa 15
  Fixing libsdl1.2debian-alsa via keep of libsdl1.2debian-pulseaudio
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libsdl1.2debian-pulseaudio
  Considering libsdl1.2debian-pulseaudio 2 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libsdl1.2debian-pulseaudio
Done
Log time: 2010-08-08 10:28:50.785510

How can I get around this and continue the upgrade?

---

### Post by earthpigg on 2010-08-14
> **teanick said:**
> 
How can I get around this and continue the upgrade?

```
sudo apt-get install ubuntu-desktop
```

then try the upgrade

---

### Post by teanick on 2010-08-14
It didn't work. I still have the same "could not calculate the upgrade" error message.

---

### Post by mörgæs on 2010-08-15
I would always prefer a clean installation, but if you want to stick to the upgrade, you could try this:

[http://ubuntuforums.org/archive/index.php/t-764452.html](http://ubuntuforums.org/archive/index.php/t-764452.html)

---

### Post by Ginsu543 on 2010-08-15
You can't go directly from 8.04 LTS to 10.04 LTS in one upgrade. There have been significant changes made in 10.04 that an upgrade from 8.04 is recipe for disaster (I exaggerate, but still).

As has been mentioned, I recommend you do a clean install of 10.04 LTS after backing up your data.

---

### Post by theDaveTheRave on 2010-10-28
Hi all,

I hate to 'resurect' this thread.

I've just upgraded from 8.04 to 10.04

I have a major issue with a running version of MySQL server and all the stuff that hooks into it (Drupal, Sugar, Test web site -read php / jsp).

Surely an upgrade from one LTS to the next shouldn't break these things.

What I liked about ubuntu is that when you did an upgrade you where fairly sure that everything would still work when you finished. If it didn't it would be well documented with easy to follow workarounds.

As always I have done my upgrade 4 - 5 months after the official release, and I find that although there has been a fix to the mysql problems they aren't working in my instance.

I don't mind having to do a fresh install, I just didn't want to have to!

I've now spent too long out of my life trying to get the solutions to work. I'm just lucky I have the time to spend on it, but I should really be doing other things :mad:

I do remember that last time I installed MySQL I had a similar bad experience, and ended up installing from source....

Maybe that will be my best solution?

for now I'm still testing the solution from bug#551130 (post 16) over on launchpad.

David

---

