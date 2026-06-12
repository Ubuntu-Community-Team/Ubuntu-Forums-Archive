---
title: "updated ubuntu 7.04 and lost windows xp in grub -"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by mrbordig on 2007-07-22
I am a n00b to Linux and recently installed ubuntu 7.04 on a singel HD with Windows xp to dual boot.  Went smooth until I installed the updates that Ubuntu said were available.  Once I did this Grub no longer shows Windows in the menu.  It now shows 2 Ubuntu's in the menu (kernel 2.6.20-16-generic and kernel 2.6.20.15-generic) instead of Ubuntu and Windows XP.  I figure there is probably a simple solution (or at least I hope) to this.  So I need to setup Grub to see my windows partition also.  (Both Ubuntu and Windows are on the same HD).  Thanks in advance for the help.
:)

---

### Post by Pumalite on 2007-07-22
You can edit /boot/grub/menu.lst chailoading XP at the end. Can't remember the exact syntaxis
 right now, but you could try Super Grub in the meantime:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

