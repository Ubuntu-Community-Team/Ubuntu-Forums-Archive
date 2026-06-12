---
title: "HELP: Cannot Boot into Ubuntu - initramfs Exception emask"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by askmahesh on 2015-06-16
History: I had Ubuntu 15.04 running on my AMD 4 core desktop without any errors. I switched to a new desktop case (same motherboard, same SSD).

Now, after switching the case , when i started to boot into Ubuntu OS, i got ACPI probe failed and then got the initramfs failed error with emask Exception.
Only once it successfully booted and i could continue to work. But whenever i rebooted (because of upgrades), it failed to boot into Ubuntu. It gets stcuk at the initramfs error and never gets out of it. and eventually has black screen.
I even formatted the SSD (120 GB) and reinstalled Ubuntu , but still keeps getting this error. 

It also gives ALERT Dropping to shell error ...

I tried ediitng the grub menu to point the root to /dev/sda1, but no luck. 

HELP HELP !!!! Not sure what the cause of this problem and how to resolve it.

UPDATE: I went into the grub menu (pressing e) and changed the root=UUID=xxxxxxx with root=/dev/sda1 and it still gave the ACPI probe failed error . but booted into Ubuntu. 

But still looks like i have to this everytime and something is not correct here. I never had this problem earlier ever.

I still need help in knowing what the issue is and how to fix it permanently.

---

