---
title: "Update to 11.04 Big Problem"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by DaMonsterMonster on 2011-05-08
hey guys i was being a little impacient with my friends Dell Inspiron 1545 tonight..
i was updating to 11.04 from 10.10 and decided to install adobe flash player plugins at the same time...
so since i was installing 11.04 it wouldnt install adobe...i went back to the distribution upgrade now this pulls up...
Not all updates can be installed
run a partial upgrade.....
i hit run partial...now this comes up..
Can not upgrade
An upgrade from 'maverick' to 'lucid' is not supported with this tool.

when i hit reload this comes up
AN ERROR HAS OCCURRED
W: GPG error: [http://extras.ubuntu.com]("http://extras.ubuntu.com/")  maverick Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 16126D3A3E5C1192

ive restarted the computer....nothing...any help??

---

### Post by cipherboy_loc on 2011-05-08
Try:

```

sudo apt-get update 
sudo do-dist-upgrade
sudo apt-get upgrade

```

and post back (in CODE tags) the results of each.


Cipherboy

---

### Post by DaMonsterMonster on 2011-05-08
> **cipherboy_loc said:**
> Try:

```

sudo apt-get update 
sudo do-dist-upgrade
sudo apt-get upgrade

```and post back (in CODE tags) the results of each.


Cipherboy


byron@byron-laptop:~$ sudo apt-get update 
[sudo] password for byron: 
0% [Connecting to us.archive.ubuntu.com] [Connecting to security.ubuntu.com] [C
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                     
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31.4kB]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg [198B]         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [9,762B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release [31.4kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Packages                            
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Packages [144kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Packages [362kB]      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Packages [14B]   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [41.6kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Packages [63.5kB] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [15.7kB]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Packages [3,754B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [1,763B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Packages [1,797B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources [129kB]      
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources [778B] 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Packages [134kB] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources [42.2kB] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Packages [5,187B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources [2,497B]
Fetched 1,011kB in 46s (21.8kB/s)                                              
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
byron@byron-laptop:~$ 
byron@byron-laptop:~$ 

byron@byron-laptop:~$ sudo do-dist-upgrade
sudo: do-dist-upgrade: command not found
byron@byron-laptop:~$ 


byron@byron-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  aisleriot apt apt-transport-https apt-utils aptdaemon aptitude at-spi
  avahi-daemon bind9-host brasero brasero-common brltty brltty-x11
  capplets-data compiz compiz-core compiz-fusion-plugins-main compiz-gnome
  compiz-plugins computer-janitor computer-janitor-gtk cpp cpp-4.4 cron cups
  dnsutils dpkg empathy empathy-common eog evince evolution evolution-common
  evolution-couchdb evolution-data-server evolution-data-server-common
  evolution-exchange evolution-indicator evolution-plugins evolution-webcal
  f-spot file-roller firefox firefox-branding firefox-gnome-support gbrainy
  gcc gcc-4.4 gcc-4.4-base gdebi gdebi-core gdm gedit gksu gnome-applets
  gnome-bluetooth gnome-control-center gnome-disk-utility gnome-games-common
  gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common
  gnome-nettool gnome-panel gnome-power-manager gnome-screensaver
  gnome-session gnome-session-bin gnome-settings-daemon gnome-sudoku
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-user-share
  gnome-utils gnomine gstreamer0.10-gnonlin gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gtk2-engines gtk2-engines-murrine
  gtk2-engines-pixbuf gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse hpijs
  hplip hplip-data ibus ibus-gtk ibus-m17n imagemagick indicator-applet
  indicator-applet-session indicator-application indicator-me
  indicator-messages indicator-session indicator-sound libarchive1
  libatspi1.0-0 libavahi-ui0 libbind9-60 libcairo2 libcamel1.2-14
  libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcryptui0 libcups2
  libdbusmenu-gtk1 libdrm-nouveau1 libebackend1.2-0 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedataserverui1.2-8 libegroupwise1.2-13 libgail-common
  libgail18 libgcc1 libgcr0 libgdict-1.0-6 libgdu-gtk0 libgksu2-0
  libgnome-desktop-2-17 libgnome-media0 libgnome-window-settings1
  libgnomecanvas2-0 libgnomekbd4 libgnomeui-0 libgomp1 libgpod-common libgpod4
  libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-0 libgtk2.0-bin
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19
  libgtksourceview2.0-0 libgucharmap7 libgweather1 libhpmud0 libido-0.1-0
  libindicate-gtk2 libisc60 libisccfg60 liblaunchpad-integration1.0-cil
  liblwres60 libmetacity-private0 libmono-cairo2.0-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-runtime2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil
  libnautilus-extension1 libnice0 libpanel-applet2-0 libpango1.0-0
  libplymouth2 libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0
  libpulse0 librsvg2-2 librsvg2-common libstdc++6 libubuntuone-1.0-1 libvte9
  libwebkit-1.0-2 libwmf0.2-7 libwmf0.2-7-gtk libwnck22 light-themes
  linux-headers-generic metacity mono-2.0-gac mono-gac mono-runtime
  mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy
  network-manager-gnome network-manager-pptp-gnome obex-data-server onboard
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-math openoffice.org-writer openprinting-ppds plymouth
  plymouth-label plymouth-x11 pm-utils policykit-1-gnome poppler-utils
  protobuf-compiler pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-appindicator python-apt python-aptdaemon
  python-aptdaemon-gtk python-glade2 python-gnomeapplet python-gobject
  python-gtk2 python-gtkspell python-ibus python-indicate python-louis
  python-mako python-pyatspi python-pygoocanvas python-ubuntuone
  python-ubuntuone-client python-uno python-virtkey python-vte python-webkit
  python-wnck quadrapassel rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins seahorse simple-scan software-center splix synaptic
  syslinux telepathy-gabble telepathy-mission-control-5 tomboy totem
  totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk tsclient ubufox ubuntu-desktop ubuntuone-client
  ubuntuone-client-gnome update-notifier update-notifier-common upower vinagre
  vino xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xulrunner-1.9.2
  zenity
The following packages will be upgraded:
  acpi-support acpid adium-theme-ubuntu alacarte alsa-base alsa-utils anacron
  app-install-data app-install-data-partner apparmor apparmor-utils apport
  apport-gtk apt-xapian-index apturl apturl-common aspell at avahi-autoipd
  avahi-utils b43-fwcutter bash bash-completion bcmwl-kernel-source
  bcmwl-modaliases binutils bluez bluez-alsa bluez-cups bluez-gstreamer
  bogofilter bogofilter-bdb bogofilter-common bsdmainutils bsdutils
  busybox-initramfs busybox-static byobu checkbox checkbox-gtk cli-common
  command-not-found command-not-found-data compizconfig-backend-gconf
  consolekit coreutils couchdb-bin cpio cryptsetup cups-bsd cups-client
  cups-common cups-driver-gutenprint dash dbus dbus-x11 dcraw defoma
  desktop-file-utils desktopcouch dhcp3-client dhcp3-common
  dictionaries-common diffutils dkms dmsetup dnsmasq-base dosfstools
  erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key
  erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl
  esound-clients esound-common espeak espeak-data example-content fancontrol
  fglrx-modaliases finger foo2zjs foomatic-db foomatic-db-engine
  foomatic-filters ftp fuse-utils gcalctool gconf-defaults-service
  gconf-editor gconf2 gconf2-common gdb gdm-guest-session gedit-common
  genisoimage geoip-database gettext-base ghostscript ghostscript-cups
  ghostscript-x gnome-about gnome-accessibility-themes gnome-applets-data
  gnome-codec-install gnome-desktop-data gnome-doc-utils gnome-icon-theme
  gnome-menus gnome-orca gnome-panel-data gnome-session-canberra
  gnome-system-monitor gnome-themes-selected gnupg gnupg-curl gpgv groff-base
  grub-common grub-pc gsfonts gstreamer0.10-alsa gstreamer0.10-nice
  gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x guile-1.8-libs gwibber gwibber-service hdparm
  humanity-icon-theme hunspell-en-ca ibus-table ifupdown im-switch
  initramfs-tools initramfs-tools-bin inputattach iproute iptables
  iputils-arping iputils-ping iputils-tracepath irqbalance iso-codes
  jockey-common jockey-gtk kerneloops-daemon keyutils klibc-utils
  language-selector language-selector-common launchpad-integration lftp
  libacl1 libanthy0 libapparmor-perl libapparmor1 libart-2.0-2 libasound2
  libaspell15 libatasmart4 libatk1.0-0 libatk1.0-data libattr1
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1
  libavahi-gobject0 libblkid1 libbluetooth3 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libbrlapi0.5 libcaca0 libcairo-perl
  libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse
  libcanberra0 libcap-ng0 libcap2 libck-connector0 libcolamd2.7.1 libcomerr2
  libcouchdb-glib-1.0-2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1
  libcupsppdc1 libcurl3 libcurl3-gnutls libcwidget3 libdatrie1 libdb4.8
  libdbus-glib-1-2 libdbusmenu-glib1 libdecoration0 libdesktopcouch-glib-1.0-2
  libdevkit-power-gobject1 libdevmapper1.02.1 libdjvulibre-text libdjvulibre21
  libdrm-intel1 libdrm-radeon1 libdrm2 libelf1 libenchant1c2a libesd0
  libespeak1 libffi5 libflac8 libfontenc1 libfreetype6 libfreezethaw-perl
  libfuse2 libgail-gnome-module libgc1c2 libgconf2-4 libgcrypt11 libgd2-xpm
  libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgdu0
  libgeoip1 libgl1-mesa-dri libgl1-mesa-glx libglade2.0-cil libglib-perl
  libglib2.0-0 libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa
  libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome2-0 libgnome2-common
  libgnomecanvas2-common libgnomekbd-common libgnomepanel2.24-cil
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra
  libgnutls26 libgoocanvas-common libgoocanvas3 libgp11-0 libgpm2 libgs8
  libgsf-1-114 libgsf-1-common libgsl0ldbl libgssapi-krb5-2 libgssdp-1.0-2
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2.0-cil
  libgtk2.0-common libgtkmm-2.4-1c2a libgtksourceview2.0-common libgtop2-7
  libgtop2-common libgudev-1.0-0 libgupnp-1.0-3 libgutenprint2 libgvfscommon0
  libgweather-common libhtml-parser-perl libhtml-tree-perl libhunspell-1.2-0
  libhyphen0 libidl0 libidn11 libindicate4 libisccc60 libjpeg62 libjs-jquery
  libjson-glib-1.0-0 libk5crypto3 libkeyutils1 libklibc libkpathsea5 libkrb5-3
  libkrb5support0 liblaunchpad-integration1 liblcms1 libldap-2.4-2
  liblircclient0 liblockfile1 liblouis-data liblpint-bonobo0 libmailtools-perl
  libmldbm-perl libmtp8 libncurses5 libncursesw5 libneon27-gnutls
  libnet-dbus-perl libnewt0.52 libnm-glib2 libnm-util1 libnotify1 libnspr4-0d
  libnss3-1d libogg0 libpam-ck-connector libpam-gnome-keyring libpam-runtime
  libpango1.0-common libpangomm-1.4-1 libpaper-utils libpaper1
  libparted0debian1 libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1
  libperl5.10 libpisock9 libpisync1 libpixman-1-0 libplist1 libpng12-0
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpopt0
  libpth20 libpurple-bin libpurple0 libpython2.6 libraptor1 librarian0
  librasqal2 libraw1394-11 librdf0 libreadline6 librpc-xml-perl libsane
  libsasl2-2 libsasl2-modules libsdl1.2debian libsdl1.2debian-pulseaudio
  libsensors4 libsgutils2-2 libslang2 libslp1 libsmbclient libsnmp-base
  libsnmp15 libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2
  libsqlite3-0 libssl0.9.8 libsysfs2 libtag1-vanilla libtag1c2a libtasn1-3
  libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libthai-data libthai0
  libtiff4 libtimedate-perl libtotem-plparser17 libunique-1.0-0
  libupower-glib1 liburi-perl libusb-0.1-4 libusb-1.0-0 libusbmuxd1
  libuuid-perl libuuid1 libvisual-0.4-0 libvorbis0a libvorbisenc2
  libvorbisfile3 libvte-common libwbclient0 libwebkit-1.0-common
  libwnck-common libwrap0 libwww-perl libxapian15 libxcb-render0
  libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxfont1 libxft2
  libxi6 libxinerama1 libxklavier16 libxml-twig-perl libxml2 libxml2-utils
  libxrender1 libxslt1.1 libxtst6 linux-firmware linux-generic
  linux-image-generic linux-libc-dev linux-sound-base lm-sensors
  lockfile-progs logrotate ltrace make man-db manpages manpages-dev
  media-player-info memtest86+ metacity-common mime-support min12xxw
  mobile-broadband-provider-info modemmanager module-init-tools mountall
  mscompress mtools myspell-en-gb myspell-en-za nano nautilus-share
  ncurses-bin net-tools network-manager network-manager-pptp notify-osd
  ntpdate nvidia-173-modaliases nvidia-96-modaliases nvidia-common
  nvidia-current-modaliases obexd-client openoffice.org-style-human
  openssh-client openssl os-prober parted pciutils perl perl-base perl-modules
  pitivi pkg-config plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
  policykit-1 policykit-desktop-privileges ppp pptp-linux procps psfontmgr
  psmisc python python-apport python-avahi python-brlapi python-central
  python-configglue python-cups python-cupshelpers python-debian
  python-desktopcouch python-desktopcouch-records python-egenix-mxdatetime
  python-egenix-mxtools python-farsight python-gconf python-gdbm python-gmenu
  python-gnome2 python-gnomecanvas python-gnomekeyring python-gst0.10
  python-gtksourceview2 python-httplib2 python-imaging
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-libxml2 python-minimal python-newt python-papyon
  python-pkg-resources python-problem-report python-protobuf python-pyinotify
  python-simplejson python-smbc python-software-properties python-speechd
  python-support python-twisted-bin python-twisted-core python-twisted-names
  python-twisted-web python-ubuntuone-storageprotocol python-wadllib
  python-xapian python-xdg python-zope.interface python2.6 python2.6-minimal
  radeontool rarian-compat rdesktop readline-common
  rhythmbox-ubuntuone-music-store rsync rtkit samba-common samba-common-bin
  sane-utils screen screen-resolution-extra sed shared-mime-info smbclient
  software-properties-gtk speech-dispatcher ssh-askpass-gnome ssl-cert strace
  sudo system-config-printer-common system-config-printer-gnome
  system-config-printer-udev system-tools-backends tar tasksel tasksel-data
  tcpd tcpdump telepathy-butterfly telepathy-haze telepathy-salut time
  ttf-dejavu-core ttf-freefont ttf-indic-fonts-core ttf-opensymbol
  ttf-punjabi-fonts ttf-thai-tlwg ttf-unfonts-core tzdata ubuntu-artwork
  ubuntu-keyring ubuntu-minimal ubuntu-mono ubuntu-standard ubuntu-wallpapers
  udev udisks ufw unattended-upgrades unzip update-inetd update-manager
  update-manager-core ureadahead usb-creator-common usb-creator-gtk usbmuxd
  usbutils util-linux uuid-runtime vim-common vim-tiny w3m wget whiptail whois
  wodim wpasupplicant x11-apps x11-utils x11-xserver-utils xdg-user-dirs
  xdg-utils xinit xinput xorg xserver-xorg-input-all xserver-xorg-video-all
  xsltproc yelp zip zlib1g
616 upgraded, 0 newly installed, 0 to remove and 323 not upgraded.
Need to get 628kB/231MB of archives.
After this operation, 155MB disk space will be freed.
Do you want to continue [Y/n]? 



should i hit y then enter it?

---

### Post by DaMonsterMonster on 2011-05-08
> **cipherboy_loc said:**
> Try:

```

sudo apt-get update 
sudo do-dist-upgrade
sudo apt-get upgrade

```and post back (in CODE tags) the results of each.


Cipherboy
also, the power button on the top right is red.....and the battery icon has disapeered(im on a laptop)

---

### Post by cipherboy_loc on 2011-05-08
Try sudo do-dist-update. I am currently on Gentoo so I cannot post the correct command. And no, the apt-get upgrade command won't work (to upgrade to 11.04), as the apt-get update reports that you still have the maverick lists. You should run the apt-get upgrade though, first, before updating. Is this a fresh install (it seems like a lot of updates)? 


Cipherboy

---

### Post by mörgæs on 2011-05-08
> **DaMonsterMonster said:**
> the power button on the top right is red

Yes, what does that tell you (when investigating the button further)?

---

### Post by DaMonsterMonster on 2011-05-08
> **cipherboy_loc said:**
> Try sudo do-dist-update. I am currently on Gentoo so I cannot post the correct command. And no, the apt-get upgrade command won't work (to upgrade to 11.04), as the apt-get update reports that you still have the maverick lists. You should run the apt-get upgrade though, first, before updating. Is this a fresh install (it seems like a lot of updates)? 


Cipherboy
nope straight from 10.10..

---

### Post by DaMonsterMonster on 2011-05-08
> **mörgæs said:**
> Yes, what does that tell you (when investigating the button further)?
what do you mean?

---

### Post by DaMonsterMonster on 2011-05-08
> **cipherboy_loc said:**
> Try sudo do-dist-update. I am currently on Gentoo so I cannot post the correct command. And no, the apt-get upgrade command won't work (to upgrade to 11.04), as the apt-get update reports that you still have the maverick lists. You should run the apt-get upgrade though, first, before updating. Is this a fresh install (it seems like a lot of updates)? 


Cipherboy
byron@byron-laptop:~$ sudo do-dist-update
sudo: do-dist-update: command not found
byron@byron-laptop:~$

---

### Post by DaMonsterMonster on 2011-05-08
> **cipherboy_loc said:**
> Try sudo do-dist-update. I am currently on Gentoo so I cannot post the correct command. And no, the apt-get upgrade command won't work (to upgrade to 11.04), as the apt-get update reports that you still have the maverick lists. You should run the apt-get upgrade though, first, before updating. Is this a fresh install (it seems like a lot of updates)? 


Cipherboy
byron@byron-laptop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
byron@byron-laptop:~$

---

### Post by DaMonsterMonster on 2011-05-08
bump

---

### Post by DaMonsterMonster on 2011-05-08
hey cipher could you troubleshoot it if u did vnc with me?

---

### Post by N4S1 on 2011-05-08
this is what worked for me while trying to install b43 drivers, 
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

correct me if i'm wrong but i think :pthats what worked for me when i had broken packages

---

### Post by DaMonsterMonster on 2011-05-08
> **cipherboy_loc said:**
> Try sudo do-dist-update. I am currently on Gentoo so I cannot post the correct command. And no, the apt-get upgrade command won't work (to upgrade to 11.04), as the apt-get update reports that you still have the maverick lists. You should run the apt-get upgrade though, first, before updating. Is this a fresh install (it seems like a lot of updates)? 


Cipherboy
i decided to hit y then enter...and it seems to be updating...ill post what happens when its done

---

### Post by DaMonsterMonster on 2011-05-08
Setting up libsgutils2-2 (1.29-1) ...

Setting up libglib2.0-data (2.26.1-0ubuntu1) ...
Setting up libgnome-mag2 (1:0.16.1-2ubuntu1) ...

Setting up libgnomecanvas2-common (2.30.2-0ubuntu1) ...
Setting up libgnomekbd-common (2.32.0-0ubuntu1) ...
Setting up libgnomeui-common (2.24.4-0ubuntu1) ...
Setting up libwbclient0 (2:3.5.4~dfsg-1ubuntu8.4) ...

Setting up libsmbclient (2:3.5.4~dfsg-1ubuntu8.4) ...

Setting up libgnomevfs2-extra (1:2.24.3-1ubuntu1) ...
Setting up libgoocanvas-common (0.15-1) ...
Setting up libgoocanvas3 (0.15-1) ...

Setting up libgp11-0 (2.92.92.is.2.31.91-0ubuntu4.1) ...

Setting up libgsf-1-common (1.14.18-1ubuntu1) ...
Setting up libgsf-1-114 (1.14.18-1ubuntu1) ...

Setting up libgssdp-1.0-2 (0.7.2-2build1) ...

Setting up libgtk2.0-common (2.22.0-0ubuntu1) ...
Setting up libgtksourceview2.0-common (2.10.5-0ubuntu1) ...
Setting up libgupnp-1.0-3 (0.13.4-1build1) ...

Setting up libgvfscommon0 (1.6.4-0ubuntu1.1) ...

Setting up libhyphen0 (2.5-1ubuntu1) ...

Setting up libidl0 (0.8.14-0.1) ...

Setting up libindicate4 (0.4.4-0ubuntu2) ...

Setting up libisccc60 (1:9.7.1.dfsg.P2-2ubuntu0.2) ...

Setting up libkpathsea5 (2009-7) ...

Setting up liblpint-bonobo0 (0.1.38) ...

Setting up libneon27-gnutls (0.29.3-2) ...

Setting up libnspr4-0d (4.8.6-0ubuntu1) ...

Setting up libnss3-1d (3.12.9+ckbi-1.82-0ubuntu0.10.10.1) ...

Setting up libnm-util1 (0.8.1+git.20100810t184654.ab580f4-0ubuntu2) ...

Setting up libnm-glib2 (0.8.1+git.20100810t184654.ab580f4-0ubuntu2) ...

Setting up libnotify1 (0.5.0-2ubuntu1) ...

Setting up libpam-ck-connector (0.4.1-4ubuntu1) ...

Setting up libpam-gnome-keyring (2.92.92.is.2.31.91-0ubuntu4.1) ...

Setting up libpaper-utils (1.1.24) ...
Setting up libpcsclite1 (1.5.5-3ubuntu2.1) ...

Setting up libpisync1 (0.12.5-2ubuntu1) ...

Setting up libplist1 (1.3-1) ...

Setting up libpolkit-agent-1-0 (0.96-2ubuntu1.1) ...

Setting up libpth20 (2.0.7-16) ...

Setting up libpurple-bin (1:2.7.3-1ubuntu3.2) ...
Setting up libraptor1 (1.4.21-2) ...

Setting up librasqal2 (0.9.19-1) ...

Setting up libraw1394-11 (2.0.5-2ubuntu1) ...

Setting up librdf0 (1.0.10-2) ...

Setting up libsane (1.0.21-2ubuntu2) ...
Installing new version of config file /etc/sane.d/canon_dr.conf ...
Installing new version of config file /etc/sane.d/cardscan.conf ...
Installing new version of config file /etc/sane.d/epjitsu.conf ...
Installing new version of config file /etc/sane.d/fujitsu.conf ...
Installing new version of config file /etc/sane.d/genesys.conf ...
Installing new version of config file /etc/sane.d/gt68xx.conf ...
Installing new version of config file /etc/sane.d/xerox_mfp.conf ...
Installing new version of config file /etc/sane.d/dll.conf ...

Setting up libsdl1.2debian-pulseaudio (1.2.14-6ubuntu3) ...

Setting up libsdl1.2debian (1.2.14-6ubuntu3) ...
Setting up libsensors4 (1:3.1.2-6) ...

Setting up libslp1 (1.2.1-7.7ubuntu0.1) ...

Setting up libsnmp-base (5.4.3~dfsg-1ubuntu3) ...
Setting up libwrap0 (7.6.q-19) ...

Setting up libsnmp15 (5.4.3~dfsg-1ubuntu3) ...

Setting up libspectre1 (0.2.6-1) ...

Setting up libtag1-vanilla (1.6.3-1) ...

Setting up libtag1c2a (1.6.3-1) ...
Setting up libtelepathy-glib0 (0.12.0-0ubuntu1) ...

Setting up libtelepathy-farsight0 (0.0.14-2) ...

Setting up libthai-data (0.1.14-2) ...
Setting up libthai0 (0.1.14-2) ...

Setting up libtotem-plparser17 (2.30.3-0ubuntu1) ...

Setting up libunique-1.0-0 (1.1.6-1ubuntu3) ...

Setting up libupower-glib1 (0.9.5-4) ...

Setting up libusb-1.0-0 (2:1.0.8-2) ...

Setting up libusbmuxd1 (1.0.4-1) ...

Setting up libuuid-perl (0.02-4) ...
Setting up libvisual-0.4-0 (0.4.0-3) ...

Setting up libvorbisenc2 (1.3.1-1) ...

Setting up libvte-common (1:0.26.0-0ubuntu2) ...
Setting up libwebkit-1.0-common (1.2.5-0ubuntu0.10.10.1) ...
Setting up libwnck-common (1:2.30.5-0ubuntu1) ...
Setting up libxcomposite1 (1:0.4.2-1) ...

Setting up libxfont1 (1:1.4.2-1) ...

Setting up libxklavier16 (5.0-2) ...

Setting up linux-firmware (1.38.6) ...
Setting up linux-image-generic (2.6.35.28.36) ...
Setting up linux-generic (2.6.35.28.36) ...
Setting up manpages-dev (3.24-1ubuntu1) ...
Setting up metacity-common (1:2.30.2-0ubuntu1) ...

Setting up min12xxw (0.0.9-3ubuntu3) ...
Setting up modemmanager (0.4+git.20100809t153145.be28089-0ubuntu1) ...
Installing new version of config file /etc/dbus-1/system.d/org.freedesktop.ModemManager.conf ...
Setting up mtools (4.0.12-1) ...
Setting up myspell-en-gb (1:3.2.1-2ubuntu1) ...

Setting up myspell-en-za (1:3.2.1-2ubuntu1) ...

Setting up samba-common (2:3.5.4~dfsg-1ubuntu8.4) ...
Replacing config file /etc/samba/smb.conf with new version

Setting up smbclient (2:3.5.4~dfsg-1ubuntu8.4) ...
Setting up samba-common-bin (2:3.5.4~dfsg-1ubuntu8.4) ...

Setting up nautilus-share (0.7.2-13.1) ...
Setting up wpasupplicant (0.6.10-2) ...
Installing new version of config file /etc/wpa_supplicant/action_wpa.sh ...
Installing new version of config file /etc/wpa_supplicant/functions.sh ...

Setting up network-manager (0.8.1+git.20100810t184654.ab580f4-0ubuntu2) ...
Installing new version of config file /etc/dbus-1/system.d/NetworkManager.conf ...

Setting up pptp-linux (1.7.2-5) ...
Setting up network-manager-pptp (0.8.1+git.20100810t192516.1e6db5a-0ubuntu1) ...
runlevel:/var/run/utmp: No such file or directory

Setting up notify-osd (0.9.29-0ubuntu3) ...

Setting up nvidia-173-modaliases (173.14.28-0ubuntu1) ...
Setting up nvidia-96-modaliases (96.43.19-0ubuntu1) ...
Setting up nvidia-current-modaliases (260.19.06-0ubuntu1) ...
Setting up nvidia-common (0.2.24) ...

Setting up obexd-client (0.32-0ubuntu1) ...
Setting up openoffice.org-style-human (1:3.2.1-7ubuntu1.1) ...
Setting up openssl (0.9.8o-1ubuntu4.4) ...

Setting up os-prober (1.39) ...
Setting up python-launchpad-integration (0.1.38) ...

Setting up plymouth-theme-ubuntu-logo (0.8.2-2ubuntu5.1) ...
update-initramfs: deferring update (trigger activated)

Setting up policykit-desktop-privileges (0.2) ...
Setting up python-configglue (0.9pre1-0ubuntu1) ...

Setting up python-cups (1.9.51-0ubuntu2) ...

Setting up python-cupshelpers (1.2.3+20100723-0ubuntu8.2) ...

Setting up python-gtksourceview2 (2.10.1-1) ...

Setting up python-pyinotify (0.8.9-1ubuntu3) ...

Setting up python-smbc (1.0.8-0ubuntu1) ...

Setting up python-protobuf (2.3.0-2ubuntu1) ...

Setting up libpciaccess0 (0.12.0-1) ...

Setting up radeontool (1.6.1-1) ...
Setting up librarian0 (0.8.1-4.1) ...

Setting up yelp (2.30.1-0ubuntu1) ...

Setting up rarian-compat (0.8.1-4.1) ...

Setting up rdesktop (1.6.0-3ubuntu2) ...
Setting up rtkit (0.8-0ubuntu1) ...
runlevel:/var/run/utmp: No such file or directory

Setting up screen-resolution-extra (0.14) ...

Setting up ssh-askpass-gnome (1:5.5p1-4ubuntu5) ...

Setting up ssl-cert (1.0.26) ...

Setting up system-config-printer-common (1.2.3+20100723-0ubuntu8.2) ...

Setting up system-config-printer-gnome (1.2.3+20100723-0ubuntu8.2) ...

Setting up system-config-printer-udev (1.2.3+20100723-0ubuntu8.2) ...
Setting up tcpd (7.6.q-19) ...
Setting up telepathy-salut (0.3.12-1) ...
Setting up ttf-freefont (20090104-7) ...
Setting up ttf-indic-fonts-core (1:0.5.10ubuntu1) ...
Installing new version of config file /etc/fonts/conf.avail/90-ttf-bengali-fonts.conf ...
Installing new version of config file /etc/fonts/conf.avail/90-ttf-devanagari-fonts.conf ...
Installing new version of config file /etc/fonts/conf.avail/90-ttf-gujarati-fonts.conf ...
Installing new version of config file /etc/fonts/conf.avail/90-ttf-kannada-fonts.conf ...
Installing new version of config file /etc/fonts/conf.avail/90-ttf-oriya-fonts.conf ...
Installing new version of config file /etc/fonts/conf.avail/90-ttf-tamil-fonts.conf ...
Installing new version of config file /etc/fonts/conf.avail/90-ttf-telugu-fonts.conf ...
Setting up ttf-opensymbol (1:3.2.1-7ubuntu1.1) ...
Setting up ttf-punjabi-fonts (1:0.5.10ubuntu1) ...
Installing new version of config file /etc/fonts/conf.avail/90-ttf-punjabi-fonts.conf ...
Setting up ttf-thai-tlwg (1:0.4.14-1) ...
Setting up ubuntu-wallpapers (0.31.6) ...
Setting up adium-theme-ubuntu (0.3-0ubuntu1) ...

Setting up ubuntu-artwork (53.8) ...
Setting up ubuntu-mono (0.0.22) ...

Setting up unzip (6.0-4) ...

Setting up usbmuxd (1.0.4-1) ...

Setting up whois (5.0.7ubuntu1) ...
Setting up wodim (9:1.1.10-1ubuntu3) ...

Setting up xdg-user-dirs (0.12-1ubuntu1) ...
Setting up xdg-utils (1.0.2+cvs20100307-1ubuntu0.3) ...
Setting up xinit (1.2.0-2) ...
Installing new version of config file /etc/X11/xinit/xinitrc ...
Setting up xinput (1.5.2-1) ...
Setting up libglu1-mesa (7.9~git20100924-0ubuntu2) ...

Setting up xorg (1:7.5+6ubuntu3) ...
Setting up xserver-xorg-input-all (1:7.5+6ubuntu3) ...
Setting up xserver-xorg-video-all (1:7.5+6ubuntu3) ...
Setting up zip (3.0-3) ...
Setting up compizconfig-backend-gconf (0.8.4-1ubuntu5) ...
Setting up dcraw (8.99-1) ...
Setting up fancontrol (1:3.1.2-6) ...
Installing new version of config file /etc/init.d/fancontrol ...
runlevel:/var/run/utmp: No such file or directory
 * Stopping fan speed regulator fancontrol                               [ OK ] 

Setting up fglrx-modaliases (2:8.780-0ubuntu2) ...
Setting up foomatic-db (20100915-0ubuntu4) ...

Setting up inputattach (20051019-12) ...
Setting up libgweather-common (2.30.3-0ubuntu1) ...
Setting up liblircclient0 (0.8.7~pre3-0ubuntu1) ...

Setting up liblouis-data (2.0.0-1ubuntu1) ...
Setting up mobile-broadband-provider-info (20100910-1) ...
Setting up rhythmbox-ubuntuone-music-store (0.1.9-0ubuntu1) ...

Processing triggers for python-central ...
Setting up language-selector (0.6.8) ...

Setting up ubuntu-standard (1.207) ...
Setting up update-manager (1:0.142.23) ...

Setting up python-wadllib (1.1.4-2) ...

Setting up python-lazr.restfulclient (0.9.20-0ubuntu1) ...

Setting up apt-xapian-index (0.39ubuntu1) ...
Installing new version of config file /etc/cron.weekly/apt-xapian-index ...
apt-xapian-index: Building new index in background...

Setting up software-properties-gtk (0.76.7) ...

Setting up byobu (3.5-0ubuntu1) ...
Installing new version of config file /etc/byobu/statusrc ...

Setting up python-twisted-core (10.1.0-2) ...

Setting up desktopcouch (0.6.9b-0ubuntu1) ...
Installing new version of config file /etc/xdg/desktop-couch/compulsory-auth.ini ...

Setting up gnome-codec-install (0.4.7ubuntu2) ...

Setting up gnome-orca (2.32.0-0ubuntu1) ...

Setting up python-egenix-mxdatetime (3.1.3-4) ...

Setting up jockey-gtk (0.5.10-0ubuntu5.2) ...
Setting up pitivi (0.13.5-1ubuntu3) ...

Setting up python-farsight (0.0.21-1ubuntu1) ...
Setting up python-papyon (0.5.1-0ubuntu2) ...

Setting up python-twisted-names (10.1.0-1) ...

Setting up python-twisted-web (10.1.0-1) ...

Setting up python-ubuntuone-storageprotocol (1.4.0-0ubuntu1) ...

Setting up telepathy-butterfly (0.5.14-1) ...

Processing triggers for python-central ...
Setting up python-launchpadlib (1.6.1-1) ...

Setting up python-apport (1.14.1-0ubuntu8.1) ...
Installing new version of config file /etc/apport/crashdb.conf ...

Setting up apturl (0.4.1ubuntu7) ...

Setting up gwibber-service (2.32.2-0ubuntu2) ...

Setting up python-desktopcouch (0.6.9b-0ubuntu1) ...

Setting up python-desktopcouch-records (0.6.9b-0ubuntu1) ...

Processing triggers for python-central ...
Setting up apport (1.14.1-0ubuntu8.1) ...
Installing new version of config file /etc/bash_completion.d/apport_completion ...
start: Job failed to start

Setting up gwibber (2.32.2-0ubuntu2) ...
Installing new version of config file /etc/xdg/autostart/gwibber.desktop ...

Processing triggers for python-central ...
Setting up apport-gtk (1.14.1-0ubuntu8.1) ...
Setting up tasksel-data (2.81ubuntu1) ...
Setting up perl-modules (5.10.1-12ubuntu2.1) ...
Setting up udev (162-2.2) ...
Installing new version of config file /etc/init/udevtrigger.conf ...
udev start/running, process 16993
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)

Setting up alsa-utils (1.0.23-2ubuntu3.4) ...

Setting up update-inetd (4.36ubuntu0.1) ...

Setting up cups-bsd (1.4.4-6ubuntu2.3) ...

Setting up mountall (2.19) ...
Installing new version of config file /etc/init/mountall.conf ...
Installing new version of config file /etc/init/mounted-varrun.conf ...
Setting up alsa-base (1.0.23+dfsg-1ubuntu4) ...
Installing new version of config file /etc/modprobe.d/alsa-base.conf ...

Setting up checkbox (0.10.3) ...

Setting up cli-common (0.7.1) ...
Setting up udisks (1.0.1+git20100614-3) ...

Setting up libgdu0 (2.30.1-2) ...

Setting up libglib2.0-cil (2.12.10-1) ...
* Installing 1 assembly from libglib2.0-cil into Mono

Setting up libgtk2.0-cil (2.12.10-1) ...
* Installing 5 assemblies from libgtk2.0-cil into Mono

Setting up libglade2.0-cil (2.12.10-1) ...
* Installing 1 assembly from libglade2.0-cil into Mono

Setting up libgnomepanel2.24-cil (2.26.0-3) ...
* Installing 1 assembly from libgnomepanel2.24-cil into Mono

Setting up media-player-info (12-1~maverick1) ...
Setting up sane-utils (1.0.21-2ubuntu2) ...
Installing new version of config file /etc/init.d/saned ...
runlevel:/var/run/utmp: No such file or directory
saned disabled; edit /etc/default/saned

Setting up tasksel (2.81ubuntu1) ...

Setting up usb-creator-common (0.2.25.3) ...

Setting up usb-creator-gtk (0.2.25.3) ...

Setting up perl (5.10.1-12ubuntu2.1) ...

Setting up foomatic-filters (4.0.5-0ubuntu3) ...

Setting up foomatic-db-engine (4.0.5-0ubuntu6) ...

Setting up initramfs-tools (0.98.1ubuntu6) ...
Installing new version of config file /etc/initramfs-tools/update-initramfs.conf ...
Installing new version of config file /etc/initramfs-tools/initramfs.conf ...
update-initramfs: deferring update (trigger activated)

Setting up dmsetup (2:1.02.39-1ubuntu6) ...
update-initramfs: deferring update (trigger activated)

Setting up foo2zjs (20100728-0ubuntu1) ...

Setting up ubuntu-minimal (1.207) ...
Setting up apparmor (2.5.1-0ubuntu0.10.10.4) ...
Installing new version of config file /etc/apparmor.d/abstractions/dbus ...
Installing new version of config file /etc/apparmor.d/abstractions/dbus-session ...
Installing new version of config file /etc/apparmor.d/abstractions/kde ...
runlevel:/var/run/utmp: No such file or directory
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
runlevel:/var/run/utmp: No such file or directory
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]

Setting up liburi-perl (1.54-1) ...
Setting up libhtml-parser-perl (3.65-1) ...
Setting up libhtml-tree-perl (3.23-2) ...
Setting up libwww-perl (5.836-1) ...
Setting up librpc-xml-perl (0.73-1) ...
Setting up libapparmor-perl (2.5.1-0ubuntu0.10.10.4) ...
Setting up apparmor-utils (2.5.1-0ubuntu0.10.10.4) ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libmailtools-perl (2.06-1) ...
Setting up cryptsetup (2:1.1.2-1ubuntu1) ...
update-initramfs: deferring update (trigger activated)

Setting up cups-driver-gutenprint (5.2.6-0ubuntu8) ...
No Gutenprint PPD files to update.
runlevel:/var/run/utmp: No such file or directory
 * Reloading Common Unix Printing System: cupsd                          [fail] 
.....
lpstat: No such file or directory

Setting up defoma (0.11.11ubuntu1) ...

Setting up gstreamer0.10-plugins-base-apps (0.10.30-2) ...
Setting up libcairo-perl (1.070-1ubuntu1) ...
Setting up libfreezethaw-perl (0.5001-1) ...
Setting up libglib-perl (2:1.223-1) ...
Setting up libmldbm-perl (2.04-1) ...
Setting up libxml-twig-perl (1:3.34-1ubuntu1) ...
Setting up libnet-dbus-perl (0.33.6-2) ...
Setting up libpango1.0-common (1.28.2-0ubuntu1.1) ...
W: gs is already removed. It is recommended to run defoma-app purge gs.
Cleaning up font configuration of pango...
Cleaning up category xfont..
W: gs is already removed. It is recommended to run defoma-app purge gs.
Updating font configuration of pango...
Cleaning up category xfont..
Updating category xfont..

Setting up libpurple0 (1:2.7.3-1ubuntu3.2) ...

Setting up psfontmgr (0.11.11ubuntu1) ...
W: gs is already removed. It is recommended to run defoma-app purge gs.
Updating font configuration of psfontmgr...
Cleaning up category postscript..
Cleaning up category xfont..
Cleaning up category type1..
Cleaning up category pspreview..
Updating category pspreview..
Updating category type1..
Updating category xfont..
Updating category postscript..

Setting up system-tools-backends (2.10.1-0ubuntu1) ...
Setting up telepathy-haze (0.4.0-1ubuntu0.1) ...
Setting up ttf-unfonts-core (1.0.3.is.1.0.1-0ubuntu1) ...
W: gs is already removed. It is recommended to run defoma-app purge gs.

Setting up lm-sensors (1:3.1.2-6) ...
Installing new version of config file /etc/init.d/lm-sensors ...

Processing triggers for python-central ...
Setting up checkbox-gtk (0.10.3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Processing triggers for python-central ...
byron@byron-laptop:~$

---

### Post by DaMonsterMonster on 2011-05-08
> **N4S1 said:**
> this is what worked for me while trying to install b43 drivers, 
```
sudo dpkg --configure -a
``````
sudo apt-get update
``````
sudo apt-get upgrade
```correct me if i'm wrong but i think :pthats what worked for me when i had broken packages
byron@byron-laptop:~$ sudo dpkg --configure -a
[sudo] password for byron: 
byron@byron-laptop:~$ sudo dpkg --configure -a
byron@byron-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [9,762B]             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Fetched 73B in 1s (38B/s)
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
byron@byron-laptop:~$ 






byron@byron-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  aisleriot apt apt-transport-https apt-utils aptdaemon aptitude at-spi
  avahi-daemon bind9-host brasero brasero-common brltty brltty-x11
  capplets-data compiz compiz-core compiz-fusion-plugins-main compiz-gnome
  compiz-plugins computer-janitor computer-janitor-gtk cpp cpp-4.4 cron cups
  dnsutils dpkg empathy empathy-common eog evince evolution evolution-common
  evolution-couchdb evolution-data-server evolution-data-server-common
  evolution-exchange evolution-indicator evolution-plugins evolution-webcal
  f-spot file-roller firefox firefox-branding firefox-gnome-support gbrainy
  gcc gcc-4.4 gcc-4.4-base gdebi gdebi-core gdm gedit gksu gnome-applets
  gnome-bluetooth gnome-control-center gnome-disk-utility gnome-games-common
  gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common
  gnome-nettool gnome-panel gnome-power-manager gnome-screensaver
  gnome-session gnome-session-bin gnome-settings-daemon gnome-sudoku
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-user-share
  gnome-utils gnomine gstreamer0.10-gnonlin gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gtk2-engines gtk2-engines-murrine
  gtk2-engines-pixbuf gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse hpijs
  hplip hplip-data ibus ibus-gtk ibus-m17n imagemagick indicator-applet
  indicator-applet-session indicator-application indicator-me
  indicator-messages indicator-session indicator-sound libarchive1
  libatspi1.0-0 libavahi-ui0 libbind9-60 libcairo2 libcamel1.2-14
  libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcryptui0 libcups2
  libdbusmenu-gtk1 libdrm-nouveau1 libebackend1.2-0 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedataserverui1.2-8 libegroupwise1.2-13 libgail-common
  libgail18 libgcc1 libgcr0 libgdict-1.0-6 libgdu-gtk0 libgksu2-0
  libgnome-desktop-2-17 libgnome-media0 libgnome-window-settings1
  libgnomecanvas2-0 libgnomekbd4 libgnomeui-0 libgomp1 libgpod-common libgpod4
  libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-0 libgtk2.0-bin
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19
  libgtksourceview2.0-0 libgucharmap7 libgweather1 libhpmud0 libido-0.1-0
  libindicate-gtk2 libisc60 libisccfg60 liblaunchpad-integration1.0-cil
  liblwres60 libmetacity-private0 libmono-cairo2.0-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-runtime2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil
  libnautilus-extension1 libnice0 libpanel-applet2-0 libpango1.0-0
  libplymouth2 libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0
  libpulse0 librsvg2-2 librsvg2-common libstdc++6 libubuntuone-1.0-1 libvte9
  libwebkit-1.0-2 libwmf0.2-7 libwmf0.2-7-gtk libwnck22 light-themes
  linux-headers-generic metacity mono-2.0-gac mono-gac mono-runtime
  mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy
  network-manager-gnome network-manager-pptp-gnome obex-data-server onboard
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-math openoffice.org-writer openprinting-ppds plymouth
  plymouth-label plymouth-x11 pm-utils policykit-1-gnome poppler-utils
  protobuf-compiler pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-appindicator python-apt python-aptdaemon
  python-aptdaemon-gtk python-glade2 python-gnomeapplet python-gobject
  python-gtk2 python-gtkspell python-ibus python-indicate python-louis
  python-mako python-pyatspi python-pygoocanvas python-ubuntuone
  python-ubuntuone-client python-uno python-virtkey python-vte python-webkit
  python-wnck quadrapassel rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins seahorse simple-scan software-center splix synaptic
  syslinux telepathy-gabble telepathy-mission-control-5 tomboy totem
  totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk tsclient ubufox ubuntu-desktop ubuntuone-client
  ubuntuone-client-gnome update-notifier update-notifier-common upower vinagre
  vino xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xulrunner-1.9.2
  zenity
0 upgraded, 0 newly installed, 0 to remove and 323 not upgraded.
byron@byron-laptop:~$

---

### Post by ASULutzy on 2011-05-20
sudo apt-get dist-upgrade

Can also just try running

update-manager

---

### Post by unc0nn3ct3d on 2011-10-18
I noticed that you were seeing a fair amount of runlevel:/var/run/utmp: No such file or directory error message showing up.  I'm seeing the exact problem right now after a 11.04 upgrade and don't know what to do to fix it, well besides creating that dir which just gets lost after I reboot.

---

