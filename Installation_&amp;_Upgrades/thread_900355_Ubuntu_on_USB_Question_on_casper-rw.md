---
title: "Ubuntu on USB: Question on casper-rw"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by karthikb23 on 2008-08-25
Hi,
I have installed Hardy on USB, with an attempt to make it persistent, with the following partitioning.

/dev/sda1 - 2GB FAT32 - Contains GRUB
/dev/sda2 - 1.2GB ext2 FS- casper-rw
/dev/sda3 - 750MB FAT16 - Contains Hardy ISO

Using GRUB i am able to boot into Ubuntu with no issues.
However, my run is not persistent.
(Also, one of the said bugs about the hardy initrd: i.e. the partition containing the ISO does not mount automatically after start up)

What is this parition 'casper-rw'? Does the kernel (or something else) recognize this label and maintain settings? (Strict warnings about keeping label as 'casper-rw' in all guides).

I have tried manually mounting this partiiton, and thereafter change my wallpaper/make some directory, but this is not saved.
Also, the kernel runs off the RAM FS, and thereby all my settings are lost.

Any suggestions/inputs anyone?

---

### Post by karthikb23 on 2008-08-26
Well guys, the reason is that the casper script in the initrd, which performs certain functions during boot looks for a partition with label "casper-rw", and tries to mount this partition during boot up, if available.

Hence the reason.

---

