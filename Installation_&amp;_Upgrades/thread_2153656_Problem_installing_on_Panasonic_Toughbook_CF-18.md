---
title: "Problem installing on Panasonic Toughbook CF-18"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by eldiablo820 on 2013-06-11
Hi all, been using Ubuntu on my various home pcs & laptops for a while and I've run across this problem when trying to install onto a Panasonic Toughbook.


I've tried several different versions(9.04, 9.10, 11.10, 4.10), when trying to install or boot up alive system via usb I get the following error on startup...

Intel UNDI, PXE2.0 (build 082)

For Realtek RTL8139(X)/8130/810X PCI Fast Ethernet Controller v2.0
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.


It keeps constantly cycling through this error, it can't seem to get beyond this step.

I've also tried a FreeBSD install, it recognises the existence of both the ethernet and wireless adapter but won't communicate with either of them. On a Windows XP install both of these devices work fine.

I've done a bit of reading around and there doesnt seem to be any compatability issues with this model of laptop so I'm a bit stuck. I'm pretty much a beginner to linux systems and I've never had any bootup issues before. 

Is there a way to interrupt the boot sequence and skip this step or will this be a matter of compiling an installer from source code?


Thanks in advance for any help.

---

### Post by tgalati4 on 2013-06-11
Is there a BIOS setting that has PXE in the boot list?  If so, remove it or push it lower on the list.  The other thing to try is to turn off the ethernet card in BIOS if possible, at least to get the Live session to boot.

---

