---
title: "How install Special Grub or Boot Menu"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by mrbs21 on 2011-03-17
Hi all.

Someone knows how I can do this:

We have computers with Windows XP (master hard disk), but We will to recive Hard Disks with Ubuntu's image and I need install the disks like slaves. Then, my team must select which operating system will boot. Windows or Linux.

How I can install a boot menu without damage my operating systems especially Linux image should not change it. Windows does not interest me much, but for now there is information there.

 Someone can recommend me some solution?

Thanks a Lot!

---

### Post by ronparent on 2011-03-17
The simplest solution is to enter the bios and change the boot order so that the new disk with Ubuntu boots first. Then, assuming the drive has the grub boot loader already installed, do a **sudo update-grub** to update the /boot/grub/grub.cfg to put the windows into the grub boot menu. That should do it and you should be able to boot into either system on the next boot.

If grub should require reinstallation, follow the two step method in this reference: **[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2**

Post if you still have problems.

---

### Post by Dutch70 on 2011-03-17
On my system, I just had to hit the escape key to "choose boot options" when the system was starting, then boot into the hdd that had Ubuntu on it & then run "sudo update-grub" but I am using SATA hdd's.

---

