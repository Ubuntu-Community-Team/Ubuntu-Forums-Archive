---
title: "Any fix for baytrail bug when installing, know fix for after"
date: 2019-05-17
forum: Installation &amp; Upgrades
---

### Post by crip720 on 2019-05-17
I am planning to replace hard drive with an ssd soon and do a clean install of maybe 16.04 or 18.04/19.04.  When I installed 16.04 had to try three or four times because of freeze up.  Was wondering if there is any fix for baytrail bug before or during installation, or if fix is already in 18.04 or 19.04.  It will be a clean install on blank ssd.  Thank you.

---

### Post by ubfan1 on 2019-05-17
I've not had any freezing problems with my z3735f compute stick (other than running out of memory).  The thing to watch out for in your setup is that the bootloaders wiill still try to  get installed onto /dev/sda1, which turn out to be the install media.  Recent reports of success in these cases (19.04?)  involve creating the EFI partition on the target, fat format, and manually mount it yourself at /boot/efi on the target.  Earlier reports trying this indicate failure, so you may have to manually copy all the bootlaoder files into their proper locations yourself (.../EFI/Boot/bootx64.efi (copy of shimx64.efi), .../EFI/Boot/grubx64.efi, .../EFI/ubuntu/grubx64.efi, .../EFI/shimx64.efi, and .../EFI/gurbx64.efi).  The grub.cfg should be just a stub bringing in the maintained copy from /boot/grub, but the full one will work (reinstall grub after things are working would be an easy fix to get the stub in place).

---

### Post by crip720 on 2019-05-17
Maybe the ssd be fast enough installing the freeze up does not happen.  Will be using a USB3 stick this time also.

---

