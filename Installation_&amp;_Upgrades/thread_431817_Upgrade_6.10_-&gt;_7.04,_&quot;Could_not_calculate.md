---
title: "Upgrade 6.10 -&gt; 7.04, &quot;Could not calculate the upgrade&quot;"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by GreenLight on 2007-05-03
I am trying to upgrade from Edgy to Feisty, using the alternate CD. I have to use the CD because I do not have broadband at home. On two separate systems, I get this error shortly after beginning the upgrade:

Could not calculate the upgrade
A unresolvable problem occurred while calculating the upgrade.
Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

Will filing a bug report do any good? Is anyone else experiencing this?

There are three files in the mentioned directory:
		apt.log (36K)
		main.log (6K)
		term.log (0K)

Contents of apt.log (shortened because the original length is too large):

gpgv: Signature made Sun 15 Apr 2007 09:44:07 AM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing libc6 as dep of mcpp
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

[snip -- length too long]

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
Installing cupsys-client as dep of cupsys-bsd
Installing update-inetd as dep of cupsys-bsd
Installing dmsetup as dep of libdevmapper1.02
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing python-apport as dep of apport
Installing python-problem-report as dep of python-apport
Installing python-launchpad-bugs as dep of python-apport
Installing libcaca0 as dep of gstreamer0.10-plugins-good
Installing libcucul0 as dep of libcaca0
Installing libvte9 as dep of gnome-terminal
Installing libvte-common as dep of libvte9
Installing gnome-terminal-data as dep of gnome-terminal
Installing myspell-en-za as dep of language-support-en
Installing e2fslibs as dep of e2fsprogs
Installing cpp-4.1 as dep of gcc-4.1
Installing binutils as dep of gcc-4.1
Installing upstart as dep of upstart-compat-sysv
Installing libpoppler1 as dep of libpoppler1-glib
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libx86-1 as dep of vbetool
Installing python-orca-brlapi as dep of gnome-orca
Installing libgail-gnome-module as dep of gnome-orca
Installing libxml-twig-perl as dep of libnet-dbus-perl
Installing gnome-mount as dep of gnome-volume-manager
Installing libgdiplus as dep of libmono-system1.0-cil
Installing libungif4g as dep of libgdiplus
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing python-gtk2 as dep of python-glade2
Installing python-bittorrent as dep of bittorrent
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
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libgda2-common as dep of libgda2-3
Installing liboobs-1-3 as dep of gnome-applets
Installing gnome-applets-data as dep of gnome-applets
Installing linux-restricted-modules-2.6.20-15-generic as dep of linux-restricted-modules-generic
Installing libusplash0 as dep of usplash
Installing gpgv as dep of gnupg
Starting
Starting 2
WARNING: Failed to read mirror file
Investigating libpng12-0
Package libpng12-0 has broken dep on libpng12-dev
  Considering libpng12-dev 4 as a solution to libpng12-0 1165
  Added libpng12-dev to the remove list
  Fixing libpng12-0 via remove of libpng12-dev
Investigating libx11-dev
Package libx11-dev has broken dep on libx11-6
  Considering libx11-6 4134 as a solution to libx11-dev 32
  Removing libx11-dev rather than change libx11-6
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 2797 as a solution to zlib1g-dev 26
  Removing zlib1g-dev rather than change zlib1g
Investigating libxext-dev
Package libxext-dev has broken dep on libxext6
  Considering libxext6 2522 as a solution to libxext-dev 24
  Removing libxext-dev rather than change libxext6
Investigating libvolume-id0
Package libvolume-id0 has broken dep on libvolumeid0
  Considering libvolumeid0 4 as a solution to libvolume-id0 20
  Added libvolumeid0 to the remove list
  Fixing libvolume-id0 via remove of libvolumeid0
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-modules
  Considering libsasl2-modules 30 as a solution to libsasl2 16
