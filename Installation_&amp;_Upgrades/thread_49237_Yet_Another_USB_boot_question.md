---
title: "Yet Another USB boot question"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by ol_geezer on 2005-07-15
OK, I have tried the install every which way to Tuesday.

What I am running into is that the BIOS will boot from the USB drive, but GRUB complains that it can't find the correct partition no matter where I tell it the boot partition is.

I told the install to put GRUB on the USB drive (sda) partition #1   <(sda,1)> or
< /dev/sda> or <(sda0,1)> etc.
 
Part of the problem is that there is no map of partitions in the installer that uses the same nomenclature as GRUB.

setup:  IBM thinkpad A31 running Windows XP

Internal IDE drive (hd0,1 - the data partition, and 4 - another hidden service partition - where I think the current boot partition is)
external USB drive (sda,1  - /  and 5 swap)

Which is the correct partition to put GRUB on so it can see the boot partition?  I tried putting it on the XP partition, but that failed, and I had to do an fdisk /MBR to recover.

Thanks for any help

---

