---
title: "How to show Grub on dual boot with win8 (64 bit)"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by raunhar on 2013-07-13
I installed ubuntu 12.10 64 bit on Dell Inspiron.
After the installation, the Grub menu does not showup, and it boots directly to Ubuntu.
When I go to Boot Options, under Boot Menu, it shows some options like Ubuntu , Windows etc.
How do i get the Grub to display after startup.

---

### Post by carl4926 on 2013-07-13
You should get a boot menu
You are sure you didn't wipe away Windows

Did you follow this
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by bry012 on 2013-07-13
Try boot repair. Sometimes grub can get broken during the install process.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Also, what boot system are you using? BIOS or UEFI? If UEFI you might need to revert back to legacy to get your dual boot to work.

---

