---
title: "Upgrading From CD problem"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by pt123 on 2006-06-02
I tried to the Ubuntu upgrade with 6.06 CD option mentioned here
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

after I typed this
sudo apt-get update && sudo apt-get dist-upgrade

It says
960 upgraded, 153 newly installed, 40 to remove and 2 not upgraded.
Need to get 391MB/487MB of archives.
After unpacking 72.0MB of additional disk space will be used.


Why would I want it to download 391 MB when I downloaded the CD.

What is the point. ](*,)

---

### Post by BungaMan on 2006-06-02
doesn't it download them from cd?

did you run 
sudo apt-cdrom add
before sudo apt-get update ...

---

### Post by pt123 on 2006-06-02
Yeah i did that here is my source list as you can see the CD rom is at the top.

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

## deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
## deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe


## my addidtion
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## Backports
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) dapper-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) dapper-extras main universe multiverse restricted

---

### Post by pt123 on 2006-06-02
Here is the packages it lists:

 acpi-support acpid adduser alien alsa-base alsa-utils appres apt apt-utils
  aptitude arts aspell at base-files base-passwd bash bc beforelight
  bicyclerepair bind9-host binutils binutils-static bitmap bittorrent
  bogofilter bogofilter-bdb bogofilter-common bsdmainutils bsdutils bsh
  bug-buddy bzip2 capplets-data cdrecord console-common console-data
  console-tools contact-lookup-applet coreutils cpio cron cupsys cupsys-bsd
  cupsys-client cupsys-driver-gimpprint dash dbus dbus-1-utils dc debconf
  debconf-i18n debconf-utils debhelper debianutils desktop-base
  desktop-file-utils dhcp3-client dhcp3-common dictionaries-common diff
  discover1 discover1-data dmidecode dmsetup dnsutils doc-debian dosfstools
  dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs editres eject eog
  esound esound-common ethtool evms evms-ncurses evolution
  evolution-data-server evolution-exchange evolution-webcal fastjar fdutils
  fetchmail file file-roller findutils finger firefox fontconfig foomatic-db
  foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters
  foomatic-filters-ppds fortune-mod fortunes-min fping freeglut3 fstobdf ftp
  gaim gaim-data gamin gcalctool gcc-3.3-base gcc-3.4-base gconf-editor gconf2
  gdb gdesklets gdesklets-data gdm gedit gedit-common gettext-base gimp
  gimp-data gimp-python gksu gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-btdownload gnome-control-center gnome-desktop-data
  gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring
  gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data
  gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnupg
  gnupg-agent grep grepmap groff-base grub gs-common gs-esp
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-alsa gstreamer0.8-artsd
  gstreamer0.8-audiofile gstreamer0.8-caca gstreamer0.8-cdio
  gstreamer0.8-cdparanoia gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-esd
  gstreamer0.8-festival gstreamer0.8-flac gstreamer0.8-gnomevfs
  gstreamer0.8-gsm gstreamer0.8-gtk gstreamer0.8-hermes gstreamer0.8-jpeg
  gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-mikmod gstreamer0.8-misc
  gstreamer0.8-mms gstreamer0.8-mpeg2dec gstreamer0.8-musepack
  gstreamer0.8-oss gstreamer0.8-plugin-apps gstreamer0.8-plugins
  gstreamer0.8-sdl gstreamer0.8-sid gstreamer0.8-speex gstreamer0.8-swfdec
  gstreamer0.8-theora gstreamer0.8-tools gstreamer0.8-vorbis gstreamer0.8-x
  gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8
  gucharmap guile-1.6-libs gxine gzip hal hal-device-manager hdparm hermes1
  hicolor-icon-theme hostname hpijs html2text hwdata hwdb-client iceauth ico
  ifupdown ijsgimpprint imake imlib-base info initramfs-tools initrd-tools
  initscripts intltool-debian iproute iptables iputils-arping iputils-ping
  iputils-tracepath irssi-text jackd klibc-utils klogd language-pack-en
  language-pack-en-base laptop-detect launchpad-integration less lesstif1
  lesstif2 lftp libaa1 libacl1 libadns1 libao2 libarts1-audiofile libaspell15
  libatk1.0-0 libattr1 libaudio2 libaudiofile0 libavc1394-0 libbind9-0
  libblkid1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libbz2-1.0 libc6 libc6-dev libc6-i686 libcomerr2 libconsole libcroco3
  libcupsimage2 libcurl3 libdb1-compat libdb3 libdb4.2 libdb4.3
  libdirectfb-0.9-22 libdiscover1 libdmx1 libdv4 libdvdread3 libebook1.2-5
  libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserverui1.2-6
  libedit2 libeel2-2 libeel2-data libelfg0 libesd-alsa0 libevms-2.5 libfaad2-0
  libflac++5c2 libflac7 libfontconfig1 libfontenc1 libfribidi0 libfs6 libg2c0
  libgadu3 libgail-common libgail17 libgal2.4-0 libgal2.4-common libgamin0
  libgc1c2 libgcj-common libgconf2-4 libgd2-noxpm libgda2-3 libgda2-common
  libgeoip1 libggi2 libgii0 libgii0-target-x libgimp2.0 libgl1-mesa
  libgl1-mesa-dri libglade2-0 libglib-perl libglib1.2 libglu1-mesa
  libgnome-desktop-2 libgnome-keyring0 libgnome-menu2 libgnome-pilot2
  libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-vfs-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnucrypto-java libgnujaxp-java libgnujaxp-jni
  libgnutls11 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1 libgsl0
  libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgstreamer0.8-0
  libgtk1.2 libgtk1.2-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common
  libgtksourceview1.0-0 libgtkspell0 libgucharmap4 libguile-ltdl-1
  libhal-storage1 libhal1 libhsqldb-java libice6 libid3tag0 libidl0
  libijs-0.35 libisccc0 libisccfg1 libiw28 libjessie-java libjpeg-progs
  libjpeg62 libklibc liblaunchpad-integration0 libldap2 liblircclient0
  liblockfile1 liblpint-bonobo0 libltdl3 liblzo1 libmagic1 libmdbtools
  libmetacity0 libmms0 libmodplug0c2 libmpcdec3 libmpeg2-4 libmyspell3c2
  libmysqlclient14 libnautilus-extension1 libncurses5 libncursesw5 libneon24
  libnetpbm10 libnspr4 libnss3 liboggflac3 liboil0.3 libopenal0 liborbit2
  libostyle1c2 libpam-modules libpam-runtime libpam0g libpanel-applet2-0
  libpcap0.8 libpcre3 libperl5.8 libpisock8 libpisync0 libpixman1 libpng12-0
  libportaudio0 libpq3 libpq4 libpt-plugins-alsa libpt-plugins-v4l2 libpth2
  libqthreads-12 libraptor1 librasqal0 libraw1394-5 librdf0 libreadline4
  libreadline5 librecode0 libreiserfs0.3-0 librpm4 librsvg2-2 librsvg2-common
  libsamplerate0 libsane libsasl2 libsasl2-modules libscrollkeeper0
  libsdl1.2debian libsdl1.2debian-oss libselinux1 libsensors3
  libservlet2.3-java libshout3 libsidplay1 libslang2 libslp1 libsm6
  libsmbclient libsmjs1 libsndfile1 libsnmp-base libsoup2.2-8 libspeex1
  libsqlite0 libsqlite3-0 libss2 libssl0.9.7 libstartup-notification0
  libstdc++5 libswfdec0.3 libt1-5 libtar libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libtheora0 libtiff-tools libtiff4
  libtunepimp-bin libungif4g libunicode-string-perl libusb-0.1-4 libuuid1
  libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libwrap0 libx11-6
  libxalan2-java libxau6 libxaw7 libxcomposite1 libxcursor1 libxdamage1
  libxdmcp6 libxerces2-java libxext6 libxfixes3 libxft2 libxi6 libxine1c2
  libxinerama1 libxkbfile1 libxkbui1 libxklavier10 libxml2-utils libxmu6
  libxmuu1 libxosd2 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxslt1.1
  libxss1 libxt-java libxt6 libxtrap6 libxtst6 libxv1 libxvidcore4
  libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-386 linux-image-386
  linux-kernel-headers linux-restricted-modules-386
  linux-restricted-modules-common linux-sound-base listres locales login
  logrotate lsb lsb-base lsb-core lsb-cxx lsb-graphics lsb-release lshw
  lshw-common lsof lvm-common lvm2 m4 mailx make makedepend makedev manpages
  mawk mdadm mdetect memtest86+ menu-xdg metacity mime-support mkisofs
  module-init-tools mount mozilla-firefox-locale-en-gb mplayer-386
  msttcorefonts mutt myspell-en-gb myspell-en-us mysql-common nano nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto ncurses-base ncurses-bin
  ncurses-term net-tools netbase netcat netkit-inetd netpbm
  notification-daemon ntp ntpdate nvidia-kernel-common nvidia-settings oclock
  odbcinst1debian1 openjade openoffice.org openoffice.org-gtk-gnome
  openoffice.org2 openoffice.org2-base openoffice.org2-calc
  openoffice.org2-draw openoffice.org2-impress openoffice.org2-math
  openoffice.org2-writer openssh-client openssh-server parted passwd pciutils
  

