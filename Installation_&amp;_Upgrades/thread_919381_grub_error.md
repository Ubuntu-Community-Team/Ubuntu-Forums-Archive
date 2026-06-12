---
title: "grub error"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by bigredcherokee on 2008-09-13
Trying to install Ubuntu and run into a slight problem. 

Hardware specs

EPOX 8k9A7I board

300 gig Seagate SATA Hard drive

SATA CD-Rom

IDE-CD Rom

I can go through the install but on reboot I get the following error

Grub Loading Stage 1.5.
Grub hard disk error

I get this with other distros as well. Please help I really don't want to ever go back to windows.......



Thanks.

---

### Post by Herman on 2008-09-14
GRUB hard disk error

Quoted from the [GNU/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html")
> The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed. 
Check that your hard disk is plugged in and if it's an IDE hard disk, make sure it and all other IDE drives are jumpered correctly (master, slave or cable select).

Check that your hard disk has been properly detected and set up in your BIOS.

---

