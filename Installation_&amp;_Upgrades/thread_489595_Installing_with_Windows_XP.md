---
title: "Installing with Windows XP"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by flygirl on 2007-07-01
I have an installing question. I only have one hard drive and Windows XP is installed on it. File System: NTFS
Size: 27.95 GB
Used: 5.10 GB
Unused: 22.84 GB 
I need to know how to partition the hard drive before installing Ubuntu. I dont want to install Ubuntu over Windows, I like to have two OS's on my PC thank you.

---

### Post by Pumalite on 2007-07-01
Defrag XP several times.Get rid of all temp files and anything you don't need, then partition the rest. Check your partition with Gparted, format to ext3. Then install>'Guided>Largest Available Space'. In step 5 or 6 you get to a point where you can choose where to put GRUB (bootloader). Let it be hd0,0 Grub will pick up XP and you will have a dual boot system.

---

### Post by louieb on 2007-07-01
To setup dual booting on a single drive.
#1 rule backup anything you don't want to loose it may happen.
#2 rule defrag you windows installation and defrag it again.
#3 run chkdsk on you windows installation.
#4 rule backup anything you don't want to loose it may happen.
 
After you have backed up, defragged and run chkdsk.  The installer  on the live CD should offer to shrink the windows partition and install Ubuntu in the newly empty space. If all goes well dual booting using GRUB for the boot manager / loader will be set up on your computer. 
 
check out the psychocats link in signature for a walk through of the live CD install.

---

### Post by flygirl on 2007-07-01
Hey thanks.

---

