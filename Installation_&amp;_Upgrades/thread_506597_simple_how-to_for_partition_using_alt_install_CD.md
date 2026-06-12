---
title: "simple how-to for partition using alt install CD?"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by neatokino on 2007-07-21
I'm trying to install Feisty on a 1st Generation Macbook Pro, dual boot OSX/Ubuntu.  There are tons of how-to's, and I've read through many of them, but I can't understand what I need to do when asked to partition the hard drive in the install.

I'm using the alternate install CD, as recommended in all the how-to's.  I've installed bootcamp and refit, so there is a (13G) partition set aside by boot camp on which to install Linux.

I'm following the installation guide in the wiki, and here's the instruction that hangs me up:

> At step 4, "Prepare disk space", choose Manually edit partition table and click Forward. Delete /dev/sda3 (and /dev/sda4 if it exists) from /dev/sda. Create an ext3 partition taking up all but 512MB of the disk and mount it on /, and create a swap partition taking up the remaining 512MB. Click Forward.

If that's supposed to be self-explanatory, it isn't!  Can anyone provide a really easy how-to, assuming I know nothing whatsoever about deleting or creating or mounting partitions during the install?    I'm lost!

TIA

---

### Post by confused57 on 2007-07-21
> **neatokino said:**
> I'm trying to install Feisty on a 1st Generation Macbook Pro, dual boot OSX/Ubuntu.  There are tons of how-to's, and I've read through many of them, but I can't understand what I need to do when asked to partition the hard drive in the install.

I'm using the alternate install CD, as recommended in all the how-to's.  I've installed bootcamp and refit, so there is a (13G) partition set aside by boot camp on which to install Linux.

I'm following the installation guide in the wiki, and here's the instruction that hangs me up:



If that's supposed to be self-explanatory, it isn't!  Can anyone provide a really easy how-to, assuming I know nothing whatsoever about deleting or creating or mounting partitions during the install?    I'm lost!

TIA
This guide has some excellent screenshots of the alternate cd, see the sections Ubuntu+FAT32 & Ubuntu&NTFS:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by neatokino on 2007-07-22
Thanks!  All done... am posting this now from Macbook Pro and Ubuntu, wireless, even!!!!!

---

