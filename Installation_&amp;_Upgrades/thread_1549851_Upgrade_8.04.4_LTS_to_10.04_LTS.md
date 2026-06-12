---
title: "Upgrade 8.04.4 LTS to 10.04 LTS"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by jverdeyen on 2010-08-10
When upgrading from Ubuntu 8.04.4 LTS into 10.04 LTS I get the following errors:

```

sudo do-release-upgrade --proposed
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
tar: Removing leading `/' from member names

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
No candidate ver:  jabberd2
No candidate ver:  libtonezone2.0
No candidate ver:  virtualbox-3.1
No candidate ver:  dahdi-linux
No candidate ver:  timevault

Updating repository information
WARNING: Failed to read mirror file
Done downloading            

Checking package manager
Reading package lists: Donem lucid-proposed/universe Packages: 95     
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists: Donem hardy-proposed/universe Packages: 95     
Reading state information: Done
Reading state information: Done
Reading state information: Done

```

And these are my log files:
APT.LOG
```

Log time: 2010-08-10 13:18:21.792440
Log time: 2010-08-10 13:18:22.666043
Log time: 2010-08-10 13:18:33.162317
Installing libc6 as dep of x11-apps
Installing libc-bin as dep of libc6
Installing findutils as dep of libc6
Installing libmcpp0 as dep of mcpp
Installing libio-compress-perl as dep of libio-compress-base-perl
Installing libcompress-raw-bzip2-perl as dep of libio-compress-perl
Installing perl as dep of libcompress-raw-bzip2-perl
Installing perl-base as dep of perl
Installing dpkg as dep of perl-base
Installing libuuid-perl as dep of doc-base
Installing libuuid1 as dep of libuuid-perl
Installing libmldbm-perl as dep of doc-base
Installing libfreezethaw-perl as dep of libmldbm-perl
Installing perl-modules as dep of perl
Installing libdb4.8 as dep of perl
Installing libcompress-raw-zlib-perl as dep of libio-compress-perl
Installing light-themes as dep of ubuntu-artwork
Installing ubuntu-mono as dep of light-themes
Installing humanity-icon-theme as dep of ubuntu-mono
Installing gtk2-engines-murrine as dep of light-themes
Installing libatk1.0-0 as dep of gtk2-engines-murrine
Installing libfontconfig1 as dep of gtk2-engines-murrine
Installing fontconfig-config as dep of libfontconfig1
Installing libglib2.0-0 as dep of gtk2-engines-murrine
Installing libpcre3 as dep of libglib2.0-0
Installing libgtk2.0-0 as dep of gtk2-engines-murrine
Installing libcairo2 as dep of libgtk2.0-0
Installing libdirectfb-1.2-0 as dep of libcairo2
Installing libts-0.0-0 as dep of libdirectfb-1.2-0
Installing tsconf as dep of libts-0.0-0
Installing libpixman-1-0 as dep of libcairo2
Installing libxcb-render-util0 as dep of libcairo2
Installing libxcb-render0 as dep of libxcb-render-util0
Installing libcups2 as dep of libgtk2.0-0
Installing libgssapi-krb5-2 as dep of libcups2
Installing libk5crypto3 as dep of libgssapi-krb5-2
Installing libkrb5support0 as dep of libk5crypto3
Installing libkrb5-3 as dep of libgssapi-krb5-2
Installing libxrandr2 as dep of libgtk2.0-0
Installing adium-theme-ubuntu as dep of ubuntu-artwork
Installing libmono-security2.0-cil as dep of libmono-data-tds2.0-cil
Installing libmono-system2.0-cil as dep of libmono-security2.0-cil
Installing mono-runtime as dep of libmono-system2.0-cil
Installing mono-gac as dep of mono-runtime
Installing mono-2.0-gac as dep of mono-gac
Installing libtalloc2 as dep of libsmbclient
Installing libhfsp0 as dep of libhfsp-dev
Installing libbsd0 as dep of libedit2
Installing language-pack-nl as dep of language-pack-nl-base
Installing libiec61883-0 as dep of libfreebob0
Installing libraw1394-11 as dep of libiec61883-0
Installing libstdc++6 as dep of libfreebob0
Installing gcc-4.4-base as dep of libstdc++6
Installing libsm6 as dep of libsm-dev
Installing perl-tk as dep of libtk-tablematrix-perl
Installing python as dep of python-gnome2
Installing python2.6 as dep of python
Installing python2.6-minimal as dep of python2.6
Installing libssl0.9.8 as dep of python2.6-minimal
Installing libreadline6 as dep of python2.6
Installing libsqlite3-0 as dep of python2.6
Installing python-minimal as dep of python
Installing python-gobject as dep of python-gnome2
Installing python-support as dep of python-gobject
Installing libffi5 as dep of python-gobject
Installing python-gnomecanvas as dep of python-gnome2
Installing python-gtk2 as dep of python-gnome2
Installing python-cairo as dep of python-gtk2
Installing libpango1.0-0 as dep of python-gtk2
Installing libpango1.0-common as dep of libpango1.0-0
Installing libthai0 as dep of libpango1.0-0
Installing libdatrie1 as dep of libthai0
Installing libthai-data as dep of libthai0
Installing python-pyorbit as dep of python-gnome2
Installing libgconf2-4 as dep of python-gnome2
Installing libdbus-glib-1-2 as dep of libgconf2-4
Installing libxml2 as dep of libgconf2-4
Installing gconf2-common as dep of libgconf2-4
Installing libpopt0 as dep of python-gnome2
Installing python-gconf as dep of python-gnome2
Installing libsoup-gnome2.4-1 as dep of libgweather1
Installing libproxy0 as dep of libsoup-gnome2.4-1
Installing libsoup2.4-1 as dep of libsoup-gnome2.4-1
Installing libgweather-common as dep of libgweather1
Installing openssh-client as dep of openssh-server
Installing libappindicator0 as dep of gnome-power-manager
Installing libdbusmenu-glib1 as dep of libappindicator0
Installing libdbusmenu-gtk1 as dep of libappindicator0
Installing libindicator0 as dep of libappindicator0
Installing libjson-glib-1.0-0 as dep of libappindicator0
Installing indicator-application as dep of libappindicator0
Installing libcanberra-gtk0 as dep of gnome-power-manager
Installing libcanberra0 as dep of libcanberra-gtk0
Installing libasound2 as dep of libcanberra0
Installing libpython2.6 as dep of libasound2
Installing libltdl7 as dep of libcanberra0
Installing libtdb1 as dep of libcanberra0
Installing libcanberra-gtk-module as dep of libcanberra-gtk0
Installing libdevkit-power-gobject1 as dep of gnome-power-manager
Installing libnotify1 as dep of gnome-power-manager
Installing libunique-1.0-0 as dep of gnome-power-manager
Installing upower as dep of gnome-power-manager
Installing libgudev-1.0-0 as dep of upower
Installing libudev0 as dep of libgudev-1.0-0
Installing libpolkit-gobject-1-0 as dep of upower
Installing libeggdbus-1-0 as dep of libpolkit-gobject-1-0
Installing libupower-glib1 as dep of upower
Installing policykit-1 as dep of upower
Installing libpolkit-backend-1-0 as dep of policykit-1
new important dependency: udisks
Installing udisks as dep of gnome-power-manager
Installing libatasmart4 as dep of udisks
Installing libparted0debian1 as dep of udisks
Installing libblkid1 as dep of libparted0debian1
Installing libdevmapper1.02.1 as dep of libparted0debian1
Installing libsgutils2-2 as dep of udisks
Installing mtools as dep of udisks
Installing gnome-settings-daemon as dep of gnome-session
Installing libgnome-desktop-2-17 as dep of gnome-settings-daemon
Installing libstartup-notification0 as dep of libgnome-desktop-2-17
Installing libxcb-atom1 as dep of libstartup-notification0
Installing libxcb-aux0 as dep of libstartup-notification0
Installing libxcb-event1 as dep of libstartup-notification0
Installing libebook1.2-9 as dep of gnome-control-center
Installing libcamel1.2-14 as dep of libebook1.2-9
Installing libedataserver1.2-11 as dep of libcamel1.2-14
Installing libgnome-menu2 as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libgnomekbd4 as dep of gnome-control-center
Installing libxklavier16 as dep of libgnomekbd4
Installing libgnomekbd-common as dep of libgnomekbd4
Installing libmetacity-private0 as dep of gnome-control-center
Installing metacity-common as dep of libmetacity-private0
Installing librsvg2-2 as dep of gnome-control-center
Installing libcroco3 as dep of librsvg2-2
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libxi6 as dep of gnome-control-center
Installing libx11-6 as dep of libxi6
Installing libxcb1 as dep of libx11-6
Installing capplets-data as dep of gnome-control-center
Installing gnome-icon-theme as dep of gnome-control-center
Installing ubuntu-system-service as dep of gnome-control-center
Installing python-central as dep of ubuntu-system-service
new important dependency: policykit-1-gnome
Installing policykit-1-gnome as dep of gnome-control-center
Installing libpolkit-agent-1-0 as dep of policykit-1-gnome
new important dependency: screen-resolution-extra
Installing screen-resolution-extra as dep of gnome-control-center
Installing python-xkit as dep of screen-resolution-extra
Installing libpulse-mainloop-glib0 as dep of gnome-settings-daemon
Installing libpulse0 as dep of libpulse-mainloop-glib0
Installing libsndfile1 as dep of libpulse0
Installing gnome-session-bin as dep of gnome-session
Installing upstart as dep of udev
Installing libdbus-1-3 as dep of upstart
Installing libnih-dbus1 as dep of upstart
Installing libnih1 as dep of libnih-dbus1
Installing sysvinit-utils as dep of upstart
Installing mountall as dep of upstart
Installing plymouth as dep of mountall
Installing libdrm-intel1 as dep of plymouth
Installing libdrm2 as dep of libdrm-intel1
Installing libdrm-nouveau1 as dep of plymouth
Installing libdrm-radeon1 as dep of plymouth
Installing libplymouth2 as dep of plymouth
Installing plymouth-theme-ubuntu-text as dep of plymouth
Installing coreutils as dep of mountall
Installing ifupdown as dep of upstart
Installing netbase as dep of ifupdown
Installing initramfs-tools as dep of udev
Installing initramfs-tools-bin as dep of initramfs-tools
Installing klibc-utils as dep of initramfs-tools
Installing libklibc as dep of klibc-utils
Installing busybox-initramfs as dep of initramfs-tools
Installing util-linux as dep of initramfs-tools
Installing xserver-xorg-core as dep of xserver-xorg
Installing xserver-common as dep of xserver-xorg-core
Installing libpciaccess0 as dep of xserver-xorg-core
new important dependency: libgl1-mesa-dri
Installing libgl1-mesa-dri as dep of xserver-xorg-core
Installing xserver-xorg-video-all as dep of xserver-xorg
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
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
new important dependency: intel-gpu-tools
Installing intel-gpu-tools as dep of xserver-xorg-video-intel
Installing xserver-xorg-video-mga as dep of xserver-xorg-video-all
Installing xserver-xorg-video-neomagic as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nouveau as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nv as dep of xserver-xorg-video-all
Installing xserver-xorg-video-rendition as dep of xserver-xorg-video-all
Installing xserver-xorg-video-s3 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-s3virge as dep of xserver-xorg-video-all
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
Installing xserver-xorg-video-v4l as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vmware as dep of xserver-xorg-video-all
Installing xserver-xorg-input-all as dep of xserver-xorg
Installing xserver-xorg-input-evdev as dep of xserver-xorg-input-all
Installing xserver-xorg-input-synaptics as dep of xserver-xorg-input-all
Installing xserver-xorg-input-vmmouse as dep of xserver-xorg-input-all
Installing xserver-xorg-input-mouse as dep of xserver-xorg-input-vmmouse
Installing xserver-xorg-input-wacom as dep of xserver-xorg-input-all
Installing xkb-data as dep of xserver-xorg
Installing libruby1.8 as dep of ruby1.8-dev
Installing libgconf2.0-cil as dep of tomboy
Installing libglib2.0-cil as dep of libgconf2.0-cil
Installing libgmime2.4-cil as dep of tomboy
Installing libgmime-2.4-2 as dep of libgmime2.4-cil
Installing libgnome2.24-cil as dep of tomboy
Installing libart2.0-cil as dep of libgnome2.24-cil
Installing libglade2.0-cil as dep of libgnome2.24-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libmono-cairo2.0-cil as dep of libgtk2.0-cil
Installing libgnome-vfs2.0-cil as dep of libgnome2.24-cil
Installing libgnomepanel2.24-cil as dep of tomboy
Installing liblaunchpad-integration1.0-cil as dep of tomboy
Installing libmono-addins-gui0.2-cil as dep of tomboy
Installing libmono-addins0.2-cil as dep of libmono-addins-gui0.2-cil
Installing libmono-posix2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libbz2-1.0 as dep of bzip2
Installing libespeak1 as dep of espeak
Installing libportaudio2 as dep of libespeak1
Installing libjack0 as dep of libportaudio2
Installing espeak-data as dep of libespeak1
Installing libidn11 as dep of kdelibs4c2a
Installing libilmbase6 as dep of kdelibs4c2a
Installing libopenexr6 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing kdelibs5-data as dep of kdelibs-data
Installing busybox-static as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: apt-transport-https
Installing apt-transport-https as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing apt as dep of apt-transport-https
new important dependency: irqbalance
Installing irqbalance as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcap-ng0 as dep of irqbalance
Installing cpu-checker as dep of update-notifier-common
new important dependency: libpam-modules
Installing libpam-modules as dep of update-notifier-common
Installing base-files as dep of libpam-modules
Installing libselinux1 as dep of libpam-modules
new important dependency: libgpm2
Installing libgpm2 as dep of libncurses5
Installing kdebase-runtime as dep of kipi-plugins
Installing kdelibs5 as dep of kdebase-runtime
Installing libattica0 as dep of kdelibs5
Installing libqt4-network as dep of libattica0
Installing libqtcore4 as dep of libqt4-network
Installing libdbusmenu-qt2 as dep of kdelibs5
Installing libqt4-dbus as dep of libdbusmenu-qt2
Installing libqt4-xml as dep of libqt4-dbus
Installing libqtgui4 as dep of libdbusmenu-qt2
Installing libenchant1c2a as dep of kdelibs5
Installing libhunspell-1.2-0 as dep of libenchant1c2a
Installing hunspell-en-us as dep of libhunspell-1.2-0
Installing liblzma1 as dep of kdelibs5
Installing libphonon4 as dep of kdelibs5
Installing libqt4-designer as dep of libphonon4
Installing libqt4-script as dep of libqt4-designer
Installing libpolkit-qt-1-0 as dep of kdelibs5
Installing libqt4-qt3support as dep of kdelibs5
Installing libqt4-sql as dep of libqt4-qt3support
Installing libqt4-sql-mysql as dep of libqt4-sql
Installing libmysqlclient16 as dep of libqt4-sql-mysql
Installing mysql-common as dep of libmysqlclient16
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
Installing libstreamanalyzer0 as dep of kdelibs5
Installing libexiv2-6 as dep of libstreamanalyzer0
Installing exiv2 as dep of libexiv2-6
Installing libstreams0 as dep of libstreamanalyzer0
Installing kdelibs-bin as dep of kdelibs5
Installing shared-desktop-ontologies as dep of kdelibs5
Installing libplasma3 as dep of kdebase-runtime
Installing libqca2 as dep of libplasma3
Installing ca-certificates as dep of libqca2
Installing libqt4-opengl as dep of libplasma3
Installing libssh-4 as dep of kdebase-runtime
Installing kdebase-runtime-data as dep of kdebase-runtime
Installing oxygen-icon-theme as dep of kdebase-runtime
Installing phonon-backend-xine as dep of kdebase-runtime
Installing libxine1 as dep of phonon-backend-xine
Installing libxine1-misc-plugins as dep of libxine1
Installing libmagickcore2 as dep of libxine1-misc-plugins
Installing libmagickwand2 as dep of libxine1-misc-plugins
Installing libmodplug0c2 as dep of libxine1-misc-plugins
Installing libspeex1 as dep of libxine1-misc-plugins
Installing libxine1-bin as dep of libxine1-misc-plugins
Installing libxine1-x as dep of libxine1
Installing libxcb-shape0 as dep of libxine1-x
Installing libxcb-shm0 as dep of libxine1-x
Installing libxcb-xv0 as dep of libxine1-x
Installing libxine1-console as dep of libxine1
Installing libcaca0 as dep of libxine1-console
Installing plasma-scriptengine-javascript as dep of kdebase-runtime
Installing icoutils as dep of kdebase-runtime
Installing kubuntu-debug-installer as dep of kdebase-runtime
Installing kpackagekit as dep of kubuntu-debug-installer
Installing libpackagekit-qt-12 as dep of kpackagekit
Installing polkit-kde-1 as dep of kpackagekit
Installing software-properties-kde as dep of kpackagekit
Installing python-qt4 as dep of software-properties-kde
Installing libqt4-assistant as dep of python-qt4
Installing libqt4-help as dep of python-qt4
Installing libqt4-scripttools as dep of python-qt4
Installing libqt4-test as dep of python-qt4
Installing python-sip as dep of python-qt4
Installing python-kde4 as dep of software-properties-kde
Installing kdepimlibs5 as dep of python-kde4
Installing libakonadiprivate1 as dep of kdepimlibs5
Installing libboost-program-options1.40.0 as dep of libakonadiprivate1
Installing libgpg-error0 as dep of kdepimlibs5
Installing libgpgme11 as dep of kdepimlibs5
Installing libical0 as dep of kdepimlibs5
Installing kdepimlibs-data as dep of kdepimlibs5
Installing phonon as dep of python-kde4
Installing install-package as dep of software-properties-kde
Installing gdebi-kde as dep of install-package
Installing gdebi-core as dep of gdebi-kde
Installing python-debian as dep of gdebi-core
Installing kdesudo as dep of gdebi-kde
Installing packagekit as dep of kpackagekit
Installing libnm-glib2 as dep of packagekit
Installing libnm-util1 as dep of libnm-glib2
Installing libgnome-bluetooth7 as dep of network-manager-gnome
Installing network-manager as dep of network-manager-gnome
Installing wpasupplicant as dep of network-manager
Installing libpcsclite1 as dep of wpasupplicant
new important dependency: dnsmasq-base
Installing dnsmasq-base as dep of network-manager
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
Installing libgpod4 as dep of kipi-plugins
Installing libimobiledevice0 as dep of libgpod4
Installing libplist1 as dep of libimobiledevice0
Installing libtasn1-3 as dep of libimobiledevice0
Installing libusbmuxd1 as dep of libimobiledevice0
Installing usbmuxd as dep of libimobiledevice0
Installing libusb-1.0-0 as dep of usbmuxd
Installing libkdcraw8 as dep of kipi-plugins
Installing libkexiv2-8 as dep of kipi-plugins
Installing libkipi7 as dep of kipi-plugins
Installing libksane0 as dep of kipi-plugins
Installing libsane as dep of libksane0
Installing libgphoto2-2 as dep of libsane
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libieee1284-3 as dep of libsane
Installing libv4l-0 as dep of libsane
Installing cups as dep of openprinting-ppds
Installing libcupscgi1 as dep of cups
Installing libcupsdriver1 as dep of cups
Installing libcupsimage2 as dep of cups
Installing libcupsmime1 as dep of cups
Installing libcupsppdc1 as dep of cups
Installing libijs-0.35 as dep of cups
Installing libpoppler5 as dep of cups
Installing libslp1 as dep of cups
Installing poppler-utils as dep of cups
Installing cups-common as dep of cups
Installing cups-client as dep of cups
Installing foomatic-filters as dep of cups
Installing cups-driver-gutenprint as dep of cups
Installing libgutenprint2 as dep of cups-driver-gutenprint
Installing ghostscript-cups as dep of cups-driver-gutenprint
Installing ghostscript as dep of ghostscript-cups
Installing libgs8 as dep of ghostscript
new important dependency: libxml-sax-expat-perl
Installing libxml-sax-expat-perl as dep of libxml-sax-perl
new important dependency: ttf-sazanami-mincho
Installing ttf-sazanami-mincho as dep of ttf-kochi-mincho
Installing console-terminus as dep of console-setup
Installing kbd as dep of console-setup
Installing libice6 as dep of libice-dev
Installing python-twisted-core as dep of python-twisted-mail
Installing python-twisted-bin as dep of python-twisted-core
Installing python-zope.interface as dep of python-twisted-core
Installing python-pkg-resources as dep of python-zope.interface
new important dependency: python-openssl
Installing python-openssl as dep of python-twisted-core
Installing x11proto-randr-dev as dep of libxrandr-dev
Installing libgstreamer-plugins-base0.10-0 as dep of gnome-media
Installing libgstreamer0.10-0 as dep of libgstreamer-plugins-base0.10-0
Installing libmono-data-tds1.0-cil as dep of libmono-system-data1.0-cil
Installing libmono-security1.0-cil as dep of libmono-data-tds1.0-cil
Installing libpolkit2 as dep of libpolkit-dbus2
Installing compiz-core as dep of compiz-gnome
Installing libprotobuf5 as dep of libcompizconfig0
Installing compiz-plugins as dep of compiz-gnome
Installing libexempi3 as dep of nautilus
Installing libnautilus-extension1 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing shared-mime-info as dep of nautilus
Installing gvfs as dep of nautilus
Installing libgdu0 as dep of gvfs
Installing libgvfscommon0 as dep of gvfs
Installing libglib2.0-data as dep of nautilus
Installing libmono-posix1.0-cil as dep of libmono1.0-cil
Installing libexpat1 as dep of libexpat1-dev
Installing libcdio10 as dep of libcdio-paranoia0
Installing libesd0 as dep of libgnome2-0
Installing esound-common as dep of libesd0
new important dependency: esound-clients
Installing esound-clients as dep of esound-common
Installing libgnome2-common as dep of libgnome2-0
Installing libcdparanoia0 as dep of cdparanoia
Installing librrds-perl as dep of munin
Installing librrd4 as dep of librrds-perl
Installing liblog-log4perl-perl as dep of munin
Installing munin-common as dep of munin
Installing libglib2.0-dev as dep of gnome-settings-daemon-dev
Installing libbind9-60 as dep of bind9-host
Installing libdns64 as dep of libbind9-60
Installing libgeoip1 as dep of libdns64
Installing geoip-database as dep of libgeoip1
Installing libisc60 as dep of libdns64
Installing libisccfg60 as dep of libbind9-60
Installing libisccc60 as dep of libisccfg60
Installing liblwres60 as dep of bind9-host
Installing swi-prolog as dep of swi-prolog-http
Installing libgmp3-dev as dep of swi-prolog
Installing libgmp3c2 as dep of libgmp3-dev
Installing libgmpxx4ldbl as dep of libgmp3-dev
Installing libreadline-dev as dep of swi-prolog
Installing libreadline6-dev as dep of libreadline-dev
Installing libncurses5-dev as dep of libreadline6-dev
Installing libgamin0 as dep of gamin
Installing dpkg-dev as dep of debhelper
Installing xz-utils as dep of dpkg-dev
Installing libaspell15 as dep of aspell
Installing libuniconf4.6 as dep of wvdial
Installing libwvstreams4.6-base as dep of libuniconf4.6
Installing libwvstreams4.6-extras as dep of libuniconf4.6
Installing ruby1.8 as dep of irb1.8
Installing libreadline-ruby1.8 as dep of irb1.8
Installing libxdamage1 as dep of libxdamage-dev
Installing libpoppler-glib4 as dep of tracker
Installing libtotem-plparser17 as dep of tracker
new important dependency: odt2txt
Installing odt2txt as dep of tracker
Installing libzip1 as dep of odt2txt
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing samba-common as dep of smbclient
Installing libnewt0.52 as dep of whiptail
Installing liblua5.1-0 as dep of nmap
Installing libpcap0.8 as dep of nmap
Installing linux-image-server as dep of linux-server
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing linux-image-2.6.32-24-server as dep of linux-image-server
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing wireless-crda as dep of linux-image-2.6.32-24-server
Installing linux-firmware as dep of linux-image-server
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libgucharmap7 as dep of gucharmap
Installing libatspi1.0-0 as dep of brltty-x11
Installing brltty as dep of brltty-x11
Installing libicu42 as dep of brltty
Installing totem as dep of totem-plugins
Installing gstreamer0.10-plugins-base as dep of totem
Installing libtheora0 as dep of gstreamer0.10-plugins-base
Installing totem-common as dep of totem
Installing totem-mozilla as dep of totem
Installing libbluetooth3 as dep of totem-plugins
Installing libgdata6 as dep of totem-plugins
Installing libgdata-common as dep of libgdata6
Installing python-rdflib as dep of totem-plugins
Installing python-httplib2 as dep of totem-plugins
Installing python-gnomeapplet as dep of computertemp
Installing tk as dep of x11vnc
Installing tcl as dep of tk
Installing software-center as dep of gnome-app-install
Installing python-aptdaemon as dep of software-center
Installing aptdaemon as dep of python-aptdaemon
Installing python-aptdaemon-gtk as dep of software-center
Installing python-webkit as dep of software-center
Installing libwebkit-1.0-2 as dep of python-webkit
Installing libwebkit-1.0-common as dep of libwebkit-1.0-2
Installing libspeexdsp1 as dep of pulseaudio
Installing libasound2-plugins as dep of pulseaudio
new important dependency: rtkit
Installing rtkit as dep of pulseaudio
Installing libgnomeui-common as dep of libgnomeui-0
new important dependency: obex-data-server
Installing obex-data-server as dep of gvfs-backends
Installing libopenobex1 as dep of obex-data-server
Installing libglib-perl as dep of libgtk2-perl
Installing libpango-perl as dep of libgtk2-perl
Installing libossp-uuid16 as dep of libossp-uuid-perl
Installing python-twisted-web as dep of python-twisted-lore
new important dependency: libmono-i18n-west2.0-cil
Installing libmono-i18n-west2.0-cil as dep of libmono-corlib2.0-cil
Installing policykit as dep of policykit-gnome
Installing libcairomm-1.0-1 as dep of libgtkmm-2.4-1c2a
Installing libglibmm-2.4-1c2a as dep of libgtkmm-2.4-1c2a
Installing libpangomm-1.4-1 as dep of libgtkmm-2.4-1c2a
Installing odbcinst as dep of odbcinst1debian1
Installing lynx-cur as dep of lynx
Installing libfile-copy-recursive-perl as dep of update-inetd
Installing libavcodec52 as dep of libquicktime1
Installing libavutil49 as dep of libavcodec52
Installing libgsm1 as dep of libavcodec52
Installing libschroedinger-1.0-0 as dep of libavcodec52
Installing liboil0.3 as dep of libschroedinger-1.0-0
Installing libfaad2 as dep of libquicktime1
Installing libswscale0 as dep of libquicktime1
Installing libapache2-mod-php5 as dep of php5
Installing php5-common as dep of libapache2-mod-php5
Installing at-spi as dep of python-pyatspi
Installing libevent-1.4-2 as dep of transmission-cli
Installing transmission-common as dep of transmission-cli
Installing rubygems1.8 as dep of rubygems
Installing mesa-common-dev as dep of libgl1-mesa-dev
Installing libdrm-dev as dep of mesa-common-dev
Installing linux-libc-dev as dep of libdrm-dev
Installing e2fslibs as dep of testdisk
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing python-gtksourceview2 as dep of gedit
Installing libcryptui0 as dep of seahorse
Installing libgnome-keyring0 as dep of seahorse
Installing libgcr0 as dep of gnome-keyring
Installing libgp11-0 as dep of libgcr0
Installing gnupg as dep of seahorse
new important dependency: gnupg-curl
Installing gnupg-curl as dep of gnupg
Installing python-gmenu as dep of gnome-menus
Installing python-xdg as dep of python-gmenu
Installing readahead-fedora as dep of readahead
Installing libaudit0 as dep of readahead-fedora
Installing libvte9 as dep of gnome-terminal
Installing gnome-terminal-data as dep of gnome-terminal
Installing libcrack2 as dep of netatalk
Installing cracklib-runtime as dep of libcrack2
Installing wamerican as dep of cracklib-runtime
new important dependency: db4.8-util
Installing db4.8-util as dep of netatalk
Installing xml-core as dep of docbook-xml
Installing libvorbis0a as dep of libvorbis-dev
Installing libvorbisenc2 as dep of libvorbis-dev
Installing libvorbisfile3 as dep of libvorbis-dev
Installing libxinerama1 as dep of libxinerama-dev
Installing libavformat52 as dep of mplayer
Installing libdvdread4 as dep of mplayer
Installing libmp3lame0 as dep of mplayer
Installing libopenal1 as dep of mplayer
Installing libpostproc51 as dep of mplayer
Installing libx264-85 as dep of mplayer
new important dependency: byobu
Installing byobu as dep of screen
Installing python-newt as dep of byobu
Installing libyaml-syck-perl as dep of libdate-manip-perl
Installing x11proto-input-dev as dep of libxi-dev
Installing python-pyasn1 as dep of python-twisted-conch
Installing libept0 as dep of aptitude
Installing xserver-xorg-video-openchrome as dep of xserver-xorg-video-via
Installing xmltv-util as dep of xmltv-gui
Installing libxml-dom-perl as dep of xmltv-util
Installing libxml-perl as dep of libxml-dom-perl
Installing libxml-regexp-perl as dep of libxml-dom-perl
Installing libxml-libxslt-perl as dep of xmltv-util
Installing libxml-libxml-perl as dep of libxml-libxslt-perl
Installing libdatetime-format-strptime-perl as dep of xmltv-util
Installing libdatetime-perl as dep of libdatetime-format-strptime-perl
Installing libdatetime-locale-perl as dep of libdatetime-perl
Installing liblist-moreutils-perl as dep of libdatetime-locale-perl
Installing libparams-validate-perl as dep of libdatetime-locale-perl
Installing libdatetime-timezone-perl as dep of libdatetime-perl
Installing libclass-singleton-perl as dep of libdatetime-timezone-perl
Installing python2.6-dev as dep of python-dev
new important dependency: xinput
Installing xinput as dep of acpi-support
Installing libgdiplus as dep of libmono-system-web1.0-cil
Installing libsvn1 as dep of subversion
Installing libaprutil1 as dep of libsvn1
Installing apache2.2-bin as dep of apache2.2-common
Installing libaprutil1-dbd-sqlite3 as dep of apache2.2-bin
Installing libaprutil1-ldap as dep of apache2.2-bin
Installing libneon27-gnutls as dep of libsvn1
Installing libscim8c2a as dep of scim
Installing krb5-multidev as dep of libkrb5-dev
Installing libgssrpc4 as dep of krb5-multidev
Installing libkadm5srv-mit7 as dep of krb5-multidev
Installing libkdb5-4 as dep of libkadm5srv-mit7
Installing libkadm5clnt-mit7 as dep of krb5-multidev
Installing python-apport as dep of apport
Installing python-launchpadlib as dep of python-apport
Installing python-simplejson as dep of python-launchpadlib
Installing libjs-jquery as dep of python-simplejson
Installing python-wadllib as dep of python-launchpadlib
Installing python-lazr.uri as dep of python-wadllib
Installing python-lazr.restfulclient as dep of python-launchpadlib
Installing python-oauth as dep of python-launchpadlib
new important dependency: apport-symptoms
Installing apport-symptoms as dep of apport
Installing cpp as dep of g++
Installing cpp-4.4 as dep of cpp
Installing libmpfr1ldbl as dep of cpp-4.4
Installing gcc as dep of g++
Installing gcc-4.4 as dep of gcc
Installing binutils as dep of gcc-4.4
Installing libgcc1 as dep of gcc-4.4
Installing g++-4.4 as dep of g++
Installing libstdc++6-4.4-dev as dep of g++-4.4
Installing netcat-openbsd as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing rsyslog as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing ureadahead as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libavahi-client3 as dep of libavahi-client-dev
Installing libogg0 as dep of libogg-dev
Installing python-twisted-names as dep of python-twisted
Installing python-twisted-runner as dep of python-twisted
Installing sun-java6-jre as dep of sun-java6-bin
Installing checkbox-gtk as dep of hwtest-gtk
Installing checkbox as dep of checkbox-gtk
Installing libgd2-xpm as dep of php5-gd
Installing libdb4.8-dev as dep of libdb-dev
Installing libcurl3 as dep of libcurl4-openssl-dev
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libtag1-vanilla as dep of libtag1c2a
Installing libcupsys2 as dep of libcupsys2-dev
Installing update-manager-core as dep of update-manager
new important dependency: software-properties-gtk
Installing software-properties-gtk as dep of update-manager
new important dependency: libltdl-dev
Installing libltdl-dev as dep of libtool
Installing libgdict-1.0-6 as dep of gnome-utils
Installing libpci3 as dep of vbetool
Installing gconf-defaults-service as dep of gconf-editor
Installing libsdl1.2debian as dep of libsdl1.2-dev
Installing libasound2-dev as dep of libsdl1.2-dev
Installing libesd0-dev as dep of libsdl1.2-dev
Installing libaudiofile-dev as dep of libesd0-dev
Installing libaudiofile0 as dep of libaudiofile-dev
Installing libpulse-dev as dep of libsdl1.2-dev
Installing libpulse-browse0 as dep of libpulse-dev
Installing libxt-dev as dep of libpulse-dev
Installing libxt6 as dep of libxt-dev
Installing libdirectfb-dev as dep of libsdl1.2-dev
Installing libdirectfb-extra as dep of libdirectfb-dev
Installing libjpeg62-dev as dep of libdirectfb-dev
Installing libjpeg62 as dep of libjpeg62-dev
Installing libsysfs-dev as dep of libdirectfb-dev
Installing libsysfs2 as dep of libsysfs-dev
Installing libaa1-dev as dep of libsdl1.2-dev
Installing libslang2-dev as dep of libaa1-dev
Installing libslang2 as dep of libslang2-dev
Installing libcaca-dev as dep of libsdl1.2-dev
Installing libaudio-dev as dep of libsdl1.2-dev
Installing libaudio2 as dep of libaudio-dev
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing bluetooth as dep of bluez-utils
Installing bluez as dep of bluetooth
Installing bluez-alsa as dep of bluetooth
Installing bluez-cups as dep of bluetooth
Installing bluez-gstreamer as dep of bluetooth
Installing python-speechd as dep of gnome-orca
Installing speech-dispatcher as dep of python-speechd
Installing libdotconf1.0 as dep of speech-dispatcher
Installing libspeechd2 as dep of speech-dispatcher
Installing python-louis as dep of gnome-orca
Installing liblouis0 as dep of python-louis
Installing liblouis-data as dep of liblouis0
Installing libfaac0 as dep of libfaac-dev
Installing firefox-branding as dep of firefox
Installing libiw30 as dep of wireless-tools
Installing tcl8.5 as dep of python-tk
Installing tk8.5 as dep of python-tk
Installing gnome-desktop-data as dep of gnome-about
Installing libtask-weaken-perl as dep of libsoap-lite-perl
Installing x11proto-xext-dev as dep of x11proto-fixes-dev
Installing libxext6 as dep of libxext-dev
Installing git-core as dep of gitweb
Installing libemail-date-format-perl as dep of libemail-date-perl
Installing diffutils as dep of diff
Installing libwww-perl as dep of libwww-mechanize-perl
Installing libhttp-server-simple-perl as dep of libwww-mechanize-perl
Installing evolution-data-server-common as dep of libedataserverui1.2-8
Installing python-configobj as dep of bzr
new important dependency: smartdimmer
Installing smartdimmer as dep of hal
Installing libglu1-mesa as dep of libglu1-mesa-dev
Installing libmono-system-web2.0-cil as dep of libmono2.0-cil
Installing libmono-sqlite2.0-cil as dep of libmono-system-web2.0-cil
Installing libsqlite0 as dep of libmono-sqlite2.0-cil
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
new important dependency: indicator-applet
Installing indicator-applet as dep of gnome-panel
Installing indicator-messages as dep of indicator-applet
Installing libindicate4 as dep of indicator-messages
Installing indicator-sound as dep of indicator-applet
Installing libido-0.1-0 as dep of indicator-sound
Installing libgnomevfs2-0-dbg as dep of gnome-dbg
Installing libgnomevfs2-0 as dep of libgnomevfs2-0-dbg
Installing libgtk2.0-0-dbg as dep of gnome-dbg
Installing libgnome2-dbg as dep of gnome-dbg
Installing libgnomecanvas2-dbg as dep of gnome-dbg
Installing libgnomeui-0-dbg as dep of gnome-dbg
Installing nautilus-dbg as dep of gnome-dbg
Installing libpango1.0-0-dbg as dep of gnome-dbg
Installing librsvg2-dbg as dep of gnome-dbg
Installing totem-dbg as dep of gnome-dbg
Installing evolution-data-server-dbg as dep of gnome-dbg
Installing evolution-data-server as dep of evolution-data-server-dbg
Installing libebackend1.2-0 as dep of evolution-data-server
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing libegroupwise1.2-13 as dep of evolution-data-server
Installing libgdata-google1.2-1 as dep of evolution-data-server
Installing libgdata1.2-1 as dep of libgdata-google1.2-1
Installing evolution-dbg as dep of gnome-dbg
Installing evolution as dep of evolution-dbg
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgtkhtml-editor0 as dep of evolution
Installing libgtkhtml3.14-19 as dep of libgtkhtml-editor0
Installing libgtkhtml-editor-common as dep of libgtkhtml-editor0
Installing liblpint-bonobo0 as dep of evolution
Installing evolution-common as dep of evolution
Installing evolution-plugins as dep of evolution
Installing libpst4 as dep of evolution-plugins
Installing evolution-webcal as dep of evolution
Installing python-gtk2-dbg as dep of gnome-dbg
Installing python-dbg as dep of python-gtk2-dbg
Installing python2.6-dbg as dep of python-dbg
Installing python-numpy-dbg as dep of python-gtk2-dbg
Installing python-numpy as dep of python-numpy-dbg
Installing libblas3gf as dep of python-numpy
Installing libgfortran3 as dep of libblas3gf
Installing liblapack3gf as dep of python-numpy
Installing python-cairo-dbg as dep of python-gtk2-dbg
Installing python-gobject-dbg as dep of python-gtk2-dbg
Installing libgsf-gnome-1-114-dbg as dep of gnome-dbg
Installing libgsf-gnome-1-114 as dep of libgsf-gnome-1-114-dbg
Installing libgsf-1-114-dbg as dep of libgsf-gnome-1-114-dbg
Installing gstreamer0.10-plugins-base-dbg as dep of gnome-dbg
Installing gstreamer0.10-x as dep of gstreamer0.10-plugins-base-dbg
Installing gstreamer0.10-plugins-good-dbg as dep of gnome-dbg
Installing gstreamer0.10-pulseaudio as dep of gstreamer0.10-plugins-good-dbg
Installing gstreamer0.10-esd as dep of gstreamer0.10-plugins-good-dbg
Installing gstreamer0.10-plugins-ugly-dbg as dep of gnome-dbg
Installing gstreamer0.10-plugins-ugly as dep of gstreamer0.10-plugins-ugly-dbg
Installing libid3tag0 as dep of gstreamer0.10-plugins-ugly
Installing libmad0 as dep of gstreamer0.10-plugins-ugly
Installing libopencore-amrnb0 as dep of gstreamer0.10-plugins-ugly
Installing libopencore-amrwb0 as dep of gstreamer0.10-plugins-ugly
Installing libsidplay1 as dep of gstreamer0.10-plugins-ugly
Installing libgstreamer0.10-0-dbg as dep of gnome-dbg
Installing libgtkhtml3.14-dbg as dep of gnome-dbg
Installing anjuta-dbg as dep of gnome-dbg
Installing anjuta as dep of anjuta-dbg
Installing libdevhelp-1-1 as dep of anjuta
Installing devhelp-common as dep of libdevhelp-1-1
Installing libgda-4.0-4 as dep of anjuta
Installing libgda-4.0-common as dep of libgda-4.0-4
Installing libgdl-1-3 as dep of anjuta
Installing libgladeui-1-9 as dep of anjuta
Installing libvala0 as dep of anjuta
Installing anjuta-common as dep of anjuta
Installing exuberant-ctags as dep of anjuta
Installing autogen as dep of anjuta
Installing guile-1.8-libs as dep of autogen
Installing libopts25 as dep of autogen
Installing libopts25-dev as dep of autogen
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
Installing libavahi-gobject0 as dep of epiphany-browser
Installing libgirepository1.0-0 as dep of epiphany-browser
Installing libseed0 as dep of epiphany-browser
Installing gnome-js-common as dep of libseed0
Installing gir1.0-glib-2.0 as dep of libseed0
Installing gir1.0-clutter-1.0 as dep of libseed0
Installing gir1.0-freedesktop as dep of gir1.0-clutter-1.0
Installing gir1.0-pango-1.0 as dep of gir1.0-clutter-1.0
Installing libclutter-1.0-0 as dep of gir1.0-clutter-1.0
Installing gir1.0-gstreamer-0.10 as dep of libseed0
Installing gir1.0-gtk-2.0 as dep of libseed0
Installing gir1.0-atk-1.0 as dep of gir1.0-gtk-2.0
Installing libwebkit-1.0-2-dbg as dep of epiphany-browser-dbg
Installing eog-dbg as dep of gnome-dbg
Installing libgdl-1-dbg as dep of gnome-dbg
Installing libgda3-3-dbg as dep of gnome-dbg
Installing libgda3-3 as dep of libgda3-3-dbg
Installing libgda3-common as dep of libgda3-3
Installing libloudmouth1-0-dbg as dep of gnome-dbg
Installing libloudmouth1-0 as dep of libloudmouth1-0-dbg
Installing gimp-dbg as dep of gnome-dbg
Installing gimp as dep of gimp-dbg
Installing libgimp2.0 as dep of gimp
Installing gimp-data as dep of libgimp2.0
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
Installing system-tools-backends as dep of liboobs-1-4
Installing libnet-dbus-perl as dep of system-tools-backends
Installing libxft2-dbg as dep of gnome-dbg
Installing libxml2-dbg as dep of gnome-dbg
Installing rhythmbox-dbg as dep of gnome-dbg
Installing rhythmbox as dep of rhythmbox-dbg
Installing media-player-info as dep of rhythmbox
Installing rhythmbox-plugins as dep of rhythmbox
Installing libmtp8 as dep of rhythmbox-plugins
Installing libmusicbrainz4c2a as dep of rhythmbox-plugins
Installing python-mako as dep of rhythmbox-plugins
Installing rhythmbox-plugin-cdrecorder as dep of rhythmbox
Installing libbrasero-media0 as dep of rhythmbox-plugin-cdrecorder
Installing brasero-common as dep of libbrasero-media0
Installing usplash as dep of usplash-theme-ubuntu
new important dependency: sensible-utils
Installing sensible-utils as dep of devscripts
Installing libpam-runtime as dep of cron
Installing scim-modules-socket as dep of scim-gtk2-immodule
new important dependency: fancontrol
Installing fancontrol as dep of lm-sensors
Installing linux-headers-2.6.32-24-generic as dep of linux-headers-generic
Installing linux-headers-2.6.32-24 as dep of linux-headers-2.6.32-24-generic
Installing openssl as dep of ssl-cert
Installing liblame0 as dep of liblame-dev
Installing libavdevice52 as dep of ffmpeg
Installing libdc1394-22 as dep of libavdevice52
Installing libavfilter0 as dep of ffmpeg
Installing zlib1g as dep of zlib1g-dev
Installing hugs as dep of libhugs-haskell98-bundled
Installing libmjpegtools-1.9 as dep of transcode
new important dependency: twolame
Installing twolame as dep of transcode
Installing libmagic1 as dep of file
Installing libxcb-render0-dev as dep of libcairo2-dev
Installing libxcb-render-util0-dev as dep of libcairo2-dev
Installing apturl-common as dep of apturl
Installing libjs-mootools as dep of phpmyadmin
Installing javascript-common as dep of libjs-mootools
Installing wwwconfig-common as dep of javascript-common
Installing libsox1a as dep of sox
Installing libsox-fmt-base as dep of libsox1a
Installing libsox-fmt-alsa as dep of libsox1a
Installing vim-runtime as dep of vim
Installing dhcp3-common as dep of dhcp3-client
Installing libavidemux0 as dep of avidemux-cli
Installing lame as dep of libavidemux0
new important dependency: avidemux-plugins-cli
Installing avidemux-plugins-cli as dep of avidemux-cli
Installing avidemux-plugins-common as dep of avidemux-plugins-cli
Installing xulrunner-1.9.2 as dep of yelp
Installing gnome-doc-utils as dep of yelp
Installing rarian-compat as dep of scrollkeeper
new important dependency: libmono-i18n-west1.0-cil
Installing libmono-i18n-west1.0-cil as dep of libmono-corlib1.0-cil
Installing libgksu2-0 as dep of gksu
Installing python-pycurl as dep of landscape-client
Installing libcurl3-gnutls as dep of python-pycurl
Installing landscape-common as dep of landscape-client
Installing python-smartpm as dep of landscape-common
Installing python-pexpect as dep of python-smartpm
new important dependency: nvidia-common
Installing nvidia-common as dep of jockey-common
Installing nvidia-current-modaliases as dep of nvidia-common
Installing nvidia-173-modaliases as dep of nvidia-common
Installing nvidia-96-modaliases as dep of nvidia-common
new important dependency: fglrx-modaliases
Installing fglrx-modaliases as dep of jockey-common
new important dependency: bcmwl-modaliases
Installing bcmwl-modaliases as dep of jockey-common
Installing conky-all as dep of conky
Installing libimlib2 as dep of conky-all
Installing libc-dev-bin as dep of libc6-dev
Installing manpages-dev as dep of libc-dev-bin
Installing libavahi-core6 as dep of avahi-daemon
Installing libmpg123-0 as dep of mpg123
Installing libbonoboui2-common as dep of libbonoboui2-0
new important dependency: python-appindicator
Installing python-appindicator as dep of jockey-gtk
Installing xorg-docs-core as dep of xorg
new important dependency: hpijs
Installing hpijs as dep of foomatic-db
Installing libhpmud0 as dep of hpijs
Installing libsnmp15 as dep of libhpmud0
Installing libsnmp-base as dep of libsnmp15
Installing libperl5.10 as dep of libsnmp15
new important dependency: lockfile-progs
Installing lockfile-progs as dep of ntpdate
new important dependency: libmagickcore2-extra
Installing libmagickcore2-extra as dep of imagemagick
Installing grub-common as dep of grub
Installing os-prober as dep of grub-common
Installing python-smbc as dep of system-config-printer-common
Installing python-cupshelpers as dep of system-config-printer-common
new important dependency: system-config-printer-udev
Installing system-config-printer-udev as dep of system-config-printer-common
new important dependency: avahi-utils
Installing avahi-utils as dep of system-config-printer-common
Installing install-info as dep of info
Installing p7zip-full as dep of p7zip-rar
Installing insserv as dep of sysv-rc
Installing libavahi-common3 as dep of libavahi-common-dev
Installing gnome-themes-selected as dep of gnome-themes
new important dependency: libnet-libidn-perl
Installing libnet-libidn-perl as dep of libio-socket-ssl-perl
new important dependency: libmime-types-perl
Installing libmime-types-perl as dep of libmime-lite-perl
Installing libntfs-3g75 as dep of ntfs-3g
Installing python-bugbuddy as dep of python-gnome2-desktop
Installing python-evince as dep of python-gnome2-desktop
Installing python-evolution as dep of python-gnome2-desktop
Installing python-gnomedesktop as dep of python-gnome2-desktop
Installing python-gnomekeyring as dep of python-gnome2-desktop
Installing python-gnomeprint as dep of python-gnome2-desktop
Installing python-gtop as dep of python-gnome2-desktop
Installing python-mediaprofiles as dep of python-gnome2-desktop
Installing python-metacity as dep of python-gnome2-desktop
Installing python-rsvg as dep of python-gnome2-desktop
Installing python-totem-plparser as dep of python-gnome2-desktop
Installing python-wnck as dep of python-gnome2-desktop
Installing libuu0 as dep of uudeview
Starting
Starting 2
Investigating libc6
Package libc6 has broken dep on belocs-locales-bin
  Considering belocs-locales-bin -2 as a solution to libc6 11801
  Added belocs-locales-bin to the remove list
  Fixing libc6 via remove of belocs-locales-bin
