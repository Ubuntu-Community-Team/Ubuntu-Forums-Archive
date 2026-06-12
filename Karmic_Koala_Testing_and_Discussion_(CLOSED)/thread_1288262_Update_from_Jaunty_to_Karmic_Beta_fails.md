---
title: "Update from Jaunty to Karmic Beta fails?"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aeternitas on 2009-10-11
Running into a problem completing the upgrade from Jaunty to Karmic beta; running from update-manager -d ran fine until all packages were downloaded, following that (and every attempt to complete since) yields this dialog box:

The upgrade is now aborted. Your system could be in an unstable state. A recovery will run now (dpkg --configure -a).

Output if the command is run from a Terminal window sheds this light, though I'm not sure how to proceed with it:

```
ERROR:root:SystemError  from cache.commit(): E:Couldn't configure pre-depend openoffice.org-core for openoffice.org-filter-binfilter, probably a dependency cycle.
update-manager: Fatal IO error 9 (bad file descriptor) on X Server :0.0.
none
(several empty lines)
ERROR:root:SystemError from cache.commit(): installArchives() failed.
```Now, if update manager launches, it has quite a few packages it wants to deal with, giving me a prompt with 'Partial Upgrade' or 'Close'; partial upgrade gives me a repeat of the above, Close gives me a 600+ item list of packages to be updated.  Quite a bit lost here, and not sure how to proceed.  Suggestions, preferably that don't involve wiping my root part and starting over?

---

### Post by MelDJ on 2009-10-11
why do you want to update to Karmic Beta? wait a while for the stable release

---

### Post by Chris_82 on 2009-10-13
Same error here.
Tried more than once but the problem persists.

[jaunty / 2.6.28-15-generic]

---

### Post by kansasnoob on 2009-10-13
> **Chris_82 said:**
> Same error here.
Tried more than once but the problem persists.

[jaunty / 2.6.28-15-generic]

Would you please post the output from Terminal of:

```
cat /etc/issue
```

and:

```
uname -a
```

---

### Post by Chris_82 on 2009-10-13
Command outputs are the following:

cat /etc/issue:

Ubuntu 9.04 \n \l

uname -a:

Linux myibm 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux


cheers

---

### Post by kansasnoob on 2009-10-13
Run each of the following commands:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

And post any errors from "update" here along with the output from "upgrade". Like this:

> Fetched 10.3MB in 2min 46s (61.8kB/s)                                          
Reading package lists... Done
lance@lance-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  byobu
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 54.3kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 


Just type [COLOR="Red"]n[/COLOR] for now, I'm just trying to get a feeling for what's wrong.

---

### Post by kansasnoob on 2009-10-13
I'm going to be out for about an hour.

---

### Post by rb0171610 on 2009-10-13
> **aeternitas said:**
> Quite a bit lost here, and not sure how to proceed.  Suggestions, preferably that don't involve wiping my root part and starting over?
If you are trying to upgrade your stable version with the beta version on a machine that you are afraid to destroy the current installation on the root partition, you should consider doing one of the following:

A) backing up your partitions in case you want to do a full restore
B) installing the beta version in a virtual machine so that you can test it in a sandbox environment that will have not have an effect on your current Linux Installation
C) waiting for the final release of Karmic and trying your upgrade then

Upgrading to a Beta release is not recommended on a production machine.  It is crucial to remember that this software is being tested and is not the final version that will be released.  Even if you were to successfully upgrade, daily updates to the software can break your installation and/or render it not bootable.  That being said, happy testing.

---

### Post by kansasnoob on 2009-10-13
> **rb0171610 said:**
> If you are trying to upgrade your stable version with the beta version on a machine that you are afraid to destroy the current installation on the root partition, you should consider doing one of the following:

A) backing up your partitions in case you want to do a full restore
B) installing the beta version in a virtual machine so that you can test it in a sandbox environment that will have not have an effect on your current Linux Installation
C) waiting for the final release of Karmic and trying your upgrade then

Upgrading to a Beta release is not recommended on a production machine.  It is crucial to remember that this software is being tested and is not the final version that will be released.  Even if you were to successfully upgrade, daily updates to the software can break your installation and/or render it not bootable.  That being said, happy testing.

+1! All great recommendations!

I'm suspecting some confusion as to what a dist-upgrade to "testing" is.

I see no indication that the system is only "partially upgraded" to karmic. More likely that there's just a dpkg error we can easily resolve, along with some patient guidance.

