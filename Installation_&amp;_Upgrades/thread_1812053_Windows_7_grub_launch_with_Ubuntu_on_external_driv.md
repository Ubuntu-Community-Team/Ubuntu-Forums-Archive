---
title: "Windows 7 grub launch with Ubuntu on external drive"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by 1234blizzard on 2011-07-25
Hello,

So right now, I have a system set up so that Windows 7 is on the internal drive while my Ubuntu 10.04 is on a External USB Hard Drive. When I launch my computer, it will automatically boot into Windows 7. I can also get into my Ubuntu system through the boot menu. I want to add Windows 7 into my grub but I can't seem to do it.

sudo fdisk -l /dev/sda shows as:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x667dbdca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30394   244035584    7  HPFS/NTFS
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Thanks!

---

### Post by Quackers on 2011-07-26
Boot into Ubuntu and open up a terminal then run ```
sudo update-grub
``` and you should see the Windows Loader appear as grub.cfg is run.
If you do, reboot then go into your bios settings and put the external drive before the internal drive in the boot order settings.
Save the changes and reboot.

If your external drive is connected in future you should see a grub menu giving you the choice of which OS to boot.
If the external drive is not connected at boot, your internal drive should boot Windows directly.

---

### Post by 1234blizzard on 2011-08-30
I have figured out my problem. This was the code I had to add. 

title Windows 
map (hd0) (hd1) 
map (hd1) (hd0) 
rootnoverify (hd1,0) 
makeactive #if you use Windows7 this line should be commented out 
chainloader +1

---

