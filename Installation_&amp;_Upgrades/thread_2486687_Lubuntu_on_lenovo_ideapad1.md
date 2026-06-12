---
title: "Lubuntu on lenovo ideapad1"
date: 2023-05-08
forum: Installation &amp; Upgrades
---

### Post by mats67 on 2023-05-08
HI
after installing lubuntu i restart and remove installation usbdisk and hit enter 
boot meny comes up with 
1.ubuntu
2,windows boot manager
3.eMMC Card Ramaxel 64 GB
i choose 1 and hit enter nothing happends and the same with 2 and 3 
what may i have done wrong ??

---

### Post by tea for one on 2023-05-08
Assuming that you did not see error messages during installation.
Also, that you installed in UEFI mode.

Power off PC
Power on and quickly press F2 to access UEFI settings.
Security > Secure Boot > Disabled
Security > Intel Platform Trust Technology > Disabled
Boot > Boot Mode > UEFI
Boot Priority Order > 1 Ubuntu

Save settings and let's see what happens.

---

