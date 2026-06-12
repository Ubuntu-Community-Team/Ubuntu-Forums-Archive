---
title: "installed hardy from dapper, got boxes not english"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by renovate on 2008-05-20
I installed hardy from dapper, but my system is showing everything as boxes instead of a readable language. I tried loading my live breezy cd to look at the menu but when I am in hardy and I try to change the language support, i get a prompt with a lock, and a description in boxes which I can't read. I assume it's asking for the root password, so I enter it, but then nothing happens, and I can't open the language changing application.

If you could describe another way for me to fix this problem and get english back, preferably with screen-shots or at least icon descriptions (as the box-font is totally unreadable and defies my best guesses) I would reeeeally appreciate it.

I'm having trouble keeping an internet connection with that system (wireless on a laptop) so it might have been a problem with the upgrade.


Thanks a bunch.

---

### Post by zvacet on 2008-05-20
```
ssudo apt-get update && sudo apt-get upgrade
```

---

### Post by renovate on 2008-05-21
Here's what happens

```
user@user:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 http://security.ubuntu.com hardy-security Release.gpg [191B]
Get:2 http://us.archive.ubuntu.com hardy Release.gpg [191B]
Get:3 http://us.archive.ubuntu.com hardy-updates Release.gpg [191B]
Get:4 http://security.ubuntu.com hardy-security Release [44.0kB]
Get:5 http://us.archive.ubuntu.com hardy Release [65.9kB]
Get:6 http://security.ubuntu.com hardy-security/main Packages [12.5kB]
Get:7 http://us.archive.ubuntu.com hardy-updates Release [51.2kB]
Get:8 http://security.ubuntu.com hardy-security/restricted Packages [14B]
Get:9 http://security.ubuntu.com hardy-security/universe Packages [8460B]
Get:10 http://security.ubuntu.com hardy-security/multiverse Packages [14B]
Get:11 http://security.ubuntu.com hardy-security/main Sources [4313B]
Get:12 http://security.ubuntu.com hardy-security/restricted Sources [14B]
Get:13 http://security.ubuntu.com hardy-security/universe Sources [1984B]
Get:14 http://security.ubuntu.com hardy-security/multiverse Sources [14B]
Get:15 http://us.archive.ubuntu.com hardy/main Packages [1178kB]
Get:16 http://us.archive.ubuntu.com hardy/restricted Packages [6986B]
Get:17 http://us.archive.ubuntu.com hardy/universe Packages [4297kB]
Get:18 http://ca.archive.ubuntu.com hardy-backports Release.gpg [191B]
Get:19 http://ca.archive.ubuntu.com hardy-backports Release [44.0kB]
Get:20 http://us.archive.ubuntu.com hardy/multiverse Packages [179kB]
Get:21 http://us.archive.ubuntu.com hardy/main Sources [338kB]
Get:22 http://us.archive.ubuntu.com hardy/restricted Sources [1488B]
Get:23 http://us.archive.ubuntu.com hardy/universe Sources [1323kB]
Get:24 http://ca.archive.ubuntu.com hardy-backports/main Packages [48.6kB]
Get:25 http://us.archive.ubuntu.com hardy/multiverse Sources [60.9kB]
Get:26 http://us.archive.ubuntu.com hardy-updates/main Packages [50.1kB]
Get:27 http://us.archive.ubuntu.com hardy-updates/restricted Packages [14B]
Get:28 http://us.archive.ubuntu.com hardy-updates/universe Packages [22.9kB]
Get:29 http://us.archive.ubuntu.com hardy-updates/multiverse Packages [4318B]
Get:30 http://us.archive.ubuntu.com hardy-updates/main Sources [13.5kB]
Get:31 http://us.archive.ubuntu.com hardy-updates/restricted Sources [14B]
Get:32 http://us.archive.ubuntu.com hardy-updates/universe Sources [4524B]
Get:33 http://us.archive.ubuntu.com hardy-updates/multiverse Sources [700B]
Get:34 http://ca.archive.ubuntu.com hardy-backports/restricted Packages [14B]
Get:35 http://ca.archive.ubuntu.com hardy-backports/universe Packages [10.6kB]
Get:36 http://ca.archive.ubuntu.com hardy-backports/multiverse Packages [14B]
Get:37 http://ca.archive.ubuntu.com hardy-backports/main Sources [6643B]
Get:38 http://ca.archive.ubuntu.com hardy-backports/restricted Sources [14B]
Get:39 http://ca.archive.ubuntu.com hardy-backports/universe Sources [1593B]
Get:40 http://ca.archive.ubuntu.com hardy-backports/multiverse Sources [14B]
Fetched 7781kB in 33s (234kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  acpi acpi-support acpid alsa-utils anacron apmd apt apt-utils aptitude
  aspell at ayttm base-files base-passwd bash bc belocs-locales-bin
  bicyclerepair bind9-host binutils binutils-static bittorrent blender blt
  bluez-cups bluez-pcmcia-support bluez-utils bogofilter-bdb bsdmainutils
  bsdutils bsh bug-buddy bzip2 capplets-data cdparanoia console-tools
  contact-lookup-applet coreutils cpio cpp cron cupsys cupsys-bsd
  cupsys-client dash dbus dc debhelper debianutils desktop-file-utils
  dhcp3-client dhcp3-common diff discover1 dmidecode dmsetup dnsutils
  dosfstools dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs ed eject
  eog erlang erlang-base esound ethtool evince evms evms-ncurses evolution
  evolution-data-server evolution-exchange evolution-plugins evolution-webcal
  fastjar fdutils fetchmail file file-roller findutils finger firefox
  firefox-gnome-support fontconfig foomatic-db-engine fortune-mod fping
  freeglut3 ftp gaim gamin gcalctool gcc gcj-4.1 gcj-4.1-base gcjwebplugin
  gconf-editor gconf2 gdb gdk-imlib11 gdm gedit gedit-common gettext
  gettext-base gij gij-4.1 gimp gimp-data gimp-python gjdoc gksu
  gnome-app-install gnome-applets gnome-applets-data gnome-bin
  gnome-btdownload gnome-control-center gnome-cups-manager gnome-doc-utils
  gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-libs-data
  gnome-lokkit gnome-media gnome-menus gnome-netstatus-applet gnome-nettool
  gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager
  gnomemeeting gnupg grep groff-base grub gs-common gs-esp gthumb
  gtk2-engines-pixbuf gtkhtml3.8 gucharmap guile-1.6-libs gzip hal hdparm
  hermes1 hostname hpijs hplip-data html2text ifupdown info initramfs-tools
  initscripts iproute iptables iputils-arping iputils-ping iputils-tracepath
  java-gcj-compat java-gcj-compat-dev jfsutils klogd language-selector
  language-support-en laptop-detect launchpad-integration less lftp
  liba52-0.7.4 libaa1 libacl1 libadns1 libao2 libapm1 libart-2.0-2 libart2
  libartsc0 libasound2 libaspell15 libatk1.0-0 libatm1 libattr1 libaudio2
  libaudiofile0 libavc1394-0 libavifile-0.7c2 libblkid1 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libbz2-1.0 libc6
  libc6-dev libc6-i686 libcairo2 libcap1 libcdparanoia0 libcomerr2
  libcompfaceg1 libconsole libcroco3 libcupsimage2 libcurl3 libcurl3-gnutls
  libdb1-compat libdb4.2 libdb4.3 libdiscover1 libdjvulibre15 libdv4
  libdvdnav4 libdvdread3 libedata-book1.2-2 libedit2 libeel2-2 libelfg0
  libesd-alsa0 libevms-2.5 libexif12 libexpat1 libfaac0 libfontconfig1
  libfontenc1 libfreetype6 libfribidi0 libfs6 libgail-common libgamin0
  libgc1c2 libgcc1 libgcj7-dev libgcj7-jar libgconf2-4 libgcrypt11
  libgd2-noxpm libgda2-3 libgdbm3 libgdk-pixbuf2 libgeoip1 libggi2 libgimp2.0
  libgl1-mesa-dri libglade2-0 libgle3 libglib-perl libglib2.0-0
  libglib2.0-data libglide2 libglu1-mesa libgnome-desktop-2 libgnome-keyring0
  libgnome-menu2 libgnome-pilot2 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome32
  libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomesupport0 libgnomeui-0 libgnomeui-common
  libgnomeui32 libgnomevfs2-0 libgnomevfs2-common libgnorba27 libgnorbagtk0
  libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpmg1 libgsm1 libgtk1.2
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtkhtml2-0 libgtkhtml3.8-15
  libgtksourceview1.0-0 libgtkspell0 libguile-ltdl-1 libhal-storage1 libhal1
  libhsqldb-java libice6 libid3tag0 libidl0 libidn11 libieee1284-3 libijs-0.35
  libjpeg62 libkrb53 liblame0 liblcms1 liblircclient0 liblocale-gettext-perl
  liblpint-bonobo0 libltdl3 libmad0 libmagic1 libmdbtools libmetacity0 libmng1
  libmp4v2-0 libmpcdec3 libmpeg2-4 libnautilus-extension1 libncurses5
  libncursesw5 libogg0 liboil0.3 liborbit0 liborbit2 libpam-modules libpam0g
  libpanel-applet2-0 libpango1.0-0 libpaper1 libparse-recdescent-perl
  libpcap0.8 libperl5.8 libpng12-0 libpopt0 libportaudio0 libqt3-mt
  libqthreads-12 libraptor1 librasqal0 librdf0 libreadline5 librecode0
  librsvg2-2 librsvg2-common libsane libsasl2 libsasl2-modules
  libscrollkeeper0 libsdl-erlang libsdl1.2debian libsdl1.2debian-oss
  libselinux1 libshout3 libsigc++-1.2-5c2 libslang2 libslp1 libsm6
  libsmbclient libsndfile1 libsoup2.2-8 libspeex1 libsqlite0 libsqlite3-0
  libss2 libssl0.9.8 libstartup-notification0 libstdc++6 libstlport4.6c2
  libsysfs2 libtext-charwidth-perl libtext-iconv-perl libtheora0 libtiff4
  libungif4g libunicode-string-perl libusb-0.1-4 libuuid1 libvorbis0a
  libvorbisenc2 libvorbisfile3 libvte-common libwmf0.2-7 libwrap0 libx11-6
  libxalan2-java libxau6 libxaw7 libxcursor1 libxdamage1 libxdmcp6
  libxerces2-java libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbfile1 libxml1 libxml2 libxml2-utils libxmu6 libxmuu1 libxosd2 libxp6
  libxpm4 libxrandr2 libxrender1 libxres1 libxslt1.1 libxss1 libxt6 libxtrap6
  libxtst6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1
  linux-386 linux-image-386 linux-restricted-modules-386 locales login
  logrotate lokkit lshw lsof ltrace lvm2 make man-db mawk mcpp mdadm mdetect
  mesa-utils metacity mii-diag module-init-tools mount
  mozilla-firefox-locale-en-gb mp3burn mpg321 mplayer mtr-tiny nano nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto ncurses-bin net-tools
  netbase netcat notification-daemon ntpdate odbcinst1debian1 ogle
  openssh-client openssl parted passwd patch pciutils pcmciautils perl
  perl-base perl-modules pkg-config pmount pnm2ppa po-debconf powermgmt-base
  powernowd ppp procmail procps psmisc python python-adns python-apt
  python-cddb python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-epydoc python-examples python-gadfly python-gd python-gdbm
  python-genetic python-geoip python-glade2 python-gmenu python-gnome2
  python-gnome2-extras python-gnupginterface python-gtk2 python-htmlgen
  python-htmltmpl python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-launchpad-integration python-ldap python-minimal
  python-musicbrainz python-mysqldb python-netcdf python-newt python-numeric
  python-osd python-pam python-pexpect python-pgsql python-pisock
  python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl
  python-pyorbit python-pyvorbis python-pyxattr python-reportlab
  python-simpletal python-soappy python-sqlite python-stats python-syck
  python-tk python-unit python-uno python-xdg python-xml python-xmpp python2.4
  python2.4-examples python2.4-minimal rdesktop readahead reiser4progs
  reiserfsprogs reportbug rhythmbox rss-glx rsync samba-common sane-utils
  screen scrollkeeper sed serpentine shared-mime-info slocate smbclient
  sound-juicer ssh-askpass-gnome strace sudo synaptic sysklogd
  system-tools-backends sysvinit tar tcl8.4 tcpd tcpdump telnet time tk8.4
  toshset totem totem-gstreamer tsclient ttf-indic-fonts ttf-opensymbol
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-standard ucf
  udev unixodbc unzip update-manager update-notifier usbutils usplash
  util-linux vbetool view3ds vim vim-common vino vorbis-tools w3m wget
  whiptail whois wings3d wireless-tools wpasupplicant wvdial x11-common xauth
  xbase-clients xchat xchat-common xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-utils xfsprogs xinit xkeyboard-config xpmutils xresprobe xsane
  xsane-common xscreensaver xscreensaver-data xscreensaver-gl xserver-xorg
  xserver-xorg-core xserver-xorg-driver-all xserver-xorg-input-acecad
  xserver-xorg-input-aiptek xserver-xorg-input-all xserver-xorg-input-calcomp
  xserver-xorg-input-citron xserver-xorg-input-digitaledge
  xserver-xorg-input-dmc xserver-xorg-input-dynapro
  xserver-xorg-input-elographics xserver-xorg-input-evdev
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-kbd
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mouse xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void xserver-xorg-input-wacom
  xsltproc xterm xutils yafray yelp zenity zip zlib1g zlib1g-dev
0 upgraded, 0 newly installed, 0 to remove and 682 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up xfonts-scalable (1.0.0-6) ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exitdpkg: error processing xfonts-scalable (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 xfonts-scalable
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user:~$

```

