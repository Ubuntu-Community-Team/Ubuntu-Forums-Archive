---
title: "Need help enabling/installing Crystal HD"
date: 2017-08-21
forum: Installation &amp; Upgrades
---

### Post by flamingfox on 2017-08-21
Hello,

So recently, I have been tasked with trying to revive my Aspire One notebook, since Windows 10 doesn't support Crystal HD. So in an attempt to make the notebook as lightweight as possible (in case I might want to make it into a PVR), I have installed Lubuntu 17.04.

I have attempted to install the Crystal HD drivers from [https://github.com/dbason/crystalhd](https://github.com/dbason/crystalhd), but I have run into a problem with the first command line:
```
master@Attis:~$ sudo apt-get install checkinstall git-core autoconf build-essential subversion dpkg-dev fakeroot pbuilder build-essential dh-make debhelper devscripts patchutils quilt git-buildpackage pristine-tar git yasm zlib1g-dev zlib-bin libzip-dev libx11-dev libx11-dev libxv-dev vstream-client-dev libgtk2.0-dev libpulse-dev libxxf86dga-dev x11proto-xf86dga-dev git libgstreamermm-0.10-dev libgstreamer0.10-dev automake libtool python-appindicator
[sudo] password for master: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zlib-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  minizip:i386 minizip

E: Package 'zlib-bin' has no installation candidate
E: Unable to locate package libgstreamermm-0.10-dev
E: Couldn't find any package by glob 'libgstreamermm-0.10-dev'
E: Couldn't find any package by regex 'libgstreamermm-0.10-dev'
E: Unable to locate package libgstreamer0.10-dev
E: Couldn't find any package by glob 'libgstreamer0.10-dev'
E: Couldn't find any package by regex 'libgstreamer0.10-dev'
master@Attis:~$
``` 

I can't proceed with the installation if I don't have the necessary requirements yet, so I am stuck right now. Any ideas how to fix this?

Thanks in advance,

FlamingFox

---

### Post by wyliecoyoteuk on 2017-08-21
Have got the universe repo enabled?

sudo add-apt-repository universe

---

### Post by flamingfox on 2017-08-21
```
master@Attis:~$ sudo add-apt-repository universe
[sudo] password for master: 
'universe' distribution component is already enabled for all sources.
```

Already setup apparently...

---

### Post by flamingfox on 2017-08-30
Never mind... somehow by manually installing all the required packages via the Package Manager, I have successfully got CrystalHD to work.

---

