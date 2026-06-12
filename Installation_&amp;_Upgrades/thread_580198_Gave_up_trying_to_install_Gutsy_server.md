---
title: "Gave up trying to install Gutsy server"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by sethryan on 2007-10-18
I give up trying to install Gutsy server on my very standard system. I was doing a fresh install over Edgy. In fact I stayed on Edgy because Feisty had a bug that prevented my raid 5 array from coming cleanly on boot.

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177)

Now Gutsy is coming out and I am very excited. Despite the fact that I already installed the desktop version at work and dual monitor support for ATI is completely broken (I tried my known working xorg.conf and fglrx drivers as well as the ATI driver). Now I get home and the installation for Gutsy server takes FOREVER to do anything. The detect hardware takes 10 minutes. And unless I use expert mode and keep stopping it from loading the ide-floppy module (which freezes the install) then I don't get anywhere.

I spent all DAY trying to get this thing loaded but it still doesn't work. I'm going back to Fedora or some other distro because this CD is completely useless.

Hardware is
Asus A8N SLI Deluxe
Athlon X2 3800
1Gig ddr400
1 x Seagate ATA 20 gig drive
5 x 250gb Western digital SATA drives

---

### Post by sethryan on 2007-10-23
Has anyone else had this problem? The install took forever, mostly the detect hardware screens took forever and I also had the modprobe exit error.

---

### Post by lipilee on 2008-01-12
hi,
is it possible that your floppy (if you still have one at all) is crappy? the reason it freezes might be that the installer sees something that looks like a floppy drive but does not actually get any response.
I would try deactivating the floppy in the BIOS and wherever I can (who needs it anyway), maybe that solves the problem.

---

