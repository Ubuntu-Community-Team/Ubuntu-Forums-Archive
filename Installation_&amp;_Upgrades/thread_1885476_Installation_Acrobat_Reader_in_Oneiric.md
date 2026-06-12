---
title: "Installation Acrobat Reader in Oneiric"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by MrQuincle on 2011-11-23
Dear people,

Yesterday I wanted to reinstall my 32-bits applications, skype and acroread. 

I understood that 64-bits Oneiric (11.10) does now provide real 32-bits support, so I can install Adobe Acrobat Reader like this:
```

 sudo apt-get install acroread:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 acroread:i386 : Depends: libgtk2.0-0:i386 (>= 2.8.0) but it is not going to be installed
                 Depends: libxml2:i386 (>= 2.6.27) but it is not going to be installed
                 Depends: acroread-common:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Descending the dependency chain:
```

sudo apt-get install libgtk2.0-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtk2.0-0:i386 : Depends: libcups2:i386 (>= 1.4.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

```

sudo apt-get install libcups2:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcups2:i386 : Depends: libavahi-client3:i386 (>= 0.6.16) but it is not going to be installed
                 Depends: libavahi-common3:i386 (>= 0.6.16) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I ended here. And had a big panick attack. I had to reinstall gdm, update-manager, etc. on accidently typing yes to the following question:
```

sudo apt-get install libavahi-common3:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  telepathy-indicator libswt-cairo-gtk-3-jni libtextcat-data python-prctl libtextcat0 libmythes-1.2-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavahi-common-data:i386 pinentry-curses
Suggested packages:
  pinentry-doc
The following packages will be REMOVED:
  alacarte apport-gtk avahi-daemon azureus bamfdaemon baobab browser-plugin-gnash caribou colord compiz compiz-core compiz-gnome compiz-plugins-default
  compiz-plugins-main-default compizconfig-backend-gconf cups cups-client cups-driver-gutenprint cups-pk-helper cups-ppdc default-jdk default-jre
  default-jre-headless delta3d-dev desktopcouch eclipse eclipse-jdt eclipse-pde eclipse-platform eclipse-rcp empathy evince evolution-data-server firefox
  firefox-globalmenu gdm gedit ghostscript ghostscript-cups ghostscript-x gimp gir1.2-caribou-1.0 gir1.2-dbusmenu-gtk-0.4 gir1.2-gkbd-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gtk-2.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-launchpad-integration-3.0 gir1.2-mutter-3.0 gir1.2-panelapplet-4.0
  gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gksu glipper gnash gnome-applets gnome-bluetooth gnome-control-center gnome-dictionary
  gnome-icon-theme gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring gnome-media gnome-online-accounts gnome-panel gnome-power-manager
  gnome-screenshot gnome-search-tool gnome-session gnome-session-bin gnome-session-fallback gnome-settings-daemon gnome-shell gnome-system-log
  gnome-system-monitor gnome-terminal gnome-themes-standard gnome-user-guide gnome-user-share gnome-utils gs-cjk-resource gtk2-engines gvfs-backends
  humanity-icon-theme ibus ibus-gtk ibus-gtk3 icedtea-netx indicator-application indicator-appmenu indicator-datetime indicator-messages indicator-power
  indicator-session indicator-sound indicator-status-provider-mc5 libappindicator1 libappindicator3-1 libavahi-client3 libavahi-common-data
  libavahi-common-dev libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libbamf3-0 libbonoboui2-0 libbrasero-media3-1
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcaribou0 libclutter-gtk-0.10-0 libcompizconfig0 libcups2
  libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libcv-dev libcvaux-dev libcvaux2.1 libdmapsharing-3.0-2 libedataserverui-3.0-1
  libevince3-3 libg3d-plugin-gdkpixbuf libgail-3-0 libgail-common libgail18 libgcr-3-1 libgcu0 libgdict-1.0-6 libgimp2.0 libgksu2-0 libglade2-0
  libglade2-dev libglade2.0-cil libglademm-2.4-1c2a libglademm-2.4-dev libgladeui-1-11 libgnome-bluetooth8 libgnome-control-center1 libgnome-desktop-2-17
  libgnome-desktop-3-2 libgnome-media-profiles-3.0-0 libgnome-vfs2.0-cil libgnome2-0 libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl
  libgnome2.24-cil libgnomecanvas2-0 libgnomekbd7 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-extra libgoa-1.0-0 libgoffice-0.8-8 libgoocanvas3 libgrip0
  libgs9 libgtk-3-0 libgtk-3-bin libgtk-sharp-beans-cil libgtk-vnc-1.0-0 libgtk2-gladexml-perl libgtk2-perl libgtk2-ruby1.8 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-cil libgtk2.0-dev libgtkglext1 libgtkglext1-dev libgtkhex0 libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmathview0c2a libgtkmm-2.4-1c2a
  libgtkmm-2.4-dev libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview2.0-0 libgtkspell0 libgucharmap-2-90-7 libgucharmap7 libgweather-3-0
  libhighgui-dev libhighgui2.1 libido3-0.1-0 libindicator3-6 libindicator6 libkeybinder0 liblaunchpad-integration-3.0-1 liblaunchpad-integration1
  liblaunchpad-integration1.0-cil libmetacity-private0 libmlt++3 libmlt4 libmono-addins-gui0.2-cil libmrpt-base0.9 libmrpt-bayes0.9 libmrpt-detectors0.9
  libmrpt-dev libmrpt-gui0.9 libmrpt-hmtslam0.9 libmrpt-hwdrivers0.9 libmrpt-maps0.9 libmrpt-obs0.9 libmrpt-opengl0.9 libmrpt-reactivenav0.9
  libmrpt-scanmatching0.9 libmrpt-slam0.9 libmrpt-topography0.9 libmrpt-vision0.9 libmutter0 libmx-1.0-2 libnautilus-extension1 libnm-gtk0
  libnotify0.4-cil libnss-mdns liboverlay-scrollbar-0.2-0 libpanel-applet-4-0 libpeas-1.0-0 libpolkit-gtk-1-0 libpurple0 libqtbamf1 libreoffice-common
  libreoffice-core libreoffice-style-human librhythmbox-core4 librsvg2-common librsvg2-dev libsane libsexy2 libspectre1 libswt-gnome-gtk-3-jni
  libswt-gnome-gtk-3.5-jni libswt-gtk-3-java libswt-gtk-3-jni libswt-webkit-gtk-3-jni libunique-1.0-0 libunique-3.0-0 libunity-2d-private0
  libunity-core-4.0-4 libvte-2.90-9 libvte9 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwnck-3-0 libwnck22 libwxgtk2.8-0 libwxgtk2.8-dev libxfce4ui-1-0
  libyelp0 macchanger-gtk meld melt metacity mousetweaks mrpt-libs nautilus nautilus-sendto nautilus-sendto-empathy network-manager-gnome nvidia-settings
  oneconf openjdk-6-jdk openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib paman pavucontrol pavumeter pinentry-gtk2 plymouth-x11 policykit-1-gnome
  pulseaudio-equalizer python-appindicator python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-avahi
  python-desktopcouch-application python-glade2 python-gmenu python-gnome2 python-gnomekeyring python-gtk2 python-gtksourceview2 python-gtkspell
  python-ibus python-keybinder python-launchpad-integration python-notify python-pygoocanvas python-rsvg python-ubuntuone-client python-virtkey python-vte
  python-webkit python-wnck rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins robot3d robot3d-dev ruby-gtk2 sane-utils sessioninstaller
  software-center software-properties-gtk ssh-askpass-gnome synaptic telepathy-haze telepathy-salut thoggen thunderbird thunderbird-globalmenu
  thunderbird-gnome-support ubuntu-docs ubuntu-sso-client unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-asset-pool
  unity-lens-applications unity-lens-files unity-place-applications unity-place-files unity-services update-manager update-notifier upnp-inspector vlc
  vlc-nox vlc-plugin-notify vlc-plugin-pulse vuze winff winff-doc wireshark x11vnc xdg-user-dirs-gtk xournal xscreensaver yelp zeitgeist zeitgeist-datahub
  zeitgeist-extension-fts zenity
The following NEW packages will be installed:
  libavahi-common-data:i386 libavahi-common3:i386 pinentry-curses
0 upgraded, 3 newly installed, 359 to remove and 0 not upgraded.
Need to get 0 B/76.8 kB of archives.
After this operation, 1,076 MB disk space will be freed.
Do you want to continue [Y/n]? 

```

First I thought it was removing redundant 32-bit versions of these packages, but then I realized my icons disappeared... and something else must be happening. Ctrl+C didn't work (known bug). So I killed the apt-get process.

I reinstalled most of the things and have the feeling that this error which remains should be easy to solve. First, however, I would like to know if people were able to install "acroread" on 64-bit system and how.

Thanks in advance!


PS: I did of course already:
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch

```

---

### Post by fantab on 2011-11-23
The simplest way to install Acroread is to do it from **Ubuntu Software Center.**

You can also install it with **Synaptic**.

Or from **Terminal**

```
$sudo apt-get install acroread
```

yes...  on 64 bit_11.10 (just make sure you have Multiverse Repos enabled, this is enabled by default so if you haven't disabled them don't worry)

---

### Post by MrQuincle on 2011-11-24
> **fantab said:**
> The simplest way to install Acroread is to do it from **Ubuntu Software Center.**


Hi fantab. I thought my post was clear that I am WAY BEYOND that stage of trying to install acroread. Of course the universe/multiverse repositories are enabled. I know my way around launchpad, cowbuilder, update-alternatives, apt-get, apt-cache, dpkg, ldd, nm, etc. 

My problem is that I want to install a 32bit application (acroread) on 11.10 and I end up in a dependency hell w.r.t. libgtk-2.0 (via libcups). I admit that I installed Gnome 3 already on 11.04.

```

pt-cache show gnome-shell
Package: gnome-shell
Priority: optional
Section: universe/gnome
Installed-Size: 4868
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Gustavo Noronha Silva <gustavo.noronha@collabora.co.uk>
Architecture: amd64
Version: 3.2.0-0ubuntu1
Depends: gir1.2-atk-1.0, gir1.2-clutter-1.0, gir1.2-cogl-1.0, gir1.2-folks-0.6, gir1.2-freedesktop, gir1.2-gdkpixbuf-2.0, gir1.2-gee-1.0, gir1.2-glib-2.0, gir1.2-gmenu-3.0, gir1.2-gtk-3.0, gir1.2-json-1.0, gir1.2-mutter-3.0, gir1.2-networkmanager-1.0, gir1.2-pango-1.0, gir1.2-soup-2.4, gir1.2-telepathyglib-0.12, gir1.2-telepathylogger-0.2, gjs (>= 1.29.18), gnome-bluetooth (>= 3.0.0), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.10.0), libcanberra0 (>= 0.2), libclutter-1.0-0 (>= 1.7.6), libcogl5 (>= 1.7.4), libcroco3 (>= 0.6.2), libdbus-glib-1-2 (>= 0.78), libecal1.2-10 (>= 3.2.0), libedataserver1.2-15 (>= 3.2.0), libedataserverui-3.0-1 (>= 3.2.0), libfolks25 (>= 0.5.2), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgee2 (>= 0.5.0), libgirepository-1.0-1 (>= 0.9.2), libgjs0c (>= 1.29.18), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.29.10), libgnome-desktop-3-2 (>= 2.91.5), libgnome-keyring0 (>= 2.20.3), libgnome-menu-3-0 (>= 3.1.5), libgstreamer0.10-0 (>= 0.10.20), libgtk-3-0 (>= 3.0.0), libical0 (>= 0.30), libjson-glib-1.0-0 (>= 0.13.2), libmozjs185-1.0 (>= 1.8.5~hg20110306r6), libmutter0 (>= 3.1.92), libnm-glib4 (>= 0.8.998), libnm-util2 (>= 0.8.998), libpango1.0-0 (>= 1.14.0), libpolkit-agent-1-0 (>= 0.99), libpolkit-gobject-1-0 (>= 0.94), libpulse-mainloop-glib0 (>= 1:0.99.1), libpulse0 (>= 1:0.99.1), libstartup-notification0 (>= 0.11), libtelepathy-glib0 (>= 0.15.5), libtelepathy-logger2 (>= 0.2.0), libx11-6, libxfixes3 (>= 1:5.0), libxml2 (>= 2.7.4), dconf-gsettings-backend | gsettings-backend, gconf2 (>= 2.28.1-2), caribou, libdconf0 | gsettings-backend, gnome-settings-daemon (>= 2.91.5.1), gsettings-desktop-schemas (>= 0.1.7), gnome-icon-theme-symbolic (>= 2.91), gnome-icon-theme-full, gir1.2-accountsservice-1.0, gir1.2-gconf-2.0, gir1.2-gkbd-3.0, gir1.2-gnomebluetooth-1.0, gir1.2-polkit-1.0, gir1.2-upowerglib-1.0, python, pkg-config, mesa-utils

```

Yesterday, I installed acroread on another Ubuntu 11.10 which went smoothly. Hence, I would like to know:
[LIST]
[*]Is it impossible to have acroread and Gnome 3 at the same time on my system?
[*]Or can I somehow fool dpkg in installing a 32bits version of the libgtk2.0-0 package?
[/LIST]

---

### Post by fantab on 2011-11-24
> **MrQuincle said:**
> Hi fantab. I thought my post was clear that I am WAY BEYOND that stage of trying to install acroread. Of course the universe/multiverse repositories are enabled. I know my way around launchpad, cowbuilder, update-alternatives, apt-get, apt-cache, dpkg, ldd, nm, etc. 

My problem is that I want to install a 32bit application (acroread) on 11.10 and I end up in a dependency hell w.r.t. libgtk-2.0 (via libcups). I admit that I installed Gnome 3 already on 11.04.

```

pt-cache show gnome-shell
Package: gnome-shell
Priority: optional
Section: universe/gnome
Installed-Size: 4868
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Gustavo Noronha Silva <gustavo.noronha@collabora.co.uk>
Architecture: amd64
Version: 3.2.0-0ubuntu1
Depends: gir1.2-atk-1.0, gir1.2-clutter-1.0, gir1.2-cogl-1.0, gir1.2-folks-0.6, gir1.2-freedesktop, gir1.2-gdkpixbuf-2.0, gir1.2-gee-1.0, gir1.2-glib-2.0, gir1.2-gmenu-3.0, gir1.2-gtk-3.0, gir1.2-json-1.0, gir1.2-mutter-3.0, gir1.2-networkmanager-1.0, gir1.2-pango-1.0, gir1.2-soup-2.4, gir1.2-telepathyglib-0.12, gir1.2-telepathylogger-0.2, gjs (>= 1.29.18), gnome-bluetooth (>= 3.0.0), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.10.0), libcanberra0 (>= 0.2), libclutter-1.0-0 (>= 1.7.6), libcogl5 (>= 1.7.4), libcroco3 (>= 0.6.2), libdbus-glib-1-2 (>= 0.78), libecal1.2-10 (>= 3.2.0), libedataserver1.2-15 (>= 3.2.0), libedataserverui-3.0-1 (>= 3.2.0), libfolks25 (>= 0.5.2), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgee2 (>= 0.5.0), libgirepository-1.0-1 (>= 0.9.2), libgjs0c (>= 1.29.18), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.29.10), libgnome-desktop-3-2 (>= 2.91.5), libgnome-keyring0 (>= 2.20.3), libgnome-menu-3-0 (>= 3.1.5), libgstreamer0.10-0 (>= 0.10.20), libgtk-3-0 (>= 3.0.0), libical0 (>= 0.30), libjson-glib-1.0-0 (>= 0.13.2), libmozjs185-1.0 (>= 1.8.5~hg20110306r6), libmutter0 (>= 3.1.92), libnm-glib4 (>= 0.8.998), libnm-util2 (>= 0.8.998), libpango1.0-0 (>= 1.14.0), libpolkit-agent-1-0 (>= 0.99), libpolkit-gobject-1-0 (>= 0.94), libpulse-mainloop-glib0 (>= 1:0.99.1), libpulse0 (>= 1:0.99.1), libstartup-notification0 (>= 0.11), libtelepathy-glib0 (>= 0.15.5), libtelepathy-logger2 (>= 0.2.0), libx11-6, libxfixes3 (>= 1:5.0), libxml2 (>= 2.7.4), dconf-gsettings-backend | gsettings-backend, gconf2 (>= 2.28.1-2), caribou, libdconf0 | gsettings-backend, gnome-settings-daemon (>= 2.91.5.1), gsettings-desktop-schemas (>= 0.1.7), gnome-icon-theme-symbolic (>= 2.91), gnome-icon-theme-full, gir1.2-accountsservice-1.0, gir1.2-gconf-2.0, gir1.2-gkbd-3.0, gir1.2-gnomebluetooth-1.0, gir1.2-polkit-1.0, gir1.2-upowerglib-1.0, python, pkg-config, mesa-utils

```Yesterday, **I installed acroread on another Ubuntu 11.10 which went smoothly**. Hence, I would like to know:
[LIST]
[*]Is it impossible to have acroread and Gnome 3 at the same time on my system?
[*]Or can I somehow fool dpkg in installing a 32bits version of the libgtk2.0-0 package?
[/LIST]


By Gnome 3 you mean Gnome-Shell, because whether UNITY or SHELL it is Gnome 3.

Installing Acroread, which is 32 bit, is very easy to do in Ubuntu_64bit as you already know. Yes, you have somehow managed to mess up while installing Gnome-Shell and unless a better solution comes your way, I suggest you reinstall Ubuntu. 

By the way, Acroread does not depend on the Desktop Environment, be it Shell, Unity or something else.

Hope this helps.

---

### Post by MrQuincle on 2011-11-28
> **fantab said:**
> By Gnome 3 you mean Gnome-Shell, because whether UNITY or SHELL it is Gnome 3.

Installing Acroread, which is 32 bit, is very easy to do in Ubuntu_64bit as you already know. Yes, you have somehow managed to mess up while installing Gnome-Shell and unless a better solution comes your way, I suggest you reinstall Ubuntu. 

By the way, Acroread does not depend on the Desktop Environment, be it Shell, Unity or something else.

Hope this helps.
This is of course of no help. 

If I have package dependency problems like e.g. this person here [http://askubuntu.com/questions/76766/how-do-i-overcome-these-package-dependency-problems](http://askubuntu.com/questions/76766/how-do-i-overcome-these-package-dependency-problems) and I would reinstall my operating system all the time I would be doing nothing else... 

I prefer to learn how my system operates, and I hope someone else is willing to help me out here in understanding my system.

---

### Post by MrQuincle on 2011-11-28
Hi everybody who ever runs into this kind of problems... And I have seen many of these online referring then to acroread, then to skype, then to a flashplugin, then to anything else that depends on e.g. nspluginviewer or CUPS.

I solved my problem by removing the following text from /var/lib/dpkg/status:
```

Package: libavahi-common3
Status: purge ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 140
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: avahi
Version: 0.6.30-5ubuntu1~natty2
Depends: libc6 (>= 2.4), libavahi-common-data
Pre-Depends: multiarch-support
Description: Avahi common library
 Avahi is a fully LGPL framework for Multicast DNS Service Discovery.
 It allows programs to publish and discover services and hosts
 running on a local network with no specific configuration. For
 example you can plug into a network and instantly find printers to
 print to, files to look at and people to talk to.
 .
 This package contains the Avahi common library, which is a set of common
 functions used by many of Avahis components and client applications.
Homepage: http://avahi.org/
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>

Package: libavahi-common-data
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 884
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: avahi
Version: 0.6.30-5ubuntu1~natty2
Description: Avahi common data files
 Avahi is a fully LGPL framework for Multicast DNS Service Discovery.
 It allows programs to publish and discover services and hosts
 running on a local network with no specific configuration. For
 example you can plug into a network and instantly find printers to
 print to, files to look at and people to talk to.
 .
 This package contains common data files for avahi.
Homepage: http://avahi.org/
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>

Package: libavahi-client3
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 164
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: avahi
Version: 0.6.30-5ubuntu1~natty2
Depends: libavahi-common3 (>= 0.6.22), libc6 (>= 2.4), libdbus-1-3 (>= 1.1.1)
Pre-Depends: multiarch-support
Description: Avahi client library
 Avahi is a fully LGPL framework for Multicast DNS Service Discovery.
 It allows programs to publish and discover services and hosts
 running on a local network with no specific configuration. For
 example you can plug into a network and instantly find printers to
 print to, files to look at and people to talk to.
 .
 This package contains the library for Avahi's C API which  allows you
 to integrate mDNS/DNS-SD functionality into your application.
Homepage: http://avahi.org/
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>

```
After you do this, run the usual apt-get update (2x), apt-get -f install and apt-get upgrade.

And now you should be able to install acroread in the normal way. If another package is giving you troubles, remove it in the dpkg status file and reinstall it as usual.

So, back to booklet printing.

:popcorn:

---

### Post by IPEX-731BA5DD06 on 2012-01-26
Note, the bin file 9.4.7-1 won't install properly. It partly installs, maybe I did it wrong, but wouldn't install. 

I right clicked on file, made executable, drag and dropped into a terminal, highlighted cursor (made solid white) it starts to install, but stops so far in?? don't know, don't care, the sudo apt-get worked listed above, Thank you very much peeps

---

