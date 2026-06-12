---
title: "What is 'error broken count 0' mean?.."
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by Thebuntuway on 2012-03-13
Hi fellas, i am truely new in linux. There are some problem that i need to solve. The error called 'broken count 0'. I am so  don't understand with it and im not dare to act like professional linux user because im just to young with it. So guys, is there any way to fix this?

---

### Post by jerrrys on 2012-03-13
I don't know what that means.  Can you just tell me whats not working?

---

### Post by raja.genupula on 2012-03-14
in which process you are getting that error ?

are you trying to launch/install/execute something ? 

whats the action giving you thats error . 

please give us that info . Thank you

---

### Post by Thebuntuway on 2012-03-14
These is the error fellas!
------------------------------------------------------------------
An error occurred, please run package manager from the right-click or  apt-get in a terminal to see what is wrong. The error message was:  'Error: Broken count>0: This is usually means that your installed  package have unmet dependencies.
-------------------------------------------------------------------
And these what i got when i run 'apt-get' in terminal:
The program 'apt' can be found in the following packages:
 * openjdk-6-jdk
 * openjdk-7-jdk
Try: sudo apt-get install <selected package>
--------------------------------------------------------------------
Then i insert the 'sudo apt-get install -f', these what i got:
```
cursethephobia@cursethephobia:~$ sudo apt-get install -f
[sudo] password for cursethephobia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  accountsservice adduser adobe-flash-properties-gtk apg appmenu-qt apport-gtk
  apt apt-transport-https apt-xapian-index apturl apturl-common aspell-en
  avahi-autoipd avahi-utils bamfdaemon banshee banshee-extension-soundmenu
  base-files bc binfmt-support bluez bluez-alsa bluez-gstreamer brasero
  brasero-common bsdutils bzip2 c2esp checkbox cli-common colord compiz
  compiz-core compiz-plugins-default compiz-plugins-main-default console-setup
  coreutils cpp-4.6 cups-client cups-driver-gutenprint cups-ppdc dash dbus
  debconf debianutils desktop-file-utils dictionaries-common diffutils
  dmidecode dnsmasq-base dnsutils doc-base duplicity dvd+rw-tools e2fslibs ed
  empathy eog espeak evince evince-common evolution-data-server exiv2 file
  firefox-globalmenu fontconfig foo2zjs gamin gbrainy gcalctool gcc-4.6
  gconf2-common gdb gedit gedit-common genisoimage geoclue
  geoclue-ubuntu-geoip gettext-base gir1.2-atk-1.0 gir1.2-atspi-2.0
  gir1.2-dbusmenu-gtk-0.4 gir1.2-gconf-2.0 gir1.2-gmenu-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-indicate-0.6 gir1.2-soup-2.4
  gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-webkit-3.0 glib-networking
  gnome-control-center gnome-font-viewer gnome-games-common gnome-icon-theme
  gnome-icon-theme-symbolic gnome-keyring gnome-media gnome-nettool
  gnome-screenshot gnome-search-tool gnome-session gnome-session-canberra
  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log
  gnome-system-monitor gnome-terminal gnome-user-guide gpgv grub-common
  grub-pc-bin gs-cjk-resource gsettings-desktop-schemas
  gstreamer0.10-fluendo-mp3 gstreamer0.10-nice gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-ugly gtk2-engines gtk2-engines-murrine
  gtk3-engines-unico gvfs-backends gvfs-bin gwibber-service-facebook hdparm
  hpijs humanity-icon-theme hunspell-en-us ibus-gtk ibus-gtk3 ibus-pinyin
  ifupdown indicator-appmenu indicator-power indicator-session indicator-sound
  initramfs-tools initramfs-tools-bin install-info intel-gpu-tools iproute
  isc-dhcp-common jockey-common language-pack-en language-pack-gnome-en-base
  language-selector-gnome laptop-detect lftp liba52-0.7.4
  libappindicator0.1-cil libappindicator1 libapt-inst1.3 libapt-pkg4.11
  libasound2 libasound2-plugins libaspell15 libatasmart4 libatspi2.0-0
  libattr1 libavahi-glib1 libavahi-ui-gtk3-0 libavc1394-0 libbamf0 libbamf3-0
  libbind9-60 libbluetooth3 libbrasero-media3-1 libburn4 libc-dev-bin
  libc6-dev libcairo-gobject2 libcairo2 libcairomm-1.0-1
  libcanberra-gtk-module libcanberra-gtk3-0 libcanberra-gtk3-module
  libcap2-bin libcdio-cdda0 libcdio10 libck-connector0 libclass-isa-perl
  libcolamd2.7.1 libcups2 libcupsdriver1 libcupsmime1 libcurl3-gnutls
  libdaemon0 libdbus-1-3 libdbus-glib-1-2 libdbus-glib1.0-cil
  libdbusmenu-glib4 libdconf-dbus-1-0 libdconf-qt0 libdconf0 libdecoration0
  libdevmapper-event1.02.1 libdevmapper1.02.1 libdns69 libdrm-nouveau1a
  libdrm-radeon1 libdrm2 libdv4 libdvdread4 libebook1.2-12 libedata-cal-1.2-13
  libedataserver1.2-15 libedataserverui-3.0-1 libelf1 libenchant1c2a
  libespeak1 libexempi3 libexif12 libexpat1 libffi6 libfile-basedir-perl
  libfile-mimeinfo-perl libflac8 libfolks-telepathy25 libfontconfig1
  libfreetype6 libfribidi0 libfuse2 libgail-3-0 libgail-3-common libgamin0
  libgcc1 libgconf2-4 libgconf2.0-cil libgcr-3-1 libgcrypt11 libgd2-xpm
  libgdata13 libgdbm3 libgdiplus libgdk-pixbuf2.0-0 libgdu-gtk0 libgdu0
  libgeoip1 libgif4 libgirepository-1.0-1 libgksu2-0 libgl1-mesa-dri
  libglade2-0 libglapi-mesa libglib-perl libglu1-mesa libgnome-control-center1
  libgnome-menu2 libgnome2-common libgnomekbd7 libgnomevfs2-common
  libgoa-1.0-0 libgpg-error0 libgpgme11 libgpod-common libgpod4 libgrip0
  libgs9 libgssapi-krb5-2 libgssdp-1.0-2 libgstfarsight0.10-0
  libgstreamer-plugins-base0.10-0 libgtk-3-0 libgtk-3-common
  libgtk-sharp-beans-cil libgtk2.0-0 libgtk2.0-cil libgtkmm-2.4-1c2a
  libgtksourceview-3.0-0 libgtkspell0 libgtop2-7 libgudev-1.0-0
  libgudev1.0-cil libgupnp-igd-1.0-3 libgvnc-1.0-0 libgweather-3-0
  libgwibber-gtk2 libgwibber2 libhunspell-1.2-0 libical0 libidl0 libidn11
  libieee1284-3 libimobiledevice2 libindicate-gtk3
  libindicator-messages-status-provider1 libisc62 libisccc60 libisccfg62
  libjpeg62 libjson-glib-1.0-0 libk5crypto3 libkeyutils1 libkpathsea5
  libkrb5support0 liblaunchpad-integration1.0-cil liblcms2-2 libllvm2.9
  libltdl7 liblvm2app2.2 liblwres60 libmagic1 libmission-control-plugins0
  libmono-addins-gui0.2-cil libmono-cairo4.0-cil libmono-csharp4.0-cil
  libmono-system-configuration4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libmount1 libmpc2 libmtp9 libnatpmp1 libncurses5
  libneon27-gnutls libnice10 libnl3 libnm-util2 libnotify-bin libnotify0.4-cil
  libnotify4 libnspr4 libnux-1.0-0 libogg0 liboil0.3 libopencc1
  libopencore-amrwb0 liboverlay-scrollbar3-0.2-0 libpam-gnome-keyring
  libpam-modules libpam0g libpango-perl libpango1.0-0 libparted0debian1
  libpcap0.8 libpci3 libpeas-1.0-0 libperl5.12 libplymouth2
  libpolkit-agent-1-0 libpolkit-gobject-1-0 libpopt0 libportaudio2
  libprotobuf7 libproxy0 libpth20 libpulse-mainloop-glib0 libpulse0
  libpurple-bin libpurple0 libpython2.7 libqt4-dbus libqt4-declarative
  libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqtbamf1 libqtcore4 libqtdee2 libqtgconf1 libqtgui4 libquadmath0 libquvi0
  libraptor2-0 librarian0 libraw1394-11 librdf0 libreadline6
  libreoffice-base-core libreoffice-common libreoffice-emailmerge
  libreoffice-gnome libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-writer librest-0.7-0 librsync1 librtmp0
  libsamplerate0 libsane libsane-hpaio libsdl1.2debian libsgutils2-2 libshout3
  libslp1 libsmbclient libsnmp15 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2
  libspeex1 libspeexdsp1 libsqlite3-0 libssl1.0.0 libswitch-perl libsysfs2
  libt1-5 libtag1-vanilla libtasn1-3 libtdb1 libtelepathy-glib0
  libtelepathy-logger2 libtext-iconv-perl libtext-wrapi18n-perl libtextcat0
  libthai0 libtheora0 libtiff4 libtotem-plparser17 libtwolame0 libudev0
  libunity6 libupower-glib1 libusb-0.1-4 libusb-1.0-0 libusbmuxd1 libutempter0
  libutouch-evemu1 libutouch-frame1 libuuid-perl libuuid1 libv4l-0
  libvorbisenc2 libvorbisfile3 libvte-2.90-9 libwavpack1 libwbclient0
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwmf0.2-7 libwpd-0.9-9 libwps-0.2-2
  libx264-116 libxapian22 libxcb-dri2-0 libxcb-render0 libxcb-shm0
  libxcb-util0 libxcb1 libxcomposite1 libxdmcp6 libxext6 libxfont1 libxi6
  libxinerama1 libxkbfile1 libxml2 libxmuu1 libxpm4 libxrandr2 libxrender1
  libxres1 libxslt1.1 libxv1 libxvmc1 libxxf86dga1 libyelp0
  linux-headers-3.0.0-12 linux-headers-3.0.0-12-generic locales lockfile-progs
  login logrotate lsb-base lsb-release lshw makedev man-db memtest86+ metacity
  metacity-common modemmanager module-init-tools mono-gac mono-runtime mount
  mountall mousetweaks mscompress mtools mtr-tiny nautilus-data nautilus-share
  ncurses-bin netbase netcat-openbsd network-manager-pptp ntfs-3g
  obex-data-server openprinting-ppds openssl os-prober overlay-scrollbar
  parted pciutils pcmciautils perl-base perl-modules
  plymouth-theme-ubuntu-logo pm-utils policykit-1-gnome ppp pppconfig procps
  psmisc pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr
  python python-appindicator python-apport python-aptdaemon
  python-aptdaemon.gtk3widgets python-brlapi python-cairo python-dbus
  python-defer python-egenix-mxdatetime python-egenix-mxtools python-gdbm
  python-gnupginterface python-gobject-2 python-gobject-cairo python-ibus
  python-indicate python-keyring python-lazr.uri python-libproxy
  python-minimal python-papyon python-pexpect python-pkg-resources
  python-protobuf python-pycurl python-smbc python-software-properties
  python-support python-twisted-bin python-twisted-web python-ubuntuone-client
  python-ubuntuone-control-panel python-vte python-wnck python-xkit
  python-zope.interface python2.7 python2.7-minimal qt-at-spi radeontool
  rfkill rsync samba-common sane-utils seahorse sed shared-mime-info shotwell
  simple-scan software-center splix ssh-askpass-gnome ssl-cert sudo
  system-config-printer-gnome system-config-printer-udev sysv-rc tar tcpd
  tcpdump telepathy-butterfly telepathy-gabble telepathy-haze
  telepathy-indicator telepathy-mission-control-5 telnet thunderbird
  thunderbird-globalmenu totem totem-mozilla ttf-unfonts-core tzdata
  ubuntu-artwork ubuntu-extras-keyring ubuntu-sso-client ubuntu-standard
  ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel
  ubuntuone-control-panel-gtk ubuntuone-installer ucf udisks unity unity-2d
  unity-2d-panel unity-asset-pool unity-common unity-greeter unity-services
  update-inetd update-manager-core ure usb-creator-common usb-modeswitch
  usbutils vim-common vinagre visualboyadvance visualboyadvance-gtk wamerican
  whiptail whois wireless-crda wpasupplicant x11-session-utils x11-xkb-utils
  xdg-user-dirs-gtk xfonts-base xfonts-mathml xfonts-scalable xinit xorg
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-fbdev
  xserver-xorg-video-openchrome xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-savage xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-vesa
  xserver-xorg-video-vmware xterm zeitgeist zeitgeist-core
  zeitgeist-extension-fts zlib1g
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libapt-pkg4.11 (due to apt) libgcc1 (due to apt) zlib1g (due to apt)
  base-files bsdutils coreutils libattr1 (due to coreutils) dash debianutils
  (due to dash) diffutils login libpam0g (due to login) libpam-modules (due to
  login) mount libmount1 (due to mount) ncurses-bin libncurses5 (due to
  ncurses-bin) perl-base python-minimal python2.7-minimal (due to
  python-minimal) sed install-info (due to sed) tar
0 upgraded, 0 newly installed, 650 to remove and 0 not upgraded.
After this operation, 960 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] Yes, do as I say!
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 15665 package 'libgmime2.4-cil':
 missing description
dpkg: error: parsing file '/var/lib/dpkg/status' near line 15665 package 'libgmime2.4-cil':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
```
-----------------------------------------------------------------------------------
SO THEN???:confused::confused::confused::confused::confused::confused::confused:

---

### Post by jerrrys on 2012-03-14
Hi Thebuntuway

in terminal enter:

sudo apt-get update

and please post any errors

---

### Post by whiskers751 on 2012-03-15
You probably have some package that has loads of dependencies.
To have a look, type sudo aptitude.
That should let you see the problem...

---

### Post by raja.genupula on 2012-03-15
i think you have gone to big area . your system saying apt was not found . but for one more time confirmation as Jerry asked give me output of 

```
sudo apt-get update
```

---

