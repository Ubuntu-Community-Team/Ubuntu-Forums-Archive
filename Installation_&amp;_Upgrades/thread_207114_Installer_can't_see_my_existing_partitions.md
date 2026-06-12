---
title: "Installer can't see my existing partitions"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by phelge on 2006-07-01
Hello,

I would like to try ubunu 6.06. During the installation on hard disk, the installer can't see my existing partitions of my 200Gbytes HD. It proposes to erase the whole disk. I've several OS installed and have no problem at all for mounting/using these partitions.

I googled and found some users reporting this issue but no obvious solution. Can someone help me ? Thanks

Here is the content :
# fdisk -l /dev/hda
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+   7  HPFS/NTFS
/dev/hda2   *        2551       19225   133941937+   5  Extended
/dev/hda3            7720       10269    20482875    7  HPFS/NTFS
/dev/hda4           10270       11544    10241437+   c  W95 FAT32 (LBA)
/dev/hda5            2551        2680     1044193+  82  Linux swap / Solaris
/dev/hda6            2681        5229    20474811   83  Linux
/dev/hda7            5230        7719    20000893+  83  Linux
/dev/hda8           11545       14114    20643493+  83  Linux
/dev/hda9           14115       16675    20571201   83  Linux
/dev/hda10          16676       19225    20482843+  83  Linux

---

### Post by adityavb on 2006-08-02
yea...got your problem...if you can see, the cyinder numbers for primary partitions /dev/hda3 is 7720-10269 and for /dev/hda4 is 10270-11544 .While the range for extended partition is 2551-19225 . SO the problem is that the cylinders from 7720-111544 (hda3+hda4)  are being counted twice , once in hda3/4 entries and once in extended partition entry. 

To correct this problem , you need an automatic utility called "Partition Table Doctor" from windows , or you need to manually edit your partition table from linux, which I am not expert in.Please look around on the forums for that....feel free to mail me if you need any more help.

---

### Post by adityavb on 2006-08-02
sry ..posted by mistake ..mods can delete this

---

### Post by adityavb on 2006-08-03
Well all operations wid partition table are potentially dangerous, I have never edited it manually , but with partition table doctor I had a good experince , it was fixed in no time. So my advice is use  the partition table doctor in windows

---

