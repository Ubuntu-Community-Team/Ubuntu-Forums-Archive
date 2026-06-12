---
title: "Installing in UEFI mode causes problems..."
date: 2015-09-19
forum: Installation &amp; Upgrades
---

### Post by mikevaughn on 2015-09-19
I'm  dual-booting with Windows 10. I installed Kubuntu in UEFI mode so I can  access Windows from the GRUB boot menu rather than having to go into  the BIOS each time, and now 4 of my USB ports don't work, boot time is drastically increased, and there's a ~10-second delay when sitting at the login screen before the  devices on the USB ports which *do* work start actually doing  anything. The following error message is displayed at the bootsplash  screen several times when booting:
```
usb 3-3: device descriptor read/8, error -110
```
The really odd thing is that a) this problem affects the OSes which  were installed prior to installing Kubuntu in UEFI mode, and b) the  problem resolved itself the last time I reinstalled Windows 10 (not just  for Windows 10, but for every OS I have installed).

  Any help with this would be much appreciated, as I'd rather not reinstall Windows again if I don't absolutely *have* to.

---

### Post by ubfan1 on 2015-09-20
Make and model of your machine?  A similar error in  [https://bbs.archlinux.org/viewtopic.php?id=198460](https://bbs.archlinux.org/viewtopic.php?id=198460)  was fixed by changing a UEFI setting for Advanced CPU, Boot performance,  from "Turbo" to "Max-non-turbo".

---

### Post by Bucky Ball on 2015-09-20
And which release of Kubuntu?

---

