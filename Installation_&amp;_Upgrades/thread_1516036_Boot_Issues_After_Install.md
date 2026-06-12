---
title: "Boot Issues After Install"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Deland01 on 2010-06-23
I just installed Ubuntu Server v8.04.3 x-86 onto an old server. I ran through the Install wizard fine, the installer then said it would restart the system and the message I now see on screen is

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER


If I press enterom CD:
GRUB


The server did have Win XP on there before I loaded Ubuntu. Ubuntu detected this and installed GRUB but I still wanst able to get teh server working using GRUB witha dual boot. I ended up deleteing the RAID array & setting it back up (RAID 1).

The install was fine but I now see the DISK BOOT FAILURE message.

Any suggestions?

The server is SUPERMICRO, SUPERSERVER 5013C

Its a few years old but the disks should still be ok.

---

### Post by khelben1979 on 2010-06-23
I would recommend you to use 2 harddisks if you intend to use a dual boot solution, because, it's much easier in my opinion to get this to work. Windows XP on one harddrive and Ubuntu on the other one.

That should give you no more hassle with using GRUB, hopefully!

---

### Post by Deland01 on 2010-06-23
I don't want XP, just want to boot the server as Ubuntu. I deleted the Disk array which is like formatting the drives. I then installed Ubuntu again & this time the setup wizard didn't find any other operating systems (Win XP). I specified to use the entire disk to install Ubunto onto.

---

### Post by darkod on 2010-06-23
I'm not sure what options you had, but if asked where to install grub did you select like /dev/sda or /dev/mapper/....

For raid I think you need to use /dev/mapper/... because the array is already active, especially on a server which should have proper hardware raid (not fakeraid).

---

### Post by Deland01 on 2010-06-23
[COLOR=black][FONT=Verdana]Ermmmm.... Ive installed Ubuntu like 5 times now. Im really not sure what I picked on the GRUB install options. It asked to install GRUB on the first install. I might try installing Win Server 2003 to over write the boot loader & then format the drive & then re-try an ubuntu install.[/FONT][/COLOR]

---

### Post by darkod on 2010-06-23
Also, when running only ubuntu most people prefer to set up software raid. If you can, it would mean disabling the hardware raid, leave the disks as two separate disks, and during the install you set up software raid.
Look here, there are a number of guides for server install on hardware or software raid. Maybe it will help:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

