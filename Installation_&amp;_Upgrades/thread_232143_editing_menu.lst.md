---
title: "editing menu.lst"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by matoxxx on 2006-08-08
hi
can anyone tell me how should my menu.lst file look like to boot winXP partition

i have single drive formated like this
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         255     2048256   83  Linux
/dev/sda2             256        5099    38909430    5  Extended
/dev/sda3            5100        7649    20482875    b  W95 FAT32
/dev/sda4   *        7650        9729    16707600    b  W95 FAT32
/dev/sda5             256        1275     8193118+  83  Linux
/dev/sda6            1276        4959    29591698+  83  Linux
/dev/sda7            4960        5099     1124518+  82  Linux swap / Solaris
matoxxx@matoxxx-desktop:/boot/grub$

sda4 is the win partition so how should the entry in menu.lst look like

thanks for help

---

### Post by confused57 on 2006-08-08
Looks like the root should be (hd0,3), there's an example of what the Windows entry should look like in your menu.lst, should just be able to use something similar...but use root  (hd0,3).
I'm on XP currently(I know, 40 lashes with a wet noodle), so I can't tell you for sure what my menu.lst entry is.

Just noticed, Windows is on a partition after Linux...may make it difficult to boot Windows...I've seen one person report they are able to do so:
[http://www.ubuntuforums.org/showthread.php?t=225583&page=2](http://www.ubuntuforums.org/showthread.php?t=225583&page=2)

Here's an excellent guide to reinstall grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Good Luck.

---

