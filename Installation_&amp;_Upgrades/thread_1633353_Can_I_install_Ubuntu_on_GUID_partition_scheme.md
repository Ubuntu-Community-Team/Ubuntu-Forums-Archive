---
title: "Can I install Ubuntu on GUID partition scheme?"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Doug11 on 2010-11-29
Just wondering if Ubuntu will install alongside OSX on a GUID partiton scheme.

---

### Post by srs5694 on 2010-11-29
Yes; however, Ubuntu doesn't play nice with EFI at the moment, so it relies on Apple's BIOS emulation, which in turn requires an ugly and dangerous [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration, similar to what Boot Camp creates for Windows. At best, this works without problems. At worst, it creates problems booting one or both OSes. IMHO, it's better to revert to a conventional GPT setup and use grub-efi rather than grub-pc; however, doing this requires some specialized knowledge and may require some troubleshooting. It can also complicate video support on some Macs.

---