---

### Post by renovate on 2008-05-21
just for humour value, here's a screen shot.:popcorn:

---

### Post by zvacet on 2008-05-22
```
sudo aptitude upgrade
```

If that doesn´t work 

```
sudo aptitude install  acpi acpi-support acpid alsa-utils anacron apmd apt apt-utils aptitude
  aspell at ayttm base-files base-passwd bash bc belocs-locales-bin
  bicyclerepair bind9-host binutils binutils-static bittorrent blender blt
  bluez-cups bluez-pcmcia-support bluez-utils bogofilter-bdb bsdmainutils
  bsdutils bsh bug-buddy bzip2 capplets-data cdparanoia console-tools
  contact-lookup-applet coreutils cpio cpp cron cupsys cupsys-bsd
  cupsys-client dash dbus dc debhelper debianutils desktop-file-utils
  dhcp3-client dhcp3-common diff discover1 dmidecode dmsetup dnsutils
  dosfstools dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs ed eject
  eog erlang erlang-base esound ethtool evince evms evms-ncurses evolution
  evolution-data-server evolution-exchange evolution-plugins evolution-webcal
  fastjar fdutils fetchmail file file-roller findutils finger firefox
  firefox-gnome-support fontconfig foomatic-db-engine fortune-mod fping
  freeglut3 ftp gaim gamin gcalctool gcc gcj-4.1 gcj-4.1-base gcjwebplugin
  gconf-editor gconf2 gdb gdk-imlib11 gdm gedit gedit-common gettext
  gettext-base gij gij-4.1 gimp gimp-data gimp-python gjdoc gksu
  gnome-app-install gnome-applets gnome-applets-data gnome-bin
  gnome-btdownload gnome-control-center gnome-cups-manager gnome-doc-utils
  gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-libs-data
  gnome-lokkit gnome-media gnome-menus gnome-netstatus-applet gnome-nettool
  gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager
  gnomemeeting gnupg grep groff-base grub gs-common gs-esp gthumb
  gtk2-engines-pixbuf gtkhtml3.8 gucharmap guile-1.6-libs gzip hal hdparm
  hermes1 hostname hpijs hplip-data html2text ifupdown info initramfs-tools
  initscripts iproute iptables iputils-arping iputils-ping iputils-tracepath
  java-gcj-compat java-gcj-compat-dev jfsutils klogd language-selector
  language-support-en laptop-detect launchpad-integration less lftp
  liba52-0.7.4 libaa1 libacl1 libadns1 libao2 libapm1 libart-2.0-2 libart2
  libartsc0 libasound2 libaspell15 libatk1.0-0 libatm1 libattr1 libaudio2
  libaudiofile0 libavc1394-0 libavifile-0.7c2 libblkid1 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libbz2-1.0 libc6
  libc6-dev libc6-i686 libcairo2 libcap1 libcdparanoia0 libcomerr2
  libcompfaceg1 libconsole libcroco3 libcupsimage2 libcurl3 libcurl3-gnutls
  libdb1-compat libdb4.2 libdb4.3 libdiscover1 libdjvulibre15 libdv4
  libdvdnav4 libdvdread3 libedata-book1.2-2 libedit2 libeel2-2 libelfg0
  libesd-alsa0 libevms-2.5 libexif12 libexpat1 libfaac0 libfontconfig1
  libfontenc1 libfreetype6 libfribidi0 libfs6 libgail-common libgamin0
  libgc1c2 libgcc1 libgcj7-dev libgcj7-jar libgconf2-4 libgcrypt11
  libgd2-noxpm libgda2-3 libgdbm3 libgdk-pixbuf2 libgeoip1 libggi2 libgimp2.0
  libgl1-mesa-dri libglade2-0 libgle3 libglib-perl libglib2.0-0
  libglib2.0-data libglide2 libglu1-mesa libgnome-desktop-2 libgnome-keyring0
  libgnome-menu2 libgnome-pilot2 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome32
  libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomesupport0 libgnomeui-0 libgnomeui-common
  libgnomeui32 libgnomevfs2-0 libgnomevfs2-common libgnorba27 libgnorbagtk0
  libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpmg1 libgsm1 libgtk1.2
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtkhtml2-0 libgtkhtml3.8-15
  libgtksourceview1.0-0 libgtkspell0 libguile-ltdl-1 libhal-storage1 libhal1
  libhsqldb-java libice6 libid3tag0 libidl0 libidn11 libieee1284-3 libijs-0.35
  libjpeg62 libkrb53 liblame0 liblcms1 liblircclient0 liblocale-gettext-perl
  liblpint-bonobo0 libltdl3 libmad0 libmagic1 libmdbtools libmetacity0 libmng1
  libmp4v2-0 libmpcdec3 libmpeg2-4 libnautilus-extension1 libncurses5
  libncursesw5 libogg0 liboil0.3 liborbit0 liborbit2 libpam-modules libpam0g
  libpanel-applet2-0 libpango1.0-0 libpaper1 libparse-recdescent-perl
  libpcap0.8 libperl5.8 libpng12-0 libpopt0 libportaudio0 libqt3-mt
  libqthreads-12 libraptor1 librasqal0 librdf0 libreadline5 librecode0
  librsvg2-2 librsvg2-common libsane libsasl2 libsasl2-modules
  libscrollkeeper0 libsdl-erlang libsdl1.2debian libsdl1.2debian-oss
  libselinux1 libshout3 libsigc++-1.2-5c2 libslang2 libslp1 libsm6
  libsmbclient libsndfile1 libsoup2.2-8 libspeex1 libsqlite0 libsqlite3-0
  libss2 libssl0.9.8 libstartup-notification0 libstdc++6 libstlport4.6c2
  libsysfs2 libtext-charwidth-perl libtext-iconv-perl libtheora0 libtiff4
  libungif4g libunicode-string-perl libusb-0.1-4 libuuid1 libvorbis0a
  libvorbisenc2 libvorbisfile3 libvte-common libwmf0.2-7 libwrap0 libx11-6
  libxalan2-java libxau6 libxaw7 libxcursor1 libxdamage1 libxdmcp6
  libxerces2-java libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbfile1 libxml1 libxml2 libxml2-utils libxmu6 libxmuu1 libxosd2 libxp6
  libxpm4 libxrandr2 libxrender1 libxres1 libxslt1.1 libxss1 libxt6 libxtrap6
  libxtst6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1
  linux-386 linux-image-386 linux-restricted-modules-386 locales login
  logrotate lokkit lshw lsof ltrace lvm2 make man-db mawk mcpp mdadm mdetect
  mesa-utils metacity mii-diag module-init-tools mount
  mozilla-firefox-locale-en-gb mp3burn mpg321 mplayer mtr-tiny nano nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto ncurses-bin net-tools
  netbase netcat notification-daemon ntpdate odbcinst1debian1 ogle
  openssh-client openssl parted passwd patch pciutils pcmciautils perl
  perl-base perl-modules pkg-config pmount pnm2ppa po-debconf powermgmt-base
  powernowd ppp procmail procps psmisc python python-adns python-apt
  python-cddb python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-epydoc python-examples python-gadfly python-gd python-gdbm
  python-genetic python-geoip python-glade2 python-gmenu python-gnome2
  python-gnome2-extras python-gnupginterface python-gtk2 python-htmlgen
  python-htmltmpl python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-launchpad-integration python-ldap python-minimal
  python-musicbrainz python-mysqldb python-netcdf python-newt python-numeric
  python-osd python-pam python-pexpect python-pgsql python-pisock
  python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl
  python-pyorbit python-pyvorbis python-pyxattr python-reportlab
  python-simpletal python-soappy python-sqlite python-stats python-syck
  python-tk python-unit python-uno python-xdg python-xml python-xmpp python2.4
  python2.4-examples python2.4-minimal rdesktop readahead reiser4progs
  reiserfsprogs reportbug rhythmbox rss-glx rsync samba-common sane-utils
  screen scrollkeeper sed serpentine shared-mime-info slocate smbclient
  sound-juicer ssh-askpass-gnome strace sudo synaptic sysklogd
  system-tools-backends sysvinit tar tcl8.4 tcpd tcpdump telnet time tk8.4
  toshset totem totem-gstreamer tsclient ttf-indic-fonts ttf-opensymbol
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-standard ucf
  udev unixodbc unzip update-manager update-notifier usbutils usplash
  util-linux vbetool view3ds vim vim-common vino vorbis-tools w3m wget
  whiptail whois wings3d wireless-tools wpasupplicant wvdial x11-common xauth
  xbase-clients xchat xchat-common xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-utils xfsprogs xinit xkeyboard-config xpmutils xresprobe xsane
  xsane-common xscreensaver xscreensaver-data xscreensaver-gl xserver-xorg
  xserver-xorg-core xserver-xorg-driver-all xserver-xorg-input-acecad
  xserver-xorg-input-aiptek xserver-xorg-input-all xserver-xorg-input-calcomp
  xserver-xorg-input-citron xserver-xorg-input-digitaledge
  xserver-xorg-input-dmc xserver-xorg-input-dynapro
  xserver-xorg-input-elographics xserver-xorg-input-evdev
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-kbd
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mouse xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void xserver-xorg-input-wacom
  xsltproc xterm xutils yafray yelp zenity zip zlib1g zlib1g-dev
```

