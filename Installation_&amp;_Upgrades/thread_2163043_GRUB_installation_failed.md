---
title: "GRUB installation failed"
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by stephanos21 on 2013-07-16
I tried to dual boot win8 and kubuntu on an ASUS K55VD. GRUB installation is failing [http://paste.ubuntu.com/5882559/](http://paste.ubuntu.com/5882559/)

---

### Post by oldfred on 2013-07-17
I do not see issue with Boot-Repair, but it may just be it expects grub to be in a ubuntu folder in the efi partition and yours is kubuntu. First time I have seen other than ubuntu. I did see one user complain many months ago and maybe they have updated that, but Boot-Repair has not?

Does your system boot Windows with secure boot off? You have done the file rename for those systems that only boot the Windows files, but have not installed the signed kernels & grub shim to boot Ubuntu with secure boot on.

Can you boot from the kubuntu entry from UEFI?

---

