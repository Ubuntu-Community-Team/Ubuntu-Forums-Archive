---
title: "Bootloader Error"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by barqers on 2007-09-26
My setup is as so:
One 320gb Hdd
One 80gb Hdd
On the 320gb I have 100gb dedicated to my vista partition. The rest goes to Mandriva.
On the 80gb I have Ubuntu 7.04.

Now during installation I tried installing the bootloader everywhere (there was no mbr option) so I tried to install it on my 80gb Hdd...mistake... Mandriva will boot up yes, but now it won't let me access my Ubuntu OS. Is there a way I could regain that option?

Thanks guys

---

### Post by roschell on 2007-09-26
I have got one here too, 

just accepted offered download of new kernel image, installed, reboot, and could not get to system anymore. it starts for few seconds then the screen turns black. i am writing this way as i have not figured out yet how post new post here, sorry.

grub seems to be correct, and fstab also, any suggestions 

thanks

---

### Post by barqers on 2007-09-26
[http://forum.mandriva.com/viewtopic.php?p=372382#372382](http://forum.mandriva.com/viewtopic.php?p=372382#372382)

View that thread I fixed my error there.

Goodluck

---

### Post by roschell on 2007-09-27
it seems that the fault is not in grub or fstab. tried to get in through the Live cd again and search for something on the net. after while found possible help by 
command reiserfsck -check /dev/sda6
this should check the partition for problems, which turned bad block meaning error on hard drive not software. it appeared to be weird as when running system rescue disk it did fix the error, however after restart the same situation. 

the partition is /usr as I separated this from /home and / .
i also discovered that in /usr/bin i had indefinite number of x11 folders in a tree-like form.

situation resolved by new installation of ubuntu, now just add back the necessary apps

oufff, everything is there even the bookmarks

---

