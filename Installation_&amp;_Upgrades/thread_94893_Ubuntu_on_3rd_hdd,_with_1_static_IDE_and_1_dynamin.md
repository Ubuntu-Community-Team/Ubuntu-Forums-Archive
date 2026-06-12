---
title: "Ubuntu on 3rd hdd, with 1 static IDE and 1 dynaminc SATA HDDs installed"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by Falchion on 2005-11-25
Greetings all,
New around these parts, and I'm planning to install Ubuntu soon. But first I would like to check with the people in the know if this install plan would work.

some background:
My current system has 1 IDE hdd installed on the Primary channel as master and it has two static NTFS partitions on it, one of which has WinXP installed.

I also have a STATA hdd installed on that same machine, and it has 5 NTFS dynamic partitions on it, which I use to organinze my data.

I also have one DVD-RW and one CD-RW installed (this may be important later)

I just recently uncovered a spare hdd and instead of running the risk of messing around with my primary hdd, I'm thinking of slotting this hdd into the primary ide channel as slave and installing Ubuntu on it.
I believe that this will work since on POST, it always lists the primary slave slot as being empty. And I believe that my motherboard has a build in SATA controller to handle the SATA drive so that IDE and SATA are seprate.

On that third hdd, I will use it only for Ubuntu and configure partitions just for it. At this point, will the installation work? (I'm thinking most likely)

Next question. Say I make a fat32 partition on that 3rd hdd with the plan that I have some stratch space to share files between ex3 and NTFS, instead of just being restrained to only reading from the NTFS.
Will this plan work?

I actually have one last question but I actually think it's more of a Winxp question than a Linux question. It involves the drive lettering of static drives over dynamic drives (made worse with two cd-roms in question). I ask this because I am worried that a new static partition would "take over" a drive letter that is already in use by a dyanimc partition, which would then "re-letter" the whole lot of them, causing applications to break.

Thank you all for your help.

---

### Post by yesplease on 2005-11-25
You can use the third hard disk for ubuntu. I would format the partitions in ext3, the swap partition has its own format, but this is all arranged during install.

When you want a FAT partition, leave some empty space and format this after install. However, it is possible toe read ext3 from windows (with explore2fs) and read ntfs fromm ubuntu. This covers many situations.

It is possible to give fixed drive letters to partitions and drives in windows, for instance by putting your CD players on Y and Z.

---