Investigating libxcb1
Package libxcb1 has broken dep on libxcb-xlib0
  Considering libxcb-xlib0 1 as a solution to libxcb1 425
  Added libxcb-xlib0 to the remove list
  Fixing libxcb1 via remove of libxcb-xlib0
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to libcups2 263
  Added libcupsys2 to the remove list
  Fixing libcups2 via remove of libcupsys2
Investigating libthai0
Package libthai0 has broken dep on libdatrie0
  Considering libdatrie0 -1 as a solution to libthai0 169
  Added libdatrie0 to the remove list
  Fixing libthai0 via remove of libdatrie0
Investigating mono-runtime
Package mono-runtime has broken dep on mono-common
  Considering mono-common 1 as a solution to mono-runtime 145
  Added mono-common to the remove list
Package mono-runtime has broken dep on mono-jit
  Considering mono-jit -1 as a solution to mono-runtime 145
  Added mono-jit to the remove list
  Fixing mono-runtime via remove of mono-common
  Fixing mono-runtime via remove of mono-jit
Investigating xserver-xorg-core
Package xserver-xorg-core has broken dep on xserver-xorg-input-2
  Considering xserver-xorg-input-kbd -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-input-kbd to the remove list
  Considering xserver-xorg-input-mouse 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-input-synaptics 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-input-evdev 4 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-input-wacom 1 as a solution to xserver-xorg-core 81
Package xserver-xorg-core has broken dep on xserver-xorg-video-2
  Considering xserver-xorg-video-tseng 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-siliconmotion 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-ati 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-via 0 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-nv 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-i810 -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-video-i810 to the remove list
  Considering xserver-xorg-video-intel 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-chips 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-tga -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-video-tga to the remove list
  Considering xserver-xorg-video-trident 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-s3 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-vga -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-video-vga to the remove list
  Considering xserver-xorg-video-i128 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-mga 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-neomagic 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-cirrus 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-ark 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-tdfx 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-sisusb 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-dummy 0 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-rendition 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-vesa 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-cyrix -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-video-cyrix to the remove list
  Considering xserver-xorg-video-glint 0 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-fbdev 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-savage 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-openchrome 2 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-s3virge 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-voodoo 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-apm 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-sis 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-v4l 1 as a solution to xserver-xorg-core 81
  Fixing xserver-xorg-core via remove of xserver-xorg-input-kbd
  Fixing xserver-xorg-core via remove of xserver-xorg-video-i810
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tga
  Fixing xserver-xorg-core via remove of xserver-xorg-video-vga
  Fixing xserver-xorg-core via remove of xserver-xorg-video-cyrix
Investigating upstart
Package upstart has broken dep on startup-tasks
  Considering startup-tasks 2 as a solution to upstart 60
  Added startup-tasks to the remove list
Package upstart has broken dep on system-services
  Considering system-services 2 as a solution to upstart 60
  Added system-services to the remove list
Package upstart has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 5 as a solution to upstart 60
  Added upstart-compat-sysv to the remove list
  Fixing upstart via remove of startup-tasks
  Fixing upstart via remove of system-services
  Fixing upstart via remove of upstart-compat-sysv
Investigating php5-common
Package php5-common has broken dep on php5-mhash
  Considering php5-mhash -1 as a solution to php5-common 20
  Added php5-mhash to the remove list
  Fixing php5-common via remove of php5-mhash
Investigating libnautilus-extension1
Package libnautilus-extension1 has broken dep on gnome-mount
  Considering gnome-mount 1 as a solution to libnautilus-extension1 13
  Added gnome-mount to the remove list
  Fixing libnautilus-extension1 via remove of gnome-mount
Investigating console-setup
Package console-setup has broken dep on kbd
  Considering kbd 3 as a solution to console-setup 12
  Holding Back console-setup rather than change kbd
Investigating python-zope.interface
Package python-zope.interface has broken dep on python-zopeinterface
  Considering python-zopeinterface 0 as a solution to python-zope.interface 9
  Added python-zopeinterface to the remove list
  Fixing python-zope.interface via remove of python-zopeinterface
Investigating libxml-libxml-perl
Package libxml-libxml-perl has broken dep on libxml-libxml-common-perl
  Considering libxml-libxml-common-perl -1 as a solution to libxml-libxml-perl 9
  Added libxml-libxml-common-perl to the remove list
  Fixing libxml-libxml-perl via remove of libxml-libxml-common-perl
Investigating plymouth
Package plymouth has broken dep on usplash
  Considering usplash 1 as a solution to plymouth 9
  Added usplash to the remove list
  Considering usplash 1 as a solution to plymouth 9
  Fixing plymouth via remove of usplash
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
Investigating libmp3lame0
Package libmp3lame0 has broken dep on liblame0
  Considering liblame0 1 as a solution to libmp3lame0 7
  Added liblame0 to the remove list
  Fixing libmp3lame0 via remove of liblame0
Investigating libmetacity-private0
Package libmetacity-private0 has broken dep on libmetacity0
  Considering libmetacity0 -1 as a solution to libmetacity-private0 7
  Added libmetacity0 to the remove list
  Fixing libmetacity-private0 via remove of libmetacity0
Investigating nautilus
Package nautilus has broken dep on gnome-volume-manager
  Considering gnome-volume-manager -1 as a solution to nautilus 5
  Added gnome-volume-manager to the remove list
  Fixing nautilus via remove of gnome-volume-manager
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on kbd
  Considering kbd 3 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change kbd
Investigating libcrack2
Package libcrack2 has broken dep on cracklib2
  Considering cracklib2 4 as a solution to libcrack2 4
  Holding Back libcrack2 rather than change cracklib2
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken dep on libchromexvmc1
  Considering libchromexvmc1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmc1 to the remove list
Package xserver-xorg-video-openchrome has broken dep on libchromexvmcpro1
  Considering libchromexvmcpro1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmcpro1 to the remove list
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmc1
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmcpro1
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 60 as a solution to upstart-logd 2
  Removing upstart-logd rather than change upstart
Investigating libdb4.8-dev
Package libdb4.8-dev has broken dep on libdb4.6-dev
  Considering libdb4.6-dev -1 as a solution to libdb4.8-dev 2
  Added libdb4.6-dev to the remove list
  Considering libdb4.6-dev -1 as a solution to libdb4.8-dev 2
  Fixing libdb4.8-dev via remove of libdb4.6-dev
Investigating libsox1a
Package libsox1a has broken dep on libsox0
  Considering libsox0 -1 as a solution to libsox1a 2
  Added libsox0 to the remove list
  Fixing libsox1a via remove of libsox0
Investigating libgdl-1-0
Package libgdl-1-0 has broken dep on libgdl-1-common
  Considering libgdl-1-common 5 as a solution to libgdl-1-0 2
  Removing libgdl-1-0 rather than change libgdl-1-common
Investigating libgdl-gnome-1-0
Package libgdl-gnome-1-0 has broken dep on libgdl-1-0
  Considering libgdl-1-0 2 as a solution to libgdl-gnome-1-0 1
  Removing libgdl-gnome-1-0 rather than change libgdl-1-0
Investigating libgnomekbd2
Package libgnomekbd2 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 4 as a solution to libgnomekbd2 1
  Removing libgnomekbd2 rather than change libgnomekbd-common
Investigating guidance-backends
Package guidance-backends has broken dep on python
  Considering python 960 as a solution to guidance-backends 1
  Removing guidance-backends rather than change python
Investigating libuniconf4.6
Package libuniconf4.6 has broken dep on libuniconf4.4
  Considering libuniconf4.4 -1 as a solution to libuniconf4.6 0
  Added libuniconf4.4 to the remove list
  Fixing libuniconf4.6 via remove of libuniconf4.4
Investigating human-theme
Package human-theme has broken dep on gtk2-engines-ubuntulooks
  Considering gtk2-engines-ubuntulooks -1 as a solution to human-theme 0
  Added gtk2-engines-ubuntulooks to the remove list
  Fixing human-theme via remove of gtk2-engines-ubuntulooks
Investigating usplash-theme-ubuntu
Package usplash-theme-ubuntu has broken dep on usplash
  Considering usplash 1 as a solution to usplash-theme-ubuntu 0
  Removing usplash-theme-ubuntu rather than change usplash
Investigating vnc4server
Package vnc4server has broken dep on vnc4-common
  Considering vnc4-common -1 as a solution to vnc4server 0
  Added vnc4-common to the remove list
  Fixing vnc4server via remove of vnc4-common
Investigating rubygems1.8
Package rubygems1.8 has broken dep on libgems-ruby1.8
  Considering libgems-ruby1.8 -1 as a solution to rubygems1.8 0
  Added libgems-ruby1.8 to the remove list
  Fixing rubygems1.8 via remove of libgems-ruby1.8
Investigating libgnomekbdui2
Package libgnomekbdui2 has broken dep on libgnomekbd2
  Considering libgnomekbd2 1 as a solution to libgnomekbdui2 -1
  Removing libgnomekbdui2 rather than change libgnomekbd2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5391 as a solution to libperl5.8 -1
  Removing libperl5.8 rather than change perl-base
Investigating libkipi7
Package libkipi7 has broken dep on libkipi0
  Considering libkipi0 -1 as a solution to libkipi7 -1
  Holding Back libkipi7 rather than change libkipi0
Investigating python-gnome2-extras
Package python-gnome2-extras has broken dep on libgdl-1-0
  Considering libgdl-1-0 2 as a solution to python-gnome2-extras -1
  Removing python-gnome2-extras rather than change libgdl-1-0
