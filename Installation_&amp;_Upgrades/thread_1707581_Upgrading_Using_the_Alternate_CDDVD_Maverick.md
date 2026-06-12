---
title: "Upgrading Using the Alternate CD/DVD Maverick"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by leonbravo on 2011-03-15
So you're following the [https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD]("https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD")

guide for upgrading from a CD/DVD, and misteriosuly it is not working! or trying to download all packages from internet. I'm not surprised. 

First at all, you need to add the CD/DVD to the repositories. Probably, you'd find (as I did) that it is not possible to add it as in [https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD]("https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD"). There are some bugs reported in [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/579110]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/579110") and [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/602945]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/602945").  
What to do?  In the very last link, Pearson suggested to add a symbolic link from /media/cdrom to /media/apt : ln -s /media/cdrom /media/apt (just in case you need it)

Second, you may find something like "E:Error, pkgProblemResolver::
Resolve generated breaks, this may be caused by held packages.". It has been documented as a bug in [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652"). The solution is also found in there: sudo apt-get remove xserver-xorg-video-nouveau.

Hopefully, that would be enough to have runing your upgrade.

Best luck.

---

