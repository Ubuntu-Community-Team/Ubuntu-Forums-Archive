---
title: "Buffer I/O error on device fd0"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by regomodo on 2007-06-01
I'm having major issues trying to install any form of Ubuntu. On both the Xubuntu and Ubuntu live cds i get the following error

[xxx.xxx] Buffer I/o error on device fd0, logical block 0
[xxx.xxx] Buffer I/o error on device fd0, logical block 0

I have n idea what this means. I looked round and this error prevented people from booting the live cd. Not so for me.

However, i install Ubuntu and all goes fine. Once rebooted i get a grub-error 17

This ruins my XP partition (can't me arsed to search for the solution to fixmbr as the XP cd doesn't allow recovery command line)

I wipe the drive and fully format the whole drive (not the quick mode). Reinstall XP, and reboot the live cd. Same errors.

Threads suggested only using 1 cd rom drive so i unplug the 2nd. I only have 1 HDD connected and nothing in the USB ports.


WTF is going on?!

---

### Post by regomodo on 2007-06-01
Meh. Well, 7 hours later i can eventually dual boot xp and xubuntu. The intial boot after install failed with fsck. Said it was 4751days since it was last checked. Ermm, yeah. Anyways, it crapped out and restarted. It appears all is fine again, i hope.

Must sleep, its almost  4 am and i open the shop at 8:30

---

### Post by outlaw686 on 2007-06-04
Think I figured it out. Question, do you have a floppy drive on  your computer?
I don't, I just disabled floppy legacy support in my bios and no more error.

Figure its trying to read from a floppy drive that doesn't exist.

lemme know if this fixes it for you as well :p

cheers

---

### Post by regomodo on 2007-06-04
> **outlaw686 said:**
> Think I figured it out. Question, do you have a floppy drive on  your computer?
I don't, I just disabled floppy legacy support in my bios and no more error.

Figure its trying to read from a floppy drive that doesn't exist.

lemme know if this fixes it for you as well :p

cheers

Thing is Edgy never did that. It's no biggy. Xubuntu works fine now and i have no need for the floppy. Might chuck it out

---

### Post by plastichero on 2008-07-07
yeah ...
I got the same error during installation of Xubuntu 7.10 with WUBI. 

in my case the solution was simple. I didn't have any floppy drive attached, yet the installer was looking for FDD. So, from BIOS I disabled the FDD and problem was solved. Hope it worked for you.

---

