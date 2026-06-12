---
title: "[SOLVED] Cannot upgrade from 7.04 to 7.10 (package manager error)"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Airos on 2007-10-24
Okay, I give up!

I've been trying for almost a week now, and I cannot get 7.04 to upgrade to 7.10. I believe my problems are connected to this bug here; [https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296]("https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296")

My system is a Pentium 4 2.0 gHz with 512 mb of ram and an ATI Radeon all-in-wonder 9700 with 128 mb of ram.

The problem begins here...

[ATTACH]47562[/ATTACH]

No matter *how* I try to upgrade, (update manager, live cd, alternate cd), I get this same error. It occurs directly after informing me;

```
Support for some applications ended

Canonical Ltd. no longer provides support for the following software packages. You can still get support from the community.

If you have not enabled community maintained software (universe), these packages will be suggested for removal at the end of the upgrade.

binfmt-support
feisty-session-splashes
festlex-cmu
festlex-poslex
festvox-kallpc16k
gcj-4.1-base
gij-4.1
gnome-cups-manager
libdb3
libgcj7-jar
libgda2-3
libgda2-common
libglib1.2
libgnomecupsui1.0-1c2a
libgtk1.2
libgtk1.2-common
liblzo1
libportaudio0
libslab0
libstlport5.1
libxml1
libxmlsec1
libxmlsec1-nss
libxmlsec1-openssl
openoffice.org-filter-mobiledev
pmount
ttf-baekmuk
vnc-common
xarchiver
xvncviewer
```

Since it's been turning off third-party support during the setup anyways, I've tried modifying my sources;

[ATTACH]47563[/ATTACH]

[ATTACH]47564[/ATTACH]

[ATTACH]47565[/ATTACH]

I've gone as far as turning off *all* the sources on those lists. I've unplugged the computer from the internet. I've tried modifying the python script as suggested in one of the bug forums. 

Here's the .log files found in /var/log/dist-upgrade

