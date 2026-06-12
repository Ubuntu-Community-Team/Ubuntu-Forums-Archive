---
title: "Upgrade with CD"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by The Bird Man of Alcatraz on 2007-08-24
Hi,
  A few days ago I messed up the Master Boot Record on my Ubuntu 6.06 PC.  Ubuntu is intact, but I just can't boot into it.  I figured now would be a good time to upgrade to 7.04, so could someone help me upgrade with a 7.04 CD?  Will this process save all of my work?  Thanks a million! :guitar:

-The Bird Man

---

### Post by Pumalite on 2007-08-24
Get in with a Live CD and save all your data. Then do a clean install of 7.04

---

### Post by The Bird Man of Alcatraz on 2007-08-24
Thanks Pumalite, but now I can't seem to get into my drive.  These are a few of the errors that the error message lists:  wrong fs type, bad options, and bad superblock on dev/hdc1.

Does this mean my work is lost?  Thanks!

---

### Post by Pumalite on 2007-08-24
Boot from rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) and check your system and your drive specifically.

---

### Post by The Bird Man of Alcatraz on 2007-08-24
GParted shows nothing out of the ordinary.  The main Ubuntu partition is /dev/hdc1.  /dev/hdc2 is extended, and /dev/hdc5, the swap, is under the extended partition.

---

### Post by Pumalite on 2007-08-24
Use super Grub and see if you can re-install Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by The Bird Man of Alcatraz on 2007-08-25
SuperGrub worked out great, thanks a ton for the help Pumalite!

GRUB seems to work now.

However, now I am stuck with BusyBox.  The system boots up through GRUB, and says something like > can't access tty; job control turned off

GRUB points to hdc1; do I need to change that?  Thanks a ton!

---

### Post by Pumalite on 2007-08-25
Check this: [http://ubuntuforums.org/showthread.php?t=279884](http://ubuntuforums.org/showthread.php?t=279884)

---