Investigating libcupsys2-dev
Package libcupsys2-dev has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to libcupsys2-dev -1
  Removing libcupsys2-dev rather than change libcupsys2
Investigating libxcb-xlib0-dev
Package libxcb-xlib0-dev has broken dep on libxcb-xlib0
  Considering libxcb-xlib0 1 as a solution to libxcb-xlib0-dev -1
  Removing libxcb-xlib0-dev rather than change libxcb-xlib0
Investigating liblame-dev
Package liblame-dev has broken dep on liblame0
  Considering liblame0 1 as a solution to liblame-dev -1
  Removing liblame-dev rather than change liblame0
Investigating python-gtkhtml2
Package python-gtkhtml2 has broken dep on python
  Considering python 960 as a solution to python-gtkhtml2 -1
  Removing python-gtkhtml2 rather than change python
Investigating libxvidcore4-dev
Package libxvidcore4-dev has broken dep on libxvidcore4
  Considering libxvidcore4 6 as a solution to libxvidcore4-dev -1
  Removing libxvidcore4-dev rather than change libxvidcore4
Investigating displayconfig-gtk
Package displayconfig-gtk has broken dep on guidance-backends
  Considering guidance-backends 1 as a solution to displayconfig-gtk -1
  Removing displayconfig-gtk rather than change guidance-backends
Investigating cracklib-runtime
Package cracklib-runtime has broken dep on libcrack2
  Considering libcrack2 4 as a solution to cracklib-runtime -1
  Holding Back cracklib-runtime rather than change libcrack2
Investigating libltdl-dev
Package libltdl-dev has broken dep on libltdl3-dev
  Considering libltdl3-dev -1 as a solution to libltdl-dev -1
  Holding Back libltdl-dev rather than change libltdl3-dev
Investigating xulrunner-1.9-gnome-support
Package xulrunner-1.9-gnome-support has broken dep on xulrunner-1.9
  Considering xulrunner-1.9 2 as a solution to xulrunner-1.9-gnome-support -1
  Removing xulrunner-1.9-gnome-support rather than change xulrunner-1.9
Investigating netatalk
Package netatalk has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to netatalk 9999
  Added libcupsys2 to the remove list
  Fixing netatalk via keep of libcupsys2
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to libcups2 263
  Added libcupsys2 to the remove list
  Fixing libcups2 via remove of libcupsys2
 Try to Re-Instate console-setup
Investigating kipi-plugins
Package kipi-plugins has broken dep on libkipi7
  Considering libkipi7 -1 as a solution to kipi-plugins 0
  Holding Back kipi-plugins rather than change libkipi7
Investigating netatalk
Package netatalk has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to netatalk 9999
  Added libcupsys2 to the remove list
  Fixing netatalk via keep of libcupsys2
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 9999 as a solution to libcups2 263
  Holding Back libcups2 rather than change libcupsys2
Investigating libcupsimage2
Package libcupsimage2 has broken dep on libcups2
  Considering libcups2 263 as a solution to libcupsimage2 26
  Holding Back libcupsimage2 rather than change libcups2
Investigating cups-client
Package cups-client has broken dep on libcups2
  Considering libcups2 263 as a solution to cups-client 20
  Holding Back cups-client rather than change libcups2
Investigating cups
Package cups has broken dep on libcups2
  Considering libcups2 263 as a solution to cups 13
  Holding Back cups rather than change libcups2
Investigating kdelibs4c2a
Package kdelibs4c2a has broken dep on libcups2
  Considering libcups2 263 as a solution to kdelibs4c2a 12
  Holding Back kdelibs4c2a rather than change libcups2
Investigating libcupsppdc1
Package libcupsppdc1 has broken dep on libcups2
  Considering libcups2 263 as a solution to libcupsppdc1 8
  Holding Back libcupsppdc1 rather than change libcups2
Investigating libcupscgi1
Package libcupscgi1 has broken dep on libcups2
  Considering libcups2 263 as a solution to libcupscgi1 8
  Holding Back libcupscgi1 rather than change libcups2
Investigating libcupsdriver1
Package libcupsdriver1 has broken dep on libcups2
  Considering libcups2 263 as a solution to libcupsdriver1 8
  Holding Back libcupsdriver1 rather than change libcups2
Investigating libcupsmime1
Package libcupsmime1 has broken dep on libcups2
  Considering libcups2 263 as a solution to libcupsmime1 8
  Holding Back libcupsmime1 rather than change libcups2
Investigating libgnomeprint2.2-0
Package libgnomeprint2.2-0 has broken dep on libcups2
  Considering libcups2 263 as a solution to libgnomeprint2.2-0 7
  Removing libgnomeprint2.2-0 rather than change libcups2
Investigating libgs8
Package libgs8 has broken dep on libcups2
  Considering libcups2 263 as a solution to libgs8 7
  Holding Back libgs8 rather than change libcups2
Investigating libgnomecups1.0-1
Package libgnomecups1.0-1 has broken dep on libcups2
  Considering libcups2 263 as a solution to libgnomecups1.0-1 5
  Holding Back libgnomecups1.0-1 rather than change libcups2
Investigating python-cups
Package python-cups has broken dep on libcups2
  Considering libcups2 263 as a solution to python-cups 4
  Removing python-cups rather than change libcups2
Investigating libgnomeprintui2.2-0
Package libgnomeprintui2.2-0 has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 263 as a solution to libgnomeprintui2.2-0 3
  Removing libgnomeprintui2.2-0 rather than change libgnomeprint2.2-0
Investigating python-gnomeprint
Package python-gnomeprint has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 263 as a solution to python-gnomeprint 3
  Holding Back python-gnomeprint rather than change libgnomeprint2.2-0
Investigating foomatic-db-engine
Package foomatic-db-engine has broken dep on cups
  Considering cups 13 as a solution to foomatic-db-engine 2
  Holding Back foomatic-db-engine rather than change cups
Investigating ghostscript-cups
Package ghostscript-cups has broken dep on libcups2
  Considering libcups2 263 as a solution to ghostscript-cups 2
  Holding Back ghostscript-cups rather than change libcups2
Investigating foomatic-db
Package foomatic-db has broken dep on cups
  Considering cups 13 as a solution to foomatic-db 2
  Holding Back foomatic-db rather than change cups
Investigating system-config-printer-common
Package system-config-printer-common has broken dep on python-cups
  Considering python-cups 263 as a solution to system-config-printer-common 1
  Removing system-config-printer-common rather than change python-cups
 Try to Re-Instate kipi-plugins
Investigating openprinting-ppds
Package openprinting-ppds has broken dep on cups
  Considering cups 13 as a solution to openprinting-ppds 0
  Holding Back openprinting-ppds rather than change cups
Investigating system-config-printer-gnome
Package system-config-printer-gnome has broken dep on system-config-printer-common
  Considering system-config-printer-common 263 as a solution to system-config-printer-gnome 0
  Removing system-config-printer-gnome rather than change system-config-printer-common
Investigating pxljr
Package pxljr has broken dep on cups
  Considering cups 13 as a solution to pxljr 0
  Holding Back pxljr rather than change cups
Investigating libgtksourceview1.0-0
Package libgtksourceview1.0-0 has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 263 as a solution to libgtksourceview1.0-0 0
  Removing libgtksourceview1.0-0 rather than change libgnomeprint2.2-0
Investigating splix
Package splix has broken dep on libcups2
  Considering libcups2 263 as a solution to splix 0
  Holding Back splix rather than change libcups2
Investigating samba
Package samba has broken dep on libcups2
  Considering libcups2 263 as a solution to samba 0
  Removing samba rather than change libcups2
Investigating foo2zjs
Package foo2zjs has broken dep on cups
  Considering cups 13 as a solution to foo2zjs 0
  Holding Back foo2zjs rather than change cups
Investigating bluez-cups
Package bluez-cups has broken dep on cups
  Considering cups 13 as a solution to bluez-cups -1
  Holding Back bluez-cups rather than change cups
Investigating cups-driver-gutenprint
Package cups-driver-gutenprint has broken dep on libcups2
  Considering libcups2 263 as a solution to cups-driver-gutenprint -1
  Holding Back cups-driver-gutenprint rather than change libcups2
Investigating system-config-printer-udev
Package system-config-printer-udev has broken dep on libcups2
  Considering libcups2 263 as a solution to system-config-printer-udev -1
  Holding Back system-config-printer-udev rather than change libcups2
Investigating libgnome2.0-cil
Package libgnome2.0-cil has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 263 as a solution to libgnome2.0-cil -1
  Removing libgnome2.0-cil rather than change libgnomeprint2.2-0
Investigating libgtk2.0-0
Package libgtk2.0-0 has broken dep on libcups2
  Considering libcups2 263 as a solution to libgtk2.0-0 725
  Holding Back libgtk2.0-0 rather than change libcups2
Investigating python-gtk2
Package python-gtk2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to python-gtk2 93
  Removing python-gtk2 rather than change libgtk2.0-0
Investigating libbonoboui2-0
Package libbonoboui2-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libbonoboui2-0 91
  Removing libbonoboui2-0 rather than change libgtk2.0-0
Investigating libgail18
Package libgail18 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgail18 53
  Holding Back libgail18 rather than change libgtk2.0-0
Investigating libgnomeui-0
Package libgnomeui-0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to libgnomeui-0 51
  Removing libgnomeui-0 rather than change libbonoboui2-0
Investigating libgnome-desktop-2-17
Package libgnome-desktop-2-17 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgnome-desktop-2-17 31
  Holding Back libgnome-desktop-2-17 rather than change libgtk2.0-0
 Try to Re-Instate libcupsimage2
Investigating libpanel-applet2-0
Package libpanel-applet2-0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to libpanel-applet2-0 26
  Removing libpanel-applet2-0 rather than change libbonoboui2-0
Investigating librsvg2-2
Package librsvg2-2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to librsvg2-2 24
  Holding Back librsvg2-2 rather than change libgtk2.0-0
Investigating librsvg2-common
Package librsvg2-common has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to librsvg2-common 21
  Holding Back librsvg2-common rather than change libgtk2.0-0
Investigating libcanberra-gtk0
Package libcanberra-gtk0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libcanberra-gtk0 20
  Holding Back libcanberra-gtk0 rather than change libgtk2.0-0
Investigating libappindicator0
Package libappindicator0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libappindicator0 19
  Holding Back libappindicator0 rather than change libgtk2.0-0
Investigating libgtk2.0-bin
Package libgtk2.0-bin has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtk2.0-bin 18
  Holding Back libgtk2.0-bin rather than change libgtk2.0-0
Investigating python-gnome2
Package python-gnome2 has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-gnome2 16
  Removing python-gnome2 rather than change python-gtk2
Investigating libindicator0
Package libindicator0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libindicator0 16
  Holding Back libindicator0 rather than change libgtk2.0-0
Investigating libwnck22
Package libwnck22 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libwnck22 15
  Holding Back libwnck22 rather than change libgtk2.0-0
Investigating python-glade2
Package python-glade2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to python-glade2 15
  Removing python-glade2 rather than change libgtk2.0-0
Investigating ghostscript
Package ghostscript has broken dep on libgs8
  Considering libgs8 7 as a solution to ghostscript 15
  Holding Back ghostscript rather than change libgs8
Investigating libdbusmenu-gtk1
Package libdbusmenu-gtk1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libdbusmenu-gtk1 14
  Holding Back libdbusmenu-gtk1 rather than change libgtk2.0-0
Investigating libvte9
Package libvte9 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libvte9 13
  Holding Back libvte9 rather than change libgtk2.0-0
Investigating libnautilus-extension1
Package libnautilus-extension1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libnautilus-extension1 13
  Holding Back libnautilus-extension1 rather than change libgtk2.0-0
 Try to Re-Instate kdelibs4c2a
Investigating libgtk2.0-cil
Package libgtk2.0-cil has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtk2.0-cil 12
  Holding Back libgtk2.0-cil rather than change libgtk2.0-0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gnome-keyring 10
  Holding Back gnome-keyring rather than change libgtk2.0-0
Investigating libedataserverui1.2-8
Package libedataserverui1.2-8 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libedataserverui1.2-8 9
  Holding Back libedataserverui1.2-8 rather than change libgtk2.0-0
Investigating policykit-1-gnome
Package policykit-1-gnome has broken dep on libappindicator0
  Considering libappindicator0 19 as a solution to policykit-1-gnome 9
  Holding Back policykit-1-gnome rather than change libappindicator0
Investigating libwebkit-1.0-2
Package libwebkit-1.0-2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libwebkit-1.0-2 9
  Holding Back libwebkit-1.0-2 rather than change libgtk2.0-0
Investigating synaptic
Package synaptic has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to synaptic 8
  Removing synaptic rather than change libgtk2.0-0
Investigating libgtkhtml3.14-19
Package libgtkhtml3.14-19 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtkhtml3.14-19 7
  Holding Back libgtkhtml3.14-19 rather than change libgtk2.0-0
Investigating python-vte
Package python-vte has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to python-vte 7
  Removing python-vte rather than change libgtk2.0-0
Investigating libgail-common
Package libgail-common has broken dep on libgail18
  Considering libgail18 53 as a solution to libgail-common 7
  Holding Back libgail-common rather than change libgail18
Investigating libgnome-media0
Package libgnome-media0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgnome-media0 7
  Removing libgnome-media0 rather than change libgtk2.0-0
 Try to Re-Instate libgs8
Investigating libmetacity-private0
Package libmetacity-private0 has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 20 as a solution to libmetacity-private0 7
  Holding Back libmetacity-private0 rather than change libcanberra-gtk0
Investigating libgnome-pilot2
Package libgnome-pilot2 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to libgnome-pilot2 7
  Holding Back libgnome-pilot2 rather than change libbonoboui2-0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtk2-perl 6
  Removing libgtk2-perl rather than change libgtk2.0-0
Investigating rhythmbox
Package rhythmbox has broken dep on libgnome-media0
  Considering libgnome-media0 725 as a solution to rhythmbox 6
  Holding Back rhythmbox rather than change libgnome-media0
Investigating gnome-panel
Package gnome-panel has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to gnome-panel 6
  Removing gnome-panel rather than change libbonoboui2-0
Investigating nautilus
Package nautilus has broken dep on libappindicator0
  Considering libappindicator0 19 as a solution to nautilus 5
  Removing nautilus rather than change libappindicator0
Investigating libgnome-window-settings1
Package libgnome-window-settings1 has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 31 as a solution to libgnome-window-settings1 5
  Removing libgnome-window-settings1 rather than change libgnome-desktop-2-17
Investigating libgtkmm-2.4-1c2a
Package libgtkmm-2.4-1c2a has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtkmm-2.4-1c2a 5
  Holding Back libgtkmm-2.4-1c2a rather than change libgtk2.0-0
Investigating gnome-about
Package gnome-about has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to gnome-about 5
  Removing gnome-about rather than change python-gtk2
 Try to Re-Instate libgnomecups1.0-1
Investigating python-gnomeapplet
Package python-gnomeapplet has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to python-gnomeapplet 5
  Holding Back python-gnomeapplet rather than change libbonoboui2-0
Investigating gnome-control-center
Package gnome-control-center has broken dep on libappindicator0
  Considering libappindicator0 19 as a solution to gnome-control-center 5
  Removing gnome-control-center rather than change libappindicator0
Investigating python-gnome2-desktop
Package python-gnome2-desktop has broken dep on python-gnomeapplet
  Considering python-gnomeapplet 5 as a solution to python-gnome2-desktop 5
  Removing python-gnome2-desktop rather than change python-gnomeapplet
Investigating python-notify
Package python-notify has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-notify 4
  Removing python-notify rather than change python-gtk2
Investigating libevdocument2
Package libevdocument2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libevdocument2 4
  Holding Back libevdocument2 rather than change libgtk2.0-0
Investigating zenity
Package zenity has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to zenity 4
  Holding Back zenity rather than change libgtk2.0-0
Investigating python-gmenu
Package python-gmenu has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-gmenu 4
  Removing python-gmenu rather than change python-gtk2
Investigating firefox
Package firefox has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to firefox 4
  Holding Back firefox rather than change libgtk2.0-0
Investigating libglade2.0-cil
Package libglade2.0-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 12 as a solution to libglade2.0-cil 4
  Holding Back libglade2.0-cil rather than change libgtk2.0-cil
Investigating libgnomekbd4
Package libgnomekbd4 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgnomekbd4 4
  Holding Back libgnomekbd4 rather than change libgtk2.0-0
Investigating compiz-plugins
Package compiz-plugins has broken dep on librsvg2-2
  Considering librsvg2-2 24 as a solution to compiz-plugins 4
  Removing compiz-plugins rather than change librsvg2-2
Investigating libgtksourceview2.0-0
Package libgtksourceview2.0-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtksourceview2.0-0 4
  Removing libgtksourceview2.0-0 rather than change libgtk2.0-0
Investigating totem
Package totem has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to totem 4
  Holding Back totem rather than change libgtk2.0-0
Investigating python-bugbuddy
Package python-bugbuddy has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-bugbuddy 3
  Holding Back python-bugbuddy rather than change python-gtk2
Investigating python-evolution
Package python-evolution has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-evolution 3
  Holding Back python-evolution rather than change python-gtk2
Investigating python-gnomedesktop
Package python-gnomedesktop has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 31 as a solution to python-gnomedesktop 3
  Holding Back python-gnomedesktop rather than change libgnome-desktop-2-17
Investigating python-evince
Package python-evince has broken dep on libevdocument2
  Considering libevdocument2 4 as a solution to python-evince 3
  Holding Back python-evince rather than change libevdocument2
Investigating libgtkhtml-editor0
Package libgtkhtml-editor0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtkhtml-editor0 3
  Holding Back libgtkhtml-editor0 rather than change libgtk2.0-0
Investigating evolution
Package evolution has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to evolution 3
  Holding Back evolution rather than change libbonoboui2-0
Investigating libpolkit-gnome0
Package libpolkit-gnome0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libpolkit-gnome0 3
  Holding Back libpolkit-gnome0 rather than change libgtk2.0-0
Investigating policykit-gnome
Package policykit-gnome has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to policykit-gnome 3
  Holding Back policykit-gnome rather than change libgtk2.0-0
Investigating python-totem-plparser
Package python-totem-plparser has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-totem-plparser 3
  Holding Back python-totem-plparser rather than change python-gtk2
Investigating python-gnomekeyring
Package python-gnomekeyring has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-gnomekeyring 3
  Holding Back python-gnomekeyring rather than change python-gtk2
Investigating liblpint-bonobo0
Package liblpint-bonobo0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to liblpint-bonobo0 3
  Holding Back liblpint-bonobo0 rather than change libbonoboui2-0
Investigating firefox-branding
Package firefox-branding has broken dep on firefox
  Considering firefox 4 as a solution to firefox-branding 3
  Holding Back firefox-branding rather than change firefox
Investigating libgail-gnome-module
Package libgail-gnome-module has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to libgail-gnome-module 3
  Removing libgail-gnome-module rather than change libbonoboui2-0
Investigating python-rsvg
Package python-rsvg has broken dep on librsvg2-2
  Considering librsvg2-2 24 as a solution to python-rsvg 3
  Holding Back python-rsvg rather than change librsvg2-2
Investigating yelp
Package yelp has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to yelp 3
  Removing yelp rather than change libgtk2.0-0
Investigating python-mediaprofiles
Package python-mediaprofiles has broken dep on libgnome-media0
  Considering libgnome-media0 725 as a solution to python-mediaprofiles 3
  Holding Back python-mediaprofiles rather than change libgnome-media0
Investigating python-wnck
Package python-wnck has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-wnck 3
  Holding Back python-wnck rather than change python-gtk2
Investigating python-metacity
Package python-metacity has broken dep on libmetacity-private0
  Considering libmetacity-private0 7 as a solution to python-metacity 3
  Holding Back python-metacity rather than change libmetacity-private0
Investigating python-gtop
Package python-gtop has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-gtop 3
  Holding Back python-gtop rather than change python-gtk2
Investigating libido-0.1-0
Package libido-0.1-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libido-0.1-0 2
  Holding Back libido-0.1-0 rather than change libgtk2.0-0
 Try to Re-Instate foomatic-db-engine
Investigating gnome-settings-daemon
Package gnome-settings-daemon has broken dep on libappindicator0
  Considering libappindicator0 19 as a solution to gnome-settings-daemon 2
  Removing gnome-settings-daemon rather than change libappindicator0
Investigating libevview2
Package libevview2 has broken dep on libevdocument2
  Considering libevdocument2 4 as a solution to libevview2 2
  Holding Back libevview2 rather than change libevdocument2
Investigating gtk2-engines-murrine
Package gtk2-engines-murrine has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gtk2-engines-murrine 2
  Holding Back gtk2-engines-murrine rather than change libgtk2.0-0
Investigating python-webkit
Package python-webkit has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 9 as a solution to python-webkit 2
  Holding Back python-webkit rather than change libwebkit-1.0-2
Investigating libgoffice-0.8-8
Package libgoffice-0.8-8 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgoffice-0.8-8 2
  Holding Back libgoffice-0.8-8 rather than change libgtk2.0-0
Investigating eog
Package eog has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 31 as a solution to eog 2
  Removing eog rather than change libgnome-desktop-2-17
Investigating xulrunner-1.9.2
Package xulrunner-1.9.2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to xulrunner-1.9.2 2
  Holding Back xulrunner-1.9.2 rather than change libgtk2.0-0
Investigating software-properties-gtk
Package software-properties-gtk has broken dep on synaptic
  Considering synaptic 725 as a solution to software-properties-gtk 2
  Removing software-properties-gtk rather than change synaptic
Investigating compiz-gnome
Package compiz-gnome has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 31 as a solution to compiz-gnome 2
  Removing compiz-gnome rather than change libgnome-desktop-2-17
Investigating evince
Package evince has broken dep on libevdocument2
  Considering libevdocument2 4 as a solution to evince 2
  Removing evince rather than change libevdocument2
Investigating gimp
Package gimp has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to gimp 2
  Holding Back gimp rather than change python-gtk2
Investigating gtk2-engines-pixbuf
Package gtk2-engines-pixbuf has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gtk2-engines-pixbuf 2
  Holding Back gtk2-engines-pixbuf rather than change libgtk2.0-0
 Try to Re-Instate foomatic-db
Investigating libgtkhtml2-0
Package libgtkhtml2-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtkhtml2-0 2
  Holding Back libgtkhtml2-0 rather than change libgtk2.0-0
Investigating gnome-panel-dbg
Package gnome-panel-dbg has broken dep on gnome-panel
  Considering gnome-panel 725 as a solution to gnome-panel-dbg 1
  Holding Back gnome-panel-dbg rather than change gnome-panel
Investigating libmono-addins-gui0.2-cil
Package libmono-addins-gui0.2-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 12 as a solution to libmono-addins-gui0.2-cil 1
  Holding Back libmono-addins-gui0.2-cil rather than change libgtk2.0-cil
Investigating metacity
Package metacity has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 20 as a solution to metacity 1
  Removing metacity rather than change libcanberra-gtk0
Investigating gnome-session-bin
Package gnome-session-bin has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gnome-session-bin 1
  Holding Back gnome-session-bin rather than change libgtk2.0-0
Investigating libbrasero-media0
Package libbrasero-media0 has broken dep on libappindicator0
  Considering libappindicator0 19 as a solution to libbrasero-media0 1
  Holding Back libbrasero-media0 rather than change libappindicator0
Investigating libgucharmap7
Package libgucharmap7 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgucharmap7 1
  Holding Back libgucharmap7 rather than change libgtk2.0-0
Investigating gnome-applets
Package gnome-applets has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to gnome-applets 1
  Holding Back gnome-applets rather than change libbonoboui2-0
Investigating evince-dbg
Package evince-dbg has broken dep on evince
  Considering evince 4 as a solution to evince-dbg 1
  Holding Back evince-dbg rather than change evince
Investigating python-pyatspi
Package python-pyatspi has broken dep on python-gnome2
  Considering python-gnome2 725 as a solution to python-pyatspi 1
  Removing python-pyatspi rather than change python-gnome2
Investigating epiphany-browser
Package epiphany-browser has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to epiphany-browser 1
  Holding Back epiphany-browser rather than change libgtk2.0-0
Investigating python-gtk2-dbg
Package python-gtk2-dbg has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-gtk2-dbg 1
  Holding Back python-gtk2-dbg rather than change python-gtk2
Investigating eog-dbg
Package eog-dbg has broken dep on eog
  Considering eog 31 as a solution to eog-dbg 1
  Holding Back eog-dbg rather than change eog
Investigating gnome-applets-dbg
Package gnome-applets-dbg has broken dep on gnome-applets
  Considering gnome-applets 1 as a solution to gnome-applets-dbg 1
  Holding Back gnome-applets-dbg rather than change gnome-applets
Investigating python-gtksourceview2
Package python-gtksourceview2 has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-gtksourceview2 1
  Removing python-gtksourceview2 rather than change python-gtk2
Investigating nautilus-dbg
Package nautilus-dbg has broken dep on nautilus
  Considering nautilus 19 as a solution to nautilus-dbg 1
  Holding Back nautilus-dbg rather than change nautilus
Investigating gnome-pilot
Package gnome-pilot has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to gnome-pilot 1
  Removing gnome-pilot rather than change libbonoboui2-0
Investigating libgnome2.24-cil
Package libgnome2.24-cil has broken dep on libglade2.0-cil
  Considering libglade2.0-cil 4 as a solution to libgnome2.24-cil 1
  Holding Back libgnome2.24-cil rather than change libglade2.0-cil
Investigating librsvg2-dbg
Package librsvg2-dbg has broken dep on librsvg2-2
  Considering librsvg2-2 24 as a solution to librsvg2-dbg 1
  Holding Back librsvg2-dbg rather than change librsvg2-2
Investigating update-manager
Package update-manager has broken dep on synaptic
  Considering synaptic 725 as a solution to update-manager 1
  Removing update-manager rather than change synaptic
Investigating libgnome-desktop-2
Package libgnome-desktop-2 has broken dep on libgnomeui-0
  Considering libgnomeui-0 725 as a solution to libgnome-desktop-2 1
  Removing libgnome-desktop-2 rather than change libgnomeui-0
Investigating libgcr0
Package libgcr0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgcr0 1
  Holding Back libgcr0 rather than change libgtk2.0-0
Investigating libgtk2.0-0-dbg
Package libgtk2.0-0-dbg has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtk2.0-0-dbg 1
  Holding Back libgtk2.0-0-dbg rather than change libgtk2.0-0
Investigating libgtkhtml3.14-dbg
Package libgtkhtml3.14-dbg has broken dep on libgtkhtml3.14-19
  Considering libgtkhtml3.14-19 7 as a solution to libgtkhtml3.14-dbg 1
  Holding Back libgtkhtml3.14-dbg rather than change libgtkhtml3.14-19
Investigating deskbar-applet
Package deskbar-applet has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 31 as a solution to deskbar-applet 1
  Removing deskbar-applet rather than change libgnome-desktop-2-17
Investigating evolution-dbg
Package evolution-dbg has broken dep on evolution
  Considering evolution 3 as a solution to evolution-dbg 1
  Holding Back evolution-dbg rather than change evolution
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on libgtk2-perl
  Considering libgtk2-perl 725 as a solution to libgnome2-canvas-perl 1
  Removing libgnome2-canvas-perl rather than change libgtk2-perl
Investigating apturl
Package apturl has broken dep on python-glade2
  Considering python-glade2 725 as a solution to apturl 1
  Removing apturl rather than change python-glade2
Investigating libgtk2-gladexml-perl
Package libgtk2-gladexml-perl has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtk2-gladexml-perl 1
  Removing libgtk2-gladexml-perl rather than change libgtk2.0-0
Investigating gnome-user-guide
Package gnome-user-guide has broken dep on yelp
  Considering yelp 725 as a solution to gnome-user-guide 1
  Removing gnome-user-guide rather than change yelp
Investigating libgnomeui-0-dbg
Package libgnomeui-0-dbg has broken dep on libgnomeui-0
  Considering libgnomeui-0 725 as a solution to libgnomeui-0-dbg 1
  Holding Back libgnomeui-0-dbg rather than change libgnomeui-0
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgtk2.0-dev 1
  Holding Back libgtk2.0-dev rather than change libgtk2.0-0
Investigating totem-dbg
Package totem-dbg has broken dep on totem
  Considering totem 4 as a solution to totem-dbg 1
  Holding Back totem-dbg rather than change totem
Investigating firefox-gnome-support
Package firefox-gnome-support has broken dep on firefox
  Considering firefox 4 as a solution to firefox-gnome-support 1
  Holding Back firefox-gnome-support rather than change firefox
Investigating gnome-power-manager
Package gnome-power-manager has broken dep on libappindicator0
  Considering libappindicator0 19 as a solution to gnome-power-manager 0
  Removing gnome-power-manager rather than change libappindicator0
