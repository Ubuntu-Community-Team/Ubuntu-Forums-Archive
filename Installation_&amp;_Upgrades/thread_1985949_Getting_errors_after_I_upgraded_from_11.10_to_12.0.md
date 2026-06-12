---
title: "Getting errors after I upgraded from 11.10 to 12.04"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by mnshsnghl on 2012-05-24
Hi,
   While I was updating from 11.10 to 12.04, I started getting following problems, and no matter what I do, these problems are not going away :

$ apt-get install -f 
Script started on Thursday 24 May 2012 11:17:40 AM IST
root@ms-lnx:/etc/apt# apt-get install -f
Reading package lists... 0%Reading package lists... 0%Reading package lists... 2%Reading package lists... Done
Building dependency tree... 0%Building dependency tree... 0%Building dependency tree... 0%Building dependency tree... 50%Building dependency tree... 50%Building dependency tree       
Reading state information... 0%Reading state information... 0%Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kalzium-data libopenbabel4 kdeartwork-style kdeartwork-theme-window
  libktorrent-l10n ktux swh-plugins ktorrent-data kde-workspace-data
  libqapt-runtime pkg-kde-tools xplanet translate-toolkit libcfitsio3
  gstreamer0.10-fluendo-mp3:i386 plasma-active-data libgrantlee-gui0 libkleo4
  ttf-dustin plasma-widgets-active startactive-ksplash-theme advancecomp
  python-levenshtein libboost-python1.46.1 libavogadro1 libqtmultimediakit1
  libdeclarative-multimedia libpoppler-qt4-3 libindi-data fortune-mod libcln6
  libkwineffects1abi3 libboost-graph1.46.1 libnova-0.12-2 libkmanagesieve4
  librecode0 python-avogadro valgrind avogadro-data libksgrd4 python-enchant
  libkpgp4 kde-runtime-data libqapt1 fortunes shared-desktop-ontologies
  kdoctools libkdecorations4 libqimageblitz4 python-vobject libksieve4
  libqtruby4shared2 kde-baseapps-data python-qt4-sql libdrm-nouveau1a:i386
  icoutils share-like-connect libqtwebkit-qmlwebkitplugin kstars-data libao4
  libkdgantt2 kde-workspace-kgreet-plugins kgeography-data libgrantlee-core0
  libksignalplotter4 libindi0 ksysguardd libkscreensaver5 vorbis-tools poxml
  share-like-connect-data parley-data libkwinglesutils1 kdesdk-scripts
  fortunes-min startactive-data libqalculate5 xplanet-images liboil0.3:i386
  kdelibs5-data ktouch-data kdewallpapers kdesdk-strigi-plugins klettres-data
  ruby-qt4 kdeartwork-emoticons libsolidcontrolifaces4abi2 libktorrent3
  python-iniparse ruby-qt4-webkit kalgebra-common kdenetwork-filesharing
  libprocessui4a oxygen-cursor-theme optipng kde-artwork-active
  libsolidcontrol4abi2 libllvm3.0 libllvm3.0:i386 libkwinnvidiahack4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libgcrypt11
Suggested packages:
  rng-tools
The following packages will be upgraded:
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libgcrypt11
3 upgraded, 0 newly installed, 0 to remove and 147 not upgraded.
23 not fully installed or removed.
Need to get 0 B/331 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libgcrypt11 (--configure):
 libgcrypt11:amd64 1.5.0-3 cannot be configured because libgcrypt11:i386 is in a different version (1.5.0-3ubuntu0.1)
dpkg: error processing libgcrypt11:i386 (--configure):
 libgcrypt11:i386 1.5.0-3ubuntu0.1 cannot be configured because libgcrypt11:amd64 is in a different version (1.5.0-3)
dpkg: error processing libdrm-nouveau2:i386 (--configure):
 libdrm-nouveau2:i386 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise cannot be configured because libdrm-nouveau2:amd64 is in a different version (2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise)
