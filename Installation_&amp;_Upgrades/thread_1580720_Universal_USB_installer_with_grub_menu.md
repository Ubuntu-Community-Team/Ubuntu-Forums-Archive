---
title: "Universal USB installer with grub menu?"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by Z.K. on 2010-09-23
I know this is not strictly a Ubuntu question, but I was unsure where to ask this question and since it is about installing Ubuntu Server, I put this question here.

I have used the Universal USB installer to create an install USB device, but I also need to be able to boot to a DOS prompt so I can update the bios if I need to.  I would like to have just a single USB drive rather than having to carry two of them around.  

Has anybody used the Universal USB installer and is there a way to modify the resulting USB installer so that I could say add a menu program such as grub or something else that would allow me to either access the installer or go to a DOS prompt?  Kind of like the way CloneZilla does or perhaps the gparted Live CD.

---

### Post by C.S.Cameron on 2010-09-23
MultiBootUSB uses grub2 to boot Linux iso's.
It starts with a grub menu when booting.

---

