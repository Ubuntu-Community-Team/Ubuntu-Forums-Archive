---
title: "Gutsy to Hardy - Partial Upgrade freezes"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by kmount on 2008-05-12
I tries to upgrade from Gutsy to Hardy and failed when I tried again I got a dialog tghat says "Not all updates can be installed" It asks thay I run a Partial Upgrade but when I try that it stall when reading the cache which forces me to force quit.

---

### Post by dstew on 2008-05-12
Did you do an update on Gutsy before you tried the upgrade to Hardy? And, what is the exact error message you get when you try the Partial Upgrade?

---

### Post by fultona on 2008-05-14
DSTEW:  That's the mistake I made.  

I was using Feisty.  My update manager was regularly giving me patches but never gave me the upgrade option (either upgrade to Gutsy or to Hardy).  I've read great things about Hardy, so I burned ISO CDs of both upgrades (from 7.04 to 7.10, and from 7.10 to 8.04).

But I accidentally put the Hardy CD in first.  The system whirred a bit and said it couldn't do the upgrade, so I immediately removed it -- and then restarted my system and put in the Gutsy CD.

And ever since then:  Partial Upgrade.  When I click OK, it eventually prompts me for the Hardy CD -- and the whole thing fails.  The update manager now shows 462 updates, none of which it can implement.

Is there a way to "clear out" the update manager and start from scratch?

I know it was a pretty stupid mistake, but it was an honest one.

---

### Post by dstew on 2008-05-15
Do you have an internet connection?

---

### Post by fultona on 2008-05-15
> **dstew said:**
> Do you have an internet connection?

Yes, I do.  My Ubuntu software never had trouble using it, and the update manager function worked very well -- except that it never gave me the UPGRADE option from either 7.04 to 7.10, or to 8.04.

What I'm wondering at this point is ... Is there a way that I can just "reset" the update manager so that it stops thinking that I want to go straight from 7.04 to 8.04, and then let me do the upgrade from 7.04 to 7.10 (and then eventually 7.10 to 8.04)? ... 

Or should I just backup any important data and do a clean install to 8.04?

Thanks.

---

### Post by dstew on 2008-05-15
We can try some commands on the command line. I assume you are currently running Fiesty, correct? On the command line (Applications --> Accessories --> Terminal) enter```
sudo apt-get check
```Post the response.

---

### Post by fultona on 2008-05-15
> **dstew said:**
> We can try some commands on the command line. I assume you are currently running Fiesty, correct? On the command line (Applications --> Accessories --> Terminal) enter```
sudo apt-get check
```Post the response.

OK.  Yes, I am using Feisty.

Here are the results that I get:

[COLOR="Green"]
sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[/COLOR]

That's all.  Make sense to you?

(Thanks again.)

---

### Post by fultona on 2008-05-16
DSTEW: See my reply above. Thanks.

---

### Post by dstew on 2008-05-16
Yes, that is good. It means the apt-get system is generally intact. Now, on the command line do:```
sudo apt-get update
sudo apt-get upgrade
```Note, this is not an attempt at a distribution upgrade, these commands only update your current system. Any error messages with these commands?

---

### Post by fultona on 2008-05-16
OK.  I did both commands, and below are the results.

