---
title: "Probs with Wine / well the whole system... Help!"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by jannen on 2008-07-19
HELP

Couple days ago I was running the usual updates but the updates hanged at one point with this message:

"E: /var/cache/apt/archives/wine_1.0.0-1ubuntu4~hardy1_i386.deb: unable to install new version of `./usr/bin/wineserver'"

Now Wine wont work at all, and I cant even remove it! The usr/bin files are read only cant delete anything.

Might be related to when I start Ubuntu it wants to run Fdsk, but it always hangs but if I let it run I get a bunch of error messages where one says "The root filesystem is currently mounted read only mode..."

Any idea what do next, PLEASE. I have Acer laptop, 100GB harddisk... running Ubuntu 8.04 with all updates run except the last one with wine.

Thanks:confused:

---

### Post by PmDematagoda on 2008-07-19
Do you have the Ubuntu Live CD with you? If so, boot the PC with the Live CD and post the output of:-
```
sudo fdisk -l
```

---

### Post by jannen on 2008-07-19
Hi thanks... I did what you asked, heres what i have:

[B]Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45b3296d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11879    95418036   83  Linux
/dev/hda2           11880       12161     2265165    5  Extended
/dev/hda5           11880       12161     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ [/B]

I installed Ubuntu on the whole 100GB with no manual partitioning. I have no clue about whats happening with the 'mounted' drives etc... Please let me know if I need do further tests etc. Many thanks for your help!!!

---

### Post by PmDematagoda on 2008-07-20
Ok, while in the Live CD, open up a terminal and execute(Assuming that you selected the file system as ext3!!):-
```
sudo e2fsck /dev/hda1
```
if it shows up any errors, post them here.

---

### Post by jannen on 2008-07-20
Hi!

I run now the following from the live CD>

ubuntu@ubuntu:~$ sudo e2fsck /dev/hda1
[B]e2fsck 1.40.8 (13-Mar-2008)
/dev/hda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes

Inode 958763 was part of the orphaned inode list.  FIXED.
Inode 958972 was part of the orphaned inode list.  FIXED.
Inode 958974 was part of the orphaned inode list.  FIXED.
Inode 958978 was part of the orphaned inode list.  FIXED.
Inode 1812629 has illegal block(s).  Clear<y>? yes[/B]

This list contiuned I cleared a lot of stuff, answering always Yes. Wasnt sure what else to do!

Ended process with this text:

[B]/dev/hda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hda1: 168635/5963776 files (0.9% non-contiguous), 1427693/23854509 blocks[/B]

Now restarting Ubuntu have NEW problem... I come up to the desktop and I can see my desktop image, but the title bars (where menus are) flicker for a while then disappear totally, leaving me only the desktop image. Somethings gone wrong... could you help me how sort this one. I tried fix with recovery mode but no help.

Please... need more help! :confused:

---

### Post by PmDematagoda on 2008-07-20
When you boot Ubuntu in Recovery Mode, execute:-
```
apt-get install ubuntu-desktop && apt-get install --reinstall metacity
```
and see if that fixes the problems to some extent.

---

### Post by jannen on 2008-07-20
Tried that in recovery, however get message:

**Ubuntu/Desktop is already the newest version**

Restarting Ubuntu, gets me thru logging screen to my desktop, but the menu/title bars flicker for few secs then disappear...
Please dont tell me I need to reisntall all Ubuntu again!:confused:

---

### Post by PmDematagoda on 2008-07-20
Are you using Compiz-Fusion by any chance?

---

### Post by jannen on 2008-07-20
No Im not...
At moment my only internet access is through live CD...

---

