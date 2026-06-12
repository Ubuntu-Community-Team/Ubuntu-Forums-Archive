---
title: "Can't get Ubuntu 13.04 (dualboot Win8) to boot"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by george4 on 2013-08-05
I installed Ubuntu alongside with Windows 8 but after I restart it just boots directly into Windows. I did a boot repair twice but it didn't solve the problem. 
Here is the dump bin of the repair [http://paste.ubuntu.com/5950086/](http://paste.ubuntu.com/5950086/)

---

### Post by carl4926 on 2013-08-05
Did you read this
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by george4 on 2013-08-05
Yes Ofc.

---

### Post by oldfred on 2013-08-05
You are showing Ubuntu in the efi partition, and then UEFI should offer that as a choice. But some systems will only boot with secure boot on and you have to install the signed versions of Ubuntu kernels to get Ubuntu to boot in secure boot mode.
Does you system boot Windows with secure boot off?  Some do and some do not. 
Also some have modified UEFI (not per standard) to only boot the Windows efi file. If that is the case Boot-Repair can rename the Windows file to really be the grub shim file that has the Microsoft signing key. Then you boot Windows and actually get grub menu. And from grub menu you boot the backed up Windows efi file.

HP seems to have all of its repair files as separate efi files and then Boot-Repair creates boot options for them. If you want to back up the 25_custom and houseclean you can. More info on cleaning up grub menus in the link in my signature.

---

