---
title: "Install Ubuntu from hard drive"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by UFer on 2011-07-31
I would like to install Ubuntu (10.10) from an USB hard drive using UNetbooting and others USB Live creators. The problem is, it's formatted in NTFS.

I was thinking of partitioning the USB HD in two: one in NTFS (with all the data i have) and another one in FAT32, so as to install the Live USB there. But how am i going to choose from which partition to boot from when i reboot the PC? Will it automatically boot from the FAT32 partition?

---

### Post by vanadium on 2011-07-31
Simply use a cheap 1 GB USB stick.

---

### Post by UFer on 2011-07-31
> **vanadium said:**
> Simply use a cheap 1 GB USB stick.
The thing is I don't have one, i only have a SD Card (already checked; cannot boot from it at startup).

---

### Post by oldfred on 2011-07-31
If you want something a bit more complicated to set up, but easier to use. Install grub2 to the external drive and directly boot the ISO from grub2. I am doing that from NTFS, FAT32 & a full install on a USB flash. Once set up it makes it easy to copy a new ISO to the partition and edit grub with the new ISO name.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by UFer on 2011-07-31
> **oldfred said:**
> If you want something a bit more complicated to set up, but easier to use. Install grub2 to the external drive and directly boot the ISO from grub2. I am doing that from NTFS, FAT32 & a full install on a USB flash. Once set up it makes it easy to copy a new ISO to the partition and edit grub with the new ISO name.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)
Thanks for the answer. In the end I did one FAT32 partition inside the external HDD (4GB capacity FAT32, the rest NTFS) and with an old version of UNetbooting (for some reason the newest ones wouldn't recognize the drive) installed the Live CD inside the FAT32 partition. Rebooted and the installation process began. Everything went smoothingly just for one little problem that i've already solved ('Installarchive() failed' when installing the WiFi drivers).

So, yes, having an USB HDD drive with two partitions and one with the Live USB works.

---

