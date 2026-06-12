---
title: "Can't see Windows 8 UEFI on grub"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by enes5 on 2015-06-04
FIRST i know many people create kind of topics but my english doesnt enough to understand all. Just i need directions. I am new ubuntu user. I have windows 8 uefi so i am trying to install since 2 days.I deleted and installed again and again i tried everything still cant see windows 8 , i try easybcd but ubuntu doesnt work there and.. when i use easycbd ubuntu never work. So what should i do ?

Shorty i want to add windows 8 on grub.

---

### Post by oldfred on 2015-06-05
With UEFI, you do not need EasyBCD. That just adds another boot menu. You have UEFI's boot menu and grub's boot menu already.

Did you install Ubuntu in UEFI boot mode?
You can only dual boot from grub menu if Ubuntu is also installed in UEFI boot mode not BIOS/CSM boot mode. But you should be able to dual boot from UEFI boot menu, but may have to turn on/off UEFI or CSM/BIOS/Legacy mode to match install.

Also what brand/model computer?
Some require work arounds to boot ubuntu entry in UEFI mode. Some will not boot ubuntu entry and only a hard drive entry which we make really be grub or shim.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