dpkg: error processing libdrm-nouveau2 (--configure):
 libdrm-nouveau2:amd64 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise cannot be configured because libdrm-nouveau2:i386 is in a different version (2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise)
dpkg: error processing libdrm-radeon1:i386 (--configure):
 libdrm-radeon1:i386 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise cannot be configured because libdrm-radeon1:amd64 is in a different version (2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise)
dpkg: error processing libdrm-radeon1 (--configure):
 libdrm-radeon1:amd64 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise cannot be configured because libdrm-radeon1:i386 is in a different version (2.4.34+git20120512.e07b6506-0ubuntu0rNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
icotz~precise)
dpkg: dependency problems prevent configuration of libdrm-dev:
 libdrm-dev depends on libdrm-radeon1 (= 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise); however:
  Package libdrm-radeon1 is not configured yet.
 libdrm-dev depends on libdrm-nouveau2 (= 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise); however:
  Package libdrm-nouveau2 is not configured yet.
dpkg: error processing libdrm-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on libgcrypt11 (>= 1.4.5); however:
  Package libgcrypt11 is not configured yet.
dpkg: error processing xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-current:
 nvidia-current depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 nNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
vidia-current depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing nvidia-current (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin-otr:
 pidgin-otr depends on libgcrypt11 (>= 1.4.5); however:
  Package libgcrypt11 is not configured yet.
dpkg: error processing pidgin-otr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vino:
 vino depends on libgcrypt11 (>= 1.4.5); however:
  Package libgcrypt11 is not configured yet.
dpkg: error processing vino (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xephyr:
 xserver-xephyr depends on libgcrypt11 (>= 1.4.5); however:
  Package libgcrypt11 is not configured yet.
dpkg: error processing xserver-xephyr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problemNo apport report written because MaxReports is reached already
s prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics depends on xorg-input-abi-16; however:
  Package xorg-input-abi-16 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-16 is not configured yet.
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-input-synaptics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depends on xorg-input-abi-16; however:
  Package xorg-input-abi-16 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-16 is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-input-vmmouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-apm:
 xserver-xorg-video-apm depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 xserver-xorg-video-apm depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-apm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depends on libdrm-radeon1 (>= 2.4.31); however:
  Package libdrm-radeon1 is not configured yet.
 xserver-xorg-video-radeon depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 xserver-xorg-video-radeon depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-radeon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-ati:
 xserver-xorg-video-ati depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-radeon; however:
  Package xserver-xorg-video-radeon is not configured yet.
dpkg: error processing xserver-xorg-video-ati (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-cirrus:
 xserver-xorg-video-cirrus depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 xserver-xorg-video-cirrus depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-cirrus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-nouveau:
 xserver-xorg-video-nouveau depends on libdrm-nouveau2 (>= 2.4.33); however:
  Package libdrm-nouveau2 is not configured yet.
 xserver-xorg-video-nouveau depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 xserver-xorg-video-nouveau depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-nouveau (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-s3:
 xserver-xorg-video-s3 depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 xserver-xorg-video-s3 depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-s3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-s3virge:
 xserver-xorg-video-s3virge depends on xorg-video-abi-12; however:
  Package xorg-video-abi-12 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-12 is not configured yet.
 xserver-xorg-video-s3virge depends on xserver-xorg-core (>= 2:1.11.99); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-s3virge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xvfb:
 xvfb depends on libgcrypt11 (>= 1.4.5); however:
  Package libgcrypt11 is not configured yet.
dpkg: error processing xvfb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgcrypt11
 libgcrypt11:i386
 libdrm-nouveau2:i386
 libdrm-nouveau2
 libdrm-radeon1:i386
 libdrm-radeon1
 libdrm-dev
 xserver-xorg-core
 nvidia-current
 pidgin-otr
 vino
 xserver-xephyr
 xserver-xorg-input-synaptics
 xserver-xorg-input-vmmouse
 xserver-xorg-video-apm
 xserver-xorg-video-radeon
 xserver-xorg-video-ati
 xserver-xorg-video-cirrus
 xserver-xorg-video-intel
 xserver-xorg-video-nouveau
 xserver-xorg-video-s3
 xserver-xorg-video-s3virge
 xvfb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ms-lnx:/etc/apt# exit
exit

Script done on Thursday 24 May 2012 11:17:50 AM IST

---

### Post by dino99 on 2012-05-24
you should be not root to upgrade, its a very scary bad idea, log as your user.

then into /etc/apt/sources.list:
- comment out all non genuine entry (like ppa, ...)
- be sure to set only "precise" archive

save and exit

then run the cleaning scripts (clean, autoclean, autoremove)
and finally update again

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient and dont stop it before it end itself)

now you should be ready to upgrade

---

### Post by mörgæs on 2012-05-24
Agree on the root warning. Here is some background:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mnshsnghl on 2012-05-24
Thanks mate. I will keep in mind of not being the root again.
However, the issue is not yet solved. After I cleaned up my sources list, and did update, and did autoremove I got this :


$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libdrm-nouveau2 : Breaks: libdrm-nouveau2:i386 (!= 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise) but 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise is installed
 libdrm-nouveau2:i386 : Breaks: libdrm-nouveau2 (!= 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise) but 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise is installed
 libdrm-radeon1 : Breaks: libdrm-radeon1:i386 (!= 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise) but 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise is installed
 libdrm-radeon1:i386 : Breaks: libdrm-radeon1 (!= 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise) but 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise is installed
 libgcrypt11 : Breaks: libgcrypt11:i386 (!= 1.5.0-3) but 1.5.0-3ubuntu0.1 is installed
 libgcrypt11:i386 : Breaks: libgcrypt11 (!= 1.5.0-3ubuntu0.1) but 1.5.0-3 is installed
E: Unmet dependencies. Try using -f.

---

### Post by mörgæs on 2012-05-24
> **mnshsnghl said:**
> Thanks mate. I will keep in mind of not being the root again.
However, the issue is not yet solved. After I cleaned up my sources list, and did update, and did autoremove I got this :


$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**You might want to run 'apt-get -f install' to correct these.**
The following packages have unmet dependencies:
 libdrm-nouveau2 : Breaks: libdrm-nouveau2:i386 (!= 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise) but 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise is installed
 libdrm-nouveau2:i386 : Breaks: libdrm-nouveau2 (!= 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise) but 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise is installed
 libdrm-radeon1 : Breaks: libdrm-radeon1:i386 (!= 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise) but 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise is installed
 libdrm-radeon1:i386 : Breaks: libdrm-radeon1 (!= 2.4.34+git20120512.e07b6506-0ubuntu0ricotz~precise) but 2.4.34+git20120520.481234f2-0ubuntu0ricotz~precise is installed
 libgcrypt11 : Breaks: libgcrypt11:i386 (!= 1.5.0-3) but 1.5.0-3ubuntu0.1 is installed
 libgcrypt11:i386 : Breaks: libgcrypt11 (!= 1.5.0-3ubuntu0.1) but 1.5.0-3 is installed
E: Unmet dependencies. Try using -f.

:)

---

### Post by f_padia on 2012-05-24
Im getting these errors

```

The following packages have unmet dependencies.
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.5.3-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
 libreoffice-calc : Depends: libreoffice-core (= 1:3.5.3-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
 libreoffice-common : Breaks: libreoffice-core (< 1:3.5~) but 1:3.4.4-0ubuntu1 is installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.5.3-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.5.3-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.5.3-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.5.3-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.5.3-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.5.3-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

all libreoffice related, but I cant uninstall libreoffice 1:3.4.4-0ubuntu1. can anyone suggest anything? I have tried apt-get clean and dpkg reconfigure and a few other things but nothing has worked so far

---

### Post by mnshsnghl on 2012-05-25
> **mörgæs said:**
> :)

I stuck myself to the buntu I already had, ie. Ubuntu. Also went through all the solutions posted in your other link, nothing worked :(

Thanks.

---

