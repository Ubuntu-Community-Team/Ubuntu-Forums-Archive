---
title: "HELP: Migrating from large HDD to smaller SSD"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by emgee11 on 2012-01-21
Hi all,
 
I'm pretty new to the linux world (using XBMC Live). I originally installed XBMC onto a 500GB HDD several months ago and recently got a 60GB SSD very cheap at Christmas. I'd like to use the new SSD for my XBMC HTPC.
 
I tried Acronis Disk Director and GParted to image the two partitions on my existing drive (/dev/sda1 contains XBMC, /dev/sda2 contains the linux-swap). I had to resize the original partition on /dev/sda1 to a size that would fit on my new SSD /dev/sdb1 otherwise both tools would not clone/image. No problems. I then cloned the HDD to the SSD. But when I boot I get an MBR 3 and MBR 1 error. Looking around, this appears to have something to do with GRUB.
 
I also tried using dd, as in dd if=/dev/sda of=/dev/sdb. However, dd complained I ran out of room (I assume it is doing a 1-to-1 of the entire HDD not just the resized partitions, but also the unallocated space). So no luck that way.
 
The approach that gets me the MBR errors looks like it might be the way to go, I just need to know how to correct the GRUB issues. I'll keep researching, but I hope someone might be kind enough to short circuit some Googling :D time and dead ends.
 
Thank you for your time!
 
Emgee

---

### Post by snowpine on 2012-01-21
You simply need to install GRUB (you have not yet done so).

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by emgee11 on 2012-01-21
Thanks snowpine.
 
Fixed up GRUB and the MBR, got booting properly.
 
I then just had to update fstab as the UUID of the swap partition changed. Once that was updated everything is running properly.

---

