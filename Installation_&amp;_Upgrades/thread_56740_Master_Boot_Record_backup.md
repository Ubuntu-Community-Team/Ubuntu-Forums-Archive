---
title: "Master Boot Record backup"
date: 2005-08-13
forum: Installation &amp; Upgrades
---

### Post by Trexx on 2005-08-13
Hello,

 I have searched google for an answer for this, but what I found was something that I cannot seem to do.

 I was wondering if anybody could tell me how to go about backing up my MBR, so if I need too I could uninstall GRUB and replace it with my original MBR.

 Thanks for your help in advance!

---

### Post by nad on 2005-08-13
dd if=/dev/name_of_boot_drive of=filename bs=512 count=1

This will copy the first sector (512) bytes of your boot drive to file filename. As your boot record is actually only 476 bytes long (the rest being the partition table in binary) if you reconfigure your partitions you should copy back only 476 bytes to restore the mbr. Just reverse the input file (if=) and output file (of=) and change the bytes per sector (bs=) to 476.

You should also keep a text copy of your partition table handy, just in case: parted /dev/name_of_drive print > filename .

---

