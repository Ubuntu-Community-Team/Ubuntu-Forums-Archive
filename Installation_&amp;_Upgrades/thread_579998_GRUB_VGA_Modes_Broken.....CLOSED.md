---
title: "GRUB VGA Modes Broken?.....??CLOSED??"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by porphiron on 2007-10-18
Hi, folks, I've been keeping an eye on this thread for a few days now, and tbh cannot believe its been closed. no post from any of the developers on this matter, just simply closed...I dont want to anyones back up, surely this should have been sorted before 7.10 went "public", I use tty consoles for the majority of the time I spend on this perticular computer and cannot believe that this has not been sorted....just............closed..........ok ok.....fair enough there are a lot of good things about gutsy, the way lvm has been handled is pretty good..............but dont take my console away from me.....:mad:

on the whole i like gutsy, but is it me or has the console problem been pushed aside to deal with happy smiley winblows styley guis??

---

### Post by porphiron on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Lo folks, would like to mark this as solved, but by the looks of it, its kind of hit and miss for some people, anyways....i finally got the "update-initramfs" fix to work for this problem (I tried it before to no avail)

This time i dont know if it makes a heap of difference, but i placed vesafb before fbcon in the /etc/modprobe.d/blacklist-framebuffer script and also used vga=799 instead of 0x31B, have pasted the launchpad bug url for those interested and the workaround I used was from nevermind.....

CHEERS NEVERMIND!!

workaround:
> sudo nano /etc/modprobe.d/blacklist-framebuffer
> change the line "blacklist vesafb" to "# blacklist vesafb"
> sudo vi /etc/initramfs-tools/modules and add fbcon and vesafb
> sudo modprobe nvidiafb
> sudo update-initramfs -u -k all

I note with interest that last time i did this the -k and all switches were missing, so wether they make a difference i dont know as tbh i know little of initramfs......I suppose I should read up

anyways....hope others find this usefull

cheers!

Porph!

---