Package libsasl2 has broken dep on libsasl2-modules-sql
Package libsasl2 has broken dep on libsasl2-modules-gssapi-heimdal
Package libsasl2 has broken dep on libsasl2-modules-kerberos-heimdal
  Or group remove for libsasl2
Investigating libxau-dev
Package libxau-dev has broken dep on libxau6
  Considering libxau6 759 as a solution to libxau-dev 15
  Removing libxau-dev rather than change libxau6
Investigating kdebase-kio-plugins
Package kdebase-kio-plugins has broken dep on libsasl2
  Considering libsasl2 16 as a solution to kdebase-kio-plugins 13
  Removing kdebase-kio-plugins rather than change libsasl2
Investigating libxdmcp-dev
Package libxdmcp-dev has broken dep on libxdmcp6
  Considering libxdmcp6 432 as a solution to libxdmcp-dev 12
  Removing libxdmcp-dev rather than change libxdmcp6
Investigating x11proto-xext-dev
Package x11proto-xext-dev has broken dep on libxau-dev
  Considering libxau-dev 15 as a solution to x11proto-xext-dev 9
  Removing x11proto-xext-dev rather than change libxau-dev
Investigating libfreetype6-dev
Package libfreetype6-dev has broken dep on libfreetype6
  Considering libfreetype6 1424 as a solution to libfreetype6-dev 9
  Removing libfreetype6-dev rather than change libfreetype6
Investigating kdepim-kio-plugins
Package kdepim-kio-plugins has broken dep on libsasl2
  Considering libsasl2 16 as a solution to kdepim-kio-plugins 8
  Removing kdepim-kio-plugins rather than change libsasl2
Investigating libxrender-dev
Package libxrender-dev has broken dep on libxrender1
  Considering libxrender1 2325 as a solution to libxrender-dev 8
  Removing libxrender-dev rather than change libxrender1
Investigating libsm-dev
Package libsm-dev has broken dep on libsm6
  Considering libsm6 1342 as a solution to libsm-dev 7
  Removing libsm-dev rather than change libsm6
Investigating libice-dev
Package libice-dev has broken dep on libice6
  Considering libice6 1546 as a solution to libice-dev 7
  Removing libice-dev rather than change libice6
Investigating libfontconfig1-dev
Package libfontconfig1-dev has broken dep on libfontconfig1
  Considering libfontconfig1 1975 as a solution to libfontconfig1-dev 6
  Removing libfontconfig1-dev rather than change libfontconfig1
Investigating libqt3-mt-dev
Package libqt3-mt-dev has broken dep on libxext-dev
  Considering libxext-dev 24 as a solution to libqt3-mt-dev 6
  Removing libqt3-mt-dev rather than change libxext-dev
Investigating libxt-dev
Package libxt-dev has broken dep on libxt6
  Considering libxt6 888 as a solution to libxt-dev 6
  Removing libxt-dev rather than change libxt6
Investigating libgl1-mesa-dev
Package libgl1-mesa-dev has broken dep on libgl1-mesa-glx
  Considering libgl1-mesa-glx 119 as a solution to libgl1-mesa-dev 6
  Removing libgl1-mesa-dev rather than change libgl1-mesa-glx
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating libcupsys2-dev
Package libcupsys2-dev has broken dep on libcupsys2
  Considering libcupsys2 457 as a solution to libcupsys2-dev 6
  Removing libcupsys2-dev rather than change libcupsys2
Investigating konqueror
Package konqueror has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to konqueror 5
  Removing konqueror rather than change kdebase-kio-plugins
Investigating libaudiofile-dev
Package libaudiofile-dev has broken dep on libaudiofile0
  Considering libaudiofile0 144 as a solution to libaudiofile-dev 4
  Removing libaudiofile-dev rather than change libaudiofile0
Investigating libglib2.0-dev
Package libglib2.0-dev has broken dep on libglib2.0-0
  Considering libglib2.0-0 2352 as a solution to libglib2.0-dev 4
  Removing libglib2.0-dev rather than change libglib2.0-0
