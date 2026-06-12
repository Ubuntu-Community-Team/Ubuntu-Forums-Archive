---
title: "Can't install Windows 7 again"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by Kidnbe on 2011-08-07
Ok so i don't know if this is the right section beacuse i just created an account to get help.



I just installed Linux, but could'nt manage wine to work with .exe files, the problem is that when i open up a .exe it shutsdown 2 seconds after it opens.
Well i decided to uninstall Ubuntu and install Windows 7 again, but then again i got a problem. I plugged in my Windows 7 disk and restarted my computer then getting the boot cofnigure up, i changed the boot settings to "boot from CD/DVD" but it wasnt able to boot from the pc. I tried to read some guides and they all said that i should reboot with some "floppy" linux cd type in "fdisk" in a command prompt, witch i have no clue what is. I tried to put my Ubuntu cd in my computer and boot from that but that did'nt work. Am i stuck with Ubuntu? I won't give a da** if i could fix the wine problem.

---

### Post by mikewhatever on 2011-08-08
Not all Windows programs work in wine. Which ones did you try running? Perhaps there are native Linux alternatives?

To get help with installing Windows, ask at a Windows forum.

---

### Post by Mark Phelps on 2011-08-08
IF you're SURE you have the BIOS boot setting correct, and you STILL can not boot from either a Windows 7 Installation DVD or from an Ubuntu Desktop CD -- there's nothing anyone here can do to help you as your optical drive is failing.

If you CAN get the drive to work, you may then still not be able to install Win7 if the drive is already formatted for Linux -- because Win7 can not understand that filesystem.  You may then have to reboot from the Ubuntu Desktop CD and use Gnome Partition Editor to remove ALL the Linux filesystem partitions from the drive.  After that, you SHOULD be able to reboot from your Win7 Installation DVD and do the install.

---

### Post by psusi on 2011-08-08
> **Mark Phelps said:**
> 
If you CAN get the drive to work, you may then still not be able to install Win7 if the drive is already formatted for Linux -- because Win7 can not understand that filesystem.

Windows is perfectly capable of deleting partitions it does not understand.

---

