---
title: "Dual boot - GRUB Error 21"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by InfoTech on 2008-01-30
My old configuration was 2 SATA HDDs:
1 - Windows XP system drive
2 - mounted (or however is this called in the Windows) in My Documents.

I just bought new HDD and installed Ubuntu 7.10. After reboot, I got the following error message:

GRUB loading, please wait...
Error 21

What I can do in order to get my XP and Ubuntu OSs loading????

Thank for your help.

PS: Strange thing is that I do not find the 2nd HDD in BIOS, although it works perfectly under XP and Ubuntu detected 3 HDDs in installation process, as following:
sda XP disk
sbd 2nd disk used under XP
sdc disk I installed Ubuntu on

2ND PS
I managed to detect the 2nd HDD in BIOS, and now i get the
Error 17 message with GRUB
:????

---

### Post by InfoTech on 2008-01-30
Solution found!

In advanced options, I changed the "Hard Disk Boot Priority" as suggested by [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

Please note:
The "Priority Order" that did not worked was:
1. XP sys disk
2. Ubuntu sys disk
3. additional disk for XP

The "Priority Order" that works is:
1. XP sys disk
2. additional disk for XP
3. Ubuntu sys disk

---