Investigating libgcrypt11-dev
Package libgcrypt11-dev has broken dep on libgcrypt11
  Considering libgcrypt11 98 as a solution to libgcrypt11-dev 4
  Removing libgcrypt11-dev rather than change libgcrypt11
Investigating libxi-dev
Package libxi-dev has broken dep on libxi6
  Considering libxi6 1526 as a solution to libxi-dev 4
  Removing libxi-dev rather than change libxi6
Investigating libogg-dev
Package libogg-dev has broken dep on libogg0
  Considering libogg0 111 as a solution to libogg-dev 4
  Removing libogg-dev rather than change libogg0
Investigating libxcursor-dev
Package libxcursor-dev has broken dep on libxcursor1
  Considering libxcursor1 1534 as a solution to libxcursor-dev 4
  Removing libxcursor-dev rather than change libxcursor1
Investigating libglu1-mesa-dev
Package libglu1-mesa-dev has broken dep on libglu1-mesa
  Considering libglu1-mesa 66 as a solution to libglu1-mesa-dev 4
  Removing libglu1-mesa-dev rather than change libglu1-mesa
Investigating libssl-dev
Package libssl-dev has broken dep on libssl0.9.8
  Considering libssl0.9.8 158 as a solution to libssl-dev 4
  Removing libssl-dev rather than change libssl0.9.8
Investigating libxmu-dev
Package libxmu-dev has broken dep on libxext-dev
  Considering libxext-dev 24 as a solution to libxmu-dev 4
  Removing libxmu-dev rather than change libxext-dev
Investigating libxml2-dev
Package libxml2-dev has broken dep on libxml2
  Considering libxml2 1268 as a solution to libxml2-dev 4
  Removing libxml2-dev rather than change libxml2
Investigating libasound2-dev
Package libasound2-dev has broken dep on libasound2
  Considering libasound2 363 as a solution to libasound2-dev 4
  Removing libasound2-dev rather than change libasound2
Investigating libxrandr-dev
Package libxrandr-dev has broken dep on libxrandr2
  Considering libxrandr2 1554 as a solution to libxrandr-dev 4
  Removing libxrandr-dev rather than change libxrandr2
Investigating libxft-dev
Package libxft-dev has broken dep on libxft2
  Considering libxft2 800 as a solution to libxft-dev 4
  Removing libxft-dev rather than change libxft2
Investigating libmng-dev
Package libmng-dev has broken dep on zlib1g-dev
  Considering zlib1g-dev 26 as a solution to libmng-dev 4
  Removing libmng-dev rather than change zlib1g-dev
Investigating libavahi-common-dev
Package libavahi-common-dev has broken dep on libavahi-common3
  Considering libavahi-common3 346 as a solution to libavahi-common-dev 4
  Removing libavahi-common-dev rather than change libavahi-common3
Investigating libxinerama-dev
Package libxinerama-dev has broken dep on libx11-dev
  Considering libx11-dev 32 as a solution to libxinerama-dev 4
  Removing libxinerama-dev rather than change libx11-dev
Investigating libidn11-dev
Package libidn11-dev has broken dep on libidn11
  Considering libidn11 389 as a solution to libidn11-dev 4
  Removing libidn11-dev rather than change libidn11
Investigating libgpg-error-dev
Package libgpg-error-dev has broken dep on libgpg-error0
  Considering libgpg-error0 128 as a solution to libgpg-error-dev 3
  Removing libgpg-error-dev rather than change libgpg-error0
Investigating kdebase
Package kdebase has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kdebase 3
  Removing kdebase rather than change kdebase-kio-plugins
Investigating kde-core
Package kde-core has broken dep on kdebase
  Considering kdebase 3 as a solution to kde-core 3
  Removing kde-core rather than change kdebase
Investigating apache2-common
Package apache2-common has broken dep on apache2-utils
  Considering apache2-utils 2 as a solution to apache2-common 3
  Added apache2-utils to the remove list
  Fixing apache2-common via keep of apache2-utils
