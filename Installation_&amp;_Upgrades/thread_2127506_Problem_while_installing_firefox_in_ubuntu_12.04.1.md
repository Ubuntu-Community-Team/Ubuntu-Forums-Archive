---
title: "Problem while installing firefox in ubuntu 12.04.1"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by gauravjain on 2013-03-20
Hi.. I am installing firefox but getting this error, HOw to solve this ? I think this is because i removed squid but not completely.  And somebody please suggest me good article or blog to install squid proxy server on my ubuntu. As i have only 1 NIC so how to route whole traffic from it. I tried installing squid once but i could not able to access squid main page. So i removed. But then in can't even install firefox.

 root@gsursv:~# apt-get install firefoxReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu-xdg python-gnome2 libpurple0 xdg-user-dirs-gtk telepathy-indicator
  tomboy ekiga python-notify libgsf-1-common libopal3.10.2 python-pyorbit
  libmtp9 libmono-addins-gui0.2-cil gedit-common gcalctool fonts-liberation
  telepathy-logger xserver-xorg-video-all gir1.2-rb-3.0 libgtksourceview-3.0-0
  lp-solve gnome-backgrounds libpth20 libunique-1.0-0 xserver-xorg-video-ati
  gnome-media telepathy-gabble gnome-search-tool aisleriot libgdict-common
  gtali libpurple-bin python-numpy xfonts-encodings baobab python-mako
  libmono-corlib4.0-cil glchess libdmapsharing-3.0-2 rhythmbox-data
  libxcb-dri2-0 libmeanwhile1 gnome-applets libgnomecanvas2-0 poppler-utils
  libmono-system-security4.0-cil hamster-applet xserver-xorg-video-openchrome
  libraw5 libmono-cairo4.0-cil gnome-system-log gucharmap libdiscid0
  gnome-games link-grammar-dictionaries-en libmtp-runtime gnome-panel-data
  cheese gdebi libpangomm-1.4-1 libots0 linux-headers-3.2.0-29 libgnomeui-0
  xserver-xorg-video-mga libgpod-common gnobots2 libmono-system-xml4.0-cil
  libgucharmap-2-90-7 python-reportlab libmono-i18n-west4.0-cil
  libgtkmm-2.4-1c2a gnome-disk-utility odbcinst1debian2 unzip
  libmono-system-drawing4.0-cil gnome-icon-theme-extras xserver-xorg-core
  cli-common xserver-xorg-video-mach64 libmono-sharpzip4.84-cil rhythmbox
  liblaunchpad-integration1.0-cil linux-headers-3.2.0-29-generic
  telepathy-haze alacarte gedit python-imaging xserver-common libgexiv2-1
  empathy-common gnome-system-monitor libcheese-gtk21 gnome-terminal
  xserver-xorg-video-trident libgupnp-1.0-4 libmono-posix4.0-cil abiword
  xserver-xorg-video-sis libboost-signals1.46.1 gnome-sudoku abiword-common
  libindicate-gtk3 transmission-gtk lightsoff xserver-xorg-video-qxl
  libcheese3 telepathy-idle guile-1.8-libs seahorse libmagick++4 empathy
  libboost-program-options1.46.1 libwps-0.2-2 python-uniconvertor
  libgdict-1.0-6 libmono-system-core4.0-cil xserver-xorg-video-siliconmotion
  gdebi-core libcapi20-3 python-lxml libmono-system-configuration4.0-cil
  libgoffice-0.8-8-common vinagre xserver-xorg-input-vmmouse
  librhythmbox-core5 odbcinst xfonts-utils mono-runtime libdbus1.0-cil
  telepathy-salut liblapack3gf xserver-xorg-video-savage libgpod4
  libmono-addins0.2-cil gnibbles libappindicator0.1-cil python-renderpm
  xserver-xorg-video-tdfx libfarstream-0.1-0 gnuchess-book gnome-nettool
  libgtk-vnc-2.0-0 transmission-common libglibmm-2.4-1c2a gnome-screenshot
  shotwell unixodbc ttf-lyx libpt2.10.2 browser-plugin-gnash python-gmenu
  libwnck22 gnome-games-extra-data libgoffice-0.8-8 xserver-xorg-video-intel
  libxfont1 libnice10 libindicator7 abiword-plugin-grammar libgdu-gtk0
  xserver-xorg-input-all libmtdev1 libcairomm-1.0-1 simple-scan libgtkspell0
  liblink-grammar4 gnash-common xserver-xorg-video-vmware libsdl1.2debian
  swell-foop fonts-cantarell xserver-xorg-video-r128 libavahi-ui-gtk3-0
  libcluttergesture-0.0.2-0 gdm libgmime2.6-cil xfonts-base
  xserver-xorg-input-evdev gnotski mono-4.0-gac libwv-1.2-4 libgif4
  gir1.2-gtksource-3.0 libdbus-glib1.0-cil xserver-xorg-video-vesa libgdome2-0
  libgtkmm-3.0-1 libgtksourceview-3.0-common gir1.2-gucharmap-2.90
  libcolamd2.7.1 mono-gac libclutter-imcontext-0.1-0 libwpd-0.9-9
  gnome-applets-data libgsf-1-114 gir1.2-gst-plugins-base-0.10 rdesktop
  cheese-common sound-juicer vino libneon27-gnutls libminiupnpc8
  xserver-xorg-video-s3 xserver-xorg libxatracker1 libglib2.0-cil
  gnome-terminal-data libgtkmathview0c2a libtelepathy-farstream2 iagno glines
  libboost-thread1.46.1 xserver-xorg-video-fbdev xserver-xorg-input-wacom
  libgconf2.0-cil abiword-plugin-mathview libgnome-media-profiles-3.0-0
  rhythmbox-mozilla libunique-3.0-0 xserver-xorg-video-nouveau libmx-1.0-2
  libblas3gf xserver-xorg-video-neomagic gnome-dictionary
  xserver-xorg-input-mouse gedit-plugins gnumeric-common libappindicator1
  libperl5.14 libgnomeui-common liferea libexiv2-11 libmtp-common
  libgupnp-igd-1.0-4 gnash rhythmbox-plugin-zeitgeist libxvmc1
  gnome-desktop-data zip gnotravex gnect libbonoboui2-0 libwnck-common
  libclutter-gst-1.0-0 quadrapassel media-player-info mahjongg gnumeric
  libgvnc-1.0-0 libgfortran3 libgpgme11 libart-2.0-2 python-markupsafe
  gnome-games-data libmusicbrainz3-6 liblaunchpad-integration1 libzephyr4
  libmusicbrainz4-3 xserver-xorg-video-sisusb liferea-data libmono-i18n4.0-cil
  python-wnck gir1.2-webkit-3.0 libwpg-0.2-2 gnome-panel libgnome-menu2
  libabiword-2.9 xserver-xorg-video-radeon gnuchess libodbc1 libgtk2.0-cil
  xserver-xorg-video-cirrus gstreamer0.10-nice libbonoboui2-common
  libloudmouth1-0 gnome-font-viewer perlmagick rhythmbox-plugin-cdrecorder
  inkscape rhythmbox-plugins gir1.2-panelapplet-4.0 dconf-tools python-gconf
  xserver-xorg-input-synaptics libmono-security4.0-cil libgssdp-1.0-3
  libtidy-0.99-0 nautilus-sendto-empathy gnumeric-doc
  gir1.2-javascriptcoregtk-3.0 libgnomecanvas2-common file-roller libgdiplus
  libclutter-gtk-1.0-0 gnome-video-effects libatkmm-1.6-1
  python-reportlab-accel libgdome2-cpp-smart0c2a gnomine libmono-system4.0-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-globalmenu xul-ext-ubufox