Investigating tomboy
Package tomboy has broken dep on libgnome2.24-cil
  Considering libgnome2.24-cil 1 as a solution to tomboy 0
  Removing tomboy rather than change libgnome2.24-cil
Investigating libgnome-bluetooth7
Package libgnome-bluetooth7 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgnome-bluetooth7 0
  Holding Back libgnome-bluetooth7 rather than change libgtk2.0-0
Investigating gcalctool
Package gcalctool has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gcalctool 0
  Holding Back gcalctool rather than change libgtk2.0-0
 Try to Re-Instate openprinting-ppds
Investigating gnome-media
Package gnome-media has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 20 as a solution to gnome-media 0
  Removing gnome-media rather than change libcanberra-gtk0
Investigating smart-notifier
Package smart-notifier has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to smart-notifier 0
  Removing smart-notifier rather than change python-gtk2
Investigating checkbox-gtk
Package checkbox-gtk has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to checkbox-gtk 0
  Holding Back checkbox-gtk rather than change python-gtk2
Investigating update-notifier
Package update-notifier has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to update-notifier 0
  Removing update-notifier rather than change libgtk2.0-0
Investigating ubuntu-docs
Package ubuntu-docs has broken dep on gnome-user-guide
  Considering gnome-user-guide 725 as a solution to ubuntu-docs 0
  Removing ubuntu-docs rather than change gnome-user-guide
Investigating network-manager-gnome
Package network-manager-gnome has broken dep on libgnome-bluetooth7
  Considering libgnome-bluetooth7 0 as a solution to network-manager-gnome 0
  Removing network-manager-gnome rather than change libgnome-bluetooth7
 Try to Re-Instate pxljr
Investigating gucharmap
Package gucharmap has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gucharmap 0
  Holding Back gucharmap rather than change libgtk2.0-0
Investigating libseed0
Package libseed0 has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 9 as a solution to libseed0 0
  Holding Back libseed0 rather than change libwebkit-1.0-2
Investigating totem-plugins
Package totem-plugins has broken dep on totem
  Considering totem 4 as a solution to totem-plugins 0
  Removing totem-plugins rather than change totem
Investigating computertemp
Package computertemp has broken dep on python-gnome2
  Considering python-gnome2 725 as a solution to computertemp 0
  Removing computertemp rather than change python-gnome2
Investigating gdebi
Package gdebi has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to gdebi 0
  Removing gdebi rather than change python-gtk2
Investigating scim-bridge-client-gtk
Package scim-bridge-client-gtk has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to scim-bridge-client-gtk 0
  Holding Back scim-bridge-client-gtk rather than change libgtk2.0-0
Investigating nautilus-share
Package nautilus-share has broken dep on nautilus
  Considering nautilus 19 as a solution to nautilus-share 0
  Removing nautilus-share rather than change nautilus
Investigating ubufox
Package ubufox has broken dep on apturl
  Considering apturl 725 as a solution to ubufox 0
Package ubufox has broken dep on apturl-kde
  Considering apturl-kde 1 as a solution to ubufox 0
  Or group remove for ubufox
Investigating libgnomepanel2.24-cil
Package libgnomepanel2.24-cil has broken dep on libpanel-applet2-0
  Considering libpanel-applet2-0 725 as a solution to libgnomepanel2.24-cil 0
  Holding Back libgnomepanel2.24-cil rather than change libpanel-applet2-0
Investigating gparted
Package gparted has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gparted 0
  Holding Back gparted rather than change libgtk2.0-0
Investigating gnome-mag
Package gnome-mag has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gnome-mag 0
  Holding Back gnome-mag rather than change libgtk2.0-0
Investigating liblaunchpad-integration1.0-cil
Package liblaunchpad-integration1.0-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 12 as a solution to liblaunchpad-integration1.0-cil 0
  Holding Back liblaunchpad-integration1.0-cil rather than change libgtk2.0-cil
Investigating gedit
Package gedit has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gedit 0
  Removing gedit rather than change libgtk2.0-0
Investigating gnome-system-monitor
Package gnome-system-monitor has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gnome-system-monitor 0
  Holding Back gnome-system-monitor rather than change libgtk2.0-0
Investigating gnome-terminal
Package gnome-terminal has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gnome-terminal 0
  Removing gnome-terminal rather than change libgtk2.0-0
Investigating gnome-session
Package gnome-session has broken dep on gnome-settings-daemon
  Considering gnome-settings-daemon 19 as a solution to gnome-session 0
  Removing gnome-session rather than change gnome-settings-daemon
Investigating seahorse
Package seahorse has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to seahorse 0
  Removing seahorse rather than change libgtk2.0-0
Investigating libgdict-1.0-6
Package libgdict-1.0-6 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgdict-1.0-6 0
  Holding Back libgdict-1.0-6 rather than change libgtk2.0-0
Investigating software-center
Package software-center has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to software-center 0
  Holding Back software-center rather than change python-gtk2
Investigating hwtest-gtk
Package hwtest-gtk has broken dep on checkbox-gtk
  Considering checkbox-gtk 0 as a solution to hwtest-gtk 0
  Removing hwtest-gtk rather than change checkbox-gtk
Investigating tracker-search-tool
Package tracker-search-tool has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 31 as a solution to tracker-search-tool 0
  Removing tracker-search-tool rather than change libgnome-desktop-2-17
Investigating fslint
Package fslint has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to fslint 0
  Removing fslint rather than change python-gtk2
Investigating gnome-nettool
Package gnome-nettool has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gnome-nettool 0
  Holding Back gnome-nettool rather than change libgtk2.0-0
Investigating language-selector
Package language-selector has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to language-selector 0
  Removing language-selector rather than change python-gtk2
Investigating gnome-utils
Package gnome-utils has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to gnome-utils 0
  Removing gnome-utils rather than change libbonoboui2-0
Investigating gconf-editor
Package gconf-editor has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gconf-editor 0
  Removing gconf-editor rather than change libgtk2.0-0
Investigating libgegl-0.0-0
Package libgegl-0.0-0 has broken dep on librsvg2-2
  Considering librsvg2-2 24 as a solution to libgegl-0.0-0 0
  Holding Back libgegl-0.0-0 rather than change librsvg2-2
Investigating anjuta
Package anjuta has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to anjuta 0
  Holding Back anjuta rather than change libgtk2.0-0
Investigating gnome-orca
Package gnome-orca has broken dep on python-pyatspi
  Considering python-pyatspi 725 as a solution to gnome-orca 0
Package gnome-orca has broken dep on python-pyatspi2
  Or group remove for gnome-orca
Package gnome-orca has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to gnome-orca 0
  Removing gnome-orca rather than change python-gtk2
Investigating libgladeui-1-9
Package libgladeui-1-9 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libgladeui-1-9 0
  Holding Back libgladeui-1-9 rather than change libgtk2.0-0
Investigating python-sexy
Package python-sexy has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-sexy 0
  Removing python-sexy rather than change python-gtk2
Investigating bug-buddy
Package bug-buddy has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to bug-buddy 0
  Removing bug-buddy rather than change libgtk2.0-0
 Try to Re-Instate splix
Investigating tsclient
Package tsclient has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to tsclient 0
  Removing tsclient rather than change libbonoboui2-0
Investigating scim-gtk2-immodule
Package scim-gtk2-immodule has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to scim-gtk2-immodule 0
  Removing scim-gtk2-immodule rather than change libgtk2.0-0
Investigating libdeskbar-tracker
Package libdeskbar-tracker has broken dep on python-gnome2
  Considering python-gnome2 725 as a solution to libdeskbar-tracker 0
  Removing libdeskbar-tracker rather than change python-gnome2
Investigating mousetweaks
Package mousetweaks has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to mousetweaks 0
  Removing mousetweaks rather than change libbonoboui2-0
Investigating libdevhelp-1-1
Package libdevhelp-1-1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to libdevhelp-1-1 0
  Holding Back libdevhelp-1-1 rather than change libgtk2.0-0
Investigating gir1.0-gtk-2.0
Package gir1.0-gtk-2.0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gir1.0-gtk-2.0 0
  Holding Back gir1.0-gtk-2.0 rather than change libgtk2.0-0
Investigating ghostscript-x
Package ghostscript-x has broken dep on ghostscript
  Considering ghostscript 15 as a solution to ghostscript-x 0
  Holding Back ghostscript-x rather than change ghostscript
Investigating nautilus-sendto
Package nautilus-sendto has broken dep on libnautilus-extension1
  Considering libnautilus-extension1 13 as a solution to nautilus-sendto 0
  Removing nautilus-sendto rather than change libnautilus-extension1
 Try to Re-Instate foo2zjs
Investigating gnome-screensaver
Package gnome-screensaver has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 31 as a solution to gnome-screensaver 0
  Removing gnome-screensaver rather than change libgnome-desktop-2-17
Investigating onboard
Package onboard has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to onboard 0
  Removing onboard rather than change python-gtk2
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to libgnome2-perl 0
  Removing libgnome2-perl rather than change libbonoboui2-0
Investigating jockey-gtk
Package jockey-gtk has broken dep on python-notify
  Considering python-notify 725 as a solution to jockey-gtk 0
  Removing jockey-gtk rather than change python-notify
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem
  Considering totem 4 as a solution to totem-gstreamer 0
  Removing totem-gstreamer rather than change totem
Investigating gtkorphan
Package gtkorphan has broken dep on libgtk2-gladexml-perl
  Considering libgtk2-gladexml-perl 725 as a solution to gtkorphan 0
  Removing gtkorphan rather than change libgtk2-gladexml-perl
Investigating compiz
Package compiz has broken dep on compiz-plugins
  Considering compiz-plugins 24 as a solution to compiz 0
  Removing compiz rather than change compiz-plugins
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem
  Considering totem 4 as a solution to totem-mozilla 0
  Removing totem-mozilla rather than change totem
Investigating apport-gtk
Package apport-gtk has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to apport-gtk 0
  Removing apport-gtk rather than change python-gtk2
Investigating nautilus-cd-burner
Package nautilus-cd-burner has broken dep on libgnomeui-0
  Considering libgnomeui-0 725 as a solution to nautilus-cd-burner 0
  Removing nautilus-cd-burner rather than change libgnomeui-0
Investigating light-themes
Package light-themes has broken dep on gtk2-engines-murrine
  Considering gtk2-engines-murrine 2 as a solution to light-themes 0
  Holding Back light-themes rather than change gtk2-engines-murrine
Investigating file-roller
Package file-roller has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to file-roller 0
  Removing file-roller rather than change libgtk2.0-0
Investigating gnome-netstatus-applet
Package gnome-netstatus-applet has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to gnome-netstatus-applet 0
  Removing gnome-netstatus-applet rather than change libgtk2.0-0
Investigating powermanagement-interface
Package powermanagement-interface has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to powermanagement-interface 0
  Holding Back powermanagement-interface rather than change libgtk2.0-0
Investigating evolution-plugins
Package evolution-plugins has broken dep on evolution
  Considering evolution 3 as a solution to evolution-plugins -1
  Holding Back evolution-plugins rather than change evolution
Investigating bleachbit
Package bleachbit has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to bleachbit -1
  Removing bleachbit rather than change python-gtk2
Investigating indicator-applet
Package indicator-applet has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 725 as a solution to indicator-applet -1
  Holding Back indicator-applet rather than change libgtk2.0-0
Investigating libcanberra-gtk-module
Package libcanberra-gtk-module has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 20 as a solution to libcanberra-gtk-module -1
  Holding Back libcanberra-gtk-module rather than change libcanberra-gtk0
Investigating gnome-spell
Package gnome-spell has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to gnome-spell -1
  Removing gnome-spell rather than change libbonoboui2-0
Investigating indicator-messages
Package indicator-messages has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 14 as a solution to indicator-messages -1
  Holding Back indicator-messages rather than change libdbusmenu-gtk1
Investigating contact-lookup-applet
Package contact-lookup-applet has broken dep on libgnomeui-0
  Considering libgnomeui-0 725 as a solution to contact-lookup-applet -1
  Removing contact-lookup-applet rather than change libgnomeui-0
Investigating python-aptdaemon-gtk
Package python-aptdaemon-gtk has broken dep on python-gtk2
  Considering python-gtk2 725 as a solution to python-aptdaemon-gtk -1
  Holding Back python-aptdaemon-gtk rather than change python-gtk2
Investigating python-appindicator
Package python-appindicator has broken dep on libappindicator0
  Considering libappindicator0 19 as a solution to python-appindicator -1
  Holding Back python-appindicator rather than change libappindicator0
Investigating gsmartcontrol
Package gsmartcontrol has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 5 as a solution to gsmartcontrol -1
  Holding Back gsmartcontrol rather than change libgtkmm-2.4-1c2a
Investigating gnome-pilot-conduits
Package gnome-pilot-conduits has broken dep on gnome-pilot
  Considering gnome-pilot 725 as a solution to gnome-pilot-conduits -1
  Removing gnome-pilot-conduits rather than change gnome-pilot
Investigating libeel2-2
Package libeel2-2 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 725 as a solution to libeel2-2 -1
  Removing libeel2-2 rather than change libbonoboui2-0
Investigating ubuntu-tweak
Package ubuntu-tweak has broken dep on python-gnome2
  Considering python-gnome2 725 as a solution to ubuntu-tweak -1
  Removing ubuntu-tweak rather than change python-gnome2
Investigating rhythmbox-plugin-cdrecorder
Package rhythmbox-plugin-cdrecorder has broken dep on libbrasero-media0
  Considering libbrasero-media0 1 as a solution to rhythmbox-plugin-cdrecorder -1
  Holding Back rhythmbox-plugin-cdrecorder rather than change libbrasero-media0
Investigating rhythmbox-plugins
Package rhythmbox-plugins has broken dep on libappindicator0
  Considering libappindicator0 19 as a solution to rhythmbox-plugins -1
  Holding Back rhythmbox-plugins rather than change libappindicator0
Investigating indicator-application
Package indicator-application has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 14 as a solution to indicator-application -1
  Holding Back indicator-application rather than change libdbusmenu-gtk1
Investigating rhythmbox-dbg
Package rhythmbox-dbg has broken dep on rhythmbox
  Considering rhythmbox 6 as a solution to rhythmbox-dbg -2
  Holding Back rhythmbox-dbg rather than change rhythmbox
Investigating gnome-dbg
Package gnome-dbg has broken dep on gnome-applets-dbg
  Considering gnome-applets-dbg 1 as a solution to gnome-dbg -2
  Holding Back gnome-dbg rather than change gnome-applets-dbg
Investigating indicator-sound
Package indicator-sound has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 14 as a solution to indicator-sound -2
  Holding Back indicator-sound rather than change libdbusmenu-gtk1
Investigating libwebkit-1.0-2-dbg
Package libwebkit-1.0-2-dbg has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 9 as a solution to libwebkit-1.0-2-dbg -2
  Holding Back libwebkit-1.0-2-dbg rather than change libwebkit-1.0-2
Investigating libgail-gnome-dbg
Package libgail-gnome-dbg has broken dep on libgail-gnome-module
  Considering libgail-gnome-module 725 as a solution to libgail-gnome-dbg -2
  Holding Back libgail-gnome-dbg rather than change libgail-gnome-module
Investigating libgoffice-dbg
Package libgoffice-dbg has broken dep on libgoffice-0.8-8
  Considering libgoffice-0.8-8 2 as a solution to libgoffice-dbg -2
  Holding Back libgoffice-dbg rather than change libgoffice-0.8-8
 Try to Re-Instate libgtk2.0-0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 10 as a solution to libgnome-keyring0 68
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
 Try to Re-Instate libgail18
Investigating gvfs
Package gvfs has broken dep on policykit-1-gnome
  Considering policykit-1-gnome 9 as a solution to gvfs 34
  Holding Back gvfs rather than change policykit-1-gnome
 Try to Re-Instate librsvg2-2
 Try to Re-Instate librsvg2-common
 Try to Re-Instate libgtk2.0-bin
 Try to Re-Instate libwnck22
 Try to Re-Instate ghostscript
 Try to Re-Instate libvte9
 Try to Re-Instate libnautilus-extension1
 Try to Re-Instate libgtk2.0-cil
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 10
  Holding Back gnome-keyring rather than change libgcr0
 Try to Re-Instate libedataserverui1.2-8
Investigating gnome-menus
Package gnome-menus has broken dep on python-gmenu
  Considering python-gmenu 725 as a solution to gnome-menus 8
  Removing gnome-menus rather than change python-gmenu
Investigating libpangomm-1.4-1
Package libpangomm-1.4-1 has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 5 as a solution to libpangomm-1.4-1 7
  Added libgtkmm-2.4-1c2a to the remove list
  Fixing libpangomm-1.4-1 via remove of libgtkmm-2.4-1c2a
 Try to Re-Instate libgail-common
 Try to Re-Instate libgnome-pilot2
 Try to Re-Instate zenity
 Try to Re-Instate firefox
 Try to Re-Instate libglade2.0-cil
 Try to Re-Instate libpolkit-gnome0
 Try to Re-Instate policykit-gnome
 Try to Re-Instate gtk2-engines-murrine
Investigating anjuta-dbg
Package anjuta-dbg has broken dep on anjuta
  Considering anjuta 0 as a solution to anjuta-dbg 2
  Holding Back anjuta-dbg rather than change anjuta
 Try to Re-Instate gtk2-engines-pixbuf
 Try to Re-Instate libgtkhtml2-0
 Try to Re-Instate libmono-addins-gui0.2-cil
Investigating epiphany-browser-dbg
Package epiphany-browser-dbg has broken dep on epiphany-browser
  Considering epiphany-browser 1 as a solution to epiphany-browser-dbg 1
  Holding Back epiphany-browser-dbg rather than change epiphany-browser
 Try to Re-Instate libgtk2.0-dev
 Try to Re-Instate firefox-gnome-support
Investigating ubuntu-artwork
Package ubuntu-artwork has broken dep on light-themes
  Considering light-themes 0 as a solution to ubuntu-artwork 0
  Holding Back ubuntu-artwork rather than change light-themes
 Try to Re-Instate gcalctool
 Try to Re-Instate gucharmap
 Try to Re-Instate scim-bridge-client-gtk
Investigating gnome-app-install
Package gnome-app-install has broken dep on software-center
  Considering software-center 0 as a solution to gnome-app-install 0
  Removing gnome-app-install rather than change software-center
Investigating gvfs-backends
Package gvfs-backends has broken dep on gvfs
  Considering gvfs 34 as a solution to gvfs-backends 0
  Holding Back gvfs-backends rather than change gvfs
 Try to Re-Instate gparted
Investigating gparted
Package gparted has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 7 as a solution to gparted 0
  Removing gparted rather than change libgtkmm-2.4-1c2a
 Try to Re-Instate gnome-mag
 Try to Re-Instate gnome-system-monitor
Investigating gnome-system-monitor
Package gnome-system-monitor has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 7 as a solution to gnome-system-monitor 0
  Removing gnome-system-monitor rather than change libgtkmm-2.4-1c2a
 Try to Re-Instate gnome-nettool
 Try to Re-Instate ghostscript-x
Investigating gpar2
Package gpar2 has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 7 as a solution to gpar2 0
  Removing gpar2 rather than change libgtkmm-2.4-1c2a
 Try to Re-Instate powermanagement-interface
 Try to Re-Instate gsmartcontrol
Investigating gsmartcontrol
Package gsmartcontrol has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 7 as a solution to gsmartcontrol -1
  Removing gsmartcontrol rather than change libgtkmm-2.4-1c2a
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 10 as a solution to libgnome-keyring0 68
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
 Try to Re-Instate gvfs
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 10
  Holding Back gnome-keyring rather than change libgcr0
 Try to Re-Instate ubuntu-artwork
 Try to Re-Instate gvfs-backends
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 10 as a solution to libgnome-keyring0 68
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 10
  Holding Back gnome-keyring rather than change libgcr0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 10 as a solution to libgnome-keyring0 68
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 10
  Holding Back gnome-keyring rather than change libgcr0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 10 as a solution to libgnome-keyring0 68
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 10
  Holding Back gnome-keyring rather than change libgcr0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 10 as a solution to libgnome-keyring0 68
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 10
  Holding Back gnome-keyring rather than change libgcr0
Done
Log time: 2010-08-10 13:18:52.155399


```

MAIN.LOG
```

2010-08-10 13:18:21,308 INFO Using config files '['./DistUpgrade.cfg.hardy']'
2010-08-10 13:18:21,308 INFO uname information: 'Linux kermit 2.6.24-27-server #1 SMP Wed Mar 24 11:32:39 UTC 2010 x86_64'
2010-08-10 13:18:21,308 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2010-08-10 13:18:21,406 INFO release-upgrader version '0.134.7' started
2010-08-10 13:18:21,408 DEBUG Using 'DistUpgradeViewText' view
2010-08-10 13:18:21,437 DEBUG aufsOptionsAndEnvironmentSetup()
2010-08-10 13:18:21,437 DEBUG using '/tmp/upgrade-rw-qjMLgP' as aufs_rw_dir
2010-08-10 13:18:21,438 DEBUG using '/tmp/upgrade-chroot-Fc9tv-' as aufs chroot dir
2010-08-10 13:18:21,438 DEBUG enable dpkg --force-overwrite
2010-08-10 13:18:21,470 DEBUG lsb-release: 'hardy'
2010-08-10 13:18:21,470 DEBUG _pythonSymlinkCheck run
2010-08-10 13:18:21,470 DEBUG openCache()
2010-08-10 13:18:22,005 DEBUG /openCache(), new cache size 25161
2010-08-10 13:18:22,006 DEBUG needServerMode(): can not find a desktop meta package or key deps, running in server mode
2010-08-10 13:18:22,006 DEBUG checkViewDepends()
2010-08-10 13:18:22,006 DEBUG running doUpdate() (showErrors=False)
2010-08-10 13:18:22,298 DEBUG openCache()
2010-08-10 13:18:22,680 DEBUG /openCache(), new cache size 25161
2010-08-10 13:18:22,680 DEBUG doPostInitialUpdate
2010-08-10 13:18:22,680 DEBUG Plugin modules in ./plugins: langpack_manual_plugin.py dpkg_status_plugin.py remove_lilo_plugin.py kdelibs4to5_plugin.py deb_plugin.py
2010-08-10 13:18:22,680 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2010-08-10 13:18:22,681 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2010-08-10 13:18:22,681 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2010-08-10 13:18:22,682 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2010-08-10 13:18:22,682 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2010-08-10 13:18:22,682 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2010-08-10 13:18:22,682 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2010-08-10 13:18:22,683 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2010-08-10 13:18:22,683 DEBUG Loading module ./plugins/deb_plugin.py
2010-08-10 13:18:22,683 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2010-08-10 13:18:22,683 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2010-08-10 13:18:22,683 DEBUG plugins for condition 'lucidPostInitialUpdate' are '[]'
2010-08-10 13:18:22,683 DEBUG plugins for condition 'from_hardyPostInitialUpdate' are '[]'
2010-08-10 13:18:22,683 DEBUG quirks: running lucidPostInitialUpdate
2010-08-10 13:18:22,684 DEBUG running lucidPostInitialUpdate
2010-08-10 13:18:23,625 DEBUG no PkgRecord found for 'jabberd2', skipping 
2010-08-10 13:18:23,913 DEBUG no PkgRecord found for 'libtonezone2.0', skipping 
2010-08-10 13:18:23,963 DEBUG no PkgRecord found for 'virtualbox-3.1', skipping 
2010-08-10 13:18:24,068 DEBUG no PkgRecord found for 'dahdi-linux', skipping 
2010-08-10 13:18:24,075 DEBUG no PkgRecord found for 'timevault', skipping 
2010-08-10 13:18:24,225 DEBUG Foreign: gstreamer0.10-fluendo-plugins-doc gstreamer0.10-fluendo-plugins-wmv-doc
2010-08-10 13:18:24,226 DEBUG Obsolete: linux-image-2.6.24-19-server gsmartcontrol ubuntu-tweak libcap2 linux-headers-2.6.24-19 cksfv linux-headers-2.6.24-19-server samba-common-bin jdownloader libwbclient0 bleachbit avg85flx virtualbox-3.2 libopencore-amr linux-headers-2.6.24-19-generic libtheora dvdwizard libgnutls26
2010-08-10 13:18:24,226 DEBUG updateSourcesList()
2010-08-10 13:18:24,268 DEBUG rewriteSourcesList()
2010-08-10 13:18:24,270 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main #Added by software-properties'
2010-08-10 13:18:24,270 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu/ lucid restricted main #Added by software-properties' updated to new dist
2010-08-10 13:18:24,270 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy main restricted'
2010-08-10 13:18:24,271 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid main restricted' updated to new dist
2010-08-10 13:18:24,271 DEBUG examining: 'deb-src http://be.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties'
2010-08-10 13:18:24,271 DEBUG entry 'deb-src http://be.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties' updated to new dist
2010-08-10 13:18:24,271 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy-updates main restricted'
2010-08-10 13:18:24,271 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid-updates main restricted' updated to new dist
2010-08-10 13:18:24,271 DEBUG examining: 'deb-src http://be.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties'
2010-08-10 13:18:24,271 DEBUG entry 'deb-src http://be.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties' updated to new dist
2010-08-10 13:18:24,271 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy universe'
2010-08-10 13:18:24,271 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid universe' updated to new dist
2010-08-10 13:18:24,271 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy-updates universe'
2010-08-10 13:18:24,271 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid-updates universe' updated to new dist
2010-08-10 13:18:24,271 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy multiverse'
2010-08-10 13:18:24,271 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid multiverse' updated to new dist
2010-08-10 13:18:24,271 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy-updates multiverse'
2010-08-10 13:18:24,272 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid-updates multiverse' updated to new dist
2010-08-10 13:18:24,272 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse'
2010-08-10 13:18:24,272 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse' updated to new dist
2010-08-10 13:18:24,272 DEBUG examining: 'deb http://archive.canonical.com/ubuntu hardy partner'
2010-08-10 13:18:24,272 DEBUG entry 'deb http://archive.canonical.com/ubuntu lucid partner' updated to new dist
2010-08-10 13:18:24,272 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu hardy partner'
2010-08-10 13:18:24,272 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu lucid partner' updated to new dist
2010-08-10 13:18:24,272 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security main restricted'
2010-08-10 13:18:24,272 DEBUG entry 'deb http://security.ubuntu.com/ubuntu lucid-security main restricted' updated to new dist
2010-08-10 13:18:24,272 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties'
2010-08-10 13:18:24,272 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties' updated to new dist
2010-08-10 13:18:24,272 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security universe'
2010-08-10 13:18:24,272 DEBUG entry 'deb http://security.ubuntu.com/ubuntu lucid-security universe' updated to new dist
2010-08-10 13:18:24,273 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security multiverse'
2010-08-10 13:18:24,273 DEBUG entry 'deb http://security.ubuntu.com/ubuntu lucid-security multiverse' updated to new dist
2010-08-10 13:18:24,273 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe'
2010-08-10 13:18:24,273 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe' updated to new dist
2010-08-10 13:18:24,277 DEBUG running doUpdate() (showErrors=True)
2010-08-10 13:18:29,854 DEBUG openCache()
2010-08-10 13:18:33,211 DEBUG /openCache(), new cache size 30356
2010-08-10 13:18:33,212 DEBUG needServerMode(): can not find a desktop meta package or key deps, running in server mode
2010-08-10 13:18:50,041 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2010-08-10 13:18:50,042 DEBUG abort called
2010-08-10 13:18:50,042 DEBUG openCache()
2010-08-10 13:18:52,165 DEBUG /openCache(), new cache size 25161
2010-08-10 13:18:52,166 DEBUG enabling apt cron job


```

I couldn't find any solution on the net.. where should I start?

---

### Post by lechien73 on 2010-08-10
I can see why you've had problems getting to the bottom of it!

Have you tried the solution at post #4 in this bug report? [http://uri.tl/10](http://uri.tl/10)

Sorry this seems like a short response to such a detailed post :)

---

### Post by sydbat on 2010-08-10
Have you tried doing the upgrade through the "Update Manager"?

Also, I am not sure why you have '--proposed' in your first line "sudo do-release-upgrade --proposed". That might be a/the problem.

---

### Post by jverdeyen on 2010-10-01
I'm still having this issue... even when using: sudo do-release-upgrade --proposed

Any other ideas? Thx!

---

### Post by dino99 on 2010-10-01
into synaptic repo tab: only genuine repo (8.04) have to be activated, remove or deactivate all ppa if any. Then clean the system with clean, autoclean, autoremove, then check with install -f

8.04 use grub1 and now its grub2, but menu.lst is not welcome (conflicts), so when grub2 is installed, remove evrything about grub1 and menu.lst, then run: sudo update-grub

now, the kernel deal directly with X, so better to remove xorg.conf before rebooting (avoid some issues): sudo rm -f /etc/X11/xorg.conf

[https://help.ubuntu.com/community/EOLUpgrades/Hardy](https://help.ubuntu.com/community/EOLUpgrades/Hardy)

---

### Post by san_antonio9.10 on 2010-10-01
I THINK THAT YOU SHOULD UPGRADE VIA UPDATE MANAGER , IT  WOULD BE THE SAFER WAY TO ME.  I UPGRADED FROM 9.10 TO 10.04 WITHOUT ANY PROBLEM THROUGH UPDATE MANAGER. YOU CAN CHECK MY BLOG ONCE YOU UPGRADE TO 10.04 ON HOW TO CUSTOMIZE UBUNTU 10.04 DESKTOP

[http://viva-opensource.blogspot.com/](http://viva-opensource.blogspot.com/)

---

### Post by jverdeyen on 2010-10-04
> **dino99 said:**
> into synaptic repo tab: only genuine repo (8.04) have to be activated, remove or deactivate all ppa if any. Then clean the system with clean, autoclean, autoremove, then check with install -f
...


Ok, I'll give that one a try.

@ san_antonio9.10: I don't use 9.10

---

### Post by jverdeyen on 2010-10-04
I'm still havin' these issues...

apt.log

```