perl perl-base perl-modules pinentry-qt pkg-config pmount po-debconf
  popularity-contest poster postfix powermanagement-interface powermgmt-base
  powernowd ppp pppconfig procps psmisc psutils pwgen python python-adns
  python-apt python-cddb python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-epydoc python-eunuchs python-examples
  python-gadfly python-gd python-gdbm python-geoip python-glade2 python-gmenu
  python-gnome2 python-gnome2-extras python-gst python-gtk2 python-htmlgen
  python-htmltmpl python-id3lib python-imaging python-imaging-sane
  python-jabber python-kjbuckets python-launchpad-integration python-ldap
  python-minimal python-mysqldb python-numarray python-numeric python-opengl
  python-osd python-pam python-parted python-pexpect python-pgsql
  python-pisock python-pylibacl python-pyopenssl python-pyorbit python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-syck
  python-tk python-twisted python-unit python-uno python-xdg python-xml
  python-zopeinterface python2.4 python2.4-adns python2.4-apt python2.4-cairo
  python2.4-clientcookie python2.4-crypto python2.4-dbus
  python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras
  python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2
  python2.4-libxslt1 python2.4-minimal python2.4-mysqldb python2.4-numarray
  python2.4-numeric python2.4-opengl python2.4-osd python2.4-pam
  python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl
  python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-reportlab
  python2.4-samba python2.4-simpletal python2.4-sqlite python2.4-syck
  python2.4-tk python2.4-twisted python2.4-twisted-bin python2.4-unit
  python2.4-xml python2.4-zopeinterface rdesktop readahead reiser4progs
  reportbug rhythmbox rpm rss-glx rsync samba samba-common sane-utils screen
  scrollkeeper sed sessreg shared-mime-info slocate smbclient smproxy ssh
  ssh-askpass-gnome sudo synaptic sysklogd system-tools-backends sysv-rc
  sysvinit tar tcl8.4 tcpd tcpdump telnet tk8.4 toshset totem totem-xine
  tsclient ttf-arabeyes ttf-arphic-bkai00mp ttf-bengali-fonts
  ttf-devanagari-fonts ttf-freefont ttf-gujarati-fonts ttf-indic-fonts
  ttf-kannada-fonts ttf-malayalam-fonts ttf-opensymbol ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ubuntu-artwork
  ubuntu-base ubuntu-docs ubuntu-minimal ubuntu-standard ucf udev unzip
  update-manager update-notifier usbutils util-linux vbetool viewres vim
  vim-common vino vnc-common w3m wget whois wine wireless-tools wvdial x-dev
  x-ttcidfont-conf x-window-system-core x11perf x11proto-core-dev xauth
  xbase-clients xbiff xcalc xchat xchat-common xclipboard xclock xconsole
  xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-100dpi
  xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils xfontsel xfsprogs
  xgamma xgc xhost xine-ui xinit xkbutils xkeyboard-config xkill xload xlogo
  xlsatoms xlsclients xlsfonts xmag xman xmessage xmms xmodmap xmore xpdf
  xpdf-common xpdf-reader xpdf-utils xpmutils xprop xrandr xrdb xrefresh
  xresprobe xrgb xsane xsane-common xscreensaver xscreensaver-data
  xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-driver-apm
  xserver-xorg-driver-ark xserver-xorg-driver-ati xserver-xorg-driver-chips
  xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix
  xserver-xorg-driver-dummy xserver-xorg-driver-fbdev
  xserver-xorg-driver-glint xserver-xorg-driver-i128 xserver-xorg-driver-i740
  xserver-xorg-driver-i810 xserver-xorg-driver-imstt xserver-xorg-driver-mga
  xserver-xorg-driver-neomagic xserver-xorg-driver-newport
  xserver-xorg-driver-nsc xserver-xorg-driver-nv xserver-xorg-driver-rendition
  xserver-xorg-driver-s3 xserver-xorg-driver-s3virge
  xserver-xorg-driver-savage xserver-xorg-driver-siliconmotion
  xserver-xorg-driver-sis xserver-xorg-driver-tdfx xserver-xorg-driver-tga
  xserver-xorg-driver-trident xserver-xorg-driver-tseng
  xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga
  xserver-xorg-driver-via xserver-xorg-driver-vmware xserver-xorg-input-acecad
  xserver-xorg-input-aiptek xserver-xorg-input-calcomp
  xserver-xorg-input-citron xserver-xorg-input-digitaledge
  xserver-xorg-input-dmc xserver-xorg-input-dynapro
  xserver-xorg-input-elographics xserver-xorg-input-fpit
  xserver-xorg-input-hyperpen xserver-xorg-input-kbd
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mouse xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void xserver-xorg-input-wacom
  xset xsetmode xsetpointer xsetroot xsltproc xsm xstdcmap xterm xtrap xutils
  xvidtune xvinfo xvncviewer xwd xwininfo xwud yelp zenity zlib1g