apt.log
```
Installing python-central as dep of python-crypto
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
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libndesk-dbus-glib1.0-cil as dep of f-spot
Installing libndesk-dbus1.0-cil as dep of libndesk-dbus-glib1.0-cil
Installing libpopt0 as dep of libpopt-dev
Installing libcupsys2 as dep of libgnomecupsui1.0-1c2a
Installing libgcc1 as dep of libgnomecupsui1.0-1c2a
Installing gcc-4.1-base as dep of libgcc1
Installing libstdc++6 as dep of libgnomecupsui1.0-1c2a
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdirectfb-0.9-25 as dep of libsdl1.2debian-alsa
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-0 as dep of libgcj7-jar
Installing libgcj-common as dep of libgcj7-0
Installing xserver-xorg-core as dep of xserver-xorg-video-rendition
Installing libdrm2 as dep of xserver-xorg-core
Installing python-twisted-core as dep of python-twisted-names
Installing python-twisted-bin as dep of python-twisted-core
Installing libgail-common as dep of libgtkhtml3.8-15
Installing libgail18 as dep of libgail-common
Installing libgnomeprint2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing libgnomeprintui2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libwxgtk2.4-1 as dep of libwxgtk2.4-1-contrib
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
Installing python2.4 as dep of python2.4-dev
Installing python2.4-minimal as dep of python2.4
Installing libreadline5 as dep of python2.4
Installing python2.5 as dep of update-manager
Installing python2.5-minimal as dep of python2.5
Installing libsqlite3-0 as dep of python2.5
Installing update-manager-core as dep of update-manager
Installing libwps-0.1-1 as dep of openoffice.org-writer
Installing python-uno as dep of openoffice.org-writer
Installing python as dep of python-uno
Installing python-minimal as dep of python
Installing libgs-esp8 as dep of gs-esp
Installing libcupsimage2 as dep of libgs-esp8
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
Installing metacity-common as dep of metacity
Installing libbeagle0 as dep of nautilus
Installing libeel2-2 as dep of nautilus
Installing libeel2-data as dep of libeel2-2
Installing libnautilus-extension1 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing libdns22 as dep of bind9-host
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing gnome-user-guide as dep of ubuntu-docs
Installing linux-headers-2.6.20-16-generic as dep of linux-headers-generic
Installing linux-headers-2.6.20-16 as dep of linux-headers-2.6.20-16-generic
Installing dhcp3-common as dep of dhcp3-client
Installing libatspi1.0-0 as dep of python-at-spi
Installing libdb3 as dep of gnome-bin
Installing libxine1-ffmpeg as dep of libxine-extracodecs
Installing libxine1 as dep of libxine1-ffmpeg
Installing libpulse0 as dep of libxine1
Installing amule-common as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing libcurl3-gnutls as dep of vorbis-tools
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
Installing libtotem-plparser1 as dep of python-gnome2-desktop
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
Installing linux-image-2.6.20-16-generic as dep of linux-image-generic
Installing gnome-libs-data as dep of libgnome32
Installing libgnomekbd1 as dep of gnome-screensaver
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libgnomekbdui1 as dep of gnome-screensaver
Installing libxcomposite1 as dep of gnome-mag
Installing libgpod1 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libsnmp9 as dep of libsnmp9-dev
Installing libsnmp-base as dep of libsnmp9
Installing libsnmp-perl as dep of libsnmp9-dev
Installing libgcrypt11 as dep of libgcrypt11-dev
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing gnome-panel-data as dep of gnome-panel
Installing genisoimage as dep of dvd+rw-tools
Installing libfreebob0 as dep of libjack0.100.0-0
Installing libcaca0 as dep of mplayer
Installing libcucul0 as dep of libcaca0
Installing feisty-gdm-themes as dep of ubuntu-artwork
Installing feisty-session-splashes as dep of ubuntu-artwork
Installing feisty-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libslab0 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing cupsys-client as dep of cupsys-bsd
Installing update-inetd as dep of cupsys-bsd
Installing python2.5-dev as dep of python-dev
Installing dmsetup as dep of libdevmapper1.02
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing python-apport as dep of apport
Installing python-problem-report as dep of python-apport
Installing python-launchpad-bugs as dep of python-apport
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing boo as dep of banshee
Installing libipoddevice0 as dep of banshee
Installing libmono1.0-cil as dep of banshee
Installing libipodui-cil as dep of banshee
Installing libipod-cil as dep of libipodui-cil
Installing libvte9 as dep of gnome-terminal
Installing libvte-common as dep of libvte9
Installing gnome-terminal-data as dep of gnome-terminal
Installing myspell-en-za as dep of language-support-en
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libpoppler1 as dep of libpoppler1-glib
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libx86-1 as dep of vbetool
Installing singularity-data as dep of singularity
Installing python-orca-brlapi as dep of gnome-orca
Installing libgail-gnome-module as dep of gnome-orca
Installing libxml-twig-perl as dep of libnet-dbus-perl
Installing python-sip4 as dep of python-qt3
Installing libgcj7-dev as dep of gcj-4.1
Installing libgcj7-awt as dep of libgcj7-dev
Installing ecj-bootstrap as dep of gcj-4.1
Installing ecj as dep of ecj-bootstrap
Installing gnome-mount as dep of gnome-volume-manager
Installing libgdiplus as dep of libmono-system1.0-cil
Installing gij as dep of gcj
Installing hal-info as dep of hal
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing python-gtk2 as dep of python-glade2
Installing libgii1-target-x as dep of libgii1
Installing python-bittorrent as dep of bittorrent
Installing language-selector-common as dep of language-selector
Installing openoffice.org-filter-mobiledev as dep of openoffice.org
Installing cupsys as dep of cupsys-driver-gutenprint
Installing libjaxp1.3-java as dep of libxerces2-java
Installing libbonobo2-common as dep of libbonobo2-0
Installing gs-esp-x as dep of evince
Installing zlib1g as dep of zlib1g-dev
Installing libmagic1 as dep of file
Installing software-properties-gtk as dep of gnome-app-install
Installing python-software-properties as dep of software-properties-gtk
Installing libmikmod2 as dep of gweled
Installing libcdaudio1 as dep of gstreamer0.10-plugins-bad
Installing libsoundtouch1c2 as dep of gstreamer0.10-plugins-bad
Installing libwavpack1 as dep of gstreamer0.10-plugins-bad
Installing debconf as dep of tasksel
Installing gimp-data as dep of gimp
Installing libespeak1 as dep of libgnome-speech3
Installing espeak-data as dep of libespeak1
Installing mscompress as dep of foo2zjs
Installing holotz-castle-data as dep of holotz-castle
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libgda2-common as dep of libgda2-3
Installing liboobs-1-3 as dep of gnome-applets
Installing gnome-applets-data as dep of gnome-applets
Installing libnfsidmap2 as dep of nfs-kernel-server
Installing librpcsecgss3 as dep of nfs-kernel-server
Installing linux-restricted-modules-2.6.20-16-generic as dep of linux-restricted-modules-generic
Installing libusplash0 as dep of usplash
Installing gpgv as dep of gnupg
Starting
Starting 2
WARNING: Failed to read mirror file
Investigating libvolume-id0
Package libvolume-id0 has broken dep on libvolumeid0
  Considering libvolumeid0 4 as a solution to libvolume-id0 18
  Added libvolumeid0 to the remove list
  Fixing libvolume-id0 via remove of libvolumeid0
Investigating libnfsidmap2
Package libnfsidmap2 has broken dep on libnfsidmap1
  Considering libnfsidmap1 2 as a solution to libnfsidmap2 2
  Holding Back libnfsidmap2 rather than change libnfsidmap1
Investigating python-apport
Package python-apport has broken dep on python-apport-utils
  Considering python-apport-utils 0 as a solution to python-apport 2
  Added python-apport-utils to the remove list
  Fixing python-apport via remove of python-apport-utils
Investigating human-theme
Package human-theme has broken dep on human-gtk-theme
  Considering human-gtk-theme 0 as a solution to human-theme 1
  Added human-gtk-theme to the remove list
  Fixing human-theme via remove of human-gtk-theme
Investigating nfs-common
Package nfs-common has broken dep on libnfsidmap2
  Considering libnfsidmap2 2 as a solution to nfs-common 1
  Holding Back nfs-common rather than change libnfsidmap2
Investigating nfs-kernel-server
Package nfs-kernel-server has broken dep on libnfsidmap2
  Considering libnfsidmap2 2 as a solution to nfs-kernel-server 0
  Holding Back nfs-kernel-server rather than change libnfsidmap2
 Try to Re-Instate nfs-common
 Try to Re-Instate nfs-kernel-server
Done
Installing avahi-autoipd as dep of ubuntu-desktop
Installing dcraw as dep of ubuntu-desktop
Installing desktop-effects as dep of ubuntu-desktop
Installing compiz as dep of desktop-effects
Installing compiz-core as dep of compiz
Installing compiz-plugins as dep of compiz
Installing libdecoration0 as dep of compiz-plugins
Installing compiz-gtk as dep of compiz
Installing compiz-gnome as dep of compiz
Installing foomatic-db-hpijs as dep of ubuntu-desktop
Installing hpijs as dep of foomatic-db-hpijs
Installing gtk2-engines-pixbuf as dep of ubuntu-desktop
Installing libnss-mdns as dep of ubuntu-desktop
Installing openprinting-ppds as dep of ubuntu-desktop
Installing espeak as dep of ubuntu-desktop
Installing network-manager-gnome as dep of ubuntu-desktop
Installing libnm-util0 as dep of network-manager-gnome
Installing network-manager as dep of network-manager-gnome
Installing libnl1-pre6 as dep of network-manager
Installing dhcdbd as dep of network-manager
Installing restricted-manager as dep of ubuntu-desktop
Installing python-notify as dep of restricted-manager
Installing scim-tables-additional as dep of ubuntu-desktop
Installing scim-modules-table as dep of scim-tables-additional
/usr/bin/diff: /etc/hp/hplip.conf: No such file or directory
/usr/bin/diff: /etc/init.d/hplip: No such file or directory
Starting
Starting 2
Investigating nfs-common
Package nfs-common has broken dep on libnfsidmap2
  Considering libnfsidmap2 1 as a solution to nfs-common 1
  Re-Instated libnfsidmap2
  Re-Instated nfs-common
Done
Starting
Starting 2
Investigating libcamel1.2-8
Package libcamel1.2-8 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10002 as a solution to libcamel1.2-8 0
  Removing libcamel1.2-8 rather than change libedataserver1.2-7
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10002 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Starting
Starting 2
Investigating nfs-common
Package nfs-common has broken dep on libnfsidmap2
  Considering libnfsidmap2 1 as a solution to nfs-common 1
  Re-Instated libnfsidmap2
  Re-Instated nfs-common
Investigating libnfsidmap2
Package libnfsidmap2 has broken dep on libnfsidmap1
  Considering libnfsidmap1 2 as a solution to libnfsidmap2 1
  Holding Back libnfsidmap2 rather than change libnfsidmap1
Investigating nfs-common
Package nfs-common has broken dep on libnfsidmap2
  Considering libnfsidmap2 1 as a solution to nfs-common 1
  Removing nfs-common rather than change libnfsidmap2
Investigating nfs-kernel-server
Package nfs-kernel-server has broken dep on nfs-common
  Considering nfs-common 1 as a solution to nfs-kernel-server 0
    Reinst Failed because of nfs-common
  Removing nfs-kernel-server rather than change nfs-common
Done
Starting
Starting 2
Investigating linux-headers-2.6.17-10-generic
Package linux-headers-2.6.17-10-generic has broken dep on linux-headers-2.6.17-10
  Considering linux-headers-2.6.17-10 10001 as a solution to linux-headers-2.6.17-10-generic 0
  Removing linux-headers-2.6.17-10-generic rather than change linux-headers-2.6.17-10
Done
Starting
Starting 2
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10001 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Installing libnfsidmap2 as dep of nfs-kernel-server
Starting
Starting 2
Investigating libnfsidmap2
Package libnfsidmap2 has broken dep on libnfsidmap1
  Considering libnfsidmap1 1 as a solution to libnfsidmap2 2
  Added libnfsidmap1 to the remove list
  Fixing libnfsidmap2 via remove of libnfsidmap1
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
ERROR:root:gor error from PostInstallScript ./apt-autoinst-fixup.py ([Errno 2] No such file or directory: './apt-autoinst-fixup.py')
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing cpp-4.1 as dep of gcc-4.1
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13050 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing cpp-4.1 as dep of gcc-4.1
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13050 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing cpp-4.1 as dep of gcc-4.1
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13050 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing cpp-4.1 as dep of gcc-4.1
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13050 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing cpp-4.1 as dep of gcc-4.1
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13101 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13147 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13147 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
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
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing cupsys-client as dep of cupsys-bsd
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing videotrans as dep of qdvdauthor
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 128
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 18
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 18
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libmjpegtools0c2a
Package libmjpegtools0c2a has broken dep on libquicktime1
Investigating libxine1-ffmpeg
Package libxine1-ffmpeg has broken dep on libxine1
  Considering libxine1 26 as a solution to libxine1-ffmpeg 4
  Removing libxine1-ffmpeg rather than change libxine1
Investigating mjpegtools
Package mjpegtools has broken dep on libquicktime1
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 57 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 1
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 0 as a solution to python-soya 1
  Added libglew1 to the remove list
  Fixing python-soya via keep of libglew1
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
Investigating gaim
Package gaim has broken dep on libnss3
  Considering libnss3 1 as a solution to gaim -1
  Removing gaim rather than change libnss3
Investigating xine-ui
Package xine-ui has broken dep on libxine1-ffmpeg
  Considering libxine1-ffmpeg 4 as a solution to xine-ui -1
  Removing xine-ui rather than change libxine1-ffmpeg
Investigating libxine-extracodecs
Package libxine-extracodecs has broken dep on libxine1-ffmpeg
  Considering libxine1-ffmpeg 4 as a solution to libxine-extracodecs -2
  Removing libxine-extracodecs rather than change libxine1-ffmpeg
 Try to Re-Instate libmjpegtools0c2a
 Try to Re-Instate mjpegtools
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 0 as a solution to python-soya 1
  Added libglew1 to the remove list
  Fixing python-soya via keep of libglew1
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 1 as a solution to python-soya 1
  Removing python-soya rather than change libglew1
Investigating balazar
Package balazar has broken dep on python-soya
  Considering python-soya 1 as a solution to balazar -1
  Removing balazar rather than change python-soya
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13028 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
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
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing cupsys-client as dep of cupsys-bsd
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing videotrans as dep of qdvdauthor
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 128
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 4 as a solution to ghostscript 18
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 2 as a solution to ghostscript 18
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libmjpegtools0c2a
Package libmjpegtools0c2a has broken dep on libquicktime1
Investigating libxine1-ffmpeg
Package libxine1-ffmpeg has broken dep on libxine1
  Considering libxine1 26 as a solution to libxine1-ffmpeg 4
  Removing libxine1-ffmpeg rather than change libxine1
Investigating mjpegtools
Package mjpegtools has broken dep on libquicktime1
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 57 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 1
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 0 as a solution to python-soya 1
  Added libglew1 to the remove list
  Fixing python-soya via keep of libglew1
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
Investigating gaim
Package gaim has broken dep on libnss3
  Considering libnss3 1 as a solution to gaim -1
  Removing gaim rather than change libnss3
Investigating xine-ui
Package xine-ui has broken dep on libxine1-ffmpeg
  Considering libxine1-ffmpeg 4 as a solution to xine-ui -1
  Removing xine-ui rather than change libxine1-ffmpeg
Investigating libxine-extracodecs
Package libxine-extracodecs has broken dep on libxine1-ffmpeg
  Considering libxine1-ffmpeg 4 as a solution to libxine-extracodecs -2
  Removing libxine-extracodecs rather than change libxine1-ffmpeg
 Try to Re-Instate libmjpegtools0c2a
 Try to Re-Instate mjpegtools
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 0 as a solution to python-soya 1
  Added libglew1 to the remove list
  Fixing python-soya via keep of libglew1
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 1 as a solution to python-soya 1
  Removing python-soya rather than change libglew1
Investigating balazar
Package balazar has broken dep on python-soya
  Considering python-soya 1 as a solution to balazar -1
  Removing balazar rather than change python-soya
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13028 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13115 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing gtkhtml3.14 as dep of evolution
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13147 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
gpgv: Signature made Mon 15 Oct 2007 07:24:30 PM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13113 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
gpgv: Signature made Mon 15 Oct 2007 07:24:30 PM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13113 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
gpgv: Signature made Mon 15 Oct 2007 07:24:30 PM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Installing xserver-xorg-core as dep of xserver-xorg
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
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
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
Installing libgamin0 as dep of gamin
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
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
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
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ghostscript-x as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-indic-fonts-core
Installing ttf-indic-fonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing cupsys-client as dep of cupsys-bsd
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
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
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing ttf-dejavu as dep of wesnoth-data
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing totem-gstreamer as dep of totem
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 1 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 6 as a solution to ghostscript 19
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 3 as a solution to ghostscript 19
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-common
Investigating openoffice.org-style-andromeda
Package openoffice.org-style-andromeda has broken dep on openoffice.org-common
  Considering openoffice.org-common 34 as a solution to openoffice.org-style-andromeda 12
  Removing openoffice.org-style-andromeda rather than change openoffice.org-common
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 56 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x -1 as a solution to ghostscript-x 2
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 205 as a solution to python2.5-dev 1
  Removing python2.5-dev rather than change python2.5
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 1
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 0 as a solution to python-soya 1
  Added libglew1 to the remove list
  Fixing python-soya via keep of libglew1
Investigating totem-gstreamer
Package totem-gstreamer has broken dep on totem-xine
  Considering totem-xine 1 as a solution to totem-gstreamer 1
  Holding Back totem-gstreamer rather than change totem-xine
Investigating ttf-dejavu-core
Package ttf-dejavu-core has broken dep on ttf-dejavu
  Considering ttf-dejavu 8 as a solution to ttf-dejavu-core 0
  Holding Back ttf-dejavu-core rather than change ttf-dejavu
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ttf-dejavu-core
  Considering ttf-dejavu-core 0 as a solution to ubuntu-desktop 0
  Holding Back ubuntu-desktop rather than change ttf-dejavu-core
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
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Considering totem-gstreamer 1 as a solution to totem-mozilla 0
  Holding Back totem-mozilla rather than change totem-gstreamer
  Or group keep for totem-mozilla
Investigating openoffice.org-style-default
Package openoffice.org-style-default has broken dep on openoffice.org-style-andromeda
  Considering openoffice.org-style-andromeda 12 as a solution to openoffice.org-style-default -1
  Removing openoffice.org-style-default rather than change openoffice.org-style-andromeda
Investigating openoffice.org-style-industrial
Package openoffice.org-style-industrial has broken dep on openoffice.org-common
  Considering openoffice.org-common 34 as a solution to openoffice.org-style-industrial -1
  Removing openoffice.org-style-industrial rather than change openoffice.org-common
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 709 as a solution to python-dev -1
  Removing python-dev rather than change python
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin -1
  Holding Back pidgin rather than change gaim
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 0 as a solution to python-soya 1
  Added libglew1 to the remove list
  Fixing python-soya via keep of libglew1
 Try to Re-Instate ubuntu-desktop
 Try to Re-Instate totem
 Try to Re-Instate totem-mozilla
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 0 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating python-soya
Package python-soya has broken dep on libglew1
  Considering libglew1 1 as a solution to python-soya 1
  Removing python-soya rather than change libglew1
Investigating balazar
Package balazar has broken dep on python-soya
  Considering python-soya 1 as a solution to balazar -1
  Removing balazar rather than change python-soya
Done
Starting
Starting 2
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ttf-dejavu-core
  Considering ttf-dejavu-core 1 as a solution to ubuntu-desktop 0
  Re-Instated ttf-dejavu-core
  Re-Instated ubuntu-desktop
Investigating ttf-dejavu-core
Package ttf-dejavu-core has broken dep on ttf-dejavu
  Considering ttf-dejavu 8 as a solution to ttf-dejavu-core 1
  Holding Back ttf-dejavu-core rather than change ttf-dejavu
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ttf-dejavu-core
  Considering ttf-dejavu-core 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change ttf-dejavu-core
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 12788 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing zlib1g as dep of lbreakout2
Installing lbreakout2-data as dep of lbreakout2
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
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
Installing libltdl3 as dep of libgphoto2-port0
Installing libgtkhtml2.0-cil as dep of f-spot
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
Installing libstdc++6 as dep of libopenexr2c2a
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing kdelibs-data as dep of kdelibs4c2a
Installing python-setuptools as dep of python-opengl
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
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
Installing libgamin0 as dep of gamin
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
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing libflac8 as dep of gtkpod-aac
Installing libgpod2 as dep of gtkpod-aac
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing amule-common as dep of amule
Installing libcrypto++6 as dep of amule
Installing libwxbase2.8-0 as dep of amule
Installing libwxgtk2.8-0 as dep of amule
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
new important dependency: ntfs-3g
Installing ntfs-3g as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing kicker as dep of kcontrol
Installing libkonq4 as dep of kicker
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing gtkhtml3.14 as dep of evolution
Installing enigma-data as dep of enigma
Installing libalut0 as dep of vegastrike
Installing libboost-python1.34.1 as dep of vegastrike
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-libs-data as dep of libgnome32
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libkdegames1 as dep of ksame
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libjack0 as dep of libjack0.100.0-0
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing python-imaging as dep of python-imaging-tk
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bogofilter
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: hal-cups-utils
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing kq-data as dep of kq
Installing cupsys-client as dep of cupsys-bsd
Installing libglade0 as dep of libglade-gnome0
Installing python as dep of python-dev
Installing python-minimal as dep of python
Installing fontconfig-config as dep of libfontconfig1
Installing aqsis-libsc2a as dep of aqsis
Installing billard-gl-data as dep of billard-gl
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing libmono1.0-cil as dep of banshee
Installing libtaglib2.0-cil as dep of banshee
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libswscale1d as dep of ffmpeg
Installing wesnoth-music as dep of wesnoth-all
Installing wesnoth-editor as dep of wesnoth-all
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libcal3d12 as dep of python-soya
Installing libglew1.4 as dep of python-soya
Installing libode0debian1 as dep of python-soya
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing videotrans as dep of qdvdauthor
Installing libsamplerate0 as dep of sox
Installing gimp-data as dep of gimp
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing holotz-castle-data as dep of holotz-castle
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 129
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 9
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 54 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 3
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 2
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
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
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 8 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 13147 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done
```

