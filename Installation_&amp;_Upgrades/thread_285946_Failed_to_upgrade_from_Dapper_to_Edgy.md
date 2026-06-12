---
title: "Failed to upgrade from Dapper to Edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by alex1973 on 2006-10-27
I have tried to upgrade using the instructions provided at [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

It failed shortly after it finished downloading the new packages. Here are the logs:
main.log

```
2006-10-27 09:56:09,336 DEBUG Foreign: poppler-utils libxss1 libglitz1 realplay libpoppler1-glib libtunepimp2c2a libxfixes-dev libgl1-mesa libglu1-mesa x11proto-fixes-dev libwnck-common listen libgl1-mesa-dri libxfixes3 libdrm2 libxcomposite1 libpoppler1 libwnck18 libpoppler1-qt xserver-xorg-driver-i810 opera gnome-main-menu picasa mesa-utils gcontrol wine
2006-10-27 09:56:09,337 DEBUG Obsolete: libdivxencore0-binary fglrx-kernel-source libguicast fglrx-kernel-2.6.15-27-686 libfaac0 libdivx0-binary libraw1394-8 skype xorg-driver-fglrx libdvdcss2 hot-babe libmpeg3hv fglrx-control libfaad2-0 libdivxdecore0-binary libiec61883-0 beep-media-player-wma cinelerra automatix fglrx-kernel-2.6.15-26-686 libquicktimehv grub-gfxboot bmp-docklet
2006-10-27 09:56:09,338 DEBUG updateSourcesList()
2006-10-27 09:56:09,420 DEBUG rewriteSourcesList()
2006-10-27 09:56:09,849 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper main'
2006-10-27 09:56:09,849 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy main' updated to new dist
2006-10-27 09:56:09,849 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper restricted'
2006-10-27 09:56:09,849 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy restricted' updated to new dist
2006-10-27 09:56:09,849 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper universe'
2006-10-27 09:56:09,850 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy universe' updated to new dist
2006-10-27 09:56:09,850 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe restricted main'
2006-10-27 09:56:09,850 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu/ edgy multiverse universe restricted main' updated to new dist
2006-10-27 09:56:09,850 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper multiverse'
2006-10-27 09:56:09,850 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy multiverse' updated to new dist
2006-10-27 09:56:09,850 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-security main'
2006-10-27 09:56:09,850 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-security main' updated to new dist
2006-10-27 09:56:09,850 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper-security main'
2006-10-27 09:56:09,851 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy-security main' updated to new dist
2006-10-27 09:56:09,851 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-security restricted'
2006-10-27 09:56:09,851 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-security restricted' updated to new dist
2006-10-27 09:56:09,851 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted'
2006-10-27 09:56:09,851 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy-security restricted' updated to new dist
2006-10-27 09:56:09,851 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-security universe'
2006-10-27 09:56:09,851 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-security universe' updated to new dist
2006-10-27 09:56:09,852 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper-security universe'
2006-10-27 09:56:09,852 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy-security universe' updated to new dist
2006-10-27 09:56:09,852 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-security multiverse'
2006-10-27 09:56:09,852 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-security multiverse' updated to new dist
2006-10-27 09:56:09,852 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse'
2006-10-27 09:56:09,852 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy-security multiverse' updated to new dist
2006-10-27 09:56:09,852 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-updates main'
2006-10-27 09:56:09,852 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-updates main' updated to new dist
2006-10-27 09:56:09,852 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper-updates main'
2006-10-27 09:56:09,853 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy-updates main' updated to new dist
2006-10-27 09:56:09,853 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-updates restricted'
2006-10-27 09:56:09,853 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-updates restricted' updated to new dist
2006-10-27 09:56:09,853 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted'
2006-10-27 09:56:09,853 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy-updates restricted' updated to new dist
2006-10-27 09:56:09,853 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-updates universe'
2006-10-27 09:56:09,853 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-updates universe' updated to new dist
2006-10-27 09:56:09,854 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe'
2006-10-27 09:56:09,854 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy-updates universe' updated to new dist
2006-10-27 09:56:09,854 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse'
2006-10-27 09:56:09,854 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu edgy-updates multiverse' updated to new dist
2006-10-27 09:56:09,854 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse'
2006-10-27 09:56:09,854 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu edgy-updates multiverse' updated to new dist
2006-10-27 09:56:09,854 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse'
2006-10-27 09:56:09,854 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse' updated to new dist
2006-10-27 09:56:09,854 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse'
2006-10-27 09:56:09,855 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse' updated to new dist
2006-10-27 09:56:09,855 DEBUG examining: 'deb http://archive.canonical.com/ubuntu dapper-commercial main'
2006-10-27 09:56:09,856 DEBUG entry '# deb http://archive.canonical.com/ubuntu dapper-commercial main' was disabled (unknown mirror)
2006-10-27 09:56:09,856 DEBUG examining: 'deb http://ubuntu.geole.info/ dapper universe multiverse'
2006-10-27 09:56:09,857 DEBUG entry '# deb http://ubuntu.geole.info/ dapper universe multiverse' was disabled (unknown mirror)
2006-10-27 09:56:09,857 DEBUG examining: 'deb-src http://ubuntu.geole.info/ dapper universe multiverse'
2006-10-27 09:56:09,858 DEBUG entry '# deb-src http://ubuntu.geole.info/ dapper universe multiverse' was disabled (unknown mirror)
2006-10-27 09:56:09,859 DEBUG examining: 'deb http://www.getautomatix.com/apt dapper main'
2006-10-27 09:56:09,860 DEBUG entry '# deb http://www.getautomatix.com/apt dapper main' was disabled (unknown mirror)
2006-10-27 09:56:09,860 DEBUG examining: 'deb http://wine.lowvoice.nl/apt dapper main'
2006-10-27 09:56:09,861 DEBUG entry '# deb http://wine.lowvoice.nl/apt dapper main' was disabled (unknown mirror)
2006-10-27 09:56:09,861 DEBUG examining: 'deb http://theli.free.fr/packages/ dapper listen'
2006-10-27 09:56:09,862 DEBUG entry '# deb http://theli.free.fr/packages/ dapper listen' was disabled (unknown mirror)
2006-10-27 09:56:09,862 DEBUG examining: 'deb http://dl.google.com/linux/deb/ stable non-free'
2006-10-27 09:56:09,864 DEBUG entry '# deb http://dl.google.com/linux/deb/ stable non-free' was disabled (unknown mirror)
2006-10-27 09:56:09,864 DEBUG examining: 'deb http://www.beerorkid.com/compiz/ dapper main'
2006-10-27 09:56:09,865 DEBUG entry '# deb http://www.beerorkid.com/compiz/ dapper main' was disabled (unknown mirror)
2006-10-27 09:58:07,407 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2006-10-27 09:58:07,408 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2006-10-27 09:58:07,408 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2006-10-27 09:58:07,410 DEBUG running edgyQuirks handler
2006-10-27 09:58:07,415 DEBUG Installing 'python-tk' (python2.4->python upgrade rule)
2006-10-27 09:58:07,465 DEBUG Installing 'python-pycurl' (python2.4->python upgrade rule)
2006-10-27 09:58:07,467 DEBUG Installing 'python-qt3' (python2.4->python upgrade rule)
2006-10-27 09:58:07,512 DEBUG Failed to apply python2.4->python install: python-qt3 (E:Unable to correct problems, you have held broken packages.)
2006-10-27 09:58:07,513 DEBUG Installing 'python-sqlite' (python2.4->python upgrade rule)
2006-10-27 09:58:07,559 DEBUG Installing 'python-egenix-mxtexttools' (python2.4->python upgrade rule)
2006-10-27 09:58:07,560 DEBUG Installing 'python-ldap' (python2.4->python upgrade rule)
2006-10-27 09:58:07,565 DEBUG Installing 'python-pysqlite2' (python2.4->python upgrade rule)
2006-10-27 09:58:07,565 DEBUG Installing 'xserver-xorg-input-mouse' (xserver-xorg-input fixup rule)
2006-10-27 09:58:07,567 DEBUG Installing 'xserver-xorg-input-synaptics' (xserver-xorg-input fixup rule)
2006-10-27 09:58:07,573 DEBUG Installing 'python-clientcookie' (python2.4->python upgrade rule)
2006-10-27 09:58:07,577 DEBUG Installing 'python-soappy' (python2.4->python upgrade rule)
2006-10-27 09:58:07,577 DEBUG Installing 'python-xmpp' (python2.4->python upgrade rule)
2006-10-27 09:58:07,578 DEBUG Installing 'python-gadfly' (python2.4->python upgrade rule)
2006-10-27 09:58:07,580 DEBUG Installing 'python-reportlab' (python2.4->python upgrade rule)
2006-10-27 09:58:07,581 DEBUG Installing 'python-jabber' (python2.4->python upgrade rule)
2006-10-27 09:58:07,582 DEBUG Installing 'python-pylibacl' (python2.4->python upgrade rule)
2006-10-27 09:58:07,583 DEBUG Installing 'python-syck' (python2.4->python upgrade rule)
2006-10-27 09:58:07,584 DEBUG Installing 'python-ctypes' (python2.4->python upgrade rule)
2006-10-27 09:58:07,585 DEBUG Installing 'python-gtk2' (python2.4->python upgrade rule)
2006-10-27 09:58:07,586 DEBUG Installing 'python-kde3' (python2.4->python upgrade rule)
2006-10-27 09:58:07,587 DEBUG Installing 'python-unit' (python2.4->python upgrade rule)
2006-10-27 09:58:07,587 DEBUG Installing 'python-geoip' (python2.4->python upgrade rule)
2006-10-27 09:58:07,589 DEBUG Installing 'python-kjbuckets' (python2.4->python upgrade rule)
2006-10-27 09:58:07,591 DEBUG Installing 'python-id3lib' (python2.4->python upgrade rule)
2006-10-27 09:58:07,592 DEBUG Installing 'python-crypto' (python2.4->python upgrade rule)
2006-10-27 09:58:07,595 DEBUG Installing 'python-eunuchs' (python2.4->python upgrade rule)
2006-10-27 09:58:07,599 DEBUG Installing 'python-libxml2' (python2.4->python upgrade rule)
2006-10-27 09:58:07,600 DEBUG Installing 'python-glade2' (python2.4->python upgrade rule)
2006-10-27 09:58:07,601 DEBUG Installing 'python-pyxattr' (python2.4->python upgrade rule)
2006-10-27 09:58:07,602 DEBUG Installing 'python-imaging-sane' (python2.4->python upgrade rule)
2006-10-27 09:58:07,604 DEBUG Installing 'python-pyorbit' (python2.4->python upgrade rule)
2006-10-27 09:58:07,605 DEBUG Installing 'python-gdbm' (python2.4->python upgrade rule)
2006-10-27 09:58:07,608 DEBUG Installing 'python-pgsql' (python2.4->python upgrade rule)
2006-10-27 09:58:07,611 DEBUG Installing 'python-apt' (python2.4->python upgrade rule)
2006-10-27 09:58:07,611 DEBUG Installing 'python-pyopenssl' (python2.4->python upgrade rule)
2006-10-27 09:58:07,613 DEBUG Installing 'python-numeric' (python2.4->python upgrade rule)
2006-10-27 09:58:07,614 DEBUG Installing 'python-htmlgen' (python2.4->python upgrade rule)
2006-10-27 09:58:07,615 DEBUG Installing 'python-egenix-mxtools' (python2.4->python upgrade rule)
2006-10-27 09:58:07,615 DEBUG Installing 'xserver-xorg-input-kbd' (xserver-xorg-input fixup rule)
2006-10-27 09:58:07,616 DEBUG Installing 'python-simpletal' (python2.4->python upgrade rule)
2006-10-27 09:58:07,617 DEBUG Installing 'python-libbtctl' (python2.4->python upgrade rule)
2006-10-27 09:58:07,621 DEBUG Installing 'python-pymad' (python2.4->python upgrade rule)
2006-10-27 09:58:07,623 DEBUG Installing 'python-pexpect' (python2.4->python upgrade rule)
2006-10-27 09:58:07,624 DEBUG Installing 'python-libxslt1' (python2.4->python upgrade rule)
2006-10-27 09:58:07,626 DEBUG Installing 'python-egenix-mxproxy' (python2.4->python upgrade rule)
2006-10-27 09:58:07,627 DEBUG Installing 'python-htmltmpl' (python2.4->python upgrade rule)
2006-10-27 09:58:07,628 DEBUG Installing 'python-egenix-mxstack' (python2.4->python upgrade rule)
2006-10-27 09:58:07,629 DEBUG Installing 'python-pam' (python2.4->python upgrade rule)
2006-10-27 09:58:07,630 DEBUG Installing 'python-mysqldb' (python2.4->python upgrade rule)
2006-10-27 09:58:07,631 DEBUG Installing 'python-gd' (python2.4->python upgrade rule)
2006-10-27 09:58:07,633 DEBUG Installing 'python-imaging' (python2.4->python upgrade rule)
2006-10-27 09:58:07,635 DEBUG Installing 'xserver-xorg-input-evdev' (xserver-xorg-input fixup rule)
2006-10-27 09:58:07,636 DEBUG Installing 'python-xml' (python2.4->python upgrade rule)
2006-10-27 09:58:07,637 DEBUG Installing 'python-gnome2-extras' (python2.4->python upgrade rule)
2006-10-27 09:58:07,637 DEBUG Installing 'xserver-xorg-input-elographics' (xserver-xorg-input fixup rule)
2006-10-27 09:58:07,638 DEBUG Installing 'python-epydoc' (python2.4->python upgrade rule)
2006-10-27 09:58:07,640 DEBUG Installing 'python-adns' (python2.4->python upgrade rule)
2006-10-27 09:58:07,642 DEBUG Installing 'python-gnome2-desktop' (python2.4->python upgrade rule)
2006-10-27 09:58:07,642 DEBUG Installing 'python-gnome2' (python2.4->python upgrade rule)
2006-10-27 09:58:07,647 INFO Forcing downgrade of libgl1-mesa-dri for xgl.compz.info installs
2006-10-27 09:58:07,692 DEBUG Marking 'ubuntu-desktop' for upgrade
2006-10-27 09:58:07,737 DEBUG Marking 'kubuntu-desktop' for upgrade
2006-10-27 09:58:08,533 DEBUG About to apply the following changes
2006-10-27 09:58:08,691 DEBUG Held-back: listen libggi2 mplayer
2006-10-27 09:58:08,692 DEBUG Remove: python2.4-tk python2.4-pycurl xserver-xorg-driver-tga python2.4-qt3 xserver-xorg-driver-chips python2.4-sqlite fglrx-kernel-2.6.15-27-686 xserver-xorg-driver-trident xserver-xorg-driver-siliconmotion python2.4-egenix-mxtexttools x-window-system-core kdelibs-bin python2.4-ldap xserver-xorg-driver-mga libnewt0.51 xserver-xorg-driver-tseng xserver-xorg-driver-nv python2.4-pysqlite2 xorg-driver-fglrx sysvinit libvte4 python2.4-clientcookie xserver-xorg-driver-via xserver-xorg-driver-i128 xserver-xorg-driver-i740 makedepend xserver-xorg-driver-vga python2.4-soappy python2.4-xmpp python2.4-gadfly xserver-xorg-driver-nsc xserver-xorg-driver-voodoo xorg-edit python2.4-reportlab xserver-xorg-driver-all python2.4-jabber python2.4-pylibacl python2.4-syck python2.4-ctypes hplip-ppds python2.4-gtk2 python2.4-kde3 xserver-xorg-driver-s3virge fglrx-kernel-2.6.15-26-686 python2.4-gobject python2.4-kjbuckets imake xserver-xorg-driver-ati python2.4-crypto xserver-xorg-driver-sisusb xserver-xorg-driver-i810 xserver-xorg-driver-cirrus xserver-xorg-driver-sis xserver-xorg-driver-newport python2.4-libxml2 python2.4-glade2 python2.4-cairo python2.4-pyxattr libxklavier10 python2.4-imaging-sane python2.4-pyorbit linux-kernel-headers python2.4-gdbm xserver-xorg-driver-apm python2.4-pgsql xserver-xorg-driver-s3 xserver-xorg-driver-rendition python2.4-apt python2.4-pyopenssl xserver-xorg-driver-v4l python2.4-numeric xserver-xorg-driver-glint python2.4-htmlgen python2.4-egenix-mxtools python2.4-sip4-qt3 python2.4-simpletal python2.4-libbtctl python2.4-dbus xserver-xorg-driver-imstt python2.4-pymad python2.4-pexpect python2.4-libxslt1 libgtk-pixbuf-perl python2.4-egenix-mxproxy python2.4-htmltmpl python2.4-egenix-mxstack python2.4-pam python2.4-mysqldb libgcj7 xserver-xorg-driver-cyrix python2.4-egenix-mxdatetime xserver-xorg-driver-tdfx foomatic-filters-ppds xserver-xorg-driver-vesa python2.4-imaging libgl1-mesa xserver-xorg-driver-ark python2.4-xml python2.4-gnome2-extras xserver-xorg-driver-savage python2.4-adns xserver-xorg-driver-neomagic python2.4-gnome2-desktop python2.4-gnome2 xserver-xorg-driver-vmware xserver-xorg-driver-dummy xserver-xorg-driver-fbdev fglrx-control
2006-10-27 09:58:08,692 DEBUG Install: libevent-execflow-perl linux-libc-dev resilience-theme kipi-plugins binfmt-support python-gobject linux-image-2.6.17-10-386 libmyspell3c2 outdoors-theme libmikmod2 libavformat0d xserver-xorg-video-cyrix xserver-xorg-video-rendition libavcodec0d xserver-xorg-video-vesa xserver-xorg-video-s3 cli-common libqt4-sql xserver-xorg-video-sis libqt4-gui lsdvd libmono-system1.0-cil liblualib50 xserver-xorg-video-i810 system-services libcairo-perl libgtk2.0-cil adept-updater python-elementtree volumeid xserver-xorg-video-imstt libexif-dev libmono-system-data1.0-cil util-linux-locales libegroupwise1.2-12 xserver-xorg-video-chips libgksu2-0 libgnutls13 dpatch libparted1.7-1 human-icon-theme adept-notifier upstart libedataserverui1.2-8 g++-4.1 xserver-xorg-video-vga libnet-dbus-perl libgcj7-0 libdbus-1-3 libavahi-core4 libgmime-2.0-2 cpp-4.1 tasksel-data libmono-sqlite1.0-cil libmono-system-web1.0-cil libdirectfb-0.9-24 libavahi-compat-libdnssd1 gtk2-engines libhtml-tagset-perl libxine1 libgmime2.2-cil libbtctl4 libglib2.0-cil mono-common python-gconf acroread-escript libopenobex1 xserver-xorg-video-i740 python-support edgy-session-splashes python-egenix-mxdatetime edgy-community-wallpapers libqt4-core libpci2 edgy-wallpapers xserver-xorg-video-tdfx libhtml-parser-perl industrialtango-theme libwww-perl linux-image-2.6.17-10-generic xserver-xorg-video-mga xbitmaps tasksel hwdb-client-kde xserver-xorg-video-savage gray-theme gtk2-ex-formfactory-perl upstart-logd totem-mozilla hwdb-client-gnome libebook1.2-9 console-setup xserver-xorg-video-via apt-index-watcher xutils-dev xtrans-dev libgnokii3 apport xserver-xorg-video-s3virge tzdata libg2c0 adept-manager libmono-cairo1.0-cil xserver-xorg-video-neomagic kde-guidance-powermanager libhtml-tree-perl xserver-xorg-video-glint liburi-perl libsdl-image1.2 python-scientific xkb-data gnome-media-common libxml-parser-perl python-gnomecanvas libmozjs0d xserver-xorg-video-sisusb edgy-gdm-themes apport-gtk libgnome2.0-cil mktemp libwxbase2.6-0 libstdc++6-4.1-dev python-ctypes libvolumeid0 libcairo-ruby1.8 xserver-xorg-video-i128 python-libbtctl mono-gac libxevie1 xserver-xorg-video-voodoo python-gtkhtml2 usplash-theme-ubuntu libgucharmap5 python-apport-utils digikam vlc-nox openoffice.org-style-default xserver-xorg-video-nv libgphoto2-2-dev xserver-xorg-video-siliconmotion liboobs-1-2 human-theme libecal1.2-7 libqt4-qt3support python-pycurl libdb4.4 avahi-daemon xserver-xorg-video-vmware xserver-xorg-video-trident gnome-keyring-manager libtasn1-3 openoffice.org-style-crystal refblas3 upstart-compat-sysv dash libxklavier11 libgconf2.0-cil libxml-grove-perl libiodbc2 python-pymad openoffice.org-style-industrial metacity-common libpostproc0d python-pysqlite2 xserver-xorg-video-all cupsys-common python-central libdbus-1-cil mono-jit xserver-xorg-video-dummy liblua50 libvlc0 adept-common libgsf-1-114 xfonts-encodings python-sip4 linux-generic python-problem-report gcc-4.1 libbluetooth2 libmono0 xserver-xorg-video-apm libgail18 hwdb-client-common python-numeric-ext python-qt4 libgnome-window-settings1 libqt3-mt-odbc adept-installer xserver-xorg-video-tseng sysvutils xserver-xorg-video-ark adept-batch gcc-3.4-base mono-runtime legacyhuman-theme linux-restricted-modules-2.6.17-10-386 xserver-xorg-video-ati xserver-xorg-video-tga linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-generic xserver-xorg-video-newport f-spot libmono-security1.0-cil python-cairo libxml-perl xserver-xorg-video-v4l libdaemon0 xserver-xorg-video-nsc libgl1-mesa-glx libnautilus-burn4 xserver-xorg-video-cirrus libenchant1c2a xorg fontconfig-config libnjb5 human-gtk-theme libmono-sharpzip0.84-cil libvte9 python-dbus gocr linux-image-generic libmagick++9c2a human-cursors-theme libexchange-storage1.2-2 lapack3 libgtop2-common libnetpbm10 gcc-4.1-base libedata-cal1.2-6 python-libxslt1 silicon-theme tomboy libmono-corlib1.0-cil libglade2.0-cil libkexif1 libmono1.0-cil libmono-data-tds1.0-cil vim-tiny evolution-data-server-common xserver-xorg-video-fbdev libmeanwhile1 libgnome-media0 dcraw libnspr4-0d anyevent-perl libnewt0.52 startup-tasks libevent-rpc-perl libx11-data libpisock9 industrial-cursor-theme
2006-10-27 09:58:08,692 DEBUG Upgrade: ttf-devanagari-fonts beep-media-player-dev libcairo-ruby gnome-power-manager file-roller doc-base irda-utils pmount libapr0 kscreensaver x11-common tsclient libmetacity0 python-egenix-mxtexttools makedev libxtrap6 libcupsimage2 libnetcdf3 coreutils whiptail python libgconf2-ruby libbz2-1.0 libklibc libc6 laptop-mode-tools ubuntu-docs libscim8c2a libsane x11perf libfreetype6 gstreamer0.8-a52dec python-sqlite gsfonts-x11 bittorrent openobex-apps menu kdebase-data ttf-larabie-uncommon sun-java5-jre login zlib1g-dev udev gnome-utils hotkey-setup hal linux-image-386 language-selector-qt sysklogd xfonts-base liblame0 libkipi0 libsdl1.2debian libxfixes-dev gcc-4.0-base libxinerama1 libxaw7 libsysfs2 php5-mysql ksystemlog gimp-python libxrender1 libxcomposite1 libijs-0.35 gnome-about gstreamer0.10-tools gtkhtml3.8 konqueror-nsplugins libss2 fstobdf libapm1 libpam-runtime kino e2fslibs cdda2wav libpango1.0-common gstreamer0.10-plugins-base xbase-clients libgnomecanvas2-0 libkrb53 libltdl3 cupsys-driver-gutenprint kmailcvt logrotate base-files kdeprint libevms-2.5 x11proto-trap-dev tcpd ttf-bitstream-vera kubuntu-docs evms-ncurses ubuntu-standard libgtk2.0-bin libsnmp9 libffi4 libpythonize0 libexpat1 debhelper iproute libnautilus-extension1 libpng12-dev libdns21 libgnome-mag2 gtk2-engines-clearlooks lvm-common libestools1.2 adept libatspi1.0-0 gconf2-common libxvidcore4 java-gcj-compat openoffice.org-kde gnome-applets-data libstdc++5 ttf-kochi-mincho libstdc++6 wxvlc manpages python-geoip libpt-plugins-alsa gdb libxxf86misc1 xsane-common gdm poppler-utils libbonobo2-0 libxau6 libdv4 kdnssd libselinux1 ttf-kochi-gothic pcmciautils python-pqueue kdm libgutenprint2 gedit-common cdrdao ncurses-bin at samba-common libuuid1 python-eunuchs e2fsprogs cpp libjline-java python-kjbuckets openoffice.org-l10n-common vim dvdrip powernowd libssl0.9.8 libgstreamer-plugins-base0.10-0 libdmx1 libice6 sun-java5-bin x11proto-core-dev libpt-plugins-v4l libatk1-ruby vlc sysv-rc unixodbc gnome2-user-guide system-tools-backends python-crypto kdegraphics-kfile-plugins readahead apmd libglib2.0-dev libkleopatra1 linux-restricted-modules-686 libgpod0 lvm2 gnome-applets amsn openoffice.org-java-common xserver-xorg-input-wacom libisccfg1 cron libk3b2 liblcms1 kdepim-kresources python2.4-examples wireless-tools libc6-dev vim-runtime wpasupplicant python-pyorbit libgnutls12 libgnomevfs2-extra sed libgnome-desktop-2 gtk2-engines-smooth kterm libeel2-2 imagemagick binutils build-essential foomatic-db python-minimal metacity libungif4g tango-icon-theme-common bluez-cups popularity-contest console-terminus bind9-host gstreamer0.10-plugins-bad-multiverse libkmime2 wget gwenview example-content libgmp3c2 libpcre3 poster libxv-dev kdebluetooth libgdbm3 libtheora0 gnome-cups-manager gtk2-engines-thinice unzip libiec61883-0 libpopt0 gstreamer0.10-esd mysql-server-5.0 gnome-nettool libpango1.0-dev bogofilter pykdeextensions libao2 nautilus-data python-gadfly firefox gcalctool zip debconf-i18n libbonoboui2-common zlib1g xserver-xorg-input-mouse belocs-locales-bin xserver-xorg-input-synaptics gnome-games-data libgtk2.0-common alsa-oss lame libxtst6 alsa-base libxtrap-dev myspell-en-gb kpf libgd2-noxpm foomatic-db-gutenprint patch x11proto-xinerama-dev pcmcia-cs busybox-initramfs python-mysqldb initscripts python-pyogg kpdf kfind hdparm libatk1.0-dev libsasl2-modules python-gtk2 libktnef1 libpq4 gnome-libs-data pnm2ppa libdiscover1 libpng12-0 libgnome-menu2 gnome-terminal libbrlapi1 python-cddb ucf libxmuu-dev gnome-bin sun-java5-plugin ttf-gujarati-fonts libgda2-3 language-selector-common gnome-menus libxml2 libxml1 konq-plugins php5-common vim-common xev konqueror kmobiletools dvd+rw-tools module-assistant dmidecode libifp4 kde-systemsettings python-soappy network-manager kmix kooka kinoplus libgnome2-perl libatk1.0-0 bzip2 libx11-6 kubuntu-desktop memtest86+ eog ttf-lao libavahi-common3 gtk2-engines-ubuntulooks xsltproc acpi-support xfonts-75dpi libxt-java libkcal2b libxfont1 libxrandr-dev katapult libqt3-mt cdparanoia libxml2-utils xkbutils python-simpletal libxxf86dga1 libjpeg-progs libxine-extracodecs iputils-arping mysql-server libuniconf4.2 libice-dev gnome-mime-data libgimp2.0 totem libavahi-qt3-1 libqthreads-12 libglib2-ruby kaudiocreator ntp fping gnome-media openoffice.org-l10n-en-za libsm-dev ttf-larabie-deco libopenobex-1.0-0 libsdl1.2debian-alsa kaddressbook iputils-ping libvcdinfo0 mozilla-mplayer vlc-plugin-alsa gzip libxrandr2 findutils apache2-common libzvt2 libcurl3-gnutls libdbi-perl launchpad-integration kwalletmanager apache2-utils mozilla-thunderbird mdadm gettext-base kmilo libavc1394-0 x11proto-fixes-dev vlc-plugin-esd libgnomecanvas2-common mencoder libfontconfig1-dev libgadu3 libdc1394-13 toolame linux-sound-base module-init-tools python-clientcookie python2.4-librdf python-qt3 gstreamer0.10-plugins-ugly libidl0 libxext-dev gtk2-engines-pixbuf evolution-webcal libmagic1 tcpdump python-gnome2 gstreamer0.10-plugins-ugly-multiverse libxres1 libgcc1 libruby1.8 bogofilter-common libgksu1.2-1 liblockdev1 libnotify1 make libgnomeui32 kmplayer-base gawk bluez-pcmcia-support libwxgtk2.6-0 amarok-xine bug-buddy gstreamer0.10-ffmpeg gcc-3.3-base ksnapshot linux-386 vcdimager gconf2 gnome-btdownload bicyclerepair brltty dmsetup python-imaging hostname language-pack-gnome-en-base libvisual-0.4-0 libgnomebt0 linux-restricted-modules-386 libcurl3 ekiga libnss3 docbook-xml libgdl-1-common libpango1-ruby x-ttcidfont-conf openoffice.org-base libsnmp-base konsole libedataserver1.2-7 libdvbpsi4 libxvmc1 transcode python-ldap libdevmapper1.02 gnome-panel-data libisccc0 python-examples libgtk2-perl nvidia-kernel-common libbind9-0 fluxbox dhcdbd kdenetwork-kfile-plugins zenity libwvstreams4.2-base pptp-linux libblkid1 libexpat1-dev x11proto-xext-dev xcdroast vlc-plugin-arts libopal-2.2.0 libsqlite3-0 evms libgphoto2-port0 libhal1 python-vte libedata-book1.2-2 liblircclient0 vnc-common java-common ttf-arabeyes kdebase-kio-plugins xserver-xorg multisync nano klogd dnsutils gcc capplets-data xdriinfo xserver-xorg-input-all xfonts-100dpi nautilus camorama libxine-main1 acroread libxau-dev libiw28 libsmjs1 python-egenix-mxstack openoffice.org-l10n-en-us ttf-larabie-straight scmxx libgnorbagtk0 evolution-exchange libgtksourceview-common kwin-style-crystal libmimelib1c2a libxpm-dev bash xutils guile-1.6-libs fftw3 libcairo2 python-pyao grep ffmpeg reportbug gedit karm libgutenprintui2-1 imlib11 libgtk2.0-dev ssh-askpass-gnome python-gnupginterface less freeglut3 kdepim-wizards python-pyopenssl python-egenix-mxproxy libcamel1.2-8 libmusicbrainz4c2a libpcap0.8 libgsf-1-common korganizer klaptopdaemon gimp libkjsembed1 xterm libgnome2-0 python-jabber libnm-util0 perl-suid libxt-dev info kdepim-kio-plugins anacron libcdparanoia0 kate cpio hplip-data fastjar libxmu-headers libjaxp1.2-java libwnck-common liborbit2 alsa-utils gnome-themes sudo libxv1 libasound2 libgphoto2-2 kghostview fglrx-kernel-source netcat klibc-utils libhal-storage1 ncurses-term kio-apt acpid liblockfile1 gnome-phone-manager gimp-data libgamin0 gstreamer0.10-gl python-pylibacl gdebi libgcrypt11 eterm adduser keep kcontrol lshw libgpg-error0 gtk2-engines-mist python-xmpp gcj-4.1-base kdelibs4c2a xfonts-terminus kaffeine ruby1.8 libkcddb1 subtitleripper libxxf86vm1 bluez-utils x11proto-render-dev libwmf0.2-7 kubuntu-default-settings evolution kdenetwork-filesharing libwvstreams4.2-extras ubuntu-minimal ksmserver kdelibs-data ntp-simple gij-4.1 reiserfsprogs libpoppler1 python-pyvorbis libxmlsec1-openssl language-pack-en gnome-games pdmenu libgc1c2 g++-4.0 gksu gnome-app-install libsm6 libjessie-java scim-gtk2-immodule xset python-kde3 libbonobo2-common python-gmenu fdutils brltty-x11 koffice-data festival python-tk libgtk-perl libplrpc-perl python-pexpect gnome-desktop-data scim-modules-socket libusb-0.1-4 ttf-opensymbol libgnome2-common ksysguardd python2.4-minimal libvorbis0a kontact libvte-common libtext-wrapi18n-perl librdf0 gnupg knotes x11proto-kb-dev gstreamer0.10-gnomevfs deskbar-applet console-common libgeoip1 gnome-system-monitor linux-restricted-modules-common libwrap0 libtext-charwidth-perl x-dev libidn11 gstreamer0.10-plugins-base-apps gtk2-engines-gtk-qt libgnome-keyring0 python2.4-dev kicker xcursorgen gnome-terminal-data libfontenc1 libgnomeprintui2.2-0 libcairo2-dev python-egenix-mxtools khelpcenter libavahi-common-data libpisync0 gnome-doc-utils mozilla-acroread gdesklets foomatic-filters cpp-4.0 liblwres9 python-gnome2-extras libgnomecupsui1.0-1c2a libcomerr2 evolution-data-server speedcrunch foomatic-db-hpijs imlib-base mtr-tiny kdebase-bin gnome-splashscreen-manager beep-media-player kwin hpijs ttf-tamil-fonts libglade2-ruby libisc11 libapache2-mod-php5 libdbd-mysql-perl skim libfribidi0 gnome-control-center libwxgtk2.4-1 xfonts-scalable dbus-1-utils contact-lookup-applet kamera libxmlsec1-nss libsmbclient perl xcursor-themes libtasn1-2 libtotem-plparser1 kubuntu-artwork-usplash libgda2-common sun-java5-jdk kmplayer-konq-plugins libgcj-common libkscan1 libnet-daemon-perl kdesktop libfontconfig1 libwpd8c2a libconsole xmodmap xtrap libmng1 libimlib2 libgnomesupport0 gnome-ppp xprop multitail libldap2 kscd k3b libelfg0 libx11-dev vorbis-tools libncurses5 util-linux x11proto-input-dev python-pyxattr libgnomeui-common gstreamer0.8-mpeg2dec kaffeine-xine kdemultimedia-kfile-plugins libxslt1.1 procps libaspell15 koffice-libs mii-diag whois ttf-punjabi-fonts toshset libxmu6 python-uno xlibs-dev librsvg2-common lsb-release arts irssi notification-daemon libglib2.0-data kmail kopete libcompfaceg1 konversation libxosd2 gstreamer0.10-pitfdll libxmlsec1 openoffice.org-calc libtagc0 python-imaging-sane libgcj7-jar openoffice.org-math python-htmltmpl bluez-pin p7zip python-xdg gconf-editor libgdk-pixbuf2-ruby avidemux pciutils ttf-dejavu gnome-bluetooth python-gdbm gdk-imlib11 libdbus-glib-1-2 libgail-common kdeadmin-kfile-plugins libxalan2-java unattended-upgrades enscript libxcursor1 libxp6 libarts1-akode audacity libpaper1 rss-glx net-tools python-unit openssh-client libart2 tk8.4 passwd desktop-file-utils xinit gnokii fontconfig gnome-pilot-conduits python-htmlgen qobex mime-support xrdb libaudio2 xfsprogs xserver-xorg-core liboggflac3 openoffice.org-core eject libksieve0 klipper serpentine python-pgsql debconf-utils libxext6 debtags krdc iputils-tracepath xxdiff xhost wlassistant openoffice.org-impress libakode2 gtk2-engines-industrial gnome-panel libgail-gnome-module dhcp3-client gnome-volume-manager language-pack-en-base ttf-kannada-fonts gthumb libbonoboui2-0 xfonts-intl-european libfs6 libtiff4 libssl0.9.7 libmms0 lftp menu-xdg mysql-common libc6-i686 libgsl0 xserver-xorg-input-kbd libbogl0 python2.4 ttf-oriya-fonts libstdc++6-4.0-dev liba52-0.7.4 gcc-4.0 network-manager-gnome iptables bitmap libgtop2-7 libgconf2-4 hal-device-manager python-glade2 gtk2-engines-lighthouseblue ttf-gentium libgnomevfs2-0 openoffice.org-evolution libxfixes3 gtk2-engines-crux synaptic libxt6 dbus krita aterm libswfdec0.3 libgstreamer0.10-0 libavifile-0.7c2 krfb dselect python-genetic mawk libkpimidentities1 python-adns libxi6 groff-base psutils ncurses-base streamripper xscreensaver-data sound-juicer nautilus-sendto libbogl-dev strace debianutils ksvg kio-locate libglib-perl libgnomevfs2-common libxdmcp-dev gnome-icon-theme debconf bsdmainutils libsexy2 x11proto-video-dev libslang2 python-pisock at-spi locales file myspell-en-us kde-style-lipstik libgnomeprint2.2-0 ijsgutenprint gstreamer0.10-alsa evince ksplash-engine-moodin libpam-modules gnome-system-tools libxmu-dev tcl8.4 libogg0 libavahi-client3 python-stats python-reportlab libgpmg1 libgtkhtml2-0 bum cupsys mcpp lynx ttf-arphic-ukai libgnome-pilot2 ubuntu-sounds foo2zjs python-numeric python-orbit libsensors3 gnome-screensaver yelp libjpeg62 openoffice.org-writer parted libcupsys2 libmysqlclient15off libsasl2 libflac7 language-pack-gnome-en python-launchpad-integration intltool-debian mc gnomebaker slocate libflac++5c2 atitvout xfonts-terminus-dos libacl1 libpam0g kdemultimedia-kio-plugins sun-java5-demo python-newt gok console-tools openssl libfame-0.9 gstreamer0.10-plugins-good ntpdate firestarter usplash libdvdplay0 ksysguard rar libhsqldb-java libfltk1.1 ltrace bsh libgtk2-ruby x11proto-record-dev ttf-indic-fonts libperl5.8 python-apt ttf-bengali-fonts finger libattr1 hplip amarok discover1 xkeyboard-config libxdamage1 netbase app-install-data-commercial openoffice.org-help-en-us libnetpbm9 liblpint-bonobo0 aptitude language-selector libbeagle0 libgtksourceview1.0-0 gtk2-engines-redmond95 libxpm4 libpanel-applet2-0 evolution-plugins libgdl-1-0 obexserver libglade2-0 python-gnome2-desktop libstlport4.6c2 update-manager libieee1284-3 gstreamer0.10-x libkdepim1a gnome-mag librasqal0 gs-esp nautilus-cd-burner app-install-data python-gst0.10 ntp-server ttf-telugu-fonts libncursesw5 wvdial libsndfile1 psmisc ppp cupsys-bsd libxerces2-java openoffice.org-gnome libxft-dev dictionaries-common libdbus-qt-1-1c2 openoffice.org gstreamer0.10-plugins-bad libxft2 fakeroot gnome-session g++ libdjvulibre15 xfonts-utils python-xml kdepasswd x11proto-randr-dev xscreensaver-gl smbclient ttf-freefont gnome-pilot pppconfig krita-data libarts1c2a libpt-plugins-v4l2 libsepol1 gnome-keyring mount rhythmbox kppp initramfs-tools gamin iso-codes libgnomeui-0 php5-cgi apache2 libgtk2.0-0 libgnome-speech3 rsync libgnomeprintui2.2-common libquicktime0 gtk2-engines-highcontrast librsvg2-2 tcltls libast2 apache2-mpm-prefork libeel2-data xresprobe gettext libgnucrypto-java usbutils perl-base libfreetype6-dev libgtkhtml3.8-15 xmms akregator perl-modules libxmuu1 update-notifier ttf-malayalam-fonts xsane libglitz1 libtext-iconv-perl mkisofs kde-guidance knetworkconf libguile-ltdl-1 libdb3 discover1-data libglib2.0-0 kmenuedit defoma dosemu xserver-xorg-input-evdev linux-image-686 libraw1394-8 alacarte ark libgnorba27 binutils-static libgstreamer0.8-0 multi-gnome-terminal libxinerama-dev libgpgme11 gimp-print gsfonts-other python-libxml2 ksplash libvorbisfile3 sbackup firefox-gnome-support bogofilter-bdb libshout3 dpkg xserver-xorg-input-elographics mysql-client-5.0 libopenexr2c2a artsbuilder gnome-accessibility-themes easytag phpmyadmin openoffice.org-draw libmdbtools linux-686 openoffice.org-common liboil0.3 lsof libgnome32 gucharmap libwnck18 gnome-netstatus-applet xpmutils dh-make libpt-1.10.0 cupsys-client libtag1c2a vbetool powermgmt-base ubuntu-desktop libgnomevfs2-bin libkonq4 libkpimexchange1 xvncviewer libvorbisenc2 streamtuner po-debconf libservlet2.3-java shared-mime-info tangerine-icon-theme libkpathsea4 libspeex1 gnopernicus mozilla-firefox-locale-en-gb lsb-base python-syck libglew1 python-epydoc libxi-dev console-data ubuntu-artwork dhcp3-common libxkbfile1 libpoppler1-qt xml-core apt libxrender-dev libopencdk8 tar libmagick9 python-pam aspell obexftp scim-qtimm openoffice.org-l10n-en-gb libtunepimp3 kcron libmjpegtools0c2a vino odbcinst1debian1 libnspr4 ktorrent bsdutils libskim0 openoffice.org-gtk apt-utils xrandr libpango1.0-0 libartsc0 gaim gaim-data blt python-parted gdk-imlib1 tango-icon-theme totem-xine mjpegtools libgnomeprint2.2-data cdrecord libxdmcp6 gxset libraptor1 foomatic-db-engine libgnome2-vfs-perl xrefresh dpkg-dev python-netcdf scim libavahi-glib1 libxtst-dev libexif12 libsoup2.2-8 libdvdread3 libxcursor-dev openoffice.org-thesaurus-en-us pppoeconf libgnomecups1.0-1 libpoppler1-glib liblaunchpad-integration0 krusader libdrm2 hwdata php5-mysqli
2006-10-27 09:58:08,694 DEBUG Free space on /: 4996087808
2006-10-27 09:58:08,694 DEBUG Dir /usr mounted on /
2006-10-27 09:58:08,694 DEBUG Dir /var mounted on /
2006-10-27 09:58:08,694 DEBUG Dir /boot mounted on /
2006-10-27 09:58:09,458 DEBUG required download: 995753850.0 
2006-10-27 09:58:09,458 DEBUG free on /var/cache/apt/archives/: 4996087808 
2006-10-27 09:58:10,033 DEBUG need additional space: 308318208.0
2006-10-27 09:58:10,615 DEBUG /usr on same fs as /var/cache/apt/archives/, taking dl-size into account, new free: 4000333958.0
2006-10-27 09:58:10,615 DEBUG using safety buffer: 104857600
2006-10-27 15:20:13,626 ERROR IOError in cache.commit(): 'Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_0.79-3.1ubuntu1_i386.deb 400 Request denied [IP: 195.248.90.54 80]
'. Retrying (currentTry: 0)
2006-10-27 15:24:41,392 ERROR got an error from dpkg for pkg: '/var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb': 'subprocess pre-installation script returned error exit status 1
'
2006-10-27 15:24:51,351 ERROR SystemError from cache.commit(): installArchives() failed

```

---

### Post by alex1973 on 2006-10-27
Here's the apt.log:


```
gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Starting
Starting 2
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Investigating kdelibs4c2a
Package kdelibs4c2a has broken dep on kdelibs-bin
  Considering kdelibs-bin 0 as a solution to kdelibs4c2a 291
  Added kdelibs-bin to the remove list
  Fixing kdelibs4c2a via remove of kdelibs-bin
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken dep on xserver-xorg-driver-all
  Considering xserver-xorg-driver-all 0 as a solution to xserver-xorg-video-all 78
  Added xserver-xorg-driver-all to the remove list
  Fixing xserver-xorg-video-all via remove of xserver-xorg-driver-all
Investigating python-gtk2
Package python-gtk2 has broken dep on python2.4-gtk2
  Considering python2.4-gtk2 6 as a solution to python-gtk2 71
  Added python2.4-gtk2 to the remove list
  Fixing python-gtk2 via remove of python2.4-gtk2
Investigating python-glade2
Package python-glade2 has broken dep on python2.4-glade2
  Considering python2.4-glade2 0 as a solution to python-glade2 32
  Added python2.4-glade2 to the remove list
  Fixing python-glade2 via remove of python2.4-glade2
Investigating python-numeric
Package python-numeric has broken dep on python2.4-numeric
  Considering python2.4-numeric 5 as a solution to python-numeric 30
  Added python2.4-numeric to the remove list
  Fixing python-numeric via remove of python2.4-numeric
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5100 as a solution to upstart 25
  Holding Back upstart rather than change sysvinit
Investigating python-cairo
Package python-cairo has broken dep on python2.4-cairo
  Considering python2.4-cairo 5 as a solution to python-cairo 25
  Added python2.4-cairo to the remove list
  Fixing python-cairo via remove of python2.4-cairo
Investigating python-gobject
Package python-gobject has broken dep on python2.4-gobject
  Considering python2.4-gobject 5 as a solution to python-gobject 25
  Added python2.4-gobject to the remove list
  Fixing python-gobject via remove of python2.4-gobject
Investigating python-pyorbit
Package python-pyorbit has broken dep on python2.4-pyorbit
  Considering python2.4-pyorbit 5 as a solution to python-pyorbit 22
  Added python2.4-pyorbit to the remove list
  Fixing python-pyorbit via remove of python2.4-pyorbit
Investigating python-apt
Package python-apt has broken dep on python2.4-apt
  Considering python2.4-apt 0 as a solution to python-apt 17
  Added python2.4-apt to the remove list
  Fixing python-apt via remove of python2.4-apt
Investigating python-gnome2
Package python-gnome2 has broken dep on python2.4-gnome2
  Considering python2.4-gnome2 3 as a solution to python-gnome2 15
  Added python2.4-gnome2 to the remove list
  Fixing python-gnome2 via remove of python2.4-gnome2
Investigating libnewt0.52
Package libnewt0.52 has broken dep on libnewt0.51
  Considering libnewt0.51 3 as a solution to libnewt0.52 13
  Added libnewt0.51 to the remove list
  Fixing libnewt0.52 via remove of libnewt0.51
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 25 as a solution to upstart-compat-sysv 12
  Holding Back upstart-compat-sysv rather than change upstart
Investigating python-libxml2
Package python-libxml2 has broken dep on python2.4-libxml2
  Considering python2.4-libxml2 3 as a solution to python-libxml2 11
  Added python2.4-libxml2 to the remove list
  Fixing python-libxml2 via remove of python2.4-libxml2
Investigating linux-libc-dev
Package linux-libc-dev has broken dep on linux-kernel-headers
  Considering linux-kernel-headers 2 as a solution to linux-libc-dev 11
  Added linux-kernel-headers to the remove list
  Fixing linux-libc-dev via remove of linux-kernel-headers
Investigating python-dbus
Package python-dbus has broken dep on python2.4-dbus
  Considering python2.4-dbus 1 as a solution to python-dbus 11
  Added python2.4-dbus to the remove list
  Fixing python-dbus via remove of python2.4-dbus
Investigating python-gnome2-desktop
Package python-gnome2-desktop has broken dep on python2.4-gnome2-desktop
  Considering python2.4-gnome2-desktop 0 as a solution to python-gnome2-desktop 11
  Added python2.4-gnome2-desktop to the remove list
  Fixing python-gnome2-desktop via remove of python2.4-gnome2-desktop
Investigating xutils-dev
Package xutils-dev has broken dep on imake
  Considering imake 0 as a solution to xutils-dev 10
  Added imake to the remove list
Package xutils-dev has broken dep on makedepend
  Considering makedepend 1 as a solution to xutils-dev 10
  Added makedepend to the remove list
  Fixing xutils-dev via remove of imake
  Fixing xutils-dev via remove of makedepend
Investigating python-qt3
Package python-qt3 has broken dep on libqt3-mt-odbc
  Considering libqt3-mt-odbc 0 as a solution to python-qt3 9
  Holding Back python-qt3 rather than change libqt3-mt-odbc
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 25 as a solution to startup-tasks 8
  Holding Back startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 25 as a solution to system-services 8
  Holding Back system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 25 as a solution to upstart-logd 8
  Holding Back upstart-logd rather than change upstart
Investigating python-gnome2-extras
Package python-gnome2-extras has broken dep on python2.4-gnome2-extras
  Considering python2.4-gnome2-extras 0 as a solution to python-gnome2-extras 7
  Added python2.4-gnome2-extras to the remove list
  Fixing python-gnome2-extras via remove of python2.4-gnome2-extras
Investigating libxklavier11
Package libxklavier11 has broken dep on libxklavier10
  Considering libxklavier10 0 as a solution to libxklavier11 7
  Added libxklavier10 to the remove list
  Fixing libxklavier11 via remove of libxklavier10
Investigating python-xml
Package python-xml has broken dep on python2.4-xml
  Considering python2.4-xml 2 as a solution to python-xml 6
  Added python2.4-xml to the remove list
  Fixing python-xml via remove of python2.4-xml
Investigating libgcj7-0
Package libgcj7-0 has broken dep on libgcj7
  Considering libgcj7 0 as a solution to libgcj7-0 5
  Added libgcj7 to the remove list
  Fixing libgcj7-0 via remove of libgcj7
Investigating python-sip4
Package python-sip4 has broken dep on python2.4-sip4-qt3
  Considering python2.4-sip4-qt3 8 as a solution to python-sip4 5
  Holding Back python-sip4 rather than change python2.4-sip4-qt3
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 5
  Holding Back ubuntu-minimal rather than change startup-tasks
Investigating python-egenix-mxtools
Package python-egenix-mxtools has broken dep on python2.4-egenix-mxtools
  Considering python2.4-egenix-mxtools 5 as a solution to python-egenix-mxtools 5
  Holding Back python-egenix-mxtools rather than change python2.4-egenix-mxtools
Investigating hpijs
Package hpijs has broken dep on hplip-ppds
  Considering hplip-ppds 2 as a solution to hpijs 3
  Added hplip-ppds to the remove list
  Fixing hpijs via remove of hplip-ppds
Investigating python-kde3
Package python-kde3 has broken dep on python-qt3
  Considering python-qt3 9 as a solution to python-kde3 3
  Holding Back python-kde3 rather than change python-qt3
Investigating python2.4-tk
Package python2.4-tk has broken dep on python2.4
  Considering python2.4 363 as a solution to python2.4-tk 2
  Removing python2.4-tk rather than change python2.4
Investigating libgii0
Package libgii0 has broken dep on libgg0
  Considering libgii1 1 as a solution to libgii0 2
  Added libgii1 to the remove list
  Fixing libgii0 via keep of libgii1
Investigating python-gdbm
Package python-gdbm has broken dep on python2.4-gdbm
  Considering python2.4-gdbm 0 as a solution to python-gdbm 2
  Added python2.4-gdbm to the remove list
  Fixing python-gdbm via remove of python2.4-gdbm
Investigating xorg
Package xorg has broken dep on libgl1-mesa-glx
  Considering libgl1-mesa-glx 19 as a solution to xorg 2
  Holding Back xorg rather than change libgl1-mesa-glx
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken dep on xserver-xorg-driver-rendition
  Considering xserver-xorg-driver-rendition 1 as a solution to xserver-xorg-video-rendition 1
  Holding Back xserver-xorg-video-rendition rather than change xserver-xorg-driver-rendition
Investigating xserver-xorg-video-newport
Package xserver-xorg-video-newport has broken dep on xserver-xorg-driver-newport
  Considering xserver-xorg-driver-newport 1 as a solution to xserver-xorg-video-newport 1
  Holding Back xserver-xorg-video-newport rather than change xserver-xorg-driver-newport
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken dep on xserver-xorg-driver-s3virge
  Considering xserver-xorg-driver-s3virge 1 as a solution to xserver-xorg-video-s3virge 1
  Holding Back xserver-xorg-video-s3virge rather than change xserver-xorg-driver-s3virge
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken dep on xserver-xorg-driver-apm
  Considering xserver-xorg-driver-apm 1 as a solution to xserver-xorg-video-apm 1
  Holding Back xserver-xorg-video-apm rather than change xserver-xorg-driver-apm
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken dep on xserver-xorg-driver-ark
  Considering xserver-xorg-driver-ark 1 as a solution to xserver-xorg-video-ark 1
  Holding Back xserver-xorg-video-ark rather than change xserver-xorg-driver-ark
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-r128
  Considering xserver-xorg-driver-ati 1 as a solution to xserver-xorg-video-ati 1
  Holding Back xserver-xorg-video-ati rather than change xserver-xorg-driver-r128
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken dep on xserver-xorg-driver-tdfx
  Considering xserver-xorg-driver-tdfx 1 as a solution to xserver-xorg-video-tdfx 1
  Holding Back xserver-xorg-video-tdfx rather than change xserver-xorg-driver-tdfx
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken dep on xserver-xorg-driver-trident
  Considering xserver-xorg-driver-trident 1 as a solution to xserver-xorg-video-trident 1
  Holding Back xserver-xorg-video-trident rather than change xserver-xorg-driver-trident
Investigating xserver-xorg-video-glint
Package xserver-xorg-video-glint has broken dep on xserver-xorg-driver-glint
  Considering xserver-xorg-driver-glint 1 as a solution to xserver-xorg-video-glint 1
  Holding Back xserver-xorg-video-glint rather than change xserver-xorg-driver-glint
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken dep on xserver-xorg-driver-fbdev
  Considering xserver-xorg-driver-fbdev 1 as a solution to xserver-xorg-video-fbdev 1
  Holding Back xserver-xorg-video-fbdev rather than change xserver-xorg-driver-fbdev
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken dep on xserver-xorg-driver-v4l
  Considering xserver-xorg-driver-v4l 1 as a solution to xserver-xorg-video-v4l 1
  Holding Back xserver-xorg-video-v4l rather than change xserver-xorg-driver-v4l
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken dep on xserver-xorg-driver-mga
  Considering xserver-xorg-driver-mga 1 as a solution to xserver-xorg-video-mga 1
  Holding Back xserver-xorg-video-mga rather than change xserver-xorg-driver-mga
Investigating xserver-xorg-video-nsc
Package xserver-xorg-video-nsc has broken dep on xserver-xorg-driver-nsc
  Considering xserver-xorg-driver-nsc 1 as a solution to xserver-xorg-video-nsc 1
  Holding Back xserver-xorg-video-nsc rather than change xserver-xorg-driver-nsc
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken dep on xserver-xorg-driver-vesa
  Considering xserver-xorg-driver-vesa 1 as a solution to xserver-xorg-video-vesa 1
  Holding Back xserver-xorg-video-vesa rather than change xserver-xorg-driver-vesa
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken dep on xserver-xorg-driver-siliconmotion
  Considering xserver-xorg-driver-siliconmotion 1 as a solution to xserver-xorg-video-siliconmotion 1
  Holding Back xserver-xorg-video-siliconmotion rather than change xserver-xorg-driver-siliconmotion
Investigating xserver-xorg-video-tga
Package xserver-xorg-video-tga has broken dep on xserver-xorg-driver-tga
  Considering xserver-xorg-driver-tga 1 as a solution to xserver-xorg-video-tga 1
  Holding Back xserver-xorg-video-tga rather than change xserver-xorg-driver-tga
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken dep on xserver-xorg-driver-sis
  Considering xserver-xorg-driver-sis 1 as a solution to xserver-xorg-video-sis 1
  Holding Back xserver-xorg-video-sis rather than change xserver-xorg-driver-sis
Investigating xserver-xorg-video-vga
Package xserver-xorg-video-vga has broken dep on xserver-xorg-driver-vga
  Considering xserver-xorg-driver-vga 1 as a solution to xserver-xorg-video-vga 1
  Holding Back xserver-xorg-video-vga rather than change xserver-xorg-driver-vga
Investigating xserver-xorg-video-via
Package xserver-xorg-video-via has broken dep on xserver-xorg-driver-via
  Considering xserver-xorg-driver-via 1 as a solution to xserver-xorg-video-via 1
  Holding Back xserver-xorg-video-via rather than change xserver-xorg-driver-via
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken dep on xserver-xorg-driver-s3
  Considering xserver-xorg-driver-s3 1 as a solution to xserver-xorg-video-s3 1
  Holding Back xserver-xorg-video-s3 rather than change xserver-xorg-driver-s3
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken dep on xserver-xorg-driver-riva128
  Considering xserver-xorg-driver-nv 1 as a solution to xserver-xorg-video-nv 1
  Holding Back xserver-xorg-video-nv rather than change xserver-xorg-driver-riva128
Investigating xserver-xorg-video-tseng
Package xserver-xorg-video-tseng has broken dep on xserver-xorg-driver-tseng
  Considering xserver-xorg-driver-tseng 1 as a solution to xserver-xorg-video-tseng 1
  Holding Back xserver-xorg-video-tseng rather than change xserver-xorg-driver-tseng
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken dep on xserver-xorg-driver-savage
  Considering xserver-xorg-driver-savage 1 as a solution to xserver-xorg-video-savage 1
  Holding Back xserver-xorg-video-savage rather than change xserver-xorg-driver-savage
Investigating python-imaging
Package python-imaging has broken dep on python2.4-imaging
  Considering python2.4-imaging 1 as a solution to python-imaging 1
  Holding Back python-imaging rather than change python2.4-imaging
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken dep on xserver-xorg-driver-vmware
  Considering xserver-xorg-driver-vmware 1 as a solution to xserver-xorg-video-vmware 1
  Holding Back xserver-xorg-video-vmware rather than change xserver-xorg-driver-vmware
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken dep on xserver-xorg-driver-i128
  Considering xserver-xorg-driver-i128 1 as a solution to xserver-xorg-video-i128 1
  Holding Back xserver-xorg-video-i128 rather than change xserver-xorg-driver-i128
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken dep on xserver-xorg-driver-neomagic
  Considering xserver-xorg-driver-neomagic 1 as a solution to xserver-xorg-video-neomagic 1
  Holding Back xserver-xorg-video-neomagic rather than change xserver-xorg-driver-neomagic
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken dep on xserver-xorg-driver-chips
  Considering xserver-xorg-driver-chips 1 as a solution to xserver-xorg-video-chips 1
  Holding Back xserver-xorg-video-chips rather than change xserver-xorg-driver-chips
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken dep on xserver-xorg-driver-voodoo
  Considering xserver-xorg-driver-voodoo 1 as a solution to xserver-xorg-video-voodoo 1
  Holding Back xserver-xorg-video-voodoo rather than change xserver-xorg-driver-voodoo
Investigating xserver-xorg-video-i740
Package xserver-xorg-video-i740 has broken dep on xserver-xorg-driver-i740
  Considering xserver-xorg-driver-i740 1 as a solution to xserver-xorg-video-i740 1
  Holding Back xserver-xorg-video-i740 rather than change xserver-xorg-driver-i740
Investigating xserver-xorg-video-i810
Package xserver-xorg-video-i810 has broken dep on xserver-xorg-driver-i810
  Considering xserver-xorg-driver-i810 1 as a solution to xserver-xorg-video-i810 1
  Holding Back xserver-xorg-video-i810 rather than change xserver-xorg-driver-i810
Investigating xserver-xorg-video-cyrix
Package xserver-xorg-video-cyrix has broken dep on xserver-xorg-driver-cyrix
  Considering xserver-xorg-driver-cyrix 1 as a solution to xserver-xorg-video-cyrix 1
  Holding Back xserver-xorg-video-cyrix rather than change xserver-xorg-driver-cyrix
Investigating xserver-xorg-video-dummy
Package xserver-xorg-video-dummy has broken dep on xserver-xorg-driver-dummy
  Considering xserver-xorg-driver-dummy 1 as a solution to xserver-xorg-video-dummy 1
  Holding Back xserver-xorg-video-dummy rather than change xserver-xorg-driver-dummy
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken dep on xserver-xorg-driver-sisusb
  Considering xserver-xorg-driver-sisusb 1 as a solution to xserver-xorg-video-sisusb 1
  Holding Back xserver-xorg-video-sisusb rather than change xserver-xorg-driver-sisusb
Investigating xserver-xorg-video-imstt
Package xserver-xorg-video-imstt has broken dep on xserver-xorg-driver-imstt
  Considering xserver-xorg-driver-imstt 1 as a solution to xserver-xorg-video-imstt 1
  Holding Back xserver-xorg-video-imstt rather than change xserver-xorg-driver-imstt
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken dep on xserver-xorg-driver-cirrus
  Considering xserver-xorg-driver-cirrus 1 as a solution to xserver-xorg-video-cirrus 1
  Holding Back xserver-xorg-video-cirrus rather than change xserver-xorg-driver-cirrus
Investigating python-crypto
Package python-crypto has broken dep on python2.4-crypto
  Considering python2.4-crypto 0 as a solution to python-crypto 0
  Holding Back python-crypto rather than change python2.4-crypto
Investigating libgtk-pixbuf-perl
Package libgtk-pixbuf-perl has broken dep on libgtk-perl
  Considering libgtk-perl 1 as a solution to libgtk-pixbuf-perl 0
  Removing libgtk-pixbuf-perl rather than change libgtk-perl
Investigating python-egenix-mxtexttools
Package python-egenix-mxtexttools has broken dep on python2.4-egenix-mxtexttools
  Considering python2.4-egenix-mxtexttools 0 as a solution to python-egenix-mxtexttools 0
  Holding Back python-egenix-mxtexttools rather than change python2.4-egenix-mxtexttools
Investigating python-ldap
Package python-ldap has broken dep on python2.4-ldap
  Considering python2.4-ldap 0 as a solution to python-ldap 0
  Holding Back python-ldap rather than change python2.4-ldap
Investigating python-pexpect
Package python-pexpect has broken dep on python2.4-pexpect
  Considering python2.4-pexpect 0 as a solution to python-pexpect 0
  Holding Back python-pexpect rather than change python2.4-pexpect
Investigating python-imaging-sane
Package python-imaging-sane has broken dep on python-imaging
  Considering python-imaging 1 as a solution to python-imaging-sane 0
  Holding Back python-imaging-sane rather than change python-imaging
Investigating python2.4-libxslt1
Package python2.4-libxslt1 has broken dep on python2.4-libxml2
  Considering python2.4-libxml2 3 as a solution to python2.4-libxslt1 0
  Removing python2.4-libxslt1 rather than change python2.4-libxml2
Investigating x-window-system-core
Package x-window-system-core has broken dep on xorg
  Considering xorg 2 as a solution to x-window-system-core 0
  Holding Back x-window-system-core rather than change xorg
Investigating python-mysqldb
Package python-mysqldb has broken dep on python2.4-mysqldb
  Considering python2.4-mysqldb 0 as a solution to python-mysqldb 0
  Holding Back python-mysqldb rather than change python2.4-mysqldb
Investigating python-pyxattr
Package python-pyxattr has broken dep on python2.4-pyxattr
  Considering python2.4-pyxattr 0 as a solution to python-pyxattr 0
  Holding Back python-pyxattr rather than change python2.4-pyxattr
Investigating python-kjbuckets
Package python-kjbuckets has broken dep on python2.4-kjbuckets
  Considering python2.4-kjbuckets 0 as a solution to python-kjbuckets 0
  Holding Back python-kjbuckets rather than change python2.4-kjbuckets
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgl1-mesa-glx
  Considering libgl1-mesa-glx 19 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgl1-mesa-glx
Investigating python-pgsql
Package python-pgsql has broken dep on python2.4-pgsql
  Considering python2.4-pgsql 0 as a solution to python-pgsql 0
  Holding Back python-pgsql rather than change python2.4-pgsql
Investigating python-htmlgen
Package python-htmlgen has broken dep on python2.4-htmlgen
  Considering python2.4-htmlgen 0 as a solution to python-htmlgen 0
  Holding Back python-htmlgen rather than change python2.4-htmlgen
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on libgl1-mesa-glx
  Considering libgl1-mesa-glx 19 as a solution to kubuntu-desktop 0
  Removing kubuntu-desktop rather than change libgl1-mesa-glx
Investigating python-clientcookie
Package python-clientcookie has broken dep on python2.4-clientcookie
  Considering python2.4-clientcookie 0 as a solution to python-clientcookie 0
  Holding Back python-clientcookie rather than change python2.4-clientcookie
Investigating python-adns
Package python-adns has broken dep on python2.4-adns
  Considering python2.4-adns 0 as a solution to python-adns 0
  Holding Back python-adns rather than change python2.4-adns
Investigating python-pam
Package python-pam has broken dep on python2.4-pam
  Considering python2.4-pam 0 as a solution to python-pam 0
  Holding Back python-pam rather than change python2.4-pam
Investigating python-qt4
Package python-qt4 has broken dep on python-sip4
  Considering python-sip4 5 as a solution to python-qt4 0
  Holding Back python-qt4 rather than change python-sip4
Investigating python-gadfly
Package python-gadfly has broken dep on python2.4-gadfly
  Considering python2.4-gadfly 0 as a solution to python-gadfly 0
  Holding Back python-gadfly rather than change python2.4-gadfly
Investigating python-soappy
Package python-soappy has broken dep on python2.4-soappy
  Considering python2.4-soappy 0 as a solution to python-soappy 0
  Holding Back python-soappy rather than change python2.4-soappy
Investigating libvte4
Package libvte4 has broken dep on libvte-common
  Considering libvte-common 4 as a solution to libvte4 0
  Removing libvte4 rather than change libvte-common
Investigating python-pyopenssl
Package python-pyopenssl has broken dep on python2.4-pyopenssl
  Considering python2.4-pyopenssl 0 as a solution to python-pyopenssl 0
  Holding Back python-pyopenssl rather than change python2.4-pyopenssl
Investigating python-egenix-mxstack
Package python-egenix-mxstack has broken dep on python2.4-egenix-mxstack
  Considering python2.4-egenix-mxstack 0 as a solution to python-egenix-mxstack 0
  Holding Back python-egenix-mxstack rather than change python2.4-egenix-mxstack
Investigating python-pysqlite2
Package python-pysqlite2 has broken dep on python2.4-pysqlite2
  Considering python2.4-pysqlite2 0 as a solution to python-pysqlite2 0
  Holding Back python-pysqlite2 rather than change python2.4-pysqlite2
Investigating libgii1-target-x
Package libgii1-target-x has broken dep on libgii0-target-x
  Considering libgii0-target-x 2 as a solution to libgii1-target-x 0
  Holding Back libgii1-target-x rather than change libgii0-target-x
Investigating python-sqlite
Package python-sqlite has broken dep on python2.4-sqlite
  Considering python2.4-sqlite 0 as a solution to python-sqlite 0
  Holding Back python-sqlite rather than change python2.4-sqlite
Investigating python-syck
Package python-syck has broken dep on python2.4-syck
  Considering python2.4-syck 0 as a solution to python-syck 0
  Holding Back python-syck rather than change python2.4-syck
Investigating python-egenix-mxdatetime
Package python-egenix-mxdatetime has broken dep on python2.4-egenix-mxdatetime
  Considering python2.4-egenix-mxdatetime 1 as a solution to python-egenix-mxdatetime 0
  Holding Back python-egenix-mxdatetime rather than change python2.4-egenix-mxdatetime
Investigating python-pylibacl
Package python-pylibacl has broken dep on python2.4-pylibacl
  Considering python2.4-pylibacl 0 as a solution to python-pylibacl 0
  Holding Back python-pylibacl rather than change python2.4-pylibacl
Investigating python-jabber
Package python-jabber has broken dep on python2.4-jabber
  Considering python2.4-jabber 0 as a solution to python-jabber 0
  Holding Back python-jabber rather than change python2.4-jabber
Investigating python-egenix-mxproxy
Package python-egenix-mxproxy has broken dep on python2.4-egenix-mxproxy
  Considering python2.4-egenix-mxproxy 0 as a solution to python-egenix-mxproxy 0
  Holding Back python-egenix-mxproxy rather than change python2.4-egenix-mxproxy
Investigating listen
Package listen has broken dep on python-pysqlite2
  Considering python-pysqlite2 0 as a solution to listen 0
  Holding Back listen rather than change python-pysqlite2
Investigating python-xmpp
Package python-xmpp has broken dep on python2.4-xmpp
  Considering python2.4-xmpp 0 as a solution to python-xmpp 0
  Holding Back python-xmpp rather than change python2.4-xmpp
Investigating python-htmltmpl
Package python-htmltmpl has broken dep on python2.4-htmltmpl
  Considering python2.4-htmltmpl 0 as a solution to python-htmltmpl 0
  Holding Back python-htmltmpl rather than change python2.4-htmltmpl
Investigating python-reportlab
Package python-reportlab has broken dep on python2.4-reportlab
  Considering python2.4-reportlab 0 as a solution to python-reportlab 0
  Holding Back python-reportlab rather than change python2.4-reportlab
Investigating python-simpletal
Package python-simpletal has broken dep on python2.4-simpletal
  Considering python2.4-simpletal 0 as a solution to python-simpletal 0
  Holding Back python-simpletal rather than change python2.4-simpletal
Investigating foomatic-filters-ppds
Package foomatic-filters-ppds has broken dep on hplip-ppds
  Considering hplip-ppds 2 as a solution to foomatic-filters-ppds -1
  Removing foomatic-filters-ppds rather than change hplip-ppds
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken dep on xserver-xorg-video-apm
  Considering xserver-xorg-video-apm 1 as a solution to xserver-xorg-video-all 78
  Holding Back xserver-xorg-video-all rather than change xserver-xorg-video-apm
 Try to Re-Instate python-qt3
Investigating xserver-xorg
Package xserver-xorg has broken dep on xserver-xorg-video-all
  Considering xserver-xorg-video-all 78 as a solution to xserver-xorg 8
  Holding Back xserver-xorg rather than change xserver-xorg-video-all
Package xserver-xorg has broken dep on xserver-xorg-video
  Considering xserver-xorg-video-voodoo 1 as a solution to xserver-xorg 8
  Holding Back xserver-xorg rather than change xserver-xorg-video
  Or group keep for xserver-xorg
 Try to Re-Instate ubuntu-minimal
 Try to Re-Instate python-egenix-mxtools
Investigating libggi2
Package libggi2 has broken dep on libgii1
  Considering libgii1 1 as a solution to libggi2 3
  Holding Back libggi2 rather than change libgii1
 Try to Re-Instate python-kde3
 Try to Re-Instate python-imaging
 Try to Re-Instate python-crypto
 Try to Re-Instate python-egenix-mxtexttools
 Try to Re-Instate python-ldap
 Try to Re-Instate python-pexpect
 Try to Re-Instate python-imaging-sane
 Try to Re-Instate x-window-system-core
 Try to Re-Instate python-mysqldb
 Try to Re-Instate python-pyxattr
 Try to Re-Instate python-kjbuckets
Investigating hwdb-client-kde
Package hwdb-client-kde has broken dep on python-qt4
  Considering python-qt4 0 as a solution to hwdb-client-kde 0
  Holding Back hwdb-client-kde rather than change python-qt4
 Try to Re-Instate python-pgsql
 Try to Re-Instate python-htmlgen
 Try to Re-Instate python-clientcookie
 Try to Re-Instate python-adns
 Try to Re-Instate python-pam
 Try to Re-Instate python-gadfly
 Try to Re-Instate python-soappy
 Try to Re-Instate python-pyopenssl
 Try to Re-Instate python-egenix-mxstack
 Try to Re-Instate python-sqlite
 Try to Re-Instate python-syck
 Try to Re-Instate python-pylibacl
 Try to Re-Instate python-jabber
 Try to Re-Instate python-egenix-mxproxy
 Try to Re-Instate listen
 Try to Re-Instate python-xmpp
 Try to Re-Instate python-htmltmpl
 Try to Re-Instate python-reportlab
 Try to Re-Instate python-simpletal
Investigating x11-common
Package x11-common has broken dep on xserver-xorg
  Considering xserver-xorg 8 as a solution to x11-common 2678
  Added xserver-xorg to the remove list
  Fixing x11-common via remove of xserver-xorg
Investigating xserver-xorg-core
Package xserver-xorg-core has broken dep on xserver-xorg-video-all
  Considering xserver-xorg-video-all 78 as a solution to xserver-xorg-core 115
  Holding Back xserver-xorg-core rather than change xserver-xorg-video-all
Package xserver-xorg-core has broken dep on xserver-xorg-video
  Considering xserver-xorg-video-voodoo 1 as a solution to xserver-xorg-core 115
  Holding Back xserver-xorg-core rather than change xserver-xorg-video
  Or group keep for xserver-xorg-core
Investigating xorg-driver-fglrx
Package xorg-driver-fglrx has broken dep on xserver-xorg
  Considering xserver-xorg 2678 as a solution to xorg-driver-fglrx 5
  Removing xorg-driver-fglrx rather than change xserver-xorg
Investigating xserver-xorg-input-evdev
Package xserver-xorg-input-evdev has broken dep on xserver-xorg-core
  Considering xserver-xorg-core 115 as a solution to xserver-xorg-input-evdev 3
  Holding Back xserver-xorg-input-evdev rather than change xserver-xorg-core
Investigating xserver-xorg-input-mouse
Package xserver-xorg-input-mouse has broken dep on xserver-xorg-core
  Considering xserver-xorg-core 115 as a solution to xserver-xorg-input-mouse 3
  Holding Back xserver-xorg-input-mouse rather than change xserver-xorg-core
Investigating mplayer
Package mplayer has broken dep on libggi2
  Considering libggi2 3 as a solution to mplayer 3
  Holding Back mplayer rather than change libggi2
 Try to Re-Instate libggi2
Investigating xserver-xorg-input-elographics
Package xserver-xorg-input-elographics has broken dep on xserver-xorg-core
  Considering xserver-xorg-core 115 as a solution to xserver-xorg-input-elographics 3
  Holding Back xserver-xorg-input-elographics rather than change xserver-xorg-core
Investigating xserver-xorg-input-kbd
Package xserver-xorg-input-kbd has broken dep on xserver-xorg-core
  Considering xserver-xorg-core 115 as a solution to xserver-xorg-input-kbd 3
  Holding Back xserver-xorg-input-kbd rather than change xserver-xorg-core
Investigating xserver-xorg-input-synaptics
Package xserver-xorg-input-synaptics has broken dep on xserver-xorg-core
  Considering xserver-xorg-core 115 as a solution to xserver-xorg-input-synaptics 3
  Holding Back xserver-xorg-input-synaptics rather than change xserver-xorg-core
Investigating x-window-system-core
Package x-window-system-core has broken dep on xserver-xorg
  Considering xserver-xorg 2678 as a solution to x-window-system-core 0
  Removing x-window-system-core rather than change xserver-xorg
Investigating fglrx-control
Package fglrx-control has broken dep on xorg-driver-fglrx
  Considering xorg-driver-fglrx 2678 as a solution to fglrx-control 0
  Removing fglrx-control rather than change xorg-driver-fglrx
Investigating xorg-edit
Package xorg-edit has broken dep on xserver-xorg
  Considering xserver-xorg 2678 as a solution to xorg-edit 0
  Removing xorg-edit rather than change xserver-xorg
Investigating fglrx-kernel-2.6.15-26-686
Package fglrx-kernel-2.6.15-26-686 has broken dep on xorg-driver-fglrx
  Considering xorg-driver-fglrx 2678 as a solution to fglrx-kernel-2.6.15-26-686 -1
  Removing fglrx-kernel-2.6.15-26-686 rather than change xorg-driver-fglrx
Investigating fglrx-kernel-2.6.15-27-686
Package fglrx-kernel-2.6.15-27-686 has broken dep on xorg-driver-fglrx
  Considering xorg-driver-fglrx 2678 as a solution to fglrx-kernel-2.6.15-27-686 -1
  Removing fglrx-kernel-2.6.15-27-686 rather than change xorg-driver-fglrx
 Try to Re-Instate xserver-xorg-core
 Try to Re-Instate xserver-xorg-input-evdev
 Try to Re-Instate xserver-xorg-input-mouse
 Try to Re-Instate mplayer
 Try to Re-Instate xserver-xorg-input-elographics
 Try to Re-Instate xserver-xorg-input-kbd
 Try to Re-Instate xserver-xorg-input-synaptics
Done
Starting
Starting 2
Investigating libglu1-mesa
Package libglu1-mesa has broken dep on libgl1-mesa
  Considering libgl1-mesa 9 as a solution to libglu1-mesa 35
  Added libgl1-mesa to the remove list
Package libglu1-mesa has broken dep on libgl1
  Considering libgl1-mesa 9 as a solution to libglu1-mesa 35
  Added libgl1-mesa to the remove list
  Fixing libglu1-mesa via keep of libgl1-mesa
  Fixing libglu1-mesa via keep of libgl1-mesa
Investigating mplayer
Package mplayer has broken dep on libggi2
  Considering libggi2 3 as a solution to mplayer 3
  Holding Back mplayer rather than change libggi2
 Try to Re-Instate mplayer
Done
Starting
Starting 2
Investigating python2.4-kde3
Package python2.4-kde3 has broken dep on python2.4-qt3
  Considering python2.4-qt3 2 as a solution to python2.4-kde3 3
  Added python2.4-qt3 to the remove list
Package python2.4-kde3 has broken dep on python2.4-qt3
  Considering python2.4-qt3 2 as a solution to python2.4-kde3 3
  Added python2.4-qt3 to the remove list
Package python2.4-kde3 has broken dep on python2.4-sip4-qt3
  Considering python2.4-sip4-qt3 2 as a solution to python2.4-kde3 3
  Added python2.4-sip4-qt3 to the remove list
Package python2.4-kde3 has broken dep on python2.4-sip4-qt3
  Considering python2.4-sip4-qt3 2 as a solution to python2.4-kde3 3
  Added python2.4-sip4-qt3 to the remove list
  Fixing python2.4-kde3 via keep of python2.4-qt3
  Fixing python2.4-kde3 via keep of python2.4-qt3
  Fixing python2.4-kde3 via keep of python2.4-sip4-qt3
  Fixing python2.4-kde3 via keep of python2.4-sip4-qt3
Investigating python-sip4
Package python-sip4 has broken dep on python2.4-sip4-qt3
  Considering python2.4-sip4-qt3 2 as a solution to python-sip4 2
  Holding Back python-sip4 rather than change python2.4-sip4-qt3
Investigating python-qt3
Package python-qt3 has broken dep on python-sip4
  Considering python-sip4 2 as a solution to python-qt3 10004
  Re-Instated python-sip4
Package python-qt3 has broken dep on libqt3-mt-odbc
  Considering libqt3-mt-odbc 0 as a solution to python-qt3 10004
  Re-Instated libiodbc2
  Re-Instated libqt3-mt-odbc
Package python-qt3 has broken dep on python2.4-qt3
  Considering python2.4-qt3 2 as a solution to python-qt3 10004
  Added python2.4-qt3 to the remove list
  Fixing python-qt3 via remove of python2.4-qt3
Investigating python2.4-kde3
Package python2.4-kde3 has broken dep on python2.4-qt3
  Considering python2.4-qt3 2 as a solution to python2.4-kde3 3
  Added python2.4-qt3 to the remove list
Package python2.4-kde3 has broken dep on python2.4-qt3
  Considering python2.4-qt3 2 as a solution to python2.4-kde3 3
  Added python2.4-qt3 to the remove list
  Fixing python2.4-kde3 via keep of python2.4-qt3
  Fixing python2.4-kde3 via keep of python2.4-qt3
Investigating python-sip4
Package python-sip4 has broken dep on python2.4-sip4-qt3
  Considering python2.4-sip4-qt3 2 as a solution to python-sip4 2
  Holding Back python-sip4 rather than change python2.4-sip4-qt3
Investigating python-qt3
Package python-qt3 has broken dep on python-sip4
  Considering python-sip4 2 as a solution to python-qt3 10004
Package python-qt3 has broken dep on python2.4-qt3
  Considering python2.4-qt3 2 as a solution to python-qt3 10004
  Added python2.4-qt3 to the remove list
  Fixing python-qt3 via remove of python2.4-qt3
Investigating python2.4-kde3
Package python2.4-kde3 has broken dep on python2.4-qt3
  Considering python2.4-qt3 10004 as a solution to python2.4-kde3 3
  Removing python2.4-kde3 rather than change python2.4-qt3
Investigating python-kde3
Package python-kde3 has broken dep on python2.4-kde3
  Considering python2.4-kde3 10004 as a solution to python-kde3 3
  Re-Instated python-kde3
Investigating python-qt3
Package python-qt3 has broken dep on python-sip4
  Considering python-sip4 2 as a solution to python-qt3 10004
Done
Starting
Starting 2
Investigating python-qt3
Package python-qt3 has broken dep on python-sip4
  Considering python-sip4 1 as a solution to python-qt3 7
  Re-Instated python-sip4
  Re-Instated python-qt3
Investigating python-sip4
Package python-sip4 has broken dep on python2.4-sip4-qt3
  Considering python2.4-sip4-qt3 0 as a solution to python-sip4 1
  Added python2.4-sip4-qt3 to the remove list
  Fixing python-sip4 via remove of python2.4-sip4-qt3
Done
Starting
Starting 2
Investigating libgl1-mesa-dri
Package libgl1-mesa-dri has broken dep on libgl1-mesa-glx
  Considering libgl1-mesa-glx 16 as a solution to libgl1-mesa-dri -1
  Holding Back libgl1-mesa-dri rather than change libgl1-mesa-glx
 Try to Re-Instate libgl1-mesa-dri
Done
Starting
Starting 2
Done

```

---

### Post by alex1973 on 2006-10-27
Then, I changed my sources.list. Used the original file from dapper and replaced "dapper" with "edgy". I executed:
$ sudo aptitude update && sudo aptitude dist-upgrade && sudo aptitude dist-upgrade

I have attached the log

---

