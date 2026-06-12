---
title: "Kernel panic when trying to boot from CD (8.04)"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by christian93 on 2008-07-31
Hi guys,

My Problem is:
Everytime I try to boot from the installation CD, I get an error:
"Kernel panic - not syncing: Attempted to kill the idle task!"
It appears some seconds after I select the Language.

I tried both, the 64 bit and the 32 bit version of Ubuntu 8.04. Same error.

Windows Vista, openSUSE and Fedora are working.

My System:
CPU: Intel Core2Quad Q9450
Graphics Chip: NVIDIA GeForce 9600 GT
Harddisk: 2x500GB RAID 0

32 bit:
[http://img501.imageshack.us/img501/461/dsc00002tt0.jpg](http://img501.imageshack.us/img501/461/dsc00002tt0.jpg)

64 bit:
[http://img297.imageshack.us/img297/5774/dsc00001ql7.jpg](http://img297.imageshack.us/img297/5774/dsc00001ql7.jpg)

---

### Post by overdrank on 2008-07-31
> **christian93 said:**
> Hi guys,

My Problem is:
Everytime I try to boot from the installation CD, I get an error:
"Kernel panic - not syncing: Attempted to kill the idle task!"
It appears some seconds after I select the Language.

I tried both, the 64 bit and the 32 bit version of Ubuntu 8.04. Same error.

Windows Vista, openSUSE and Fedora are working.

My System:
CPU: Intel Core2Quad Q9450
Graphics Chip: NVIDIA GeForce 9600 GT
Harddisk: 2x500GB RAID 0

32 bit:
[http://img501.imageshack.us/img501/461/dsc00002tt0.jpg](http://img501.imageshack.us/img501/461/dsc00002tt0.jpg)

64 bit:
[http://img297.imageshack.us/img297/5774/dsc00001ql7.jpg](http://img297.imageshack.us/img297/5774/dsc00001ql7.jpg)

Hi and welcome, have you checked the cd for errors?
Have you tried to edit the kernel while booting the live cd and add noapic before the --.

---

### Post by christian93 on 2008-07-31
I have burned it onto a DVD because I have no spare CD's.
Does this make a difference?

edit:

I have found an empty CD now and I burned the 64 bit version onto it. Same error again. I can't even check the CD for errors because if i click on "check cd for errors", i get a kernel panic too.

noapic doesn't fix my problem.

---

