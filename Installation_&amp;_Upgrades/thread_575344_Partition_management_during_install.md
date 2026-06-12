---
title: "Partition management during install"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by Can+~ on 2007-10-13
So, a friend of mine tried installing ubuntu Feisty Fawn in his PC, the HDDs are set in this way:

-hda (20gb) old disk, windows XP installed here. Primary partition
-hdb (80gb) new disk, Samsung 7200 rpm, formatted as NTFS with random XP files. Logical.

The thing, I suggest him to try the LiveCD before resizing and all that ****, so he did, and asked him to open the Gparted. As we are only interested on the 80gb hdd, this is what happend:

-hdb:
7 GiB unknown.
72 GiB unallocated.

Weird, the whole hard disk is formatted as NTFS. Anyway, he resized back in windows with Acronis Disk Manager, left 10GiB for ubuntu. Then used the LiveCD and gparted won't run, getting stucked on "Scanning disks" (or something like that).

The weirdest thing, is that windows has the full 80 GiB (74gb actually) as ONE partition, there is no 7-72 partitions in there.

*edit*
He told me that the BIOS detects 32Gb of this Samsung hard disk, but XP detects 80 later. I googled that and got this info:
[http://www.velocityreviews.com/forums/t200667-samsung-hdd-32gb-detection-problem.html](http://www.velocityreviews.com/forums/t200667-samsung-hdd-32gb-detection-problem.html)

Still working on it.

---

### Post by Can+~ on 2007-10-14
Bump? :(

---

### Post by logos34 on 2007-10-14
You should have the jumper pins set for slave position.  Did you try the different pin positions in the Samsung installguide referenced in the above url?

---

### Post by Can+~ on 2007-10-14
Oh sorry, moving the jumper worked. He was unsure to do it, since the install guide was for a different model.

*edit*
Now the size is detected right by the BIOS, BUT still no luck with the Ubuntu.

---

### Post by logos34 on 2007-10-15
Gparted doesn't seem to be reading the partition table correctly.

You might try to proceed with the install, and if it detects the partition you left for linux select 'Guided - Use the largest continuing free disk space.'  Or choose manual, it's up to you.  Take a look at[ this]("http://www.psychocats.net/ubuntu/installing").

Otherwise try the ubuntu [Alternate CD]("http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso") next.  If even that can't detect the disk partitions correctly, you might consider backing up the XP data files if possible (to a USB or other hard disk) and wiping the drive clean with [this]("http://dban.sourceforge.net/"), and then try to partition it with gparted (either the version on the ubuntu live cd or the [Gparted live cd]("http://gparted.sourceforge.net/livecd.php")).

---

### Post by Can+~ on 2007-10-15
Thanks for your help logos34, but here's what happend:

-First, when he bought the HDD (3-4 years ago I think) he installed it and windows recognized 32GB of the 80GB available.
-He used a diskette (how old) to install a samsung provided tool, that created a partition at the beginning of the HDD, to fix this issue. This diskette was provided for users with old MoBo that don't recognize more than 32GB.
-Now that we installed ubuntu, that partition and tool caused problems. Even the Bios didn't recognize de 80GB, only windows.
-We added the jumper, and both BIOS and winodws recognized the HDD perfectly. But that tool was installed.
-Made a backup of the HDD and formatted using Gparted.
-Now all works fine.

;D. Thank you. This is [solved]

---

