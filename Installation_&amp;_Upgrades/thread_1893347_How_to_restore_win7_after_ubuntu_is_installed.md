---
title: "How to restore win7 after ubuntu is installed"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by kay21s on 2011-12-10
Hi, 

Since I have an APU machine, after win7 installed, I install ubuntu alternative.
When selecting partition, it doesn't recognize the win7 partition, and take the whole disk space as free
I used the last 100G for installing ubuntu

after installation, the disk is like this: 400GB free space, 100GB ubuntu
and I even couldn't install win7 on the 400GBfree space again, since it tells the area is of GTA or something else format

Can I restore win7 and its data?  I have some important data in original partition.

Thanks so much.

---

### Post by editheraven on 2011-12-10
Try with testpart [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) . Post the output of sudo fdisk -l

---

### Post by hansdown on 2011-12-10
Welcome to the forum, kay21s.

Try this tutorial.

[http://www.youtube.com/watch?v=dMTL_-XJjyU](http://www.youtube.com/watch?v=dMTL_-XJjyU)

---

### Post by kay21s on 2011-12-10
> **editheraven said:**
> Try with testpart [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) . Post the output of sudo fdisk -l

Thanks, it is helpful. I have found back the partitions of windows 7, but however, after I still cannot boot win7.
After select it to boot from grub, the screen goes dark, should I repair MFT?

fdisk:
------------------------------------------------
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf7a010e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
------------------------------------------------

from the test_disk
------------------------------------------------
 1 P MS Data                     2048     206847     204800   [win7 reserved]
 2 P MS Data                   206848  104325119  104118272 [win7 system C:/]
  3 P MS Data                104325120  515969023  411643904 [win7 partition E:/]
  4 P Linux Swap             515969024  537258086   21289063 [linux swap]
  5 P MS Data                537258087  976773118  439515032 [linux root]
------------------------------------------------


What should I do next? Rebuild the boot sector? repair the MFT?

Thanks

---

### Post by kay21s on 2011-12-11
Anybody can help?
I have restore MFT and boot sector with disk test, however, I still cannot enter win7

Thanks,

---

### Post by editheraven on 2011-12-11
Try this : [http://www.smipple.net/snippet/voyeg3r/How%20to%20add%20Vista%2FWindows%207%20partition%20to%20Grub%202%20%28Ubuntu%209.10,%20Karmic%20Koala%29](http://www.smipple.net/snippet/voyeg3r/How%20to%20add%20Vista%2FWindows%207%20partition%20to%20Grub%202%20%28Ubuntu%209.10,%20Karmic%20Koala%29) . Having windows and linux on same hdd (meaning only one mbr code for both of them) is not a good idea. 

Before doing the stuff in the link try this

sudo update-grub
sudo *grub*-mkconfig

---

### Post by Mark Phelps on 2011-12-13
Try using Boot-Repair to restore the Win7 boot:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

