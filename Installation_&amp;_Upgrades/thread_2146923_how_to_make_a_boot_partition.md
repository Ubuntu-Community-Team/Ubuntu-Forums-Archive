---
title: "how to make a boot partition?"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by Itayrabin on 2013-05-20
i tried installing ubuntu 13.04 along side windows 8. it install fine, but when i restarted, i did not have grub, so i tried re-installing it usuing the live-cd, but i got an error that was talking about my hard drive being GPT and me not having a voot partition..
i tried googling it and i think it is because i have a UEFI BIOS..
how can i make that boot partition so i could load into ubuntu?

---

### Post by sudodus on 2013-05-20
If you have installed an Ubuntu version with 64-bits, try YannBuntu's Boot-Repair script. See these links

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by fantab on 2013-05-20
You must turn off the "Secure Boot" from UEFI-BIOS and also "Fast Boot". Install Ubuntu and run [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") from Ubuntu LiveCD.

Windows8 already boots from EFI Boot Partition so you don't have to make a new one, unless you have messed up your EFI partition. But if that is so then Windows too will not boot.

---

