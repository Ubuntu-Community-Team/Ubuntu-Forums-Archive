---
title: "HP ProBook 450 G3"
date: 2020-01-30
forum: Installation &amp; Upgrades
---

### Post by Kevin McCready on 2020-01-30
When I try to boot this windows laptop from the USB to install Linux, it doesn't work. 

It keeps booting from the hard disk.

When I try to change the boot order the legacy and the UEFI boxes are greyed out.

If anyone can help, that would be great.

---

### Post by CelticWarrior on 2020-01-30
How did you make that USB installer? How are you trying to boot from it?

Do you want to dual-boot or have Ubuntu only? Your laptop will probably be a PITA to run a dual-boot (but it's possible with some additional steps)

---

### Post by Kevin McCready on 2020-01-30
After much trial and error this worked:
Press and hold F2 for bios, in security  section set new supervisor password then in boot section set secure boot to disabled. Then set boot order to USB. Try rebooting and holding down F12.  disable UEFI Boot mode and select legacy

---

### Post by CelticWarrior on 2020-01-30
Legacy is a very bad idea if you have a factory installed Windows which is in UEFI mode. Installing Ubuntu in Legacy will not allow dual-booting from GRub and if you turned Legacy on system wide niow Windows won't boot either.

**Please STOP the Legacy/CSM madness NOW! Ubuntu supports UEFI at least since 2012!**

---

### Post by Kevin McCready on 2020-02-02
Ta for help. Appreciated. I used mksub and wiped out Windoze. So shouldn't be a problem. I get old computers and put Linux on for people who can't afford Windoze.

---

