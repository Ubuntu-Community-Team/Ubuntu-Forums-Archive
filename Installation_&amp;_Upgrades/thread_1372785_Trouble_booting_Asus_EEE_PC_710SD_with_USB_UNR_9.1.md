---
title: "Trouble booting Asus EEE PC 710SD with USB UNR 9.10"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by jaydisc on 2010-01-04
Hi guys,

First time poster, please be gentle :)

My nephew has a new Asus EEE PC 710SD which came with the lackluster Xandros distro. We've been trying for a few days now to get UNR 9.10 on it. We have access to OS X machines, but no Windows PCs.

We initially followed the directions at [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) to do so. On the mac, I formatted our 4GB LaCie Iamakey usb drive with a Master Boot Record partition, formatted as FAT16 and used dd if=/path/to/downloaded.iso of=/dev/rdisk1 bs=1m. Now, the actual drive appears to be /dev/disk1, but the FAT16 partition was /dev/disk1s. Using of=/dev/rdisk1 seemed to destroy the MBR partitioning table and install an ISO9660 partition which would not boot. Using of=/dev/rdisk1s1 at least maintained the MBR and FAT16 partition, but again would not boot.

The next thing we tried to do was use Unetbootin under Xandros on the eeepc. To facilitate this, I had to add an etch repository and install mtools and p7zip-full and then unetbootin happily launched. Similarly with Unetbootin, I had the choice of choosing the logical device of /dev/sdb for the restore destination or /dev/sdb1. Again, neither of these resulted with anything I could boot off of. I used fdisk under Xandros to delete the existing partitions, make a new primary, active partition formatted as FAT16, but again, no boot.

Some of the next things I was told to try was to use lilo -M /dev/sdb to make sure the MBR was OK, which it was. And I was also recommended to use syslinux -f /dev/sdb. After using syslinux, I got the furthest I had gotten. I was given a blank gray screen at startup with no readable text. I could hit Esc and was given the opportunity to specify a kernel with a "boot:" prompt, but it seems the kernel on the UNR image is in the /casper/ directory and I don't seem able to specify a kernel that's not in the root directory.

Can anyone give me a few pointers as to how to get this done? Am I doing something wrong? Could it just be an incompatible USB key? If that was the case, shouldn't syslinux not work?

Thanks in advance

---

