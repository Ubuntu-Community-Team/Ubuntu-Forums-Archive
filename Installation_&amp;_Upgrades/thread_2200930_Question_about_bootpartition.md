---
title: "Question about boot/partition"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by Pascal_Paquin on 2014-01-21
Hi, I have a question about partition and boot partition.
I have install Ubuntu on a secondary partition on my hard drive, I already had windows XP on another partition
Since I just wanted to try it I have keep my winXP
Now that I like Ubuntu I wanted to remove winXP and use that partition to give more place to the Ubuntu partition.
I have found a tutorial online showing to use the installation CD, go in gparted, remove the partition of windows, format it and then copy my old Ubuntu (sda8) partition to the new one (sda1).
Everything was working fine, but I was always botting in the old partition, I have try to use the command : sudo parted /dev/sda toggle 1 boot print to make that one the booting one.
But still the same thing.. is it because I still have my old partition ? Should I just remove that partition or is there something else to do to be sure that I'm booting on the first partition and not screwing up everything ?

---

### Post by ubfan1 on 2014-01-21
Don't delete anything yet.  Run sudo update-grub , and you should see your sda1 kernels to boot in the grub menu choices.  Boot one of them, and run sudo update-grub again, that should put the new system near the top of the grub menu.  When that boot works onto the new system, you can think about deleting the old system.  Probably it will be necessary to reinstall grub before deleting the old system so grub can find its files.  sudo grub-install /dev/sda

---

### Post by Pascal_Paquin on 2014-01-21
Finally it seems that there was already a boot option, it was just call Ubuntu 13.10 (13.10) instead of just Ubuntu
So if I'm able to boot on that one, that means that everything is ok So I should be able to remove the old one ?

---