Log time: 2010-10-01 19:55:09.491115
Log time: 2010-10-01 19:55:10.343882
Log time: 2010-10-01 19:55:37.863760
Installing libc6 as dep of x11-apps
Installing libc-bin as dep of libc6
Installing findutils as dep of libc6
Installing libmcpp0 as dep of mcpp
Installing libio-compress-perl as dep of libio-compress-base-perl
Installing libcompress-raw-bzip2-perl as dep of libio-compress-perl
Installing perl as dep of libcompress-raw-bzip2-perl
Installing perl-base as dep of perl
Installing dpkg as dep of perl-base
Installing libuuid-perl as dep of doc-base
Installing libuuid1 as dep of libuuid-perl
Installing libmldbm-perl as dep of doc-base
Installing libfreezethaw-perl as dep of libmldbm-perl
Installing perl-modules as dep of perl
Installing libdb4.8 as dep of perl
Installing libcompress-raw-zlib-perl as dep of libio-compress-perl
Installing light-themes as dep of ubuntu-artwork
Installing ubuntu-mono as dep of light-themes
Installing humanity-icon-theme as dep of ubuntu-mono
Installing gtk2-engines-murrine as dep of light-themes
Installing libatk1.0-0 as dep of gtk2-engines-murrine
Installing libfontconfig1 as dep of gtk2-engines-murrine
Installing fontconfig-config as dep of libfontconfig1
Installing libglib2.0-0 as dep of gtk2-engines-murrine
Installing libpcre3 as dep of libglib2.0-0
Installing libgtk2.0-0 as dep of gtk2-engines-murrine
Installing libcairo2 as dep of libgtk2.0-0
Installing libdirectfb-1.2-0 as dep of libcairo2
Installing libts-0.0-0 as dep of libdirectfb-1.2-0
Installing tsconf as dep of libts-0.0-0
Installing libpixman-1-0 as dep of libcairo2
Installing libxcb-render-util0 as dep of libcairo2
Installing libxcb-render0 as dep of libxcb-render-util0
Installing libcups2 as dep of libgtk2.0-0
Installing libgssapi-krb5-2 as dep of libcups2
Installing libk5crypto3 as dep of libgssapi-krb5-2
Installing libkrb5support0 as dep of libk5crypto3
Installing libkrb5-3 as dep of libgssapi-krb5-2
Installing libxrandr2 as dep of libgtk2.0-0
Installing adium-theme-ubuntu as dep of ubuntu-artwork
Installing libmono-security2.0-cil as dep of libmono-data-tds2.0-cil
Installing libmono-system2.0-cil as dep of libmono-security2.0-cil
Installing mono-runtime as dep of libmono-system2.0-cil
Installing mono-gac as dep of mono-runtime
Installing mono-2.0-gac as dep of mono-gac
Installing libcap2 as dep of libsmbclient
Installing libtalloc2 as dep of libsmbclient
Installing libwbclient0 as dep of libsmbclient
Installing libhfsp0 as dep of libhfsp-dev
Installing libbsd0 as dep of libedit2
Installing language-pack-nl as dep of language-pack-nl-base
Installing libsm6 as dep of libsm-dev
Installing perl-tk as dep of libtk-tablematrix-perl
Installing python as dep of python-gnome2
Installing python2.6 as dep of python
Installing python2.6-minimal as dep of python2.6
Installing libssl0.9.8 as dep of python2.6-minimal
Installing libreadline6 as dep of python2.6
Installing libsqlite3-0 as dep of python2.6
Installing python-minimal as dep of python
Installing python-gobject as dep of python-gnome2
Installing python-support as dep of python-gobject
Installing libffi5 as dep of python-gobject
Installing python-gnomecanvas as dep of python-gnome2
Installing python-gtk2 as dep of python-gnome2
Installing python-cairo as dep of python-gtk2
Installing libpango1.0-0 as dep of python-gtk2
Installing libpango1.0-common as dep of libpango1.0-0
Installing libthai0 as dep of libpango1.0-0
Installing libdatrie1 as dep of libthai0
Installing libthai-data as dep of libthai0
Installing python-pyorbit as dep of python-gnome2
Installing libgconf2-4 as dep of python-gnome2
Installing libdbus-glib-1-2 as dep of libgconf2-4
Installing libxml2 as dep of libgconf2-4
Installing gconf2-common as dep of libgconf2-4
Installing libpopt0 as dep of python-gnome2
Installing python-gconf as dep of python-gnome2
Installing libsoup-gnome2.4-1 as dep of libgweather1
Installing libproxy0 as dep of libsoup-gnome2.4-1
Installing libsoup2.4-1 as dep of libsoup-gnome2.4-1
Installing libgweather-common as dep of libgweather1
Installing libstdc++6 as dep of menu
Installing gcc-4.4-base as dep of libstdc++6
Installing openssh-client as dep of openssh-server
Installing libappindicator0 as dep of gnome-power-manager
Installing libdbusmenu-glib1 as dep of libappindicator0
Installing libdbusmenu-gtk1 as dep of libappindicator0
Installing libindicator0 as dep of libappindicator0
Installing libjson-glib-1.0-0 as dep of libappindicator0
Installing indicator-application as dep of libappindicator0
Installing libcanberra-gtk0 as dep of gnome-power-manager
Installing libcanberra0 as dep of libcanberra-gtk0
Installing libasound2 as dep of libcanberra0
Installing libpython2.6 as dep of libasound2
Installing libltdl7 as dep of libcanberra0
Installing libtdb1 as dep of libcanberra0
Installing libcanberra-gtk-module as dep of libcanberra-gtk0
Installing libdevkit-power-gobject1 as dep of gnome-power-manager
Installing libnotify1 as dep of gnome-power-manager
Installing libunique-1.0-0 as dep of gnome-power-manager
Installing upower as dep of gnome-power-manager
Installing libgudev-1.0-0 as dep of upower
Installing libudev0 as dep of libgudev-1.0-0
Installing libpolkit-gobject-1-0 as dep of upower
Installing libeggdbus-1-0 as dep of libpolkit-gobject-1-0
Installing libupower-glib1 as dep of upower
Installing policykit-1 as dep of upower
Installing libpolkit-backend-1-0 as dep of policykit-1
new important dependency: udisks
Installing udisks as dep of gnome-power-manager
Installing libatasmart4 as dep of udisks
Installing libparted0debian1 as dep of udisks
Installing libblkid1 as dep of libparted0debian1
Installing libdevmapper1.02.1 as dep of libparted0debian1
Installing libsgutils2-2 as dep of udisks
Installing mtools as dep of udisks
Installing gnome-settings-daemon as dep of gnome-session
Installing libgnome-desktop-2-17 as dep of gnome-settings-daemon
Installing libstartup-notification0 as dep of libgnome-desktop-2-17
Installing libxcb-atom1 as dep of libstartup-notification0
Installing libxcb-aux0 as dep of libstartup-notification0
Installing libxcb-event1 as dep of libstartup-notification0
Installing libebook1.2-9 as dep of gnome-control-center
Installing libcamel1.2-14 as dep of libebook1.2-9
Installing libedataserver1.2-11 as dep of libcamel1.2-14
Installing libgnome-menu2 as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libgnomekbd4 as dep of gnome-control-center
Installing libxklavier16 as dep of libgnomekbd4
Installing libgnomekbd-common as dep of libgnomekbd4
Installing libmetacity-private0 as dep of gnome-control-center
Installing metacity-common as dep of libmetacity-private0
Installing librsvg2-2 as dep of gnome-control-center
Installing libcroco3 as dep of librsvg2-2
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libxi6 as dep of gnome-control-center
Installing libx11-6 as dep of libxi6
Installing libxcb1 as dep of libx11-6
Installing capplets-data as dep of gnome-control-center
Installing gnome-icon-theme as dep of gnome-control-center
Installing ubuntu-system-service as dep of gnome-control-center
Installing python-central as dep of ubuntu-system-service
new important dependency: policykit-1-gnome
Installing policykit-1-gnome as dep of gnome-control-center
Installing libpolkit-agent-1-0 as dep of policykit-1-gnome
new important dependency: screen-resolution-extra
Installing screen-resolution-extra as dep of gnome-control-center
Installing python-xkit as dep of screen-resolution-extra
Installing libpulse-mainloop-glib0 as dep of gnome-settings-daemon
Installing libpulse0 as dep of libpulse-mainloop-glib0
Installing libsndfile1 as dep of libpulse0
Installing gnome-session-bin as dep of gnome-session
Installing upstart as dep of udev
Installing libdbus-1-3 as dep of upstart
Installing libnih-dbus1 as dep of upstart
Installing libnih1 as dep of libnih-dbus1
Installing sysvinit-utils as dep of upstart
Installing mountall as dep of upstart
Installing plymouth as dep of mountall
Installing libdrm-intel1 as dep of plymouth
Installing libdrm2 as dep of libdrm-intel1
Installing libdrm-nouveau1 as dep of plymouth
Installing libdrm-radeon1 as dep of plymouth
Installing libplymouth2 as dep of plymouth
Installing plymouth-theme-ubuntu-text as dep of plymouth
Installing coreutils as dep of mountall
Installing ifupdown as dep of upstart
Installing netbase as dep of ifupdown
Installing initramfs-tools as dep of udev
Installing initramfs-tools-bin as dep of initramfs-tools
Installing klibc-utils as dep of initramfs-tools
Installing libklibc as dep of klibc-utils
Installing busybox-initramfs as dep of initramfs-tools
Installing util-linux as dep of initramfs-tools
Installing xserver-xorg-core as dep of xserver-xorg
Installing xserver-common as dep of xserver-xorg-core
Installing libpciaccess0 as dep of xserver-xorg-core
new important dependency: libgl1-mesa-dri
Installing libgl1-mesa-dri as dep of xserver-xorg-core
Installing xserver-xorg-video-all as dep of xserver-xorg
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
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing libxvmc1 as dep of xserver-xorg-video-intel
new important dependency: intel-gpu-tools
Installing intel-gpu-tools as dep of xserver-xorg-video-intel
Installing xserver-xorg-video-mga as dep of xserver-xorg-video-all
Installing xserver-xorg-video-neomagic as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nouveau as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nv as dep of xserver-xorg-video-all
Installing xserver-xorg-video-rendition as dep of xserver-xorg-video-all
Installing xserver-xorg-video-s3 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-s3virge as dep of xserver-xorg-video-all
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
Installing xserver-xorg-video-v4l as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vmware as dep of xserver-xorg-video-all
Installing xserver-xorg-input-all as dep of xserver-xorg
Installing xserver-xorg-input-evdev as dep of xserver-xorg-input-all
Installing xserver-xorg-input-synaptics as dep of xserver-xorg-input-all
Installing xserver-xorg-input-vmmouse as dep of xserver-xorg-input-all
Installing xserver-xorg-input-mouse as dep of xserver-xorg-input-vmmouse
Installing xserver-xorg-input-wacom as dep of xserver-xorg-input-all
Installing xkb-data as dep of xserver-xorg
Installing libruby1.8 as dep of ruby1.8-dev
Installing libgconf2.0-cil as dep of tomboy
Installing libglib2.0-cil as dep of libgconf2.0-cil
Installing libgmime2.4-cil as dep of tomboy
Installing libgmime-2.4-2 as dep of libgmime2.4-cil
Installing libgnome2.24-cil as dep of tomboy
Installing libart2.0-cil as dep of libgnome2.24-cil
Installing libglade2.0-cil as dep of libgnome2.24-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libmono-cairo2.0-cil as dep of libgtk2.0-cil
Installing libgnome-vfs2.0-cil as dep of libgnome2.24-cil
Installing libgnomepanel2.24-cil as dep of tomboy
Installing liblaunchpad-integration1.0-cil as dep of tomboy
Installing libmono-addins-gui0.2-cil as dep of tomboy
Installing libmono-addins0.2-cil as dep of libmono-addins-gui0.2-cil
Installing libmono-posix2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libbz2-1.0 as dep of bzip2
Installing libespeak1 as dep of espeak
Installing libportaudio2 as dep of libespeak1
Installing libjack0 as dep of libportaudio2
Installing espeak-data as dep of libespeak1
Installing libidn11 as dep of kdelibs4c2a
Installing libilmbase6 as dep of kdelibs4c2a
Installing libopenexr6 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing kdelibs5-data as dep of kdelibs-data
Installing busybox-static as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: apt-transport-https
Installing apt-transport-https as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing apt as dep of apt-transport-https
new important dependency: irqbalance
Installing irqbalance as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcap-ng0 as dep of irqbalance
Installing cpu-checker as dep of update-notifier-common
new important dependency: libpam-modules
Installing libpam-modules as dep of update-notifier-common
Installing base-files as dep of libpam-modules
Installing libselinux1 as dep of libpam-modules
new important dependency: libgpm2
Installing libgpm2 as dep of libncurses5
Installing kdebase-runtime as dep of kipi-plugins
Installing kdelibs5 as dep of kdebase-runtime
Installing libattica0 as dep of kdelibs5
Installing libqt4-network as dep of libattica0
Installing libqtcore4 as dep of libqt4-network
Installing libdbusmenu-qt2 as dep of kdelibs5
Installing libqt4-dbus as dep of libdbusmenu-qt2
Installing libqt4-xml as dep of libqt4-dbus
Installing libqtgui4 as dep of libdbusmenu-qt2
Installing libenchant1c2a as dep of kdelibs5
Installing libhunspell-1.2-0 as dep of libenchant1c2a
Installing hunspell-en-us as dep of libhunspell-1.2-0
Installing liblzma1 as dep of kdelibs5
Installing libphonon4 as dep of kdelibs5
Installing libqt4-designer as dep of libphonon4
Installing libqt4-script as dep of libqt4-designer
Installing libpolkit-qt-1-0 as dep of kdelibs5
Installing libqt4-qt3support as dep of kdelibs5
Installing libqt4-sql as dep of libqt4-qt3support
Installing libqt4-sql-mysql as dep of libqt4-sql
Installing libmysqlclient16 as dep of libqt4-sql-mysql
Installing mysql-common as dep of libmysqlclient16
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
Installing libstreamanalyzer0 as dep of kdelibs5
Installing libexiv2-6 as dep of libstreamanalyzer0
Installing exiv2 as dep of libexiv2-6
Installing libstreams0 as dep of libstreamanalyzer0
Installing kdelibs-bin as dep of kdelibs5
Installing shared-desktop-ontologies as dep of kdelibs5
Installing libplasma3 as dep of kdebase-runtime
Installing libqca2 as dep of libplasma3
Installing ca-certificates as dep of libqca2
Installing libqt4-opengl as dep of libplasma3
Installing libssh-4 as dep of kdebase-runtime
Installing kdebase-runtime-data as dep of kdebase-runtime
Installing oxygen-icon-theme as dep of kdebase-runtime
Installing phonon-backend-xine as dep of kdebase-runtime
Installing libxine1 as dep of phonon-backend-xine
Installing libxine1-misc-plugins as dep of libxine1
Installing libmagickcore2 as dep of libxine1-misc-plugins
Installing libmagickwand2 as dep of libxine1-misc-plugins
Installing libmodplug0c2 as dep of libxine1-misc-plugins
Installing libmpcdec3 as dep of libxine1-misc-plugins
Installing libspeex1 as dep of libxine1-misc-plugins
Installing libxine1-bin as dep of libxine1-misc-plugins
Installing libxine1-x as dep of libxine1
Installing libxcb-shape0 as dep of libxine1-x
Installing libxcb-shm0 as dep of libxine1-x
Installing libxcb-xv0 as dep of libxine1-x
Installing libxine1-console as dep of libxine1
Installing libcaca0 as dep of libxine1-console
Installing plasma-scriptengine-javascript as dep of kdebase-runtime
Installing icoutils as dep of kdebase-runtime
Installing kubuntu-debug-installer as dep of kdebase-runtime
Installing kpackagekit as dep of kubuntu-debug-installer
Installing libpackagekit-qt-12 as dep of kpackagekit
Installing polkit-kde-1 as dep of kpackagekit
Installing software-properties-kde as dep of kpackagekit
Installing python-qt4 as dep of software-properties-kde
Installing libqt4-assistant as dep of python-qt4
Installing libqt4-help as dep of python-qt4
Installing libqt4-scripttools as dep of python-qt4
Installing libqt4-test as dep of python-qt4
Installing python-sip as dep of python-qt4
Installing python-kde4 as dep of software-properties-kde
Installing kdepimlibs5 as dep of python-kde4
Installing libakonadiprivate1 as dep of kdepimlibs5
Installing libboost-program-options1.40.0 as dep of libakonadiprivate1
Installing libgpg-error0 as dep of kdepimlibs5
Installing libgpgme11 as dep of kdepimlibs5
Installing libical0 as dep of kdepimlibs5
Installing kdepimlibs-data as dep of kdepimlibs5
Installing phonon as dep of python-kde4
Installing install-package as dep of software-properties-kde
Installing gdebi-kde as dep of install-package
Installing gdebi-core as dep of gdebi-kde
Installing python-debian as dep of gdebi-core
Installing kdesudo as dep of gdebi-kde
Installing packagekit as dep of kpackagekit
Installing libnm-glib2 as dep of packagekit
Installing libnm-util1 as dep of libnm-glib2
Installing libgnome-bluetooth7 as dep of network-manager-gnome
Installing network-manager as dep of network-manager-gnome
Installing wpasupplicant as dep of network-manager
Installing libpcsclite1 as dep of wpasupplicant
new important dependency: dnsmasq-base
Installing dnsmasq-base as dep of network-manager
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
Installing libgpod4 as dep of kipi-plugins
Installing libimobiledevice0 as dep of libgpod4
Installing libplist1 as dep of libimobiledevice0
Installing libtasn1-3 as dep of libimobiledevice0
Installing libusbmuxd1 as dep of libimobiledevice0
Installing usbmuxd as dep of libimobiledevice0
Installing libusb-1.0-0 as dep of usbmuxd
Installing libkdcraw8 as dep of kipi-plugins
Installing libkexiv2-8 as dep of kipi-plugins
Installing libkipi7 as dep of kipi-plugins
Installing libksane0 as dep of kipi-plugins
Installing libsane as dep of libksane0
Installing libgphoto2-2 as dep of libsane
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libieee1284-3 as dep of libsane
Installing libv4l-0 as dep of libsane
Installing cups as dep of openprinting-ppds
Installing libcupscgi1 as dep of cups
Installing libcupsdriver1 as dep of cups
Installing libcupsimage2 as dep of cups
Installing libcupsmime1 as dep of cups
Installing libcupsppdc1 as dep of cups
Installing libijs-0.35 as dep of cups
Installing libpoppler5 as dep of cups
Installing libslp1 as dep of cups
Installing poppler-utils as dep of cups
Installing cups-common as dep of cups
Installing cups-client as dep of cups
Installing foomatic-filters as dep of cups
Installing cups-driver-gutenprint as dep of cups
Installing libgutenprint2 as dep of cups-driver-gutenprint
Installing ghostscript-cups as dep of cups-driver-gutenprint
Installing ghostscript as dep of ghostscript-cups
Installing libgs8 as dep of ghostscript
new important dependency: libxml-sax-expat-perl
Installing libxml-sax-expat-perl as dep of libxml-sax-perl
new important dependency: ttf-sazanami-mincho
Installing ttf-sazanami-mincho as dep of ttf-kochi-mincho
Installing console-terminus as dep of console-setup
Installing kbd as dep of console-setup
Installing libice6 as dep of libice-dev
Installing python-twisted-core as dep of python-twisted-mail
Installing python-twisted-bin as dep of python-twisted-core
Installing python-zope.interface as dep of python-twisted-core
Installing python-pkg-resources as dep of python-zope.interface
new important dependency: python-openssl
Installing python-openssl as dep of python-twisted-core
Installing x11proto-randr-dev as dep of libxrandr-dev
Installing libgstreamer-plugins-base0.10-0 as dep of gnome-media
Installing libgstreamer0.10-0 as dep of libgstreamer-plugins-base0.10-0
Installing libmono-data-tds1.0-cil as dep of libmono-system-data1.0-cil
Installing libmono-security1.0-cil as dep of libmono-data-tds1.0-cil
Installing libpolkit2 as dep of libpolkit-dbus2
Installing compiz-core as dep of compiz-gnome
Installing libprotobuf5 as dep of libcompizconfig0
Installing compiz-plugins as dep of compiz-gnome
Installing libexempi3 as dep of nautilus
Installing libnautilus-extension1 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing shared-mime-info as dep of nautilus
Installing gvfs as dep of nautilus
Installing libgdu0 as dep of gvfs
Installing libgvfscommon0 as dep of gvfs
Installing libglib2.0-data as dep of nautilus
Installing libmono-posix1.0-cil as dep of libmono1.0-cil
Installing libexpat1 as dep of libexpat1-dev
Installing libcdio10 as dep of libcdio-paranoia0
Installing libesd0 as dep of libgnome2-0
Installing esound-common as dep of libesd0
new important dependency: esound-clients
Installing esound-clients as dep of esound-common
Installing libgnome2-common as dep of libgnome2-0
Installing libcdparanoia0 as dep of cdparanoia
Installing librrds-perl as dep of munin
Installing librrd4 as dep of librrds-perl
Installing liblog-log4perl-perl as dep of munin
Installing munin-common as dep of munin
Installing libglib2.0-dev as dep of gnome-settings-daemon-dev
Installing libbind9-60 as dep of bind9-host
Installing libdns64 as dep of libbind9-60
Installing libgeoip1 as dep of libdns64
Installing geoip-database as dep of libgeoip1
Installing libisc60 as dep of libdns64
Installing libisccfg60 as dep of libbind9-60
Installing libisccc60 as dep of libisccfg60
Installing liblwres60 as dep of bind9-host
Installing swi-prolog as dep of swi-prolog-http
Installing libgmp3-dev as dep of swi-prolog
Installing libgmp3c2 as dep of libgmp3-dev
Installing libgmpxx4ldbl as dep of libgmp3-dev
Installing libreadline-dev as dep of swi-prolog
Installing libreadline6-dev as dep of libreadline-dev
Installing libncurses5-dev as dep of libreadline6-dev
Installing libgamin0 as dep of gamin
Installing dpkg-dev as dep of debhelper
Installing xz-utils as dep of dpkg-dev
Installing libaspell15 as dep of aspell
Installing libuniconf4.6 as dep of wvdial
Installing libwvstreams4.6-base as dep of libuniconf4.6
Installing libwvstreams4.6-extras as dep of libuniconf4.6
Installing ruby1.8 as dep of irb1.8
Installing libreadline-ruby1.8 as dep of irb1.8
Installing libxdamage1 as dep of libxdamage-dev
Installing libpoppler-glib4 as dep of tracker
Installing libtotem-plparser17 as dep of tracker
new important dependency: odt2txt
Installing odt2txt as dep of tracker
Installing libzip1 as dep of odt2txt
Installing ia32-libs as dep of nspluginwrapper
Installing lib32bz2-1.0 as dep of ia32-libs
Installing libc6-i386 as dep of lib32bz2-1.0
Installing lib32v4l-0 as dep of ia32-libs
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing libraw1394-11 as dep of libavc1394-0
Installing libnewt0.52 as dep of whiptail
Installing liblua5.1-0 as dep of nmap
Installing libpcap0.8 as dep of nmap
Installing linux-image-server as dep of linux-server
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing linux-image-2.6.32-25-server as dep of linux-image-server
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing wireless-crda as dep of linux-image-2.6.32-25-server
Installing linux-firmware as dep of linux-image-server
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libgucharmap7 as dep of gucharmap
Installing libatspi1.0-0 as dep of brltty-x11
Installing brltty as dep of brltty-x11
Installing libicu42 as dep of brltty
Installing totem as dep of totem-plugins
Installing gstreamer0.10-plugins-base as dep of totem
Installing libtheora0 as dep of gstreamer0.10-plugins-base
Installing totem-common as dep of totem
Installing totem-mozilla as dep of totem
Installing libbluetooth3 as dep of totem-plugins
Installing libgdata6 as dep of totem-plugins
Installing libgdata-common as dep of libgdata6
Installing python-rdflib as dep of totem-plugins
Installing python-httplib2 as dep of totem-plugins
Installing python-gnomeapplet as dep of computertemp
Installing tk as dep of x11vnc
Installing tcl as dep of tk
Installing software-center as dep of gnome-app-install
Installing python-aptdaemon as dep of software-center
Installing aptdaemon as dep of python-aptdaemon
Installing python-aptdaemon-gtk as dep of software-center
Installing python-webkit as dep of software-center
Installing libwebkit-1.0-2 as dep of python-webkit
Installing libwebkit-1.0-common as dep of libwebkit-1.0-2
Installing libspeexdsp1 as dep of pulseaudio
Installing libasound2-plugins as dep of pulseaudio
new important dependency: rtkit
Installing rtkit as dep of pulseaudio
Installing libgnomeui-common as dep of libgnomeui-0
new important dependency: obex-data-server
Installing obex-data-server as dep of gvfs-backends
Installing libopenobex1 as dep of obex-data-server
Installing libglib-perl as dep of libgtk2-perl
Installing libpango-perl as dep of libgtk2-perl
Installing libossp-uuid16 as dep of libossp-uuid-perl
Installing python-twisted-web as dep of python-twisted-lore
new important dependency: libmono-i18n-west2.0-cil
Installing libmono-i18n-west2.0-cil as dep of libmono-corlib2.0-cil
Installing policykit as dep of policykit-gnome
Installing libcairomm-1.0-1 as dep of libgtkmm-2.4-1c2a
Installing libglibmm-2.4-1c2a as dep of libgtkmm-2.4-1c2a
Installing libpangomm-1.4-1 as dep of libgtkmm-2.4-1c2a
Installing odbcinst as dep of odbcinst1debian1
Installing lynx-cur as dep of lynx
Installing libfile-copy-recursive-perl as dep of update-inetd
Installing libavcodec52 as dep of libquicktime1
Installing libavutil49 as dep of libavcodec52
Installing libgsm1 as dep of libavcodec52
Installing libschroedinger-1.0-0 as dep of libavcodec52
Installing liboil0.3 as dep of libschroedinger-1.0-0
Installing libfaad2 as dep of libquicktime1
Installing libswscale0 as dep of libquicktime1
Installing libapache2-mod-php5 as dep of php5
Installing php5-common as dep of libapache2-mod-php5
Installing at-spi as dep of python-pyatspi
Installing libevent-1.4-2 as dep of transmission-cli
Installing transmission-common as dep of transmission-cli
Installing rubygems1.8 as dep of rubygems
Installing mesa-common-dev as dep of libgl1-mesa-dev
Installing libdrm-dev as dep of mesa-common-dev
Installing linux-libc-dev as dep of libdrm-dev
Installing e2fslibs as dep of testdisk
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing python-gtksourceview2 as dep of gedit
Installing libcryptui0 as dep of seahorse
Installing libgnome-keyring0 as dep of seahorse
Installing libgcr0 as dep of gnome-keyring
Installing libgp11-0 as dep of libgcr0
Installing gnupg as dep of seahorse
new important dependency: gnupg-curl
Installing gnupg-curl as dep of gnupg
Installing python-gmenu as dep of gnome-menus
Installing python-xdg as dep of python-gmenu
Installing readahead-fedora as dep of readahead
Installing libaudit0 as dep of readahead-fedora
Installing libvte9 as dep of gnome-terminal
Installing gnome-terminal-data as dep of gnome-terminal
Installing libcrack2 as dep of netatalk
Installing cracklib-runtime as dep of libcrack2
Installing wamerican as dep of cracklib-runtime
new important dependency: db4.8-util
Installing db4.8-util as dep of netatalk
Installing xml-core as dep of docbook-xml
Installing libvorbis0a as dep of libvorbis-dev
Installing libvorbisenc2 as dep of libvorbis-dev
Installing libvorbisfile3 as dep of libvorbis-dev
Installing libxinerama1 as dep of libxinerama-dev
new important dependency: byobu
Installing byobu as dep of screen
Installing python-newt as dep of byobu
Installing libyaml-syck-perl as dep of libdate-manip-perl
Installing x11proto-input-dev as dep of libxi-dev
Installing python-pyasn1 as dep of python-twisted-conch
Installing libept0 as dep of aptitude
Installing xserver-xorg-video-openchrome as dep of xserver-xorg-video-via
Installing xmltv-util as dep of xmltv-gui
Installing libxml-dom-perl as dep of xmltv-util
Installing libxml-perl as dep of libxml-dom-perl
Installing libxml-regexp-perl as dep of libxml-dom-perl
Installing libxml-libxslt-perl as dep of xmltv-util
Installing libxml-libxml-perl as dep of libxml-libxslt-perl
Installing libdatetime-format-strptime-perl as dep of xmltv-util
Installing libdatetime-perl as dep of libdatetime-format-strptime-perl
Installing libdatetime-locale-perl as dep of libdatetime-perl
Installing liblist-moreutils-perl as dep of libdatetime-locale-perl
Installing libparams-validate-perl as dep of libdatetime-locale-perl
Installing libdatetime-timezone-perl as dep of libdatetime-perl
Installing libclass-singleton-perl as dep of libdatetime-timezone-perl
Installing python2.6-dev as dep of python-dev
new important dependency: xinput
Installing xinput as dep of acpi-support
Installing libgdiplus as dep of libmono-system-web1.0-cil
Installing libsvn1 as dep of subversion
Installing libaprutil1 as dep of libsvn1
Installing apache2.2-bin as dep of apache2.2-common
Installing libaprutil1-dbd-sqlite3 as dep of apache2.2-bin
Installing libaprutil1-ldap as dep of apache2.2-bin
Installing libneon27-gnutls as dep of libsvn1
Installing libscim8c2a as dep of scim
Installing krb5-multidev as dep of libkrb5-dev
Installing libgssrpc4 as dep of krb5-multidev
Installing libkadm5srv-mit7 as dep of krb5-multidev
Installing libkdb5-4 as dep of libkadm5srv-mit7
Installing libkadm5clnt-mit7 as dep of krb5-multidev
Installing python-apport as dep of apport
Installing python-launchpadlib as dep of python-apport
Installing python-simplejson as dep of python-launchpadlib
Installing libjs-jquery as dep of python-simplejson
Installing python-wadllib as dep of python-launchpadlib
Installing python-lazr.uri as dep of python-wadllib
Installing python-lazr.restfulclient as dep of python-launchpadlib
Installing python-oauth as dep of python-launchpadlib
new important dependency: apport-symptoms
Installing apport-symptoms as dep of apport
Installing cpp as dep of g++
Installing cpp-4.4 as dep of cpp
Installing libmpfr1ldbl as dep of cpp-4.4
Installing gcc as dep of g++
Installing gcc-4.4 as dep of gcc
Installing binutils as dep of gcc-4.4
Installing libgcc1 as dep of gcc-4.4
Installing g++-4.4 as dep of g++
Installing libstdc++6-4.4-dev as dep of g++-4.4
Installing netcat-openbsd as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing rsyslog as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing ureadahead as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libavahi-client3 as dep of libavahi-client-dev
Installing libogg0 as dep of libogg-dev
Installing python-twisted-names as dep of python-twisted
Installing python-twisted-runner as dep of python-twisted
Installing sun-java6-jre as dep of sun-java6-bin
Installing checkbox-gtk as dep of hwtest-gtk
Installing checkbox as dep of checkbox-gtk
Installing libgd2-xpm as dep of php5-gd
Installing firefox as dep of firefox-branding
Installing libdb4.8-dev as dep of libdb-dev
Installing libcurl3 as dep of libcurl4-openssl-dev
Installing libiec61883-0 as dep of gstreamer0.10-plugins-good
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libtag1-vanilla as dep of libtag1c2a
Installing libdvdread4 as dep of dvdauthor
Installing libdvdnav4 as dep of libdvdread4
Installing libcupsys2 as dep of libcupsys2-dev
Installing update-manager-core as dep of update-manager
new important dependency: software-properties-gtk
Installing software-properties-gtk as dep of update-manager
new important dependency: libltdl-dev
Installing libltdl-dev as dep of libtool
Installing libgdict-1.0-6 as dep of gnome-utils
Installing libopenal1 as dep of libalut0
Installing libpci3 as dep of vbetool
Installing gconf-defaults-service as dep of gconf-editor
new important dependency: samba-common-bin
Installing samba-common-bin as dep of samba-common
Installing libsdl1.2debian as dep of libsdl1.2-dev
Installing libasound2-dev as dep of libsdl1.2-dev
Installing libesd0-dev as dep of libsdl1.2-dev
Installing libaudiofile-dev as dep of libesd0-dev
Installing libaudiofile0 as dep of libaudiofile-dev
Installing libpulse-dev as dep of libsdl1.2-dev
Installing libpulse-browse0 as dep of libpulse-dev
Installing libxt-dev as dep of libpulse-dev
Installing libxt6 as dep of libxt-dev
Installing libdirectfb-dev as dep of libsdl1.2-dev
Installing libdirectfb-extra as dep of libdirectfb-dev
Installing libjpeg62-dev as dep of libdirectfb-dev
Installing libjpeg62 as dep of libjpeg62-dev
Installing libsysfs-dev as dep of libdirectfb-dev
Installing libsysfs2 as dep of libsysfs-dev
Installing libaa1-dev as dep of libsdl1.2-dev
Installing libslang2-dev as dep of libaa1-dev
Installing libslang2 as dep of libslang2-dev
Installing libcaca-dev as dep of libsdl1.2-dev
Installing libaudio-dev as dep of libsdl1.2-dev
Installing libaudio2 as dep of libaudio-dev
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing bluetooth as dep of bluez-utils
Installing bluez as dep of bluetooth
Installing bluez-alsa as dep of bluetooth
Installing bluez-cups as dep of bluetooth
Installing bluez-gstreamer as dep of bluetooth
Installing python-speechd as dep of gnome-orca
Installing speech-dispatcher as dep of python-speechd
Installing libdotconf1.0 as dep of speech-dispatcher
Installing libspeechd2 as dep of speech-dispatcher
Installing python-louis as dep of gnome-orca
Installing liblouis0 as dep of python-louis
Installing liblouis-data as dep of liblouis0
Installing libfaac0 as dep of libfaac-dev
Installing libiw30 as dep of wireless-tools
Installing libavformat52 as dep of gstreamer0.10-ffmpeg
Installing libpostproc51 as dep of gstreamer0.10-ffmpeg
Installing tcl8.5 as dep of python-tk
Installing tk8.5 as dep of python-tk
Installing gnome-desktop-data as dep of gnome-about
Installing libtask-weaken-perl as dep of libsoap-lite-perl
Installing x11proto-xext-dev as dep of x11proto-fixes-dev
Installing libxext6 as dep of libxext-dev
Installing git-core as dep of gitweb
Installing libemail-date-format-perl as dep of libemail-date-perl
Installing diffutils as dep of diff
Installing libwww-perl as dep of libwww-mechanize-perl
Installing libhttp-server-simple-perl as dep of libwww-mechanize-perl
Installing evolution-data-server-common as dep of libedataserverui1.2-8
Installing python-configobj as dep of bzr
new important dependency: smartdimmer
Installing smartdimmer as dep of hal
Installing libglu1-mesa as dep of libglu1-mesa-dev
Installing libmono-system-web2.0-cil as dep of libmono2.0-cil
Installing libmono-sqlite2.0-cil as dep of libmono-system-web2.0-cil
Installing libsqlite0 as dep of libmono-sqlite2.0-cil
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
new important dependency: indicator-applet
Installing indicator-applet as dep of gnome-panel
Installing indicator-messages as dep of indicator-applet
Installing libindicate4 as dep of indicator-messages
Installing indicator-sound as dep of indicator-applet
Installing libido-0.1-0 as dep of indicator-sound
Installing libgnomevfs2-0-dbg as dep of gnome-dbg
Installing libgnomevfs2-0 as dep of libgnomevfs2-0-dbg
Installing libgtk2.0-0-dbg as dep of gnome-dbg
Installing libgnome2-dbg as dep of gnome-dbg
Installing libgnomecanvas2-dbg as dep of gnome-dbg
Installing libgnomeui-0-dbg as dep of gnome-dbg
Installing nautilus-dbg as dep of gnome-dbg
Installing libpango1.0-0-dbg as dep of gnome-dbg
Installing librsvg2-dbg as dep of gnome-dbg
Installing totem-dbg as dep of gnome-dbg
Installing evolution-data-server-dbg as dep of gnome-dbg
Installing evolution-data-server as dep of evolution-data-server-dbg
Installing libebackend1.2-0 as dep of evolution-data-server
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing libegroupwise1.2-13 as dep of evolution-data-server
Installing libgdata-google1.2-1 as dep of evolution-data-server
Installing libgdata1.2-1 as dep of libgdata-google1.2-1
Installing evolution-dbg as dep of gnome-dbg
Installing evolution as dep of evolution-dbg
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgtkhtml-editor0 as dep of evolution
Installing libgtkhtml3.14-19 as dep of libgtkhtml-editor0
Installing libgtkhtml-editor-common as dep of libgtkhtml-editor0
Installing liblpint-bonobo0 as dep of evolution
Installing evolution-common as dep of evolution
Installing evolution-plugins as dep of evolution
Installing libpst4 as dep of evolution-plugins
Installing evolution-webcal as dep of evolution
Installing python-gtk2-dbg as dep of gnome-dbg
Installing python-dbg as dep of python-gtk2-dbg
Installing python2.6-dbg as dep of python-dbg
Installing python-numpy-dbg as dep of python-gtk2-dbg
Installing python-numpy as dep of python-numpy-dbg
Installing libblas3gf as dep of python-numpy
Installing libgfortran3 as dep of libblas3gf
Installing liblapack3gf as dep of python-numpy
Installing python-cairo-dbg as dep of python-gtk2-dbg
Installing python-gobject-dbg as dep of python-gtk2-dbg
Installing libgsf-gnome-1-114-dbg as dep of gnome-dbg
Installing libgsf-gnome-1-114 as dep of libgsf-gnome-1-114-dbg
Installing libgsf-1-114-dbg as dep of libgsf-gnome-1-114-dbg
Installing gstreamer0.10-plugins-base-dbg as dep of gnome-dbg
Installing gstreamer0.10-x as dep of gstreamer0.10-plugins-base-dbg
Installing gstreamer0.10-plugins-good-dbg as dep of gnome-dbg
Installing gstreamer0.10-pulseaudio as dep of gstreamer0.10-plugins-good-dbg
Installing gstreamer0.10-esd as dep of gstreamer0.10-plugins-good-dbg
Installing gstreamer0.10-plugins-ugly-dbg as dep of gnome-dbg
Installing gstreamer0.10-plugins-ugly as dep of gstreamer0.10-plugins-ugly-dbg
Installing libid3tag0 as dep of gstreamer0.10-plugins-ugly
Installing libmad0 as dep of gstreamer0.10-plugins-ugly
Installing libopencore-amrnb0 as dep of gstreamer0.10-plugins-ugly
Installing libopencore-amrwb0 as dep of gstreamer0.10-plugins-ugly
Installing libsidplay1 as dep of gstreamer0.10-plugins-ugly
Installing libtwolame0 as dep of gstreamer0.10-plugins-ugly
Installing libgstreamer0.10-0-dbg as dep of gnome-dbg
Installing libgtkhtml3.14-dbg as dep of gnome-dbg
Installing anjuta-dbg as dep of gnome-dbg
Installing anjuta as dep of anjuta-dbg
Installing libdevhelp-1-1 as dep of anjuta
Installing devhelp-common as dep of libdevhelp-1-1
Installing libgda-4.0-4 as dep of anjuta
Installing libgda-4.0-common as dep of libgda-4.0-4
Installing libgdl-1-3 as dep of anjuta
Installing libgladeui-1-9 as dep of anjuta
Installing libvala0 as dep of anjuta
Installing anjuta-common as dep of anjuta
Installing exuberant-ctags as dep of anjuta
Installing autogen as dep of anjuta
Installing guile-1.8-libs as dep of autogen
Installing libopts25 as dep of autogen
Installing libopts25-dev as dep of autogen
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
Installing libavahi-gobject0 as dep of epiphany-browser
Installing libgirepository1.0-0 as dep of epiphany-browser
Installing libseed0 as dep of epiphany-browser
Installing gnome-js-common as dep of libseed0
Installing gir1.0-glib-2.0 as dep of libseed0
Installing gir1.0-clutter-1.0 as dep of libseed0
Installing gir1.0-freedesktop as dep of gir1.0-clutter-1.0
Installing gir1.0-pango-1.0 as dep of gir1.0-clutter-1.0
Installing libclutter-1.0-0 as dep of gir1.0-clutter-1.0
Installing gir1.0-gstreamer-0.10 as dep of libseed0
Installing gir1.0-gtk-2.0 as dep of libseed0
Installing gir1.0-atk-1.0 as dep of gir1.0-gtk-2.0
Installing libwebkit-1.0-2-dbg as dep of epiphany-browser-dbg
Installing eog-dbg as dep of gnome-dbg
Installing libgdl-1-dbg as dep of gnome-dbg
Installing libgda3-3-dbg as dep of gnome-dbg
Installing libgda3-3 as dep of libgda3-3-dbg
Installing libgda3-common as dep of libgda3-3
Installing libloudmouth1-0-dbg as dep of gnome-dbg
Installing libloudmouth1-0 as dep of libloudmouth1-0-dbg
Installing gimp-dbg as dep of gnome-dbg
Installing gimp as dep of gimp-dbg
Installing libgimp2.0 as dep of gimp
Installing gimp-data as dep of libgimp2.0
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
Installing system-tools-backends as dep of liboobs-1-4
Installing libnet-dbus-perl as dep of system-tools-backends
Installing libxft2-dbg as dep of gnome-dbg
Installing libxml2-dbg as dep of gnome-dbg
Installing rhythmbox-dbg as dep of gnome-dbg
Installing rhythmbox as dep of rhythmbox-dbg
Installing media-player-info as dep of rhythmbox
Installing rhythmbox-plugins as dep of rhythmbox
Installing libmtp8 as dep of rhythmbox-plugins
Installing libmusicbrainz4c2a as dep of rhythmbox-plugins
Installing python-mako as dep of rhythmbox-plugins
Installing rhythmbox-plugin-cdrecorder as dep of rhythmbox
Installing libbrasero-media0 as dep of rhythmbox-plugin-cdrecorder
Installing brasero-common as dep of libbrasero-media0
Installing usplash as dep of usplash-theme-ubuntu
new important dependency: sensible-utils
Installing sensible-utils as dep of devscripts
Installing libpam-runtime as dep of cron
Installing scim-modules-socket as dep of scim-gtk2-immodule
new important dependency: fancontrol
Installing fancontrol as dep of lm-sensors
Installing linux-headers-2.6.32-25-generic as dep of linux-headers-generic
Installing linux-headers-2.6.32-25 as dep of linux-headers-2.6.32-25-generic
Installing openssl as dep of ssl-cert
Installing libavdevice52 as dep of ffmpeg
Installing libdc1394-22 as dep of libavdevice52
Installing libavfilter0 as dep of ffmpeg
Installing zlib1g as dep of zlib1g-dev
Installing hugs as dep of libhugs-haskell98-bundled
Installing libmjpegtools-1.9 as dep of transcode
Installing libmp3lame0 as dep of transcode
new important dependency: twolame
Installing twolame as dep of transcode
Installing libmagic1 as dep of file
Installing libxcb-render0-dev as dep of libcairo2-dev
Installing libxcb-render-util0-dev as dep of libcairo2-dev
Installing wine1.2 as dep of wine
Installing ttf-symbol-replacement as dep of wine1.2
Installing wine1.2-gecko as dep of wine1.2
Installing ttf-mscorefonts-installer as dep of wine1.2
Installing cabextract as dep of ttf-mscorefonts-installer
Installing libjs-mootools as dep of phpmyadmin
Installing javascript-common as dep of libjs-mootools
Installing wwwconfig-common as dep of javascript-common
Installing libsox1a as dep of sox
Installing libsox-fmt-base as dep of libsox1a
Installing libsox-fmt-alsa as dep of libsox1a
Installing vim-runtime as dep of vim
Installing dhcp3-common as dep of dhcp3-client
Installing libavidemux0 as dep of avidemux-cli
Installing lame as dep of libavidemux0
new important dependency: avidemux-plugins-cli
Installing avidemux-plugins-cli as dep of avidemux-cli
Installing avidemux-plugins-common as dep of avidemux-plugins-cli
Installing libx264-85 as dep of avidemux-plugins-common
Installing xulrunner-1.9.2 as dep of yelp
Installing gnome-doc-utils as dep of yelp
Installing rarian-compat as dep of scrollkeeper
new important dependency: libmono-i18n-west1.0-cil
Installing libmono-i18n-west1.0-cil as dep of libmono-corlib1.0-cil
Installing libgksu2-0 as dep of gksu
Installing python-pycurl as dep of landscape-client
Installing libcurl3-gnutls as dep of python-pycurl
Installing landscape-common as dep of landscape-client
Installing python-smartpm as dep of landscape-common
Installing python-pexpect as dep of python-smartpm
new important dependency: nvidia-common
Installing nvidia-common as dep of jockey-common
Installing nvidia-current-modaliases as dep of nvidia-common
Installing nvidia-173-modaliases as dep of nvidia-common
Installing nvidia-96-modaliases as dep of nvidia-common
new important dependency: fglrx-modaliases
Installing fglrx-modaliases as dep of jockey-common
new important dependency: bcmwl-modaliases
Installing bcmwl-modaliases as dep of jockey-common
Installing conky-all as dep of conky
Installing libimlib2 as dep of conky-all
Installing libc-dev-bin as dep of libc6-dev
Installing manpages-dev as dep of libc-dev-bin
Installing libavahi-core6 as dep of avahi-daemon
Installing libmpg123-0 as dep of mpg123
Installing libbonoboui2-common as dep of libbonoboui2-0
new important dependency: python-appindicator
Installing python-appindicator as dep of jockey-gtk
Installing xorg-docs-core as dep of xorg
new important dependency: hpijs
Installing hpijs as dep of foomatic-db
Installing libhpmud0 as dep of hpijs
Installing libsnmp15 as dep of libhpmud0
Installing libsnmp-base as dep of libsnmp15
Installing libperl5.10 as dep of libsnmp15
new important dependency: lockfile-progs
Installing lockfile-progs as dep of ntpdate
new important dependency: libmagickcore2-extra
Installing libmagickcore2-extra as dep of imagemagick
Installing grub-common as dep of grub
Installing os-prober as dep of grub-common
Installing flashplugin-installer as dep of flashplugin-nonfree
Installing python-smbc as dep of system-config-printer-common
Installing python-cupshelpers as dep of system-config-printer-common
new important dependency: system-config-printer-udev
Installing system-config-printer-udev as dep of system-config-printer-common
new important dependency: avahi-utils
Installing avahi-utils as dep of system-config-printer-common
Installing install-info as dep of info
Installing p7zip-full as dep of p7zip-rar
Installing insserv as dep of sysv-rc
Installing libavahi-common3 as dep of libavahi-common-dev
Installing gnome-themes-selected as dep of gnome-themes
new important dependency: libnet-libidn-perl
Installing libnet-libidn-perl as dep of libio-socket-ssl-perl
new important dependency: libmime-types-perl
Installing libmime-types-perl as dep of libmime-lite-perl
Installing libntfs-3g75 as dep of ntfs-3g
Installing python-bugbuddy as dep of python-gnome2-desktop
Installing python-evince as dep of python-gnome2-desktop
Installing python-evolution as dep of python-gnome2-desktop
Installing python-gnomedesktop as dep of python-gnome2-desktop
Installing python-gnomekeyring as dep of python-gnome2-desktop
Installing python-gnomeprint as dep of python-gnome2-desktop
Installing python-gtop as dep of python-gnome2-desktop
Installing python-mediaprofiles as dep of python-gnome2-desktop
Installing python-metacity as dep of python-gnome2-desktop
Installing python-rsvg as dep of python-gnome2-desktop
Installing python-totem-plparser as dep of python-gnome2-desktop
Installing python-wnck as dep of python-gnome2-desktop
Installing libuu0 as dep of uudeview
Starting
Starting 2
Investigating libc6
Package libc6 has broken dep on belocs-locales-bin
  Considering belocs-locales-bin -2 as a solution to libc6 11660
  Added belocs-locales-bin to the remove list
  Fixing libc6 via remove of belocs-locales-bin