---

### Post by Chris_82 on 2009-10-13
> sudo apt-get upgrade

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
...
The following packages will be upgraded:
...
844 upgraded, 0 newly installed, 0 to remove and 509 not upgraded.
Need to get 5574kB/727MB of archives.
After this operation, 215MB of additional disk space will be used.

```

I attached the whole output in the text file (... stand for the  packages)

thanks,
Christian

---

### Post by ranch hand on 2009-10-13
It would be good to see the contents of this file;
```

gksudo gedit /etc/apt/sources.list

```

---

### Post by kansasnoob on 2009-10-13
> **ranch hand said:**
> It would be good to see the contents of this file;
```

gksudo gedit /etc/apt/sources.list

```

It would be safer to use:

```
cat /etc/apt/sources.list
```

That way no accidental boo-boo will edit it.

---

### Post by kansasnoob on 2009-10-13
This:

> $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  acpid anacron apache2 apache2-mpm-worker apache2.2-common apport apt
  apt-transport-https apt-utils apt-xapian-index aptitude apturl asterisk
  asterisk-config asymptote asymptote-doc at audacity audacity-data automake
  avahi-daemon bc bind9-host bluez-gnome brasero brltty brltty-x11
  capplets-data consolekit cpp cpp-4.3 cron cups cups-bsd cups-client
  cups-driver-gutenprint cupsddk davfs2 dbus dmsetup dnsutils dolphin dpkg
  dpkg-dev ecj ecj-gcj eclipse eclipse-jdt eclipse-pde eclipse-platform
  eclipse-rcp eclipse-source ekiga emacs emacs22-bin-common emacs22-common
  emacs22-gtk enblend enfuse eog evince evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal exiv2 f-spot fastjar
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support
  firefox-gnome-support foomatic-db ftp g++ g++-4.3 gappletviewer-4.3
  gcalctool gcc gcc-4.3 gcc-4.3-base gcj-4.3 gcj-4.3-base gconf-editor gdb
  gddrescue gdm gdm-guest-session gedit gedit-common gettext ghostscript
  gij-4.3 gimp gimp-data gksu gnome-applets gnome-applets-data
  gnome-cards-data gnome-control-center gnome-games gnome-games-data gnome-mag
  gnome-media gnome-media-common gnome-netstatus-applet gnome-orca gnome-panel
  gnome-panel-data gnome-power-manager gnome-screensaver gnome-session
  gnome-settings-daemon gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes-ubuntu gnome-utils gnupg gnupg-agent gnupg2
  gparted gpgv grub gstreamer0.10-alsa gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines
  gtk2-engines-pixbuf guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse hal
  hal-cups-utils hardware-monitor hostname hpijs hplip hplip-data html2text
  hugin hugin-data hugin-tools human-theme hwinfo ifupdown imagemagick
  indicator-applet indicator-messages info initramfs-tools initscripts
  inkscape jackd jockey-common jockey-gtk junit4 kdebase-bin kdebase-data
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdelibs-bin
  kdelibs4c2a kdelibs5 keepassx kfind khelpcenter4 kile konqueror
  konqueror-nsplugins konsole ktouch lftp libaprutil1 libavc1394-0
  libbonoboui2-0 libbrasero-media0 libc-client2007b libc6 libc6-dev libc6-i686
  libcairo2 libcairomm-1.0-1 libcamel1.2-14 libclass-accessor-perl
  libcompress-raw-zlib-perl libcompress-zlib-perl libcups2 libcupsimage2
  libcurl3 libcurl3-gnutls libdbd-mysql-perl libdc1394-22 libdrm-dev
  libdrm-intel1 libdrm-nouveau1 libdrm2 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11
  libedataserverui1.2-8 libedit2 libegroupwise1.2-13 libept0
  libexchange-storage1.2-3 libexempi3 libexiv2-5 libfreebob0 libgail-common
  libgail18 libgcc1 libgcj-bc libgcj9-0 libgcj9-0-awt libgcj9-dev libgcj9-jar
  libgcj9-src libgdata-google1.2-1 libgdata1.2-1 libgdict-1.0-6 libgfortran3
  libgimp2.0 libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglib2.0-0
  libglib2.0-data libglibmm-2.4-1c2a libgnome-desktop-2-11 libgnome-media0
  libgnome-window-settings1 libgnome2.24-cil libgnomecups1.0-1
  libgnomekbd-common libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomevfs2-extra libgomp1 libgpod-common libgpod4 libgs8
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtkhtml-editor0 libgtkmm-2.4-1c2a libgtkspell0
  libgvfscommon0 libgweather1 libiec61883-0 libio-compress-base-perl
  libio-compress-zlib-perl libjack0 libkonq5 libltdl7 libmetacity0
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-data2.0-cil libmono-getoptions2.0-cil
  libmono-i18n2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil
  libnautilus-extension1 libneon27 libneon27-gnutls libnotify1 libokularcore1
  libopenmpi-dev libpango1.0-0 libpangomm-1.4-1 libpano13-bin libphonon4
  libpoppler-glib4 libpoppler-qt4-3 libpq5 libprotobuf3 libpurple0
  libpython2.6 libqca2 libqt4-dbus libqt4-designer libqt4-network
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-webkit libqt4-xml libqtcore4 libqtgui4 librdf0 librsvg2-2
  librsvg2-common libscim8c2a libsdl1.2debian libsdl1.2debian-alsa
  libsmbclient libsoprano4 libsoup-gnome2.4-1 libsoup2.4-1
  libstartup-notification0 libstdc++6 libstdc++6-4.3-dev libstreamanalyzer0
  libstreams0 libsvn1 libtag1c2a libthai-data libthai0 libtotem-plparser12
  libtracker-gtk0 libts-0.0-0 libunique-1.0-0 libvlc2 libwnck22 libwxbase2.8-0
  libwxgtk2.8-0 libxapian15 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x libxml++2.6-2 libxml2-utils lilypond
  lilypond-data linux-generic linux-headers-generic linux-image-generic
  lp-solve lshw luatex m4 metacity metacity-common
  mobile-broadband-provider-info module-init-tools mono-2.0-gac mono-gac
  mono-runtime motion mozilla-mplayer mplayer mysql-server mysql-server-5.0
  nautilus nautilus-data nautilus-sendto nautilus-share netbase nfs-common
  notify-osd ntfs-3g nvidia-180-modaliases nvidia-common obex-data-server
  octave3.0 okular openjdk-6-jdk openjdk-6-jre openmpi-common openoffice.org
  openoffice.org-base openoffice.org-base-core openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-filter-binfilter openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-officebean openoffice.org-writer openssh-client
  openssh-server parted perlmagick phonon phonon-backend-xine pidgin
  pidgin-data pidgin-libnotify pidgin-otr pinentry-gtk2 poppler-utils portmap
  procps pulseaudio-module-gconf pulseaudio-module-x11 python python-apport
  python-apt python-glade2 python-gnome2-desktop python-gst0.10 python-gtk2
  python-minimal python-uno python-wxgtk2.8 python-xapian python2.5
  python2.5-minimal python2.6 python2.6-minimal qt4-qtconfig readline-common
  redland-utils rhino rhythmbox rosegarden rosegarden-data rpm rss-glx samba
  samba-common scim scim-bridge-agent scim-bridge-client-gtk
  scim-gtk2-immodule scim-modules-socket screen-profiles
  screen-resolution-extra seahorse sg3-utils smbclient smbfs soprano-daemon
  splix ssh-askpass-gnome subversion synaptic system-tools-backends sysv-rc
  sysvinit-utils texlive-base-bin texlive-base-bin-doc texlive-xetex tomboy
  totem-common totem-gstreamer totem-plugins tracker tracker-search-tool
  tracker-utils transmission-common transmission-gtk ubuntu-minimal
  ubuntu-system-service udev ufw unattended-upgrades unetbootin unixodbc
  update-notifier upstart usb-creator usplash util-linux vinagre vino vlc
  vlc-nox wicd winbind wpasupplicant x11-common xorg xserver-xorg
  xserver-xorg-video-intel xulrunner-1.9 xulrunner-1.9-gnome-support yelp
The following packages will be upgraded:
  acpi-support adduser aircrack-ng alacarte alien alsa-base alsa-utils ant
  ant-gcj ant-optional ant-optional-gcj antlr apache2-utils apmd
  app-install-data app-install-data-partner apparmor apparmor-utils apport-gtk
  aspell aspell-en asterisk-sounds-main at-spi autoconf autotools-dev
  avahi-autoipd avahi-utils base-files bash bash-completion binfmt-support
  binutils binutils-static bluetooth bluez bluez-alsa bluez-cups
  bluez-gstreamer bluez-utils bogofilter bogofilter-bdb bogofilter-common
  bsdmainutils bsdutils busybox-initramfs bzip2 ca-certificates
  ca-certificates-java checkbox checkbox-gtk cli-common command-not-found
  command-not-found-data computer-janitor computer-janitor-gtk console-setup
  console-terminus coreutils cpio cups-common cups-pdf curl dash dblatex
  dbus-x11 dc debconf debconf-i18n debhelper default-jdk default-jre
  default-jre-headless desktop-file-utils dhcp3-client dhcp3-common
  dictionaries-common diff dir2ogg dkms dmidecode doc-base dosfstools dvipdfmx
  e2fslibs e2fsprogs ed eject emacsen-common esound esound-clients
  esound-common espeak espeak-data ethtool evolution-documentation-en
  example-content exim4-base exim4-config exim4-daemon-light fakeroot ffmpeg
  ffmpeg2theora fglrx-modaliases file file-roller findutils finger flac
  flashplugin-installer flashplugin-nonfree foo2zjs foomatic-db-engine
  foomatic-filters gamin gconf2 gconf2-common gdebi gdebi-core genisoimage
  gettext-base ghostscript-x gimp-help-common gimp-help-en git-core gjdoc
  gnome-about gnome-accessibility-themes gnome-app-install gnome-desktop-data
  gnome-doc-utils gnome-icon-theme gnome-keyring gnome-menus gnome-mount
  gnome-nettool gnome-pilot gnome-session-canberra gnome-themes-selected
  gnome-user-guide gnome-user-guide-en gnuplot gnuplot-nox gnuplot-x11 grep
  groff groff-base grub-common gsfonts gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-base-apps gstreamer0.10-schroedinger gthumb
  gthumb-data gtypist gucharmap guile-1.8 gzip h5utils hal-info hdf5-tools
  hdparm hfsplus hfsprogs hfsutils hicolor-icon-theme htop human-icon-theme
  hunspell-en-us hunt icedtea-6-jre-cacao imagemagick-doc inputattach iproute
  iptables iputils-arping iputils-ping iputils-tracepath iso-codes iw
  java-common kbd kbibtex kde-icons-oxygen kdebase-runtime-data-common
  kdelibs-data kdelibs5-data klibc-utils klogd language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector language-selector-common language-support-en
  language-support-writing-en laptop-mode-tools latex-beamer
  launchpad-integration less libaa1 libaccess-bridge-java libantlr-java
  libantlr-java-gcj libao2 libapm1 libapparmor-perl libapparmor1 libapr1
  libarchive1 libasound2 libasound2-plugins libaspell15 libatk1.0-0
  libatk1.0-data libatspi1.0-0 libattr1 libaudio2 libaudiofile0
  libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-glib1 libavahi-gobject0 libavahi-qt3-1
  libavahi-ui0 libavcodec52 libavdevice52 libavfilter0 libavformat52
  libavutil49 libbeagle1 libblkid1 libbluetooth3 libbonobo2-0
  libbonobo2-common libbonoboui2-common libboost-thread1.34.1 libbrlapi0.5
  libbz2-1.0 libcairo-perl libcanberra-gtk-module libcanberra-gtk0
  libcanberra0 libcap2 libcelt0 libchm1 libck-connector0 libcomerr2
  libcommons-beanutils-java libcommons-digester-java libcommons-el-java
  libcommons-logging-java libcryptui0 libcwidget3 libdaemon0 libdb4.6 libdb4.7
  libdbi-perl libdbus-1-3 libdbus-glib-1-2 libdca0 libdecoration0
  libdevmapper1.02.1 libdigest-sha1-perl libdjvulibre-text libdjvulibre21
  libdmx1 libdv4 libdvdread4 libecj-java libecj-java-gcj libelf1 libenca0
  libenchant1c2a libesd-alsa0 libespeak1 libevdocument1 libevview1 libexif12
  libexpat1 libffi5 libfftw3-3 libflac++6 libflac8 libfreetype6
  libfreezethaw-perl libfribidi0 libfs6 libgamin0 libgcj-common libgconf2-4
  libgconfmm-2.6-1c2 libgcr0 libgcrypt11 libgdiplus libglade2.0-cil
  libglademm-2.4-1c2a libglew1.5 libglib-perl libglib2.0-cil libglpk0
  libglu1-mesa libgmime-2.0-2a libgmime2.2a-cil libgmp3c2 libgmyth0
  libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-menu2
  libgnome-pilot2 libgnome2-0 libgnome2-canvas-perl libgnome2-common
  libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0 libgnomecanvas2-common
  libgnomecanvasmm-2.6-1c2a libgnomepanel2.24-cil libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common
  libgnutls26 libgp11-0 libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpm2
  libgraphviz4 libgsf-1-114 libgsf-1-common libgsm1 libgssglue1
  libgtk-vnc-1.0-0 libgtk2.0-cil libgtk2.0-common libgtkhtml-editor-common
  libgtkhtml2-0 libgtkhtml3.14-19 libgtksourceview2.0-0
  libgtksourceview2.0-common libgtop2-7 libgtop2-common libgucharmap7
  libgutenprint2 libgweather-common libhal-storage1 libhal1
  libhdf5-mpich-1.6.6-0 libhfsp0 libhsqldb-java libhtml-parser-perl
  libhunspell-1.2-0 libhyphen0 libical0 libice-dev libice6 libid3tag0 libidn11
  libieee1284-3 libijs-0.35 libilmbase6 libimage-exiftool-perl libimlib2
  libio-socket-ssl-perl libiptcdata0 libiw29 libjasper1 libjaxp1.3-java
  libjaxp1.3-java-gcj libjpeg62 libjsch-java libkeyutils1 libklibc
  libkonq5-templates libkpathsea4 libksba8 liblapack3gf
  liblaunchpad-integration1 liblcms1 libldap-2.4-2 liblircclient0
  liblog4j1.2-java liblog4j1.2-java-gcj liblpint-bonobo0 liblrdf0 liblua5.1-0
  liblua50 liblualib50 libmagic1 libmeanwhile1 libmng1 libmodplug0c2
  libmono-cairo2.0-cil libmono0 libmp3lame0 libmpcdec3 libmpfr1ldbl
  libmpg123-0 libmpich1.0gf libmtp8 libmx4j-java libmysqlclient15off
  libnautilus-burn4 libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libndesk-dbus1.0-cil libnet-libidn-perl libnetpbm10 libnewt0.52 libnl1
  libnm-util1 libnotify-bin libnspr4-0d libnss-mdns libnss3-1d libntfs10
  libofa0 libogg0 liboil0.3 liboobs-1-4 libopenal1 libopenexr6 libopenobex1
  libpam-ck-connector libpam-gnome-keyring libpam-modules libpam-runtime
  libpam0g libpanel-applet2-0 libpango1.0-common libpcap0.8 libpci3
  libpciaccess-dev libpciaccess0 libpcre3 libpcsclite1 libperl5.10 libpisock9
  libpisync1 libpixman-1-0 libpixman-1-dev libplot2c2 libplrpc-perl libpng12-0
  libpolkit-dbus2 libpolkit-grant2 libpolkit2 libportaudio2 libpostproc51
  libpulse-browse0 libpulse0 libpurple-bin libqhull5 libqt3-mt
  libradiusclient-ng2 libraptor1 librarian0 libreadline5 libruby1.8
  libsamplerate0 libsane libsasl2-2 libsasl2-modules libschroedinger-1.0-0
  libsdl-image1.2 libselinux1 libsensors3 libsepol1 libsexy2 libshout3
  libsigsegv0 libsilc-1.1-2 libslang2 libsm-dev libsm6 libsndfile1
  libsnmp-base libsnmp15 libspectre1 libsqlite0 libsqlite3-0 libss2
  libssl0.9.8 libstlport4.6ldbl libsvga1 libswscale0 libtalloc1 libtar
  libtasn1-3 libtdb1 libtext-wrapi18n-perl libtheora0 libtiff4 libtool
  libtrackerclient0 libudev0 libusplash0 libuuid1 libv4l-0
  libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpb0
  libvte-common libvte9 libwbclient0 libwmf-bin libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-common libwww-perl libx11-6 libx11-data libx11-dev libx86-1
  libxau-dev libxau6 libxaw7 libxcb-render-util0 libxcb-render0 libxcb-shape0
  libxcb-shm0 libxcb-xv0 libxcb1 libxcb1-dev libxcomposite1 libxcursor1
  libxerces2-java libxerces2-java-gcj libxext6 libxfixes3 libxfont1 libxi6
  libxml-twig-perl libxml2 libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1
  libxres1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86vm1 lilypond-doc
  linux-firmware linux-libc-dev linux-sound-base locales lockfile-progs login
  logrotate lsb-base lsb-release lsof ltrace lynx lynx-cur make man-db
  manpages mawk memtest86+ mesa-common-dev mesa-utils mime-support min12xxw
  mktemp mlocate mlock module-assistant mount mousetweaks mpg123 mpich-bin
  mtools mysql-client-5.0 mysql-common mysql-server-core-5.0 ncurses-base
  ncurses-bin net-tools netpbm ntfsprogs ntpdate nvidia-173-modaliases
  nvidia-96-modaliases odbcinst1debian1 onboard openjdk-6-jre-headless
  openjdk-6-jre-lib openoffice.org-emailmerge openoffice.org-filter-mobiledev
  openoffice.org-hyphenation-en-us openoffice.org-java-common
  openoffice.org-l10n-common openoffice.org-report-builder-bin
  openoffice.org-style-human openoffice.org-writer2latex openprinting-ppds
  openssl p7zip p7zip-full partimage passwd pciutils perl perl-base perl-doc
  perl-modules pkg-config pm-utils pnm2ppa po-debconf policykit
  popularity-contest preview-latex-style ps2eps psmisc pulseaudio-utils pxljr
  python-brlapi python-cairo python-central python-cups python-cupshelpers
  python-dbus python-debian python-fstab python-gconf python-gdata python-gdbm
  python-gmenu python-gnome2 python-gnomecanvas python-gobject python-gtkhtml2
  python-gtksourceview2 python-launchpad-bugs python-launchpad-integration
  python-libxml2 python-mutagen python-newt python-numpy python-pkg-resources
  python-problem-report python-pyatspi python-software-properties
  python-support python-tk python-uniconvertor python-usb python-vte
  python-wxversion raptor-utils rarian-compat rdesktop reiserfsprogs
  resolvconf rsync ruby1.8 sane-utils screen scrot seahorse-plugins sed
  shared-mime-info sndfile-programs software-properties-gtk ssh sshfs ssl-cert
  strace sudo swh-plugins sysklogd system-config-printer-common
  system-config-printer-gnome tangerine-icon-theme tar tasksel tasksel-data
  tcl8.5 tcpdump tex-common tex4ht tex4ht-common texinfo texlive texlive-base
  texlive-bibtex-extra texlive-common texlive-doc-base texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-extra texlive-generic-recommended texlive-humanities
  texlive-humanities-doc texlive-lang-cyrillic texlive-lang-french
  texlive-latex-base texlive-latex-base-doc texlive-latex-extra
  texlive-latex-extra-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-math-extra texlive-metapost
  texlive-metapost-doc texlive-pictures texlive-pictures-doc texlive-pstricks
  texlive-pstricks-doc tipa tk8.5 toshset tsclient ttf-dejavu ttf-dejavu-core
  ttf-dejavu-extra ttf-freefont ttf-liberation ttf-opensymbol
  ttf-sazanami-gothic ttf-sazanami-mincho ttf-thai-tlwg ttf-wqy-zenhei tzdata
  tzdata-java ubufox ubuntu-artwork ubuntu-docs ubuntu-gdm-themes
  ubuntu-keyring ubuntu-sounds ubuntu-standard ubuntu-wallpapers ucf
  unetbootin-translations uno-libs3 unrar unzip update-manager
  update-manager-core update-motd update-notifier-common ure usbutils
  usplash-theme-ubuntu uuid-runtime vim-common vim-tiny virtualbox-ose
  virtualbox-ose-source vlc-data vorbis-tools vpb-driver-source w3m wamerican
  wbritish wget whiptail whois wireless-crda wireless-tools wodim x11-apps
  x11-session-utils x11-xkb-utils x11-xserver-utils x11proto-core-dev
  x11proto-dri2-dev x11proto-gl-dev x11proto-input-dev x11proto-xext-dev
  xdg-user-dirs xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xinit
  xinput xkb-data xsane-common xscreensaver-data xscreensaver-gl
  xserver-common xserver-xorg-core xserver-xorg-dev xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xtrans-dev
  xutils-dev zenity zip zlib1g zlib1g-dev
844 upgraded, 0 newly installed, 0 to remove and 509 not upgraded.
Need to get 5574kB/727MB of archives.
After this operation, 215MB of additional disk space will be used.


may or may not be part of a dist-upgrade!

But there is no way to stop half way through that I know of so what happens when you say yes (y)?

---

### Post by ranch hand on 2009-10-13
I would get that sources list first.

---

### Post by kansasnoob on 2009-10-13
> **ranch hand said:**
> I would get that sources list first.

You can't stop a dist-upgrade somewhere in the middle!

Some directories/files will want to "look" in the wrong place!

---

### Post by ranch hand on 2009-10-13
I just like to check the sucker before starting.  I guess it is because he started this with Update Mangler.  I trust it about as far as I can throw my horse.

But you are right, it is a bit late now.

This is the way i always do this, with apt.  It should work alright, apt is picky and probably wouldn't work if things were really flaky.

---

### Post by kansasnoob on 2009-10-13
You have a horse?

I only have two old faintin' goats that cost me tons of money!

Back to THE problem, I'm still not sure that's a dist-upgrade. I mean 5 months into Jaunty?

I think it may be OK!

---

### Post by ranch hand on 2009-10-13
Come to look again and the command is "upgrade".  I hope the sources list has not been changed to "karmic".  Looks like a big upgrade unless he hasn't done one for months.  I hope he doesn't reboot before checking where those packages came from.

He is, as far as I know on the highest kernel.  I see in the list of packages held back (100 lines of them) that line 76 is "lilypond-data linux-generic linux-headers-generic linux-image-generic".

If his sources list has gone to karmic he better run apt again with "dist-upgrade" or go to synaptic.  Another run of dpkg --configure -a wouldn't hurt either in that case.

Yes i have a horse, and a cattle dog.  Goes with the job.

---

### Post by kansasnoob on 2009-10-13
Well, there'd be no harm done just looking at software sources but I already know just by looking at firefox, grub (lack of), and X updates.

It's Jaunty with a dpkg error and maybe some other stuff going on.

And it would be ill advised to upgrade to Karmic!

---

### Post by ranch hand on 2009-10-13
Yeh I noticed the FF 3.0.  I don't think that Jaunty has been updated for a long time.  As obtrusive as Update Mangler is in it I don't quite understand that.

I wonder if it was just installed from an older .iso and not updated.  That would go a ways to explaining the trouble upgrading to 9.10.  I have had trouble with a couple that I upgraded.  Never could figure out why.  Other identical ones upgraded fine.

Had one that I had to run dpkg --configure -a twice in a row so that I could go to synaptic and deal with a bunch of broken packages before I could run an update on it.  Next time I booted fsck said it was 32% screwy.

---

### Post by VMC on 2009-10-13
*deleted nonsense.*

---

### Post by Chris_82 on 2009-10-14
I agree that I am not the original poster..but I seem to have the same problem..

Anyway, my software sources have been changed to karmic once I started the update-manager with this command:

```
sudo update-manager -d
```

**Sources**:

```
$ more /etc/apt/sources.list | grep -v "^#" | grep -v "^$"
deb http://ubuntu.intergenia.de/ubuntu/ karmic main universe restricted multiverse
deb http://ubuntu.intergenia.de/ubuntu/ karmic-updates main universe restricted multiverse
deb http://archive.canonical.com/ubuntu karmic partner
deb http://ubuntu.intergenia.de/ubuntu/ karmic-security main universe restricted multiverse
```

thanks for the help.

---

### Post by ranch hand on 2009-10-14
You are able to boot to the OS?

You may have said but I really hope that you have run'
```

