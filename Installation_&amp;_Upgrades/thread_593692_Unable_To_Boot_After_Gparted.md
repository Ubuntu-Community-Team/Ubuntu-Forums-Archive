---
title: "Unable To Boot After Gparted"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by mgaskell on 2007-10-27
Help! I am trying to set up Gutsy on my desktop. I have been using Ubuntu on my laptop for some time. After defraging my Windows XP partition to make room for Gutsy, I booted to a stand alone copy of Gparted on my CD drive. I had two partitions, a small FAT 32 partition created by HP for recovery information and a NTFS partition for Windows XP. The FAT 32 partition was labeled /dev/hda1 and the NTFS partition was labeled /dev/hda2. Using Gparted I removed the FAT32 partition, moved the NTFS partition to the beginning of the drive, resized the NTFS partition to make room for Gutsy and created a new ext3 partition for Gutsy.

I now have two partitions. The NTFS partition is at the beginning of the drive and is labeled /dev/hda2. The ext3 partition is next and is labeled /dev/hda1. I can no longer boot to Windows XP. Booting to the Gutsy installation CD I can access the files on the NTFS partition. I stopped here. I don't want to continue with the Gutsy installation until I fix the boot problem.

Thanks in advance.

---

### Post by taurus on 2007-10-27
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by mgaskell on 2007-10-27
Thanks. I downloaded and burned the iso file. I booted to SGD. I believe I've tried every option on SGD to repair my Windows boot with no luck. Every time I try to repair the Windows boot nothing happens. I probably need some hand holding here as I'm not savy on boot records. /dev/hda2 is the ntfs partition at the beginning of the disk (after I moved it there using Gparted) with the previous Windows files. /dev/. hda1 is the ext3 formatted partition that is empty. Does the Windows partition have to be /dev/hda1 ?

Should I go ahead with the Gutsy installation and then see if I can boot into Windows? I started to do that but I was afraid that the auto-partitioning scheme in the Gusty install would erase the data in the NTFS partition.

Thanks again

---

