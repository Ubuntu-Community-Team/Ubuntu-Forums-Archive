---
title: "Disk not found after install of 18.04"
date: 2019-01-22
forum: Installation &amp; Upgrades
---

### Post by glion on 2019-01-22
Hi, 

I have a fresh WD blue 4TB hard drive. I installed off USB and the disk is not found after boot/restart.

I've tried the boot repair and still no joy. Output from boot repair below.

[http://paste.ubuntu.com/p/34g8vJ3jGh/](http://paste.ubuntu.com/p/34g8vJ3jGh/)

---

### Post by glion on 2019-01-23
Solved for anyone else who's interested.

I created the Ubuntu install USB with Rufus, the "Partition scheme" used as per instructions was set to MBR, as I was installing this on a >2TB HDD, the PC needs to boot the USB with "GPT", as Ubuntu will be installed to boot via GPT as the disk is >2TB. Else you end up mixing MBR with GPT and it wont find the disk.

---

### Post by oldfred on 2019-01-24
With very large drives I prefer not to have the default install of just / (root). It can take longer to run fsck if issues.
Also if drive will ever be used with a newer UEFI system, better to create both ESP - efi system partition (FAT32 300 to 500MB) for future UEFI boot and bios_grub for current BIOS/Legacy boot.

But having too many partitions can be an issue on managing partition & available space. So trade-offs and each user may have what they prefer. My own optimal partitioning plan when a few years old is not them what I would do if doing a new system.

---

