---
title: "GRUB not on MBR but on other primary partition"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by Jordan-D on 2007-05-14
I have 3 primary partitions. 1st one for windows, second for mac and third for Ubuntu. GRUB is installed on the MBR. Before i had openSuSE and it installed its bootloader onto its third partition so when i reinstall windows the linux loader was not lost.

So what I want to do is move or reinstall GRUB on the bootsector of the third primary partition and restore the windows MBR
Thank you

---

### Post by naren.bharatwaj on 2007-05-14
if u want to have the dos boot loader, insert the windows xp installation cd and boot from it. enter the recovery mode when it asks for a fresh install or repair. u then get to the command prompt. there u type the command "fixmbr". this will change the mbr of the current hard disk from any boot loader to dos. hope this sorts ur problem.

all the best

Naren

---

### Post by Jordan-D on 2007-05-14
Yes. This will restore the original windows MBR but hen i can not boot ubuntu. That's why i want to know how to install GRUB onto the linux partition which is primary.

but thanks for the reply anyway :)

---

