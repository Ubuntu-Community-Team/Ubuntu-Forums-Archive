---
title: "Grub and booting with an external hard drive"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by dinmikkith on 2008-01-09
Hi Folks!

I've had installed ubuntu succsessful on my external hard drive. A Western Digital My bool Essentials edition with 500 GB

But The live CD has installed the grub tu the MBR of my def hda 0,0 and not as desired to the MBR of my external hard drive. So I followed the tutorial that dave has posted in this forums for ubuntu 5.10 an used the alternate CD fir installation.

But in step 4 as I should mount something on the second console, something like proc /target/proc or so, there was a bug. 

I've tried to edit the file /etc/initramfs/modules or so to pre load the usb support. but I coudn't find the file on Ubunt 7.10.

So here is my question. 

Is it possible to mount ubuntu from an external hard drive without installing the grub bootloader in MBR of hda. for convinience here is [daves post]("http://ubuntuforums.org/showthread.php?t=80811"). 

greats 

dinmikkith

---

### Post by dinmikkith on 2008-01-17
Well, one week ago I've posted this message and now we have 50 views until this posts but 0 replais. Is there really no solution to this problem. 

I've tried a lot within the last week but I've found no solution. The only way someone else posted in an other forum is to disconnect the internal harddrive from bus system. But this is to tricky for myself. Dose anybody know a solution for this problem?:frown:

---

### Post by logos34 on 2008-01-17
If your Bios supports USB boot, all you need to do is follow post #502 of the the 'breezy' thread...[Reinstall Grub to the mbr of the external drive using the live cd]("http://ubuntuforums.org/showthread.php?t=224351"), then change root in menu.lst to (hd**0**,0) or whatever the ubuntu partition is.

Restore the windows bootloader on the internal drive using the xp install cd or super grub disk.

---

