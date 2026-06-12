---
title: "apg-get wants to remove everything :O"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by _jB on 2005-09-17
In my mission to get gnomad to work, I had to install some misc .deb files.
With my luck (and linux knowhow) ofcourse it failed, 

After .deb failed, i tried to find a package with apt-get. Apt-get said that i should **dpkg --configure -a**, so I did, wich returned

> dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 libgnome2-0 depends on libgnome2-common (= 2.10.1-1); however:
  Version of libgnome2-common on system is 2.10.0-0ubuntu1.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-0:
 libglib2.0-0 depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing libglib2.0-0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnome2-0
 libglib2.0-0

Dont know if it has anything to do with it but when i **apt-get upgrade (-f)** it wants to remove "everything" :s

> 0 upgraded, 0 newly installed, **287 to remove** and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 672MB disk space will be freed.
Do you want to continue [Y/n]? n

**[SIZE=3][COLOR=Red]Any good ideas of what to do ?[/COLOR][/SIZE]**

---

### Post by John.Michael.Kane on 2005-09-17
You may have dependency conflicts. you can try to remove the deb files you downloaded. and se if that amends the problems. or make a note of ever program you need by writing it down. do a fresh install. set up your net and use synaptic to get everything your need.

---

### Post by _jB on 2005-09-17
Oki, I'll try removing them .deb's..

Actually I thought of letting apt remove what it wants to and then simply re-install them again. Kind of a wacky way but if it helps it's worth it  ](*,) :)

---

### Post by _jB on 2005-09-17
Removed the .deb's and that helped a bit..
It stille want to remove 287 packs, but also update 87..

> **The following packages will be REMOVED:**
  acroread amule bug-buddy capplets capplets-data contact-lookup-applet d4x dbus-1-utils dbus-glib-1 dbus-qt-1
  desktop-file-utils eog evolution-data-server evolution-webcal file-roller firefox firefox-gnome-support
  foomatic-db-gimp-print foomatic-db-hpijs gaim gamin gcalctool gconf-editor gconf2 gdm gedit gedit-common gftp
  gftp-common gftp-gtk gftp-text gimp gimp-python gksu gnome-about gnome-app-install gnome-applets gnome-applets-data
  gnome-btdownload gnome-control-center gnome-cups-manager gnome-games gnome-gv gnome-keyring gnome-media gnome-menus
  gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes gnome-utils gnome-volume-manager
  gnomemeeting gs-common gs-esp gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-alsa gstreamer0.8-artsd
  gstreamer0.8-audiofile gstreamer0.8-caca gstreamer0.8-cdparanoia gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-esd
  gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-festival gstreamer0.8-ffmpeg gstreamer0.8-flac gstreamer0.8-gnomevfs
  gstreamer0.8-gsm gstreamer0.8-hermes gstreamer0.8-jack gstreamer0.8-jpeg gstreamer0.8-lame gstreamer0.8-mad
  gstreamer0.8-mikmod gstreamer0.8-misc gstreamer0.8-mpeg2dec gstreamer0.8-oss gstreamer0.8-plugin-apps
  gstreamer0.8-plugins gstreamer0.8-sdl gstreamer0.8-sid gstreamer0.8-speex gstreamer0.8-swfdec gstreamer0.8-theora
  gstreamer0.8-tools gstreamer0.8-vorbis gstreamer0.8-x gthumb gtk2-engines-clearlooks gtk2-engines-industrial
  gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.6
  gucharmap hal hal-device-manager hpijs hwdb-client ijsgimpprint irssi-text kappfinder kate kcontrol kdebase kdebase-bin
  kdebase-kio-plugins kdelibs-bin kdelibs4 kdepasswd kdeprint kdesktop kfind khelpcenter kicker kino klipper kmenuedit
  kmix konqueror konqueror-nsplugins konsole kpager kpersonalizer ksmserver ksnapshot ksplash ksynaptics ksysguard ktip
  kwin kynaptic libarts1 libatk1.0-0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libcamel1.2-3 libcroco3 libebook1.2-3
  libecal1.2-2 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-4 libeel2-2 libegroupwise1.2-5
  libgail-common libgail17 libgal2.4-0 libgal2.4-common libgamin0 libgconf2-4 libgconf2.0-cil libgconfmm2.0-1c102
  libgdiplus libgimp2.0 libgksu1.2-0 libgksuui1.0-0 libglade2-0 libglade2.0-cil libglademm2.0-1c102 libglib-perl
  libglib2.0-0 libglib2.0-cil libglib2.0-data libglib2.0-dev libgmime2.1 libgnome-desktop-2 libgnome-keyring0
  libgnome-menu0 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0
  libgnomecanvasmm2.0-1c102 libgnomecups1.0-1 libgnomecupsui1.0-1 libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-common libgsf-1 libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgstreamer0.8-0
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkhtml3.6-18 libgtkmm2.0-1c102
  libgtksourceview1.0-0 libgtkspell0 libgtop2-5 libgucharmap4 libidl0 libkonq4 libmetacity0 libmono0 libnautilus-burn1
  libnautilus-extension1 libopenal0 liborbit2 libpanel-applet2-0 libpango1.0-0 libpango1.0-common librsvg2-2
  librsvg2-common libsoup2.2-7 libswfdec0.3 libvte4 libwnck16 libwvstreams3-base libwxgtk2.5.3 mail-notification metacity
  mono mono-devel mono-gac mono-jit mono-mcs mono-utils mozilla-acroread mozilla-firefox mozilla-firefox-gnome-support
  mozilla-mplayer mozilla-thunderbird mplayer-386 mplayer-fonts nautilus nautilus-cd-burner nautilus-sendto
  openoffice.org-gtk-gnome pkg-config pnm2ppa python-glade2 python-gnome2 python-gst python-gtk2 python-pyorbit
  python2.4-dbus python2.4-glade2 python2.4-gnome2 python2.4-gtk2 python2.4-pyorbit readahead rhythmbox rss-glx
  shared-mime-info sound-juicer ssh-askpass-gnome streamtuner synaptic totem totem-xine tsclient ubuntu-artwork
  update-manager update-notifier vino wvdial xchat xchat-common xsane xscreensaver xscreensaver-gl yelp zenity

