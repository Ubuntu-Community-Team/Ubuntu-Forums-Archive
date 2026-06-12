---
title: "Upgraded from breezy -&gt; can't find root partition (nforce+SATA)"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by ndazza on 2006-07-06
Hi,
I just upgraded from breezy to dapper, using apt-get dist-upgrade (after changing sources.list). Now my system won't boot. After a few minutes of hanging on the message "Mounting root filesystem" I get dropped into an initrd shell with the error: "ALERT! /dev/md0 does not exist. Dropping to a shell". (/dev/md0 is a RAID-1 with the root partition on it).
The devices sda and sdb (my sata drives) don't exist in /dev , my motherboard is an nforce4 board. I have tried modprobe sata_nv, there are no errors but my devices still don't appear. I have tried using the kernel parameter root=/dev/sda1 as well, I get the same error and the same shell. I've tried also the suggestions in the sticky thread on this error (trying kernel parameters and the like) without any luck.
Some additional notes:
* The old kernels are still installed (from breezy) and when  booting with those, the bootup sequence succeeds. However the graphics in X is corrupted (pink and green patterns repeated over the screen), so I have to drop to a tty and work from there
* The desktop live CD shows the same symptoms - hanging on "mounting root filesystem" then eventually crashing (md5sum checks out okay, works on other computers, passes cd check on other computers, tried with different drives).

Cheers!

Darren

---

### Post by John.Michael.Kane on 2006-07-06
ndazza it looks like your experiencing the same raid issues as some other users. If you can please try installing with just one of the sata drives, and connected not to frist port sata1 but connected to port sata2. i know this is not the answer you want however dapper seems to be cranky with some sata setup's.

---

### Post by ronly on 2006-07-06
I don't know whether ndazza uses raid or not but I don't and I have the same problem - just one sata drive connected and my breezy installation got quite broken when I tried dist-upgrade but I can still boot with an older kernel but I can't do anything with the latest kernel and because that doesn't work I can't install dapper from scratch either (the live cd boots but I don't have any /dev/sd* so I can't access the drive).

---

### Post by ndazza on 2006-07-06
Hi SD-Plissken, thanks for replying!

I tried re-installing to a single sata drive using the dapper text-mode install CD, however the installer didn't complete. The installer complained that it couldn't mount the CD, so I changed CD drives and it found itself (?) and continued. Next problem: network card couldn't be detected. Strange but no biggie. Main problem: After the progress bar reading "Detecting hard drives and other hardware", the installer hangs completely on a blank blue screen (BSOD! :).
I opened a terminal and poked around. The devices /dev/sda and /dev/sdb didn't exist again and even after calling modprobe sata_nv they didn't appear (is that how it is supposed to work?). 
I do have a RAID1 on my SATA drives but I don't think the raid is the issue here as I can't access the drives at all. During the dapper flight pre-release versions the installer was working better for me, but even then the partition manager thingy couldn't see my SATA drives, just my IDE drive.

Cheers!

Darren

---

### Post by ndazza on 2006-07-10
Bump

---

### Post by ndazza on 2007-03-28
This problem has persisted through to feisty beta. Currently:

- The Feisty Herd 5 desktop cd will boot (as long as my IDE drive is not connected), but:
- There are no devices named /dev/sd*
- sata_nv is loaded
- eth0 doesn't exist. modprobe forcedeth makes no difference (doesn't fail but still no eth0)
- The USB mouse doesn't work (and neither does my usb drive)
- knoppix shows all the same symptoms. suse/mandriva don't boot at all

---