sudo dpkg --configure -a

```
If there is nothing stuck there is no harm in doing this and if here is it will most likey clear it.

I do not believe that it would be a good idea to try to go back to Jaunty.

Do you have your data, or better yet your entire home folder backed up?

I would do the back up before doing anything else at all.

---

### Post by Chris_82 on 2009-10-14
> **ranch hand said:**
> You are able to boot to the OS?

Yes, all of Jaunty runs perfectly, as almost always :)

> **ranch hand said:**
> 
You may have said but I really hope that you have run'
```

sudo dpkg --configure -a

```
If there is nothing stuck there is no harm in doing this and if here is it will most likey clear it.

I didn't do it in the first place, no. But I tried it just now and rebooted..I have not yet tried to run the **update-manager -d** once again..

> **ranch hand said:**
> 
I do not believe that it would be a good idea to try to go back to Jaunty.

I still am 100% in Jaunty, all the update did so far was change my sources.list file.

Do you have your data, or better yet your entire home folder backed up?

> **ranch hand said:**
> 
I would do the back up before doing anything else at all.

Yes, always, so don't worry, even if there is something getting messy I can come back to my old setup & data pretty quickly :)

---

### Post by Chris_82 on 2009-10-14
I should post these screenshots too..taken at the end of the **update-manager -d** command:

[INDENT]The first one is about the **dpkg --configure -a**

The final screenshot tells us something about the openoffice.org-core (openoffice.org-filter-binfilter) package dependencies.
Then follows a **Fatal IO error 9**
I have no clue about that how to know about the source of that error..
[/INDENT]

---

### Post by ranch hand on 2009-10-14
Do not re-run this in Update Mangler.

I would go to synaptic and click on the status button (bottom left on your screen) and see if there are any broken packages.  Before doing anything about any broken packages I would go to Settings>Preferences and in the first (General) tab check all the boxes except the last one (do not click on that one at all - make sure it is blank).

Now if you click on the menu item "Broken Packages" (assuming you have any) and right click on the box by the package in the main window, you will get the recommended action for that package.  You do not have to carry this out but it is nice to know.

Check to see what kernels are installed too, while you are there in synaptic.

How about checking that stuff?  Let us see where you are.

---

### Post by Chris_82 on 2009-10-14
> **ranch hand said:**
> 
I would go to synaptic and click on the status button (bottom left on your screen) and see if there are any broken packages.  Before doing anything about any broken packages I would go to Settings>Preferences and in the first (General) tab check all the boxes except the last one (do not click on that one at all - make sure it is blank).
done :-)

> **ranch hand said:**
> 
Now if you click on the menu item "Broken Packages" (assuming you have any) and right click on the box by the package in the main window, you will get the recommended action for that package.
there are none broken.

> **ranch hand said:**
> Check to see what kernels are installed too, while you are there in synaptic.

```
$ dpkg --list | grep linux-image
ii  linux-image-2.6.28-11-generic              2.6.28-11.42                              Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-13-generic              2.6.28-13.45                              Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-14-generic              2.6.28-14.47                              Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-15-generic              2.6.28-15.52                              Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.29-020629-generic          2.6.29-020629                             Linux kernel image for version 2.6.29 on x86
ii  linux-image-generic                        2.6.28.15.20                              Generic Linux kernel image

