---
title: "Edgy To Feisty Upgrade Failed"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by TheOz on 2007-01-14
I've tried to Upgrade my Edgy to Feisty with [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mirror but
when i try to run: apt-get dist-upgrade
This error appears:
E: Internal Error, Could not perform immediate configuration (2) on python-minimal

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  apache2-common gimp-python libvolumeid0 python-apport-utils ubuntu-desktop
The following NEW packages will be installed:
  apache2.2-common avahi-autoipd boo evolution-common feisty-gdm-themes
  feisty-session-splashes feisty-wallpapers genisoimage gnome-cards-data
  gnome-mount gpgv libapr1 libaprutil1 libcaca0 libcamel1.2-10 libcdaudio1
  libcucul0 libdb4.2 libdirectfb-0.9-25 libdns22 libedataserver1.2-9
  libegroupwise1.2-13 libexchange-storage1.2-3 libfreebob0 libgnomekbd-common
  libgnomekbd1 libgnomekbdui1 libicu36 libjaxp1.3-java liblua50 liblualib50
  libmodplug0c2 libneon26 libnm-glib0 libnss-mdns liboobs-1-3 libopenobex1
  libpq4 libsasl2-2 libslab0 libsoundtouch1c2 libsvn1 libvolume-id0
  libwavpack1 libxcomposite1 libxine1 libxine1-ffmpeg libxvmc1
  linux-headers-2.6.20-5 linux-headers-2.6.20-5-386
  linux-headers-2.6.20-5-generic linux-image-2.6.20-5-generic
  linux-restricted-modules-2.6.20-5-generic python-apport python2.5
  python2.5-minimal update-inetd wodim
The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2-utils apport apport-gtk banshee
  bind9-host bittorrent bug-buddy capplets-data cdrecord contact-lookup-applet
  cupsys-bsd cupsys-client deskbar-applet dnsutils dvd+rw-tools ekiga
  evolution evolution-data-server evolution-data-server-common
  evolution-exchange evolution-plugins evolution-webcal gnome-applets
  gnome-applets-data gnome-control-center gnome-games gnome-games-data
  gnome-mag gnome-menus gnome-orca gnome-panel gnome-panel-data gnome-session
  gnome-system-tools gnome-volume-manager gnupg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-good hal hplip hplip-data hwdb-client-common
  libapache2-mod-php5 libbind9-0 libbtctl4 libcamel1.2-8 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8
  libexchange-storage1.2-2 libgnome-window-settings1 libisccfg1
  libjack0.100.0-0 libopal-2.2.0 libsasl2 libsasl2-modules libsdl1.2debian
  libsdl1.2debian-alsa libxalan2-java libxerces2-java libxine-extracodecs
  liferea liferea-mozilla linux-headers-386 linux-headers-generic
  linux-image-generic linux-restricted-modules-generic mkisofs nautilus-sendto
  nvidia-glx openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-default
  openoffice.org-style-industrial openoffice.org-writer php5 php5-common
  python python-gmenu python-minimal python-uno python-vte subversion
  ubuntu-artwork udev update-manager volumeid
103 upgraded, 58 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B/217MB of archives.
After unpacking 235MB of additional disk space will be used.
Do you want to continue [Y/n]? 
E: Internal Error, Could not perform immediate configuration (2) on python-minimal

```

---

### Post by Iarwain ben-adar on 2007-01-14
Well,
if i were you, i'd wait untill the transition to python2.5 is done (i suggest you wait until wednesday or so).


Iarwain

---

### Post by allyourzigg on 2007-01-15
I have the same problem when trying to dist-upgrade, do you think it really will take to wendsday to fix? Is there some temporary work-around?

---

### Post by Iarwain ben-adar on 2007-01-16
Wednesday was just a guess from my side :D

You can try to upgrade now if you'd like,
should work :cool:


Iarwain

---

