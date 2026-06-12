---
title: "How to untangle my Dapper-&gt;Edgy-&gt;Feisty mess (via remote ssh only!)??"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by qopit on 2007-05-08
I've recently attempted an upgrade of a perfectly operating Dapper install through Edgy and to Feisty.  It has not gone well...

I used what was supposed to be the official method, which was changing sources.list and doing an update then upgrade.  I see on the main sticky in this forum that this is actually NOT recommended, but it is all I could do remotely anyway (I do this all remotely via SSH on my mother-in-law's pc which is many hours away).

After the initial problems (no X and many package complaints) I've done many desperate successions of "apt-get -f install", "dpkg --configure -a", and eventually trying to go with dist-upgrade (trying combos of apt-get and aptitude for all).  Now I seem (?) close, but am stuck in a weird dependency loop where I can't upgrade or remove things.  I'm reasonably new to Linux and now understand what people talk about with dependency hell!!! :(

Anyway... if anyone could help me untangle this mess it would be greatly appreciated!  At this point I've completely toasted my mother-in-law's pc.

Here is the mess I currently get when I do an 'aptitude dist-upgrade"...

```

russ@Binbuntu:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  gnome-app-install hal-device-manager hwdb-client libvte4 python-id3lib python-parted python2.4-libxslt1 rhythmbox-dbg
  ubuntu-desktop upstart
The following NEW packages will be automatically installed:
  cli-common console-setup console-terminus cpp-4.1 cupsys-common dash espeak espeak-data evolution-common
  evolution-data-server-common feisty-gdm-themes feisty-session-splashes feisty-wallpapers gcc-3.4-base gcc-4.1 gdebi-core
  gnome-cards-data gnome-mount gnome-user-guide gpgv gtkhtml3.14 human-cursors-theme human-icon-theme human-theme lapack3
  libbluetooth2 libbtctl4 libcaca0 libcairo-perl libcairomm-1.0-1 libcamel1.2-10 libcompress-zlib-perl libcucul0 libdb4.4 libdns22
  libebook1.2-9 libecal1.2-7 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libenchant1c2a
  libespeak1 libexchange-storage1.2-3 libfont-afm-perl libg2c0 libgadu3 libgcj-bc libgcj7-0 libgcj7-awt libgd2-xpm libgdiplus libgii1
  libgii1-target-x libgksu2-0 libgl1-mesa-glx libgnome-window-settings1 libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgpod-common
  libgpod1 libgtkhtml3.14-19 libgucharmap6 libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhunspell-1.1-0 libicu36 libiec61883-0 libjaxp1.3-java libjaxp1.3-java-gcj libmailtools-perl libmono-cairo1.0-cil
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono2.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnewt0.52 libnm-glib0 liboobs-1-3 libopenobex1
  libparted1.7-1 libpci2 libpisock9 libpq5 libpulse0 libraw1394-8 libsensors3 libslab0 libstlport5.1 libtie-ixhash-perl
  libtimedate-perl liburi-perl libvisual-0.4-0 libvisual-0.4-plugins libvolume-id0 libvte9 libwps-0.1-1 libwww-perl libxcomposite1
  libxevie1 libxklavier11 libxml-parser-perl libxml-twig-perl libxml-xpath-perl linux-image-2.6.20-15-386
  linux-restricted-modules-2.6.20-15-386 metacity-common mktemp mono-gac mono-runtime mscompress myspell-en-za
  openoffice.org-filter-mobiledev openoffice.org-hyphenation openoffice.org-style-human python-bittorrent python-cairo
  python-egenix-mxdatetime python-gconf python-gnomecanvas python-gobject python-numarray python-numeric-ext python-scientific
  python2.5 python2.5-examples refblas3 ssl-cert startup-tasks system-services sysvutils tasksel tasksel-data tzdata update-inetd
  update-manager-core upstart-compat-sysv upstart-logd util-linux-locales vim-tiny volumeid wodim xbitmaps xorg
The following packages will be automatically REMOVED:
  libgcj7 libgd2-noxpm libgii0 libgii0-target-x libgl1-mesa libnewt0.51 libxklavier10 python2.4-adns python2.4-apt python2.4-cairo
  python2.4-clientcookie python2.4-crypto python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack
  python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-gadfly python2.4-gdbm python2.4-glade2 python2.4-gnome2
  python2.4-gnome2-desktop python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-imaging python2.4-imaging-sane
  python2.4-jabber python2.4-kjbuckets python2.4-libxml2 python2.4-mysqldb python2.4-numeric python2.4-pam python2.4-pexpect
  python2.4-pgsql python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-reportlab python2.4-simpletal
  python2.4-soappy python2.4-sqlite python2.4-syck python2.4-xml python2.4-xmpp
The following NEW packages will be installed:
  cli-common console-setup console-terminus cpp-4.1 cupsys-common dash espeak espeak-data evolution-common
  evolution-data-server-common feisty-gdm-themes feisty-session-splashes feisty-wallpapers gcc-3.4-base gcc-4.1 gdebi-core
  gnome-cards-data gnome-mount gnome-user-guide gpgv gtkhtml3.14 human-cursors-theme human-icon-theme human-theme lapack3
  libbluetooth2 libbtctl4 libcaca0 libcairo-perl libcairomm-1.0-1 libcamel1.2-10 libcompress-zlib-perl libcucul0 libdb4.4 libdns22
  libebook1.2-9 libecal1.2-7 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libenchant1c2a
  libespeak1 libexchange-storage1.2-3 libfont-afm-perl libg2c0 libgadu3 libgcj-bc libgcj7-0 libgcj7-awt libgd2-xpm libgdiplus libgii1
  libgii1-target-x libgksu2-0 libgl1-mesa-glx libgnome-window-settings1 libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgpod-common
  libgpod1 libgtkhtml3.14-19 libgucharmap6 libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhunspell-1.1-0 libicu36 libiec61883-0 libjaxp1.3-java libjaxp1.3-java-gcj libmailtools-perl libmono-cairo1.0-cil
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono2.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnewt0.52 libnm-glib0 liboobs-1-3 libopenobex1
  libparted1.7-1 libpci2 libpisock9 libpq5 libpulse0 libraw1394-8 libsensors3 libslab0 libstlport5.1 libtie-ixhash-perl
  libtimedate-perl liburi-perl libvisual-0.4-0 libvisual-0.4-plugins libvolume-id0 libvte9 libwps-0.1-1 libwww-perl libxcomposite1
  libxevie1 libxklavier11 libxml-parser-perl libxml-twig-perl libxml-xpath-perl linux-image-2.6.20-15-386
  linux-restricted-modules-2.6.20-15-386 metacity-common mktemp mono-gac mono-runtime mscompress myspell-en-za
  openoffice.org-filter-mobiledev openoffice.org-hyphenation openoffice.org-style-human python-bittorrent python-cairo
  python-egenix-mxdatetime python-gconf python-gnomecanvas python-gobject python-numarray python-numeric-ext python-scientific
  python2.5 python2.5-examples refblas3 ssl-cert startup-tasks system-services sysvutils tasksel tasksel-data tzdata update-inetd
  update-manager-core upstart-compat-sysv upstart-logd util-linux-locales vim-tiny volumeid wodim xbitmaps xorg
The following packages will be REMOVED:
  libgcj7 libgd2-noxpm libgii0 libgii0-target-x libgl1-mesa libnewt0.51 libxklavier10 python2.4-adns python2.4-apt python2.4-cairo
  python2.4-clientcookie python2.4-crypto python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack
  python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-gadfly python2.4-gdbm python2.4-glade2 python2.4-gnome2
  python2.4-gnome2-desktop python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-imaging python2.4-imaging-sane
  python2.4-jabber python2.4-kjbuckets python2.4-libxml2 python2.4-mysqldb python2.4-numeric python2.4-pam python2.4-pexpect
  python2.4-pgsql python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-reportlab python2.4-simpletal
  python2.4-soappy python2.4-sqlite python2.4-syck python2.4-xml python2.4-xmpp
The following packages will be upgraded:
  alacarte apt apt-utils aptitude at-spi bind9-host bittorrent bluez-cups bluez-pcmcia-support bluez-pin bluez-utils bug-buddy
  capplets-data cdrecord contact-lookup-applet cpp cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint debianutils
  deskbar-applet dnsutils ekiga evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal f-spot firefox
  firefox-gnome-support foo2zjs gaim gaim-data gcc gcj-4.1-base gdebi gedit gedit-common gij-4.1 gimp-python gksu gnome-applets
  gnome-applets-data gnome-control-center gnome-doc-utils gnome-games gnome-games-data gnome-mag gnome-media gnome-menus gnome-panel
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-screensaver gnome-session gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-utils gnome-volume-manager gnupg gok gparted grub gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gucharmap hal hpijs hplip hplip-data initramfs-tools initscripts irssi java-gcj-compat language-selector
  language-selector-common language-support-en launchpad-integration libavc1394-0 libbind9-0 libedata-book1.2-2 libgcj7-jar
  libgconf2.0-cil libggi2 libgl1-mesa-dri libglade2.0-cil libglib-perl libglib2.0-cil libgnome-speech3 libgnome2-canvas-perl
  libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomebt0 libgtk2-perl libgtk2.0-cil libgtkmm-2.4-1c2a libisccfg1 libperl5.8
  libpisync0 librdf0 libsexy2 libsnmp9 libtext-charwidth-perl libtext-iconv-perl libvte-common libwvstreams4.2-extras libxalan2-java
  libxerces2-java linux-386 linux-image-386 linux-restricted-modules-386 locales mdadm metacity mozilla-firefox-locale-en-gb mplayer
  nautilus-cd-burner nautilus-sendto netbase notification-daemon openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-writer parted pciutils perl perl-base perl-modules python python-adns python-apt python-cddb python-clientcookie
  python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc
  python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-glade2 python-gmenu
  python-gnome2 python-gnome2-desktop python-gnupginterface python-gst0.10 python-gtk2 python-htmlgen python-htmltmpl python-imaging
  python-imaging-sane python-jabber python-kjbuckets python-launchpad-integration python-libxml2 python-mysqldb python-netcdf
  python-newt python-numeric python-pam python-pexpect python-pgsql python-pisock python-pyao python-pylibacl python-pyopenssl
  python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats
  python-syck python-unit python-uno python-vte python-xdg python-xml python-xmpp python2.4 python2.4-examples python2.4-minimal
  reportbug rhythmbox sound-juicer synaptic system-tools-backends sysvinit totem totem-gstreamer ubuntu-artwork ubuntu-docs
  ubuntu-minimal udev update-manager util-linux whiptail x-window-system-core xterm
225 packages upgraded, 158 newly installed, 46 to remove and 0 not upgraded.
Need to get 11.6MB/359MB of archives. After unpacking 388MB will be used.
The following packages have unmet dependencies:
  rhythmbox-dbg: Depends: rhythmbox (= 0.9.4.1-0ubuntu1) but 0.10.0-0ubuntu2 is to be installed.
  python2.4-libxslt1: Depends: python2.4-libxml2 (>= 2.6.17) but it is not installable
  ubuntu-desktop: Depends: avahi-autoipd but it is not installable
                  Depends: desktop-effects but it is not installable
                  Depends: gnome-keyring-manager but it is not installable
                  Depends: hwdb-client-gnome but it is not installable
                  Depends: openprinting-ppds but it is not installable
                  Depends: usplash-theme-ubuntu but it is not installable
  python-id3lib: Depends: python (< 2.5) but 2.5.1~rc1-0ubuntu3 is to be installed.
  libvte4: Depends: libvte-common (= 1:0.12.2-0ubuntu1) but 1:0.16.1-0ubuntu1 is to be installed.
  gnome-app-install: Depends: python-gtkhtml2 but it is not installable
                     Depends: software-properties-gtk but it is not installable
  hwdb-client: Depends: python (< 2.5) but 2.5.1~rc1-0ubuntu3 is to be installed.
  hal-device-manager: Depends: hwdb-client-gnome but it is not installable
  upstart: Conflicts: sysvinit but 2.86.ds1-14.1ubuntu18 is to be installed.
  python-parted: Depends: python (< 2.5) but 2.5.1~rc1-0ubuntu3 is to be installed.
Resolving dependencies...
open: 8946; closed: 4953; defer: 0; conflict: 22                                                                                         .No solution found within the allotted time.  Try harder? [Y/n]n
russ@Binbuntu:~$ 


```

Try as it might, aptitude can never work it out.

I've tried many things (too many to summarize), but does anyone have a recommendation?  It seems I need to clean out python and start fresh, but can't!  Installs being held back is confusing me, too... not sure how to prevent holdbacks.

Argh!!

Thanks,
Russ

---

### Post by qopit on 2007-05-08
Forgot to post my current sources.list.  It is:
```

deb http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ feisty universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty universe

deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

# Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free


```

---

### Post by qopit on 2007-05-09
Ok... after more research and poking around I ended up managing to uninstall pretty much everything by going lower level and using dselect to manually remove pretty much everything.

With the aid of the sticky at [http://ubuntuforums.org/showthread.php?t=18667](http://ubuntuforums.org/showthread.php?t=18667) I've been reinstalling everything and am now at the basic "aptitude upgrade" phase and my set of original problems are (finally) gone.

However - I'm now left with some things that I'm stumped on and the problem packages seem pretty important....

```

russ@Binbuntu:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have unmet dependencies:
  dmsetup: Breaks: udev (< 108-0ubuntu3) but 079-0ubuntu34 is installed and it is kept back.
  lvm2: Breaks: udev (< 103-0ubuntu3) but 079-0ubuntu34 is installed and it is kept back.

```

Why would they be held back?  I started from almost nothing!  Any help is appreciated...

Russ

---

### Post by ssam on 2007-05-09
the recommended upgrade methods for ubuntu are detailed at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

there is a command line method using update-manager-core (look at the [Network upgrade for Ubuntu servers]("http://www.ubuntu.com/getubuntu/upgrading#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf") section)

---

