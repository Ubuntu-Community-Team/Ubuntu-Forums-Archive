---
title: "partition help for windows 7 install"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by jdmBlue on 2010-05-12
When formatting a partion for windows should the existing FAT16 bootable partion be completety replaced by formatting to NTFS?

---

### Post by jonnny_j22 on 2010-05-12
Windows 7 does need ntfs, but you won't need to worry too much. when you install windows 7, select custom install and you will see the latest version of the partition editor. you can resize and create new partitions in this editor, though i recommend making a windows readable partition in gparted as it's easier then selecting and formating it in the windows instilation.

Remember that windows must have a primary partition, likes to be the first os on your drive and the mbr will write over your current bootloader, so don't worry when you restart and it just goes straight into windows, you just need to run the live cd and set the grub loader back up!

---

### Post by darkod on 2010-05-13
I agree with creating ntfs partition in advance, especially for win7.

If you have a single hdd and plan to dual boot, you should not have useless partitions on it (because the limit is 3 primary + extended). And the win7 boot partition is useless.

And if you already have some FAT16 on it, one less to work with.

What I have noticed about win7 is that if you use the installer partition manager to create your win7 system partition, it automatically creates the small 100MB boot partition and you can't skip that.

But, even if you don't have ubuntu installed on the disk, if you boot with the cd in live mode, use Gparted to create one ntfs partition with the size you want for win7, and then boot the win7 install dvd, you just tell the installer to use the existing ntfs partition and it doesn't create the 100MB one. That way you save a primary partition.

---

