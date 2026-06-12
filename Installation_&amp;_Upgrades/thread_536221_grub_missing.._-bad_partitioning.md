---
title: "grub missing.. -bad partitioning?"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by fargoth on 2007-08-27
hi, 
I want to dual boot MS-Dos, WinXP, winXP recovery console, and Xubuntu... 
now i got one hard disk  (hdb)  (my older one) with the following partitions:
hdb0 : primary and active fat32 for Ms-Dos (actually win98)
hdb1: extended NTFS with winXP and the recovery console...

currently the boot is winXP's and it shows winXP, MS-Dos, and recovery console.

the second hard disk (hda) (the newer one) has the following partitions:
hda0: extended ext3 for /
hda1: extended swap
hda2: extended NTFS for storing my data...

I have installed Xubuntu 7.04 to the newer hd (hda)
but Grub won't load... 

the weird thing is that i can access the data partition from winXP, or the / partition from the liveCD, but partition magic wont show these partitions - it just paints it all yellow and says BAD...


I want to preserve my windows boot screen and have Grub ask me whether i want to see my windows boot screen or load Xubuntu.

what should i do?

---

### Post by Pumalite on 2007-08-27
With Live CD, from Terminal: post the following (from your filesystem)
sudo fdisk -l(small L)
cat /boot/grub/menu.lst
cat /etc/fstab
bilkd

---

### Post by fargoth on 2007-08-27
well, i found the problem - grub was writen to the MBR of the hard disk which i didn't chose to boot... now it's all fine... just for out of curiosity - i read there is a way to use the ntldr (the winXP boot) to load linux - skeeping the need to install grub to the MBR...

the guides i read about this option all use dd if=/dev/hd(some number) (the /boot partition) of=/dev/fd0 (if i want to put it on a floppy)...

but what do i do if i don't have a /boot partition???

---

### Post by Pumalite on 2007-08-27
You don't need a /boot partition. Let Grub be in the MBR and you will have a menu to boot either OS.

---

### Post by fargoth on 2007-08-27
yes, i know i don't have to... i just want to know how to create the file i need to place in the windows partition so i can configure boot.ini to load linux - so i'll know how to use the winXP boot loader instead of grub...

see here:
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

this guide talks about /boot - my question is - how do i do it when i don't have a /boot partition?

---

### Post by Pumalite on 2007-08-27
I read your link. Myself, I think is a waste of time if you already have a working system with dual boot. You don't have to worry about anything. But; if you insist, I'll have to tell you that I've never done myself. It can be done certainly. My feeling is that you would have to start all over again and create your /boot partition, but I might be wrong. There are other people in this forum that can help you better. Good luck. Hopefully someone will chime in.

---

### Post by fargoth on 2007-08-28
learning is never a waste of time... a working system is nice, but it's not the only purpose i got for my computer.

thanks anyway =)

---

