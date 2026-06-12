---
title: "Installed Ubuntu Studio - Not in Boot Menu"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by Hipster Doofus on 2012-01-07
I have windows 7 installed to sdb. opensuse to sda. I installed Ubuntu Studio next to opensuse. Ubuntu does not show up in the boot menu.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   100450303    50224128   83  Linux
/dev/sda2       100452350   234420223    66983937    f  W95 Ext'd (LBA)
/dev/sda5       117223424   121436159     2106368   82  Linux swap / Solaris
/dev/sda6       121438208   163381247    20971520   83  Linux
/dev/sda7       163383296   234420223    35518464   83  Linux
/dev/sda8       100452352   117223423     8385536   82  Linux swap / Solaris
```It might look a bit messy but this is my first attempt with Linux. (as long as it works)

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   234438655   117115904    7  HPFS/NTFS/exFAT
```The boot record is on the MBR & Ubuntu was suppose to go there. How do I add it?

---

### Post by Hipster Doofus on 2012-01-08
Well I got in using EasyBCD. Once. The next time the screen was all garbled. Anyway decided to toss openSUSE. So am going to try ubuntu studio once more on a fresh drive.

---

