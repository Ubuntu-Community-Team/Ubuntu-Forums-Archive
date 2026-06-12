---
title: "Lenovo Miix Tablet won't boot USB stick install"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by Pasi_Patama on 2014-04-24
For start;

* Just got my hands on of these: [http://shop.lenovo.com/us/en/tablets/ideatab/miix-series/miix10/](http://shop.lenovo.com/us/en/tablets/ideatab/miix-series/miix10/)
* I strugled around UEFI settings, doing as described here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)0
* And created live USB stick (14.04 AMD64) with Disk Creator and also with 'dd'. 

Trouble is that this device does not boot from USB stick. It sees stick in boot menu, but boot fails to load ubuntu. I have tried everything as provided, but turning secureboot, fastboot off does not bring any difference. 

Any ideas?

---

### Post by tregas on 2014-05-12
I believe that the Atom CPUs are still only x86, so you'll need to try the 32-bit install image. I'm very curious if it works, as I'll be getting one of these soon.

---

### Post by ubfan1 on 2014-05-12
No, the Intel Atom Z3740 is a 64 bit processor.  Do you see a grub menu?  Try nomodeset  (edit the grub command and enter near the "splash quiet" (edit instructions on screen).

---

### Post by kenneth-fechter on 2014-06-23
the z3740 is a 64 bit processor, but the miix only has 32 bit efi. Ubuntu only has support  for 64 bit efi.

---

