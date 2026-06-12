---
title: "Broken package manager on upgrade to Precise"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by simgrant on 2012-06-23
Hi all,

 I got broken packages after upgrading to Precise. Here is what happens when I try to "sudo apt-get -f install"


```
simon@simgrant:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  telepathy-indicator libaccess-bridge-java fonts-horai-umefont lib32ncurses5
  libaudiofile-dev lib32tinfo5 libiso9660-7 libtotem0 lib32ffi6
  gir1.2-totem-1.0 libindicator6 libaccess-bridge-java-jni
  gir1.2-totem-plparser-1.0 libmatroska4 libesd0-dev libaudio-dev
  libjpeg62:i386 lib32ncursesw5 libnl3 libgtkspell3-0 libattica0 libgtkhex0
  libnatpmp1 icc-profiles-free libllvm2.9 libllvm2.9:i386 libaudiofile0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gstreamer0.10-plugins-good
The following NEW packages will be installed:
  gstreamer0.10-plugins-good
0 upgraded, 1 newly installed, 0 to remove and 117 not upgraded.
5 not fully installed or removed.
Need to get 0 B/1,952 kB of archives.
After this operation, 5,407 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 481923 files and directories currently installed.)
Unpacking gstreamer0.10-plugins-good (from .../gstreamer0.10-plugins-good_0.10.31-1ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/gstreamer0.10-plugins-good_0.10.31-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstautoconvert.so', which is also in package gstreamer0.10-plugins-bad 0.10.23-1~oneiric1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gstreamer0.10-plugins-good_0.10.31-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
simon@simgrant:~$ 
```



Here is a list of my sources:


```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra # disabled on upgrade to precise
deb-src [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra # disabled on upgrade to precise
# deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free # disabled on upgrade to precise
# deb-src [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free # disabled on upgrade to precise
```



I have tried everything I can think of to fix this short of doing a whole new installation.

Regards, Simgrant.

---

### Post by sunson565 on 2012-07-01
hello, did you manage to fix this problem ?

---

