---
title: "Yet another boot loader problem"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Pugnacious on 2007-10-27
Well, i've been searching around for days now and i must have missed another post like this, but here goes, just in case.

I'll add the menu.lst and fdisk list printout to this post when i get home later tonight (i'm at work), but back to the point:

I have a vista machine with four hard drives.  One IDE and Three SATA.  The IDE is a slave, the SATA1 an old xp drive that i now use for storage, and the Sata2 is Vista and Ubuntu (dual partition)

sdb1 is vista
sdb2 is ubuntu

I installed ubuntu second, and i'd like to get it to dual boot.  When i rebooted after the install, i was greeted by a missing operating system message, so i booted back into the live disk and checked the partitions.  Sure enough, ubuntu was set as the active partition.  I reconfigure it to set sdb1 as active, and the vista boot loader popped up to greet me.  

I used EasyBCD to add a link in the vista boot loader to sdb2, and i correctly get grub when i select it.

However, when i try and get into grub no matter what partition i select as root, it gives me errors.  I'll post them when i get to the machine to write them down.

Anyone know off hand how to make this configuration work?  I also noticed that the IDE was set as active as well, would that cause the problem?  I would like to be able to select ubuntu from the vista boot loader and have it correctly load up grub and then ubuntu.

---

### Post by Computer Guru on 2007-10-27
Your "root(x,y)" line in GRUB's /boot/grub/menu.lst file is wrong.

Replace that with "find --set-root /boot/kernel******" where the kernel name is the same as the one on the next line.

---

### Post by Pugnacious on 2007-10-27
Thanks i'll try that out.  I've already tried something similar, but not exactly.

**Update:

I got it working finally.  Inside the live CD it tells me that it's on (hd2,1), but after alot of trial and error, it turns out that linux sees it as on (hd0,1), and for some reason when the installer was run it saw it on (hd2,1).  No idea why, but it's working now.

---

