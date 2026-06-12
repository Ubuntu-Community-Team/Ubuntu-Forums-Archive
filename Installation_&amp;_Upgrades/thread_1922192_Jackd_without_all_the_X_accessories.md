---
title: "Jackd without all the X accessories?"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by mangodan2003 on 2012-02-08
I'm trying to build a minimal system - i have debootstrapped oneiric.

The system needs jackd - however when i go to install it it has a whopping great list (see below) of things its going to pull in which i do not want. Is there anyway to get around this?

I had a previous version of this system based on Gentoo and had manually crafted a rootfs to below 100meg by picking all the libs and binaries I needed - however as needs grew this became impracticable without a package manager system hence starting over with ubuntu.


Basically I have no need for any of the GUI related things, qt libraries etc. I just want the jack libraries,  server and associated cli counter parts.


> 
root@localhost:/home/rt# apt-get install jackd1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fontconfig fontconfig-config jackd jackd1-firewire libasyncns0 libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 libconfig++8
  libcups2 libffado2 libflac8 libfontconfig1 libice6 libiec61883-0 libjpeg62 libjson0 liblcms1 libmng1 libpulse0 libqt4-dbus
  libqt4-declarative libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraw1394-11
  libsamplerate0 libsm6 libsndfile1 libtiff4 libvorbisenc2 libx11-xcb1 libxi6 libxrender1 libxt6 libxtst6 pulseaudio-utils qdbus qjackctl
  ttf-dejavu-core x11-common
Suggested packages:
  defoma jack-tools meterbridge nas cups-common liblcms-utils pulseaudio libqt4-declarative-folderlistmodel libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer libqt4-dev qt4-qtconfig libraw1394-doc avahi-daemon
The following NEW packages will be installed:
  fontconfig fontconfig-config jackd jackd1 jackd1-firewire libasyncns0 libaudio2 libavahi-client3 libavahi-common-data libavahi-common3
  libconfig++8 libcups2 libffado2 libflac8 libfontconfig1 libice6 libiec61883-0 libjpeg62 libjson0 liblcms1 libmng1 libpulse0 libqt4-dbus
  libqt4-declarative libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraw1394-11
  libsamplerate0 libsm6 libsndfile1 libtiff4 libvorbisenc2 libx11-xcb1 libxi6 libxrender1 libxt6 libxtst6 pulseaudio-utils qdbus qjackctl
  ttf-dejavu-core x11-common
0 upgraded, 48 newly installed, 0 to remove and 0 not upgraded.



---

### Post by mangodan2003 on 2012-09-28
bump

---

