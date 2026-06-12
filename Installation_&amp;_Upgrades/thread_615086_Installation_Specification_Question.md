---
title: "Installation Specification Question"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Haluci on 2007-11-16
Hi, I'm trying to set up a dual boot configuration on my computer with Vista and Ubuntu.  I want to install Ubuntu such that the bootloader is installed to the **bootsector** of the partition that I'm installing Ubuntu on, rather than the **MBR** of my hard drive.  How to I specify this using Ubuntu's install program?

Thanks for your help!

EDIT: A bit more information... my main goal is to have a dual boot configuration of Vista and Ubuntu with Vista's bootloader in charge, using EasyBCD (I think this is called chainloading).  In order to do this, the documentation states that I need to have GRUB installed "on the bootsector of the partition that Linux is being installed to and not the MBR of the hard drive."  Everything works fine on the Ubuntu install, but under the advanced options (at the final step) it wants to install GRUB on hd0.  Do I just have it install GRUB on the partition, like hd0,4?  Would that still leave the Vista bootloader in charge?

---

### Post by Pumalite on 2007-11-16
You can install Grub to the partition in question setting it up in step 8 of the installation (Advanced Tab; from (hd0) to whatever appropriate)
If you want to make a special /boot partition; that's another matter.

---

### Post by Haluci on 2007-11-16
whoops, I edited my post while you were posting, my mistake :P

So if I wanted to install GRUB on partition 3 of hard disk 1(the partition I'm installing ext3 on), would the command be hd0,3?

---

### Post by torgrot on 2007-11-16
No it would be (hd0,2)  They number from zero

torgrot

---