---

### Post by renovate on 2008-05-22
The first code didn't work, I got some of the same error messages as before.

The second part didn't work, as I couldn't enter "y" to continue when it asked me to install the packages. So I tried just partially entering the code, up to bicyclerepair,  ```
sudo aptitude install  acpi acpi-support acpid alsa-utils anacron apmd apt apt-utils aptitude
  aspell at ayttm base-files base-passwd bash bc belocs-locales-bin
  bicyclerepair 
```

and it seems to be working, but now I have this prompt:
```
 Configuring libc6 &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                                                                        &#9474;
 &#9474; Running services and programs that are using NSS need to be restarted, otherwise they might not be able to do lookup   &#9474;
 &#9474; or authentication any more. The installation process is able to restart some services (such as ssh or telnetd), but    &#9474;
 &#9474; other programs cannot be restarted automatically. One such program that needs manual stopping and restart after the    &#9474;
 &#9474; glibc upgrade by yourself is xdm - because automatic restart might disconnect your active X11 sessions.                &#9474;
 &#9474;                                                                                                                        &#9474;
 &#9474; This script detected the following installed services which must be stopped before the upgrade: gdm                    &#9474;
 &#9474;                                                                                                                        &#9474;
 &#9474; If you want to interrupt the upgrade now and continue later, please answer No to the question below.                   &#9474;
 &#9474;                                                                                                                        &#9474;
 &#9474; Do you want to upgrade glibc now?                                                                                      &#9474;
 &#9474;                                                                                                                        &#9474;
 &#9474;                                   <Yes>                                      <No>           
```

and I'm not sure how to manually start/stop xdm.

Thanks again.

---

### Post by zvacet on 2008-05-23
```
sudo /etc/init.d/gdm stop
```

If that doesn´t work 

```
sudo /etc/init.d/xdm stop
```

---

