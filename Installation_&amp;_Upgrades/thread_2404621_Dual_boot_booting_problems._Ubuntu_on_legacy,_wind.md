---
title: "Dual boot booting problems. Ubuntu on legacy, windows on UEFI"
date: 2018-10-26
forum: Installation &amp; Upgrades
---

### Post by tenky on 2018-10-26
After installing dual boot I've noticed it doesn't load up the OS booting choice. Instead I need to access them through BIOS by changing boot options which is very annoying.
Both platforms are installed on same SSD. What are my options to fix the problem?

---

### Post by yancek on 2018-10-26
Ubuntu/Grub installed in Legacy mode won't boot windows UEFI.  This is explained at the Ubuntu documentation site at the link below.  Since you have mixed and EFI install of windows with a Legacy install of Ubuntu, booting through the BIOS is your only option until you change that by converting Ubuntu to UEFI mode, also explained at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

