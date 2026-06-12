---
title: "broken: gamin - possible bug in aptitude?"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by r.stiltskin on 2007-03-12
Possible bug in aptitude, or apt-get or anjuta?

I just did a complete new installation of Kubuntu Edgy Eft (after my attempt to upgrade it from Dapper turned up so many problems that it didn't seem worth trying to fix).

The installation went cleanly; no errors or broken packages occurred.
apt-get -fs install does not report any problems
aptitude -fs install does not report any problems

Now I want to install Anjuta.
apt-get -s install anjuta returns:
```
# apt-get -s install anjuta
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  anjuta-common devhelp-common libapr0 libdevhelp-1-0 libgbf-1-0
  libgbf-1-common libgdl-1-0 libgdl-1-common libsvn0 libvte-common libvte9
Suggested packages:
  libgtk2.0-dev libgtkmm2.0-dev libgnome2-dev libgnomemm2.0-dev devhelp-books
  glade-2 glade-gnome-2
Recommended packages:
  cvs gnome-terminal yelp automake autoconf autogen indent ctags devhelp
  gnome-devel libtool
The following NEW packages will be installed:
  anjuta anjuta-common devhelp-common libapr0 libdevhelp-1-0 libgbf-1-0
  libgbf-1-common libgdl-1-0 libgdl-1-common libsvn0 libvte-common libvte9
0 upgraded, 12 newly installed, 0 to remove and 118 not upgraded.

```
So -- according to apt-get, no problems.

[SIZE="4"]But...[/SIZE]aptitude -s install anjuta gives this mess:```

# aptitude -s install anjuta
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gamin
The following packages have been automatically kept back:
  kppp linux-image-2.6.17-10-generic openoffice.org-writer xbase-clients
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-all xutils
The following NEW packages will be automatically installed:
  alacarte anjuta-common app-install-data-commercial autoconf autogen
  automake1.4 autotools-dev bluefish capplets-data cvs deborphan
  deskbar-applet desktop-base desktop-file-utils devhelp devhelp-common
  dialog doc-gnome-hig docbook docbook-dsssl docbook-to-man docbook-xsl
  evolution-data-server evolution-data-server-common exuberant-ctags fam
  gksu glade-common glade-gnome gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-common gnome-control-center gnome-core-devel
  gnome-desktop-data gnome-devel gnome-doc-utils gnome-icon-theme
  gnome-media gnome-menus gnome-netstatus-applet gnome-panel
  gnome-panel-data gnome-power-manager gnome-session gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-utils gnome2-user-guide
  gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-x gtk-doc-tools gtranslator guile-1.6-libs imagemagick
  indent intltool jade libaa1 libapr0 libart-2.0-dev libatk1.0-dev
  libatspi-dev libatspi1.0-0 libaudiofile-dev libavahi-client-dev
  libavahi-common-dev libavahi-glib-dev libavc1394-0 libbeagle0
  libbonobo2-dev libbonoboui2-dev libbz2-dev libcairo-perl libcairo2-dev
  libcamel1.2-8 libcdio6 libcompress-zlib-perl libcroco3-dev libdbus-1-dev
  libdbus-glib-1-dev libdevhelp-1-0 libdv-bin libdv4 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libeel2-2 libeel2-data libeel2-dev
  libegroupwise1.2-12 libenchant1c2a libesd0-dev libexpat1-dev
  libfont-afm-perl libfontconfig1-dev libfreetype6-dev libgail-common
  libgail-dev libgail-gnome-module libgail18 libgbf-1-0 libgbf-1-common
  libgconf2-dev libgcrypt11-dev libgda2-3 libgda2-bin libgda2-common
  libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksu2-0 libgksuui1.0-1
  libglade2-dev libglib-perl libglib2.0-dev libglib2.0-doc
  libgnome-desktop-dev libgnome-keyring-dev libgnome-menu-dev
  libgnome-menu2 libgnome-window-settings1 libgnome2-canvas-perl
  libgnome2-dev libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-dev
  libgnomeprint2.2-dev libgnomeprintui2.2-dev libgnomeui-dev
  libgnomevfs2-dev libgnomevfs2-extra libgnutls-dev libgpg-error-dev
  libgsf-1-dev libgtk1.2 libgtk1.2-common libgtk2-perl libgtk2.0-dev
  libgtk2.0-doc libgtkhtml2-0 libgtksourceview-dev libgtkspell0
  libgucharmap5 libguile-ltdl-1 libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libice-dev libidl-dev libiec61883-0
  libjpeg62-dev liblpint-bonobo0 libltdl3 libltdl3-dev liblzo-dev
  libmailtools-perl libnautilus-extension-dev libnautilus-extension1
  libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-2 libopencdk8-dev
  libopts25 libopts25-dev liborbit2-dev libpanel-applet2-dev
  libpango1.0-dev libpango1.0-doc libpng12-dev libpopt-dev libqthreads-12
  librsvg2-common librsvg2-dev libselinux1-dev libsepol1-dev libsexy2
  libshout3 libsm-dev libsoup2.2-8 libsp1c2 libstartup-notification0-dev
  libsvn0 libtasn1-3-dev libtimedate-perl libtool liburi-perl libvte-common
  libvte9 libwww-perl libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxklavier11 libxml-grove-perl libxml-parser-perl libxml-perl
  libxml2-dev libxml2-utils libxrandr-dev libxrender-dev libxslt1-dev
  libxt-dev libxtst-dev m4 menu menu-xdg metacity nautilus
  nautilus-cd-burner nautilus-data notification-daemon orbit2 portmap
  python-beagle python-gconf python-gdbm python-gmenu python-gnome2
  python-gnome2-extras python-gnomecanvas python-gnupginterface
  python-gtkhtml2 python-launchpad-integration python-soappy python-vte
  python-xdg python-xml sp synaptic system-tools-backends
  unattended-upgrades update-manager x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xsltproc
  xtrans-dev yelp zlib1g-dev
The following packages have been kept back:
  avahi-daemon bind9-host dbus dnsutils gnupg info kate kcontrol
  kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdeprint
  kdesktop kdm kdnssd kfind khelpcenter kicker klipper kmenuedit
  koffice-data koffice-libs konqueror konqueror-nsplugins konsole kopete
  kpf krdc krfb krita krita-data ksmserver ksplash ksysguard ksysguardd
  kwin language-pack-en language-pack-kde-en libavahi-common-data
  libavahi-compat-libdnssd1 libavahi-core4 libavahi-qt3-1 libbind9-0 libc6
  libc6-dev libc6-i686 libdns21 libimlib2 libisc11 libisccc0 libisccfg1
  libkonq4 libkrb53 liblwres9 libmagick++9c2a libmagick9 libpoppler1
  libpoppler1-qt libpq4 libruby1.8 libsmbclient libvolumeid0 libxine1
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic
  linux-headers-generic linux-image-generic linux-libc-dev openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-impress
  openoffice.org-java-common openoffice.org-kde openoffice.org-math
  openoffice.org-style-crystal openoffice.org-style-default poppler-utils
  python-uno ruby1.8 samba-common screen slocate smbclient tar tcpdump
  ttf-opensymbol tzdata udev volumeid w3m wlassistant x11-common xorg
  xserver-xorg
The following NEW packages will be installed:
  alacarte anjuta anjuta-common app-install-data-commercial autoconf
  autogen automake1.4 autotools-dev bluefish capplets-data cvs deborphan
  deskbar-applet desktop-base desktop-file-utils devhelp devhelp-common
  dialog doc-gnome-hig docbook docbook-dsssl docbook-to-man docbook-xsl
  evolution-data-server evolution-data-server-common exuberant-ctags fam
  gksu glade-common glade-gnome gnome-about gnome-app-install gnome-applets
  gnome-applets-data gnome-common gnome-control-center gnome-core-devel
  gnome-desktop-data gnome-devel gnome-doc-utils gnome-icon-theme
  gnome-media gnome-menus gnome-netstatus-applet gnome-panel
  gnome-panel-data gnome-power-manager gnome-session gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-utils gnome2-user-guide
  gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-x gtk-doc-tools gtranslator guile-1.6-libs imagemagick
  indent intltool jade libaa1 libapr0 libart-2.0-dev libatk1.0-dev
  libatspi-dev libatspi1.0-0 libaudiofile-dev libavahi-client-dev
  libavahi-common-dev libavahi-glib-dev libavc1394-0 libbeagle0
  libbonobo2-dev libbonoboui2-dev libbz2-dev libcairo-perl libcairo2-dev
  libcamel1.2-8 libcdio6 libcompress-zlib-perl libcroco3-dev libdbus-1-dev
  libdbus-glib-1-dev libdevhelp-1-0 libdv-bin libdv4 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libeel2-2 libeel2-data libeel2-dev
  libegroupwise1.2-12 libenchant1c2a libesd0-dev libexpat1-dev
  libfont-afm-perl libfontconfig1-dev libfreetype6-dev libgail-common
  libgail-dev libgail-gnome-module libgail18 libgbf-1-0 libgbf-1-common
  libgconf2-dev libgcrypt11-dev libgda2-3 libgda2-bin libgda2-common
  libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksu2-0 libgksuui1.0-1
  libglade2-dev libglib-perl libglib2.0-dev libglib2.0-doc
  libgnome-desktop-dev libgnome-keyring-dev libgnome-menu-dev
  libgnome-menu2 libgnome-window-settings1 libgnome2-canvas-perl
  libgnome2-dev libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-dev
  libgnomeprint2.2-dev libgnomeprintui2.2-dev libgnomeui-dev
  libgnomevfs2-dev libgnomevfs2-extra libgnutls-dev libgpg-error-dev
  libgsf-1-dev libgtk1.2 libgtk1.2-common libgtk2-perl libgtk2.0-dev
  libgtk2.0-doc libgtkhtml2-0 libgtksourceview-dev libgtkspell0
  libgucharmap5 libguile-ltdl-1 libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libice-dev libidl-dev libiec61883-0
  libjpeg62-dev liblpint-bonobo0 libltdl3 libltdl3-dev liblzo-dev
  libmailtools-perl libnautilus-extension-dev libnautilus-extension1
  libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-2 libopencdk8-dev
  libopts25 libopts25-dev liborbit2-dev libpanel-applet2-dev
  libpango1.0-dev libpango1.0-doc libpng12-dev libpopt-dev libqthreads-12
  librsvg2-common librsvg2-dev libselinux1-dev libsepol1-dev libsexy2
  libshout3 libsm-dev libsoup2.2-8 libsp1c2 libstartup-notification0-dev
  libsvn0 libtasn1-3-dev libtimedate-perl libtool liburi-perl libvte-common
  libvte9 libwww-perl libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxklavier11 libxml-grove-perl libxml-parser-perl libxml-perl
  libxml2-dev libxml2-utils libxrandr-dev libxrender-dev libxslt1-dev
  libxt-dev libxtst-dev m4 menu menu-xdg metacity nautilus
  nautilus-cd-burner nautilus-data notification-daemon orbit2 portmap
  python-beagle python-gconf python-gdbm python-gmenu python-gnome2
  python-gnome2-extras python-gnomecanvas python-gnupginterface
  python-gtkhtml2 python-launchpad-integration python-soappy python-vte
  python-xdg python-xml sp synaptic system-tools-backends
  unattended-upgrades update-manager x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xsltproc
  xtrans-dev yelp zlib1g-dev
The following packages will be upgraded:
  libavahi-client3 libavahi-common3 libdbus-1-3 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libpng12-0
7 packages upgraded, 263 newly installed, 0 to remove and 111 not upgraded.
Need to get 93.9MB/95.8MB of archives. After unpacking 403MB will be used.
The following packages have unmet dependencies:
  gamin: Conflicts: fam but 2.7.0-10ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
anjuta [Not Installed]
fam [Not Installed]
glade-gnome [Not Installed]
gnome-devel [Not Installed]

Leave the following dependencies unresolved:
nautilus recommends fam
Score is -174

Accept this solution? [Y/n/q/?]                
```


Should I ignore aptitude & just go ahead with apt-get install anjuta?

Should this be reported as an aptitude bug?


This is basically a completely clean new system; the only "extras" added after the (alternate) install cd were:
apt-get install linux-restricted-modules-`uname -r` to get drivers for atheros wireless card and synaptic touchpad

apt-get install java-package (needed to build sun-j2sdk1.5 .deb package)
dpkg sun-j2sdk1.5_1.5.0+update11_i386.deb
apt-get install sun-java5-doc
apt-get install gedit
apt-get install eclipse

Of course, there were various dependencies installed along with gedit and eclipse, but everything went smoothly & no errors or broken packages appeared.

---

