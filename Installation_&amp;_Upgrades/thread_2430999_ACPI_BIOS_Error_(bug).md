---
title: "ACPI BIOS Error (bug)"
date: 2019-11-10
forum: Installation &amp; Upgrades
---

### Post by kamui9624 on 2019-11-10
Hello guys,

I've installed Ubuntu six years ago on another machine, and now I would like to install it in the new one. Unfourtunately I'm facing a real pain in the a** every single time that I'm trying to use the live USB. I'm aware that this could be 100th time this question appear in the forum but no one seems to have found a way out, is this an hardware related problem that will be solved with some new driver implementation? You can see the output that I have when I try to install Ubuntu in the picture attached (sorry, I've never used dmesg in this situations).

P.S.: My laptop is a Lenovo Y540-15IRH.

Thank you and have a lovely day.

---

### Post by ubfan1 on 2019-11-10
First, check for any BIOS/firmware updates from the vendor.  Which release/kernel are you trying to install?  Trying 19.10 with the 5.x kernel might help.  acpi=0 on the grub linux line might allow you to boot at some reduced capability until you update kernels.

---

