---
title: "Wubi Boot Issue - SHORT VERSION"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by MikeInDetroit on 2012-01-12
Short Version of: [http://ubuntuforums.org/showthread.php?t=1907540](http://ubuntuforums.org/showthread.php?t=1907540)

1. Used Wubi 
2. Inside XP
3. Single drive partition type: HPFS/NTFS/exFAT
4. Likely encrypted drive
5. Sophos, not GRUB, primary boot loader 
6. Upon startup Ubuntu drops into common error (below).  Cannot find root drive
7. Wanted to edit MBR to point to sda1 (correct name)
8. Cannot use GRUB as Sophos controlling
9. LiveCD does not seem to find the root drive !!!

Questions:
1. On encrypted HD (laptop) would Wubi install work?
2. Can I change the MBR any other way either directly from XP or copying it to another Ubuntu installation and editing it there?

(Obviously I don't want to run any of the tools that fix a grub installation as it will just clobber the XP Sophos boot loader or just pooch things up so...)





The Ubuntu startup issue:

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping to a shell!
(initramfs)

---

### Post by MikeInDetroit on 2012-01-12
Yes and I am a super-uber-newbie.   (I'm good at somethings but this isn't one of them ;).

---

### Post by MikeInDetroit on 2012-01-12
This is the only information I've been able to locate so far:

[http://ubuntuforums.org/showthread.php?t=1039401&highlight=dual+boot+encrypted+drive](http://ubuntuforums.org/showthread.php?t=1039401&highlight=dual+boot+encrypted+drive)

Now, I would really prefer to get Wubi working because it's not likely I'll be creating a second partition on this encrypted drive without wiping out the laptop and starting from scratch.

---

### Post by Rubi1200 on 2012-01-12
Please don't create multiple threads on the same subject; it dilutes community effort and makes offering solutions harder.

Duplicate here:
[http://ubuntuforums.org/showthread.php?t=1907885&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1907885&highlight=wubi)

Thread closed.

Thanks for understanding.

---

