---
title: "Ubuntu installed inside Windows won't Startat"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by mytorciar on 2008-08-31
I had installed Ubuntu 8.04 inside windows xp sp2. It was working perfectly fine, I was able to update it and also install some more software.

Today, ubunu wont start. On the dual boot screen on pressing the ubuntu option, it shows a list of booting options of ubuntu. On selecting anyone ubuntu gives error message, does not load and it says " press any key to exit". It also shows the windows option and i can load winxp safely.

I have tried the xp disk check for errors option and then retried but no luck. Any help is welcome.
Thanks 
Mytor

---

### Post by manishtech on 2008-09-02
Can you tell us what error message you get?

---

### Post by mytorciar on 2008-09-03
Thank for your reply: 

My system:
C: windows 98
d: wxpsp2 (some programs are installed by default in this drive)
i: XP Programs (Rest of the programs are isntalled) and also Ubuntu (10gigs)
other drives are data and backup drives
Total disk =160gb, RAM=1gb
=====================
On boot up:

Booting ubuntu 8.04.1 kernel 2.6.24-19 generic
filesystem is type FAT, partition type 0xb

kernel /boot/vmlinuz-2.6.24-19 generic root UUID=1675D61C35EFDC3F loop =/ubuntu/disks/ root 

disk ro quiet splash

Error 15: File not found
Press any key to continue......
 

after pressing a key display on screen is:

GRUBDOS 0.4.3 2008-04.22, Memory 639k 1014M, code end: 0x41228

choices:
ubuntu 8.04.1,  kernel 2.6.24-19 generic
ubuntu 8.04.1, kernel 2.6.24-19 generic (recovery mode)
ubuntu 8.04.1, kernel 2.6.24-16 generic
ubuntu 8.04.1, kernel 2.6.24-16 generic (recovery mode)
ubuntu 8.04.1, memtest 86+

other operating systems
Windows/NT/2000/XP (loader)
Press enter or 'b' to boot, 'e' to edit commands, 'c' for command line

=======================================================
on pressing first choice display is 

Booting ubuntu 8.04.1 kernel 2.6.24-19 generic
filesystem is type FAT, partition type 0xb

kernel /boot/vmlinuz-2.6.24-19 generic root UUID=1675D61C35EFDC3F loop =/ubuntu/disks/ root 

disk ro quiet splash

Error 15: File not found
Press any key to continue......
================
On Second Choice display is:
Booting ubuntu 8.04.1 kernel 2.6.24-19 generic
filesystem is type FAT, partition type 0xb

kernel /boot/vmlinuz-2.6.24-19 generic root UUID=1675D61C35EFDC3F loop =/ubuntu/disks/ root 

disk ro single 

Error 15: File not found
Press any key to continue......
=====================
On third choice display is:
Booting ubuntu 8.04.1 kernel 2.6.24-19 generic
filesystem is type FAT, partition type 0xb

kernel /boot/vmlinuz-2.6.24-16 generic root UUID=1675D61C35EFDC3F loop =/ubuntu/disks/ root 

disk ro quiet splash

Error 15: File not found
Press any key to continue......
===============
On 4th choice display is:

Booting ubuntu 8.04.1 kernel 2.6.24-19 generic
filesystem is type FAT, partition type 0xb

kernel /boot/vmlinuz-2.6.24-16 generic root UUID=1675D61C35EFDC3F loop =/ubuntu/disks/ root 

disk ro single

Error 15: File not found
Press any key to continue......
==================
On 5th choice display is:
Booting ubuntu 8.04.1 kernel 2.6.24-19 generic
filesystem is type FAT, partition type 0xb

kernel /boot/memtest/86+.bin

Error 15: File not found
Press any key to continue......
===========================================

On last choice it boots into WinXP without any problem


Mytor Ciar

---

### Post by manishtech on 2008-09-03
> Booting ubuntu 8.04.1 kernel 2.6.24-19 generic
filesystem is type FAT, partition type 0xb

kernel /boot/vmlinuz-2.6.24-19 generic root UUID=1675D61C35EFDC3F loop =/ubuntu/disks/ root 

disk ro quiet splash

Error 15: File not found

How is ubuntu installed on FAT filesystem?

---

### Post by mytorciar on 2008-09-04
Ubuntu is installed on NTFS drive INSIDE windows xp which is one of the options for 8.04 from the live cd.

till now it was working allright. I have been updating it and also have added some softwares successfully. But all of a sudden this happened and Ubuntu stopped working.
Mytor

---