---

### Post by confused57 on 2006-06-02
I think you need to "comment out" all repositories, except the CD when upgrading from the CD:

[http://www.ubuntuforums.org/showthread.php?t=179477](http://www.ubuntuforums.org/showthread.php?t=179477)

See aysiu's instructions near the bottom of the first page.

---

### Post by pt123 on 2006-06-02
When I did the commenting out and typed
 sudo apt-get update && sudo apt-get dist-upgrade

This is what it said:

Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by pt123 on 2006-06-02
Using Synaptic I uninstalled libc6-dev and ran

 sudo apt-get update && sudo apt-get dist-upgrade

and got this

Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by catlett on 2006-06-02
How old is the iso your using? If you are not installing with the current iso the upgrade wil fetch the the latest updates whereever they are i.e. cd or repositories
Plus if you are not going to boot from the disk there is no need to put it in and then dist-upgrade. You would do that if you didn't have an internet connection.
Some people like to use the disk to upgrade but they do a "clean install". They boot to the cd and reformat the hard drive and reinstall from the cd. If you're in your ubuntu install and place the cd in the drive and open the terminal and run the dist-upgrade the cd is just another "repository" for the update manager to use. If it has the newsest version of applications, those will be used. If it's applications are older than the ones on the online repositories then the manager will download from the repos and install them instead of installing from the cd.
So either boot from the cd or just let the packages be downloaded.

---

### Post by pt123 on 2006-06-02
That is just BS I downloaded the ISO today. I don't want to download the packages again from the internet. 

So every computer I have to upgrade I have to redownload all the files from the internet? That is ludicrous is Ubuntu in some deal with the ISP's so we have to redownload same files again and again.

The CD ROm upgrade worked fine for 5.04 to 5.10 upgrade.

---

### Post by neymac on 2006-06-02
[QUOTE=pt123]I tried to the Ubuntu upgrade with 6.06 CD option mentioned here
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

after I typed this
sudo apt-get update && sudo apt-get dist-upgrade

It says
960 upgraded, 153 newly installed, 40 to remove and 2 not upgraded.
Need to get 391MB/487MB of archives.
After unpacking 72.0MB of additional disk space will be used.


Why would I want it to download 391 MB when I downloaded the CD.

What is the point. ](*,)[/QUOTE]