Investigating libxcb1
Package libxcb1 has broken dep on libxcb-xlib0
  Considering libxcb-xlib0 1 as a solution to libxcb1 422
  Added libxcb-xlib0 to the remove list
  Fixing libxcb1 via remove of libxcb-xlib0
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to libcups2 261
  Added libcupsys2 to the remove list
  Fixing libcups2 via remove of libcupsys2
Investigating libthai0
Package libthai0 has broken dep on libdatrie0
  Considering libdatrie0 -1 as a solution to libthai0 169
  Added libdatrie0 to the remove list
  Fixing libthai0 via remove of libdatrie0
Investigating mono-runtime
Package mono-runtime has broken dep on mono-common
  Considering mono-common 1 as a solution to mono-runtime 145
  Added mono-common to the remove list
Package mono-runtime has broken dep on mono-jit
  Considering mono-jit -1 as a solution to mono-runtime 145
  Added mono-jit to the remove list
  Fixing mono-runtime via remove of mono-common
  Fixing mono-runtime via remove of mono-jit
Investigating xserver-xorg-core
Package xserver-xorg-core has broken dep on xserver-xorg-input-2
  Considering xserver-xorg-input-kbd -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-input-kbd to the remove list
  Considering xserver-xorg-input-mouse 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-input-synaptics 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-input-evdev 4 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-input-wacom 1 as a solution to xserver-xorg-core 81
Package xserver-xorg-core has broken dep on xserver-xorg-video-2
  Considering xserver-xorg-video-tseng 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-siliconmotion 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-ati 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-via 0 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-nv 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-i810 -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-video-i810 to the remove list
  Considering xserver-xorg-video-intel 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-chips 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-tga -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-video-tga to the remove list
  Considering xserver-xorg-video-trident 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-s3 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-vga -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-video-vga to the remove list
  Considering xserver-xorg-video-i128 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-mga 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-neomagic 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-cirrus 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-ark 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-tdfx 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-sisusb 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-dummy 0 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-rendition 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-vesa 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-cyrix -1 as a solution to xserver-xorg-core 81
  Added xserver-xorg-video-cyrix to the remove list
  Considering xserver-xorg-video-glint 0 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-fbdev 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-savage 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-openchrome 2 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-s3virge 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-voodoo 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-apm 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-sis 1 as a solution to xserver-xorg-core 81
  Considering xserver-xorg-video-v4l 1 as a solution to xserver-xorg-core 81
  Fixing xserver-xorg-core via remove of xserver-xorg-input-kbd
  Fixing xserver-xorg-core via remove of xserver-xorg-video-i810
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tga
  Fixing xserver-xorg-core via remove of xserver-xorg-video-vga
  Fixing xserver-xorg-core via remove of xserver-xorg-video-cyrix
Investigating upstart
Package upstart has broken dep on startup-tasks
  Considering startup-tasks 2 as a solution to upstart 60
  Added startup-tasks to the remove list
Package upstart has broken dep on system-services
  Considering system-services 2 as a solution to upstart 60
  Added system-services to the remove list
Package upstart has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 5 as a solution to upstart 60
  Added upstart-compat-sysv to the remove list
  Fixing upstart via remove of startup-tasks
  Fixing upstart via remove of system-services
  Fixing upstart via remove of upstart-compat-sysv
Investigating php5-common
Package php5-common has broken dep on php5-mhash
  Considering php5-mhash -1 as a solution to php5-common 20
  Added php5-mhash to the remove list
  Fixing php5-common via remove of php5-mhash
Investigating console-setup
Package console-setup has broken dep on kbd
  Considering kbd 3 as a solution to console-setup 12
  Holding Back console-setup rather than change kbd
Investigating python-zope.interface
Package python-zope.interface has broken dep on python-zopeinterface
  Considering python-zopeinterface 0 as a solution to python-zope.interface 9
  Added python-zopeinterface to the remove list
  Fixing python-zope.interface via remove of python-zopeinterface
Investigating libxml-libxml-perl
Package libxml-libxml-perl has broken dep on libxml-libxml-common-perl
  Considering libxml-libxml-common-perl -1 as a solution to libxml-libxml-perl 9
  Added libxml-libxml-common-perl to the remove list
  Fixing libxml-libxml-perl via remove of libxml-libxml-common-perl
Investigating plymouth
Package plymouth has broken dep on usplash
  Considering usplash 1 as a solution to plymouth 9
  Added usplash to the remove list
  Considering usplash 1 as a solution to plymouth 9
  Fixing plymouth via remove of usplash
Investigating libnautilus-extension1
Package libnautilus-extension1 has broken dep on gnome-mount
  Considering gnome-mount 1 as a solution to libnautilus-extension1 8
  Added gnome-mount to the remove list
  Fixing libnautilus-extension1 via remove of gnome-mount
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
Investigating libmetacity-private0
Package libmetacity-private0 has broken dep on libmetacity0
  Considering libmetacity0 -1 as a solution to libmetacity-private0 7
  Added libmetacity0 to the remove list
  Fixing libmetacity-private0 via remove of libmetacity0
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on kbd
  Considering kbd 3 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change kbd
Investigating libmp3lame0
Package libmp3lame0 has broken dep on liblame0
  Considering liblame0 1 as a solution to libmp3lame0 4
  Added liblame0 to the remove list
  Fixing libmp3lame0 via remove of liblame0
Investigating libcrack2
Package libcrack2 has broken dep on cracklib2
  Considering cracklib2 4 as a solution to libcrack2 4
  Holding Back libcrack2 rather than change cracklib2
Investigating nautilus
Package nautilus has broken dep on gnome-volume-manager
  Considering gnome-volume-manager -1 as a solution to nautilus 3
  Added gnome-volume-manager to the remove list
  Fixing nautilus via remove of gnome-volume-manager
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken dep on libchromexvmc1
  Considering libchromexvmc1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmc1 to the remove list
Package xserver-xorg-video-openchrome has broken dep on libchromexvmcpro1
  Considering libchromexvmcpro1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmcpro1 to the remove list
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmc1
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmcpro1
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 60 as a solution to upstart-logd 2
  Removing upstart-logd rather than change upstart
Investigating libdb4.8-dev
Package libdb4.8-dev has broken dep on libdb4.6-dev
  Considering libdb4.6-dev -1 as a solution to libdb4.8-dev 2
  Added libdb4.6-dev to the remove list
  Considering libdb4.6-dev -1 as a solution to libdb4.8-dev 2
  Fixing libdb4.8-dev via remove of libdb4.6-dev
Investigating libsox1a
Package libsox1a has broken dep on libsox0
  Considering libsox0 -1 as a solution to libsox1a 2
  Added libsox0 to the remove list
  Fixing libsox1a via remove of libsox0
Investigating libgdl-1-0
Package libgdl-1-0 has broken dep on libgdl-1-common
  Considering libgdl-1-common 5 as a solution to libgdl-1-0 2
  Removing libgdl-1-0 rather than change libgdl-1-common
Investigating libgdl-gnome-1-0
Package libgdl-gnome-1-0 has broken dep on libgdl-1-0
  Considering libgdl-1-0 2 as a solution to libgdl-gnome-1-0 1
  Removing libgdl-gnome-1-0 rather than change libgdl-1-0
Investigating libgnomekbd2
Package libgnomekbd2 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 4 as a solution to libgnomekbd2 1
  Removing libgnomekbd2 rather than change libgnomekbd-common
Investigating guidance-backends
Package guidance-backends has broken dep on python
  Considering python 940 as a solution to guidance-backends 1
  Removing guidance-backends rather than change python
Investigating libuniconf4.6
Package libuniconf4.6 has broken dep on libuniconf4.4
  Considering libuniconf4.4 -1 as a solution to libuniconf4.6 0
  Added libuniconf4.4 to the remove list
  Fixing libuniconf4.6 via remove of libuniconf4.4
Investigating human-theme
Package human-theme has broken dep on gtk2-engines-ubuntulooks
  Considering gtk2-engines-ubuntulooks -1 as a solution to human-theme 0
  Added gtk2-engines-ubuntulooks to the remove list
  Fixing human-theme via remove of gtk2-engines-ubuntulooks
Investigating usplash-theme-ubuntu
Package usplash-theme-ubuntu has broken dep on usplash
  Considering usplash 1 as a solution to usplash-theme-ubuntu 0
  Removing usplash-theme-ubuntu rather than change usplash
