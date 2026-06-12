---
title: "moving GRUB to another HDD"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by fjodork on 2007-08-19
Hi.

I got 3 hdd in my pc, 1: ide hdd with xp install, 2:SATA hdd with ubuntu and 3: SATA with FAT32 for storage from both OS.

Im using GRUB and its installed in HDD1 MBR, but that hdd is faulty(hw damage) and needs replacement, so i want to install GRUB on HDD2 and install XP again on a new disk and just a reference to it in the GRUB menu.

Exactly how do I reinstall/move GRUB to HDD2 without to have to reinstall Ubuntu?

Thx in advance.


Br fjodork

---

### Post by bulldog on 2007-08-19
Just reinstall GRUB with the live cd.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Just keep an eye on which disk you put it on.

---

### Post by fjodork on 2007-08-19
Ok. Great. Ill give it a try when I get my new hdd back. 

Br fjodork

---

