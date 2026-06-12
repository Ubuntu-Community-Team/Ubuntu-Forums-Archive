---
title: "&quot;pkgProblemResolver:Resolve generated breaks&quot; going from 8.04 LTS to 10.04 LTS"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by poptoppop on 2011-08-07
I've searched around and seen this problem quite a few places, but alas none of the help I've tried has actually helped me.  So here I am.

I'm finally getting around to jumping from Hardy (8.04 LTS) to Lucid (10.04), and I'm getting the dreaded error:

$ **sudo do-release-upgrade**
Checking for a new ubuntu release
*...blah blah blah...*
[B]E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages.[/B]

I've tried all the advice I've found.  Among other things:
$ **sudo apt-get update**
$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I've also deactivated (commented out) all my non-Ubuntu repositories and removed (I think?) what seemed to be likely culprit packages:
[LIST]
[*] a special wine build I had
[*] Dropbox
[*] a special ffmpeg build
[*] nvidia drivers
[*] anything else I saw in Synaptic from local/non-free or local/universe or local/multiverse
[/list]

Here's the contents of */var/log/dist-upgrade/apt.log* for the latest attempt:
```
Log time: 2011-08-07 17:13:17.280935
Log time: 2011-08-07 17:13:21.693685
Log time: 2011-08-07 17:13:39.786876
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
Installing libblkid1 as dep of util-linux
Installing libuuid1 as dep of libblkid1
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libdevmapper-event1.02.1 as dep of lvm2
Installing watershed as dep of lvm2
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
Installing libgtk2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libmono-cairo2.0-cil as dep of libgtk2.0-cil
Installing libmono-addins0.2-cil as dep of libmono-addins-gui0.2-cil
Installing libmono-posix2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libmcpp0 as dep of mcpp
Installing update-inetd as dep of sane-utils
Installing libfile-copy-recursive-perl as dep of update-inetd
Installing tex-common as dep of texlive-lang-finnish
Installing texlive-base as dep of texlive-lang-finnish
Installing texlive-doc-base as dep of texlive-base
Installing texlive-common as dep of texlive-doc-base
Installing luatex as dep of texlive-base
Installing libpoppler5 as dep of luatex
Installing texlive-luatex as dep of luatex
Installing texlive-binaries as dep of texlive-base
Installing libkpathsea5 as dep of texlive-binaries
Installing libstdc++6 as dep of texlive-binaries
Installing gcc-4.4-base as dep of libstdc++6
Installing libgcr0 as dep of gnome-keyring
Installing libgp11-0 as dep of libgcr0
Installing libflickrnet2.2-cil as dep of f-spot
Installing libmono-system-web2.0-cil as dep of libflickrnet2.2-cil
Installing libmono2.0-cil as dep of libmono-system-web2.0-cil
Installing libgdiplus as dep of libmono-system-web2.0-cil
Installing libgconf2.0-cil as dep of f-spot
Installing libglade2.0-cil as dep of f-spot
Installing libgnome-keyring1.0-cil as dep of f-spot
Installing libgnome-vfs2.0-cil as dep of f-spot
Installing libgnome2.24-cil as dep of f-spot
Installing libart2.0-cil as dep of libgnome2.24-cil
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libnunit2.4-cil as dep of f-spot
Installing libmono-system-runtime2.0-cil as dep of libnunit2.4-cil
Installing gvfs-bin as dep of f-spot
Installing gvfs as dep of gvfs-bin
Installing libgdu0 as dep of gvfs
Installing udisks as dep of libgdu0
Installing libatasmart4 as dep of udisks
Installing libgudev-1.0-0 as dep of udisks
Installing libparted0debian1 as dep of udisks
Installing libsgutils2-2 as dep of udisks
Installing mtools as dep of udisks
Installing ntfsprogs as dep of udisks
Installing libfuse2 as dep of ntfsprogs
Installing mount as dep of libfuse2
Installing libntfs10 as dep of ntfsprogs
Installing libgvfscommon0 as dep of gvfs
Installing libcupsys2 as dep of libgnomecupsui1.0-1c2a
Installing libbsd0 as dep of libedit2
Installing linux-headers-generic-pae as dep of linux-headers-server
Installing linux-headers-2.6.32-33-generic-pae as dep of linux-headers-generic-pae
Installing linux-headers-2.6.32-33 as dep of linux-headers-2.6.32-33-generic-pae
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libpcap0.8 as dep of nethogs
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libiec61883-0 as dep of libfreebob0
Installing libraw1394-11 as dep of libiec61883-0
Installing libsm6 as dep of libsm-dev
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
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libtag1-vanilla as dep of libtag1c2a
Installing libv4l-0 as dep of gstreamer0.10-plugins-good
Installing gstreamer0.10-nice as dep of libgstfarsight0.10-0
Installing libidn11 as dep of libpurple0
Installing libperl5.10 as dep of libpurple0
Installing perl-base as dep of libperl5.10
Installing libuuid-perl as dep of doc-base
Installing perl as dep of libuuid-perl
Installing perl-modules as dep of perl
Installing libmldbm-perl as dep of doc-base
Installing libfreezethaw-perl as dep of libmldbm-perl
Installing libsilcclient-1.1-3 as dep of libpurple0
Installing libzephyr4 as dep of libpurple0
Installing python-numpy as dep of python-netcdf
Installing libgfortran3 as dep of python-numpy
Installing python-scientific as dep of python-netcdf
new important dependency: pyro
Installing pyro as dep of python-scientific
Installing python-support as dep of pyro
Installing samba-common-bin as dep of backuppc
Installing libcap2 as dep of samba-common-bin
Installing libtalloc2 as dep of samba-common-bin
Installing libwbclient0 as dep of samba-common-bin
Installing samba-common as dep of samba-common-bin
Installing libsocket6-perl as dep of backuppc
new important dependency: rrdtool
Installing rrdtool as dep of backuppc
Installing librrd4 as dep of rrdtool
new important dependency: libio-dirent-perl
Installing libio-dirent-perl as dep of backuppc
Installing libopenal1 as dep of python-openal
Installing libgmime2.4-cil as dep of tomboy
Installing libgmime-2.4-2 as dep of libgmime2.4-cil
Installing libgnomepanel2.24-cil as dep of tomboy
Installing liblaunchpad-integration1.0-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
Installing python-zope.interface as dep of python-twisted-core
Installing libbz2-1.0 as dep of bzip2
Installing libopal3.6.6 as dep of ekiga
Installing libgsm1 as dep of libopal3.6.6
Installing libpt2.6.5 as dep of libopal3.6.6
Installing libspeexdsp1 as dep of libopal3.6.6
Installing libpt2.6.5-plugins as dep of ekiga
Installing libespeak1 as dep of espeak
Installing libportaudio2 as dep of libespeak1
Installing libjack0 as dep of libportaudio2
Installing espeak-data as dep of libespeak1
Installing libilmbase6 as dep of kdelibs4c2a
Installing libopenexr6 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing kdelibs5-data as dep of kdelibs-data
Installing python2.6-examples as dep of python-examples
new important dependency: libgpm2
Installing libgpm2 as dep of libncurses5
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libopenrawgnome1 as dep of gthumb
Installing libopenraw1 as dep of libopenrawgnome1
Installing gthumb-data as dep of gthumb
Installing cups-common as dep of cupsys-common
Installing libice6 as dep of libice-dev
Installing libimlib2 as dep of libimlib2-dev
Installing liblzma1 as dep of libarchive1
Installing update-manager-core as dep of update-manager
Installing python-apt as dep of update-manager-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
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
new important dependency: vim-addon-manager
Installing vim-addon-manager as dep of bicyclerepair
Installing ruby as dep of vim-addon-manager
Installing ruby1.8 as dep of ruby
Installing libruby1.8 as dep of ruby1.8
Installing gnome-media-common as dep of gnome-media
Installing libxext6 as dep of libxext-dev
Installing mysql-client-5.1 as dep of mysql-client
Installing mysql-common as dep of mysql-client-5.1
Installing libmysqlclient16 as dep of mysql-client-5.1
Installing mysql-client-core-5.1 as dep of mysql-client-5.1
Installing php-geshi as dep of websvn
Installing libexempi3 as dep of nautilus
Installing libnautilus-extension1 as dep of nautilus
Installing nautilus-data as dep of nautilus
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
Installing libgnome2-common as dep of libgnome2-0
Installing system-config-printer-udev as dep of hal-cups-utils
Installing python-cups as dep of system-config-printer-udev
Installing python-cupshelpers as dep of system-config-printer-udev
Installing libbind9-60 as dep of bind9-host
Installing libdns64 as dep of libbind9-60
Installing libgeoip1 as dep of libdns64
new important dependency: geoip-database
Installing geoip-database as dep of libgeoip1
Installing libisc60 as dep of libdns64
Installing libisccfg60 as dep of libbind9-60
Installing libisccc60 as dep of libisccfg60
Installing liblwres60 as dep of bind9-host
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing gimp-help-common as dep of gimp-help-en
Installing libgamin0 as dep of gamin
Installing python-imaging as dep of python-imaging-sane
Installing linux-headers-2.6.32-33-generic as dep of linux-headers-generic
Installing dpkg-dev as dep of debhelper
Installing xz-utils as dep of dpkg-dev
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing xserver-xorg-video-apm as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ark as dep of xserver-xorg-video-all
Installing xserver-xorg-video-chips as dep of xserver-xorg-video-all
Installing xserver-xorg-video-cirrus as dep of xserver-xorg-video-all
Installing xserver-xorg-video-fbdev as dep of xserver-xorg-video-all
Installing xserver-xorg-video-geode as dep of xserver-xorg-video-all
new important dependency: xserver-xorg-video-cyrix
Installing xserver-xorg-video-cyrix as dep of xserver-xorg-video-geode
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
Installing libcdio10 as dep of gstreamer0.10-plugins-ugly
Installing libdvdread4 as dep of gstreamer0.10-plugins-ugly
Installing libmad0 as dep of gstreamer0.10-plugins-ugly
Installing libopencore-amrnb0 as dep of gstreamer0.10-plugins-ugly
Installing libopencore-amrwb0 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
new important dependency: cups-client
Installing cups-client as dep of xsane
Installing libcupsimage2 as dep of cups-client
Installing libpoppler-glib4 as dep of tracker
Installing libraptor1 as dep of tracker
new important dependency: odt2txt
Installing odt2txt as dep of tracker
Installing libzip1 as dep of odt2txt
Installing libgcj-common as dep of libgcj-bc
Installing libgcj10 as dep of libgcj-bc
Installing gcj-4.4-base as dep of libgcj10
Installing gcj-4.4-jre-lib as dep of libgcj10
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing libasound2-dev as dep of libsdl1.2-dev
Installing libesd0-dev as dep of libsdl1.2-dev
Installing libaudiofile-dev as dep of libesd0-dev
Installing libaudiofile0 as dep of libaudiofile-dev
Installing libpulse-dev as dep of libsdl1.2-dev
Installing libpulse-browse0 as dep of libpulse-dev
Installing libxt-dev as dep of libpulse-dev
Installing libxt6 as dep of libxt-dev
Installing libavahi-client-dev as dep of libpulse-dev
Installing libavahi-client3 as dep of libavahi-client-dev
Installing libavahi-common-dev as dep of libavahi-client-dev
Installing libavahi-common3 as dep of libavahi-common-dev
Installing libdbus-1-dev as dep of libavahi-client-dev
Installing libdirectfb-dev as dep of libsdl1.2-dev
Installing libdirectfb-extra as dep of libdirectfb-dev
Installing libsysfs-dev as dep of libdirectfb-dev
Installing libsysfs2 as dep of libsysfs-dev
Installing libaa1-dev as dep of libsdl1.2-dev
Installing libslang2-dev as dep of libaa1-dev
Installing libslang2 as dep of libslang2-dev
Installing libncurses5-dev as dep of libaa1-dev
Installing libcaca-dev as dep of libsdl1.2-dev
Installing libaudio-dev as dep of libsdl1.2-dev
Installing libaudio2 as dep of libaudio-dev
Installing libsnmp-base as dep of libsnmp15
Installing gawk as dep of libsnmp-base
Installing libsensors4 as dep of libsnmp15
Installing lm-sensors as dep of libsensors4
Installing fancontrol as dep of lm-sensors
Installing xserver-xorg-video-r128 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-mach64 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-radeon as dep of xserver-xorg-video-ati
Installing amule-common as dep of amule
Installing libcrypto++8 as dep of amule
Installing libupnp3 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing libmagickcore2 as dep of obex-data-server
Installing libmagickwand2 as dep of obex-data-server
Installing libiw30 as dep of wireless-tools
Installing texlive-fonts-recommended as dep of texlive
Installing texlive-latex-recommended as dep of texlive
Installing texlive-latex-base as dep of texlive-latex-recommended
Installing ijsgutenprint as dep of foomatic-db-gutenprint
Installing libgutenprint2 as dep of ijsgutenprint
Installing cups as dep of foomatic-db-gutenprint
Installing libcupscgi1 as dep of cups
Installing libcupsdriver1 as dep of cups
Installing libcupsmime1 as dep of cups
Installing libcupsppdc1 as dep of cups
Installing poppler-utils as dep of cups
Installing foomatic-filters as dep of cups
Installing cups-driver-gutenprint as dep of cups
Installing ghostscript-cups as dep of cups-driver-gutenprint
Installing ghostscript as dep of ghostscript-cups
Installing libgs8 as dep of ghostscript
Installing librasqal2 as dep of librdf0
Installing libsvn1 as dep of libapache2-svn
Installing libapr1 as dep of libsvn1
Installing libaprutil1 as dep of libsvn1
Installing apache2.2-bin as dep of apache2.2-common
Installing libaprutil1-dbd-sqlite3 as dep of apache2.2-bin
Installing libaprutil1-ldap as dep of apache2.2-bin
Installing libneon27-gnutls as dep of libsvn1
Installing libnewt0.52 as dep of whiptail
new important dependency: ttf-sazanami-mincho
Installing ttf-sazanami-mincho as dep of ttf-kochi-mincho
Installing liblua5.1-0 as dep of nmap
Installing busybox-static as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: apt-transport-https
Installing apt-transport-https as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
new important dependency: irqbalance
Installing irqbalance as dep of ubuntu-standard
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcap-ng0 as dep of irqbalance
Installing libpixman-1-dev as dep of xserver-xorg-dev
Installing x11proto-core-dev as dep of xserver-xorg-dev
Installing x11proto-input-dev as dep of xserver-xorg-dev
Installing x11proto-randr-dev as dep of xserver-xorg-dev
Installing x11proto-render-dev as dep of xserver-xorg-dev
Installing x11proto-dri2-dev as dep of xserver-xorg-dev
Installing libxkbfile-dev as dep of xserver-xorg-dev
Installing libxkbfile1 as dep of libxkbfile-dev
Installing libpciaccess-dev as dep of xserver-xorg-dev
Installing brltty as dep of brltty-x11
Installing libgucharmap7 as dep of gucharmap
Installing libnm-glib2 as dep of network-manager
Installing libnm-util1 as dep of libnm-glib2
Installing libgnome-bluetooth7 as dep of network-manager-gnome
Installing mobile-broadband-provider-info as dep of network-manager-gnome
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
Installing libavahi-core6 as dep of avahi-daemon
Installing dbus as dep of avahi-daemon
Installing aisleriot as dep of gnome-games
Installing guile-1.8-libs as dep of aisleriot
Installing gnome-games-common as dep of aisleriot
Installing glchess as dep of gnome-games
Installing python-gtkglext1 as dep of glchess
Installing libgtkglext1 as dep of python-gtkglext1
Installing glines as dep of gnome-games
Installing gnect as dep of gnome-games
Installing gnibbles as dep of gnome-games
Installing libclutter-1.0-0 as dep of gnibbles
Installing libclutter-gtk-0.10-0 as dep of gnibbles
Installing gnobots2 as dep of gnome-games
Installing gnome-mahjongg as dep of gnome-games
Installing gnome-sudoku as dep of gnome-games
Installing gnomine as dep of gnome-games
Installing gnotravex as dep of gnome-games
Installing gnotski as dep of gnome-games
Installing gtali as dep of gnome-games
Installing iagno as dep of gnome-games
Installing lightsoff as dep of gnome-games
Installing seed as dep of lightsoff
Installing libseed0 as dep of seed
Installing libgirepository1.0-0 as dep of libseed0
Installing libmpfr1ldbl as dep of libseed0
Installing gnome-js-common as dep of libseed0
Installing gir1.0-glib-2.0 as dep of libseed0
Installing gir1.0-clutter-1.0 as dep of libseed0
Installing gir1.0-freedesktop as dep of gir1.0-clutter-1.0
Installing gir1.0-pango-1.0 as dep of gir1.0-clutter-1.0
Installing gir1.0-gstreamer-0.10 as dep of libseed0
Installing gir1.0-gtk-2.0 as dep of libseed0
Installing gir1.0-atk-1.0 as dep of gir1.0-gtk-2.0
Installing gir1.0-gconf-2.0 as dep of lightsoff
Installing gir1.0-clutter-gtk-0.10 as dep of lightsoff
Installing quadrapassel as dep of gnome-games
Installing swell-foop as dep of gnome-games
Installing gdebi-core as dep of gdebi
Installing python-debian as dep of gdebi-core
Installing default-jre-headless as dep of libxt-java
Installing openjdk-6-jre-headless as dep of default-jre-headless
Installing openjdk-6-jre-lib as dep of openjdk-6-jre-headless
Installing ca-certificates-java as dep of openjdk-6-jre-headless
Installing ca-certificates as dep of ca-certificates-java
Installing tzdata-java as dep of openjdk-6-jre-headless
Installing tzdata as dep of tzdata-java
Installing icedtea-6-jre-cacao as dep of openjdk-6-jre-headless
Installing libasound2-plugins as dep of pulseaudio
new important dependency: rtkit
Installing rtkit as dep of pulseaudio
Installing smarty as dep of gallery2
Installing libphp-adodb as dep of gallery2
Installing libxinerama1 as dep of libxinerama-dev
Installing cups-ppdc as dep of cupsddk
Installing libcairo2-dev as dep of libpango1.0-dev
Installing libxcb-render0-dev as dep of libcairo2-dev
Installing libxcb-render-util0-dev as dep of libcairo2-dev
Installing libavidemux0 as dep of avidemux
Installing mjpegtools as dep of libavidemux0
Installing libmjpegtools-1.9 as dep of mjpegtools
Installing libquicktime1 as dep of libmjpegtools-1.9
Installing libavcodec52 as dep of libquicktime1
Installing libavutil49 as dep of libavcodec52
Installing libschroedinger-1.0-0 as dep of libavcodec52
Installing liboil0.3 as dep of libschroedinger-1.0-0
Installing libfaad2 as dep of libquicktime1
Installing libswscale0 as dep of libquicktime1
Installing twolame as dep of libavidemux0
new important dependency: avidemux-plugins-gtk
Installing avidemux-plugins-gtk as dep of avidemux
Installing avidemux-plugins-common as dep of avidemux-plugins-gtk
Installing libmp3lame0 as dep of avidemux-plugins-common
Installing libx264-85 as dep of avidemux-plugins-common
Installing upower as dep of gnome-power-manager
Installing libupower-glib1 as dep of upower
Installing lynx-cur as dep of lynx
Installing nautilus-scripts-manager as dep of nautilus-script-audio-convert
Installing exim4-base as dep of exim4-daemon-light
Installing libglibmm-2.4-1c2a as dep of gparted
Installing libgtkmm-2.4-1c2a as dep of gparted
Installing libcairomm-1.0-1 as dep of libgtkmm-2.4-1c2a
Installing libpangomm-1.4-1 as dep of libgtkmm-2.4-1c2a
Installing libapache2-mod-php5 as dep of php5
Installing php5-common as dep of libapache2-mod-php5
Installing libcurl3-gnutls as dep of python-pycurl
Installing totem as dep of totem-plugins
Installing totem-common as dep of totem
new important dependency: totem-mozilla
Installing totem-mozilla as dep of totem
Installing libgdata6 as dep of totem-plugins
Installing libgdata-common as dep of libgdata6
Installing python-rdflib as dep of totem-plugins
Installing python-httplib2 as dep of totem-plugins
Installing python-gnomeapplet as dep of gnome-mag
Installing dovecot-common as dep of dovecot-imapd
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
Installing libgpgme11 as dep of seahorse
Installing gnupg as dep of seahorse
new important dependency: gnupg-curl
Installing gnupg-curl as dep of gnupg
Installing xserver-xorg-input-mouse as dep of xserver-xorg-input-vmmouse
Installing readahead-fedora as dep of readahead
Installing e2fslibs as dep of readahead-fedora
Installing libaudit0 as dep of readahead-fedora
Installing rarian-compat as dep of scrollkeeper
Installing xml-core as dep of rarian-compat
Installing libcrack2 as dep of netatalk
Installing cracklib-runtime as dep of libcrack2
new important dependency: db4.8-util
Installing db4.8-util as dep of netatalk
new important dependency: libpam-cracklib
Installing libpam-cracklib as dep of netatalk
Installing libhpmud0 as dep of hpijs
new important dependency: keyutils
Installing keyutils as dep of smbfs
Installing python-reportbug as dep of reportbug
Installing mysql-client-5.0 as dep of mysql-server-5.0
Installing light-themes as dep of ubuntu-artwork
Installing ubuntu-mono as dep of light-themes
Installing humanity-icon-theme as dep of ubuntu-mono
Installing gtk2-engines-murrine as dep of light-themes
Installing adium-theme-ubuntu as dep of ubuntu-artwork
new important dependency: byobu
Installing byobu as dep of screen
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
new important dependency: debian-faq
Installing debian-faq as dep of doc-debian
Installing openssl as dep of openssl-blacklist
Installing python-tk as dep of python-imaging-tk
Installing blt as dep of python-tk
Installing tcl8.5 as dep of python-tk
Installing tk8.5 as dep of python-tk
Installing gtk2-engines as dep of gnome-themes
Installing gnome-themes-selected as dep of gnome-themes
Installing cpu-checker as dep of update-notifier-common
Installing libxrender1 as dep of libxrender-dev
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
Installing python-avahi as dep of desktopcouch
Installing python-gnomekeyring as dep of python-desktopcouch
Installing python-oauth as dep of python-desktopcouch-records
Installing gwibber-service as dep of gwibber
Installing python-indicate as dep of gwibber-service
Installing libindicate-gtk2 as dep of python-indicate
Installing ubuntuone-client-gnome as dep of indicator-me
Installing ubuntuone-client as dep of ubuntuone-client-gnome
Installing python-ubuntuone-client as dep of ubuntuone-client
Installing python-ubuntuone-storageprotocol as dep of python-ubuntuone-client
Installing python-protobuf as dep of python-ubuntuone-storageprotocol
Installing protobuf-compiler as dep of python-protobuf
Installing libprotobuf5 as dep of protobuf-compiler
Installing libprotoc5 as dep of protobuf-compiler
Installing python-twisted-web as dep of python-ubuntuone-client
Installing python-pyinotify as dep of python-ubuntuone-client
Installing python-twisted-names as dep of python-ubuntuone-client
Installing python-configglue as dep of ubuntuone-client
Installing libpam-ck-connector as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libsdl1.2debian-pulseaudio as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing notify-osd as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing notify-osd-icons as dep of notify-osd
Installing software-center as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing python-xapian as dep of software-center
Installing libxapian15 as dep of python-xapian
Installing python-aptdaemon as dep of software-center
Installing aptdaemon as dep of python-aptdaemon
Installing python-aptdaemon-gtk as dep of software-center
Installing apt-xapian-index as dep of software-center
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
Installing libgd2-noxpm as dep of libm17n-0
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
Installing openoffice.org-base-core as dep of openoffice.org-writer
Installing libwps-0.1-1 as dep of openoffice.org-writer
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
new important dependency: ttf-liberation
Installing ttf-liberation as dep of ubuntu-desktop
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
new important dependency: automake
Installing automake as dep of autoconf
Installing libdca-dev as dep of libdts-dev
Installing libdca0 as dep of libdca-dev
Installing libscim8c2a as dep of scim-modules-socket
Installing libvte9 as dep of vinagre
Installing linux-image-generic-pae as dep of linux-image-server
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing linux-image-2.6.32-33-generic-pae as dep of linux-image-generic-pae
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing wireless-crda as dep of linux-image-2.6.32-33-generic-pae
Installing linux-firmware as dep of linux-image-generic-pae
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libxdmcp6 as dep of libxdmcp-dev
Installing krb5-multidev as dep of libkrb5-dev
Installing libgssrpc4 as dep of krb5-multidev
Installing libkadm5srv-mit7 as dep of krb5-multidev
Installing libkdb5-4 as dep of libkadm5srv-mit7
Installing libkadm5clnt-mit7 as dep of krb5-multidev
Installing python-apport as dep of apport
Installing python-launchpadlib as dep of python-apport
Installing python-wadllib as dep of python-launchpadlib
Installing python-lazr.uri as dep of python-wadllib
Installing python-lazr.restfulclient as dep of python-launchpadlib
new important dependency: apport-symptoms
Installing apport-symptoms as dep of apport
Installing cpp as dep of g++
Installing cpp-4.4 as dep of cpp
Installing gcc as dep of g++
Installing gcc-4.4 as dep of gcc
Installing binutils as dep of gcc-4.4
Installing libgcc1 as dep of gcc-4.4
Installing g++-4.4 as dep of g++
Installing libstdc++6-4.4-dev as dep of g++-4.4
Installing libwww-perl as dep of librpc-xml-perl
Installing libxml-libxml-perl as dep of librpc-xml-perl
Installing libxml-namespacesupport-perl as dep of libxml-libxml-perl
Installing libxml-sax-perl as dep of libxml-libxml-perl
Installing libxml-sax-expat-perl as dep of libxml-sax-perl
Installing libogg0 as dep of libogg-dev
Installing xviewg as dep of xviewg-dev
Installing usplash as dep of usplash-theme-ubuntu
Installing texlive-generic-recommended as dep of texlive-pstricks
new important dependency: ps2eps
Installing ps2eps as dep of texlive-pstricks
new important dependency: texlive-extra-utils
Installing texlive-extra-utils as dep of texlive-pstricks
Installing lacheck as dep of texlive-extra-utils
Installing libgd2-xpm as dep of php5-gd
Installing gnome-terminal-data as dep of gnome-terminal
Installing libpng12-0 as dep of libpng12-dev
Installing libpci3 as dep of toshset
Installing libpolkit-gtk-1-0 as dep of gnome-system-tools
Installing libgif4 as dep of libgif-dev
Installing libpolkit2 as dep of policykit
Installing libsys-hostname-long-perl as dep of libmail-sendmail-perl
Installing python-ogg as dep of python-pyvorbis
new important dependency: nvidia-common
Installing nvidia-common as dep of jockey-common
Installing nvidia-current-modaliases as dep of nvidia-common
Installing nvidia-173-modaliases as dep of nvidia-common
Installing nvidia-96-modaliases as dep of nvidia-common
new important dependency: fglrx-modaliases
Installing fglrx-modaliases as dep of jockey-common
new important dependency: bcmwl-modaliases
Installing bcmwl-modaliases as dep of jockey-common
new important dependency: libltdl-dev
Installing libltdl-dev as dep of libtool
Installing libgdict-1.0-6 as dep of gnome-utils
Installing kdebase-runtime as dep of k3b
Installing kdelibs5 as dep of kdebase-runtime
Installing libattica0 as dep of kdelibs5
Installing libqt4-network as dep of libattica0
Installing libqtcore4 as dep of libqt4-network
Installing libdbusmenu-qt2 as dep of kdelibs5
Installing libqt4-dbus as dep of libdbusmenu-qt2
Installing libqt4-xml as dep of libqt4-dbus
Installing libqtgui4 as dep of libdbusmenu-qt2
Installing libphonon4 as dep of kdelibs5
Installing libqt4-designer as dep of libphonon4
Installing libqt4-script as dep of libqt4-designer
Installing libpolkit-qt-1-0 as dep of kdelibs5
Installing libqt4-qt3support as dep of kdelibs5
Installing libqt4-sql as dep of libqt4-qt3support
Installing libqt4-sql-mysql as dep of libqt4-sql
Installing libqt4-svg as dep of kdelibs5
Installing libqt4-webkit as dep of kdelibs5
Installing libqt4-xmlpatterns as dep of libqt4-webkit
Installing libsoprano4 as dep of kdelibs5
Installing libclucene0ldbl as dep of libsoprano4
Installing soprano-daemon as dep of libsoprano4
Installing libiodbc2 as dep of soprano-daemon
Installing virtuoso-nepomuk as dep of soprano-daemon
Installing libstreamanalyzer0 as dep of kdelibs5
Installing libexiv2-6 as dep of libstreamanalyzer0
Installing exiv2 as dep of libexiv2-6
Installing libstreams0 as dep of libstreamanalyzer0
Installing kdelibs-bin as dep of kdelibs5
Installing shared-desktop-ontologies as dep of kdelibs5
Installing libplasma3 as dep of kdebase-runtime
Installing libqca2 as dep of libplasma3
Installing libqt4-opengl as dep of libplasma3
Installing libssh-4 as dep of kdebase-runtime
Installing kdebase-runtime-data as dep of kdebase-runtime
Installing oxygen-icon-theme as dep of kdebase-runtime
Installing phonon-backend-xine as dep of kdebase-runtime
Installing libxine1 as dep of phonon-backend-xine
Installing libxine1-misc-plugins as dep of libxine1
Installing libxine1-bin as dep of libxine1-misc-plugins
Installing libxine1-x as dep of libxine1
Installing libxcb-shape0 as dep of libxine1-x
Installing libxcb-shm0 as dep of libxine1-x
Installing libxcb-xv0 as dep of libxine1-x
Installing libxine1-console as dep of libxine1
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
Installing kdepimlibs-data as dep of kdepimlibs5
Installing phonon as dep of python-kde4
Installing install-package as dep of software-properties-kde
Installing gdebi-kde as dep of install-package
Installing kdesudo as dep of gdebi-kde
Installing packagekit as dep of kpackagekit
Installing libpackagekit-glib2-12 as dep of packagekit
Installing packagekit-backend-apt as dep of packagekit
Installing python-packagekit as dep of packagekit-backend-apt
Installing update-manager-kde as dep of kpackagekit
Installing libk3b6 as dep of k3b
Installing libkcddb4 as dep of libk3b6
Installing bluetooth as dep of bluez-utils
new important dependency: cvs
Installing cvs as dep of gettext
Installing libxcursor1 as dep of libxcursor-dev
Installing python-speechd as dep of gnome-orca
Installing python-louis as dep of gnome-orca
Installing liblouis0 as dep of python-louis
Installing liblouis-data as dep of liblouis0
Installing libfaac0 as dep of libfaac-dev
Installing at-spi as dep of python-pyatspi
Installing xserver-xorg-input-synaptics as dep of xserver-xorg-input-all
Installing diffutils as dep of diff
Installing libass4 as dep of vlc-nox
Installing libavformat52 as dep of vlc-nox
Installing libcddb2 as dep of vlc-nox
Installing libdvbpsi5 as dep of vlc-nox
Installing libpostproc51 as dep of vlc-nox
Installing libvlc2 as dep of vlc-nox
Installing libvlccore2 as dep of libvlc2
Installing vlc-data as dep of libvlccore2
Installing odbcinst as dep of odbcinst1debian1
Installing linux-generic-pae as dep of linux-server
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing texlive-pictures as dep of texlive-latex-extra
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
Installing nautilus-dbg as dep of gnome-dbg
Installing libpango1.0-0-dbg as dep of gnome-dbg
Installing librsvg2-dbg as dep of gnome-dbg
Installing totem-dbg as dep of gnome-dbg
Installing evolution-data-server-dbg as dep of gnome-dbg
Installing evolution-dbg as dep of gnome-dbg
Installing python-gtk2-dbg as dep of gnome-dbg
Installing python-dbg as dep of python-gtk2-dbg
Installing python2.6-dbg as dep of python-dbg
Installing python-numpy-dbg as dep of python-gtk2-dbg
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
Installing libvala0 as dep of anjuta
Installing anjuta-common as dep of anjuta
Installing exuberant-ctags as dep of anjuta
Installing autogen as dep of anjuta
Installing libopts25 as dep of autogen
Installing libopts25-dev as dep of autogen
Installing intltool as dep of anjuta
Installing evince-dbg as dep of gnome-dbg
Installing evince as dep of evince-dbg
Installing libdjvulibre21 as dep of evince
Installing libdjvulibre-text as dep of libdjvulibre21
Installing libevdocument2 as dep of evince
Installing libevview2 as dep of evince
Installing libspectre1 as dep of evince
Installing epiphany-browser-dbg as dep of gnome-dbg
Installing epiphany-browser as dep of epiphany-browser-dbg
Installing epiphany-browser-data as dep of epiphany-browser
Installing libwebkit-1.0-2-dbg as dep of epiphany-browser-dbg
Installing eog-dbg as dep of gnome-dbg
Installing libgdl-1-dbg as dep of gnome-dbg
Installing libgda3-3-dbg as dep of gnome-dbg
Installing libgda3-3 as dep of libgda3-3-dbg
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
Installing samba as dep of swat
Installing mysql-server-5.1 as dep of mysql-server
Installing mysql-client-5.1 as dep of mysql-server-5.1
Installing mysql-server-core-5.1 as dep of mysql-server-5.1
Installing libhtml-template-perl as dep of mysql-server-5.1
Installing libpango-perl as dep of libgtk2-perl
Installing libjpeg62 as dep of libjpeg62-dev
Installing libmono-posix1.0-cil as dep of libmono1.0-cil
Installing liblame0 as dep of liblame-dev
Installing python-smbc as dep of system-config-printer-common
new important dependency: avahi-utils
Installing avahi-utils as dep of system-config-printer-common
Installing libxdamage1 as dep of libxdamage-dev
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
Installing sensible-utils as dep of debianutils
Installing libmagic1 as dep of file
Installing libtiff4 as dep of libtiff4-dev
Installing libtiffxx0c2 as dep of libtiff4-dev
Installing libfreetype6 as dep of libfreetype6-dev
Installing apturl-common as dep of apturl
Installing libode1sp as dep of python-soya
Installing libnetpbm10 as dep of netpbm
Installing wine1.2 as dep of wine
Installing libmpg123-0 as dep of wine1.2
Installing ttf-symbol-replacement as dep of wine1.2
Installing ttf-umefont as dep of wine1.2
Installing ttf-droid as dep of wine1.2
Installing ttf-mscorefonts-installer as dep of wine1.2
Installing cabextract as dep of ttf-mscorefonts-installer
Installing wine1.2-gecko as dep of wine1.2
Installing libnspr4 as dep of libebook1.2-5
Installing libpthread-stubs0 as dep of libpthread-stubs0-dev
Installing libpst4 as dep of evolution-plugins
Installing libyaml-syck-perl as dep of libdate-manip-perl
Installing khelpcenter4 as dep of khelpcenter
Installing librpm0 as dep of rpm
Installing librpmio0 as dep of librpm0
Installing rpm-common as dep of librpm0
Installing librpmbuild0 as dep of rpm
Installing rpm2cpio as dep of rpm
Installing landscape-common as dep of landscape-client
Installing python-smartpm as dep of landscape-common
new important dependency: libmono-i18n-west2.0-cil
Installing libmono-i18n-west2.0-cil as dep of libmono-corlib2.0-cil
Installing libsox1a as dep of sox
Installing libsox-fmt-base as dep of libsox1a
Installing libsox-fmt-alsa as dep of libsox1a
new important dependency: xinput
Installing xinput as dep of acpi-support
Installing vim-runtime as dep of vim
Installing libxcb-keysyms1 as dep of vlc
Installing libxml2-doc as dep of gstreamer0.10-doc
Installing libglib2.0-doc as dep of gstreamer0.10-doc
Installing liba52-0.7.4 as dep of liba52-0.7.4-dev
Installing libc-client2007e as dep of php5-imap
Installing libmikmod2 as dep of libsdl-mixer1.2
Installing libgksu2-0 as dep of gksu
Installing libc-dev-bin as dep of libc6-dev
Installing manpages-dev as dep of libc-dev-bin
new important dependency: xserver-xorg-video-cyrix
Installing xserver-xorg-video-cyrix as dep of xserver-xorg-video-geode
new important dependency: pidgin-libnotify
Installing pidgin-libnotify as dep of pidgin
Installing xorg-docs-core as dep of xorg
new important dependency: lockfile-progs
Installing lockfile-progs as dep of ntpdate
Installing libservlet2.5-java as dep of libhsqldb-java
new important dependency: timidity-daemon
Installing timidity-daemon as dep of timidity
new important dependency: libmagickcore2-extra
Installing libmagickcore2-extra as dep of imagemagick
Installing libgraphviz4 as dep of libmagickcore2-extra
Installing gconf-defaults-service as dep of gconf-editor
Installing grub-common as dep of grub
Installing os-prober as dep of grub-common
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
Installing libiso9660-7 as dep of libvcdinfo0
new important dependency: python-dnspython
Installing python-dnspython as dep of python-xmpp
Installing discover as dep of discover1
Installing libdiscover2 as dep of discover
Installing discover-data as dep of libdiscover2
new important dependency: python-reportlab-accel
Installing python-reportlab-accel as dep of python-reportlab
Installing libntfs-3g75 as dep of ntfs-3g
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing python-gnome2-extras as dep of serpentine
Installing libevent-1.4-2 as dep of transmission-gtk
Starting
Starting 2
Investigating libc6
Package libc6 has broken dep on belocs-locales-bin
  Considering belocs-locales-bin -2 as a solution to libc6 15001
  Added belocs-locales-bin to the remove list
  Fixing libc6 via remove of belocs-locales-bin
Investigating dpkg
Package dpkg has broken dep on emacs21
  Considering emacs21 -1 as a solution to dpkg 6141
  Added emacs21 to the remove list
  Fixing dpkg via remove of emacs21
Investigating libxcb1
Package libxcb1 has broken dep on libxcb-xlib0
  Considering libxcb-xlib0 1 as a solution to libxcb1 539
  Added libxcb-xlib0 to the remove list
  Fixing libxcb1 via remove of libxcb-xlib0
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 9 as a solution to libcups2 374
  Added libcupsys2 to the remove list
  Fixing libcups2 via remove of libcupsys2
Investigating libthai0
Package libthai0 has broken dep on libdatrie0
  Considering libdatrie0 -1 as a solution to libthai0 247
  Added libdatrie0 to the remove list
  Fixing libthai0 via remove of libdatrie0
Investigating mono-runtime
Package mono-runtime has broken dep on mono-common
  Considering mono-common 1 as a solution to mono-runtime 188
  Added mono-common to the remove list
Package mono-runtime has broken dep on mono-jit
  Considering mono-jit -1 as a solution to mono-runtime 188
  Added mono-jit to the remove list
  Fixing mono-runtime via remove of mono-common
  Fixing mono-runtime via remove of mono-jit
Investigating perl-modules
Package perl-modules has broken dep on libversion-perl
  Considering libversion-perl 1 as a solution to perl-modules 166
  Added libversion-perl to the remove list
  Fixing perl-modules via remove of libversion-perl
Investigating libnspr4-0d
Package libnspr4-0d has broken dep on libnspr4
  Considering libnspr4 6 as a solution to libnspr4-0d 150
  Added libnspr4 to the remove list
  Fixing libnspr4-0d via remove of libnspr4
Investigating texlive-common
Package texlive-common has broken dep on texlive-base-bin
  Considering texlive-base-bin -1 as a solution to texlive-common 112
  Added texlive-base-bin to the remove list
  Fixing texlive-common via remove of texlive-base-bin
Investigating xserver-xorg-core
Package xserver-xorg-core has broken dep on xserver-xorg-input-2
  Considering xserver-xorg-input-kbd -1 as a solution to xserver-xorg-core 98
  Added xserver-xorg-input-kbd to the remove list
  Considering xserver-xorg-input-mouse 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-input-elographics 0 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-input-synaptics 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-input-evdev 6 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-input-wacom 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-input-vmmouse 2 as a solution to xserver-xorg-core 98
Package xserver-xorg-core has broken dep on xserver-xorg-video-2
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-siliconmotion 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-i740 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-geode 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-via 0 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-nv 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-i810 -1 as a solution to xserver-xorg-core 98
  Added xserver-xorg-video-i810 to the remove list
  Considering xserver-xorg-video-intel 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-chips 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-tga -1 as a solution to xserver-xorg-core 98
  Added xserver-xorg-video-tga to the remove list
  Considering xserver-xorg-video-trident 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-s3 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-vga -1 as a solution to xserver-xorg-core 98
  Added xserver-xorg-video-vga to the remove list
  Considering xserver-xorg-video-i128 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-mga 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-nsc -1 as a solution to xserver-xorg-core 98
  Added xserver-xorg-video-nsc to the remove list
  Considering xserver-xorg-video-newport -1 as a solution to xserver-xorg-core 98
  Added xserver-xorg-video-newport to the remove list
  Considering xserver-xorg-video-neomagic 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-cirrus 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-ark 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-tdfx 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-sisusb 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-dummy 0 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-rendition 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-vesa 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-cyrix -1 as a solution to xserver-xorg-core 98
  Added xserver-xorg-video-cyrix to the remove list
  Considering xserver-xorg-video-imstt -1 as a solution to xserver-xorg-core 98
  Added xserver-xorg-video-imstt to the remove list
  Considering xserver-xorg-video-glint 0 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-fbdev 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-savage 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-radeon 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-vmware 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-openchrome 3 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-s3virge 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-voodoo 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-apm 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-sis 2 as a solution to xserver-xorg-core 98
  Considering xserver-xorg-video-v4l 2 as a solution to xserver-xorg-core 98
  Fixing xserver-xorg-core via remove of xserver-xorg-input-kbd
  Fixing xserver-xorg-core via remove of xserver-xorg-video-i810
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tga
  Fixing xserver-xorg-core via remove of xserver-xorg-video-vga
  Fixing xserver-xorg-core via remove of xserver-xorg-video-nsc
  Fixing xserver-xorg-core via remove of xserver-xorg-video-newport
  Fixing xserver-xorg-core via remove of xserver-xorg-video-cyrix
  Fixing xserver-xorg-core via remove of xserver-xorg-video-imstt
Investigating libnss3-1d
Package libnss3-1d has broken dep on libnss3
  Considering libnss3 0 as a solution to libnss3-1d 92
  Added libnss3 to the remove list
  Fixing libnss3-1d via remove of libnss3
Investigating upstart
Package upstart has broken dep on startup-tasks
  Considering startup-tasks 2 as a solution to upstart 61
  Added startup-tasks to the remove list
Package upstart has broken dep on system-services
  Considering system-services 2 as a solution to upstart 61
  Added system-services to the remove list
Package upstart has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 5 as a solution to upstart 61
  Added upstart-compat-sysv to the remove list
  Fixing upstart via remove of startup-tasks
  Fixing upstart via remove of system-services
  Fixing upstart via remove of upstart-compat-sysv
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
  Considering cupsddk-drivers -1 as a solution to cups 22
  Added cupsddk-drivers to the remove list
  Fixing cups via remove of cupsddk-drivers
Investigating libnautilus-extension1
Package libnautilus-extension1 has broken dep on gnome-mount
  Considering gnome-mount 1 as a solution to libnautilus-extension1 22
  Added gnome-mount to the remove list
  Fixing libnautilus-extension1 via remove of gnome-mount
Investigating libsdl1.2debian-alsa
Package libsdl1.2debian-alsa has broken dep on libsdl1.2debian-pulseaudio
  Considering libsdl1.2debian-pulseaudio 19 as a solution to libsdl1.2debian-alsa 19
  Removing libsdl1.2debian-alsa rather than change libsdl1.2debian-pulseaudio
Investigating kdebase-runtime
Package kdebase-runtime has broken dep on kdebase-bin-kde3
  Considering kdebase-bin-kde3 -1 as a solution to kdebase-runtime 17
  Added kdebase-bin-kde3 to the remove list
  Fixing kdebase-runtime via remove of kdebase-bin-kde3
Investigating gnome-games-common
Package gnome-games-common has broken dep on gnome-cards-data
  Considering gnome-cards-data 3 as a solution to gnome-games-common 17
  Added gnome-cards-data to the remove list
  Fixing gnome-games-common via remove of gnome-cards-data
Investigating libstlport4.6ldbl
Package libstlport4.6ldbl has broken dep on libstlport4.6c2
  Considering libstlport4.6c2 -1 as a solution to libstlport4.6ldbl 16
  Added libstlport4.6c2 to the remove list
  Fixing libstlport4.6ldbl via remove of libstlport4.6c2
Investigating plymouth
Package plymouth has broken dep on usplash
  Considering usplash 1 as a solution to plymouth 14
  Added usplash to the remove list
  Considering usplash 1 as a solution to plymouth 14
  Fixing plymouth via remove of usplash
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-modules
  Considering libsasl2-modules 15 as a solution to libsasl2 12
Package libsasl2 has broken dep on libsasl2-modules-sql
Package libsasl2 has broken dep on libsasl2-modules-gssapi-heimdal
Package libsasl2 has broken dep on libsasl2-modules-kerberos-heimdal
  Or group remove for libsasl2
Investigating python-zope.interface
Package python-zope.interface has broken dep on python-zopeinterface
  Considering python-zopeinterface 0 as a solution to python-zope.interface 9
  Added python-zopeinterface to the remove list
  Fixing python-zope.interface via remove of python-zopeinterface
Investigating x11-apps
Package x11-apps has broken dep on bitmap
  Considering bitmap -1 as a solution to x11-apps 8
  Added bitmap to the remove list
Package x11-apps has broken dep on ico
  Considering ico -1 as a solution to x11-apps 8
  Added ico to the remove list
Package x11-apps has broken dep on xgc
  Considering xgc -1 as a solution to x11-apps 8
  Added xgc to the remove list
  Fixing x11-apps via remove of bitmap
  Fixing x11-apps via remove of ico
  Fixing x11-apps via remove of xgc
Investigating nautilus
Package nautilus has broken dep on gnome-volume-manager
  Considering gnome-volume-manager -1 as a solution to nautilus 8
  Added gnome-volume-manager to the remove list
  Fixing nautilus via remove of gnome-volume-manager
Investigating libedataserver1.2-7
Package libedataserver1.2-7 has broken dep on libnspr4
  Considering libnspr4 6 as a solution to libedataserver1.2-7 8
  Added libnspr4 to the remove list
  Fixing libedataserver1.2-7 via keep of libnspr4
Investigating rsyslog
Package rsyslog has broken dep on linux-kernel-log-daemon
  Considering klogd 0 as a solution to rsyslog 8
  Considering syslog-ng 0 as a solution to rsyslog 8
  Considering syslog-ng 0 as a solution to rsyslog 8
  Considering socklog-run 0 as a solution to rsyslog 8
  Considering klogd 0 as a solution to rsyslog 8
  Added klogd to the remove list
  Considering inetutils-syslogd 0 as a solution to rsyslog 8
  Considering dsyslog 0 as a solution to rsyslog 8
Package rsyslog has broken dep on system-log-daemon
  Considering sysklogd 0 as a solution to rsyslog 8
  Considering syslog-ng 0 as a solution to rsyslog 8
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
Investigating libldap2
Package libldap2 has broken dep on libsasl2
  Considering libsasl2 12 as a solution to libldap2 8
  Removing libldap2 rather than change libsasl2
Investigating gimp
Package gimp has broken dep on gimp-gnomevfs
  Considering gimp-gnomevfs -1 as a solution to gimp 7
  Added gimp-gnomevfs to the remove list
  Fixing gimp via remove of gimp-gnomevfs
Investigating foomatic-db
Package foomatic-db has broken dep on foomatic-db-hpijs
  Considering foomatic-db-hpijs -1 as a solution to foomatic-db 7
  Added foomatic-db-hpijs to the remove list
  Fixing foomatic-db via remove of foomatic-db-hpijs
Investigating libmetacity-private0
Package libmetacity-private0 has broken dep on libmetacity0
  Considering libmetacity0 -1 as a solution to libmetacity-private0 6
  Added libmetacity0 to the remove list
  Fixing libmetacity-private0 via remove of libmetacity0
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet -1 as a solution to gdm 5
  Added fast-user-switch-applet to the remove list
  Fixing gdm via remove of fast-user-switch-applet
Investigating libpt-1.10.0
Package libpt-1.10.0 has broken dep on libldap2
  Considering libldap2 8 as a solution to libpt-1.10.0 5
  Removing libpt-1.10.0 rather than change libldap2
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken dep on libchromexvmc1
  Considering libchromexvmc1 -1 as a solution to xserver-xorg-video-openchrome 3
  Added libchromexvmc1 to the remove list
Package xserver-xorg-video-openchrome has broken dep on libchromexvmcpro1
  Considering libchromexvmcpro1 -1 as a solution to xserver-xorg-video-openchrome 3
  Added libchromexvmcpro1 to the remove list
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmc1
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmcpro1
Investigating libmp3lame0
Package libmp3lame0 has broken dep on liblame0
  Considering liblame0 2 as a solution to libmp3lame0 3
  Added liblame0 to the remove list
  Fixing libmp3lame0 via remove of liblame0
Investigating libsox1a
Package libsox1a has broken dep on libsox0
  Considering libsox0 -1 as a solution to libsox1a 3
  Added libsox0 to the remove list
  Fixing libsox1a via remove of libsox0
Investigating ttf-sil-gentium
Package ttf-sil-gentium has broken dep on ttf-gentium
  Considering ttf-gentium -1 as a solution to ttf-sil-gentium 2
  Added ttf-gentium to the remove list
  Fixing ttf-sil-gentium via remove of ttf-gentium
Investigating libpt-1.10.10-plugins-alsa
Package libpt-1.10.10-plugins-alsa has broken dep on libpt-plugins-alsa
  Considering libpt-plugins-alsa -1 as a solution to libpt-1.10.10-plugins-alsa 2
  Added libpt-plugins-alsa to the remove list
  Fixing libpt-1.10.10-plugins-alsa via remove of libpt-plugins-alsa
Investigating mysql-client-5.1
Package mysql-client-5.1 has broken dep on mysql-client-5.0
  Considering mysql-client-5.0 1 as a solution to mysql-client-5.1 2
  Added mysql-client-5.0 to the remove list
  Fixing mysql-client-5.1 via remove of mysql-client-5.0
Investigating python-gd
Package python-gd has broken dep on python2.4-gd
  Considering python2.4-gd -2 as a solution to python-gd 2
  Added python2.4-gd to the remove list
  Fixing python-gd via remove of python2.4-gd
Investigating libupnp3
Package libupnp3 has broken dep on libupnp2
  Considering libupnp2 -2 as a solution to libupnp3 2
  Added libupnp2 to the remove list
  Fixing libupnp3 via remove of libupnp2
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 61 as a solution to upstart-logd 2
  Removing upstart-logd rather than change upstart
Investigating libcrack2
Package libcrack2 has broken dep on cracklib2
  Considering cracklib2 -1 as a solution to libcrack2 2
  Added cracklib2 to the remove list
  Fixing libcrack2 via remove of cracklib2
Investigating libgtkhtml-editor-common
Package libgtkhtml-editor-common has broken dep on gtkhtml3.14
  Considering gtkhtml3.14 -1 as a solution to libgtkhtml-editor-common 2
  Added gtkhtml3.14 to the remove list
  Fixing libgtkhtml-editor-common via remove of gtkhtml3.14
Investigating libpt-1.10.10-plugins-v4l
Package libpt-1.10.10-plugins-v4l has broken dep on libpt-plugins-v4l
  Considering libpt-plugins-v4l -1 as a solution to libpt-1.10.10-plugins-v4l 2
  Added libpt-plugins-v4l to the remove list
  Fixing libpt-1.10.10-plugins-v4l via remove of libpt-plugins-v4l
Investigating libpt-1.10.10-plugins-v4l2
Package libpt-1.10.10-plugins-v4l2 has broken dep on libpt-plugins-v4l2
  Considering libpt-plugins-v4l2 -1 as a solution to libpt-1.10.10-plugins-v4l2 2
  Added libpt-plugins-v4l2 to the remove list
  Fixing libpt-1.10.10-plugins-v4l2 via remove of libpt-plugins-v4l2
Investigating libgsl0ldbl
Package libgsl0ldbl has broken dep on libgsl0
  Considering libgsl0 -1 as a solution to libgsl0ldbl 2
  Added libgsl0 to the remove list
  Fixing libgsl0ldbl via remove of libgsl0
Investigating libgnomekbd2
Package libgnomekbd2 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 4 as a solution to libgnomekbd2 1
  Removing libgnomekbd2 rather than change libgnomekbd-common
Investigating envyng-core
Package envyng-core has broken dep on python
  Considering python 1526 as a solution to envyng-core 1
  Removing envyng-core rather than change python
Investigating guidance-backends
Package guidance-backends has broken dep on python
  Considering python 1526 as a solution to guidance-backends 1
  Removing guidance-backends rather than change python
Investigating python-gnome2-extras
Package python-gnome2-extras has broken dep on python
  Considering python 1526 as a solution to python-gnome2-extras 1
  Removing python-gnome2-extras rather than change python
Investigating gnome-bluetooth
Package gnome-bluetooth has broken dep on bluez-gnome
  Considering bluez-gnome -1 as a solution to gnome-bluetooth 1
  Added bluez-gnome to the remove list
  Fixing gnome-bluetooth via remove of bluez-gnome
Investigating kicker
Package kicker has broken dep on kdebase-data
  Considering kdebase-data 7 as a solution to kicker 1
  Removing kicker rather than change kdebase-data
Investigating libavcodec1d
Package libavcodec1d has broken dep on liblame0
  Considering liblame0 2 as a solution to libavcodec1d 1
  Removing libavcodec1d rather than change liblame0
Investigating libgdl-1-0
Package libgdl-1-0 has broken dep on libgdl-1-common
  Considering libgdl-1-common 5 as a solution to libgdl-1-0 1
  Removing libgdl-1-0 rather than change libgdl-1-common
Investigating libcamel1.2-8
Package libcamel1.2-8 has broken dep on libnss3
  Considering libnss3 0 as a solution to libcamel1.2-8 0
  Removing libcamel1.2-8 rather than change libnss3
Investigating aisleriot
Package aisleriot has broken dep on gnome-games-data
  Considering gnome-games-data -1 as a solution to aisleriot 0
  Added gnome-games-data to the remove list
  Fixing aisleriot via remove of gnome-games-data
Investigating libdiscover2
Package libdiscover2 has broken dep on libdiscover1
  Considering libdiscover1 -1 as a solution to libdiscover2 0
  Added libdiscover1 to the remove list
  Fixing libdiscover2 via remove of libdiscover1
Investigating mysql-server-5.1
Package mysql-server-5.1 has broken dep on mysql-server-5.0
  Considering mysql-server-5.0 -1 as a solution to mysql-server-5.1 0
  Added mysql-server-5.0 to the remove list
  Fixing mysql-server-5.1 via remove of mysql-server-5.0
Investigating libgdl-gnome-1-0
Package libgdl-gnome-1-0 has broken dep on libgdl-1-0
  Considering libgdl-1-0 1 as a solution to libgdl-gnome-1-0 0
  Removing libgdl-gnome-1-0 rather than change libgdl-1-0
Investigating usplash-theme-ubuntu
Package usplash-theme-ubuntu has broken dep on usplash
  Considering usplash 1 as a solution to usplash-theme-ubuntu 0
  Removing usplash-theme-ubuntu rather than change usplash
Investigating python-ogg
Package python-ogg has broken dep on python-pyogg
  Considering python-pyogg -1 as a solution to python-ogg 0
  Added python-pyogg to the remove list
  Fixing python-ogg via remove of python-pyogg
Investigating human-theme
Package human-theme has broken dep on gtk2-engines-ubuntulooks
  Considering gtk2-engines-ubuntulooks -1 as a solution to human-theme 0
  Added gtk2-engines-ubuntulooks to the remove list
  Fixing human-theme via remove of gtk2-engines-ubuntulooks
Investigating kdebase-bin
Package kdebase-bin has broken dep on kcontrol
  Considering kcontrol -1 as a solution to kdebase-bin 0
  Added kcontrol to the remove list
  Fixing kdebase-bin via remove of kcontrol
Investigating brasero
Package brasero has broken dep on nautilus-cd-burner
  Considering nautilus-cd-burner 0 as a solution to brasero 0
  Holding Back brasero rather than change nautilus-cd-burner
Investigating libgnomecupsui1.0-1c2a
Package libgnomecupsui1.0-1c2a has broken dep on libcupsys2
  Considering libcupsys2 9 as a solution to libgnomecupsui1.0-1c2a -1
  Removing libgnomecupsui1.0-1c2a rather than change libcupsys2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5409 as a solution to libperl5.8 -1
  Removing libperl5.8 rather than change perl-base
Investigating libxvidcore4-dev
Package libxvidcore4-dev has broken dep on libxvidcore4
  Considering libxvidcore4 6 as a solution to libxvidcore4-dev -1
  Removing libxvidcore4-dev rather than change libxvidcore4
Investigating libexchange-storage1.2-1
Package libexchange-storage1.2-1 has broken dep on libldap2
  Considering libldap2 8 as a solution to libexchange-storage1.2-1 -1
  Removing libexchange-storage1.2-1 rather than change libldap2
Investigating pm-utils-powersave-policy
Package pm-utils-powersave-policy has broken dep on laptop-mode-tools
  Considering laptop-mode-tools 0 as a solution to pm-utils-powersave-policy -1
  Holding Back pm-utils-powersave-policy rather than change laptop-mode-tools
Investigating libavformat1d
Package libavformat1d has broken dep on libavcodec1d
  Considering libavcodec1d 1 as a solution to libavformat1d -1
  Removing libavformat1d rather than change libavcodec1d
Investigating python-gtkhtml2
Package python-gtkhtml2 has broken dep on python
  Considering python 1526 as a solution to python-gtkhtml2 -1
  Removing python-gtkhtml2 rather than change python
Investigating python2.4-unit
Package python2.4-unit has broken dep on python2.4-tk
  Considering python-tk 4 as a solution to python2.4-unit -1
  Removing python2.4-unit rather than change python2.4-tk
Investigating librpm4.4
Package librpm4.4 has broken dep on librpm0
  Considering librpm0 4 as a solution to librpm4.4 -1
  Removing librpm4.4 rather than change librpm0
Investigating libgnomekbdui2
Package libgnomekbdui2 has broken dep on libgnomekbd2
  Considering libgnomekbd2 1 as a solution to libgnomekbdui2 -1
  Removing libgnomekbdui2 rather than change libgnomekbd2
Investigating python-xml
Package python-xml has broken dep on python
  Considering python 1526 as a solution to python-xml -1
  Removing python-xml rather than change python
Investigating liblame-dev
Package liblame-dev has broken dep on liblame0
  Considering liblame0 2 as a solution to liblame-dev -1
  Removing liblame-dev rather than change liblame0
Investigating displayconfig-gtk
Package displayconfig-gtk has broken dep on guidance-backends
  Considering guidance-backends 1 as a solution to displayconfig-gtk -1
  Removing displayconfig-gtk rather than change guidance-backends
Investigating libxcb-xlib0-dev
Package libxcb-xlib0-dev has broken dep on libxcb-xlib0
  Considering libxcb-xlib0 1 as a solution to libxcb-xlib0-dev -1
  Removing libxcb-xlib0-dev rather than change libxcb-xlib0
Investigating envyng-gtk
Package envyng-gtk has broken dep on envyng-core
  Considering envyng-core 1 as a solution to envyng-gtk -1
  Removing envyng-gtk rather than change envyng-core
Investigating libltdl-dev
Package libltdl-dev has broken dep on libltdl3-dev
  Considering libltdl3-dev 0 as a solution to libltdl-dev -1
  Holding Back libltdl-dev rather than change libltdl3-dev
Investigating libcupsys2-dev
Package libcupsys2-dev has broken dep on libcupsys2
  Considering libcupsys2 9 as a solution to libcupsys2-dev -1
  Removing libcupsys2-dev rather than change libcupsys2
Investigating libcupsys2-gnutls10
Package libcupsys2-gnutls10 has broken dep on libcupsys2
  Considering libcupsys2 9 as a solution to libcupsys2-gnutls10 -1
  Removing libcupsys2-gnutls10 rather than change libcupsys2
Investigating serpentine
Package serpentine has broken dep on python-gnome2-extras
  Considering python-gnome2-extras 1 as a solution to serpentine -1
  Removing serpentine rather than change python-gnome2-extras
Investigating netatalk
Package netatalk has broken dep on libcupsys2
  Considering libcupsys2 9 as a solution to netatalk 9999
  Added libcupsys2 to the remove list
  Fixing netatalk via keep of libcupsys2
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 9 as a solution to libcups2 374
  Added libcupsys2 to the remove list
  Fixing libcups2 via remove of libcupsys2
Investigating libnspr4-0d
Package libnspr4-0d has broken dep on libnspr4
  Considering libnspr4 6 as a solution to libnspr4-0d 150
  Added libnspr4 to the remove list
  Fixing libnspr4-0d via remove of libnspr4
Investigating libedataserver1.2-7
Package libedataserver1.2-7 has broken dep on libnspr4
  Considering libnspr4 6 as a solution to libedataserver1.2-7 8
  Added libnspr4 to the remove list
  Fixing libedataserver1.2-7 via keep of libnspr4
Investigating brasero-common
Package brasero-common has broken dep on brasero
  Considering brasero 0 as a solution to brasero-common 7
  Added brasero to the remove list
  Fixing brasero-common via remove of brasero
Investigating libebook1.2-5
Package libebook1.2-5 has broken dep on libcamel1.2-8
  Considering libcamel1.2-8 0 as a solution to libebook1.2-5 1
  Added libcamel1.2-8 to the remove list
  Fixing libebook1.2-5 via keep of libcamel1.2-8
Investigating libcamel1.2-8
Package libcamel1.2-8 has broken dep on libnss3
  Considering libnss3 0 as a solution to libcamel1.2-8 0
  Removing libcamel1.2-8 rather than change libnss3
Investigating netatalk
Package netatalk has broken dep on libcupsys2
  Considering libcupsys2 9 as a solution to netatalk 9999
  Added libcupsys2 to the remove list
  Fixing netatalk via keep of libcupsys2
Investigating libcups2
Package libcups2 has broken dep on libcupsys2
  Considering libcupsys2 9999 as a solution to libcups2 374
  Holding Back libcups2 rather than change libcupsys2
Investigating libnspr4-0d
Package libnspr4-0d has broken dep on libnspr4
  Considering libnspr4 6 as a solution to libnspr4-0d 150
  Added libnspr4 to the remove list
  Fixing libnspr4-0d via remove of libnspr4
Investigating libcupsimage2
Package libcupsimage2 has broken dep on libcups2
  Considering libcups2 374 as a solution to libcupsimage2 38
  Holding Back libcupsimage2 rather than change libcups2
Investigating cups-client
Package cups-client has broken dep on libcups2
  Considering libcups2 374 as a solution to cups-client 36
  Holding Back cups-client rather than change libcups2
Investigating cups
Package cups has broken dep on libcups2
  Considering libcups2 374 as a solution to cups 22
  Holding Back cups rather than change libcups2
Investigating openjdk-6-jre-headless
Package openjdk-6-jre-headless has broken dep on libcups2
  Considering libcups2 374 as a solution to openjdk-6-jre-headless 18
  Holding Back openjdk-6-jre-headless rather than change libcups2
Investigating libcupsppdc1
Package libcupsppdc1 has broken dep on libcups2
  Considering libcups2 374 as a solution to libcupsppdc1 14
  Holding Back libcupsppdc1 rather than change libcups2
Investigating libcupscgi1
Package libcupscgi1 has broken dep on libcups2
  Considering libcups2 374 as a solution to libcupscgi1 13
  Holding Back libcupscgi1 rather than change libcups2
Investigating libcupsmime1
Package libcupsmime1 has broken dep on libcups2
  Considering libcups2 374 as a solution to libcupsmime1 13
  Holding Back libcupsmime1 rather than change libcups2
Investigating libcupsdriver1
Package libcupsdriver1 has broken dep on libcups2
  Considering libcups2 374 as a solution to libcupsdriver1 13
  Holding Back libcupsdriver1 rather than change libcups2
Investigating libgs8
Package libgs8 has broken dep on libcups2
  Considering libcups2 374 as a solution to libgs8 12
  Holding Back libgs8 rather than change libcups2
Investigating libgnomeprint2.2-0
Package libgnomeprint2.2-0 has broken dep on libcups2
  Considering libcups2 374 as a solution to libgnomeprint2.2-0 12
  Removing libgnomeprint2.2-0 rather than change libcups2
Investigating libgnomecups1.0-1
Package libgnomecups1.0-1 has broken dep on libcups2
  Considering libcups2 374 as a solution to libgnomecups1.0-1 9
  Holding Back libgnomecups1.0-1 rather than change libcups2
Investigating kdelibs4c2a
Package kdelibs4c2a has broken dep on libcups2
  Considering libcups2 374 as a solution to kdelibs4c2a 8
  Holding Back kdelibs4c2a rather than change libcups2
Investigating libedataserver1.2-7
Package libedataserver1.2-7 has broken dep on libnspr4
  Considering libnspr4 150 as a solution to libedataserver1.2-7 8
  Removing libedataserver1.2-7 rather than change libnspr4
Investigating foomatic-db
Package foomatic-db has broken dep on cups
  Considering cups 22 as a solution to foomatic-db 7
  Holding Back foomatic-db rather than change cups
Investigating foomatic-db-engine
Package foomatic-db-engine has broken dep on cups
  Considering cups 22 as a solution to foomatic-db-engine 6
  Holding Back foomatic-db-engine rather than change cups
Investigating libgnomeprintui2.2-0
Package libgnomeprintui2.2-0 has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 374 as a solution to libgnomeprintui2.2-0 6
  Removing libgnomeprintui2.2-0 rather than change libgnomeprint2.2-0
Investigating python-gnomeprint
Package python-gnomeprint has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 374 as a solution to python-gnomeprint 5
  Holding Back python-gnomeprint rather than change libgnomeprint2.2-0
Investigating openjdk-6-jre-lib
Package openjdk-6-jre-lib has broken dep on openjdk-6-jre-headless
  Considering openjdk-6-jre-headless 18 as a solution to openjdk-6-jre-lib 3
  Holding Back openjdk-6-jre-lib rather than change openjdk-6-jre-headless
Investigating python-cups
Package python-cups has broken dep on libcups2
  Considering libcups2 374 as a solution to python-cups 3
  Removing python-cups rather than change libcups2
Investigating system-config-printer-common
Package system-config-printer-common has broken dep on python-cups
  Considering python-cups 374 as a solution to system-config-printer-common 2
  Removing system-config-printer-common rather than change python-cups
Investigating libgtkhtml3.8-15
Package libgtkhtml3.8-15 has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 374 as a solution to libgtkhtml3.8-15 1
  Removing libgtkhtml3.8-15 rather than change libgnomeprint2.2-0
Investigating system-config-printer-gnome
Package system-config-printer-gnome has broken dep on system-config-printer-common
  Considering system-config-printer-common 374 as a solution to system-config-printer-gnome 1
  Removing system-config-printer-gnome rather than change system-config-printer-common
Investigating cups-ppdc
Package cups-ppdc has broken dep on libcups2
  Considering libcups2 374 as a solution to cups-ppdc 1
  Holding Back cups-ppdc rather than change libcups2
Investigating libecal1.2-3
Package libecal1.2-3 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 150 as a solution to libecal1.2-3 1
  Removing libecal1.2-3 rather than change libedataserver1.2-7
Investigating samba
Package samba has broken dep on libcups2
  Considering libcups2 374 as a solution to samba 1
  Removing samba rather than change libcups2
Investigating libebook1.2-5
Package libebook1.2-5 has broken dep on libcamel1.2-8
  Considering libcamel1.2-8 0 as a solution to libebook1.2-5 1
  Added libcamel1.2-8 to the remove list
Package libebook1.2-5 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 150 as a solution to libebook1.2-5 1
  Removing libebook1.2-5 rather than change libedataserver1.2-7
Investigating openprinting-ppds
Package openprinting-ppds has broken dep on cups
  Considering cups 22 as a solution to openprinting-ppds 1
  Holding Back openprinting-ppds rather than change cups
Investigating cups-bsd
Package cups-bsd has broken dep on libcups2
  Considering libcups2 374 as a solution to cups-bsd 1
  Holding Back cups-bsd rather than change libcups2
Investigating ghostscript-cups
Package ghostscript-cups has broken dep on libcups2
  Considering libcups2 374 as a solution to ghostscript-cups 1
  Holding Back ghostscript-cups rather than change libcups2
Investigating foomatic-db-gutenprint
Package foomatic-db-gutenprint has broken dep on cups
  Considering cups 22 as a solution to foomatic-db-gutenprint 0
  Holding Back foomatic-db-gutenprint rather than change cups
Investigating pxljr
Package pxljr has broken dep on cups
  Considering cups 22 as a solution to pxljr 0
  Holding Back pxljr rather than change cups
Investigating libgtksourceview1.0-0
Package libgtksourceview1.0-0 has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 374 as a solution to libgtksourceview1.0-0 0
  Removing libgtksourceview1.0-0 rather than change libgnomeprint2.2-0
Investigating bluez-cups
Package bluez-cups has broken dep on cups
  Considering cups 22 as a solution to bluez-cups 0
  Holding Back bluez-cups rather than change cups
Investigating hplip
Package hplip has broken dep on libcups2
  Considering libcups2 374 as a solution to hplip 0
  Removing hplip rather than change libcups2
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on cups
  Considering cups 22 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change cups
Investigating system-config-printer-udev
Package system-config-printer-udev has broken dep on libcups2
  Considering libcups2 374 as a solution to system-config-printer-udev 0
  Holding Back system-config-printer-udev rather than change libcups2
Investigating cups-driver-gutenprint
Package cups-driver-gutenprint has broken dep on libcups2
  Considering libcups2 374 as a solution to cups-driver-gutenprint 0
  Holding Back cups-driver-gutenprint rather than change libcups2
Investigating swat
Package swat has broken dep on samba
  Considering samba 374 as a solution to swat 0
  Removing swat rather than change samba
Investigating splix
Package splix has broken dep on libcups2
  Considering libcups2 374 as a solution to splix 0
  Holding Back splix rather than change libcups2
Investigating cupsys-driver-gutenprint
Package cupsys-driver-gutenprint has broken dep on cups-driver-gutenprint
  Considering cups-driver-gutenprint 0 as a solution to cupsys-driver-gutenprint 0
  Holding Back cupsys-driver-gutenprint rather than change cups-driver-gutenprint
Investigating foo2zjs
Package foo2zjs has broken dep on cups
  Considering cups 22 as a solution to foo2zjs 0
  Holding Back foo2zjs rather than change cups
Investigating cups-pdf
Package cups-pdf has broken dep on cups
  Considering cups 22 as a solution to cups-pdf 0
  Holding Back cups-pdf rather than change cups
Investigating cupsddk
Package cupsddk has broken dep on cups-ppdc
  Considering cups-ppdc 1 as a solution to cupsddk -1
  Removing cupsddk rather than change cups-ppdc
Investigating cupsys-bsd
Package cupsys-bsd has broken dep on cups-bsd
  Considering cups-bsd 1 as a solution to cupsys-bsd -1
  Removing cupsys-bsd rather than change cups-bsd
Investigating libedata-cal1.2-1
Package libedata-cal1.2-1 has broken dep on libecal1.2-3
  Considering libecal1.2-3 150 as a solution to libedata-cal1.2-1 -1
  Removing libedata-cal1.2-1 rather than change libecal1.2-3
Investigating libgnome2.0-cil
Package libgnome2.0-cil has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 374 as a solution to libgnome2.0-cil -1
  Removing libgnome2.0-cil rather than change libgnomeprint2.2-0
Investigating libedataserverui1.2-6
Package libedataserverui1.2-6 has broken dep on libebook1.2-5
  Considering libebook1.2-5 150 as a solution to libedataserverui1.2-6 -1
  Removing libedataserverui1.2-6 rather than change libebook1.2-5
Investigating gtkhtml3.8
Package gtkhtml3.8 has broken dep on libgnomeprint2.2-0
  Considering libgnomeprint2.2-0 374 as a solution to gtkhtml3.8 -1
  Removing gtkhtml3.8 rather than change libgnomeprint2.2-0
Investigating cupsys-client
Package cupsys-client has broken dep on cups-client
  Considering cups-client 36 as a solution to cupsys-client -1
  Holding Back cupsys-client rather than change cups-client
Investigating cupsys
Package cupsys has broken dep on cups
  Considering cups 22 as a solution to cupsys -1
  Holding Back cupsys rather than change cups
Investigating icedtea-6-jre-cacao
Package icedtea-6-jre-cacao has broken dep on openjdk-6-jre-headless
  Considering openjdk-6-jre-headless 18 as a solution to icedtea-6-jre-cacao -2
  Holding Back icedtea-6-jre-cacao rather than change openjdk-6-jre-headless
Investigating libgtk2.0-0
Package libgtk2.0-0 has broken dep on libcups2
  Considering libcups2 374 as a solution to libgtk2.0-0 1147
  Holding Back libgtk2.0-0 rather than change libcups2
Investigating python-gtk2
Package python-gtk2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to python-gtk2 150
  Removing python-gtk2 rather than change libgtk2.0-0
Investigating libbonoboui2-0
Package libbonoboui2-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libbonoboui2-0 146
  Removing libbonoboui2-0 rather than change libgtk2.0-0
Investigating libgnomeui-0
Package libgnomeui-0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to libgnomeui-0 83
  Removing libgnomeui-0 rather than change libbonoboui2-0
Investigating libgail18
Package libgail18 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgail18 80
  Holding Back libgail18 rather than change libgtk2.0-0
Investigating libcanberra-gtk0
Package libcanberra-gtk0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libcanberra-gtk0 65
  Holding Back libcanberra-gtk0 rather than change libgtk2.0-0
Investigating librsvg2-2
Package librsvg2-2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to librsvg2-2 58
  Holding Back librsvg2-2 rather than change libgtk2.0-0
Investigating libpanel-applet2-0
Package libpanel-applet2-0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to libpanel-applet2-0 41
  Removing libpanel-applet2-0 rather than change libbonoboui2-0
Investigating libgnome-desktop-2-17
Package libgnome-desktop-2-17 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgnome-desktop-2-17 40
  Holding Back libgnome-desktop-2-17 rather than change libgtk2.0-0
 Try to Re-Instate libcupsimage2
Investigating librsvg2-common
Package librsvg2-common has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to librsvg2-common 35
  Holding Back librsvg2-common rather than change libgtk2.0-0
Investigating ghostscript
Package ghostscript has broken dep on libgs8
  Considering libgs8 12 as a solution to ghostscript 32
  Holding Back ghostscript rather than change libgs8
Investigating libappindicator0
Package libappindicator0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libappindicator0 29
  Holding Back libappindicator0 rather than change libgtk2.0-0
Investigating python-glade2
Package python-glade2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to python-glade2 28
  Removing python-glade2 rather than change libgtk2.0-0
Investigating libgtk2.0-bin
Package libgtk2.0-bin has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtk2.0-bin 28
  Holding Back libgtk2.0-bin rather than change libgtk2.0-0
Investigating python-gnome2
Package python-gnome2 has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-gnome2 24
  Removing python-gnome2 rather than change python-gtk2
Investigating libindicator0
Package libindicator0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libindicator0 23
  Holding Back libindicator0 rather than change libgtk2.0-0
Investigating libwebkit-1.0-2
Package libwebkit-1.0-2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libwebkit-1.0-2 23
  Holding Back libwebkit-1.0-2 rather than change libgtk2.0-0
Investigating libgtk2.0-cil
Package libgtk2.0-cil has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtk2.0-cil 22
  Holding Back libgtk2.0-cil rather than change libgtk2.0-0
Investigating libnautilus-extension1
Package libnautilus-extension1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libnautilus-extension1 22
  Holding Back libnautilus-extension1 rather than change libgtk2.0-0
Investigating libwnck22
Package libwnck22 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libwnck22 21
  Holding Back libwnck22 rather than change libgtk2.0-0
Investigating default-jre-headless
Package default-jre-headless has broken dep on openjdk-6-jre-headless
  Considering openjdk-6-jre-headless 18 as a solution to default-jre-headless 21
  Holding Back default-jre-headless rather than change openjdk-6-jre-headless
Investigating libdbusmenu-gtk1
Package libdbusmenu-gtk1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libdbusmenu-gtk1 20
  Holding Back libdbusmenu-gtk1 rather than change libgtk2.0-0
Investigating policykit-1-gnome
Package policykit-1-gnome has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to policykit-1-gnome 19
  Holding Back policykit-1-gnome rather than change libappindicator0
Investigating libgtkhtml3.14-19
Package libgtkhtml3.14-19 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtkhtml3.14-19 19
  Removing libgtkhtml3.14-19 rather than change libgtk2.0-0
Investigating libvte9
Package libvte9 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libvte9 18
  Holding Back libvte9 rather than change libgtk2.0-0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-keyring 17
  Holding Back gnome-keyring rather than change libgtk2.0-0
Investigating gnome-games-common
Package gnome-games-common has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to gnome-games-common 17
  Holding Back gnome-games-common rather than change libcanberra-gtk0
Investigating libedataserverui1.2-8
Package libedataserverui1.2-8 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libedataserverui1.2-8 17
  Holding Back libedataserverui1.2-8 rather than change libgtk2.0-0
Investigating synaptic
Package synaptic has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to synaptic 14
  Removing synaptic rather than change libgtk2.0-0
Investigating gnome-panel
Package gnome-panel has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gnome-panel 13
  Removing gnome-panel rather than change libbonoboui2-0
Investigating python-gnomekeyring
Package python-gnomekeyring has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-gnomekeyring 12
  Holding Back python-gnomekeyring rather than change python-gtk2
 Try to Re-Instate libgs8
Investigating libgnome-pilot2
Package libgnome-pilot2 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to libgnome-pilot2 11
  Holding Back libgnome-pilot2 rather than change libbonoboui2-0
Investigating evolution
Package evolution has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to evolution 10
  Removing evolution rather than change libbonoboui2-0
Investigating libgtkhtml-editor0
Package libgtkhtml-editor0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtkhtml-editor0 10
  Holding Back libgtkhtml-editor0 rather than change libgtk2.0-0
Investigating python-vte
Package python-vte has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to python-vte 10
  Removing python-vte rather than change libgtk2.0-0
Investigating libgail-common
Package libgail-common has broken dep on libgail18
  Considering libgail18 80 as a solution to libgail-common 9
  Holding Back libgail-common rather than change libgail18
Investigating libgnome-media0
Package libgnome-media0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgnome-media0 9
  Removing libgnome-media0 rather than change libgtk2.0-0
Investigating gnome-control-center
Package gnome-control-center has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to gnome-control-center 9
  Removing gnome-control-center rather than change libappindicator0
Investigating gnome-about
Package gnome-about has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to gnome-about 9
  Removing gnome-about rather than change python-gtk2
 Try to Re-Instate libgnomecups1.0-1
 Try to Re-Instate kdelibs4c2a
Investigating nautilus
Package nautilus has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to nautilus 8
  Removing nautilus rather than change libappindicator0
Investigating python-webkit
Package python-webkit has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 23 as a solution to python-webkit 8
  Holding Back python-webkit rather than change libwebkit-1.0-2
Investigating liblpint-bonobo0
Package liblpint-bonobo0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to liblpint-bonobo0 8
  Removing liblpint-bonobo0 rather than change libbonoboui2-0
Investigating pidgin
Package pidgin has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to pidgin 8
  Removing pidgin rather than change libgtk2.0-0
Investigating python-gmenu
Package python-gmenu has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-gmenu 8
  Removing python-gmenu rather than change python-gtk2
Investigating python-notify
Package python-notify has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-notify 7
  Removing python-notify rather than change python-gtk2
Investigating libglade2.0-cil
Package libglade2.0-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 22 as a solution to libglade2.0-cil 7
  Holding Back libglade2.0-cil rather than change libgtk2.0-cil
Investigating gnome-session-bin
Package gnome-session-bin has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-session-bin 7
  Holding Back gnome-session-bin rather than change libgtk2.0-0
Investigating python-gnomeapplet
Package python-gnomeapplet has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to python-gnomeapplet 7
  Holding Back python-gnomeapplet rather than change libbonoboui2-0
Investigating gimp
Package gimp has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to gimp 7
  Removing gimp rather than change python-gtk2
 Try to Re-Instate foomatic-db
Investigating python-wnck
Package python-wnck has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-wnck 7
  Holding Back python-wnck rather than change python-gtk2
Investigating python-gnome2-desktop
Package python-gnome2-desktop has broken dep on python-gnomeapplet
  Considering python-gnomeapplet 7 as a solution to python-gnome2-desktop 7
  Removing python-gnome2-desktop rather than change python-gnomeapplet
Investigating rhythmbox
Package rhythmbox has broken dep on libgnome-media0
  Considering libgnome-media0 1147 as a solution to rhythmbox 6
  Removing rhythmbox rather than change libgnome-media0
 Try to Re-Instate foomatic-db-engine
Investigating firefox
Package firefox has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to firefox 6
  Holding Back firefox rather than change libgtk2.0-0
Investigating libmetacity-private0
Package libmetacity-private0 has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to libmetacity-private0 6
  Holding Back libmetacity-private0 rather than change libcanberra-gtk0
Investigating libgnomekbd4
Package libgnomekbd4 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgnomekbd4 5
  Holding Back libgnomekbd4 rather than change libgtk2.0-0
Investigating python-evince
Package python-evince has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-evince 5
  Holding Back python-evince rather than change python-gtk2
Investigating zenity
Package zenity has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to zenity 5
  Holding Back zenity rather than change libgtk2.0-0
Investigating gtk2-engines-pixbuf
Package gtk2-engines-pixbuf has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gtk2-engines-pixbuf 5
  Holding Back gtk2-engines-pixbuf rather than change libgtk2.0-0
Investigating gir1.0-gtk-2.0
Package gir1.0-gtk-2.0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gir1.0-gtk-2.0 5
  Holding Back gir1.0-gtk-2.0 rather than change libgtk2.0-0
Investigating python-gnomedesktop
Package python-gnomedesktop has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 40 as a solution to python-gnomedesktop 5
  Holding Back python-gnomedesktop rather than change libgnome-desktop-2-17
Investigating gdm
Package gdm has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gdm 5
  Holding Back gdm rather than change libbonoboui2-0
Investigating libgtksourceview2.0-0
Package libgtksourceview2.0-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtksourceview2.0-0 5
  Removing libgtksourceview2.0-0 rather than change libgtk2.0-0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtk2-perl 5
  Removing libgtk2-perl rather than change libgtk2.0-0
Investigating python-metacity
Package python-metacity has broken dep on libmetacity-private0
  Considering libmetacity-private0 6 as a solution to python-metacity 5
  Holding Back python-metacity rather than change libmetacity-private0
Investigating libevdocument2
Package libevdocument2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libevdocument2 5
  Holding Back libevdocument2 rather than change libgtk2.0-0
Investigating python-rsvg
Package python-rsvg has broken dep on librsvg2-2
  Considering librsvg2-2 58 as a solution to python-rsvg 5
  Holding Back python-rsvg rather than change librsvg2-2
Investigating python-mediaprofiles
Package python-mediaprofiles has broken dep on libgnome-media0
  Considering libgnome-media0 1147 as a solution to python-mediaprofiles 5
  Holding Back python-mediaprofiles rather than change libgnome-media0
Investigating python-bugbuddy
Package python-bugbuddy has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-bugbuddy 5
  Holding Back python-bugbuddy rather than change python-gtk2
Investigating python-totem-plparser
Package python-totem-plparser has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-totem-plparser 5
  Holding Back python-totem-plparser rather than change python-gtk2
Investigating python-evolution
Package python-evolution has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-evolution 5
  Holding Back python-evolution rather than change python-gtk2
Investigating firefox-branding
Package firefox-branding has broken dep on firefox
  Considering firefox 6 as a solution to firefox-branding 5
  Holding Back firefox-branding rather than change firefox
Investigating totem
Package totem has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to totem 5
  Holding Back totem rather than change libgtk2.0-0
Investigating python-gtop
Package python-gtop has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-gtop 5
  Holding Back python-gtop rather than change python-gtk2
Investigating libmono-addins-gui0.2-cil
Package libmono-addins-gui0.2-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 22 as a solution to libmono-addins-gui0.2-cil 4
  Holding Back libmono-addins-gui0.2-cil rather than change libgtk2.0-cil
Investigating python-desktopcouch-records
Package python-desktopcouch-records has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-desktopcouch-records 4
  Holding Back python-desktopcouch-records rather than change python-gtk2
Investigating xulrunner-1.9.2
Package xulrunner-1.9.2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to xulrunner-1.9.2 4
  Holding Back xulrunner-1.9.2 rather than change libgtk2.0-0
Investigating gnome-settings-daemon
Package gnome-settings-daemon has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to gnome-settings-daemon 4
  Removing gnome-settings-daemon rather than change libappindicator0
Investigating libwxgtk2.8-0
Package libwxgtk2.8-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libwxgtk2.8-0 4
  Holding Back libwxgtk2.8-0 rather than change libgtk2.0-0
Investigating libindicate-gtk2
Package libindicate-gtk2 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libindicate-gtk2 4
  Holding Back libindicate-gtk2 rather than change libgtk2.0-0
Investigating libgnome2.24-cil
Package libgnome2.24-cil has broken dep on libglade2.0-cil
  Considering libglade2.0-cil 7 as a solution to libgnome2.24-cil 4
  Holding Back libgnome2.24-cil rather than change libglade2.0-cil
Investigating libido-0.1-0
Package libido-0.1-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libido-0.1-0 4
  Holding Back libido-0.1-0 rather than change libgtk2.0-0
Investigating libgtkmm-2.4-1c2a
Package libgtkmm-2.4-1c2a has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtkmm-2.4-1c2a 4
  Holding Back libgtkmm-2.4-1c2a rather than change libgtk2.0-0
Investigating yelp
Package yelp has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to yelp 4
  Removing yelp rather than change libgtk2.0-0
Investigating libgucharmap7
Package libgucharmap7 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgucharmap7 4
  Holding Back libgucharmap7 rather than change libgtk2.0-0
Investigating python-desktopcouch
Package python-desktopcouch has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-desktopcouch 4
  Holding Back python-desktopcouch rather than change python-gtk2
Investigating update-manager
Package update-manager has broken dep on synaptic
  Considering synaptic 1147 as a solution to update-manager 3
  Removing update-manager rather than change synaptic
Investigating metacity
Package metacity has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to metacity 3
  Removing metacity rather than change libcanberra-gtk0
Investigating epiphany-browser
Package epiphany-browser has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to epiphany-browser 3
  Holding Back epiphany-browser rather than change libgtk2.0-0
Investigating libgail-gnome-module
Package libgail-gnome-module has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to libgail-gnome-module 3
  Removing libgail-gnome-module rather than change libbonoboui2-0
Investigating desktopcouch
Package desktopcouch has broken dep on python-desktopcouch
  Considering python-desktopcouch 4 as a solution to desktopcouch 3
  Holding Back desktopcouch rather than change python-desktopcouch
Investigating libgegl-0.0-0
Package libgegl-0.0-0 has broken dep on librsvg2-2
  Considering librsvg2-2 58 as a solution to libgegl-0.0-0 3
  Holding Back libgegl-0.0-0 rather than change librsvg2-2
Investigating libbrasero-media0
Package libbrasero-media0 has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to libbrasero-media0 3
  Holding Back libbrasero-media0 rather than change libappindicator0
Investigating libseed0
Package libseed0 has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 23 as a solution to libseed0 3
  Holding Back libseed0 rather than change libwebkit-1.0-2
Investigating python-aptdaemon-gtk
Package python-aptdaemon-gtk has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-aptdaemon-gtk 3
  Holding Back python-aptdaemon-gtk rather than change python-gtk2
Investigating libevview2
Package libevview2 has broken dep on libevdocument2
  Considering libevdocument2 5 as a solution to libevview2 3
  Holding Back libevview2 rather than change libevdocument2
Investigating libgnome-bluetooth7
Package libgnome-bluetooth7 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgnome-bluetooth7 3
  Holding Back libgnome-bluetooth7 rather than change libgtk2.0-0
Investigating libgcr0
Package libgcr0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgcr0 3
  Holding Back libgcr0 rather than change libgtk2.0-0
Investigating eog
Package eog has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 40 as a solution to eog 3
  Removing eog rather than change libgnome-desktop-2-17
Investigating libubuntuone-1.0-1
Package libubuntuone-1.0-1 has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 23 as a solution to libubuntuone-1.0-1 3
  Holding Back libubuntuone-1.0-1 rather than change libwebkit-1.0-2
Investigating libclutter-gtk-0.10-0
Package libclutter-gtk-0.10-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libclutter-gtk-0.10-0 3
  Holding Back libclutter-gtk-0.10-0 rather than change libgtk2.0-0
Investigating libgnome-window-settings1
Package libgnome-window-settings1 has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 40 as a solution to libgnome-window-settings1 3
  Removing libgnome-window-settings1 rather than change libgnome-desktop-2-17
Investigating software-properties-gtk
Package software-properties-gtk has broken dep on synaptic
  Considering synaptic 1147 as a solution to software-properties-gtk 3
  Removing software-properties-gtk rather than change synaptic
Investigating ibus
Package ibus has broken dep on python-glade2
  Considering python-glade2 1147 as a solution to ibus 3
  Holding Back ibus rather than change python-glade2
Investigating gnome-applets
Package gnome-applets has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gnome-applets 3
  Removing gnome-applets rather than change libbonoboui2-0
Investigating gtk2-engines-murrine
Package gtk2-engines-murrine has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gtk2-engines-murrine 3
  Holding Back gtk2-engines-murrine rather than change libgtk2.0-0
Investigating python-wxgtk2.8
Package python-wxgtk2.8 has broken dep on libwxgtk2.8-0
  Considering libwxgtk2.8-0 4 as a solution to python-wxgtk2.8 3
  Removing python-wxgtk2.8 rather than change libwxgtk2.8-0
Investigating ca-certificates-java
Package ca-certificates-java has broken dep on openjdk-6-jre-headless
  Considering openjdk-6-jre-headless 18 as a solution to ca-certificates-java 3
  Holding Back ca-certificates-java rather than change openjdk-6-jre-headless
Package ca-certificates-java has broken dep on java6-runtime-headless
  Considering openjdk-6-jre-headless 18 as a solution to ca-certificates-java 3
  Holding Back ca-certificates-java rather than change java6-runtime-headless
  Or group keep for ca-certificates-java
Investigating libwxgtk2.6-0
Package libwxgtk2.6-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libwxgtk2.6-0 2
  Holding Back libwxgtk2.6-0 rather than change libgtk2.0-0
Investigating python-gtksourceview2
Package python-gtksourceview2 has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-gtksourceview2 2
  Removing python-gtksourceview2 rather than change python-gtk2
Investigating libgoffice-0.8-8
Package libgoffice-0.8-8 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgoffice-0.8-8 2
  Holding Back libgoffice-0.8-8 rather than change libgtk2.0-0
Investigating liblaunchpad-integration1.0-cil
Package liblaunchpad-integration1.0-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 22 as a solution to liblaunchpad-integration1.0-cil 2
  Holding Back liblaunchpad-integration1.0-cil rather than change libgtk2.0-cil
Investigating notify-osd
Package notify-osd has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to notify-osd 2
  Holding Back notify-osd rather than change libgtk2.0-0
Investigating libpolkit-gnome0
Package libpolkit-gnome0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libpolkit-gnome0 2
  Holding Back libpolkit-gnome0 rather than change libgtk2.0-0
Investigating evince
Package evince has broken dep on libevdocument2
  Considering libevdocument2 5 as a solution to evince 2
  Removing evince rather than change libevdocument2
Investigating libgtkhtml2-0
Package libgtkhtml2-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtkhtml2-0 2
  Holding Back libgtkhtml2-0 rather than change libgtk2.0-0
Investigating indicator-applet-session
Package indicator-applet-session has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to indicator-applet-session 2
  Holding Back indicator-applet-session rather than change libgtk2.0-0
Investigating rhythmbox-plugins
Package rhythmbox-plugins has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to rhythmbox-plugins 2
  Holding Back rhythmbox-plugins rather than change libappindicator0
Investigating python-ubuntuone
Package python-ubuntuone has broken dep on libubuntuone-1.0-1
  Considering libubuntuone-1.0-1 3 as a solution to python-ubuntuone 2
  Holding Back python-ubuntuone rather than change libubuntuone-1.0-1
Investigating gnome-system-tools
Package gnome-system-tools has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-system-tools 2
  Holding Back gnome-system-tools rather than change libgtk2.0-0
Investigating libgtkglext1
Package libgtkglext1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtkglext1 2
  Holding Back libgtkglext1 rather than change libgtk2.0-0
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on libgtk2-perl
  Considering libgtk2-perl 1147 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change libgtk2-perl
Investigating libgtk2.0-0-dbg
Package libgtk2.0-0-dbg has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtk2.0-0-dbg 1
  Holding Back libgtk2.0-0-dbg rather than change libgtk2.0-0
Investigating python-pygoocanvas
Package python-pygoocanvas has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to python-pygoocanvas 1
  Holding Back python-pygoocanvas rather than change libgtk2.0-0
Investigating gwibber-service
Package gwibber-service has broken dep on python-notify
  Considering python-notify 1147 as a solution to gwibber-service 1
  Holding Back gwibber-service rather than change python-notify
Investigating gcalctool
Package gcalctool has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gcalctool 1
  Holding Back gcalctool rather than change libgtk2.0-0
Investigating gnome-nettool
Package gnome-nettool has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-nettool 1
  Holding Back gnome-nettool rather than change libgtk2.0-0
Investigating gnome-media
Package gnome-media has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to gnome-media 1
  Removing gnome-media rather than change libcanberra-gtk0
Investigating gucharmap
Package gucharmap has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gucharmap 1
  Holding Back gucharmap rather than change libgtk2.0-0
Investigating gdebi
Package gdebi has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to gdebi 1
  Removing gdebi rather than change python-gtk2
Investigating gnome-bluetooth
Package gnome-bluetooth has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to gnome-bluetooth 1
  Holding Back gnome-bluetooth rather than change libappindicator0
Investigating gnome-power-manager
Package gnome-power-manager has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to gnome-power-manager 1
  Removing gnome-power-manager rather than change libappindicator0
Investigating alacarte
Package alacarte has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to alacarte 1
  Removing alacarte rather than change python-gtk2
Investigating gedit
Package gedit has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gedit 1
  Removing gedit rather than change libgtk2.0-0
Investigating evolution-dbg
Package evolution-dbg has broken dep on evolution
  Considering evolution 1147 as a solution to evolution-dbg 1
  Holding Back evolution-dbg rather than change evolution
Investigating eog-dbg
Package eog-dbg has broken dep on eog
  Considering eog 40 as a solution to eog-dbg 1
  Holding Back eog-dbg rather than change eog
Investigating seahorse
Package seahorse has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to seahorse 1
  Removing seahorse rather than change libgtk2.0-0
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libbonoboui2-0
Investigating ghostscript-x
Package ghostscript-x has broken dep on ghostscript
  Considering ghostscript 32 as a solution to ghostscript-x 1
  Holding Back ghostscript-x rather than change ghostscript
Investigating light-themes
Package light-themes has broken dep on gtk2-engines-murrine
  Considering gtk2-engines-murrine 3 as a solution to light-themes 1
  Holding Back light-themes rather than change gtk2-engines-murrine
Investigating indicator-applet
Package indicator-applet has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to indicator-applet 1
  Holding Back indicator-applet rather than change libgtk2.0-0
Investigating gnome-pilot
Package gnome-pilot has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gnome-pilot 1
  Removing gnome-pilot rather than change libbonoboui2-0
Investigating update-notifier
Package update-notifier has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to update-notifier 1
  Removing update-notifier rather than change libgtk2.0-0
Investigating seed
Package seed has broken dep on libseed0
  Considering libseed0 3 as a solution to seed 1
  Holding Back seed rather than change libseed0
Investigating ubuntuone-client-gnome
Package ubuntuone-client-gnome has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to ubuntuone-client-gnome 1
  Holding Back ubuntuone-client-gnome rather than change libgtk2.0-0
Investigating gnome-terminal
Package gnome-terminal has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-terminal 1
  Removing gnome-terminal rather than change libgtk2.0-0
Investigating python-gtkspell
Package python-gtkspell has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-gtkspell 1
  Holding Back python-gtkspell rather than change python-gtk2
Investigating couchdb-bin
Package couchdb-bin has broken dep on xulrunner-1.9.2
  Considering xulrunner-1.9.2 4 as a solution to couchdb-bin 1
  Holding Back couchdb-bin rather than change xulrunner-1.9.2
Investigating libpolkit-gtk-1-0
Package libpolkit-gtk-1-0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libpolkit-gtk-1-0 1
  Holding Back libpolkit-gtk-1-0 rather than change libgtk2.0-0
Investigating gnome-utils
Package gnome-utils has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gnome-utils 1
  Removing gnome-utils rather than change libbonoboui2-0
Investigating software-center
Package software-center has broken dep on python-aptdaemon-gtk
  Considering python-aptdaemon-gtk 3 as a solution to software-center 1
  Holding Back software-center rather than change python-aptdaemon-gtk
Investigating libgdu-gtk0
Package libgdu-gtk0 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgdu-gtk0 1
  Holding Back libgdu-gtk0 rather than change libgtk2.0-0
Investigating checkbox-gtk
Package checkbox-gtk has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to checkbox-gtk 1
  Holding Back checkbox-gtk rather than change python-gtk2
Investigating python-pyatspi
Package python-pyatspi has broken dep on python-gnome2
  Considering python-gnome2 1147 as a solution to python-pyatspi 1
  Removing python-pyatspi rather than change python-gnome2
Investigating libgtk2.0-dev
Package libgtk2.0-dev has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgtk2.0-dev 1
  Holding Back libgtk2.0-dev rather than change libgtk2.0-0
Investigating language-selector
Package language-selector has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to language-selector 1
  Removing language-selector rather than change python-gtk2
Investigating gnome-system-monitor
Package gnome-system-monitor has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-system-monitor 1
  Holding Back gnome-system-monitor rather than change libgtk2.0-0
Investigating gnome-panel-dbg
Package gnome-panel-dbg has broken dep on gnome-panel
  Considering gnome-panel 1147 as a solution to gnome-panel-dbg 1
  Holding Back gnome-panel-dbg rather than change gnome-panel
Investigating gnome-user-guide
Package gnome-user-guide has broken dep on yelp
  Considering yelp 1147 as a solution to gnome-user-guide 1
  Removing gnome-user-guide rather than change yelp
Investigating apturl
Package apturl has broken dep on python-glade2
  Considering python-glade2 1147 as a solution to apturl 1
  Removing apturl rather than change python-glade2
 Try to Re-Instate openprinting-ppds
Investigating nautilus-dbg
Package nautilus-dbg has broken dep on nautilus
  Considering nautilus 29 as a solution to nautilus-dbg 1
  Holding Back nautilus-dbg rather than change nautilus
Investigating libgtkhtml3.14-dbg
Package libgtkhtml3.14-dbg has broken dep on libgtkhtml3.14-19
  Considering libgtkhtml3.14-19 1147 as a solution to libgtkhtml3.14-dbg 1
  Holding Back libgtkhtml3.14-dbg rather than change libgtkhtml3.14-19
Investigating gnome-applets-dbg
Package gnome-applets-dbg has broken dep on gnome-applets
  Considering gnome-applets 1147 as a solution to gnome-applets-dbg 1
  Holding Back gnome-applets-dbg rather than change gnome-applets
Investigating policykit-gnome
Package policykit-gnome has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to policykit-gnome 1
  Holding Back policykit-gnome rather than change libgtk2.0-0
Investigating gir1.0-clutter-gtk-0.10
Package gir1.0-clutter-gtk-0.10 has broken dep on gir1.0-gtk-2.0
  Considering gir1.0-gtk-2.0 5 as a solution to gir1.0-clutter-gtk-0.10 1
  Holding Back gir1.0-clutter-gtk-0.10 rather than change gir1.0-gtk-2.0
Investigating librsvg2-dbg
Package librsvg2-dbg has broken dep on librsvg2-2
  Considering librsvg2-2 58 as a solution to librsvg2-dbg 1
  Holding Back librsvg2-dbg rather than change librsvg2-2
Investigating epiphany-browser-dbg
Package epiphany-browser-dbg has broken dep on epiphany-browser
  Considering epiphany-browser 3 as a solution to epiphany-browser-dbg 1
  Holding Back epiphany-browser-dbg rather than change epiphany-browser
Investigating libgdict-1.0-6
Package libgdict-1.0-6 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgdict-1.0-6 1
  Holding Back libgdict-1.0-6 rather than change libgtk2.0-0
Investigating gconf-editor
Package gconf-editor has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gconf-editor 1
  Removing gconf-editor rather than change libgtk2.0-0
Investigating libgnomeui-0-dbg
Package libgnomeui-0-dbg has broken dep on libgnomeui-0
  Considering libgnomeui-0 1147 as a solution to libgnomeui-0-dbg 1
  Holding Back libgnomeui-0-dbg rather than change libgnomeui-0
Investigating python-ubuntuone-client
Package python-ubuntuone-client has broken dep on python-gnomekeyring
  Considering python-gnomekeyring 12 as a solution to python-ubuntuone-client 1
  Holding Back python-ubuntuone-client rather than change python-gnomekeyring
Package python-ubuntuone-client has broken dep on python-gnome2-desktop
  Considering python-gnome2-desktop 7 as a solution to python-ubuntuone-client 1
  Holding Back python-ubuntuone-client rather than change python-gnome2-desktop
  Or group keep for python-ubuntuone-client
Package python-ubuntuone-client has broken dep on python-notify
  Considering python-notify 1147 as a solution to python-ubuntuone-client 1
  Holding Back python-ubuntuone-client rather than change python-notify
Investigating deskbar-applet
Package deskbar-applet has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 40 as a solution to deskbar-applet 1
  Removing deskbar-applet rather than change libgnome-desktop-2-17
Investigating totem-dbg
Package totem-dbg has broken dep on totem
  Considering totem 5 as a solution to totem-dbg 1
  Holding Back totem-dbg rather than change totem
Investigating python-ibus
Package python-ibus has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-ibus 1
  Holding Back python-ibus rather than change python-gtk2
Investigating libgnome-desktop-2
Package libgnome-desktop-2 has broken dep on libgnomeui-0
  Considering libgnomeui-0 1147 as a solution to libgnome-desktop-2 1
  Removing libgnome-desktop-2 rather than change libgnomeui-0
Investigating gnome-session
Package gnome-session has broken dep on gnome-settings-daemon
  Considering gnome-settings-daemon 29 as a solution to gnome-session 1
  Removing gnome-session rather than change gnome-settings-daemon
Investigating file-roller
Package file-roller has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to file-roller 1
  Removing file-roller rather than change libgtk2.0-0
Investigating nautilus-sendto
Package nautilus-sendto has broken dep on libnautilus-extension1
  Considering libnautilus-extension1 22 as a solution to nautilus-sendto 1
  Removing nautilus-sendto rather than change libnautilus-extension1
Investigating python-gtk2-dbg
Package python-gtk2-dbg has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-gtk2-dbg 1
  Holding Back python-gtk2-dbg rather than change python-gtk2
Investigating f-spot
Package f-spot has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to f-spot 0
  Removing f-spot rather than change libgtk2.0-0
Investigating libgladeui-1-9
Package libgladeui-1-9 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libgladeui-1-9 0
  Holding Back libgladeui-1-9 rather than change libgtk2.0-0
Investigating tomboy
Package tomboy has broken dep on libgnome2.24-cil
  Considering libgnome2.24-cil 4 as a solution to tomboy 0
  Removing tomboy rather than change libgnome2.24-cil
Investigating ekiga
Package ekiga has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to ekiga 0
  Removing ekiga rather than change libgtk2.0-0
Investigating gthumb
Package gthumb has broken dep on libgnomeui-0
  Considering libgnomeui-0 1147 as a solution to gthumb 0
  Removing gthumb rather than change libgnomeui-0
Investigating libgnomepanel2.24-cil
Package libgnomepanel2.24-cil has broken dep on libpanel-applet2-0
  Considering libpanel-applet2-0 1147 as a solution to libgnomepanel2.24-cil 0
  Holding Back libgnomepanel2.24-cil rather than change libpanel-applet2-0
Investigating aisleriot
Package aisleriot has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to aisleriot 0
  Holding Back aisleriot rather than change libcanberra-gtk0
Investigating hal-cups-utils
Package hal-cups-utils has broken dep on system-config-printer-udev
  Considering system-config-printer-udev 0 as a solution to hal-cups-utils 0
  Removing hal-cups-utils rather than change system-config-printer-udev
Investigating gtali
Package gtali has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gtali 0
  Holding Back gtali rather than change libgtk2.0-0
Investigating ubuntu-docs
Package ubuntu-docs has broken dep on gnome-user-guide
  Considering gnome-user-guide 1147 as a solution to ubuntu-docs 0
  Removing ubuntu-docs rather than change gnome-user-guide
Investigating libgtk2-ex-simple-list-perl
Package libgtk2-ex-simple-list-perl has broken dep on libgtk2-perl
  Considering libgtk2-perl 1147 as a solution to libgtk2-ex-simple-list-perl 0
  Removing libgtk2-ex-simple-list-perl rather than change libgtk2-perl
Investigating glchess
Package glchess has broken dep on gnome-games-common
  Considering gnome-games-common 17 as a solution to glchess 0
  Holding Back glchess rather than change gnome-games-common
Investigating libdevhelp-1-1
Package libdevhelp-1-1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libdevhelp-1-1 0
  Holding Back libdevhelp-1-1 rather than change libgtk2.0-0
Investigating amule
Package amule has broken dep on libwxgtk2.8-0
  Considering libwxgtk2.8-0 4 as a solution to amule 0
  Removing amule rather than change libwxgtk2.8-0
 Try to Re-Instate foomatic-db-gutenprint
 Try to Re-Instate pxljr
Investigating libopenrawgnome1
Package libopenrawgnome1 has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to libopenrawgnome1 0
  Holding Back libopenrawgnome1 rather than change libgtk2.0-0
Investigating gnome-games
Package gnome-games has broken dep on aisleriot
  Considering aisleriot 0 as a solution to gnome-games 0
  Removing gnome-games rather than change aisleriot
Investigating gnome-session-canberra
Package gnome-session-canberra has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to gnome-session-canberra 0
  Holding Back gnome-session-canberra rather than change libcanberra-gtk0
Investigating libxt-java
Package libxt-java has broken dep on default-jre-headless
  Considering default-jre-headless 21 as a solution to libxt-java 0
  Holding Back libxt-java rather than change default-jre-headless
Investigating evolution-exchange
Package evolution-exchange has broken dep on evolution
  Considering evolution 1147 as a solution to evolution-exchange 0
  Removing evolution-exchange rather than change evolution
Investigating quadrapassel
Package quadrapassel has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to quadrapassel 0
  Holding Back quadrapassel rather than change libcanberra-gtk0
Investigating ubufox
Package ubufox has broken dep on apturl
  Considering apturl 1147 as a solution to ubufox 0
Package ubufox has broken dep on apturl-kde
  Considering apturl-kde 1 as a solution to ubufox 0
  Or group remove for ubufox
Investigating gnobots2
Package gnobots2 has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to gnobots2 0
  Holding Back gnobots2 rather than change libcanberra-gtk0
Investigating avidemux
Package avidemux has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to avidemux 0
  Removing avidemux rather than change libgtk2.0-0
Investigating gnome-mahjongg
Package gnome-mahjongg has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-mahjongg 0
  Holding Back gnome-mahjongg rather than change libgtk2.0-0
Investigating gparted
Package gparted has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gparted 0
  Holding Back gparted rather than change libgtk2.0-0
Investigating totem-plugins
Package totem-plugins has broken dep on totem
  Considering totem 5 as a solution to totem-plugins 0
  Removing totem-plugins rather than change totem
Investigating gnome-screensaver
Package gnome-screensaver has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 40 as a solution to gnome-screensaver 0
  Removing gnome-screensaver rather than change libgnome-desktop-2-17
Investigating gnome-mag
Package gnome-mag has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-mag 0
  Holding Back gnome-mag rather than change libgtk2.0-0
 Try to Re-Instate bluez-cups
Investigating lightsoff
Package lightsoff has broken dep on gnome-games-common
  Considering gnome-games-common 17 as a solution to lightsoff 0
  Holding Back lightsoff rather than change gnome-games-common
Investigating libgtkhtml3.16-cil
Package libgtkhtml3.16-cil has broken dep on libgtk2.0-cil
  Considering libgtk2.0-cil 22 as a solution to libgtkhtml3.16-cil 0
  Removing libgtkhtml3.16-cil rather than change libgtk2.0-cil
Investigating vinagre
Package vinagre has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to vinagre 0
  Holding Back vinagre rather than change libbonoboui2-0
Investigating hwtest-gtk
Package hwtest-gtk has broken dep on checkbox-gtk
  Considering checkbox-gtk 1 as a solution to hwtest-gtk 0
  Removing hwtest-gtk rather than change checkbox-gtk
Investigating gnibbles
Package gnibbles has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to gnibbles 0
  Holding Back gnibbles rather than change libcanberra-gtk0
Investigating network-manager-gnome
Package network-manager-gnome has broken dep on libgnome-bluetooth7
  Considering libgnome-bluetooth7 3 as a solution to network-manager-gnome 0
  Removing network-manager-gnome rather than change libgnome-bluetooth7
Investigating soundconverter
Package soundconverter has broken dep on python-gnome2
  Considering python-gnome2 1147 as a solution to soundconverter 0
  Removing soundconverter rather than change python-gnome2
Investigating scim-gtk2-immodule
Package scim-gtk2-immodule has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to scim-gtk2-immodule 0
  Removing scim-gtk2-immodule rather than change libgtk2.0-0
Investigating anjuta
Package anjuta has broken dep on libdevhelp-1-1
  Considering libdevhelp-1-1 0 as a solution to anjuta 0
  Holding Back anjuta rather than change libdevhelp-1-1
Investigating gnome-orca
Package gnome-orca has broken dep on python-pyatspi
  Considering python-pyatspi 1147 as a solution to gnome-orca 0
Package gnome-orca has broken dep on python-pyatspi2
  Or group remove for gnome-orca
Package gnome-orca has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to gnome-orca 0
  Removing gnome-orca rather than change python-gtk2
Investigating nautilus-cd-burner
Package nautilus-cd-burner has broken dep on libgnomeui-0
  Considering libgnomeui-0 1147 as a solution to nautilus-cd-burner 0
  Removing nautilus-cd-burner rather than change libgnomeui-0
Investigating swell-foop
Package swell-foop has broken dep on gnome-games-common
  Considering gnome-games-common 17 as a solution to swell-foop 0
  Holding Back swell-foop rather than change gnome-games-common
Investigating mysql-admin
Package mysql-admin has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 4 as a solution to mysql-admin 0
  Removing mysql-admin rather than change libgtkmm-2.4-1c2a
Investigating gnotski
Package gnotski has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnotski 0
  Holding Back gnotski rather than change libgtk2.0-0
Investigating computertemp
Package computertemp has broken dep on python-gnome2
  Considering python-gnome2 1147 as a solution to computertemp 0
  Removing computertemp rather than change python-gnome2
Investigating gok
Package gok has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to gok 0
  Removing gok rather than change libcanberra-gtk0
Investigating python-sexy
Package python-sexy has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to python-sexy 0
  Removing python-sexy rather than change python-gtk2
Investigating bug-buddy
Package bug-buddy has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to bug-buddy 0
  Removing bug-buddy rather than change libgtk2.0-0
 Try to Re-Instate splix
Investigating tsclient
Package tsclient has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to tsclient 0
  Removing tsclient rather than change libbonoboui2-0
Investigating vino
Package vino has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to vino 0
  Removing vino rather than change libgtk2.0-0
Investigating mousetweaks
Package mousetweaks has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to mousetweaks 0
  Removing mousetweaks rather than change libbonoboui2-0
 Try to Re-Instate cupsys-driver-gutenprint
Investigating firefox-gnome-support
Package firefox-gnome-support has broken dep on firefox
  Considering firefox 6 as a solution to firefox-gnome-support 0
  Holding Back firefox-gnome-support rather than change firefox
Investigating xchm
Package xchm has broken dep on libwxgtk2.8-0
  Considering libwxgtk2.8-0 4 as a solution to xchm 0
  Holding Back xchm rather than change libwxgtk2.8-0
Investigating powermanagement-interface
Package powermanagement-interface has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to powermanagement-interface 0
  Holding Back powermanagement-interface rather than change libgtk2.0-0
Investigating iagno
Package iagno has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to iagno 0
  Holding Back iagno rather than change libcanberra-gtk0
Investigating glines
Package glines has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to glines 0
  Holding Back glines rather than change libgtk2.0-0
Investigating gnome-app-install
Package gnome-app-install has broken dep on software-center
  Considering software-center 1 as a solution to gnome-app-install 0
  Removing gnome-app-install rather than change software-center
Investigating nautilus-scripts-manager
Package nautilus-scripts-manager has broken dep on nautilus
  Considering nautilus 29 as a solution to nautilus-scripts-manager 0
  Holding Back nautilus-scripts-manager rather than change nautilus
Investigating gnome-sudoku
Package gnome-sudoku has broken dep on gnome-games-common
  Considering gnome-games-common 17 as a solution to gnome-sudoku 0
  Holding Back gnome-sudoku rather than change gnome-games-common
Investigating evolution-plugins
Package evolution-plugins has broken dep on evolution
  Considering evolution 1147 as a solution to evolution-plugins 0
  Removing evolution-plugins rather than change evolution
Investigating nautilus-share
Package nautilus-share has broken dep on nautilus
  Considering nautilus 29 as a solution to nautilus-share 0
  Removing nautilus-share rather than change nautilus
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem
  Considering totem 5 as a solution to totem-gstreamer 0
  Removing totem-gstreamer rather than change totem
 Try to Re-Instate foo2zjs
Investigating libdeskbar-tracker
Package libdeskbar-tracker has broken dep on python-gnome2
  Considering python-gnome2 1147 as a solution to libdeskbar-tracker 0
  Removing libdeskbar-tracker rather than change python-gnome2
Investigating tracker-search-tool
Package tracker-search-tool has broken dep on libgnome-desktop-2-17
  Considering libgnome-desktop-2-17 40 as a solution to tracker-search-tool 0
  Removing tracker-search-tool rather than change libgnome-desktop-2-17
Investigating gnotravex
Package gnotravex has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnotravex 0
  Holding Back gnotravex rather than change libgtk2.0-0
Investigating gnome-netstatus-applet
Package gnome-netstatus-applet has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-netstatus-applet 0
  Removing gnome-netstatus-applet rather than change libgtk2.0-0
Investigating gnect
Package gnect has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to gnect 0
  Holding Back gnect rather than change libcanberra-gtk0
Investigating onboard
Package onboard has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to onboard 0
  Removing onboard rather than change python-gtk2
Investigating jockey-gtk
Package jockey-gtk has broken dep on python-notify
  Considering python-notify 1147 as a solution to jockey-gtk 0
  Removing jockey-gtk rather than change python-notify
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1147 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
 Try to Re-Instate cups-pdf
Investigating apport-gtk
Package apport-gtk has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to apport-gtk 0
  Removing apport-gtk rather than change python-gtk2
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem
  Considering totem 5 as a solution to totem-mozilla 0
  Removing totem-mozilla rather than change totem
Investigating transmission-gtk
Package transmission-gtk has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to transmission-gtk 0
  Removing transmission-gtk rather than change libappindicator0
Investigating scim-bridge-client-gtk
Package scim-bridge-client-gtk has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to scim-bridge-client-gtk 0
  Holding Back scim-bridge-client-gtk rather than change libgtk2.0-0
Investigating sound-juicer
Package sound-juicer has broken dep on libbrasero-media0
  Considering libbrasero-media0 3 as a solution to sound-juicer 0
  Removing sound-juicer rather than change libbrasero-media0
Investigating gnomine
Package gnomine has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnomine 0
  Holding Back gnomine rather than change libgtk2.0-0
Investigating python-indicate
Package python-indicate has broken dep on libindicate-gtk2
  Considering libindicate-gtk2 4 as a solution to python-indicate 0
  Holding Back python-indicate rather than change libindicate-gtk2
Investigating computer-janitor-gtk
Package computer-janitor-gtk has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to computer-janitor-gtk -1
  Holding Back computer-janitor-gtk rather than change python-gtk2
Investigating libcanberra-gtk-module
Package libcanberra-gtk-module has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to libcanberra-gtk-module -1
  Holding Back libcanberra-gtk-module rather than change libcanberra-gtk0
Investigating pidgin-libnotify
Package pidgin-libnotify has broken dep on libindicate-gtk2
  Considering libindicate-gtk2 4 as a solution to pidgin-libnotify -1
  Holding Back pidgin-libnotify rather than change libindicate-gtk2
Investigating indicator-application
Package indicator-application has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 20 as a solution to indicator-application -1
  Holding Back indicator-application rather than change libdbusmenu-gtk1
Investigating gnome-codec-install
Package gnome-codec-install has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to gnome-codec-install -1
  Holding Back gnome-codec-install rather than change python-gtk2
Investigating gbrainy
Package gbrainy has broken dep on libgnome2.24-cil
  Considering libgnome2.24-cil 4 as a solution to gbrainy -1
  Holding Back gbrainy rather than change libgnome2.24-cil
Investigating empathy
Package empathy has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to empathy -1
  Holding Back empathy rather than change libcanberra-gtk0
Investigating gnome-pilot-conduits
Package gnome-pilot-conduits has broken dep on gnome-pilot
  Considering gnome-pilot 1147 as a solution to gnome-pilot-conduits -1
  Removing gnome-pilot-conduits rather than change gnome-pilot
Investigating gnome-user-share
Package gnome-user-share has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to gnome-user-share -1
  Holding Back gnome-user-share rather than change libcanberra-gtk0
Investigating nautilus-sendto-empathy
Package nautilus-sendto-empathy has broken dep on libcanberra-gtk0
  Considering libcanberra-gtk0 65 as a solution to nautilus-sendto-empathy -1
  Holding Back nautilus-sendto-empathy rather than change libcanberra-gtk0
Investigating simple-scan
Package simple-scan has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to simple-scan -1
  Holding Back simple-scan rather than change libgtk2.0-0
Investigating gnome-btdownload
Package gnome-btdownload has broken dep on python-glade2
  Considering python-glade2 1147 as a solution to gnome-btdownload -1
  Removing gnome-btdownload rather than change python-glade2
Investigating indicator-messages
Package indicator-messages has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 20 as a solution to indicator-messages -1
  Holding Back indicator-messages rather than change libdbusmenu-gtk1
Investigating rhythmbox-plugin-cdrecorder
Package rhythmbox-plugin-cdrecorder has broken dep on libbrasero-media0
  Considering libbrasero-media0 3 as a solution to rhythmbox-plugin-cdrecorder -1
  Holding Back rhythmbox-plugin-cdrecorder rather than change libbrasero-media0
Investigating gnome-disk-utility
Package gnome-disk-utility has broken dep on libgdu-gtk0
  Considering libgdu-gtk0 1 as a solution to gnome-disk-utility -1
  Holding Back gnome-disk-utility rather than change libgdu-gtk0
Investigating gnome-spell
Package gnome-spell has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gnome-spell -1
  Removing gnome-spell rather than change libbonoboui2-0
Investigating usb-creator-gtk
Package usb-creator-gtk has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to usb-creator-gtk -1
  Holding Back usb-creator-gtk rather than change python-gtk2
Investigating indicator-me
Package indicator-me has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 20 as a solution to indicator-me -1
  Holding Back indicator-me rather than change libdbusmenu-gtk1
Investigating gaim
Package gaim has broken dep on pidgin
  Considering pidgin 1147 as a solution to gaim -1
  Removing gaim rather than change pidgin
Investigating ibus-m17n
Package ibus-m17n has broken dep on ibus
  Considering ibus 3 as a solution to ibus-m17n -1
  Holding Back ibus-m17n rather than change ibus
Investigating python-appindicator
Package python-appindicator has broken dep on libappindicator0
  Considering libappindicator0 29 as a solution to python-appindicator -1
  Holding Back python-appindicator rather than change libappindicator0
Investigating contact-lookup-applet
Package contact-lookup-applet has broken dep on libgnomeui-0
  Considering libgnomeui-0 1147 as a solution to contact-lookup-applet -1
  Removing contact-lookup-applet rather than change libgnomeui-0
Investigating libeel2-2
Package libeel2-2 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to libeel2-2 -1
  Removing libeel2-2 rather than change libbonoboui2-0
Investigating ibus-table
Package ibus-table has broken dep on ibus
  Considering ibus 3 as a solution to ibus-table -1
  Holding Back ibus-table rather than change ibus
Investigating libgucharmap4
Package libgucharmap4 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to libgucharmap4 -1
  Removing libgucharmap4 rather than change libbonoboui2-0
Investigating pitivi
Package pitivi has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to pitivi -1
  Holding Back pitivi rather than change python-gtk2
Investigating indicator-session
Package indicator-session has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 20 as a solution to indicator-session -1
  Holding Back indicator-session rather than change libdbusmenu-gtk1
Investigating libgnomebt0
Package libgnomebt0 has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to libgnomebt0 -1
  Removing libgnomebt0 rather than change libbonoboui2-0
 Try to Re-Instate cupsys-client
Investigating gwibber
Package gwibber has broken dep on python-gtk2
  Considering python-gtk2 1147 as a solution to gwibber -1
  Holding Back gwibber rather than change python-gtk2
 Try to Re-Instate cupsys
Investigating gdm-guest-session
Package gdm-guest-session has broken dep on gdm
  Considering gdm 5 as a solution to gdm-guest-session -1
  Holding Back gdm-guest-session rather than change gdm
Investigating evolution-couchdb
Package evolution-couchdb has broken dep on evolution
  Considering evolution 1147 as a solution to evolution-couchdb -1
  Holding Back evolution-couchdb rather than change evolution
Investigating rhythmbox-dbg
Package rhythmbox-dbg has broken dep on rhythmbox
  Considering rhythmbox 1147 as a solution to rhythmbox-dbg -2
  Holding Back rhythmbox-dbg rather than change rhythmbox
Investigating gnome-dbg
Package gnome-dbg has broken dep on gnome-applets-dbg
  Considering gnome-applets-dbg 1 as a solution to gnome-dbg -2
  Holding Back gnome-dbg rather than change gnome-applets-dbg
Investigating evolution-indicator
Package evolution-indicator has broken dep on evolution
  Considering evolution 1147 as a solution to evolution-indicator -2
  Holding Back evolution-indicator rather than change evolution
Investigating python-gtkglext1
Package python-gtkglext1 has broken dep on libgtkglext1
  Considering libgtkglext1 2 as a solution to python-gtkglext1 -2
  Holding Back python-gtkglext1 rather than change libgtkglext1
Investigating libwebkit-1.0-2-dbg
Package libwebkit-1.0-2-dbg has broken dep on libwebkit-1.0-2
  Considering libwebkit-1.0-2 23 as a solution to libwebkit-1.0-2-dbg -2
  Holding Back libwebkit-1.0-2-dbg rather than change libwebkit-1.0-2
Investigating libgoffice-dbg
Package libgoffice-dbg has broken dep on libgoffice-0.8-8
  Considering libgoffice-0.8-8 2 as a solution to libgoffice-dbg -2
  Holding Back libgoffice-dbg rather than change libgoffice-0.8-8
Investigating rhythmbox-ubuntuone-music-store
Package rhythmbox-ubuntuone-music-store has broken dep on python-webkit
  Considering python-webkit 8 as a solution to rhythmbox-ubuntuone-music-store -2
  Holding Back rhythmbox-ubuntuone-music-store rather than change python-webkit
Investigating indicator-sound
Package indicator-sound has broken dep on libdbusmenu-gtk1
  Considering libdbusmenu-gtk1 20 as a solution to indicator-sound -2
  Holding Back indicator-sound rather than change libdbusmenu-gtk1
Investigating libgail-gnome-dbg
Package libgail-gnome-dbg has broken dep on libgail-gnome-module
  Considering libgail-gnome-module 1147 as a solution to libgail-gnome-dbg -2
  Holding Back libgail-gnome-dbg rather than change libgail-gnome-module
 Try to Re-Instate libgtk2.0-0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 17 as a solution to libgnome-keyring0 119
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
 Try to Re-Instate libgail18
Investigating gvfs
Package gvfs has broken dep on policykit-1-gnome
  Considering policykit-1-gnome 19 as a solution to gvfs 59
  Holding Back gvfs rather than change policykit-1-gnome
 Try to Re-Instate librsvg2-2
 Try to Re-Instate librsvg2-common
 Try to Re-Instate ghostscript
 Try to Re-Instate libgtk2.0-bin
 Try to Re-Instate libgtk2.0-cil
 Try to Re-Instate libnautilus-extension1
 Try to Re-Instate libwnck22
 Try to Re-Instate libvte9
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 3 as a solution to gnome-keyring 17
  Holding Back gnome-keyring rather than change libgcr0
 Try to Re-Instate libedataserverui1.2-8
Investigating gnome-menus
Package gnome-menus has broken dep on python-gmenu
  Considering python-gmenu 1147 as a solution to gnome-menus 16
  Removing gnome-menus rather than change python-gmenu
Investigating plymouth
Package plymouth has broken dep on gdm
  Considering gdm 5 as a solution to plymouth 14
  Upgrading gdm due to Breaks field in plymouth
 Try to Re-Instate libgnome-pilot2
 Try to Re-Instate libgail-common
 Try to Re-Instate libglade2.0-cil
 Try to Re-Instate firefox
 Try to Re-Instate zenity
 Try to Re-Instate gtk2-engines-pixbuf
Investigating system-tools-backends
Package system-tools-backends has broken dep on gnome-system-tools
  Considering gnome-system-tools 2 as a solution to system-tools-backends 5
  Upgrading gnome-system-tools due to Breaks field in system-tools-backends
Investigating gdm
Package gdm has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gdm 5
  Holding Back gdm rather than change libbonoboui2-0
Investigating libpangomm-1.4-1
Package libpangomm-1.4-1 has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 4 as a solution to libpangomm-1.4-1 5
  Added libgtkmm-2.4-1c2a to the remove list
  Fixing libpangomm-1.4-1 via remove of libgtkmm-2.4-1c2a
 Try to Re-Instate firefox-branding
 Try to Re-Instate totem
Investigating totem
Package totem has broken dep on totem-gstreamer
  Considering totem-gstreamer 5 as a solution to totem 5
Package totem has broken dep on totem-xine
  Considering totem-xine 0 as a solution to totem 5
  Or group remove for totem
Package totem has broken dep on totem-plugins
  Considering totem-plugins 5 as a solution to totem 5
  Removing totem rather than change totem-plugins
 Try to Re-Instate libmono-addins-gui0.2-cil
 Try to Re-Instate libwxgtk2.8-0
Investigating ubuntuone-client
Package ubuntuone-client has broken dep on python-ubuntuone-client
  Considering python-ubuntuone-client 1 as a solution to ubuntuone-client 3
  Holding Back ubuntuone-client rather than change python-ubuntuone-client
 Try to Re-Instate gtk2-engines-murrine
Investigating evince-dbg
Package evince-dbg has broken dep on evince
  Considering evince 5 as a solution to evince-dbg 2
  Holding Back evince-dbg rather than change evince
 Try to Re-Instate libwxgtk2.6-0
Investigating anjuta-dbg
Package anjuta-dbg has broken dep on anjuta
  Considering anjuta 0 as a solution to anjuta-dbg 2
  Holding Back anjuta-dbg rather than change anjuta
 Try to Re-Instate libpolkit-gnome0
 Try to Re-Instate libgtkhtml2-0
Investigating gnome-system-tools
Package gnome-system-tools has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-system-tools 2
  Holding Back gnome-system-tools rather than change libgtk2.0-0
 Try to Re-Instate gcalctool
 Try to Re-Instate gnome-nettool
 Try to Re-Instate gucharmap
Investigating ubuntu-artwork
Package ubuntu-artwork has broken dep on light-themes
  Considering light-themes 1 as a solution to ubuntu-artwork 1
  Holding Back ubuntu-artwork rather than change light-themes
 Try to Re-Instate ghostscript-x
 Try to Re-Instate libgtk2.0-dev
 Try to Re-Instate gnome-system-monitor
Investigating gnome-system-monitor
Package gnome-system-monitor has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 5 as a solution to gnome-system-monitor 1
  Removing gnome-system-monitor rather than change libgtkmm-2.4-1c2a
 Try to Re-Instate policykit-gnome
Investigating gvfs-fuse
Package gvfs-fuse has broken dep on gvfs
  Considering gvfs 59 as a solution to gvfs-fuse 0
  Holding Back gvfs-fuse rather than change gvfs
 Try to Re-Instate libxt-java
Investigating nautilus-script-audio-convert
Package nautilus-script-audio-convert has broken dep on nautilus-scripts-manager
  Considering nautilus-scripts-manager 0 as a solution to nautilus-script-audio-convert 0
  Holding Back nautilus-script-audio-convert rather than change nautilus-scripts-manager
 Try to Re-Instate gparted
Investigating gparted
Package gparted has broken dep on libgtkmm-2.4-1c2a
  Considering libgtkmm-2.4-1c2a 5 as a solution to gparted 0
  Removing gparted rather than change libgtkmm-2.4-1c2a
 Try to Re-Instate gnome-mag
Investigating gvfs-bin
Package gvfs-bin has broken dep on gvfs
  Considering gvfs 59 as a solution to gvfs-bin 0
  Holding Back gvfs-bin rather than change gvfs
 Try to Re-Instate vinagre
 Try to Re-Instate firefox-gnome-support
 Try to Re-Instate xchm
 Try to Re-Instate powermanagement-interface
Investigating gvfs-backends
Package gvfs-backends has broken dep on gvfs
  Considering gvfs 59 as a solution to gvfs-backends 0
  Holding Back gvfs-backends rather than change gvfs
 Try to Re-Instate scim-bridge-client-gtk
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 17 as a solution to libgnome-keyring0 119
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
 Try to Re-Instate gvfs
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 3 as a solution to gnome-keyring 17
  Holding Back gnome-keyring rather than change libgcr0
Investigating plymouth
Package plymouth has broken dep on gdm
  Considering gdm 5 as a solution to plymouth 14
  Upgrading gdm due to Breaks field in plymouth
Investigating system-tools-backends
Package system-tools-backends has broken dep on gnome-system-tools
  Considering gnome-system-tools 2 as a solution to system-tools-backends 5
  Upgrading gnome-system-tools due to Breaks field in system-tools-backends
Investigating gdm
Package gdm has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gdm 5
  Holding Back gdm rather than change libbonoboui2-0
Investigating gnome-system-tools
Package gnome-system-tools has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-system-tools 2
  Holding Back gnome-system-tools rather than change libgtk2.0-0
 Try to Re-Instate ubuntu-artwork
 Try to Re-Instate gvfs-fuse
 Try to Re-Instate nautilus-script-audio-convert
 Try to Re-Instate gvfs-backends
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 17 as a solution to libgnome-keyring0 119
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 3 as a solution to gnome-keyring 17
  Holding Back gnome-keyring rather than change libgcr0
Investigating plymouth
Package plymouth has broken dep on gdm
  Considering gdm 5 as a solution to plymouth 14
  Upgrading gdm due to Breaks field in plymouth
Investigating system-tools-backends
Package system-tools-backends has broken dep on gnome-system-tools
  Considering gnome-system-tools 2 as a solution to system-tools-backends 5
  Upgrading gnome-system-tools due to Breaks field in system-tools-backends
Investigating gdm
Package gdm has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gdm 5
  Holding Back gdm rather than change libbonoboui2-0
Investigating gnome-system-tools
Package gnome-system-tools has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-system-tools 2
  Holding Back gnome-system-tools rather than change libgtk2.0-0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 17 as a solution to libgnome-keyring0 119
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 3 as a solution to gnome-keyring 17
  Holding Back gnome-keyring rather than change libgcr0
Investigating plymouth
Package plymouth has broken dep on gdm
  Considering gdm 5 as a solution to plymouth 14
  Upgrading gdm due to Breaks field in plymouth
Investigating system-tools-backends
Package system-tools-backends has broken dep on gnome-system-tools
  Considering gnome-system-tools 2 as a solution to system-tools-backends 5
  Upgrading gnome-system-tools due to Breaks field in system-tools-backends
Investigating gdm
Package gdm has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gdm 5
  Holding Back gdm rather than change libbonoboui2-0
Investigating gnome-system-tools
Package gnome-system-tools has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-system-tools 2
  Holding Back gnome-system-tools rather than change libgtk2.0-0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 17 as a solution to libgnome-keyring0 119
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 3 as a solution to gnome-keyring 17
  Holding Back gnome-keyring rather than change libgcr0
Investigating plymouth
Package plymouth has broken dep on gdm
  Considering gdm 5 as a solution to plymouth 14
  Upgrading gdm due to Breaks field in plymouth
Investigating system-tools-backends
Package system-tools-backends has broken dep on gnome-system-tools
  Considering gnome-system-tools 2 as a solution to system-tools-backends 5
  Upgrading gnome-system-tools due to Breaks field in system-tools-backends
Investigating gdm
Package gdm has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gdm 5
  Holding Back gdm rather than change libbonoboui2-0
Investigating gnome-system-tools
Package gnome-system-tools has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-system-tools 2
  Holding Back gnome-system-tools rather than change libgtk2.0-0
Investigating libgnome-keyring0
Package libgnome-keyring0 has broken dep on gnome-keyring
  Considering gnome-keyring 17 as a solution to libgnome-keyring0 119
  Upgrading gnome-keyring due to Breaks field in libgnome-keyring0
Investigating gnome-keyring
Package gnome-keyring has broken dep on libgcr0
  Considering libgcr0 3 as a solution to gnome-keyring 17
  Holding Back gnome-keyring rather than change libgcr0
Investigating plymouth
Package plymouth has broken dep on gdm
  Considering gdm 5 as a solution to plymouth 14
  Upgrading gdm due to Breaks field in plymouth
Investigating system-tools-backends
Package system-tools-backends has broken dep on gnome-system-tools
  Considering gnome-system-tools 2 as a solution to system-tools-backends 5
  Upgrading gnome-system-tools due to Breaks field in system-tools-backends
Investigating gdm
Package gdm has broken dep on libbonoboui2-0
  Considering libbonoboui2-0 1147 as a solution to gdm 5
  Holding Back gdm rather than change libbonoboui2-0
Investigating gnome-system-tools
Package gnome-system-tools has broken dep on libgtk2.0-0
  Considering libgtk2.0-0 1147 as a solution to gnome-system-tools 2
  Holding Back gnome-system-tools rather than change libgtk2.0-0
Done
Log time: 2011-08-07 17:14:05.043317

```