Investigating vnc4server
Package vnc4server has broken dep on vnc4-common
  Considering vnc4-common -1 as a solution to vnc4server 0
  Added vnc4-common to the remove list
  Fixing vnc4server via remove of vnc4-common
Investigating rubygems1.8
Package rubygems1.8 has broken dep on libgems-ruby1.8
  Considering libgems-ruby1.8 -1 as a solution to rubygems1.8 0
  Added libgems-ruby1.8 to the remove list
  Fixing rubygems1.8 via remove of libgems-ruby1.8
Investigating libgnomekbdui2
Package libgnomekbdui2 has broken dep on libgnomekbd2
  Considering libgnomekbd2 1 as a solution to libgnomekbdui2 -1
  Removing libgnomekbdui2 rather than change libgnomekbd2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5396 as a solution to libperl5.8 -1
  Removing libperl5.8 rather than change perl-base
Investigating libkipi7
Package libkipi7 has broken dep on libkipi0
  Considering libkipi0 -1 as a solution to libkipi7 -1
  Holding Back libkipi7 rather than change libkipi0
Investigating python-gnome2-extras
Package python-gnome2-extras has broken dep on libgdl-1-0
  Considering libgdl-1-0 2 as a solution to python-gnome2-extras -1
  Removing python-gnome2-extras rather than change libgdl-1-0
Investigating libcupsys2-dev
Package libcupsys2-dev has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to libcupsys2-dev -1
  Removing libcupsys2-dev rather than change libcupsys2
Investigating libxcb-xlib0-dev
Package libxcb-xlib0-dev has broken dep on libxcb-xlib0
  Considering libxcb-xlib0 1 as a solution to libxcb-xlib0-dev -1
  Removing libxcb-xlib0-dev rather than change libxcb-xlib0
Investigating liblame-dev
Package liblame-dev has broken dep on liblame0
  Considering liblame0 1 as a solution to liblame-dev -1
  Removing liblame-dev rather than change liblame0
Investigating python-gtkhtml2
Package python-gtkhtml2 has broken dep on python
  Considering python 940 as a solution to python-gtkhtml2 -1
  Removing python-gtkhtml2 rather than change python
Investigating libxvidcore4-dev
Package libxvidcore4-dev has broken dep on libxvidcore4
  Considering libxvidcore4 3 as a solution to libxvidcore4-dev -1
  Removing libxvidcore4-dev rather than change libxvidcore4
Investigating displayconfig-gtk
Package displayconfig-gtk has broken dep on guidance-backends
  Considering guidance-backends 1 as a solution to displayconfig-gtk -1
  Removing displayconfig-gtk rather than change guidance-backends
Investigating cracklib-runtime
Package cracklib-runtime has broken dep on libcrack2
  Considering libcrack2 4 as a solution to cracklib-runtime -1
  Holding Back cracklib-runtime rather than change libcrack2
Investigating libltdl-dev
Package libltdl-dev has broken dep on libltdl3-dev
  Considering libltdl3-dev -1 as a solution to libltdl-dev -1
  Holding Back libltdl-dev rather than change libltdl3-dev
Investigating netatalk
Package netatalk has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to netatalk 9999
  Added libcupsys2 to the remove list
  Fixing netatalk via keep of libcupsys2
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to libcups2 261
  Added libcupsys2 to the remove list
  Fixing libcups2 via remove of libcupsys2
 Try to Re-Instate console-setup
Investigating kipi-plugins
Package kipi-plugins has broken dep on libkipi7
  Considering libkipi7 -1 as a solution to kipi-plugins 0
  Holding Back kipi-plugins rather than change libkipi7
Investigating netatalk
Package netatalk has broken dep on libcupsys2
  Considering libcupsys2 3 as a solution to netatalk 9999
  Added libcupsys2 to the remove list
  Fixing netatalk via keep of libcupsys2
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 9999 as a solution to libcups2 261
  Holding Back libcups2 rather than change libcupsys2
Investigating libcupsimage2
Package libcupsimage2 has broken dep on libcups2
  Considering libcups2 261 as a solution to libcupsimage2 26
  Holding Back libcupsimage2 rather than change libcups2
Investigating cups-client
Package cups-client has broken dep on libcups2
  Considering libcups2 261 as a solution to cups-client 20
  Holding Back cups-client rather than change libcups2
Investigating cups
Package cups has broken dep on libcups2
  Considering libcups2 261 as a solution to cups 13
  Holding Back cups rather than change libcups2
Investigating kdelibs4c2a
Package kdelibs4c2a has broken dep on libcups2
  Considering libcups2 261 as a solution to kdelibs4c2a 12
  Holding Back kdelibs4c2a rather than change libcups2
Investigating libcupsppdc1
Package libcupsppdc1 has broken dep on libcups2
  Considering libcups2 261 as a solution to libcupsppdc1 8
  Holding Back libcupsppdc1 rather than change libcups2
Investigating libcupscgi1
Package libcupscgi1 has broken dep on libcups2
  Considering libcups2 261 as a solution to libcupscgi1 8
  Holding Back libcupscgi1 rather than change libcups2
Investigating libcupsdriver1
Package libcupsdriver1 has broken dep on libcups2
  Considering libcups2 261 as a solution to libcupsdriver1 8
  Holding Back libcupsdriver1 rather than change libcups2
Investigating libcupsmime1
Package libcupsmime1 has broken dep on libcups2
  Considering libcups2 261 as a solution to libcupsmime1 8
  Holding Back libcupsmime1 rather than change libcups2
Investigating libgnomeprint2.2-0
Package libgnomeprint2.2-0 has broken dep on libcups2
  Considering libcups2 261 as a solution to libgnomeprint2.2-0 7
  Removing libgnomeprint2.2-0 rather than change libcups2
Investigating libgs8
Package libgs8 has broken dep on libcups2
  Considering libcups2 261 as a solution to libgs8 7
  Holding Back libgs8 rather than change libcups2
Investigating libgnomecups1.0-1
Package libgnomecups1.0-1 has broken dep on libcups2
  Considering libcups2 261 as a solution to libgnomecups1.0-1 5
  Holding Back libgnomecups1.0-1 rather than change libcups2
Investigating python-cups
Package python-cups has broken dep on libcups2
  Considering libcups2 261 as a solution to python-cups 4
  Removing python-cups rather than change libcups2
Investigating libgnomeprintui2.2-0
Package libgnomeprintui2.2-0 has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 261 as a solution to libgnomeprintui2.2-0 3
  Removing libgnomeprintui2.2-0 rather than change libgnomeprint2.2-0
Investigating python-gnomeprint
Package python-gnomeprint has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 261 as a solution to python-gnomeprint 3
  Holding Back python-gnomeprint rather than change libgnomeprint2.2-0
Investigating foomatic-db-engine
Package foomatic-db-engine has broken dep on cups
  Considering cups 13 as a solution to foomatic-db-engine 2
  Holding Back foomatic-db-engine rather than change cups
Investigating ghostscript-cups
Package ghostscript-cups has broken dep on libcups2
  Considering libcups2 261 as a solution to ghostscript-cups 2
  Holding Back ghostscript-cups rather than change libcups2
Investigating foomatic-db
Package foomatic-db has broken dep on cups
  Considering cups 13 as a solution to foomatic-db 2
  Holding Back foomatic-db rather than change cups
Investigating system-config-printer-common
Package system-config-printer-common has broken dep on python-cups
  Considering python-cups 261 as a solution to system-config-printer-common 1
  Removing system-config-printer-common rather than change python-cups
 Try to Re-Instate kipi-plugins
Investigating openprinting-ppds
Package openprinting-ppds has broken dep on cups
  Considering cups 13 as a solution to openprinting-ppds 0
  Holding Back openprinting-ppds rather than change cups
Investigating system-config-printer-gnome
Package system-config-printer-gnome has broken dep on system-config-printer-common
  Considering system-config-printer-common 261 as a solution to system-config-printer-gnome 0
  Removing system-config-printer-gnome rather than change system-config-printer-common
Investigating pxljr
Package pxljr has broken dep on cups
  Considering cups 13 as a solution to pxljr 0
  Holding Back pxljr rather than change cups
Investigating libgtksourceview1.0-0
Package libgtksourceview1.0-0 has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 261 as a solution to libgtksourceview1.0-0 0
  Removing libgtksourceview1.0-0 rather than change libgnomeprint2.2-0
Investigating splix
Package splix has broken dep on libcups2
  Considering libcups2 261 as a solution to splix 0
  Holding Back splix rather than change libcups2
Investigating samba
Package samba has broken dep on libcups2
  Considering libcups2 261 as a solution to samba 0
  Removing samba rather than change libcups2
Investigating foo2zjs
Package foo2zjs has broken dep on cups
  Considering cups 13 as a solution to foo2zjs 0
  Holding Back foo2zjs rather than change cups
Investigating bluez-cups
Package bluez-cups has broken dep on cups
  Considering cups 13 as a solution to bluez-cups -1
  Holding Back bluez-cups rather than change cups
Investigating cups-driver-gutenprint
Package cups-driver-gutenprint has broken dep on libcups2
  Considering libcups2 261 as a solution to cups-driver-gutenprint -1
  Holding Back cups-driver-gutenprint rather than change libcups2
Investigating system-config-printer-udev
Package system-config-printer-udev has broken dep on libcups2
  Considering libcups2 261 as a solution to system-config-printer-udev -1
  Holding Back system-config-printer-udev rather than change libcups2
Investigating libgnome2.0-cil
Package libgnome2.0-cil has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 261 as a solution to libgnome2.0-cil -1
  Removing libgnome2.0-cil rather than change libgnomeprint2.2-0
Investigating libgtk2.0-0
Package libgtk2.0-0 has broken dep on libcups2
  Considering libcups2 261 as a solution to libgtk2.0-0 708
  Holding Back libgtk2.0-0 rather than change libcups2
Investigating libbonoboui2-0
Package libbonoboui2-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libbonoboui2-0 89
  Removing libbonoboui2-0 rather than change libgtk2.0-0
Investigating python-gtk2
Package python-gtk2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to python-gtk2 87
  Removing python-gtk2 rather than change libgtk2.0-0
Investigating libgail18
Package libgail18 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgail18 51
  Holding Back libgail18 rather than change libgtk2.0-0
Investigating libgnomeui-0
Package libgnomeui-0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to libgnomeui-0 49
  Removing libgnomeui-0 rather than change libbonoboui2-0
Investigating libgnome-desktop-2-17
Package libgnome-desktop-2-17 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgnome-desktop-2-17 29
  Holding Back libgnome-desktop-2-17 rather than change libgtk2.0-0
 Try to Re-Instate libcupsimage2
Investigating libpanel-applet2-0
Package libpanel-applet2-0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to libpanel-applet2-0 26
  Removing libpanel-applet2-0 rather than change libbonoboui2-0
Investigating librsvg2-2
Package librsvg2-2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to librsvg2-2 24
  Holding Back librsvg2-2 rather than change libgtk2.0-0
Investigating librsvg2-common
Package librsvg2-common has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to librsvg2-common 20
  Holding Back librsvg2-common rather than change libgtk2.0-0
Investigating libcanberra-gtk0
Package libcanberra-gtk0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libcanberra-gtk0 20
  Holding Back libcanberra-gtk0 rather than change libgtk2.0-0
Investigating libappindicator0
Package libappindicator0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libappindicator0 17
  Holding Back libappindicator0 rather than change libgtk2.0-0
Investigating libgtk2.0-bin
Package libgtk2.0-bin has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtk2.0-bin 17
  Holding Back libgtk2.0-bin rather than change libgtk2.0-0
Investigating python-gnome2
Package python-gnome2 has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-gnome2 16
  Removing python-gnome2 rather than change python-gtk2
Investigating libindicator0
Package libindicator0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libindicator0 16
  Holding Back libindicator0 rather than change libgtk2.0-0
Investigating libwnck22
Package libwnck22 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libwnck22 15
  Holding Back libwnck22 rather than change libgtk2.0-0
Investigating ghostscript
Package ghostscript has broken dep on libgs8
  Considering libgs8 7 as a solution to ghostscript 15
  Holding Back ghostscript rather than change libgs8
Investigating libdbusmenu-gtk1
Package libdbusmenu-gtk1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libdbusmenu-gtk1 14
  Holding Back libdbusmenu-gtk1 rather than change libgtk2.0-0
 Try to Re-Instate kdelibs4c2a
Investigating python-glade2
Package python-glade2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to python-glade2 12
  Removing python-glade2 rather than change libgtk2.0-0
Investigating libgtk2.0-cil
Package libgtk2.0-cil has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtk2.0-cil 12
  Holding Back libgtk2.0-cil rather than change libgtk2.0-0
Investigating libvte9
Package libvte9 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libvte9 11
  Holding Back libvte9 rather than change libgtk2.0-0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gnome-keyring 9
  Holding Back gnome-keyring rather than change libgtk2.0-0
Investigating libedataserverui1.2-8
Package libedataserverui1.2-8 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libedataserverui1.2-8 9
  Holding Back libedataserverui1.2-8 rather than change libgtk2.0-0
Investigating policykit-1-gnome
Package policykit-1-gnome has broken dep on libappindicator0
  Considering libappindicator0 17 as a solution to policykit-1-gnome 9
  Holding Back policykit-1-gnome rather than change libappindicator0
Investigating libwebkit-1.0-2
Package libwebkit-1.0-2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libwebkit-1.0-2 8
  Holding Back libwebkit-1.0-2 rather than change libgtk2.0-0
Investigating libnautilus-extension1
Package libnautilus-extension1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libnautilus-extension1 8
  Holding Back libnautilus-extension1 rather than change libgtk2.0-0
Investigating libgtkhtml3.14-19
Package libgtkhtml3.14-19 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtkhtml3.14-19 7
  Holding Back libgtkhtml3.14-19 rather than change libgtk2.0-0
Investigating libgail-common
Package libgail-common has broken dep on libgail18
  Considering libgail18 51 as a solution to libgail-common 7
  Holding Back libgail-common rather than change libgail18
Investigating libgnome-media0
Package libgnome-media0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgnome-media0 7
  Removing libgnome-media0 rather than change libgtk2.0-0
 Try to Re-Instate libgs8
Investigating libmetacity-private0
Package libmetacity-private0 has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 20 as a solution to libmetacity-private0 7
  Holding Back libmetacity-private0 rather than change libcanberra-gtk0
Investigating libgnome-pilot2
Package libgnome-pilot2 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to libgnome-pilot2 7
  Holding Back libgnome-pilot2 rather than change libbonoboui2-0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtk2-perl 6
  Removing libgtk2-perl rather than change libgtk2.0-0
Investigating rhythmbox
Package rhythmbox has broken dep on libgnome-media0
  Considering libgnome-media0 708 as a solution to rhythmbox 6
  Holding Back rhythmbox rather than change libgnome-media0
Investigating gnome-panel
Package gnome-panel has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to gnome-panel 6
  Removing gnome-panel rather than change libbonoboui2-0
Investigating libgnome-window-settings1
Package libgnome-window-settings1 has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 29 as a solution to libgnome-window-settings1 5
  Removing libgnome-window-settings1 rather than change libgnome-desktop-2-17
Investigating libgtkmm-2.4-1c2a
Package libgtkmm-2.4-1c2a has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtkmm-2.4-1c2a 5
  Holding Back libgtkmm-2.4-1c2a rather than change libgtk2.0-0
Investigating gnome-about
Package gnome-about has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to gnome-about 5
  Removing gnome-about rather than change python-gtk2
Investigating python-vte
Package python-vte has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to python-vte 5
  Removing python-vte rather than change libgtk2.0-0
 Try to Re-Instate libgnomecups1.0-1
Investigating synaptic
Package synaptic has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to synaptic 5
  Removing synaptic rather than change libgtk2.0-0
Investigating python-gnomeapplet
Package python-gnomeapplet has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to python-gnomeapplet 5
  Holding Back python-gnomeapplet rather than change libbonoboui2-0
Investigating gnome-control-center
Package gnome-control-center has broken dep on libappindicator0
  Considering libappindicator0 17 as a solution to gnome-control-center 5
  Removing gnome-control-center rather than change libappindicator0
Investigating python-gnome2-desktop
Package python-gnome2-desktop has broken dep on python-gnomeapplet
  Considering python-gnomeapplet 5 as a solution to python-gnome2-desktop 5
  Removing python-gnome2-desktop rather than change python-gnomeapplet
Investigating python-notify
Package python-notify has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-notify 4
  Removing python-notify rather than change python-gtk2
Investigating libevdocument2
Package libevdocument2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libevdocument2 4
  Holding Back libevdocument2 rather than change libgtk2.0-0
Investigating zenity
Package zenity has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to zenity 4
  Holding Back zenity rather than change libgtk2.0-0
Investigating python-gmenu
Package python-gmenu has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-gmenu 4
  Removing python-gmenu rather than change python-gtk2
Investigating firefox
Package firefox has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to firefox 4
  Holding Back firefox rather than change libgtk2.0-0
Investigating libglade2.0-cil
Package libglade2.0-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 12 as a solution to libglade2.0-cil 4
  Holding Back libglade2.0-cil rather than change libgtk2.0-cil
Investigating libgnomekbd4
Package libgnomekbd4 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgnomekbd4 4
  Holding Back libgnomekbd4 rather than change libgtk2.0-0
Investigating compiz-plugins
Package compiz-plugins has broken dep on librsvg2-2
  Considering librsvg2-2 24 as a solution to compiz-plugins 4
  Removing compiz-plugins rather than change librsvg2-2
Investigating libgtksourceview2.0-0
Package libgtksourceview2.0-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtksourceview2.0-0 4
  Removing libgtksourceview2.0-0 rather than change libgtk2.0-0
Investigating totem
Package totem has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to totem 4
  Holding Back totem rather than change libgtk2.0-0
Investigating python-bugbuddy
Package python-bugbuddy has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-bugbuddy 3
  Holding Back python-bugbuddy rather than change python-gtk2
Investigating python-evolution
Package python-evolution has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-evolution 3
  Holding Back python-evolution rather than change python-gtk2
Investigating python-gnomedesktop
Package python-gnomedesktop has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 29 as a solution to python-gnomedesktop 3
  Holding Back python-gnomedesktop rather than change libgnome-desktop-2-17
Investigating nautilus
Package nautilus has broken dep on libappindicator0
  Considering libappindicator0 17 as a solution to nautilus 3
  Removing nautilus rather than change libappindicator0
Investigating python-evince
Package python-evince has broken dep on libevdocument2
  Considering libevdocument2 4 as a solution to python-evince 3
  Holding Back python-evince rather than change libevdocument2
Investigating libgtkhtml-editor0
Package libgtkhtml-editor0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtkhtml-editor0 3
  Holding Back libgtkhtml-editor0 rather than change libgtk2.0-0
Investigating evolution
Package evolution has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to evolution 3
  Holding Back evolution rather than change libbonoboui2-0
Investigating libpolkit-gnome0
Package libpolkit-gnome0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libpolkit-gnome0 3
  Holding Back libpolkit-gnome0 rather than change libgtk2.0-0
Investigating policykit-gnome
Package policykit-gnome has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to policykit-gnome 3
  Holding Back policykit-gnome rather than change libgtk2.0-0
Investigating python-totem-plparser
Package python-totem-plparser has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-totem-plparser 3
  Holding Back python-totem-plparser rather than change python-gtk2
Investigating python-gnomekeyring
Package python-gnomekeyring has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-gnomekeyring 3
  Holding Back python-gnomekeyring rather than change python-gtk2
Investigating liblpint-bonobo0
Package liblpint-bonobo0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to liblpint-bonobo0 3
  Holding Back liblpint-bonobo0 rather than change libbonoboui2-0
Investigating libgail-gnome-module
Package libgail-gnome-module has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to libgail-gnome-module 3
  Removing libgail-gnome-module rather than change libbonoboui2-0
Investigating python-rsvg
Package python-rsvg has broken dep on librsvg2-2
  Considering librsvg2-2 24 as a solution to python-rsvg 3
  Holding Back python-rsvg rather than change librsvg2-2
Investigating yelp
Package yelp has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to yelp 3
  Removing yelp rather than change libgtk2.0-0
Investigating python-mediaprofiles
Package python-mediaprofiles has broken dep on libgnome-media0
  Considering libgnome-media0 708 as a solution to python-mediaprofiles 3
  Holding Back python-mediaprofiles rather than change libgnome-media0
Investigating python-wnck
Package python-wnck has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-wnck 3
  Holding Back python-wnck rather than change python-gtk2
Investigating python-metacity
Package python-metacity has broken dep on libmetacity-private0
  Considering libmetacity-private0 7 as a solution to python-metacity 3
  Holding Back python-metacity rather than change libmetacity-private0
Investigating python-gtop
Package python-gtop has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-gtop 3
  Holding Back python-gtop rather than change python-gtk2
Investigating libido-0.1-0
Package libido-0.1-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libido-0.1-0 2
  Holding Back libido-0.1-0 rather than change libgtk2.0-0
 Try to Re-Instate foomatic-db-engine
Investigating gnome-settings-daemon
Package gnome-settings-daemon has broken dep on libappindicator0
  Considering libappindicator0 17 as a solution to gnome-settings-daemon 2
  Removing gnome-settings-daemon rather than change libappindicator0
Investigating libevview2
Package libevview2 has broken dep on libevdocument2
  Considering libevdocument2 4 as a solution to libevview2 2
  Holding Back libevview2 rather than change libevdocument2
Investigating gtk2-engines-murrine
Package gtk2-engines-murrine has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gtk2-engines-murrine 2
  Holding Back gtk2-engines-murrine rather than change libgtk2.0-0
Investigating libgoffice-0.8-8
Package libgoffice-0.8-8 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgoffice-0.8-8 2
  Holding Back libgoffice-0.8-8 rather than change libgtk2.0-0
Investigating eog
Package eog has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 29 as a solution to eog 2
  Removing eog rather than change libgnome-desktop-2-17
Investigating xulrunner-1.9.2
Package xulrunner-1.9.2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to xulrunner-1.9.2 2
  Holding Back xulrunner-1.9.2 rather than change libgtk2.0-0
Investigating compiz-gnome
Package compiz-gnome has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 29 as a solution to compiz-gnome 2
  Removing compiz-gnome rather than change libgnome-desktop-2-17
Investigating evince
Package evince has broken dep on libevdocument2
  Considering libevdocument2 4 as a solution to evince 2
  Removing evince rather than change libevdocument2
Investigating gimp
Package gimp has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to gimp 2
  Holding Back gimp rather than change python-gtk2
Investigating gtk2-engines-pixbuf
Package gtk2-engines-pixbuf has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gtk2-engines-pixbuf 2
  Holding Back gtk2-engines-pixbuf rather than change libgtk2.0-0
 Try to Re-Instate foomatic-db
Investigating libgtkhtml2-0
Package libgtkhtml2-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtkhtml2-0 2
  Holding Back libgtkhtml2-0 rather than change libgtk2.0-0
Investigating gnome-panel-dbg
Package gnome-panel-dbg has broken dep on gnome-panel
  Considering gnome-panel 708 as a solution to gnome-panel-dbg 1
  Holding Back gnome-panel-dbg rather than change gnome-panel
Investigating libmono-addins-gui0.2-cil
Package libmono-addins-gui0.2-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 12 as a solution to libmono-addins-gui0.2-cil 1
  Holding Back libmono-addins-gui0.2-cil rather than change libgtk2.0-cil
Investigating metacity
Package metacity has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 20 as a solution to metacity 1
  Removing metacity rather than change libcanberra-gtk0
Investigating gnome-session-bin
Package gnome-session-bin has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gnome-session-bin 1
  Holding Back gnome-session-bin rather than change libgtk2.0-0
Investigating libbrasero-media0
Package libbrasero-media0 has broken dep on libappindicator0
  Considering libappindicator0 17 as a solution to libbrasero-media0 1
  Holding Back libbrasero-media0 rather than change libappindicator0
Investigating libgucharmap7
Package libgucharmap7 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgucharmap7 1
  Holding Back libgucharmap7 rather than change libgtk2.0-0
Investigating gnome-applets
Package gnome-applets has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to gnome-applets 1
  Holding Back gnome-applets rather than change libbonoboui2-0
Investigating evince-dbg
Package evince-dbg has broken dep on evince
  Considering evince 4 as a solution to evince-dbg 1
  Holding Back evince-dbg rather than change evince
Investigating python-pyatspi
Package python-pyatspi has broken dep on python-gnome2
  Considering python-gnome2 708 as a solution to python-pyatspi 1
  Removing python-pyatspi rather than change python-gnome2
Investigating epiphany-browser
Package epiphany-browser has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to epiphany-browser 1
  Holding Back epiphany-browser rather than change libgtk2.0-0
Investigating python-gtk2-dbg
Package python-gtk2-dbg has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-gtk2-dbg 1
  Holding Back python-gtk2-dbg rather than change python-gtk2
Investigating eog-dbg
Package eog-dbg has broken dep on eog
  Considering eog 29 as a solution to eog-dbg 1
  Holding Back eog-dbg rather than change eog
Investigating gnome-applets-dbg
Package gnome-applets-dbg has broken dep on gnome-applets
  Considering gnome-applets 1 as a solution to gnome-applets-dbg 1
  Holding Back gnome-applets-dbg rather than change gnome-applets
Investigating python-gtksourceview2
Package python-gtksourceview2 has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-gtksourceview2 1
  Removing python-gtksourceview2 rather than change python-gtk2
Investigating nautilus-dbg
Package nautilus-dbg has broken dep on nautilus
  Considering nautilus 17 as a solution to nautilus-dbg 1
  Holding Back nautilus-dbg rather than change nautilus
Investigating gnome-pilot
Package gnome-pilot has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to gnome-pilot 1
  Removing gnome-pilot rather than change libbonoboui2-0
Investigating libgnome2.24-cil
Package libgnome2.24-cil has broken dep on libglade2.0-cil
  Considering libglade2.0-cil 4 as a solution to libgnome2.24-cil 1
  Holding Back libgnome2.24-cil rather than change libglade2.0-cil
Investigating librsvg2-dbg
Package librsvg2-dbg has broken dep on librsvg2-2
  Considering librsvg2-2 24 as a solution to librsvg2-dbg 1
  Holding Back librsvg2-dbg rather than change librsvg2-2
Investigating update-manager
Package update-manager has broken dep on synaptic
  Considering synaptic 708 as a solution to update-manager 1
  Removing update-manager rather than change synaptic
Investigating libgnome-desktop-2
Package libgnome-desktop-2 has broken dep on libgnomeui-0
  Considering libgnomeui-0 708 as a solution to libgnome-desktop-2 1
  Removing libgnome-desktop-2 rather than change libgnomeui-0
Investigating libgcr0
Package libgcr0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgcr0 1
  Holding Back libgcr0 rather than change libgtk2.0-0
Investigating libgtk2.0-0-dbg
Package libgtk2.0-0-dbg has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtk2.0-0-dbg 1
  Holding Back libgtk2.0-0-dbg rather than change libgtk2.0-0
Investigating libgtkhtml3.14-dbg
Package libgtkhtml3.14-dbg has broken dep on libgtkhtml3.14-19
  Considering libgtkhtml3.14-19 7 as a solution to libgtkhtml3.14-dbg 1
  Holding Back libgtkhtml3.14-dbg rather than change libgtkhtml3.14-19
Investigating deskbar-applet
Package deskbar-applet has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 29 as a solution to deskbar-applet 1
  Removing deskbar-applet rather than change libgnome-desktop-2-17
Investigating evolution-dbg
Package evolution-dbg has broken dep on evolution
  Considering evolution 3 as a solution to evolution-dbg 1
  Holding Back evolution-dbg rather than change evolution
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on libgtk2-perl
  Considering libgtk2-perl 708 as a solution to libgnome2-canvas-perl 1
  Removing libgnome2-canvas-perl rather than change libgtk2-perl
Investigating libgtk2-gladexml-perl
Package libgtk2-gladexml-perl has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtk2-gladexml-perl 1
  Removing libgtk2-gladexml-perl rather than change libgtk2.0-0
Investigating gnome-user-guide
Package gnome-user-guide has broken dep on yelp
  Considering yelp 708 as a solution to gnome-user-guide 1
  Removing gnome-user-guide rather than change yelp
Investigating libgnomeui-0-dbg
Package libgnomeui-0-dbg has broken dep on libgnomeui-0
  Considering libgnomeui-0 708 as a solution to libgnomeui-0-dbg 1
  Holding Back libgnomeui-0-dbg rather than change libgnomeui-0
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgtk2.0-dev 1
  Holding Back libgtk2.0-dev rather than change libgtk2.0-0
Investigating totem-dbg
Package totem-dbg has broken dep on totem
  Considering totem 4 as a solution to totem-dbg 1
  Holding Back totem-dbg rather than change totem
Investigating gnome-power-manager
Package gnome-power-manager has broken dep on libappindicator0
  Considering libappindicator0 17 as a solution to gnome-power-manager 0
  Removing gnome-power-manager rather than change libappindicator0
