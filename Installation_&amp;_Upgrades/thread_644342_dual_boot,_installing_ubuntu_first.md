---
title: "dual boot, installing ubuntu first"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by seandiggity on 2007-12-18
A friend of mine just got a new IDE hard drive and installed Ubuntu on it.  He is still not completely comfortable with leaving Windows, so he wants to have it installed on one of the partitions.

I've set up dual boot systems before, but always after Windows was already installed.  In this case, Ubuntu is already installed on the first partition, and there's an empty partition for a fresh Windows XP install.  Is there a recommended way of setting up Windows on another partition after Ubuntu is already installed?  How can I make sure the Windows installer doesn't ruin the MBR (or do any other harm)?

The drive is set up as:

partition 1: Ubuntu ext3, mounted at /
partition 2: swap
partition 3: empty fat32 for Windows
partition 4: empty ext3 for storage

Any suggestions are appreciated.

---

### Post by jken146 on 2007-12-18
Install windows on that empty partition.  It will overwrite the MBR, so you won't get GRUB any more.  That's OK though because you can use a Ubuntu live CD to reinstall GRUB.  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

As for the storage partition, you may be interested in [www.fs-driver.org](www.fs-driver.org) for a Windows driver for the ext2 filesystem (works for ext3 too).

---

### Post by rsambuca on 2007-12-18
Jken gave good advice.  I would just add that you should definitely format the Windows partition as ntfs.  It is a much better filesystem than FAT32, and can still be read and written to from linux.

---

### Post by seandiggity on 2007-12-19
Thanks for the great advice...you confirmed my suspicions about having to restore grub with the LiveCD.  Thanks for the link to that ext2 driver also, I was aware of it but have never used it.

As for the difference between fat32 and ntfs...I know that ntfs is the better filesystem, but can it be easily resized (e.g. with gparted)?  If not, I'd still like to go with fat 32 because I think my friend will want to shrink the Windows partition when he realizes how little he uses it.

---

### Post by Pumalite on 2007-12-19
Gparted Live CD can resize any format.

---

### Post by Sef on 2007-12-19
Windows should be on the first partition.   If there is enough space on an empty partition, then simply use [Clonezilla]("http://gparted-livecd.tuxfamily.org/") to copy Ubuntu to one of the partitions.  If not, then create a partition which is big enough.

---

### Post by fs3rp4 on 2007-12-19
Before everting do a MBR backup with dd commnad. Easy and relyable

Backup
 dd if=/dev/hda of=mbr.backup bs=512 count=1

Restore
 dd if=mbr.backup of=/dev/hda bs=512 count=1

---

