---
title: "How do I tell which internal drive is which, for install?"
date: 2014-11-11
forum: Installation &amp; Upgrades
---

### Post by mlevin77 on 2014-11-11
I am installing Ubuntu 12.04 LTS onto an Apple G5 system. I've got it booted off the live CD and want to install it on one of my 3 internal disks. The  "Home folder" window (in the left hand panel) is showing the 3 disks by name (they have names assigned by Apple OS that's on them) and I know which one I want to wipe and install Ubunto onto. When I ran the install, there are 2 options: "Erase disk and install Ubuntu", and "Something else". I didn't choose the firstone because I didn't know if it would give me the option of choosing the correct disk. Will it, or do I need the "Something else"? When I did choose the latter, the menu is showing the disks as /dev/sda1, /dev/sda2, etc. - how do I figure out which one corresponds to which name?

---

### Post by Impavidus on 2014-11-11
You need the "something else" option. This allows manual partitioning.

To find out which ID correspond to which label, run this command in a terminal in your live session:```
sudo blkid
```

---

### Post by mlevin77 on 2014-11-11
Aha! Excellent, now I see that it's sda3 that I want. Now, I've selected it, and hit "Install Now", but a menu pops up that says "No root file system is defined. Please correct this from the partitioning menu."   What do I need to do to tell it to install Ubuntu onto sda3 (wiping it) and leave the other disks untouched? I think I'm supposed to Edit a partition onto that same sda3 disk as "/" and choose a file system type, but the one it seems to want (Apple_Bootstrap) isn't on the list of available choices :-(

---

### Post by yancek on 2014-11-11
sda3 would be the third partition on the first disk.  Are you sure you have the correct drive/partition.  Are you mixing terminology and using the term "disk" when you mean partition?  Do you have three physical hard drives? In Linux, drives are numbered sda, sdb, sdc, etc with sda being the first hard drive, sdb being the second hard drive and so on.  The numbers after the letters are for partitions so sda3 would be the third partition on the first hard drive.

If you know which partition you want, then in the installer main window you would select that partition by mouse-clicking it to highlight it in the main window and selecting the Edit tab below the window.  One of the options in the Edit window is Mount point where you would select the "/" forward slash, the symbol for root.

---

### Post by mlevin77 on 2014-11-11
Ah, good point. What I have, according to "sudo blkld", is sda3 and sda5, which are on one drive, and sdb2 which is on another drive (why there's no sda1,2,4 I don't know). So, what I want is to leave sdb2 untouched, and to install Ubuntu onto sda3, or if that's impossible, wipe that whole disk and install there. Is that possible?  I did select it in the Edit window, and select the / etc., but it's complaining that Apple_Bootstrap isn't there, and that's not on the dropdown list of available choices. What do I choose to enable my PPC G5 Apple box to work with Ubuntu on that partition?

---

