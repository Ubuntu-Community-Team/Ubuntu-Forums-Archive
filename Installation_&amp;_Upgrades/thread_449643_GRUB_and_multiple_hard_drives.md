---
title: "GRUB and multiple hard drives"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by paultomo on 2007-05-20
Just installed Ubuntu but having a few problems getting it to boot using GRUB, the hard drive numbering seems to be confused.

My primary drive is a SATA drive with XP on it and I also installed Ubuntu onto this. It now has 4 partitions, XP system, NTFS data, Ubuntu / and a swap. I also have a slave IDE drive which is from a previous computer and still has windows 2000 installed which I don't use, but it has lots of data I want access to.

I installed Ubuntu using the live cd which went ok and GRUB was setup on hd0. When I restarted however GRUB didn't appear and XP booted. Reading through the forms I found threads regarding re-installation of grub using the live cd which i tried but didn't work. I did notice however that when I searched for /boot/grub/stage1 that it was on (hd1,2), I expected it to be on (hd0,2). I then tried setting up grub on hd1 instead and on restart the grub menu came up. Unfortunately when I selected Ubuntu I got an error message saying that the partition couldn't be found. I then chose XP and win 2000 booted. Restarting and choosing win 2000 booted XP? Opening the entries on the grub list Unbuntu is on (hd1,2), XP is on (hd0,0) and win 2000 is on (hd1,0). Also in the XP entry are the following lines:
map [hd0,0] [hd1,0]
map [hd1,0] [hd0,0]
There seems to be some confusion as to the hd numbering but I can't work out where, how or why. Does anyone have any suggestions as to what went wrong and how to rectify it? I'm considering unplugging the IDE drive, re-installing Ubuntu so there shouldn't be any numbering confusion, then re-connecting the IDE drive.

---

### Post by confused57 on 2007-05-20
> **paultomo said:**
> Just installed Ubuntu but having a few problems getting it to boot using GRUB, the hard drive numbering seems to be confused.

My primary drive is a SATA drive with XP on it and I also installed Ubuntu onto this. It now has 4 partitions, XP system, NTFS data, Ubuntu / and a swap. I also have a slave IDE drive which is from a previous computer and still has windows 2000 installed which I don't use, but it has lots of data I want access to.

I installed Ubuntu using the live cd which went ok and GRUB was setup on hd0. When I restarted however GRUB didn't appear and XP booted. Reading through the forms I found threads regarding re-installation of grub using the live cd which i tried but didn't work. I did notice however that when I searched for /boot/grub/stage1 that it was on (hd1,2), I expected it to be on (hd0,2). I then tried setting up grub on hd1 instead and on restart the grub menu came up. Unfortunately when I selected Ubuntu I got an error message saying that the partition couldn't be found. I then chose XP and win 2000 booted. Restarting and choosing win 2000 booted XP? Opening the entries on the grub list Unbuntu is on (hd1,2), XP is on (hd0,0) and win 2000 is on (hd1,0). Also in the XP entry are the following lines:
map [hd0,0] [hd1,0]
map [hd1,0] [hd0,0]
There seems to be some confusion as to the hd numbering but I can't work out where, how or why. Does anyone have any suggestions as to what went wrong and how to rectify it? I'm considering unplugging the IDE drive, re-installing Ubuntu so there shouldn't be any numbering confusion, then re-connecting the IDE drive.

In the grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hd1,2) to (hd0,2), then press "b" to boot...this is temporary if it works, but it can be made permanent in your /boot/grub/menu.lst.  Once you get Ubuntu booted, you can just change the title of your XP & Win200 entries.

---

