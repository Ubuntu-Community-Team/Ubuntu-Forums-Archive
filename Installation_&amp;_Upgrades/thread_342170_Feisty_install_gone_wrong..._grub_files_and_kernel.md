---
title: "Feisty install gone wrong... grub files and kernel deleted"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by tjk on 2007-01-19
I've read **many** postings, but every situation is somewhat different then mine, and I am at the point of getting very frustrated, so hopefully someone can make some suggestions as to how to deal with my predicament.

First of all here is some important info from a "sudo fdisk -l":
----------------------------------------
Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         184     1477948+  83  Linux                                ---> boot folder
/dev/hda2           22492       30149    61512885    b  W95 FAT32               ----> Windows folder
/dev/hda3           30150       30515     2939895   82  Linux swap / Solaris  ---> swap 
/dev/hda4             185       22491   179180977+   5  Extended                     
/dev/hda5             185        4887    37776784+  83  Linux                           ----> /home  (data)
/dev/hda6            4888        7359    19856277   83  Linux               ---> was the reformated partition that I have temp installed xubuntu on.
/dev/hda7   *        7360       22392   120752541   83  Linux                 --> the "lost" Kubuntu folders (with only small locked "lost & found" folder currently there)
/dev/hda8           22393       22491      795186   82  Linux swap / Solaris --> main swap partition

Partition table entries are not in disk order
-------------------------------------------

About a week ago I tried to install Feisty on partition hda6 (which at that point was partition hda5).  I don't know if it was something that I did wrong or if qtpart renumbered almost all of my partitions, but almost everything changed after I formated the available partition hda6.  After exiting the Feisty installation I couldn't reboot because I got a error 15 from grub.  I then used a live CD to check things out.  There were no files remaining from my previous installations in the boot partition (hda1), even though I had not requested a reformat.  Hda8 (which previously was hda5) appears to still contain all my /home data ( :|  -- sigh of relief!!).  However, the remaining dirs/folders that were in hda7 (was hda6) are most likely gone -- except there is something weird in this partition -- there is a locked "lost and found" folder that I can't access (but it's not very big, that's why I don't think it's all my dirs/folders).

Now... what do you think happened and what shall I try to do?  Try to recover the partitions (I have tried 1 partition repair program already to just review the possible changes-- which don't seem to be correct)  Or maybe the files are just deleted?  Or will I have to reinstall Kubuntu AMD64 -- and if so, can I just leave the /home partition where it is when I reinstall (of course backup first)?  -- and if so, will I have to reinstall all the packages that were there before (or is there a command or package that will see all the past installation settings / configurations in the /home/username folder and reinstall automatically (probably wishful thinking)?

---

### Post by Sef on 2007-01-19
> dev/hda1 * 1 184 1477948+ 83 Linux ---> boot folder

> dev/hda7 * 7360 22392 120752541 83 Linux --> the "lost" Kubuntu folders (with only small locked "lost & found" folder currently there)

Those two partitions, both say they are the boot partition.   I would make only one the boot partition and see if that helps at all.  As for getting your partitions back, check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by tjk on 2007-01-20
> **Sef said:**
> Those two partitions, both say they are the boot partition.   I would make only one the boot partition and see if that helps at all.  As for getting your partitions back, check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

I change it so that hda1 is the only boot partition --- didn't help.
I ran TestDisk, but it didn't find a recoverable hda7.

So any advice on reinstalling (as that seems to be my only option)?

---

