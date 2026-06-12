---
title: "Installation trouble"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by OBELIKS on 2005-10-13
Hi!
I'm having trouble doing a clean instal of Breezy. I have two hard drives, on HDD1 I have Windows XP, and I want to install Breezy on second HDD.
So my installation procedure is:
On the partitionig screen - Erase entire disk: IDE1 slave .....
And the I have problems with boot loader. If i choose GRUB I always get Error 17 (my second HDD is in LBA by the way) no matter where I install it /dev/hdb or /dev/hdb1 (I dont want to write anything on hda) and if I choose LILO i get the following screen:
[[img]http://www.shrani.si/pics/051013_1103520_thumb.jpg[/img]](http://www.shrani.si/pics/051013_1103520.jpg)
Oh, I make linux.bs with dd and write c:\linux.bs="Ubuntu" to the boot.ini, for the booting process.
AND I did not have problems with installing Hoary if I installed LILO on /dev/hdb1.
Thanks

---

### Post by az on 2005-10-13
You should probably write grub (or lilo) to hda.

---

### Post by OBELIKS on 2005-10-13
Hm, I dont want to do that and besides I dont think that will help.

---

### Post by xaverx on 2005-10-13
try choose install grub in MBR

---

### Post by OBELIKS on 2005-10-13
Been there done that, not working.

---

### Post by OBELIKS on 2005-10-13
Should I install Hoary first and then upgrade to Breezy? That should give me a complete working Breezy!?

---

### Post by officeboy on 2005-10-13
Basically the same problem I'm having,
Had windows XP x64 on 160gb (hd0,0 or /dev/hda)
Installed breezy on spare 80gb (hd1,0 or /dev/hdb1)
I get 
GRUB Loading Status1.5
Grub Loading, please wait...
Error 17

I've tried editing the menu.lst, changing root to rootnoverify and changing chainloader +1 to chainloader (hd0,0)+1


I've got a Athlon 64 3000+ on a Gigabyte GA-K8NF-9
WinXPx64 is 160gb on hda
spare is 80gb on hdb install setup hda1 as / and hda5 as swap
storage is 120gb on sda

---

### Post by officeboy on 2005-10-13
What seems weird is that the error 17 would seem to indicate that grub can't find the /boot/grub/ portion of our slave/hdb drives. 
However, that is where ubuntu is installed and should be the most readable&#8230;

---

### Post by OBELIKS on 2005-10-13
Well I'm writing this in Hoary, and I'm upgrading to Breezy. So it must be something in installation script, that is not working.
Wish me luck. :D

---

### Post by officeboy on 2005-10-13
good luck, I found my problem. 
Hdb was set to auto, not LBA, changed that and away we went.

---

### Post by OBELIKS on 2005-10-15
Hey, me again. So I installed Hoary first and did an upgrade to Breezy, and the problem remains. I get the same screen as I posted before.
So is this even an installation problem or it is a kernel problem? And I just remembered this problem first appeared with the Breezy release candidate. A nightly that I installed week before worked ok.
Help please.

An nevermind the GRUB trouble, that is another unrelated problem, as it seems that I cant make GRUB work.

---

