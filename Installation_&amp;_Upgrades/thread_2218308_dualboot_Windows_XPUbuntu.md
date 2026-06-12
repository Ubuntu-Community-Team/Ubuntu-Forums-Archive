---
title: "dualboot Windows XP/Ubuntu"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by UBUminJ on 2014-04-20
At the moment I have a dualboot Ubuntu 12.10 and Windows XP.

Actually, I would like to erase Windows fully but
* some of my gadgets have good Windows software
* .mov files have problems with Ubuntu software and my camera produces *.mov files

So, I will keep WinXP in a small corner.

At the moment, I have 1 TB Win and 1 TB Ubuntu but I want to change this to 100GB Win and the rest Ubuntu during the install of Ubuntu 14.04

My question: can I do this during the Ubuntu replacement or do I first need to shrink Windows and then claim the remaining place?

I have already prepared the shrinking in Windows (threw out unnecessary software, stopped the paging (pagefile.sys) and moved everything at the start of the disk.

Thank you

---

### Post by pfeiffep on 2014-04-20
> **UBUminJ said:**
> At the moment I have a dualboot Ubuntu 12.10 and Windows XP.

Actually, I would like to erase Windows fully but
* some of my gadgets have good Windows software
* .mov files have problems with Ubuntu software and my camera produces *.mov files

So, I will keep WinXP in a small corner.

At the moment, I have 1 TB Win and 1 TB Ubuntu but I want to change this to 100GB Win and the rest Ubuntu during the install of Ubuntu 14.04

My question: can I do this during the Ubuntu replacement or do I first need to shrink Windows and then claim the remaining place?

I have already prepared the shrinking in Windows (threw out unnecessary software, stopped the paging (pagefile.sys) and moved everything at the start of the disk.

Thank you
From all I've read you should manipulate Windows partitions with Windows tools.

---

### Post by fantab on 2014-04-20
You MUST shrink/resize XP first and with Windows tools only. Windows works best if the C: partition has atlest 30% of free space, so shrink it wisely. And don't use XP to go online whenever the support ends.

Did you install ubuntu-restricted-extras package? It might help you overcome your difficulty with .mov files as it deals with ['restricted' formats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by UBUminJ on 2014-04-21
What is the problem with using GParted under Ubuntu and resizing the NTFS partition?
Thanks

---

### Post by oldfred on 2014-04-21
Generally better to use Windows tools for Windows and Linux tools for Linux.

While gparted usually works, Windows does have to run chkdsk after any resize. You need to immediately reboot into Windows so it can run chkdsk and make whatever repairs it does for its new size.

And we have seen cases where resizing or moving NTFS partitions with Linux tools have created issues. But we are not sure if it was Linux or a previous issue with Windows that would have happened anyway. So, it more so Windows users do not blame Linux tools for issues they may have had anyway. :)

And good backups are vital as any major change to system can get corrupted or issues occur that only can be resolved with a full restore.

---

### Post by UBUminJ on 2014-04-26
Unfortunately, the advice to use Windows tools led to an unbootable PC.

I used EaseUs Partition Master from inside Windows, resized the Windows partition from 1000 GB to 200 GB, rebooted to finish the work. So far, OK. But in the next boot, no system was found anymore and Grub rescue methods as described in several places of the web did not revive the PC. Fortunately, I have a copy of all data.

I recommend using GParted from the beginning.

As it was only Windows XP, I then decided to just let it as it is - and now it is a full Ubuntu PC.

---

