---
title: "LILO bypasses windows installations"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by JoeO on 2005-08-15
I have a triple boot system installed.  One HD, Win98 1st on it's own partition, XP Pro next on it's own partition and Ubunto third on it's partition(s).  Everything has gone fine on all the install's.  After 98 and XP were installed, the MS dual boot sytem worked fine.  Then I installed Ubunto and it properly saw the partitions and left he windows partitions as they were and installed itself on it's partition.  On reboot, it displays one line saying Lilo 22.6.1   Loading Linux......

There is no option to choose linux or booting into the Windows OS, which is what I wanted.  Any help?

I have Linux in a dual boot configuration on three other systems in the house, but they are using Grub.  For whatever reason Grub did not want to install anywhere but the MBR, despite my attempts otherwise.  Knowing I'm a linux newbie of sorts, I can presume I made a mistake somewhere installing GRUB, but it did work fine on the other dual systems.  That's water under the bridge I guess.  I have LILO and need to know how to fix it.

Thanks.

---

### Post by kamstrup on 2005-08-16
I think you should play around with the command "grub-install" . . . It sounds like there's some old Lilo installation lingering around on your system.

You can use fdisk to deactivate the active/bootable flag on the active partition, and see if it picks up grub then, or simply set the active partition to your Ubuntu (root) partition.

DISCLAIMER: You'll need a (Linux) boot disk or Live CD to rescue your system if anything goes wrong... 

Good luck

---

