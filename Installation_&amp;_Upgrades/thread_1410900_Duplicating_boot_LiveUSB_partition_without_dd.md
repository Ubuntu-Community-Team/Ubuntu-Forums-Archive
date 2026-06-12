---
title: "Duplicating boot LiveUSB partition without dd ?"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by vanjeje on 2010-02-19
Hello,

***How is it possible to duplicate a working LiveUSB boot partition on another disk, without (nearly) use of dd ?***

I recently bought an external USB disk Samsung S1 Mini 250GB, which is 4kB sector size instead of 512B. LiveUSB creator does not work on it. Nor does GParted. So I wanted to copy without dd or partimage...

I have started a live session from CD. With fdisk -b 4096, I created a FAT partition, mkfs.vfat -F 32 to format it. I mounted, and copied all files from the original partition (on an SDHC card) to the new one (tar cf - * | cd ../dest; tar xvf - ). And copied the MBR (first 446 bytes) using dd. syslinux to make the new partition bootable, but it claims it does not work because of sector size 4096 (not 512). :-( I did not find any workaround for syslinux.
 
But then if I try the same method on a new SDHC card, it boots ok, language menu is displayed, everything looks good (same as CD, same as original SDHC card), except that after a bunch of lines
"/init: line 1: can't open /dev/sr0: No medium found"
boot process stops with
"(initramfs) Unable to find a medium containing a live file system"

***Did I miss some important thing ?***
And any solution for syslinux on 4k sector size disk ?

I tried UNetBootin on Windows, on the SDHC card it is ok with a simple GRUB menu. No boot at all on the 4k sector size disk.

---

### Post by vanjeje on 2010-02-22
Up

Found [this]("http://ubuntuforums.org/showthread.php?p=8865284") and [this]("http://ubuntuforums.org/showthread.php?t=599599&highlight=backup+system+restore+boot")... Still wonder why my LiveUSB partition cloned to a micro SDHC does not completely boot...

---

