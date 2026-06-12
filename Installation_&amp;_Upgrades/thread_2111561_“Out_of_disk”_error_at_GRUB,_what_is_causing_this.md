---
title: "“Out of disk” error at GRUB, what is causing this?"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by seoernghiepdu on 2013-02-02
I tried to installing Ubuntu with both USB boot & CD but i can't install it, don't have any error when set-up but when my laptop complete & reboot, it always notice a error below:

> error: out of disk   
grub rescue >

or with Kubuntu 11.10, error:

> error: not find the file 
grub rescue >
And I can't access Ubuntu environment. My laptop chip is **Intel Pentium (R) M** so I only tried with 11.04 & 11.10 versions. I tried Lubuntu, Xutunbu, Ubuntu, Kubuntu with both USB & CD but it occurred same error. But if i run with trial mode, it run normally. Have any one experienced this problem, please help me. Thank you!

---

### Post by darkod on 2013-02-02
Some computers can't find the boot files if they are beyond 137GB on the disk. This is a BIOS limitation, not ubuntu. If this is the case with your machine, it could be the reason.

Are you trying to install dual boot, do you have windows, or you want only ubuntu on the machine?

---

### Post by presence1960 on 2013-02-02
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

### Post by seoernghiepdu on 2013-02-02
> Some computers can't find the boot files if they are beyond 137GB on the disk. This is a BIOS limitation, not ubuntu. If this is the case with your machine, it could be the reason.

Are you trying to install dual boot, do you have windows, or you want only ubuntu on the machine?
I tried both dual boot & full install on hard disk but same result :(

---

### Post by darkod on 2013-02-02
I asked what you want. The point was, if you want only ubuntu on the machine, to suggest doing a new install but using manual partitioning (Something Else option), create a small 500MB /boot partition on the front of the disk. That way you are sure the boot files stay at front.

You can partition the rest of the disk as you wish, with or without separate /home partition.

But if you want a dual boot with another OS, especially windows, you have to plan the partitions on the disk first, before even starting to install. If you plan a second linux installation, it's probably better to create another small 500MB /boot partition for it too. Different distributions can't share /boot, so each has to have one, and close to the front of the disk (in the first 137GB).

---

### Post by seoernghiepdu on 2013-02-02
> **darkod said:**
> I asked what you want. The point was, if you want only ubuntu on the machine, to suggest doing a new install but using manual partitioning (Something Else option), create a small 500MB /boot partition on the front of the disk. That way you are sure the boot files stay at front.

You can partition the rest of the disk as you wish, with or without separate /home partition.

But if you want a dual boot with another OS, especially windows, you have to plan the partitions on the disk first, before even starting to install. If you plan a second linux installation, it's probably better to create another small 500MB /boot partition for it too. Different distributions can't share /boot, so each has to have one, and close to the front of the disk (in the first 137GB).

**presence1960** said about **Grub2**, i'm researching about it, but i don't know purpose of creat partition size 500MB & the boot file stay at front ?

---

### Post by presence1960 on 2013-02-02
> **seoernghiepdu said:**
> **presence1960** said about **Grub2**, i'm researching about it, but i don't know purpose of creat partition size 500MB & the boot file stay at front ?

If you follow the instructions in the link I provided it may get you to boot into ubuntu, at which point you can then follow the next instruction to edit the file which is most likely causing the out of disk error. No need to reinstall unless that does not work. Sometimes, not all times, the out of disk error occurs in newer BIOS capable of reading past the 137 GB boundary. It is caused by a line in the file noted in the link.

---

### Post by seoernghiepdu on 2013-02-02
@**presence1960** - @**darkod**: i'm a amatuer of Linux & GRUB is a new knowlege with me, so i don't understand overall tutorials and have to start with small steps, i hope can installing Ubuntu early :D.
Thanks for ur help!
P/S: I looked for a tut on internet: [http://opensource-sidh.blogspot.com/2011/05/install-grub-in-ubuntu-from-server-cd.html](http://opensource-sidh.blogspot.com/2011/05/install-grub-in-ubuntu-from-server-cd.html). Could u follow this tut to install GRUB?

---