Investigating libkrb5-dev
Package libkrb5-dev has broken dep on libkrb53
  Considering libkrb53 290 as a solution to libkrb5-dev 3
  Removing libkrb5-dev rather than change libkrb53
Investigating libgnutls-dev
Package libgnutls-dev has broken dep on libgnutls13
  Considering libgnutls13 602 as a solution to libgnutls-dev 3
  Removing libgnutls-dev rather than change libgnutls13
Investigating libexpat1-dev
Package libexpat1-dev has broken dep on libexpat1
  Considering libexpat1 307 as a solution to libexpat1-dev 3
  Removing libexpat1-dev rather than change libexpat1
Investigating libpopt-dev
Package libpopt-dev has broken dep on libpopt0
  Considering libpopt0 453 as a solution to libpopt-dev 2
  Removing libpopt-dev rather than change libpopt0
Investigating korn
Package korn has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to korn 2
Package korn has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to korn 2
  Or group remove for korn
Investigating kdelibs4-dev
Package kdelibs4-dev has broken dep on libasound2-dev
  Considering libasound2-dev 4 as a solution to kdelibs4-dev 2
  Removing kdelibs4-dev rather than change libasound2-dev
 Try to Re-Instate apache2-utils
Investigating kdemultimedia-dev
Package kdemultimedia-dev has broken dep on kdelibs4-dev
  Considering kdelibs4-dev 2 as a solution to kdemultimedia-dev 2
  Removing kdemultimedia-dev rather than change kdelibs4-dev
Investigating libtasn1-3-dev
Package libtasn1-3-dev has broken dep on libtasn1-3
  Considering libtasn1-3 48 as a solution to libtasn1-3-dev 2
  Removing libtasn1-3-dev rather than change libtasn1-3
Investigating libpcre3-dev
Package libpcre3-dev has broken dep on libpcre3
  Considering libpcre3 245 as a solution to libpcre3-dev 2
  Removing libpcre3-dev rather than change libpcre3
Investigating libopencdk8-dev
Package libopencdk8-dev has broken dep on libopencdk8
  Considering libopencdk8 43 as a solution to libopencdk8-dev 2
  Removing libopencdk8-dev rather than change libopencdk8
Investigating libpoppler1-qt
Package libpoppler1-qt has broken dep on libpoppler1
  Considering libpoppler1 16 as a solution to libpoppler1-qt 2
  Removing libpoppler1-qt rather than change libpoppler1
Investigating libxmu-headers
Package libxmu-headers has broken dep on libx11-dev
  Considering libx11-dev 32 as a solution to libxmu-headers 2
  Removing libxmu-headers rather than change libx11-dev
Investigating libsasl2-dev
Package libsasl2-dev has broken dep on libsasl2
  Considering libsasl2 16 as a solution to libsasl2-dev 2
  Removing libsasl2-dev rather than change libsasl2
Investigating libavahi-client-dev
Package libavahi-client-dev has broken dep on libavahi-client3
  Considering libavahi-client3 320 as a solution to libavahi-client-dev 2
  Removing libavahi-client-dev rather than change libavahi-client3
Investigating human-theme
Package human-theme has broken dep on human-gtk-theme
  Considering human-gtk-theme 0 as a solution to human-theme 2
  Added human-gtk-theme to the remove list
  Fixing human-theme via remove of human-gtk-theme
Investigating libavahi-qt3-dev
Package libavahi-qt3-dev has broken dep on libqt3-mt-dev
  Considering libqt3-mt-dev 6 as a solution to libavahi-qt3-dev 2
  Removing libavahi-qt3-dev rather than change libqt3-mt-dev
Investigating libxslt1-dev
Package libxslt1-dev has broken dep on libxslt1.1
  Considering libxslt1.1 293 as a solution to libxslt1-dev 2
  Removing libxslt1-dev rather than change libxslt1.1
