---
title: "boot twice necessary"
date: 2015-08-06
forum: Installation &amp; Upgrades
---

### Post by antigates on 2015-08-06
installed 14.04 with encrypt, seems to run fine, but:

have to boot twice, first time i get a brief ubuntu magenta screen, right to black and hangs.  click on, click off, and effective boot occurs with no further problems. 

not a big problem, but druther it booted first time. any easy answers? [hard answers over my head]

tried a re-install, no help, tried simple open install, ok, except there was a few instances of kb lag.

tried a 15 install, no boot at all.. is my hp 200omni unwelcome in latest ubuntu releases, i did find 12.01 wouldn't work, 12.04 would work if i got the right one.

thx for sympathy, double thx for a fix. triple thx if a humble user can execute.

---

### Post by dino99 on 2015-08-07
pay attention to your logs (mainly /var/log/dmesg, & Xorg.0.log) you might find something usefull to dig around the issue

---

### Post by antigates on 2015-08-08
thx, will poke around

---

### Post by oldfred on 2015-08-08
Is system UEFI or BIOS?
Many new UEFI systems will try to boot in UEFI mode, then change to boot in BIOS mode.

New HP with UEFI do not like anything other than Windows and have to have work arounds to have a bootable UEFI.

---

