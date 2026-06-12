---
title: "Dual boot install win7 64 Ubu 64 issue efi"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by luishasbon on 2012-01-15
Well im going to be short. I bought an acer aspire 5560 i had windows 7 home premium 64 preinstalled, It had a lot of anoying software so I got the installation dvd for windows, I used Gparted for deletin the backup factory default partition pqservice, and then I tried to install fresh new windows, inding I couldnt why? because it was a Efi disk, after this, I used Gparted to delete everything made a new partition table, installed ubuntu full, not dualboot, an after that i was able to install windows again, of course I left a extended partition for installing ubuntu after it, now I tried to install ubuntu 11.10 from USB, it didnt show one problem udring installation, after installation reboot, not even GRUB showed it boots directly to windows. So I dont know what to do. Ive tried EasyBCD but it does not work. Please Dear Comunity Help me. Thanks!!!

---

### Post by darkod on 2012-01-15
From ubuntu live mode please post the output of:
sudo fdisk -l (small L)

---