Investigating libdbus-1-dev
Package libdbus-1-dev has broken dep on libdbus-1-3
  Considering libdbus-1-3 430 as a solution to libdbus-1-dev 2
  Removing libdbus-1-dev rather than change libdbus-1-3
Investigating libtiff4-dev
Package libtiff4-dev has broken dep on zlib1g-dev
  Considering zlib1g-dev 26 as a solution to libtiff4-dev 2
  Removing libtiff4-dev rather than change zlib1g-dev
Investigating libesd0-dev
Package libesd0-dev has broken dep on libesd-alsa0
  Considering libesd-alsa0 137 as a solution to libesd0-dev 2
Package libesd0-dev has broken dep on libesd0
  Or group remove for libesd0-dev
Package libesd0-dev has broken dep on libaudiofile-dev
  Considering libaudiofile-dev 4 as a solution to libesd0-dev 2
  Removing libesd0-dev rather than change libaudiofile-dev
Investigating x11proto-fixes-dev
Package x11proto-fixes-dev has broken dep on x11proto-xext-dev
  Considering x11proto-xext-dev 9 as a solution to x11proto-fixes-dev 2
  Removing x11proto-fixes-dev rather than change x11proto-xext-dev
Investigating konq-plugins
Package konq-plugins has broken dep on konqueror
  Considering konqueror 5 as a solution to konq-plugins 2
  Removing konq-plugins rather than change konqueror
Investigating libkadm55
Package libkadm55 has broken dep on libkrb53
  Considering libkrb53 290 as a solution to libkadm55 2
  Removing libkadm55 rather than change libkrb53
Investigating libarts1-audiofile
Package libarts1-audiofile has broken dep on kdemultimedia-dev
  Considering kdemultimedia-dev 2 as a solution to libarts1-audiofile 2
  Removing libarts1-audiofile rather than change kdemultimedia-dev
Investigating libncurses5-dev
Package libncurses5-dev has broken dep on libncurses5
  Considering libncurses5 628 as a solution to libncurses5-dev 2
  Removing libncurses5-dev rather than change libncurses5
Investigating libopenexr-dev
Package libopenexr-dev has broken dep on xlibmesa-gl-dev
Package libopenexr-dev has broken dep on libgl-dev
  Considering libgl1-mesa-dev 6 as a solution to libopenexr-dev 2
  Or group remove for libopenexr-dev
Package libopenexr-dev has broken dep on xlibmesa-glu-dev
Package libopenexr-dev has broken dep on libglu-dev
  Considering libglu1-mesa-dev 4 as a solution to libopenexr-dev 2
  Or group remove for libopenexr-dev
Investigating libartsc0-dev
Package libartsc0-dev has broken dep on libglib2.0-dev
  Considering libglib2.0-dev 4 as a solution to libartsc0-dev 2
  Removing libartsc0-dev rather than change libglib2.0-dev
Investigating python-apport
Package python-apport has broken dep on python-apport-utils
  Considering python-apport-utils 0 as a solution to python-apport 2
  Added python-apport-utils to the remove list
  Fixing python-apport via remove of python-apport-utils
Investigating libxfixes-dev
Package libxfixes-dev has broken dep on libxfixes3
  Considering libxfixes3 1148 as a solution to libxfixes-dev 2
  Removing libxfixes-dev rather than change libxfixes3
Investigating libvorbis-dev
Package libvorbis-dev has broken dep on libogg-dev
  Considering libogg-dev 4 as a solution to libvorbis-dev 2
  Removing libvorbis-dev rather than change libogg-dev
Investigating libbz2-dev
Package libbz2-dev has broken dep on libbz2-1.0
  Considering libbz2-1.0 314 as a solution to libbz2-dev 2
  Removing libbz2-dev rather than change libbz2-1.0
Investigating libarts1-dev
Package libarts1-dev has broken dep on libartsc0-dev
  Considering libartsc0-dev 2 as a solution to libarts1-dev 2
  Removing libarts1-dev rather than change libartsc0-dev
