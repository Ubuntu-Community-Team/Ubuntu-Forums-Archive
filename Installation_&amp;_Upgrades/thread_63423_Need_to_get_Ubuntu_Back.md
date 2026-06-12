---
title: "Need to get Ubuntu Back"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by pailhead on 2005-09-07
I recently reinstalled XP and need to get Ubuntu back so I can dual boot.  I tried to fix it with the live CD but it didn't work.  What is to be done to get Ubuntu back and grub back into the MBR?

I've got XP installed on one partition and Ubuntu installed on another.  Just in case that helps.

Thanks..

---

### Post by adwait on 2005-09-07
When you reinstalled XP, it overwrote the MBR and hence GRUB is gone. With the live CD, install GRUB, or with the installation package even.....

---

### Post by az on 2005-09-08
With the live cd, open a terminal and run

sudo mkdir hda
sudo mount /dev/hda5 /hda
sudo chroot /hda
grub-install


You can do this from the installer cd, as well.  This is assuming that your Ubuntu install is on /dev/hda5, USE THE CORRECT DEVICE INSTEAD!

---