apt-autoinst-fixup.log
```
2007-06-04 00:13:50,900 DEBUG Starting to check for auto-install states that need fixup
2007-06-04 00:13:50,915 DEBUG Found installed meta-pkg: 'ubuntu-standard' 
2007-06-04 00:13:50,916 INFO Removed auto-flag from package 'command-not-found'
2007-06-04 00:13:50,917 INFO Removed auto-flag from package 'update-manager-core'
2007-06-04 00:13:50,958 DEBUG Found installed meta-pkg: 'ubuntu-minimal' 
2007-06-04 00:13:50,959 INFO Removed auto-flag from package 'apt'
2007-06-04 00:13:51,008 DEBUG Found installed meta-pkg: 'ubuntu-desktop' 
2007-06-04 00:13:51,008 INFO Removed auto-flag from package 'avahi-autoipd'
2007-06-04 00:13:51,009 INFO Removed auto-flag from package 'dcraw'
2007-06-04 00:13:51,009 INFO Removed auto-flag from package 'desktop-effects'
2007-06-04 00:13:51,010 INFO Removed auto-flag from package 'foomatic-db-hpijs'
2007-06-04 00:13:51,010 INFO Removed auto-flag from package 'genisoimage'
2007-06-04 00:13:51,011 INFO Removed auto-flag from package 'gs-esp-x'
2007-06-04 00:13:51,011 INFO Removed auto-flag from package 'gtk2-engines-pixbuf'
2007-06-04 00:13:51,012 INFO Removed auto-flag from package 'libnss-mdns'
2007-06-04 00:13:51,012 INFO Removed auto-flag from package 'openprinting-ppds'
2007-06-04 00:13:51,013 INFO Removed auto-flag from package 'wodim'
2007-06-04 00:13:51,013 INFO Removed auto-flag from package 'espeak'
2007-06-04 00:13:51,014 INFO Removed auto-flag from package 'gnome-user-guide'
2007-06-04 00:13:51,014 INFO Removed auto-flag from package 'network-manager-gnome'
2007-06-04 00:13:51,015 INFO Removed auto-flag from package 'restricted-manager'
2007-06-04 00:13:51,015 INFO Removed auto-flag from package 'scim-tables-additional'
```