Investigating kde-amusements
Package kde-amusements has broken dep on kde-core
  Considering kde-core 3 as a solution to kde-amusements 1
  Removing kde-amusements rather than change kde-core
Investigating kdepim
Package kdepim has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kdepim 1
  Removing kdepim rather than change kdepim-kio-plugins
Investigating feisty-wallpapers
Package feisty-wallpapers has broken dep on edgy-wallpapers
  Considering edgy-wallpapers 0 as a solution to feisty-wallpapers 1
  Added edgy-wallpapers to the remove list
  Fixing feisty-wallpapers via remove of edgy-wallpapers
Investigating comerr-dev
Package comerr-dev has broken dep on libcomerr2
  Considering libcomerr2 426 as a solution to comerr-dev 1
  Removing comerr-dev rather than change libcomerr2
Investigating kdeaddons
Package kdeaddons has broken dep on konq-plugins
  Considering konq-plugins 2 as a solution to kdeaddons 1
  Removing kdeaddons rather than change konq-plugins
Investigating kdemultimedia
Package kdemultimedia has broken dep on libarts1-audiofile
  Considering libarts1-audiofile 2 as a solution to kdemultimedia 1
  Removing kdemultimedia rather than change libarts1-audiofile
Investigating libcurl3-openssl-dev
Package libcurl3-openssl-dev has broken dep on libcurl3
  Considering libcurl3 22 as a solution to libcurl3-openssl-dev 1
  Removing libcurl3-openssl-dev rather than change libcurl3
Investigating feisty-session-splashes
Package feisty-session-splashes has broken dep on edgy-session-splashes
  Considering edgy-session-splashes 0 as a solution to feisty-session-splashes 1
  Added edgy-session-splashes to the remove list
  Fixing feisty-session-splashes via remove of edgy-session-splashes
Investigating feisty-gdm-themes
Package feisty-gdm-themes has broken dep on edgy-gdm-themes
  Considering edgy-gdm-themes 0 as a solution to feisty-gdm-themes 1
  Added edgy-gdm-themes to the remove list
  Fixing feisty-gdm-themes via remove of edgy-gdm-themes
Investigating openoffice.org-style-default
Package openoffice.org-style-default has broken dep on openoffice.org-common
  Considering openoffice.org-common 32 as a solution to openoffice.org-style-default 0
  Removing openoffice.org-style-default rather than change openoffice.org-common
Investigating perl-debug
Package perl-debug has broken dep on perl
  Considering perl 447 as a solution to perl-debug 0
  Removing perl-debug rather than change perl
Investigating openoffice.org-style-industrial
Package openoffice.org-style-industrial has broken dep on openoffice.org-common
  Considering openoffice.org-common 32 as a solution to openoffice.org-style-industrial 0
  Removing openoffice.org-style-industrial rather than change openoffice.org-common
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 562 as a solution to python-dev 0
  Removing python-dev rather than change python
Investigating libreadline5-dev
Package libreadline5-dev has broken dep on libreadline5
  Considering libreadline5 82 as a solution to libreadline5-dev 0
  Removing libreadline5-dev rather than change libreadline5
Investigating libspeex-dev
Package libspeex-dev has broken dep on libspeex1
  Considering libspeex1 18 as a solution to libspeex-dev 0
  Removing libspeex-dev rather than change libspeex1
Investigating kde
Package kde has broken dep on kde-core
  Considering kde-core 3 as a solution to kde 0
  Removing kde rather than change kde-core
Investigating libedit-dev
Package libedit-dev has broken dep on libncurses5-dev
  Considering libncurses5-dev 2 as a solution to libedit-dev 0
  Removing libedit-dev rather than change libncurses5-dev
Investigating knights
Package knights has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to knights 0
  Removing knights rather than change kdebase-kio-plugins
