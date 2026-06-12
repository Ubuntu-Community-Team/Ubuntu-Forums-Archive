---
title: "Installing Ubuntu over Redhat 9"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by Tarrkus on 2006-09-27
Hi -

I have a machine that currently dual-boots Redhat 9 and XP.  I'm going to install Ubuntu on the RH9 partitions.  I don't want to save any of the data on the RH9 partitions.  My concern is that I don't screw up the boot loader.  Currently the machine has GRUB 0.93 on it.  Are there any problems I should watch out for?  Anything out of the ordinary that I should do during the install?  Thanks.

-T

---

### Post by _teo_ on 2006-09-27
In my opinion nothing in particular, but I'm not that experienced.

During installation process GRUB will replace the existing boot loader in MBR - no mater which one is already installed. So, this should work.

---

