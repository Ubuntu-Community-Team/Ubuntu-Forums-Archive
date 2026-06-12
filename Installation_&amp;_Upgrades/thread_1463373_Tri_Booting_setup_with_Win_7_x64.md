---
title: "Tri Booting setup with Win 7 x64?"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by Kuki Kid on 2010-04-26
Hey I just want to say hello to this forum, it seems pretty strong. Also I have a question to ask. I am running dual boot on ubuntu 9.1 with windows xp SP3 32 Bit. I would like to add another partition and install windows 7 64 Bit ( I know my hardware will handle it I checked). I don't know much about ubuntu and I was wondering will the bootloader automatically detect a new partition with win 7 x64 on it? Or if what I said made complete nonsense, my direct question would be How do I run Windows xp 32 bit, Ubuntu Fiesty 64bit( 32 bit mabey ) and Win 7 32 bit all on one pc?

---

### Post by blucat on 2010-04-27
Hi, I'm running a setup similar to what you want.  You can install Windows 7 alongside XP, or you can install Windows over XP.  So be careful when you do the install.  When you install Windows 7 alongside XP, when you reboot you will be in the windows bootloader.  It will give you the choice of booting into Windows 7 or previous version of windows (XP).  Ubuntu will not be shown in this boot loader.  You can then use a live linux cd to restore the grub bootloader.  You will need to run a couple of commands in the terminal to restore the grub bootloader.  I don't have the actual commands handy but if you do a quick google search for "restore grub after windows install" you should find it easily.  After you do this you original grub menu will appear.  You can then select to boot into Ubuntu or Windows.
If you select windows, you will be shown the windows bootloader where you can the select Windows 7 or previous version of windows.  I hope this helps.  If you have trouble finding the process for restoring grub let me know and I will try to post a link to it.

---

### Post by oldfred on 2010-04-27
Welcome to the forums - Kuki Kid & blucat

Windows only knows how to boot from an active partition or in Ubuntu the boot flag. The second windows will combine its boot into the boot of the active partition and will not be separately bootable. Also it then allows the install to a logical partition but if you ever remove the first windows it is just about impossible to boot the second windows. Both windows should be in primary partitions.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