Investigating tomboy
Package tomboy has broken dep on libgnome2.24-cil
  Considering libgnome2.24-cil 1 as a solution to tomboy 0
  Removing tomboy rather than change libgnome2.24-cil
Investigating libgnome-bluetooth7
Package libgnome-bluetooth7 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgnome-bluetooth7 0
  Holding Back libgnome-bluetooth7 rather than change libgtk2.0-0
Investigating gcalctool
Package gcalctool has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gcalctool 0
  Holding Back gcalctool rather than change libgtk2.0-0
 Try to Re-Instate openprinting-ppds
Investigating gnome-media
Package gnome-media has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 20 as a solution to gnome-media 0
  Removing gnome-media rather than change libcanberra-gtk0
Investigating smart-notifier
Package smart-notifier has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to smart-notifier 0
  Removing smart-notifier rather than change python-gtk2
Investigating checkbox-gtk
Package checkbox-gtk has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to checkbox-gtk 0
  Holding Back checkbox-gtk rather than change python-gtk2
Investigating update-notifier
Package update-notifier has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to update-notifier 0
  Removing update-notifier rather than change libgtk2.0-0
Investigating ubuntu-docs
Package ubuntu-docs has broken dep on gnome-user-guide
  Considering gnome-user-guide 708 as a solution to ubuntu-docs 0
  Removing ubuntu-docs rather than change gnome-user-guide
Investigating nspluginwrapper
Package nspluginwrapper has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to nspluginwrapper 0
  Holding Back nspluginwrapper rather than change libgtk2.0-0
Investigating network-manager-gnome
Package network-manager-gnome has broken dep on libgnome-bluetooth7
  Considering libgnome-bluetooth7 0 as a solution to network-manager-gnome 0
  Removing network-manager-gnome rather than change libgnome-bluetooth7
 Try to Re-Instate pxljr
Investigating gucharmap
Package gucharmap has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gucharmap 0
  Holding Back gucharmap rather than change libgtk2.0-0
Investigating libseed0
Package libseed0 has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 8 as a solution to libseed0 0
  Holding Back libseed0 rather than change libwebkit-1.0-2
Investigating totem-plugins
Package totem-plugins has broken dep on totem
  Considering totem 4 as a solution to totem-plugins 0
  Removing totem-plugins rather than change totem
Investigating computertemp
Package computertemp has broken dep on python-gnome2
  Considering python-gnome2 708 as a solution to computertemp 0
  Removing computertemp rather than change python-gnome2
Investigating gdebi
Package gdebi has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to gdebi 0
  Removing gdebi rather than change python-gtk2
Investigating scim-bridge-client-gtk
Package scim-bridge-client-gtk has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to scim-bridge-client-gtk 0
  Holding Back scim-bridge-client-gtk rather than change libgtk2.0-0
Investigating libgnomepanel2.24-cil
Package libgnomepanel2.24-cil has broken dep on libpanel-applet2-0
  Considering libpanel-applet2-0 708 as a solution to libgnomepanel2.24-cil 0
  Holding Back libgnomepanel2.24-cil rather than change libpanel-applet2-0
Investigating gparted
Package gparted has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gparted 0
  Holding Back gparted rather than change libgtk2.0-0
Investigating gnome-mag
Package gnome-mag has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gnome-mag 0
  Holding Back gnome-mag rather than change libgtk2.0-0
Investigating liblaunchpad-integration1.0-cil
Package liblaunchpad-integration1.0-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 12 as a solution to liblaunchpad-integration1.0-cil 0
  Holding Back liblaunchpad-integration1.0-cil rather than change libgtk2.0-cil
Investigating gedit
Package gedit has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gedit 0
  Removing gedit rather than change libgtk2.0-0
Investigating gnome-system-monitor
Package gnome-system-monitor has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gnome-system-monitor 0
  Holding Back gnome-system-monitor rather than change libgtk2.0-0
Investigating gnome-terminal
Package gnome-terminal has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gnome-terminal 0
  Removing gnome-terminal rather than change libgtk2.0-0
Investigating gnome-session
Package gnome-session has broken dep on gnome-settings-daemon
  Considering gnome-settings-daemon 17 as a solution to gnome-session 0
  Removing gnome-session rather than change gnome-settings-daemon
Investigating seahorse
Package seahorse has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to seahorse 0
  Removing seahorse rather than change libgtk2.0-0
Investigating libgdict-1.0-6
Package libgdict-1.0-6 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgdict-1.0-6 0
  Holding Back libgdict-1.0-6 rather than change libgtk2.0-0
Investigating software-center
Package software-center has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to software-center 0
  Holding Back software-center rather than change python-gtk2
Investigating hwtest-gtk
Package hwtest-gtk has broken dep on checkbox-gtk
  Considering checkbox-gtk 0 as a solution to hwtest-gtk 0
  Removing hwtest-gtk rather than change checkbox-gtk
Investigating tracker-search-tool
Package tracker-search-tool has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 29 as a solution to tracker-search-tool 0
  Removing tracker-search-tool rather than change libgnome-desktop-2-17
Investigating fslint
Package fslint has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to fslint 0
  Removing fslint rather than change python-gtk2
Investigating gnome-nettool
Package gnome-nettool has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gnome-nettool 0
  Holding Back gnome-nettool rather than change libgtk2.0-0
Investigating language-selector
Package language-selector has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to language-selector 0
  Removing language-selector rather than change python-gtk2
Investigating python-webkit
Package python-webkit has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 8 as a solution to python-webkit 0
  Holding Back python-webkit rather than change libwebkit-1.0-2
Investigating gnome-utils
Package gnome-utils has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to gnome-utils 0
  Removing gnome-utils rather than change libbonoboui2-0
Investigating gconf-editor
Package gconf-editor has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gconf-editor 0
  Removing gconf-editor rather than change libgtk2.0-0
Investigating libgegl-0.0-0
Package libgegl-0.0-0 has broken dep on librsvg2-2
  Considering librsvg2-2 24 as a solution to libgegl-0.0-0 0
  Holding Back libgegl-0.0-0 rather than change librsvg2-2
Investigating anjuta
Package anjuta has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to anjuta 0
  Holding Back anjuta rather than change libgtk2.0-0
Investigating gnome-orca
Package gnome-orca has broken dep on python-pyatspi
  Considering python-pyatspi 708 as a solution to gnome-orca 0
Package gnome-orca has broken dep on python-pyatspi2
  Or group remove for gnome-orca
Package gnome-orca has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to gnome-orca 0
  Removing gnome-orca rather than change python-gtk2
Investigating libgladeui-1-9
Package libgladeui-1-9 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libgladeui-1-9 0
  Holding Back libgladeui-1-9 rather than change libgtk2.0-0
Investigating python-sexy
Package python-sexy has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-sexy 0
  Removing python-sexy rather than change python-gtk2
Investigating bug-buddy
Package bug-buddy has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to bug-buddy 0
  Removing bug-buddy rather than change libgtk2.0-0
 Try to Re-Instate splix
Investigating software-properties-gtk
Package software-properties-gtk has broken dep on synaptic
  Considering synaptic 708 as a solution to software-properties-gtk 0
  Removing software-properties-gtk rather than change synaptic
Investigating tsclient
Package tsclient has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to tsclient 0
  Removing tsclient rather than change libbonoboui2-0
Investigating scim-gtk2-immodule
Package scim-gtk2-immodule has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to scim-gtk2-immodule 0
  Removing scim-gtk2-immodule rather than change libgtk2.0-0
Investigating libdeskbar-tracker
Package libdeskbar-tracker has broken dep on python-gnome2
  Considering python-gnome2 708 as a solution to libdeskbar-tracker 0
  Removing libdeskbar-tracker rather than change python-gnome2
Investigating mousetweaks
Package mousetweaks has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to mousetweaks 0
  Removing mousetweaks rather than change libbonoboui2-0
Investigating libdevhelp-1-1
Package libdevhelp-1-1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to libdevhelp-1-1 0
  Holding Back libdevhelp-1-1 rather than change libgtk2.0-0
Investigating gir1.0-gtk-2.0
Package gir1.0-gtk-2.0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gir1.0-gtk-2.0 0
  Holding Back gir1.0-gtk-2.0 rather than change libgtk2.0-0
Investigating ghostscript-x
Package ghostscript-x has broken dep on ghostscript
  Considering ghostscript 15 as a solution to ghostscript-x 0
  Holding Back ghostscript-x rather than change ghostscript
 Try to Re-Instate foo2zjs
Investigating gnome-screensaver
Package gnome-screensaver has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 29 as a solution to gnome-screensaver 0
  Removing gnome-screensaver rather than change libgnome-desktop-2-17
Investigating onboard
Package onboard has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to onboard 0
  Removing onboard rather than change python-gtk2
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to libgnome2-perl 0
  Removing libgnome2-perl rather than change libbonoboui2-0
Investigating jockey-gtk
Package jockey-gtk has broken dep on python-notify
  Considering python-notify 708 as a solution to jockey-gtk 0
  Removing jockey-gtk rather than change python-notify
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem
  Considering totem 4 as a solution to totem-gstreamer 0
  Removing totem-gstreamer rather than change totem
Investigating gtkorphan
Package gtkorphan has broken dep on libgtk2-gladexml-perl
  Considering libgtk2-gladexml-perl 708 as a solution to gtkorphan 0
  Removing gtkorphan rather than change libgtk2-gladexml-perl
Investigating compiz
Package compiz has broken dep on compiz-plugins
  Considering compiz-plugins 24 as a solution to compiz 0
  Removing compiz rather than change compiz-plugins
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem
  Considering totem 4 as a solution to totem-mozilla 0
  Removing totem-mozilla rather than change totem
Investigating apport-gtk
Package apport-gtk has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to apport-gtk 0
  Removing apport-gtk rather than change python-gtk2
Investigating light-themes
Package light-themes has broken dep on gtk2-engines-murrine
  Considering gtk2-engines-murrine 2 as a solution to light-themes 0
  Holding Back light-themes rather than change gtk2-engines-murrine
Investigating firefox-gnome-support
Package firefox-gnome-support has broken dep on firefox
  Considering firefox 4 as a solution to firefox-gnome-support 0
  Holding Back firefox-gnome-support rather than change firefox
Investigating file-roller
Package file-roller has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to file-roller 0
  Removing file-roller rather than change libgtk2.0-0
Investigating gnome-netstatus-applet
Package gnome-netstatus-applet has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to gnome-netstatus-applet 0
  Removing gnome-netstatus-applet rather than change libgtk2.0-0
Investigating powermanagement-interface
Package powermanagement-interface has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to powermanagement-interface 0
  Holding Back powermanagement-interface rather than change libgtk2.0-0
Investigating evolution-plugins
Package evolution-plugins has broken dep on evolution
  Considering evolution 3 as a solution to evolution-plugins -1
  Holding Back evolution-plugins rather than change evolution
Investigating bleachbit
Package bleachbit has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to bleachbit -1
  Removing bleachbit rather than change python-gtk2
Investigating indicator-applet
Package indicator-applet has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 708 as a solution to indicator-applet -1
  Holding Back indicator-applet rather than change libgtk2.0-0
Investigating libcanberra-gtk-module
Package libcanberra-gtk-module has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 20 as a solution to libcanberra-gtk-module -1
  Holding Back libcanberra-gtk-module rather than change libcanberra-gtk0
Investigating gnome-spell
Package gnome-spell has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to gnome-spell -1
  Removing gnome-spell rather than change libbonoboui2-0
Investigating indicator-messages
Package indicator-messages has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 14 as a solution to indicator-messages -1
  Holding Back indicator-messages rather than change libdbusmenu-gtk1
Investigating contact-lookup-applet
Package contact-lookup-applet has broken dep on libgnomeui-0
  Considering libgnomeui-0 708 as a solution to contact-lookup-applet -1
  Removing contact-lookup-applet rather than change libgnomeui-0
Investigating python-aptdaemon-gtk
Package python-aptdaemon-gtk has broken dep on python-gtk2
  Considering python-gtk2 708 as a solution to python-aptdaemon-gtk -1
  Holding Back python-aptdaemon-gtk rather than change python-gtk2
Investigating python-appindicator
Package python-appindicator has broken dep on libappindicator0
  Considering libappindicator0 17 as a solution to python-appindicator -1
  Holding Back python-appindicator rather than change libappindicator0
Investigating gsmartcontrol
Package gsmartcontrol has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 5 as a solution to gsmartcontrol -1
  Holding Back gsmartcontrol rather than change libgtkmm-2.4-1c2a
Investigating gnome-pilot-conduits
Package gnome-pilot-conduits has broken dep on gnome-pilot
  Considering gnome-pilot 708 as a solution to gnome-pilot-conduits -1
  Removing gnome-pilot-conduits rather than change gnome-pilot
Investigating libeel2-2
Package libeel2-2 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 708 as a solution to libeel2-2 -1
  Removing libeel2-2 rather than change libbonoboui2-0
Investigating ubuntu-tweak
Package ubuntu-tweak has broken dep on python-gnome2
  Considering python-gnome2 708 as a solution to ubuntu-tweak -1
  Removing ubuntu-tweak rather than change python-gnome2
Investigating rhythmbox-plugin-cdrecorder
Package rhythmbox-plugin-cdrecorder has broken dep on libbrasero-media0
  Considering libbrasero-media0 1 as a solution to rhythmbox-plugin-cdrecorder -1
  Holding Back rhythmbox-plugin-cdrecorder rather than change libbrasero-media0
Investigating rhythmbox-plugins
Package rhythmbox-plugins has broken dep on libappindicator0
  Considering libappindicator0 17 as a solution to rhythmbox-plugins -1
  Holding Back rhythmbox-plugins rather than change libappindicator0
Investigating indicator-application
Package indicator-application has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 14 as a solution to indicator-application -1
  Holding Back indicator-application rather than change libdbusmenu-gtk1
Investigating rhythmbox-dbg
Package rhythmbox-dbg has broken dep on rhythmbox
  Considering rhythmbox 6 as a solution to rhythmbox-dbg -2
  Holding Back rhythmbox-dbg rather than change rhythmbox
Investigating gnome-dbg
Package gnome-dbg has broken dep on gnome-applets-dbg
  Considering gnome-applets-dbg 1 as a solution to gnome-dbg -2
  Holding Back gnome-dbg rather than change gnome-applets-dbg
Investigating indicator-sound
Package indicator-sound has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 14 as a solution to indicator-sound -2
  Holding Back indicator-sound rather than change libdbusmenu-gtk1
Investigating libwebkit-1.0-2-dbg
Package libwebkit-1.0-2-dbg has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 8 as a solution to libwebkit-1.0-2-dbg -2
  Holding Back libwebkit-1.0-2-dbg rather than change libwebkit-1.0-2
Investigating libgail-gnome-dbg
Package libgail-gnome-dbg has broken dep on libgail-gnome-module
  Considering libgail-gnome-module 708 as a solution to libgail-gnome-dbg -2
  Holding Back libgail-gnome-dbg rather than change libgail-gnome-module
Investigating libgoffice-dbg
Package libgoffice-dbg has broken dep on libgoffice-0.8-8
  Considering libgoffice-0.8-8 2 as a solution to libgoffice-dbg -2
  Holding Back libgoffice-dbg rather than change libgoffice-0.8-8
 Try to Re-Instate libgtk2.0-0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 9 as a solution to libgnome-keyring0 65
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
 Try to Re-Instate libgail18
Investigating gvfs
Package gvfs has broken dep on policykit-1-gnome
  Considering policykit-1-gnome 9 as a solution to gvfs 30
  Holding Back gvfs rather than change policykit-1-gnome
 Try to Re-Instate librsvg2-2
 Try to Re-Instate librsvg2-common
 Try to Re-Instate libgtk2.0-bin
 Try to Re-Instate libwnck22
 Try to Re-Instate ghostscript
 Try to Re-Instate libgtk2.0-cil
 Try to Re-Instate libvte9
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 9
  Holding Back gnome-keyring rather than change libgcr0
 Try to Re-Instate libedataserverui1.2-8
Investigating gnome-menus
Package gnome-menus has broken dep on python-gmenu
  Considering python-gmenu 708 as a solution to gnome-menus 8
  Removing gnome-menus rather than change python-gmenu
 Try to Re-Instate libnautilus-extension1
Investigating libpangomm-1.4-1
Package libpangomm-1.4-1 has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 5 as a solution to libpangomm-1.4-1 7
  Added libgtkmm-2.4-1c2a to the remove list
  Fixing libpangomm-1.4-1 via remove of libgtkmm-2.4-1c2a
 Try to Re-Instate libgail-common
 Try to Re-Instate libgnome-pilot2
 Try to Re-Instate zenity
Investigating firefox-branding
Package firefox-branding has broken dep on firefox
  Considering firefox 4 as a solution to firefox-branding 4
  Holding Back firefox-branding rather than change firefox
 Try to Re-Instate firefox
 Try to Re-Instate libglade2.0-cil
 Try to Re-Instate libpolkit-gnome0
 Try to Re-Instate policykit-gnome
 Try to Re-Instate gtk2-engines-murrine
Investigating anjuta-dbg
Package anjuta-dbg has broken dep on anjuta
  Considering anjuta 0 as a solution to anjuta-dbg 2
  Holding Back anjuta-dbg rather than change anjuta
 Try to Re-Instate gtk2-engines-pixbuf
 Try to Re-Instate libgtkhtml2-0
 Try to Re-Instate libmono-addins-gui0.2-cil
Investigating epiphany-browser-dbg
Package epiphany-browser-dbg has broken dep on epiphany-browser
  Considering epiphany-browser 1 as a solution to epiphany-browser-dbg 1
  Holding Back epiphany-browser-dbg rather than change epiphany-browser
 Try to Re-Instate libgtk2.0-dev
Investigating ubuntu-artwork
Package ubuntu-artwork has broken dep on light-themes
  Considering light-themes 0 as a solution to ubuntu-artwork 0
  Holding Back ubuntu-artwork rather than change light-themes
 Try to Re-Instate gcalctool
 Try to Re-Instate nspluginwrapper
 Try to Re-Instate gucharmap
 Try to Re-Instate scim-bridge-client-gtk
Investigating gnome-app-install
Package gnome-app-install has broken dep on software-center
  Considering software-center 0 as a solution to gnome-app-install 0
  Removing gnome-app-install rather than change software-center
Investigating gvfs-backends
Package gvfs-backends has broken dep on gvfs
  Considering gvfs 30 as a solution to gvfs-backends 0
  Holding Back gvfs-backends rather than change gvfs
 Try to Re-Instate gparted
Investigating gparted
Package gparted has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 7 as a solution to gparted 0
  Removing gparted rather than change libgtkmm-2.4-1c2a
 Try to Re-Instate gnome-mag
 Try to Re-Instate gnome-system-monitor
Investigating gnome-system-monitor
Package gnome-system-monitor has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 7 as a solution to gnome-system-monitor 0
  Removing gnome-system-monitor rather than change libgtkmm-2.4-1c2a
 Try to Re-Instate gnome-nettool
 Try to Re-Instate ghostscript-x
Investigating gpar2
Package gpar2 has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 7 as a solution to gpar2 0
  Removing gpar2 rather than change libgtkmm-2.4-1c2a
 Try to Re-Instate firefox-gnome-support
 Try to Re-Instate powermanagement-interface
 Try to Re-Instate gsmartcontrol
Investigating gsmartcontrol
Package gsmartcontrol has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 7 as a solution to gsmartcontrol -1
  Removing gsmartcontrol rather than change libgtkmm-2.4-1c2a
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 9 as a solution to libgnome-keyring0 65
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
 Try to Re-Instate gvfs
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 9
  Holding Back gnome-keyring rather than change libgcr0
 Try to Re-Instate firefox-branding
 Try to Re-Instate ubuntu-artwork
 Try to Re-Instate gvfs-backends
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 9 as a solution to libgnome-keyring0 65
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 9
  Holding Back gnome-keyring rather than change libgcr0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 9 as a solution to libgnome-keyring0 65
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 9
  Holding Back gnome-keyring rather than change libgcr0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 9 as a solution to libgnome-keyring0 65
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 9
  Holding Back gnome-keyring rather than change libgcr0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 9 as a solution to libgnome-keyring0 65
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 1 as a solution to gnome-keyring 9
  Holding Back gnome-keyring rather than change libgcr0
Done
Log time: 2010-10-01 19:56:15.727095

```

main.log:

```

2010-10-01 19:55:08,265 INFO Using config files '['./DistUpgrade.cfg.hardy']'
2010-10-01 19:55:08,272 INFO uname information: 'Linux kermit 2.6.24-28-server #1 SMP Thu Sep 16 14:49:46 UTC 2010 x86_64'
2010-10-01 19:55:08,272 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2010-10-01 19:55:08,803 INFO release-upgrader version '0.134.10' started
2010-10-01 19:55:08,980 DEBUG svg pixbuf loader failed (Error displaying image)
2010-10-01 19:55:08,981 ERROR html widget
Traceback (most recent call last):
  File "/tmp/tmpMIR8tj/DistUpgradeViewGtk.py", line 404, in __init__
    import webkit
ImportError: No module named webkit
2010-10-01 19:55:08,982 DEBUG Using 'DistUpgradeViewGtk' view
2010-10-01 19:55:09,008 DEBUG aufsOptionsAndEnvironmentSetup()
2010-10-01 19:55:09,008 DEBUG using '/tmp/upgrade-rw-BN_kcC' as aufs_rw_dir
2010-10-01 19:55:09,008 DEBUG using '/tmp/upgrade-chroot-t9sYzI' as aufs chroot dir
2010-10-01 19:55:09,008 DEBUG enable dpkg --force-overwrite
2010-10-01 19:55:09,079 DEBUG lsb-release: 'hardy'
2010-10-01 19:55:09,085 DEBUG who -m --ips: ''
2010-10-01 19:55:09,086 DEBUG _pythonSymlinkCheck run
2010-10-01 19:55:09,099 DEBUG openCache()
2010-10-01 19:55:09,540 DEBUG /openCache(), new cache size 25012
2010-10-01 19:55:09,540 DEBUG needServerMode(): can not find a desktop meta package or key deps, running in server mode
2010-10-01 19:55:09,541 DEBUG checkViewDepends()
2010-10-01 19:55:09,541 DEBUG running doUpdate() (showErrors=False)
2010-10-01 19:55:09,622 WARNING updateStatus: dlFailed on 'http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,634 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,639 WARNING updateStatus: dlFailed on 'http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,640 WARNING updateStatus: dlFailed on 'http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,640 WARNING updateStatus: dlFailed on 'http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,641 WARNING updateStatus: dlFailed on 'http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,672 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,672 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,672 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,673 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,673 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,673 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,673 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:09,917 DEBUG openCache()
2010-10-01 19:55:10,360 DEBUG /openCache(), new cache size 25012
2010-10-01 19:55:10,360 DEBUG doPostInitialUpdate
2010-10-01 19:55:10,360 DEBUG Plugin modules in ./plugins: langpack_manual_plugin.py dpkg_status_plugin.py remove_lilo_plugin.py kdelibs4to5_plugin.py deb_plugin.py
2010-10-01 19:55:10,361 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2010-10-01 19:55:10,361 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2010-10-01 19:55:10,362 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2010-10-01 19:55:10,362 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2010-10-01 19:55:10,362 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2010-10-01 19:55:10,363 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2010-10-01 19:55:10,363 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2010-10-01 19:55:10,363 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2010-10-01 19:55:10,364 DEBUG Loading module ./plugins/deb_plugin.py
2010-10-01 19:55:10,364 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2010-10-01 19:55:10,364 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2010-10-01 19:55:10,364 DEBUG plugins for condition 'lucidPostInitialUpdate' are '[]'
2010-10-01 19:55:10,364 DEBUG plugins for condition 'from_hardyPostInitialUpdate' are '[]'
2010-10-01 19:55:10,364 DEBUG quirks: running lucidPostInitialUpdate
2010-10-01 19:55:10,364 DEBUG running lucidPostInitialUpdate
2010-10-01 19:55:15,189 DEBUG no PkgRecord found for 'jabberd2', skipping 
2010-10-01 19:55:19,398 DEBUG no PkgRecord found for 'freeradius-common', skipping 
2010-10-01 19:55:19,462 DEBUG no PkgRecord found for 'libwbclient0', skipping 
2010-10-01 19:55:19,511 DEBUG no PkgRecord found for 'libtonezone2.0', skipping 
2010-10-01 19:55:19,596 DEBUG no PkgRecord found for 'virtualbox-3.1', skipping 
2010-10-01 19:55:19,768 DEBUG no PkgRecord found for 'dahdi-linux', skipping 
2010-10-01 19:55:19,781 DEBUG no PkgRecord found for 'timevault', skipping 
2010-10-01 19:55:19,839 DEBUG no PkgRecord found for 'libcap2', skipping 
2010-10-01 19:55:19,940 DEBUG Foreign: gstreamer0.10-fluendo-plugins-doc gstreamer0.10-fluendo-plugins-wmv-doc
2010-10-01 19:55:19,941 DEBUG Obsolete: linux-image-2.6.24-19-server gsmartcontrol ubuntu-tweak linux-headers-2.6.24-19 linux-headers-2.6.24-19-server libntfs-3g28 jdownloader cksfv bleachbit avg85flx virtualbox-3.2 libopencore-amr linux-headers-2.6.24-19-generic libtheora dvdwizard libgnutls26
2010-10-01 19:55:19,941 DEBUG updateSourcesList()
2010-10-01 19:55:19,985 DEBUG rewriteSourcesList()
2010-10-01 19:55:19,986 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main #Added by software-properties'
2010-10-01 19:55:19,986 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu/ lucid restricted main #Added by software-properties' updated to new dist
2010-10-01 19:55:19,986 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy main restricted'
2010-10-01 19:55:19,986 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid main restricted' updated to new dist
2010-10-01 19:55:19,986 DEBUG examining: 'deb-src http://be.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties'
2010-10-01 19:55:19,986 DEBUG entry 'deb-src http://be.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties' updated to new dist
2010-10-01 19:55:19,987 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy universe'
2010-10-01 19:55:19,987 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid universe' updated to new dist
2010-10-01 19:55:19,987 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy multiverse'
2010-10-01 19:55:19,987 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid multiverse' updated to new dist
2010-10-01 19:55:19,987 DEBUG examining: 'deb http://archive.canonical.com/ubuntu hardy partner'
2010-10-01 19:55:19,987 DEBUG entry 'deb http://archive.canonical.com/ubuntu lucid partner' updated to new dist
2010-10-01 19:55:19,987 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu hardy partner'
2010-10-01 19:55:19,987 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu lucid partner' updated to new dist
2010-10-01 19:55:19,987 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security main restricted'
2010-10-01 19:55:19,987 DEBUG entry 'deb http://security.ubuntu.com/ubuntu lucid-security main restricted' updated to new dist
2010-10-01 19:55:19,987 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties'
2010-10-01 19:55:19,987 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties' updated to new dist
2010-10-01 19:55:19,987 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security universe'
2010-10-01 19:55:19,988 DEBUG entry 'deb http://security.ubuntu.com/ubuntu lucid-security universe' updated to new dist
2010-10-01 19:55:19,988 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security multiverse'
2010-10-01 19:55:19,988 DEBUG entry 'deb http://security.ubuntu.com/ubuntu lucid-security multiverse' updated to new dist
2010-10-01 19:55:19,988 DEBUG examining: 'deb http://be.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe'
2010-10-01 19:55:19,988 DEBUG entry 'deb http://be.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe' updated to new dist
2010-10-01 19:55:19,992 DEBUG running doUpdate() (showErrors=True)
2010-10-01 19:55:20,078 WARNING updateStatus: dlFailed on 'http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,078 WARNING updateStatus: dlFailed on 'http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,082 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,091 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,093 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,094 WARNING updateStatus: dlFailed on 'http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,094 WARNING updateStatus: dlFailed on 'http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,094 WARNING updateStatus: dlFailed on 'http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,098 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,098 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,099 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,100 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:20,109 WARNING updateStatus: dlFailed on 'http://be.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2' 
2010-10-01 19:55:35,732 DEBUG openCache()
2010-10-01 19:55:37,877 DEBUG /openCache(), new cache size 30379
2010-10-01 19:55:37,877 DEBUG needServerMode(): can not find a desktop meta package or key deps, running in server mode
2010-10-01 19:56:13,553 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2010-10-01 19:56:13,553 DEBUG abort called
2010-10-01 19:56:13,554 DEBUG openCache()
2010-10-01 19:56:15,807 DEBUG /openCache(), new cache size 25012
2010-10-01 19:56:15,813 DEBUG enabling apt cron job

```

---

### Post by jverdeyen on 2010-10-04
Or should I go from 8.04 -> 8.10 -> 9.04 -> 9.10 -> 10.04...

---

### Post by mörgæs on 2010-10-04
That will only make it a lot worse.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

