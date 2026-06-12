---
title: "W10 UEFI secure boot - dual boot Ubuntu 16.04"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by wqzwill on 2016-07-26
W10 (OEM) UEFI (secure boot) 64-bit. I want to install Ubuntu 16.04 in dual boot.
Questions :
1) Secure boot (now is enabled) should be disabled ?
2) After making the room for U16.04(/,/home,swap), in the combo "Device for boot loader instalation" we choose EFI partition ?
   (In EFI partition we have allready Windows Boot Manager).
Thanks.

---

### Post by ubfan1 on 2016-07-26
Ubuntu has no trouble installing UEFI on machines following the UEFI standard.  Some machines do not, however, so you might have to play vendor specific games like renaming the bootloader or boot EFI entry, adding "trust" to the bootloaders, etc.  Try it with secure boot enabled first.   The bootloaders will be installed in the first disk's EFI partition in their own directory (regardless of what you enter (bug)), so they don't interfere with the Windows bootloaders.

---

### Post by yancek on 2016-07-26
The site below is the Ubuntu documentation on dual booting UEFI with windows.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by wqzwill on 2016-07-27
[h=1][SIZE=3]Dual-boot Ubuntu 16.04 and Windows 10 on a PC with UEFI firmware[/SIZE][/h]                                    on June 5, 2016

[http://linuxbsdos.com/2016/06/05/dual-boot-ubuntu-16-04-and-windows-10-on-a-pc-with-uefi-firmware/](http://linuxbsdos.com/2016/06/05/dual-boot-ubuntu-16-04-and-windows-10-on-a-pc-with-uefi-firmware/)

---

