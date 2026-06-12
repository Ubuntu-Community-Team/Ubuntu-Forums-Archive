---
title: "Install Ubuntu 12.04.3 on Samsung ATIV Book 8"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by hashmat2 on 2014-07-29
I am trying to boot Ubuntu 12.04(64 bit) on the laptop Samsung ATIV book 8. Samsung ATIV book 8 came with Windows 7. I am successfully able to install Linux Ubuntu 12.04 on the SSD using USB pen drive which has erased Windows 7. But when I go to the BIOS configuration, I am not able to select the SSD, it has disappeared after installing Linux on SSD and and the options are blank, no boot device options. I tried different combinations of changing the following boot options: - Secure boot control, OS mode selection, Fast BIOS mode.
But it doesn't give back the SSD option to boot.

I later followed install Ubuntu in UEFI mode ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)), not the boot repair option. But still the same problem, I don't see SSD device as boot device option in BIOS.
Is anybody successful in installing Ubuntu on ATIV 8 ? 

Thanks.

---

### Post by hashmat2 on 2014-08-01
Finally I am to install Ubuntu using following boot options:
CSM mode
Fast boot OFF
Secure boot OFF

---