main.log
```
2007-10-24 03:55:24,887 INFO release-upgrader version '0.81' started
2007-10-24 03:55:31,529 DEBUG lsb-release: 'feisty'
2007-10-24 03:55:31,529 DEBUG _pythonSymlinkCheck run
2007-10-24 03:55:34,074 DEBUG checkViewDepends()
2007-10-24 03:55:41,786 DEBUG Foreign: libdivxencore0-binary libdivxdecore0-binary ffmpeg libdvdcss2 libavcodec0d libavformat0d picasa automatix2 libdivx0-binary libpostproc0d pmount wine
2007-10-24 03:55:41,787 DEBUG Obsolete: build-essential lostlabyrinth acetoneiso2 linux-libc-dev dvdauthor xorg-driver-fglrx envy ubuntuzilla libjasper1 animorph1 libxml2 xorg-driver-fglrx-dev linux-restricted-modules-2.6.17-10-generic sun-j2re1.5 fglrx-amdcccle linux-image-2.6.17-11-generic fglrx-kernel-source libc6-dev linux-restricted-modules-2.6.17-11-generic libatm1 fglrx-kernel-2.6.20-16-generic libc6 vive w32codecs mhgui1 makehuman linux-image-2.6.17-10-generic fakeroot wxsvg
2007-10-24 03:55:41,789 DEBUG updateSourcesList()
2007-10-24 03:55:41,889 DEBUG rewriteSourcesList()
2007-10-24 03:55:41,901 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ edgy universe'
2007-10-24 03:55:41,902 DEBUG entry '# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe' was disabled (unknown dist)
2007-10-24 03:55:41,902 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe'
2007-10-24 03:55:41,902 DEBUG entry '# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe' was disabled (unknown dist)
2007-10-24 03:55:41,903 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse'
2007-10-24 03:55:41,903 DEBUG entry '# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse' was disabled (unknown dist)
2007-10-24 03:55:41,903 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse'
2007-10-24 03:55:41,904 DEBUG entry '# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse' was disabled (unknown dist)
2007-10-24 03:55:41,904 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu edgy-security universe'
2007-10-24 03:55:41,904 DEBUG entry '# deb http://security.ubuntu.com/ubuntu edgy-security universe' was disabled (unknown dist)
2007-10-24 03:55:41,904 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu edgy-security universe'
2007-10-24 03:55:41,905 DEBUG entry '# deb-src http://security.ubuntu.com/ubuntu edgy-security universe' was disabled (unknown dist)
2007-10-24 03:55:41,905 DEBUG examining: 'deb http://www.getautomatix.com/apt feisty main'
2007-10-24 03:55:41,909 DEBUG entry '# deb http://www.getautomatix.com/apt feisty main' was disabled (unknown mirror)
2007-10-24 03:55:41,910 DEBUG transitioned commerical to 'deb http://archive.canonical.com/ubuntu gutsy partner' 
2007-10-24 03:55:41,910 DEBUG examining: 'deb http://packages.medibuntu.org/ feisty free non-free'
2007-10-24 03:55:41,914 DEBUG entry '# deb http://packages.medibuntu.org/ feisty free non-free' was disabled (unknown mirror)
2007-10-24 03:55:41,915 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse'
2007-10-24 03:55:41,915 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse' updated to new dist
2007-10-24 03:55:41,916 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse #Added by software-properties'
2007-10-24 03:55:41,916 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties' updated to new dist
2007-10-24 03:55:41,916 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu/ feisty-security universe main multiverse restricted'
2007-10-24 03:55:41,916 DEBUG entry 'deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted' updated to new dist
2007-10-24 03:55:41,917 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu/ feisty-security universe main multiverse restricted'
2007-10-24 03:55:41,917 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted' updated to new dist
2007-10-24 03:55:41,917 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu/ feisty-updates universe main multiverse restricted'
2007-10-24 03:55:41,917 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted' updated to new dist
2007-10-24 03:55:41,918 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates universe main multiverse restricted'
2007-10-24 03:55:41,918 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted' updated to new dist
2007-10-24 03:55:41,918 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu/ feisty-proposed universe main multiverse restricted'
2007-10-24 03:55:41,918 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted' updated to new dist
2007-10-24 03:55:41,919 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed universe main multiverse restricted'
2007-10-24 03:55:41,919 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted' updated to new dist
2007-10-24 03:55:41,919 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu/ feisty-backports universe main multiverse restricted'
2007-10-24 03:55:41,920 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted' updated to new dist
2007-10-24 03:55:41,920 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports universe main multiverse restricted'
2007-10-24 03:55:41,920 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted' updated to new dist
2007-10-24 03:55:41,920 DEBUG examining: 'deb http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"'
2007-10-24 03:55:41,925 DEBUG entry '# deb http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"' was disabled (unknown mirror)
2007-10-24 03:55:41,925 DEBUG examining: 'deb-src http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"'
2007-10-24 03:55:41,929 DEBUG entry '# deb-src http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"' was disabled (unknown mirror)
2007-10-24 03:56:57,840 DEBUG demoted: 'binfmt-support feisty-session-splashes festlex-cmu festlex-poslex festvox-kallpc16k gcj-4.1-base gij-4.1 gnome-cups-manager libdb3 libgcj7-jar libgda2-3 libgda2-common libglib1.2 libgnomecupsui1.0-1c2a libgtk1.2 libgtk1.2-common liblzo1 libportaudio0 libslab0 libstlport5.1 libxml1 libxmlsec1 libxmlsec1-nss libxmlsec1-openssl openoffice.org-filter-mobiledev pmount ttf-baekmuk vnc-common xarchiver xvncviewer'
2007-10-24 03:57:44,081 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2007-10-24 03:57:44,330 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2007-10-24 03:57:44,565 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2007-10-24 03:57:44,566 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2007-10-24 03:57:44,566 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2007-10-24 03:57:44,817 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2007-10-24 03:57:45,050 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2007-10-24 03:57:45,050 DEBUG running gutsyQuirks handler
2007-10-24 03:57:45,051 DEBUG found nfs mount in line 'nfsd /proc/fs/nfsd nfsd rw 0 0', marking nfs-common for install 
2007-10-24 03:57:45,276 DEBUG Kernel uname: '2.6.20-16-generic' 
2007-10-24 03:57:45,330 WARNING envy detected, trying to workaround
2007-10-24 03:57:48,864 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
```

