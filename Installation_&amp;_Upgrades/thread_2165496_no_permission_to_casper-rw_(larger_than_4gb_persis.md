---
title: "no permission to casper-rw (larger than 4gb persistent usb drive)"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by jack5 on 2013-08-05
After failing to do a full install of ubuntu onto USB, I decided to create a persistent drive instead. ([http://ubuntuforums.org/showthread.php?t=2164732](http://ubuntuforums.org/showthread.php?t=2164732))

I followed these instructions online:
> 
[LIST=1]
[*]Start by making your persistent bootable USB flash drive. Easy way to do this is by using [UNetbootin]("http://adf.ly/EjFBf"). Pick a small size for persistent, doesn't matter what size. Once you have made it, (shift + del) delete the file called casper-rw.
[*]Next you'll need a partition tool capable of making EXT2 partitions on a USB drive. If your running Ubuntu you can use [GParted]("http://adf.ly/EjFEw"). System > Administration > Gparted
[*]Select your USB drive and Unmount.
[*]Resize the main FAT32 partition to its minimum, no free space is  required on this partition unless you want to use it for other reasons.
[*]Once you have resized the FAT32 partition, you'll want to create a  new partition on the unallocated space, pick the size you want, and  label it casper-rw with the file system EXT2.
[*]Just apply all the changes, and your done.
[/LIST]


After that I boot into Ubuntu 13.04 (I also tried Lubuntu 13.04) successfully, but I am unable to write any documents into casper-rw.

---

### Post by jack5 on 2013-08-05
bump

---

### Post by ubfan1 on 2013-08-05
Is your machine a UEFI machine?  If so, see bug 1159016.  These machines actually use grub instead of syslinux to boot the live media, so the "persistent" addition to the linux boot line in the syslinux files is missed.  You can add the word persistent to the linux line(s) in the /boot/grub/grub.cfg file on your live media and things should work.

---

### Post by jack5 on 2013-08-06
works perfectly. thanks.

---

