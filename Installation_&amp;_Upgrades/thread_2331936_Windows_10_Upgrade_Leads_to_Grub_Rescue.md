---
title: "Windows 10 Upgrade Leads to Grub Rescue"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by archangelus2 on 2016-07-26
I took Microsoft up on the offer to upgrade my Windows 7 install to Windows 10 for free and am now unable to boot into any of my operating systems. I have a 2TB data drive and a 256GB SSD that my OSes were installed on. It's been so long I don't remember how the boot was configured though I do remember there were some complications with it when I initially set it up. If I am interpreting the boot info log correctly that complication may be that my Windows MBR is actually on my 2TB data drive and not the 256GB SSD OS drive. I have tried the boot-repair program from a Live Ubuntu USB and did not see any change in boot behavior. Before I go messing with anything else I wanted to see if anybody had any recommendations for which step I take next. 

grub rescue shows:

```
(hd0)
(hd0,msdos5)
(hd0,msdos3)
(hd0,msdos2)
(hd0,msdos1)
(hd1)
```

Which all produce the error 'unknown filesystem.' when I try the ls command on them.

Full boot info log is here: [http://paste2.org/nYLp31Db](http://paste2.org/nYLp31Db)

Thanks for any help.

---

### Post by yancek on 2016-07-27
The only sign of any Linux system on your two hard drives is the swap partition, sdb5.  There is no root filesystem for Ubuntu so either that was overwritten  or more likely, was not included in the partition table which was re-written by windows after the upgrade.  You can see below the start sector for the Extended partition and the start sector for swap which leaves a lot of room for what was your Ubuntu partition.  That would indicate your Ubuntu / partition is still there but not included in the new partition table.  I'm not sure how you would recover that but I've seen posts here dealing with.  Hopefully someone else will post to explain it.

> /dev/sdb4         369,418,240   468,860,927    99,442,688   5 Extended
 	/dev/sdb5         461,002,752   468,860,927     7,858,176  82 Linux swap / Solaris

---

### Post by archangelus2 on 2016-07-27
Thanks Yancek. I actually found another thread where you also replied that I think will be my next course of action, trying to repair the partition table with Testdisk.

[https://ubuntuforums.org/showthread.php?t=2320440](https://ubuntuforums.org/showthread.php?t=2320440)

---

