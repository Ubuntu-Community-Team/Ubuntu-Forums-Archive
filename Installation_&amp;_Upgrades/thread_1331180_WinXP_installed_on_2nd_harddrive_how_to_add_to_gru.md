---
title: "WinXP installed on 2nd harddrive how to add to grub menu."
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by thex707 on 2009-11-19
Hi,

   I recently added WinXP to my 2nd harddrive which is a slave. I have ubuntu on my first main one. The thing i want to do here is I would like to have the GRUB menu to have WinXP on it so i dont have to go to the BIOS and tell it to load it that way.. I would like my linux drive to be the main one so the GRUB menu will load with the GRUB menu having WinXP so i can boot it from there. 


i dont know if this is needed so u guys know but here is the results from fdisk:

> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9544    76662148+  83  Linux
/dev/sda2            9545        9726     1461915    5  Extended
/dev/sda5            9545        9726     1461883+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4997    40138371    7  HPFS/NTFS




any help is appreciated thanks!

---

### Post by darkod on 2009-11-19
Do you know which grub you have?
The latest 9.10 started shipping with grub2, before that grub1 (or just grub) was used. If you upgraded to 9.10 grub may emained the old version.

If it's the new grub2 adding XP is easy, just running in terminal:
sudo update-grub

should detect it and add correct entry to the grub2 menu. Try that, if you have the old grub come back.

---

### Post by thex707 on 2009-11-19
no i do have the old grub i have ubuntu 9.04..

i assumed tho that the windows would take over even tho it was on the slave spot. but it didn't happen.. thankfully.

---

### Post by darkod on 2009-11-19
OK, then open:
sudo gedit /boot/grub/menu.lst

That is the file controlling the grub menu and booting. At the end you will need to add:

title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

Save and close the file. Reboot and see if it works.

---

### Post by thex707 on 2009-11-19
No, it doesn't work.. It shows "Windows XP" on the GRUB boot menu and when i clicked it it just showed it was "Starting UP" like what it does for ubuntu but its just stays there...


UPDATE:

I got it working!!!! Thanks to you helping me get an idea what had to be done i searched around witht that grub commands and i found something it was suppose to be like this:
> 
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

and i tried it and it worked!!  thanks for helping otherwise i would still be stuck!!

---

### Post by darkod on 2009-11-19
Glad you got it working. I am still not sure when the map command has to be used, I never had to use it myself. :) But the main thing is it's working now.

---