main_pre_req.log
```
2007-10-24 03:55:05,921 INFO release-upgrader version '0.81' started
2007-10-24 03:55:06,702 DEBUG lsb-release: 'feisty'
2007-10-24 03:55:06,702 DEBUG _pythonSymlinkCheck run
2007-10-24 03:55:09,414 DEBUG checkViewDepends()
2007-10-24 03:55:09,415 DEBUG getRequiredBackports()
2007-10-24 03:55:19,423 DEBUG marking 'release-upgrader-apt' for install
2007-10-24 03:55:19,639 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-24 03:55:24,327 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1924684 DestFile:'/tmp/tmpPXxO3a/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2' 
2007-10-24 03:55:24,328 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1307096 DestFile:'/tmp/tmpPXxO3a/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb' DescURI: 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-apt/release-upgrader-apt_0.6.46.4ubuntu10.' 
2007-10-24 03:55:24,329 DEBUG extracting udeb '/tmp/tmpPXxO3a/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' 
2007-10-24 03:55:24,527 DEBUG extracting udeb '/tmp/tmpPXxO3a/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb' 
```

main_update_self.log
```
2007-10-24 03:39:08,888 INFO release-upgrader version '0.81' started
2007-10-24 03:39:12,802 DEBUG lsb-release: 'feisty'
2007-10-24 03:39:12,803 DEBUG _pythonSymlinkCheck run
2007-10-24 03:39:15,955 DEBUG checkViewDepends()
2007-10-24 03:39:24,441 DEBUG useNetwork: 'True' (selected by user)
2007-10-24 03:39:27,477 INFO runDistUpgrader() called, re-exec self
```

I'm at my wits end here. I've tried everything I can think of on my own, and I've tried any suggestion I've been able to find on these boards about this bug. Can *anyone* help me with a simple fix that *doesn't* involve making a backup of my /home and doing a complete system install? 

Thanks for your time.

---

### Post by nanotube on 2007-10-24
try the following:
back up your current /etc/apt/sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.preinstallbackup
```
then edit your sources.list to only include official feisty ubuntu repositories. Just remove everything, and paste the following content into it:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
dfolkins@groovy4:~$ more /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

then try the upgrade again...

---

### Post by Airos on 2007-10-24
Well, it's *mostly* working now... I changed the sources.list, but I still got the same error through update-manager. I did manage to upgrade using the alternate CD and synaptic package manager, though, and then use update-manager to snag, (*almost*), all the latest packages. So, I suppose this issue, for me at least, has been solved. 

Thank you for your help!

---

### Post by nanotube on 2007-10-24
cool. :) not sure how much help i was, but i'm glad it worked out for you :)

---

