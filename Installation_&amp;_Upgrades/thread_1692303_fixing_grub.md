---
title: "fixing grub"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by teddy92 on 2011-02-21
hi!
recently i installed windows 7 :evil: on my system and obviously ubuntu didn t boot again :)
i tryed to restore grub in all ways i found but i failed..at last i installed a new copy of ubuntu on the swap partiotion and it worked, but so i haven t got a swap partition anymore :(
is it possible to reinstall grub from scratch on the first partition?
this is my fdisk -l:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08520852

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97654784   83  Linux
/dev/sda2           12158       17637    44008448    7  HPFS/NTFS
/dev/sda3           17637       29794    97655808   83  Linux
/dev/sda4           29795       30401     4875727+  82  Linux swap / Solaris

Disk /dev/sdb: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         489     3921856    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(487, 254, 63) logical=(488, 65, 25)

---

### Post by YesWeCan on 2011-02-21
Hi. This is linux, you can do anything. :)
But I'm not sure what you mean and what you are trying to achieve. sda4 is listed as a swap partition.

---

### Post by teddy92 on 2011-02-22
> **YesWeCan said:**
> Hi. This is linux, you can do anything. :)
But I'm not sure what you mean and what you are trying to achieve. sda4 is listed as a swap partition.
i want to rebuild grub on the first partition because i messed up the old one :)

---

### Post by Quackers on 2011-02-22
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

