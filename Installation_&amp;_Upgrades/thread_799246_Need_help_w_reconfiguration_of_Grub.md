---
title: "Need help w/ reconfiguration of Grub"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by linuxology on 2008-05-18
I have 2 250GB drives.  The primary drive held my Windows installation and my secondary drive was just a data drive.  When I installed Ubuntu I partitioned the primary drive so Linux and Windows resides on the same drive.  I now want to put them on seperate drives.  I have the Windows and Linux partitions imaged and my plan is to partition the data (secondary) drive and put the Windows image on the extra partition I will create and then reallocate all the space that was being used by the Windows partition (primary drive) to Linux.  I know by doing this it will mess up my grub, to boot Windows and possibly Linux.  I was wondering is there an easy way to fix all this?  Thanks

---

### Post by iaculallad on 2008-05-18
For reconfiguring GRUB, you can refer it to the [GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") page.

It seems that you had freshly installed both OS. I would recommend you doing a fresh install on both windows and Ubuntu since transferring images on another drive would alter your GRUB menu list. But if you refer on the link above, surely, you could do it without the fresh install.

---

### Post by linuxology on 2008-05-18
> **iaculallad said:**
> For reconfiguring GRUB, you can refer it to the [GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") page.

It seems that you had freshly installed both OS. I would recommend you doing a fresh install on both windows and Ubuntu since transferring images on another drive would alter your GRUB menu list. But if you refer on the link above, surely, you could do it without the fresh install.

I previously had Windows and decided to Dual boot.  I installed Ubuntu on the same drive as Windows when I should have installed it on the secondary drive.

---

### Post by iaculallad on 2008-05-18
You could always use the Partition Manager which comes with Ubuntu's liveCD to "re-Partition" (as in delete your /,/home, and swap and format it on any file system you want) your existing Ubuntu drive, then, afterwards install your Ubuntu on your secondary drive.

---

### Post by linuxology on 2008-05-18
Yeah looks like the best solution is just to reinstall.  This would be the safest and probably least amount of trouble.

---

