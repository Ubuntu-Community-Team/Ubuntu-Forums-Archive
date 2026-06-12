---
title: "[SOLVED] Serious installation problems"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by sadako1 on 2008-08-12
Hello all, this is my second flirtation with Ubuntu (and Linux) and it's really not going well. I downloaded the Ubuntu 8.04.1 x64 desktop edition from the torrent server and burned it nice and slow to a disk, checked it, did fresh 0-fill formats of both SATA drives and went to work. The live disk started no problem, let me set up my partitions (swap, ext3 and fat32), let me fill in my data and then let me start the installation. That is as far as I've ever got.

The machine's come at me with a host of different errors, including input/output errors and other errors that say the disk is corrupt. OK, I thought, check the files, check the drives (seagate SATA drives - both fully checked with the manufacturer's seatools suite and come up as good), burn a new disk with a fresh copy of the ISO from a different location, with a different machine and different writer and try again. Same issues.

I tried the same thing a couple of times, went to Ubuntu 7.04 which I installed without (much) problem last time and that didn't work. Xubuntu. Same. Fedora 9 was a bit more successful, managing to install an OS, but that wasn't any good as it didn't work (no admin access, most packages missing, no access to repositories) so I tried a different approach. I clean installed Windows XP (with no issues!) and tried Wubi. Same. I then tried Unetbootin. Same.

Looking around I saw hints that maybe there were some weird issues with hardware config, so I unplugged drives so that I was only installing with one hard drive in the machine. Same. I've removed a stick of RAM to see if there were issues with duel channel RAM. Same. Short of swapping out my motherboard I have no idea.

My hardware is:
-  Sapphire Pure Innovation motherboard (bit proprietory, I know. Is this my problem?) with ATI chipset
-  AMD 3700 64bit
-  2GB mushkin redline
-  ATI X1800XT
-  430W power
-  SATA DVD-RW
-  160gb & 120gb SATA Seagate Barracuda

This is getting to me now. I'm REALLY wanting to get out of M$ and I love the way Ubuntu works, preferring it to XP and Vista in a big way... when it works.

Please help, I'm at the end of my tether!

Andrew

---

### Post by Pumalite on 2008-08-12
Try the Alternate CD.

---

### Post by sadako1 on 2008-08-14
Cheers for that. Who'd have thought the solution would be so easy?!

Just out of curiosity, what's so different about the alternate ISO and the LIVE?

---

### Post by Pumalite on 2008-08-14
The Alternate CD is a text based installer designed to avoid hardware and/or graphics problems. I'm glad you got it working. Good luck!

---

