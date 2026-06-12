---
title: "Dual Boot Issue"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by sheardp on 2010-08-13
I currently dual boot Ubuntu and Windows XP. I need to install Windows 7 as well, but that will overwrite the Ubuntu boot loader. This will need upgrading anyway, to take account of the Windows 7 boot loader. So my question is whether I can install Windows 7 and then repair the Ubuntu boot loader, perhaps by reinstalling Ubuntu.

---

### Post by lechien73 on 2010-08-13
Yes, you can indeed do that. You don't need to re-install Ubuntu either. Just boot in from a Live CD, and then follow the instructions in this post: [http://uri.tl/8](http://uri.tl/8) to get Grub working again.

---

### Post by oldfred on 2010-08-13
Besure to install 7 to a primary partition. If you want to directly boot both windows follow these instructions, otherwise windows combines boot loaders into one partition so it can boot both.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by MAFoElffen on 2010-08-13
The only thing to add to "considerations" is that Winodws OS'es like to be in the lower part of the partition table.  

So you might want to move/resize your partitions to allow Win7 to install into (example- sda1 or sda2) before Ubuntu's partition (example- sda3).   Win7 (and other Windows OS'es) is not tolerant about being too far from the root of the disk.  Ubuntu has shown me the it's more tolerant about running in "other" places on the disk than the Windows OS'es.

---