Suggested packages:
  latex-xft-fonts firefox-gnome-support
The following NEW packages will be installed:
  firefox firefox-globalmenu xul-ext-ubufox
0 upgraded, 3 newly installed, 0 to remove and 199 not upgraded.
2 not fully installed or removed.
Need to get 24.3 MB of archives.
After this operation, 54.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main firefox amd64 19.0.2+build1-0ubuntu0.12.04.1 [24.2 MB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main firefox-globalmenu amd64 19.0.2+build1-0ubuntu0.12.04.1 [50.3 kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main xul-ext-ubufox all 2.6-0ubuntu0.12.04.1 [58.5 kB]
Fetched 24.3 MB in 3min 30s (116 kB/s)                                         
Selecting previously unselected package firefox.
(Reading database ... 182594 files and directories currently installed.)
Unpacking firefox (from .../firefox_19.0.2+build1-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package firefox-globalmenu.
Unpacking firefox-globalmenu (from .../firefox-globalmenu_19.0.2+build1-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package xul-ext-ubufox.
Unpacking xul-ext-ubufox (from .../xul-ext-ubufox_2.6-0ubuntu0.12.04.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up squid3 (3.1.19-1ubuntu3.12.04.2) ...
Creating Squid HTTP proxy 3.x spool directory structure
2013/03/20 17:51:12| cache_cf.cc(381) parseOneConfigFile: squid.conf:1145 unrecognized: 'The'
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of squid:
 squid depends on squid3; however:
  Package squid3 is not configured yet.
dpkg: error processing squid (--configure):
 dependency problems - leaving unconfigured
Setting up firefox (19.0.2+build1-0ubuntu0.12.04.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (19.0.2+build1-0ubuntu0.12.04.1) ...
Setting up xul-ext-ubufox (2.6-0ubuntu0.12.04.1) ...
Errors were encountered while processing:
 squid3
 squid
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ibjsb4 on 2013-03-20
Looks like its still trying to configure squid.  Try a house cleaning.

```
sudo apt-get clean
sudo apt-get autoremove
sudo rm /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by gauravjain on 2013-03-21
root@gaurav:~# **apt-get clean**
root@gaurav:~# **apt-get autoremove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up squid3 (3.1.19-1ubuntu3.12.04.2) ...
Creating Squid HTTP proxy 3.x spool directory structure
2013/03/21 14:15:12| cache_cf.cc(381) parseOneConfigFile: squid.conf:1145 unrecognized: 'The'
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of squid:
 squid depends on squid3; however:
  Package squid3 is not configured yet.
dpkg: error processing squid (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 squid3
 squid
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@gaurav:~# **rm /var/lib/apt/lists/***
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
root@indies-server:~# **apt-get update **
After downloaded 26.3 MB it shows this, 
Fetched 26.3 MB in 1min 44s (252 kB/s)                                         
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://download.opensuse.org](http://download.opensuse.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 977C43A8BA684223
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)

---

### Post by gauravjain on 2013-03-21
And After run all the commands first time, Gedit also removed, And when i try to reinstall it, It shows following,
root@gaurav:~# apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gedit-common gir1.2-gtksource-3.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common
The following NEW packages will be installed:
  gedit gedit-common gir1.2-gtksource-3.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common
0 upgraded, 5 newly installed, 0 to remove and 168 not upgraded.
2 not fully installed or removed.
Need to get 1,373 kB of archives.
After this operation, 9,838 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main libgtksourceview-3.0-common all 3.4.2-0ubuntu1 [168 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main libgtksourceview-3.0-0 amd64 3.4.2-0ubuntu1 [196 kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-gtksource-3.0 amd64 3.4.2-0ubuntu1 [15.9 kB]
Get:4 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise/main gedit-common all 3.4.1-0ubuntu1 [166 kB]
Get:5 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise/main gedit amd64 3.4.1-0ubuntu1 [827 kB]
Fetched 1,373 kB in 6s (211 kB/s)                                              
Selecting previously unselected package libgtksourceview-3.0-common.
(Reading database ... 131025 files and directories currently installed.)
Unpacking libgtksourceview-3.0-common (from .../libgtksourceview-3.0-common_3.4.2-0ubuntu1_all.deb) ...
Selecting previously unselected package libgtksourceview-3.0-0.
Unpacking libgtksourceview-3.0-0 (from .../libgtksourceview-3.0-0_3.4.2-0ubuntu1_amd64.deb) ...
Selecting previously unselected package gir1.2-gtksource-3.0.
Unpacking gir1.2-gtksource-3.0 (from .../gir1.2-gtksource-3.0_3.4.2-0ubuntu1_amd64.deb) ...
Selecting previously unselected package gedit-common.
Unpacking gedit-common (from .../gedit-common_3.4.1-0ubuntu1_all.deb) ...
Selecting previously unselected package gedit.
Unpacking gedit (from .../gedit_3.4.1-0ubuntu1_amd64.deb) ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up squid3 (3.1.19-1ubuntu3.12.04.2) ...
Creating Squid HTTP proxy 3.x spool directory structure
2013/03/21 14:28:59| cache_cf.cc(381) parseOneConfigFile: squid.conf:1145 unrecognized: 'The'
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of squid:
 squid depends on squid3; however:
  Package squid3 is not configured yet.
dpkg: error processing squid (--configure):
 dependency problems - leaving unconfigured
Setting up libgtksourceview-3.0-common (3.4.2-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up libgtksourceview-3.0-0 (3.4.2-0ubuntu1) ...
Setting up gir1.2-gtksource-3.0 (3.4.2-0ubuntu1) ...
Setting up gedit-common (3.4.1-0ubuntu1) ...
Setting up gedit (3.4.1-0ubuntu1) ...
update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 squid3
 squid
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by gauravjain on 2013-03-26
Nobody has a solution of my problem, Please help me it may big problem for me.

---

### Post by vasa1 on 2013-03-26
Just curious but please explain why you're **root**? And *The following packages were automatically installed and are no longer required:* in your first post seemed to want to delete quite a lot of stuff that seems fundamental to the OS.

---

