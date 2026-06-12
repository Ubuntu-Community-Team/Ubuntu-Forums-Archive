---
title: "Dual boot with Xp"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by Jikaabx on 2007-03-31
I'd like to create a dual boot with Ubuntu 6.10 and Windows Xp, except I'm not exactly sure to how to go about it.  Any help anyone can offer would be great.  I've read the installation guide and it helped a bit, but not quite enough.  I see the install icon on the desktop in the Ubuntu when its booted from the CD...would that partition the drive and everything? Thanks.

---

### Post by confused57 on 2007-03-31
> **Jikaabx said:**
> I'd like to create a dual boot with Ubuntu 6.10 and Windows Xp, except I'm not exactly sure to how to go about it.  Any help anyone can offer would be great.  I've read the installation guide and it helped a bit, but not quite enough.  I see the install icon on the desktop in the Ubuntu when its booted from the CD...would that partition the drive and everything? Thanks.

You probably should read over the "Plan Partitions" and "Install Desktop CD" in this link:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Also, it would be a good idea to defrag your Window's partition, maybe even a couple of times, before trying to use the partitioner on the live cd installer.  Backing up any important data would be a good idea...there's always the very slight chance of a problem.

If you don't have a Window's installation cd(not a recovery cd), you might want to download & burn a copy of the Super Grub Disk before installing Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only an approx 500 kb download & would be useful to have if you have booting problems

You shouldn't have any problems at all, but it doesn't hurt to be prepared in the unlikely case that you do.

---

### Post by Jikaabx on 2007-03-31
This is a pretty typical dual-boot scenario. And I believe it's also the one that will be created if you choose to have Ubuntu's installer automatically resize your Windows partition and create a Ubuntu partition out of the free space. I'm not sure if the proportions are right. Ubuntu's installer probably makes it a little more 50/50, but I'd need someone to confirm that, as I've always done my partitioning manually instead of automatically.

Thats basically what I want to do, is split the remaining free space down the middle.

---