Investigating libcurl3-dev
Package libcurl3-dev has broken dep on libcurl3-openssl-dev
  Considering libcurl3-openssl-dev 1 as a solution to libcurl3-dev 0
  Removing libcurl3-dev rather than change libcurl3-openssl-dev
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating kdegraphics-kfile-plugins
Package kdegraphics-kfile-plugins has broken dep on libpoppler1-qt
  Considering libpoppler1-qt 2 as a solution to kdegraphics-kfile-plugins 2
  Removing kdegraphics-kfile-plugins rather than change libpoppler1-qt
Investigating kdegraphics
Package kdegraphics has broken dep on kdegraphics-kfile-plugins
  Considering kdegraphics-kfile-plugins 2 as a solution to kdegraphics 1
  Removing kdegraphics rather than change kdegraphics-kfile-plugins
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Investigating kmail
Package kmail has broken dep on kdepim-kio-plugins
  Considering kdepim-kio-plugins 8 as a solution to kmail 6
Package kmail has broken dep on kdebase-kio-plugins
  Considering kdebase-kio-plugins 13 as a solution to kmail 6
  Or group remove for kmail
Package kmail has broken dep on bogofilter
Done

Contents of main.log:

2007-04-23 21:20:23,321 INFO release-upgrader version '0.59.19' started
2007-04-23 21:20:24,036 DEBUG lsb-release: 'edgy'
2007-04-23 21:20:24,037 DEBUG _pythonSymlinkCheck run
2007-04-23 21:20:33,794 DEBUG useNetwork: 'False' (selected by user)
2007-04-23 21:20:33,795 DEBUG doUpdate() will not use the network because self.useNetwork==false
2007-04-23 21:20:34,556 DEBUG Foreign: 
2007-04-23 21:20:34,556 DEBUG Obsolete: libmono-cairo1.0-cil kdebase-bin libavahi-common3 libavahi-core4 totem libedataserverui1.2-8 libfreetype6-dev evince mysql-common libavahi-client-dev linux-headers-2.6.17-11 gimp-python vmware-player-kernel-modules-2.6.17-11 gdm libmysqlclient15off openoffice.org-style-industrial xserver-xorg ttf-opensymbol postgresql-client-8.1 libmono1.0-cil kcontrol linux-headers-2.6.17-10-generic kdebase-data avahi-daemon openoffice.org-core gimp-data mono-runtime app-install-data-commercial libmono-system-data1.0-cil openoffice.org-evolution kdesktop kdebase gnome-games-data klipper linux-image-generic mysql-client-5.0 openoffice.org-style-default kdelibs4-dev krdc gnome-system-tools libpoppler1 libmagick9 libmono-security1.0-cil libgtk2.0-0 clamav-freshclam ksysguardd libgtop2-common bind9-host libpoppler1-qt konqueror evolution linux-restricted-modules-2.6.17-10-generic openoffice.org-writer ruby1.8-examples libisccc0 dbus python-imaging gnome-control-center kappfinder kpf libgnomeprintui2.2-common liblwres9 libpng12-dev kdebase-kio-plugins libavahi-qt3-1 squid-common konqueror-nsplugins libgimp2.0 libpng12-0 update-manager libnspr4 kdnssd kwin udev libmono-system1.0-cil mysql-server-5.0 linux-libc-dev libc6-i686 libmono-system-web1.0-cil openoffice.org-impress openoffice.org-base clamav-base language-pack-en libkrb5-dev libebook1.2-9 libwpd8c2a kate libpoppler1-glib libqt3-mt-dev libqt3-mt-mysql libgnome-window-settings1 mono-common openoffice.org-gnome libcamel1.2-8 libdns21 libmagic1 imagemagick libclamav1 xserver-xorg-core linux-source libsoup2.2-8 screen ksmserver clamav gnome-panel gnome-games knewsticker dbus-1-utils kmenuedit krfb kopete openoffice.org-common libgnomevfs2-0 dnsutils totem-gstreamer kdict postgresql-8.1 evolution-data-server nautilus-data capplets-data linux-generic volumeid kpersonalizer libbind9-0 libmono-data-tds1.0-cil language-pack-gnome-en smbclient slocate libxfont1 ekiga kicker libaudio2 librss1 firefox poppler-utils libqt3-headers libx11-data libdbus-1-3 libdbus-1-dev khelpcenter libkonq4 gnome-applets xserver-xorg-video-all libkadm55 libgtk2.0-bin libnss3 vmware-player-kernel-modules xbase-clients libedata-book1.2-2 libedataserver1.2-7 openoffice.org openoffice.org-java-common libsmbclient kdelibs-data w3m gnupg2 tzdata xutils gnome-panel-data libavahi-compat-libdnssd1 libpq4 libexchange-storage1.2-2 x11-common tcpdump linux-headers-2.6.17-10 libswt3.2-gtk-java libqt3-mt libegroupwise1.2-12 libgsf-1-common libavahi-common-dev openoffice.org-math openoffice.org-calc qt3-dev-tools libkrb53 libpanel-applet2-0 kfind kdenetwork-kfile-plugins kpager ksysguard python-uno libgnomevfs2-common libruby1.8 libnautilus-extension1 info firefox-themes-ubuntu evolution-data-server-common libavahi-qt3-dev libxine1 squid libgtop2-7 ubuntu-docs libmono-sharpzip0.84-cil libx11-dev linux-image-2.6.17-10-generic kwifimanager gnupg ksplash gnome-netstatus-applet xserver-xorg-input-all libavahi-glib1 totem-mozilla libaudio-dev kdelibs4c2a nautilus file tar firefox-gnome-support gpgsm ksirc gnupg-agent libfreetype6 linux-image-2.6.17-11-generic libswt3.2-gtk-jni ktip libgnomeprintui2.2-0 samba-common libmono-corlib1.0-cil kppp linux-restricted-modules-common libgnomevfs2-extra linux-source-2.6.17 openoffice.org-draw libisc11 libtotem-plparser1 libmono-sqlite1.0-cil gnome-applets-data ruby1.8 libmono0 linux-headers-generic kget libgnomevfs2-bin libgtk2.0-common gimp libavahi-client3 dcoprss libx11-6 mysql-client mono-jit update-notifier popularity-contest konsole ruby1.8-dev libc6-dev linux-restricted-modules-2.6.17-11-generic libavahi-common-data mono-gac xorg libc6 libecal1.2-7 linux-headers-2.6.17-11-generic kdenetwork kdepasswd libvolumeid0 libisccfg1 kdelibs openoffice.org-gtk libedata-cal1.2-6 libgsf-1-114 libgpgme11 system-tools-backends linux-restricted-modules-generic kdeprint vino evolution-plugins
2007-04-23 21:20:34,558 DEBUG updateSourcesList()
2007-04-23 21:20:34,610 DEBUG rewriteSourcesList()
2007-04-23 21:20:34,611 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted'
2007-04-23 21:20:34,611 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe main multiverse restricted' updated to new dist
2007-04-23 21:20:34,612 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties'
2007-04-23 21:20:34,612 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe main multiverse restricted #Added by software-properties' updated to new dist
2007-04-23 21:20:34,619 DEBUG AptCdrom.add() called with '/media/cdrom0'
2007-04-23 21:20:49,749 DEBUG AptCdrom.add() returned: 1
2007-04-23 21:20:49,749 DEBUG doUpdate() will not use the network because self.useNetwork==false

---

### Post by thug007 on 2007-05-04
I have exactly the same cicumstances (except only one computer!) but a different error - please see my "Upgrade to 7.04 gone to sleep" thread in the General Help  forum.

Have U seen the upgrade fix proposed in post #3 of the "Feisty (7.04) Upgrade Problems - Fix" thread of user finalzero  in this forum ?  

Very messy situation indeed - I think there must be many of us but it is difficult to devise a unifying thread title to look for in the forum.

After 2 days I am stiil forlornly hoping to be able to stop the upgrade (still hanging) without borking 6.10.

Regards,
              thug007

---

