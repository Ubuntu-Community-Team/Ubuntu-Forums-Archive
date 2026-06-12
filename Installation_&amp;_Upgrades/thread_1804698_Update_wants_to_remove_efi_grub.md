---
title: "Update wants to remove efi grub"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by nhaskins on 2011-07-15
I'm running Kubuntu natty on grub-efi-amd64. I've just received notification of a bunch of new packages to install, I believe part of it is a kernel update. When I click on "apply" a window comes up which says "Additional changes are required to complete the task". "2 packages to remove" lists "grub-efi" and "grub-efi-amd64". It lists 5 packages to install 3 of which are linux kernel and 2 of which are the bios version of grub.

How can I update my system without having efi-grub removed?

Thanks in advance.

Neil

---

### Post by amiliv on 2011-08-21
Yup, I'd like to figure out same thing.  Replacing grub-efi with the other version of Grub makes my system unbootable.  Attempting to run grub-install with BIOS version of Grub fails miserably.  Reinstalling grub-efi and running grub-install works perfectly.

What I usually do is simply re-install grub-efi, and things work again.  But, yeah, it's major pain that Ubuntu updater is keen on removing grub-efi from my system (an newish Gateway PC, nothing too special about it)...

---

### Post by Cyjan on 2012-09-22
my grub  (EFI GRUB on Mac) 
vanished after first update for 12.04
i managed to fix it by downloading program called boot-repair tool booted with Ubuntu LiveCD 
thanks!

---

