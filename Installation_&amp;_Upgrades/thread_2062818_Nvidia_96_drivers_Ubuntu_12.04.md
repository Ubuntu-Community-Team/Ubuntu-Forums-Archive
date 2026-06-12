---
title: "Nvidia 96 drivers Ubuntu 12.04"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by hpacheco on 2012-09-25
Hello everyone.

I have been struggling for a while to be able to install the legacy nvidia-96 drivers in ubuntu 12.04.
When I was about to give up, I noticed NVIDIA release some new drivers compatible with the Xorg version used in 12.04.

[http://www.nvnews.net/vbulletin/showthread.php?t=179489&page=8](http://www.nvnews.net/vbulletin/showthread.php?t=179489&page=8)

I then looked for a debian package to perform this install that I found here:

[https://launchpad.net/debian/experimental/+source/nvidia-graphics-drivers-legacy-96xx](https://launchpad.net/debian/experimental/+source/nvidia-graphics-drivers-legacy-96xx)

However, after a while trying to satisfy all dependencies, I noticed that a required package nvidia-installer-cleanup is in conflict with ubuntu-drivers-common (they both share a sub-package nvidia-common). I have even tried the 12.10 repositories but with no luck.
In fact, there is no candidate package for nvidia-installer-cleanup either in 12.10 or 12.04.

Has anyone tried to do the same thing? This should not be very difficult to wrap up... but not for me.



o

---

### Post by bogan on 2012-09-26
Hi!, **hpacheco**,

According to the nvidia.com/drivers Web page the latest nvidia 96 driver v.96.43.23 is compatible with the 12.04 Xorg-xserver.v1.11 & 1.12 in 12.04, and is available as a '.run' file from: 
[http://www.nvidia.com/object/linux-display-ia32-96.43.23-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.23-driver.html)
> Added support for X.Org xserver versions 1.11 and 1.12.
Improved compatibility with recent Linux kernels.What video card are you using? a Gforce4 MX 440??
 
Please Post:```
 lspci -nnk | grep -iA3 VGA
```Chao!, **bogan.**

---

### Post by hpacheco on 2012-09-26
Yes, it does, but that update is pretty recent.

My video card is a Geforce4 Ti 4800 SE.

I have tried installing it directly form the .run, but this brings issues with the nouveau drivers, and I have broken my system before because of this (deactivating the nouveau drivers and a failed installation of the nvidia drivers made my system unable to boot into X and into text mode). 

Therefore I was looking for a .deb-based solution.
However, this recent update to the NVIDIA drivers has not yet been updated in the ubuntu packages, and my attempt to do so has failed due to the above-mentioned conflict.

---

### Post by lucamanu on 2013-03-05
Hallo both.
I have the same problem with a fresh install of Lubuntu 12.10. 
I have a GeForce MX440-SE. 
Upon installation, the system was running on Nouveau, which is almost acceptable. However, due to some artifacts and wrong rendering of overlaying, I decided to perform various tests. 
After every change, I always hard reboot the whole system, as I noticed that a simple restart of xserver is not sufficient.

I tried initially with nvidia-common and nvidia-common-updates, but neither works. These install blacklist nouveau, so no risk of conflict. Note that nvidia-xconfig says that no nvidia driver is installed.

I tried then downloading the driver v.96.43.23 from nvidia.com. 
The first problem is that the script immediately issues a warning, saying it fails (I tried to understand why, to no avail). However it offers the possibility to go ahead, and everything seems fine. However at graphic level there is no difference with the nvidia-common: the system sets automatically a lower resolution (compared to nouveau) and does not allow to change it. The only difference is that this time nvidia-xconfig confirms that a nvidia driver is installed (not yet working though).

Searching on the net, it seems that xorg-xserver is incompatible, however backtracking it to a previous version would for me only be a last instance choice.

Did you have any progress since sept last year? Suggestions for a possible solution?
Thanks a lot.

---

