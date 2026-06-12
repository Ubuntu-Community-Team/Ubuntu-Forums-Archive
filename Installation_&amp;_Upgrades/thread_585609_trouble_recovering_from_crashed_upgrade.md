---
title: "trouble recovering from crashed upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Ba66e77 on 2007-10-21
After a crashed upgrade, I'm having trouble trying to recover.  Running "apt-get update" reports a problem with dpkg.  Running the advised "dpkg --configure -a" results in a parse error in /var/lib/dpkg/status.  Full output is below.  What does this mean and how do I fix it?

barrett@barrett-desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Packages
Fetched 2B in 1s (2B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
barrett@barrett-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 29725 package `libc6':
 `triggers-pendi' is not allowed for third (status) word in `status' field

---

### Post by Ba66e77 on 2007-10-22
bump

---

### Post by Wobedraggled on 2007-10-22
Move the "status" file or rename it and rerun "dpkg --configure -a"

---

### Post by Ba66e77 on 2007-10-22
No joy

barrett@barrett-desktop:~$ sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory

This is the section it's complaining about:
  29724 Package: libc6
  29725 Status: install ok triggers-pending
  29726 Priority: required
  29727 Section: libs
  29728 Installed-Size: 10120
  29729 Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
  29730 Architecture: i386
  29731 Source: glibc
  29732 Version: 2.6.1-1ubuntu9
  29733 Provides: glibc-2.6-1
  29734 Depends: libgcc1
  29735 Suggests: locales, glibc-doc
  29736 Conflicts: libterm-readline-gnu-perl (<< 1.15-2), tzdata (<< 2007e-2)
  29737 Conffiles:
  29738  /etc/init.d/glibc.sh 2b765577647ae33c2fdcc7bba95e4c7f
  29739  /etc/ld.so.conf.d/i486-linux-gnu 36f09aeeab18f6af453d0a1db0a0942c
  29740  /etc/ld.so.conf.d/libc.conf d4d833fd095fb7b90e1bb4a547f16de6
  29741  /etc/gai.conf 25b7f2e990aa62df7b7d233acd644813
  29742  /etc/bindresvport.blacklist db84c47f31f8d5a334a4053d8368e902
  29743 Description: GNU C Library: Shared libraries
  29744  Contains the standard libraries that are used by nearly all programs on
  29745  the system. This package includes shared versions of the standard C library
  29746  and the standard math library, as well as many others.
  29747 Triggers-Pending: ldconfig
  29748 Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
  29749

---

### Post by Ba66e77 on 2007-10-22
Further info:

trying to run adept_manager, I get this message in a pop-up when it loads: "The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

Trying to run apt-setup, I get:
barrett@barrett-desktop:~$ apt-setup
bash: apt-setup: command not found

---

### Post by Wayne Doust on 2007-11-09
I'm experiencing this exact error as well. Has there been any progress with it?

I left the upgrade running overnight on a Sony Vaio UX280P from an external firewire CDROM drive. When I woke up, the notebook was suspended and upon waking up it (it was waiting for an acknowledgement) it could not see the CD until it was umounted and remounted. Unfortunately a lot of packages were missed. The upgrade continued as best it could before it finally bombed out. 

sudo dpkg --configure -a 

dpkg: parse error, in file '/var/lib/dpkg/status' near line 35569 pacakage libc6':
'triggers-pend1' is not allowed for third (status) word in 'status' field

---

### Post by Ba66e77 on 2007-11-10
There hasn't really been any progress, though I have managed to get things working.  I ended up downloading the alternate install cd and running the upgrade through that.  That didn't get things working, but it did get things fixed enough that I could run though several iterations of apt-get update.  It took most of a weekend and probably a dozen runs of apt-get update (with things getting a little better each time), but things are working.

Good luck.

---

