---
title: "Partition table install problem"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by fifer1227 on 2010-09-17
Hi - I'm new to this forum and would appreciate a steer. Trying to install 10.04 with the live CD to a pc with XP occupying entire hard drive. I get to step 3 of 7 of installation wizard and enter UK keyboard layout which takes me to step 4 of 8 (?!). This is the partition table but it's blank and all the buttons are greyed out. When I right click on the blank area I just get 'Revert'. Doesn't let me go forward. I'm stuck! Do I need to free up space on hard drive before using the installer? I have exactly same problem with Mint installer. Thanks.

---

### Post by Sylos on 2010-09-17
Hi there. I dont have a huge amount of experience with this but I can offer a general insight.

Normally during the install you will be offered at this stage 3 main options:
1. Install to entire disk.
2. Guided resize - moves all windows files to one end of the disk and uses the free space.
3. Manual - you set up the partitions yourself (not for the faint hearted!)

What you are experiencing seems like a fault somewhere.

Have you checked the installation disk for Faults?

---

### Post by fifer1227 on 2010-09-17
Yes, I was expecting those options. It may be a live disk fault but I suspect not as the Mint intsllation disk has same problem. I don't think the hard drive is faulty. Cheers

---

### Post by Sylos on 2010-09-17
Hmm.
What version of windows is running on it and how is the drive partitioned at the moment?
Do you know what fielsystem is used for each partition?

Not sure if I can help with that info but it cant hurt to look.

Good luck.

---

### Post by fifer1227 on 2010-09-17
Thanks. It's XP Home and the drive is unpartitioned - just the one NTFS disk with Windows.

---

### Post by srs5694 on 2010-09-17
If XP is on it, the disk *is* partitioned, even if it uses just one partition.

I'm not 100% positive, but I suspect you've run into [this problem.](http://www.rodsbooks.com/missing-parts/index.html) For diagnosis, type "sudo fdisk -lu" at a command prompt from an Ubuntu Live CD boot, then post the output, preferably between a [noparse]```
[/noparse] and a [noparse]
```[/noparse] string for legibility. This will let us see what's going on. Note that the "-lu" is a lowercase L, not a digit 1, and a lowercase u.

---

