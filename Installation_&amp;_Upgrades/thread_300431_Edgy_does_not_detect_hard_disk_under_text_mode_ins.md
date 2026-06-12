---
title: "Edgy does not detect hard disk under text mode installatio"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by acid_burn on 2006-11-15
Hi all!
I have an Olidata workstation, with [this]("http://www.motherboards.org/mobot/motherboards_d/ASUS/P5GD1/") motherboard and a Edgy DVD. If I start the installation in text mode, the installer does not detect the hard disk, then i'm not able to partition the disk. The installer show me a list of modules to specify which type of hard disk I have, but i've tryed them all without success. If i boot live ubuntu, ad then install Edgy whit ubiquity, the installer detect successfully the hard disk, but i'm not able to configure LVM. Now i have two questions (and i hope at least one solution) ;) :
1) how to force the text installer to detect succesfully the hard disk?
2) how to configure LVM from ubiquity?

thanks in advance to all
byez

---

### Post by acid_burn on 2006-11-17
solved copying the it821x module (extracted from the package linux-image-2.6.17-10-386) to a floppy, then loading it from the text installer, selecting "load the driver from a floppy". but... why the module isn't already included by default in the installer kernel?

linux rulez
byez

---

