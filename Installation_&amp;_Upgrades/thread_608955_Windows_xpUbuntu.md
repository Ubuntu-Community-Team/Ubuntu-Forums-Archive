---
title: "Windows xp/Ubuntu"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by dragonflyy on 2007-11-10
I had windows xp previously installed on my system. I decided I wanted to dual boot Ubuntu 7.10. I have done this in the past with Fedora with little to no problems, but I can't get this to work right.

Both XP and Ubuntu work fine (I have to edit my BIOS to change my boot drive each time though.) I had XP installed on my SATA drive (hd2,0) and put Ubuntu on my Primary IDE drive (hd0,0) Everything works fine except GRUB ... when I select WIndows XP it says BOOTMGR is missing. Windows XP doesn't use BOOTMGR it uses NTLDR which is present on the drive. I googled the BOOTMGR message and all I get is information on Windows Vista ... I don't have Vista anywhere on any drive. Can anyone help me out here? I have played with the menu.lst file and still get the same error everytime. Also is there a command/program that will show me which drive is where? (as in what hd0 is and hd1 and hd2?)

Thanks in advanced ..
DragonFlyy

---

### Post by louieb on 2007-11-10
Since I don't have a sata ide mix can't remember the exact fix. But It has to do with adjusting the /boot/grub/device.map file.
This thread will get you in the right direction.[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by dragonflyy on 2007-11-10
title		Microsoft Windows XP Professional
map (hd0) (hd2)
map (hd2) (hd0)
rootnoverify (hd2,0)
savedefault
chainloader	+1

This is the XP info in my menu.lst .... Everything loads fine until I select this and then it says can't fine BOOTMGR.

---

### Post by oilchangeguy on 2007-11-10
try this, i've got my two ide drives set up like this way. and no problems.

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