```

{gonna hit the hay now :-)}

---

### Post by ranch hand on 2009-10-14
Well I'll be.

I think if I was you, I would switch my sources back to jaunty and run apt-get update and apt-get upgrade just to make sure you are caught up.  And to see if anything breaks.

I would gksudo gedit /etc/atp/sources.list and the first thing Iwould do is save it as "sources.list.karmic.  Then I would change the bugger back to jaunty and save that as sources.list.

That way, when 9.10 settles down just a little bit, if you still wnat you can try this again.  All you will need to do is change the name of your sources.list to sources.list.jaunty and knock the karmic off the other copy and hit apt-get update and apt-get dist upgrade.

Make sure that your copy of Jaunty is right up to date before trying this again.  Tommorow is kernel freeze, and I beleive the RC is to come out the 22nd.  That is what I would be shooting for.

---

### Post by Chris_82 on 2009-10-17
> **ranch hand said:**
> I think if I was you, I would switch my sources back to jaunty and run apt-get update and apt-get upgrade just to make sure you are caught up.  And to see if anything breaks.

Did that, nothing broke. My system has been up-to-date.

How I finally got my machine from Jaunty to Karmic was with a fresh install from a Karmic-CD. I think that was a good idea since that way my "/" got cleaned from any remaining more or less big jaunty-issues. :P

Thanks for the help anyway,

cl

---

### Post by aeternitas on 2009-10-17
> **Chris_82 said:**
> 
How I finally got my machine from Jaunty to Karmic was with a fresh install from a Karmic-CD.
cl

This is ultimately what I ended up doing; my home folder was no big deal, I had a few screenshots in it, that was it; anything critical I keep on a separate partition. Reading through the thread here, anything that was suggested here I'm sure would have yielded approximately the same results.

I have learned my lesson, though;when 10.4 gets going, I'll wait for release, rather than play around with a Beta...unless I have a system that can handle a VM well :P

---

### Post by ranch hand on 2009-10-17
I prefer clean installs myself.  I can back up and put the data back on later with a clean OS.

I think we are going to be pleased with this bugger.

---

### Post by Chris_82 on 2009-10-17
Yes indeed I am pleased so far with the Kolala.. :-)

Flash videos in firefox take way too much cpu at the moment but I think the final Koala will be fine.

---

