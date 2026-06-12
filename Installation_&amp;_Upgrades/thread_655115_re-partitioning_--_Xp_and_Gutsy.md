---
title: "re-partitioning -- Xp and Gutsy"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by pat_can_vault on 2007-12-31
On first hearing about Ubuntu, and Linux, I was a little skeptical, having always been a Windows user. Upon making partitions for Linux and XP (dual-boot), I decided I would give each OS half of my Hard Drive. After now using Ubuntu for about a month, (being very impressed with little problems) I have thought it would be a good idea to donate more of my space to Ubuntu. I also want to keep XP.  I downloaded "GParted" at the thought that this might do the trick, but I don't really know how to re-partition it so Ubuntu has more space, and XP has less. 

Any suggestions?

Thanks in advance:)

---

### Post by chewearn on 2007-12-31
> **pat_can_vault said:**
> On first hearing about Ubuntu, and Linux, I was a little skeptical, having always been a Windows user. Upon making partitions for Linux and XP (dual-boot), I decided I would give each OS half of my Hard Drive. After now using Ubuntu for about a month, (being very impressed with little problems) I have thought it would be a good idea to donate more of my space to Ubuntu. I also want to keep XP.  I downloaded "GParted" at the thought that this might do the trick, but I don't really know how to re-partition it so Ubuntu has more space, and XP has less. 

Any suggestions?

Thanks in advance:)

You cannot work on a mounted partition, so your would have to use the ubuntu livecd, or gparted livecd.

Boot into winxp first, defrag it a few times, make sure everything is moved to the beginning of the partition, below to new partition size.

Then, boot into livecd, and you can use gparted to resize.

---

### Post by darkstaar on 2007-12-31
Well, you don't need (or want) to repartition. Rather, you can resize the partitions using Gparted. It's easily done though, with any partition reworking, there is some risk involved so you'll want to make sure that any really important files are backed up somewhere off that hard drive.

Otherwise, like AstalaVista said.

---

### Post by zipperback on 2007-12-31
Read the following thread in regard to getting your system setup for dual booting.

I posted some links there.

[http://ubuntuforums.org/showthread.php?t=653213](http://ubuntuforums.org/showthread.php?t=653213)

- zipperback
:popcorn:

---

### Post by pat_can_vault on 2007-12-31
> **AstalaVista said:**
> You cannot work on a mounted partition, so your would have to use the ubuntu livecd, or gparted livecd.

Boot into winxp first, defrag it a few times, make sure everything is moved to the beginning of the partition, below to new partition size.

Then, boot into livecd, and you can use gparted to resize.

So, are you suggesting I boot into the LiveCD, then run GParted? Could you explain this further...

Sorry I'm stil a noob...:(

---

### Post by chewearn on 2008-01-01
> **pat_can_vault said:**
> So, are you suggesting I boot into the LiveCD, then run GParted? Could you explain this further...

Sorry I'm stil a noob...:(

Yes, boot into livecd.  At the gnome desktop, click on:
Top Panel Menu > System > Administration > Partition Editor

You will get the GParted apps, which is very much like any other commercial partition tool, e.g. Partition Magic.

There, you can rightclick on the partition, and select resize, etc.  Then click apply button.  Try do only one partition operation at a time; don't do multiple partition changes.

Important note:
The livecd gparted has a bug, where it might crash after the operation is completed, and it try to rescan your harddisk.  This bug was fixed recently, but the livecd gparted is older version.
Ignore the crash; the partition operation has already been completed; just open up gparted again to continue.

If you are scared of this bug, you can use the gparted livecd:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by pat_can_vault on 2008-01-01
Thank you very much. 

Appreciate the help!:KS

---

