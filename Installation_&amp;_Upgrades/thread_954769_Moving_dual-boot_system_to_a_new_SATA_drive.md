---
title: "Moving dual-boot system to a new SATA drive"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2008-10-21
My sister has a computer with two drives: one with Win2K the other with Ubuntu 8.  Alas, the motherboard died, and instead of getting a new one she bought a new computer with a 500Gig SATA drive.  That means that we can't just do a drive transplant.  I know we can use Ghost to move the Windows drive to the first part of the new drive, but how do we move the Ubuntu drive?

Also, of course, I'll need to get Grub installed.  I presume I can use a LiveCD to boot, and use that to install Grub, but I'll probably need to edit both menu.lst and /etc/fstab to get it right.  I presume that I can label the partitions and use those instead of device names (That's what I do on my own box under Fedora.) but any pointers to possible "gotchas" will be appreciated.

---

### Post by Pumalite on 2008-10-21
You can use clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)
To reinstall Grub; if you need to:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
To edit menu.lst; post back when you get there.

---

### Post by sideburns on 2008-10-21
OK.  I think I understand, but there's a few questions I'll need to ask, JIC.  First, the documentation refers to naming the image.  If I'm just cloning the drive to its final destination, does it matter what I name it, and if so, why.  Second, as I'm going to be cloning two 80 Gig drives onto one 500 Gig, should I partition the drive first?  Last, will I need to worry about having a separate /boot partition on the new drive?

---

### Post by sideburns on 2008-10-22
Ok.  I've got everything across, and Ubuntu boots if I edit grub.  (I have to change (hd1.0) to (hd0,0).  I thought I'd changed grub.conf, but I guess I need to change menu.lst as well.  Not a major issue.  Alas, I still can't get Win2K booting.

Originally, the old machine had two hard drives, with Windows on the first, Ubuntu on the second.  Now, they share a 500Gig drive with Windows at the front.  Due to a bit of messing up in the partitioning, the Ubuntu partition is listed as #1, and Windows as #3.  I made sure the Windows partition was marked as bootable.  Do I need to play around with mapping the drives to get Windows to boot, or do I just need to be sure which partition Grub thinks it is?

[Edit]
Never mind.  I found out that it's on (hd0,2) by brute force: try each possible number in order until it responded.  Alas, there's still an error, but I'll either find out how to fix it on my own or start an new thread because it's a different issue.

---

### Post by Pumalite on 2008-10-22
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by sideburns on 2008-10-22
We're past that by now.  I have the right info in menu.lst and I've edited boot.ini to get past that problem.  Alas, it still blue-screens and even if I try for a logged boot, I don't find a log file afterword.  I'm not sure what's going on, but I don't think it's a grub or Ubuntu issue anymore.

---

### Post by Shazaam on 2008-10-22
Will Windows boot into "Safe Mode"? If it will try to run a disk check (chkdsk). Once that passes defragment the Windows partition.

---

### Post by sideburns on 2008-10-22
Windows 2K is installed and it won't boot into anything, even Safe Mode.  However, you did give me an idea: use F8 to get a boot menu, select Command Prompt Only and run chkdsk /f, JIC.

Alas, Command Prompt didn't work any better.  We may need to find out Install CD and use that to repair/reinstall.

---

