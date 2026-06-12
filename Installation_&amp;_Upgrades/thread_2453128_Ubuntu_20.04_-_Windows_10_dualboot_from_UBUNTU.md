---
title: "Ubuntu 20.04 - Windows 10 dualboot from UBUNTU"
date: 2020-11-03
forum: Installation &amp; Upgrades
---

### Post by sliwkahax on 2020-11-03
Hi! I wanted to make a windows - ubuntu dual-boot.
All the tutorial i have found were about making the dual-boot from windows.
Should i install windows like normal or what?
Thanks.

---

### Post by Frogs Hair on 2020-11-03
Welcome [COLOR=#000000]sliwkahax: 

can you please provide some information about your system as well as what operating system if any is currently installed.  [/COLOR]

---

### Post by sliwkahax on 2020-11-03
I have ubuntu 20.04 right now, without any other systems. I have got a partition ready for windows.

---

### Post by Frogs Hair on 2020-11-03
It is recommended to install Ubuntu first to avoid windows overwriting Ubuntu. I have been dual booting with Win 7 and now 10 for years and have not tried installing windows after Ubuntu.  There are some tutorials for installing that way but not having used those methods I can't recommend them. Backup before you start! At the very least you will have to update grub from a live Ubuntu media to get Ubuntu to boot after installing Windows. If you only need windows occasionally and have enough memory a virtual installation might be a better option to avoid problems with both installations.

There are tutorials if you search. 
[https://blog.webnersolutions.com/installing-windows-after-ubuntu-os-in-a-dual-boot-system/](https://blog.webnersolutions.com/installing-windows-after-ubuntu-os-in-a-dual-boot-system/)

---

### Post by CelticWarrior on 2020-11-03
If the system is UEFI the order of OS installations isn't relevant.

---

### Post by Frogs Hair on 2020-11-03
> **CelticWarrior said:**
> If the system is UEFI the order of OS installations isn't relevant. 

One way to check is with the following command if you aren't sure.   ```
ls /sys/firmware/efi
```

---