**The following packages will be upgraded:**
  apache2-common apache2-mpm-prefork apache2-utils cvs libapr0 libdmx1 libdps1 libfs6 libice-dev libice6 libmysqlclient14
  libmysqlclient14-dev libnet-ssleay-perl libnspr4 libnss3 libruby1.8 libsm-dev libsm6 libx11-6 libx11-dev libxau6 libxaw7
  libxaw8 libxcomposite1 libxdamage1 libxdmcp6 libxext-dev libxext6 libxfixes3 libxi-dev libxi6 libxi6-dbg libxinerama-dev
  libxinerama1 libxinerama1-dbg libxkbfile-dev libxkbfile1 libxkbui1 libxmu-dev libxmu6 libxmuu1 libxp6 libxpm4
  libxrandr-dev libxrandr2 libxss1 libxt-dev libxt6 libxtrap6 libxtst-dev libxtst6 libxv-dev libxv1 libxxf86dga1
  libxxf86misc1 libxxf86vm1 libzlib-ruby1.8 mysql-client mysql-server openssl php4-cli php4-common php4-gd php4-mysql
  php4-pear php4-universe-common x-dev x-window-system-core xbase-clients xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-scalable xlibmesa-dri xlibmesa-gl xlibmesa-gl-dev xlibmesa-glu xlibmesa-glu-dev xlibs xlibs-data xorg-common
  xserver-common xserver-xorg xterm xutils zlib1g zlib1g-dev
87 upgraded, 0 newly installed, 287 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 62,3MB of archives.
After unpacking 672MB disk space will be freed.

 :|

---

### Post by John.Michael.Kane on 2005-09-17
You may have to just do a clean install. try to take note of what deb's caused this problem, and install them..

---

### Post by _jB on 2005-09-17
bummer :s

Some guy told me that the problem was caused because I triede to install debian .deb on ubuntu, so I wount do that anymore  O:)

---

