---
title: "New install q's, dual HD, dual boot with XP install first"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by wv25m on 2007-02-06
First off, I'm a complete newbie with Linux and want to make the jump.

I have an HP 9030 laptop with dual 100Gig HDs.  I have XP installed already and want to have a dual boot setup and want to install ubuntu 6.10 (current HD setup is NTFS).  What I would like to do is somehow install ubuntu on my slave drive, keep my XP on my primary drive without modifying it (at all if possible), and have the option at bootup to select between ubuntu and XP.  Since this is a laptop, I'm not cracking it open and messing with jumpers etc.  What do I need to do in order to make this happen???

Thanks in advance.

---

### Post by confused57 on 2007-02-06
> **wv25m said:**
> First off, I'm a complete newbie with Linux and want to make the jump.

I have an HP 9030 laptop with dual 100Gig HDs.  I have XP installed already and want to have a dual boot setup and want to install ubuntu 6.10 (current HD setup is NTFS).  What I would like to do is somehow install ubuntu on my slave drive, keep my XP on my primary drive without modifying it (at all if possible), and have the option at bootup to select between ubuntu and XP.  Since this is a laptop, I'm not cracking it open and messing with jumpers etc.  What do I need to do in order to make this happen???

Thanks in advance.

You might be able to accomplish this by entering the bios setup, set your slave drive as the first hard drive boot device...when installing Ubuntu, this drive "should" show as hd0, since it is the first boot hard drive.  You should be able to determine from the partitioner if this is the correct drive designated as hd0(hdb, or sdb?).
Once Ubuntu is installed, you can add an entry to boot Windows, similar to what's described here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I always use the alternate cd to designate where to install grub, but I've read(haven't actually used the live cd installer) that you can do so with the live cd...I think if I remember correctly on step 5 of 6, it'll give you the option of where to install grub.  The default is hd0, which should be correct if your hard drives are correctly identified, but you can also click the "arrow" for a drop-down menu of where you would like grub installed.

With the alternate cd, I usually enter "/dev/hdb"(in your case) to make sure grub gets installed to the correct drive's mbr.  

Windows mbr can be restored, if grub is "accidentally" installed to the wrong mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

or the Super Grub Disk can restore Windows mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
in fact, I'd recommend that you make a SGD cd(approx 500 kb download) before installing Ubuntu, it's a pretty handy utility to have around for booting Windows or Linux(or restoring the mbr of either).

---

