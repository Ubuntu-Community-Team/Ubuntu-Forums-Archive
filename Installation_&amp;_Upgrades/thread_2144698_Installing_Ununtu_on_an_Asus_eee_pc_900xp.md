---
title: "Installing Ununtu on an Asus eee pc 900/xp"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by mathtone on 2013-05-13
Hi!

Im trying to install Ubuntu 13.04 on my netbook, but keep getting errors when formatting the hard drives. The inserted hard drive is an 16 gigabyte SSD. On some other sites i read that it is best to use AHCI instead of IDE but this does not appear to be an option in the BIOS.

This is the error I get:  "the File System Creation In Partition 1 Of Sci1 (0,0,0) (sda) Failed" 
And: "Libparted Bug Found!: input/output error during read on /dev/sda"
And: "Invalid partition table on /dev/sda - wrong signature b77b"


Anyone got any tips or advice?

Thanks in advance!

---

### Post by dino99 on 2013-05-13
follow that thread  [http://ubuntuforums.org/showthread.php?t=2033027&p=12129337#post12129337](http://ubuntuforums.org/showthread.php?t=2033027&p=12129337#post12129337)

---

### Post by coldraven on 2013-05-13
I thought that I had posted about this before but I cannot find it. So from memory here is a couple of tips.
If you update the BIOS the fan will run much quieter. See my post in this thread:
[http://ubuntuforums.org/archive/index.php/t-2027964.html](http://ubuntuforums.org/archive/index.php/t-2027964.html)

You should have a small 8MB partition labeled "BIOS", if you update the BIOS copy the new 900.ROM here, rename the old one to 900.bak.
You can hide this partition later by editing fstab.

To install Linux switch of "Boot Boost" in the BIOS otherwise it will be reading the file 900.ROM from disc.

My eeepc 900 has a 4GB and a 16GB SSD.
I put / on the 4GB and /home on the 16GB but I suggest you also put /tmp on the 16GB because you will soon run out of room on the small drive.
It is running Xubuntu 12.04, everything worked straight away but now complains that there is not enough room for updates.

---

### Post by mathtone on 2013-05-13
Im already running the newest BIOS version.

The tread about SSD's was interesting but i didn't find what to look for in it

---

