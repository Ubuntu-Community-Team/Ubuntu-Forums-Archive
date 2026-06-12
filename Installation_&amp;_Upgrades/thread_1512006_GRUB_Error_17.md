---
title: "GRUB Error 17"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by jef3189 on 2010-06-17
Hello!

I'm trying to fix the partitions on my laptop. 

Here's how it was setup before I made the change:

dev/sda1 ext4 (8 gigs) <-- This is where my original karmic installation was
dev/sda2 ntfs (100 mb) (Windows 7 System Partition thingy)
dev/sda3 ntfs (175 gigs) <-- Windows 7 install

So first I shrunk the windows partition to about 150 gigs, and used the unallocated 25 or gigs and formatted it as ext4 and copied dev/sda1 to it.

Now I have all the same as above now with

dev/sda4 > extended
    dev/sda5 (25 gigs) (COPIED VERSION OF sda1)

so I had two installations of ubuntu and deleted the sda1 partition. Now I get a GRUB Error 17 when I boot. 

I'm in a live CD and I have access to a console, how can I reconfigure GRUB?

Thanks!

---

### Post by bcbc on 2010-06-17
Reinstall the grub bootloader specifying sda5 as your root directory.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