So... what's the next step?  How do I figure out *what* is causing the upgrade to fall over?

Thanks in advance for the help!

---

### Post by mörgæs on 2011-08-09
I can not say why the upgrade fails, but it is a common experience. 

Since you have 8.04, you use ext3 as the file system. I would recommend a fresh install of a new Ubuntu release, which will also give you the option of switching to ext4.

---

### Post by poptoppop on 2011-08-09
> **mörgæs said:**
> Since you have 8.04, you use ext3 as the file system. I would recommend a fresh install of a new Ubuntu release, which will also give you the option of switching to ext4.
Ugh, but thanks for the reply :).

I dread the words "fresh install," but since we're on the subject is there a guide somewhere that I can follow to walk myself through that process? This is a personal server so it's not business-critical, but because it's a hobby thing I don't have a week to invest redoing everything if it goes badly.

---

### Post by poptoppop on 2011-08-09
> **mörgæs said:**
> Since you have 8.04, you use ext3 as the file system. I would recommend a fresh install of a new Ubuntu release, which will also give you the option of switching to ext4.
Sorry for the double-reply, but what would be the reason for switching to ext4? I'm perfectly happy with the system I've got -- I'd just like to stay on a supported system and my understanding is that 8.04 has dropped off the support calendar.  Thanks!

---

### Post by mörgæs on 2011-08-09
Hope this helps:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Regarding ext3 and 4 I guess that best is to search here:
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

The question comes up from time to time, and the threads tend to get moved into Recurring.

---

