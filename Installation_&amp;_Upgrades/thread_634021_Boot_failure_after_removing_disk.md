---
title: "Boot failure after removing disk"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Jonatan_w on 2007-12-07
Hi

I installed Ubuntu 7.10 on my second hard drive (hdb) and kept WinXP on the first one (hda), Install went smooth and I had dual boot functionality with GRUB and Ubuntu was working well. I decided to remove my WinXP harddrive completly from the system because I didnt want to keep XP. However it seems that GRUB was installed into the MBR of hda and thus I couldnt boot anything after removing the drive.

I booted the Ubuntu install CD and I have tried numerous ways to repair grub without success.

Method 1:
Using the installation to setup /dev/hdb1 mount point to /. I cant continue to install grub without formatting partition after making changes to the partition table.

Method 2:
Firstly I write "sudo fdisk -l" gives output:

Disk /dev/hdb: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d6fafa3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4754    38186473+  83  Linux
/dev/hdb2            4755        4963     1678792+   5  Extended
/dev/hdb5            4755        4963     1678761   82  Linux swap / Solaris

Since the disk hda was removed from my system the first disk is hdb then it goes on with hdc, hdd and sda.

I believe hdb1 translates to hd1,0 in grub so I try starting grub and type in "root (hd1,0)"   

"Error 21: Selected disk does not exist"

Grub hasnt always given this answer, earlier (before reboot) it went fine and then when I tried "setup hd1" it responded with "cannot mount partition" 

Method 3:
I mounted the linux system into /ubuntu and then proceeded with "chroot ubuntu" and launched grub from within my system, problem was that no hard drives was listed in /dev so I couldnt configure grub..

Maybe I need to update my hard drive table so that hdb becomes hda or something, im just guessing here anyway Im starting to run out of ideas and also running out of forum threads to look through, I would approciate som help.

---

### Post by Archmage on 2007-12-07
I think the right entry would be root (hd0,1).

But I would suggest to switch the first one to be the master and therefore hda (hd0,0).

---

### Post by Jonatan_w on 2007-12-07
Solved the problem.

After setting my hard drive as master and burner as slave I had greater success. Problem was also that I was inconsistent with using "sudo grub" and "grub" so I had different error messages. Anyways, boot drive as master and "sudo grub".

---

