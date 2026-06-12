---
title: "Dual Boot XP + Ubuntu..... help!"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by UKCamaroSS on 2007-10-20
Hi,

Firstly, I'm a complete Linux newbie (been using it for 1 week).

Instead of installing Ubuntu 7.10 over my last Ubuntu install, I seem to have created another OS.... how can I delete the first copy?

To make it a little clearer:
 I installed Ubuntu 7.04 (64 bit version) last week, as a dual boot with XP. On Thursday last week, I used the update function in 7.04 to upgrade to 7.10
I then tried to get MythTV (Mythbuntu) working.... but thought I failed!

Due to issue's with the 7.10 (64 bit software), today I used the 32 bit version LiveCD to install 7.10 again - but I now have the following shown when I boot up:

7.10, kernel 2.6.22-14 generic
7.10, kernel 2.6.22-14 generic (recovery mode)
7.10, memtest86+

Other OS...:lolflag:
Windows XP Media Center
7.10, kernel 2.6.22-14-generic (on/dev/hdc2)
7.10, kernel 2.6.22-14-generic (recovery mode) (on/dev/hdc2)
7.10, kernel 2.6.20-16-generic (on/dev/hdc2)
7.10, kernel 2.6.20-16-generic (recovery mode) (on/dev/hdc2)
7.10, memtest86+ (on/dev/hdc2)

I have an AMD Athlon 64 3000+ cpu
Geforce Nvidia FX5700LE graphics card
512 MB memory
2 Hard drive's (1*80GB and 1*225GB)

I would like to get back to just one copy of Ubuntu 7.10 (32bit) with one XP.... how can I do that?

Thanks,

---

### Post by tribunal on 2007-10-20
you already have one copy of Ubuntu :)
But you have mixed versions - it is not good 
you can: 
1) clean menu - it is done using /boot/grub/menu.lst
2) clean the system

---

### Post by UKCamaroSS on 2007-10-20
> **tribunal said:**
> you already have one copy of Ubuntu :)
But you have mixed versions - it is not good 
you can: 
1) clean menu - it is done using /boot/grub/menu.lst
2) clean the system

When you say clean menu & Clean system.... what does each do... and how would I clean the system if I choose that option?

---

### Post by tribunal on 2007-10-20
You can just remove some strings from /boot/grub/menu.lst - this is first solution
Or you can reinstall all your system (but at first, clean system linux partition)

---

