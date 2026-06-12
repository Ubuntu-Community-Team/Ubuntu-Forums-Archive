---
title: "Upgraded to 10.10. Won't boot."
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by oroberts on 2010-10-13
Heya,
I'm having trouble with my installation after upgrading to 10.10. I've had this box for several years, upgrading through various versions. It has two old HDDs in it, but they work fine.
The installation went fine except for a warning message window that popped up for a few seconds then disappeared. It said something about failed to install a probe for a HDD or something. 
Afterwards it restarted, and won't boot. I see the "Starting up..." text, for a few seconds, then I get a dump of info saying it couldn't find the boot partition, including text like
"ALERT! /dev/disk/by-uuid/f099d37f-... does not exist. dropping       to a shell!"
performing ls /dev/disks/by-uuid shows only one entry
dcde5511-...

I have started up using SystemRescueCD, and I can see all the partitions there, and they are:
6149227e-.... maps to /dev/sda5, a linux swap partition, under     /dev/sda2 ext partition
    f099d37f-..... maps to /dev/sda1 a linux boot partition
    dcde5511-.... maps to /dev/sdb1 a HPFS secondary drive 

so clearly the primary drive (sda, a Maxtor) has not been detected, and none of its partitions are mounted. sdb, a WD is fine.

How can I recover from this please?

---

### Post by oroberts on 2010-10-14
If I just do an install over the top, will it leave the existing setup? Will it leave the user home directories?

---

### Post by mörgæs on 2010-10-14
This might help you when doing a fresh install:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by oroberts on 2010-10-19
Copied the sbackup files to a Ubuntu 10.10 VM, and it wants to upgrade them before recovering them, but it fails. And yes, I've set the permissions liberally, and it still fails to find a file that is clearly there.
I've just unzipped the archive and copied all my files back to windows.
bye bye ubuntu.
not happy.

---

### Post by oroberts on 2010-10-19
Huh, look at that. One of the grub menus marked as server actually boots to the login, but the mouse and keyboard are disabled. I can boot into the corresponding recovery console, but how do I fix the mouse/keyoard? They are PS/2. I get keyboard in the recovery shell, just not when I boot to the login.
None of the grub options marked as generic boot at all. I figure this is something to do with this box starting as a server edition, then getting the desktop loaded afterwards. ??
Anyway, how can I get the mouse/keyboard working again from the recovery console?

Thanks.
Owen

---

### Post by mörgæs on 2010-10-19
I can not give a precise answer, but there have been quite a few of these questions for 10.10. Have you tried if 10.04 works better?

---

### Post by oroberts on 2010-10-20
I've been upgrading since 8.04. Never had this much trouble.

---