[COLOR="DarkGreen"]**sudo apt-get update**
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Get:4 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release.gpg [189B]
Get:5 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Translation-en_US [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                 
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release [50.9kB]     
Get:7 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release [9434B]             
Hit [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [200kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages [6341B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources [49.0kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources [956B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Fetched 317kB in 2s (151kB/s)
Reading package lists... Done

**sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  acpi-support apt apt-utils aptitude at-spi bind9-host bluez-utils brltty
  brltty-x11 bug-buddy capplets-data cdrdao compiz compiz-core compiz-gnome
  compiz-plugins console-setup contact-lookup-applet cpp cupsys cupsys-bsd
  cupsys-client cupsys-driver-gutenprint dbus deskbar-applet dmsetup dnsutils
  dpkg eject ekiga eog evince evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins
  evolution-webcal f-spot file-roller firefox firefox-gnome-support gcalctool
  gcc gconf-editor gconf2 gconf2-common gdebi gdebi-core gdm gedit
  gedit-common gimp gimp-data gimp-python gksu gnome-app-install gnome-applets
  gnome-applets-data gnome-cards-data gnome-control-center gnome-games
  gnome-games-data gnome-keyring gnome-mag gnome-media gnome-media-common
  gnome-mount gnome-nettool gnome-orca gnome-panel gnome-panel-data
  gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver
  gnome-session gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-utils gnome-volume-manager gnupg grub
  gstreamer0.10-plugins-good gstreamer0.10-x gtk2-engines gtk2-engines-pixbuf
  gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap hal hpijs hplip hplip-data
  human-theme initramfs-tools iproute language-support-en lftp libatspi1.0-0
  libblkid1 libbonoboui2-0 libbonoboui2-common libcairo-perl libcairo2
  libcupsimage2 libcupsys2 libcurl3 libdjvulibre15 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13
  libenchant1c2a libexchange-storage1.2-3 libgail-common libgail-gnome-module
  libgail18 libgc1c2 libgcc1 libgconf2-4 libgimp2.0 libgksu2-0 libglade2-0
  libglade2.0-cil libglib-perl libgnome-desktop-2 libgnome-media0
  libgnome-window-settings1 libgnome2-canvas-perl libgnome2-vfs-perl
  libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1
  libgnomekbd-common libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra
  libgnutls13 libgphoto2-2 libgphoto2-port0 libgpod-common libgtk2-perl
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.14-19
  libgtkspell0 libgucharmap6 libhunspell-1.1-0 libkrb53 liblpint-bonobo0
  libmetacity0 libmono-sqlite2.0-cil libmusicbrainz4c2a libnautilus-burn4
  libnautilus-extension1 libnet-dbus-perl libnotify1 libpam-modules
  libpanel-applet2-0 libpango1.0-0 libperl5.8 librsvg2-2 librsvg2-common
  libsane libsasl2-2 libsasl2-modules libscim8c2a libsdl1.2debian
  libsdl1.2debian-alsa libsexy2 libsmbclient libsndfile1 libstdc++6 libtag1c2a
  libvte-common libvte9 libwmf0.2-7 libwnck-common libwpd8c2a libwps-0.1-1
  libx11-6 libxml-parser-perl libxplc0.3.13 linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  lshw metacity metacity-common nautilus nautilus-cd-burner nautilus-data
  nautilus-sendto netcat network-manager network-manager-gnome
  notification-daemon onboard openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-style-human openoffice.org-writer
  openssh-client perl perl-base perl-modules poppler-utils python python-apt
  python-cairo python-glade2 python-gnome2 python-gnome2-desktop
  python-gnomecanvas python-gobject python-gtk2 python-gtkhtml2
  python-launchpad-integration python-minimal python-notify python-uno
  python-virtkey python-vte python2.5 python2.5-minimal rhythmbox rss-glx
  samba-common scim scim-gtk2-immodule scim-modules-socket smbclient
  sound-juicer ssh-askpass-gnome synaptic system-tools-backends tomboy toshset
  totem totem-mozilla tsclient ttf-opensymbol ubuntu-artwork ubuntu-desktop
  ubuntu-minimal ubuntu-standard udev update-manager update-manager-core
  update-notifier vino wireless-tools wvdial xbase-clients xkb-data xorg xsane
  xsane-common xscreensaver-data xscreensaver-gl xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-imstt xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-newport
  xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xutils yelp zenity
The following packages will be upgraded:
  acpi acpid adduser alacarte alsa-base alsa-utils apmd app-install-data
  app-install-data-commercial apport apport-gtk aspell avahi-autoipd
  avahi-daemon base-files base-passwd bash bc belocs-locales-bin binutils
  binutils-static bluez-cups bsdmainutils bsdutils busybox-initramfs bzip2
  ca-certificates cdparanoia cli-common command-not-found
  command-not-found-data console-terminus console-tools coreutils cpio cron
  cupsys-common dash dc dcraw debconf debconf-i18n debianutils defoma
  desktop-file-utils dhcdbd dhcp3-client dhcp3-common dictionaries-common diff
  discover1 discover1-data dmidecode doc-base docbook-xml dosfstools
  dvd+rw-tools e2fslibs e2fsprogs ed esound-common espeak espeak-data ethtool
  example-content file findutils finger fontconfig fontconfig-config foo2zjs
  foomatic-db foomatic-db-engine foomatic-db-hpijs foomatic-filters
  fortune-mod fortunes-min freeglut3 ftp gamin gdb genisoimage gettext-base
  gnome-about gnome-accessibility-themes gnome-desktop-data gnome-doc-utils
  gnome-icon-theme gnome-menus gnome-mime-data gnome-netstatus-applet
  gnome-themes gnome-user-guide gpgv grep groff-base gsfonts
  gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools guile-1.6-libs gzip
  hdparm hostname hotkey-setup human-icon-theme ifupdown info initscripts
  inputattach installation-report iptables iputils-arping iputils-ping
  iputils-tracepath iso-codes klibc-utils klogd language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector language-selector-common laptop-detect laptop-mode-tools
  launchpad-integration less libaa1 libacl1 libao2 libapm1 libart-2.0-2
  libasound2 libaspell15 libatk1.0-0 libattr1 libaudiofile0 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core5 libavahi-glib1
  libbluetooth2 libbonobo2-0 libbonobo2-common libbz2-1.0 libc6 libc6-i686
  libcaca0 libcap1 libcdparanoia0 libcomerr2 libconsole libcroco3 libcucul0
  libdaemon0 libdatrie0 libdbus-1-3 libdbus-glib-1-2 libdecoration0
  libdiscover1 libdrm2 libdv4 libedit2 libelfg0 libesd-alsa0 libespeak1
  libexif12 libexpat1 libfontconfig1 libfontenc1 libfreetype6 libfribidi0
  libgamin0 libgconf2.0-cil libgcrypt11 libgl1-mesa-dri libgl1-mesa-glx
  libglib2.0-0 libglib2.0-cil libglu1-mesa libgmime-2.0-2 libgmime2.2-cil
  libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome2-0
  libgnome2-common libgnomevfs2-bin libgpg-error0 libgpmg1 libgsf-1-114
  libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtk2.0-common libgtksourceview-common libgtksourceview1.0-0 libgtop2-7
  libgtop2-common libguile-ltdl-1 libgutenprint2 libhal-storage1 libhal1
  libhtml-parser-perl libhtml-tree-perl libice6 libidl0 libidn11 libieee1284-3
  libjpeg62 libklibc libkpathsea4 liblcms1 liblircclient0
  liblocale-gettext-perl libmagic1 libmono-cairo1.0-cil libmono-corlib1.0-cil
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-system-data2.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono0 libmono2.0-cil libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libndesk-dbus1.0-cil libnewt0.52 libnm-glib0 libnm-util0 libnss-mdns libogg0
  liboil0.3 liborbit2 libpam-runtime libpam0g libpango1.0-common libpaper1
  libparted1.7-1 libpcap0.8 libpcre3 libpisock9 libpng12-0 libportaudio0
  libpulse0 libqthreads-12 libraw1394-8 libreadline5 librecode0
  libscrollkeeper0 libselinux1 libsensors3 libsepol1 libshout3
  libsigc++-2.0-0c2a libslang2 libslp1 libsm6 libsnmp-base libsqlite3-0 libss2
  libssl0.9.8 libsysfs2 libtasn1-3 libthai-data libthai0 libtheora0 libtiff4
  liburi-perl libusb-0.1-4 libusplash0 libuuid1 libvisual-0.4-0 libvolume-id0
  libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 libwww-perl libx11-data
  libx86-1 libxau6 libxaw7 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxevie1 libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbfile1 libxml-twig-perl libxml2 libxml2-utils libxmu6 libxmuu1 libxpm4
  libxrandr2 libxrender1 libxres1 libxslt1.1 libxss1 libxt6 libxtrap6 libxtst6
  libxv1 libxxf86dga1 linux-restricted-modules-common linux-sound-base locales
  login lsb-base lsb-release lsof ltrace makedev man-db manpages memtest86+
  mesa-utils mime-support mktemp module-init-tools mono-common mono-gac
  mono-jit mono-runtime mount mtr-tiny myspell-en-gb myspell-en-us
  myspell-en-za nano ncurses-base ncurses-bin ndisgtk ndiswrapper-common
  ndiswrapper-utils-1.9 net-tools netbase ntpdate nvidia-kernel-common
  openoffice.org-hyphenation openoffice.org-thesaurus-en-us openprinting-ppds
  openssl parted passwd pciutils pcmciautils pkg-config popularity-contest
  powermanagement-interface powernowd ppp pppconfig pppoeconf procps psmisc
  python-apport python-central python-dbus python-gconf python-gdbm
  python-gmenu python-gnupginterface python-gst0.10 python-launchpad-bugs
  python-libxml2 python-numeric python-problem-report python-pyorbit
  python-software-properties python-support python-xdg rdesktop readahead
  readline-common reiserfsprogs rsync screen scrollkeeper sed shared-mime-info
  smartdimmer software-properties-gtk ssl-cert startup-tasks strace sudo
  sysklogd system-services sysv-rc sysvutils tangerine-icon-theme tar tasksel
  tasksel-data tcpdump thunderbird-locale-en-gb time ttf-arabeyes
  ttf-arphic-uming ttf-freefont ttf-malayalam-fonts ttf-thai-tlwg tzdata
  ubuntu-docs ubuntu-keyring ucf unattended-upgrades unzip update-inetd
  upstart upstart-compat-sysv upstart-logd usbutils usplash
  usplash-theme-ubuntu util-linux util-linux-locales vbetool vim-common
  vim-tiny wamerican wbritish wget whiptail whois wodim wpasupplicant
  x-ttcidfont-conf x11-common xauth xbitmaps xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-encodings xfonts-utils xinit xml-core xresprobe
  xserver-xorg-video-i810 xsltproc xterm xutils-dev zlib1g
462 upgraded, 0 newly installed, 0 to remove and 334 not upgraded.
Need to get 0B/174MB of archives.
After unpacking 12.3MB of additional disk space will be used.
Do you want to continue [Y/n]? [/COLOR]

AND THEN I typed the "y" and got this:

[COLOR="DarkGreen"]Media change: please insert the disc labeled
 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)'
in the drive '/cdrom/' and press enter
[/COLOR]
NOTE that it asked for the Hardy, not the Gutsy.

AND THEN ...  the CD whirred and whirred for about six minutes and, then, this appeared in the terminal box:

[COLOR="DarkGreen"]Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring libc6 &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Running services and programs that are using NSS need to be restarted,    &#9474;  
 &#9474; otherwise they might not be able to do lookup or authentication any       &#9474;  
 &#9474; more. The installation process is able to restart some services (such as  &#9474;  
 &#9474; ssh or telnetd), but other programs cannot be restarted automatically.    &#9474;  
 &#9474; One such program that needs manual stopping and restart after the glibc   &#9474;  
 &#9474; upgrade by yourself is xdm - because automatic restart might disconnect   &#9474;  
 &#9474; your active X11 sessions.                                                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; This script detected the following installed services which must be       &#9474;  
 &#9474; stopped before the upgrade: gdm                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you want to interrupt the upgrade now and continue later, please       &#9474;  
 &#9474; answer No to the question below.                                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok> [/COLOR]      

 
So then I hit enter and in a little box labeled "Configuring libc6," was asked: [COLOR="DarkGreen"]"Do you want to upgrade glibc now?  Yes/No"[/COLOR[/COLOR]]

And ... a long process started ... the terminal session for which I have attached in a txt file called "fultona_terminal."

Then I restarted the system and ... it gave me a black screen saying that it was stopping or terminating all services and that it "will now restart."  It didn't restart for 10 minutes, so I forced a shutdown and repowered and the same kernel (16?) started, I got the same logon sequence as before, the same desktop, the same BUT no more wireless.

Gosh, if I've messed something up, would it be easier just to do a fresh install?

As always, THANKS!

---

### Post by dstew on 2008-05-16
Wow. You are traveling in territory unfamiliar to me. If it goes bad, you might reboot in Recovery Mode, then try again. That is because Recovery Mode does not start gdm or xdm, so the process may not get blocked.

---

### Post by fultona on 2008-05-16
I'll let you know how this little adventure winds up.

I think I'm just going to do a fresh install.  I've already backed up all of my important data.

Thanks!!!

---

### Post by fultona on 2008-05-16
Fresh install completed.  Very smooth so far.  Even wireless worked immediately.

Thanks for your help so I could try the "upgrade" approach, but I just got in too deep.  THANKS.

---

### Post by kmount on 2008-05-23
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This is what I get when I do the sudo apt-get check

---

### Post by dstew on 2008-05-23
kmount, that error occurs if Synaptic is open and you try to use the command line apt-get. Both processes use the same resources, so when one is active, it "locks" the resources to prevent other processes from accessing it. You just need to be sure only one process is going at any time.

---

### Post by kmount on 2008-05-23
> **dstew said:**
> kmount, that error occurs if Synaptic is open and you try to use the command line apt-get. Both processes use the same resources, so when one is active, it "locks" the resources to prevent other processes from accessing it. You just need to be sure only one process is going at any time.
 Thanks
I am not running Synaptic, infact when I try to open synaptic I get the message: Unable to get exclusive lock
I need to know how to stop any process that may be running in the background

---

### Post by dstew on 2008-05-23
To look at your processes, use the command **Top**. You can kill a process using System --> Administration --> System Monitor, processes tab. If you know the application name, you can use the **killall** command. For example, if firefox was frozen, you could get a terminal with ctrl-atl-F1 and enter```
sudo killall firefox
```That kills firefox and all the processes it may have spawned.

---

