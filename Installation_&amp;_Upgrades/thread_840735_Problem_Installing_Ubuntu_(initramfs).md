---
title: "Problem Installing Ubuntu: (initramfs)"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by dougw4 on 2008-06-25
Hi: 

I'm yet another newbie to Ubuntu. I've installed on an empty hard drive several times, but always get the same result when I try to boot from the installed copy of Ubuntu. I get a black screen with the following:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-In shell (ash)
Enter 'help' for a list of built-in commands. 

(initramfs)


Does anyone know what to make of this?

Thanks,

Doug Witmer

---

### Post by avtolle on 2008-06-25
There is a veritable plethora of threads on this topic. But, before you go searching, I've a few questions:

1) Did you verify the md5sum of the iso before burning to cd? (This presumes you did not receive a CD from Ship-it);

2. Did you burn it slowly (4x or so) to a CD-R?

3) Did you verify the integrity of the CD before trying to install (option 4 from the menu when first booting, as I recall);

4) Are you trying to install from a Live (Desktop) CD, using the graphic installer? 

5) Do you have any SATA drives?

Just a few items to consider. BTW, if the iso is good, the CD is good, then it sounds like you will need to begin trying various boot parameters. A search of other threads with this topic will provide you with a list. 

Good luck.

---

### Post by dougw4 on 2008-06-25
Yes, I verified the integrity of the disk just before installing.

And, yes, I've installed both ways -- from the live CD and from the menu.

No, I don't have any SATA drives. I'm trying to put Ubuntu on an older (December 2002) computer.

I will start reading threads on boot parameters. Thanks for the suggestion. I really didn't know where to start!

---

### Post by avtolle on 2008-06-25
Look for threads concerning Busy Box or Intrafms in the title; there seems to be a lot of folks experiencing your problem. Good luck.

---

### Post by dougw4 on 2008-06-25
Okay, My problem is now fixed. I read some of the other threads where people were seeing the (initramfs) prompt. I tried playing around with BIOS parameters, but that didn't fix anything. Then something inspired me to put the ide hard drive on a different cable from the ide CD ROM drive. That did the trick! Thanks to everyone who offered tips.

Doug Witmer

---

