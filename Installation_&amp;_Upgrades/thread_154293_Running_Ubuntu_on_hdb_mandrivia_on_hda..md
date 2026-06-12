---
title: "Running Ubuntu on hdb mandrivia on hda."
date: 2006-04-02
forum: Installation &amp; Upgrades
---

### Post by medphys on 2006-04-02
Hi all,

I am new to Ubuntu and I would like to ask a few questions about Ubuntu.  I would like to install Ubuntu on my 2nd drive hdb, and leave Mandrivia on my primary drive hda.  I am running Lilo bootloader (standard with Mandrivia) and modify it so that I can switch between them but for now the primary system will be Mandrivia.  I plan to use Ubuntu, but I want to play with the system for a while before switching.   When I load Ubuntu, will the boot loader from Ubuntu be loaded on my system.  

What problems have people experienced using Ubuntu on hdb and another linux system on hda?

Thanks for your help, I think I will enjoy Ubuntu.

---

### Post by Sutekh on 2006-04-02
You can tell the Ubuntu bootloader (GRUB) to install itself on the second disc /dev/hdb instead of /dev/hda, so it won't overwrite Mandriva's bootloader.  

You will need to modify the Lilo bootloader so that you can boot Ubuntu, but I don't have any experience with Lilo, only GRUB.

I haven't had any problems with multiple Linux OS on my hard drives, it just takes some work to keep the orginal bootloader intact and working with the new system.

---

