---
title: "Python dependancy problem"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by BDwinsAlt on 2007-04-09
I have an issue with Python2.4.  When I try to reinstall or remove python2.4 it wants me to remove about 208 other packages including gnome and other important packages.  I downloaded the python source and tried it that way but I had no luck.  It wants me to remove all packages (including my package manager) before install it.  I install a different verison of python and now I can't install anything else with the package manager.  It says the dependancy is broken.  I can't seem to fix it.  I tried downloading the source and building it with the apt-get but no luck.

How can I reinstall python without it conflicting with my ENTIRE system.

Thanks,
Brad

```

root@brad-desktop:/home/brad/Desktop# apt-get install python2.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.4 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python2.4: Depends: python2.4-minimal (= 2.4.4~c1-0ubuntu1) but 2.4.4-3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@brad-desktop:/home/brad/Desktop# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-crypto resapplet f-spot libgnomecupsui1.0-1c2a libopenexr2c2a
  desktop-base python-zopeinterface liblaunchpad-integration0 libcamel1.2-8
  libgtkhtml3.8-15 libarts1c2a planner tomboy wallpaper-tray camorama
  python-twisted-core evolution-webcal ekiga python2.4-dbg kdelibs4c2a
  libgsf-gnome-1-114 openoffice.org-gnome python-twisted-web2 python-gst0.10
  notification-daemon libgnomevfs2-0 gcalctool python2.4-dev libopenal0a
  gthumb gnome-desktop-environment libgstreamer0.8-0 python2.4-schoolbell
  update-manager system-config-kickstart openoffice.org-writer python-gnome2
  gnome-nettool python-support courier-authlib-ldap libgoffice-0-common
  gnome-media metacity abiword-gnome nautilus python2.4-examples libgnome2-0
  libapache2-mod-python2.4 libgail-gnome-module dia-libs python-at-spi
  python2.4-speex libcyrus-imap-perl21 bluefish giplet python-apport-utils
  python2.4-librdf beryl-settings-bindings python-gnome2-extras
  gstreamer0.8-misc gucharmap boson-base python-gnomecanvas
  industrial-cursor-theme python-clientform gnome-games hwdb-client-gnome
  libgstreamer-gconf0.8-0 gdebi sensors-applet vnc-common evolution-exchange
  python2.4-gd evolution beryl-dev openoffice.org-gtk libgnome-media0
  python-pygame python2.4-dictclient gnome-power-manager python2.4-paramiko
  libexchange-storage1.2-2 python2.4-configlet childsplay gnome-screensaver
  rhythmbox ttf-dustin gspot alacarte kdelibs-data gedit python-libxml2
  gnome-menus gtk2-engines-pixbuf gnome-office abiword-common libkdegames1
  python-numeric firestarter python-docutils boson-data python-roman
  python2.4-moinmoin screem gnome-control-center ipython hplip gconf2
  libbonoboui2-0 python2.4-samba ubuntu-desktop metacity-common boson-music
  librrd2 libgnome2-perl liblualib50 python-apt python-virtkey
  gnome-pilot-conduits python-subversion python2.4-id3lib mesa-common-dev
  mgetty-fax python-dev thunderbird-locale-en-gb python-gconf liberror-perl
  gnome-pilot libedata-cal1.2-6 python2.4-semanage gnumeric-common
  update-notifier python-mechanize apport libsasl2-dev python2.4-dictdlib
  gnome-media-common nautilus-data libgnome-menu2 python2.4 python-pullparser
  gstreamer0.10-plugins-good gnome-terminal language-support-en libwavpack0
  language-support-es python-clientcookie startupmanager dolphin netspeed
  language-support-sv libpanel-applet2-0 libgnome2.0-cil python-gtkhtml2
  gnome-utils gnome-themes-extras beryl-manager heliodor-dbg libhesiod0
  heliodor-dev python-gd gnome-btdownload gdm-themes gnome-orca python-qt3
  fast-user-switch-applet blt xvncviewer libgnome2-common gnome-about
  hwdb-client-common gnome-volume-manager dia-gnome nautilus-cd-burner
  glunarclock python-tz beryl-settings eog gdm capplets-data
  libgnome2-vfs-perl libavahi-qt3-1 boson python-glade2 python-uno
  gnome-backgrounds python python-sip4 expect python-xdg gnome-spell
  amarok-xine bug-buddy launchpad-integration python-vte unattended-upgrades
  bittorrent language-selector python-ctypes libgnomeui-0 gnome-doc-utils
  alsa-utils python-xml openoffice.org libfile-tail-perl libecal1.2-7
  python-central python-twisted-conch amarok tsclient zope3 gaim vino
  python-dbus gnome-keyring-manager thunderbird-locale-es-ar
  gnome-system-monitor python-gnupginterface zope-common localechooser-data
  thunderbird-locale-es-es firefox-gnome-support ubuntu-minimal evince
  gnome-games-data libgtk2-gladexml-perl libtunepimp3 python2.4-pypoker-eval
  gnome-app-install libifp4 libebook1.2-9 evolution-plugins libgoffice-0-3
  gtkhtml3.8 libedataserverui1.2-8 contact-lookup-applet
  libgnome-window-settings1 libmetacity0 music-applet
  python-launchpad-integration libedata-book1.2-2 openoffice.org-help-de
  evolution-data-server libgnomevfs2-bin openoffice.org-help-es
  libgnomevfs2-extra liblpint-bonobo0 python-setuptools yelp libgl1-mesa-dev
  python2.4-gamin openoffice.org-help-sv synaptic gksu gnome-main-menu
  libeel2-2 python-gdbm gnome-core dia-common gnome-netstatus-applet
  gnome-applets-dbg tk8.4 language-selector-common gnome-applets-dev
  hal-device-manager kbattleship gnome-terminal-data librrds-perl
  libgucharmap5 onboard libgksu2-0 gnome-applets gnumeric
  libgstreamer-plugins0.8-0 totem-xine libgnome2-gconf-perl python-gmenu
  heliodor gconf-editor libzephyr3 libtotem-plparser1 gnome-system-tools
  libgnomebt0 python2.4-opencv gnome-panel openoffice.org-help-en-gb liblua50
  gtk2-engines-spherecrystal gstreamer0.10-gnomevfs totem deskbar-applet
  python-gnome2-desktop libnautilus-extension1 greenwich
  openoffice.org-help-en-us childsplay-plugins gnome gnome-applets-data
  apport-gtk childsplay-alphabet-sounds-de inkscape gnome-session
  libgnome-desktop-2 python-reportlab libgail-gnome-dbg python-twisted-bin
  lsb-release python-gtk2 beryl totem-mozilla python-cairo libnjb5 libgdl-1-0
  mgetty gimp-python file-roller serpentine nautilus-sendto gnome-cups-manager
  gnome-panel-data sound-juicer hwdata python-gobject libgnomevfs2-common
  libgdl-1-common netapplet thunderbird-locale-sv-se
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  abiword-gnome alacarte alsa-utils amarok amarok-xine apport apport-gtk beryl
  beryl-manager beryl-settings beryl-settings-bindings bittorrent bluefish
  boson boson-base boson-data boson-music bug-buddy camorama capplets-data
  childsplay childsplay-alphabet-sounds-de childsplay-plugins
  contact-lookup-applet deskbar-applet dia-common dia-gnome dia-libs dolphin
  ekiga eog evince evolution evolution-data-server evolution-exchange
  evolution-plugins evolution-webcal f-spot fast-user-switch-applet
  file-roller firefox-gnome-support firestarter gaim gcalctool gconf-editor
  gconf2 gdebi gdm gdm-themes gedit gimp-python giplet gksu glunarclock gnome
  gnome-about gnome-app-install gnome-applets gnome-applets-data
  gnome-applets-dbg gnome-applets-dev gnome-btdownload gnome-control-center
  gnome-core gnome-cups-manager gnome-desktop-environment gnome-doc-utils
  gnome-games gnome-games-data gnome-keyring-manager gnome-main-menu
  gnome-media gnome-media-common gnome-menus gnome-netstatus-applet
  gnome-nettool gnome-office gnome-orca gnome-panel gnome-panel-data
  gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver
  gnome-session gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-utils gnome-volume-manager gnumeric
  greenwich gspot gstreamer0.10-gnomevfs gstreamer0.10-plugins-good
  gstreamer0.8-misc gthumb gtkhtml3.8 gucharmap hal-device-manager heliodor
  heliodor-dbg heliodor-dev hplip hwdb-client-common hwdb-client-gnome
  inkscape ipython kbattleship kdelibs4c2a language-selector
  language-selector-common language-support-en language-support-es
  language-support-sv launchpad-integration libapache2-mod-python2.4
  libbonoboui2-0 libcamel1.2-8 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libexchange-storage1.2-2
  libgail-gnome-dbg libgail-gnome-module libgdl-1-0 libgdl-1-common libgksu2-0
  libgnome-desktop-2 libgnome-media0 libgnome-menu2 libgnome-window-settings1
  libgnome2-0 libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnome2.0-cil libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra
  libgoffice-0-3 libgsf-gnome-1-114 libgstreamer-gconf0.8-0 libgtkhtml3.8-15
  libgucharmap5 libkdegames1 liblaunchpad-integration0 liblpint-bonobo0
  libmetacity0 libnautilus-extension1 libpanel-applet2-0 libtotem-plparser1
  lsb-release metacity metacity-common music-applet nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto netapplet netspeed
  notification-daemon onboard openoffice.org openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-de openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-help-es openoffice.org-help-sv
  openoffice.org-writer planner python python-apport-utils python-apt
  python-at-spi python-cairo python-central python-clientcookie
  python-clientform python-crypto python-ctypes python-dbus python-dev
  python-docutils python-gconf python-gd python-gdbm python-glade2
  python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras
  python-gnomecanvas python-gnupginterface python-gobject python-gst0.10
  python-gtk2 python-gtkhtml2 python-launchpad-integration python-libxml2
  python-mechanize python-numeric python-pullparser python-pygame python-qt3
  python-reportlab python-roman python-setuptools python-sip4
  python-subversion python-support python-twisted-bin python-twisted-conch
  python-twisted-core python-twisted-web2 python-tz python-uno python-virtkey
  python-vte python-xdg python-xml python-zopeinterface python2.4
  python2.4-configlet python2.4-dbg python2.4-dev python2.4-dictclient
  python2.4-dictdlib python2.4-examples python2.4-gamin python2.4-gd
  python2.4-id3lib python2.4-librdf python2.4-moinmoin python2.4-opencv
  python2.4-paramiko python2.4-pypoker-eval python2.4-samba
  python2.4-schoolbell python2.4-semanage python2.4-speex resapplet rhythmbox
  screem sensors-applet serpentine sound-juicer startupmanager synaptic
  system-config-kickstart thunderbird-locale-en-gb thunderbird-locale-es-ar
  thunderbird-locale-es-es thunderbird-locale-sv-se tomboy totem totem-mozilla
  totem-xine tsclient ubuntu-desktop ubuntu-minimal unattended-upgrades
  update-manager update-notifier vino wallpaper-tray yelp zope-common zope3
0 upgraded, 0 newly installed, 281 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0B of archives.
After unpacking 934MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


```

---

### Post by BDwinsAlt on 2007-04-13
Bump... :confused:

---

### Post by AbieSwanepoel on 2007-04-15
Can you please provide a bit of background?

What distro are you using?
Why do you want to reinstall/remove Python? 
What events lead up to the point that made you decide to reinstall python?


Python is used extensively in Ubuntu so you don't miss the mark with your satement "How can I reinstall python without it conflicting with my ENTIRE system".

Depending on the distro you are using it can be almost impossible to remove Python2.4.

You can try to reinstall/fix it from Synaptic.

If you just wanted to install a later version of Python (e.g. 2.5) then you could install it alongside 2.4. The system packages are dependent on a specific version of Python (2.3, 2.4 or 2.5 depending on your distro) but you can install another version as well if you want to write Python programs for it.

---

### Post by FRuMMaGe on 2007-04-17
I have the same problem :(

---

