---
title: "Kde 3.5.4"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by D!mon on 2006-08-03
There is a new realease of KDE, but official ubuntu mirror still includes 
KDE 3.5.2; is there any way to upgrade using official mirror?

---

### Post by bmorency on 2006-08-03
To upgrade to the newest version of KDE you have to add a new repository to your /etc/apt/sources.list file. You have to add one when ever there is a new version of KDE that is released.

There is a page on the Kubuntu homepage thet tells you what to add. Here is the link. [http://kubuntu.org]("http://kubuntu.org/announcements/kde-354.php")

once you have added it in the console just type: sudo aptitude update

Then you will be able to update to the new version.

---

### Post by infoseeker on 2006-08-04
> These packages are available for i386, AMD64 and PowerPC.
I am using 686 kernel. Will/can KDE be updated ?
> uname -r
2.6.15-26-686

---

### Post by daller on 2006-08-05
When I try to upgrade, the package:

**kdelibs-bin**

...is going to be removed...

Should I upgrade anyway?

---
**KDELIBS-BIN**
Description: core binaries for all KDE applications
 This package contains all the common binaries with are used by KDE
 applications. You need these binaries to run KDE applications.
 .
 Several scripts included in kdebase-bin, related to the handling of SMB
 and NFS shares, require the perl-suid package to work properly.
 .
 This package is part of KDE, and a component of the KDE libraries module.
 See the 'kde' and 'kdelibs' packages for more information.

---

### Post by daller on 2006-08-05
> **infoseeker said:**
> I am using 686 kernel. Will/can KDE be updated ?

It will work!

---