did you use the "alternate" or the "desktop" CD?
To upgrade from previous installed Ubuntu you must use the "alternate" CD.
see [http://ubuntu.c3sl.ufpr.br/releases/6.06/](http://ubuntu.c3sl.ufpr.br/releases/6.06/)  
(Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
  [COLOR="Blue"]  * upgrading from older installations without network access;[/COLOR]
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 192MB of RAM. )

---

### Post by pt123 on 2006-06-02
Ok thanks I will try that

---

### Post by subtler on 2006-06-02
I made the same mistake. I tried to upgrade from the live/install cd not the alternate cd. my breezy got screwed up beyond help. so I just repartitioned and installed dapper from the iso I downloaded. I lost my old configuration. but then I didn't use half the stuff I put on breezy anyway. now I have dapper. I'll remember to read more carefully when I upgrade next time.

---

### Post by digitalkarabao on 2006-06-02
I am not alone :) I commited the same mistake. Charge it to experience.

---

### Post by pt123 on 2006-06-02
Yeah don't know why they had to release a separate CD for an upgrade. 

The xserver crashed after the upgrade. They need to implement a feature to go through reconfiguring it in the upgrade process.

---

### Post by neymac on 2006-06-02
[QUOTE=pt123]Yeah don't know why they had to release a separate CD for an upgrade. 

The xserver crashed after the upgrade. They need to implement a feature to go through reconfiguring it in the upgrade process.[/QUOTE]
My xserver crashed too. I did restart with the new kernel (2.6.15-23) and it work again.

---

