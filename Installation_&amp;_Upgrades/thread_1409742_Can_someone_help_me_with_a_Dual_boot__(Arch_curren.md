---
title: "Can someone help me with a Dual boot  (Arch currently installed)"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by Joe Ker1086 on 2010-02-17
I am getting ready to install ubuntu 9.10 along side arch linux but i have had a really hard time dualboooting in the past...here is my partition scheme

/dev/sda1 - /boot
/dev/sda2 - extended partition (houses /dev/sda5 and /dev/sda6)
/dev/sda3 - /root - current arch install
/dev/sda4 - /home - want to share with ubuntu and arch
/dev/sda5 - swap
/dev/sda6 - where i want to install ubuntu

any help would be appriciated...i dont mind not mounting a separate /boot partition for my ubuntu install if it will be easier....

---

### Post by magnusk on 2010-02-18
Install Ubuntu's bootloader on sda6 (not sda) and add use chainloading [http://wiki.archlinux.org/index.php/GRUB]("http://wiki.archlinux.org/index.php/GRUB").

---

### Post by Joe Ker1086 on 2010-02-18
ok, so i screwed up, it didnt give me the option of where to install grub......like i thought it would, so now i am at a loss....how would i uninstall grub 2 from sda and reinstall it to sda6?

---

