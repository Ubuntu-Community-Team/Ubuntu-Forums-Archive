---
title: "Dual boot, ubuntu installed first"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by pubairplanes on 2008-08-14
Hey all,

I have been using Ubuntu for about two years now. For the past few months I have had a single boot system, running Ubuntu 8.04.

Yesterday I purchased an iPod touch and, in an attempt to get it working, I installed windows xp onto a blank partition. My drive now has 5 partitions, Ubuntu, Swap, NTFS storage 1, NTFS storage 2, and Windows XP. When I boot the system it skips my old grub boot loader and boots right into Windows XP.

Obviously, what I want is for the system to ask me which OS to load. From what I understand, installing XP first usually does this automatically, but I didn't do that... so yea. I remember reading something about a file that controls the windows boot loader, and that you can add other OS's to that. Can anyone tell me the file, or how to get a boot menu with both systems?

Thanks!

PS. All of my files are safe in an NTFS partition, just a side note.

---

### Post by meindian523 on 2008-08-14
Nopes,it's the other way round,installing XP after installing Ubuntu makes sure you boot XP and won't ask you which system to load.Follow:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by willix on 2008-08-21
One way of doing it is reinstalling the first boot stage of grub 
read here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
then you need to add something like

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

to your /boot/grub/menu.lst file where (hd0,0) should point to your windows partition (replace the first 0 with your drive number and the second with the partition number, both a zero based).

and reboot

---

