---
title: "Ubuntu 20.04"
date: 2021-09-05
forum: Installation &amp; Upgrades
---

### Post by predata on 2021-09-05
Recently i installed ubuntu but now i have same problem : i can't boot in windows and i can't boot in ubuntu because grub opened in console as Miniman bash-like how to fix it?

---

### Post by grahammechanical on 2021-09-05
After you installed Ubuntu were both operating systems working acceptably? Or, did this problem occur on the first re-boot into Ubuntu. Grub is the bootloader. If we have installed Ubuntu correctly we should be able to load either Windows or Ubuntu from the Grub boot menu. Do you see a Grub boot menu?

The error to you are experiencing comes when we select from Grub boot menu an OS to load but Grub cannot find the OS boot files. So, something is wrong and you need to give more information about your hardware (specifications) and the setup of the operating systems on your machine.

Windows version? UEFI motherboard? Did you install Ubuntu in the same mode as Windows was installed? Modern machines pre-installed with Windows 10 have Windows installed in UEFI mode. Ubuntu must be installed in the same mode. If we install Ubuntu in bios/legacy/CSM mode then we will not be able to dual boot with Windows in the usual manner.

Regards

---

