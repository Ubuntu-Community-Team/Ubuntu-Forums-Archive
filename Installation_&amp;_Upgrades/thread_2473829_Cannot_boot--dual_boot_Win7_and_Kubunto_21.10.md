---
title: "Cannot boot--dual boot Win7 and Kubunto 21.10"
date: 2022-04-14
forum: Installation &amp; Upgrades
---

### Post by zombie-hunter on 2022-04-14
Grub2 having issues and repair gets stuck at cannot delete previous grub.

Pastebin [https://paste.ubuntu.com/p/JwjTCBcBHH/](https://paste.ubuntu.com/p/JwjTCBcBHH/)

I can access a "try" Kubuntu OS from a USB
Normal boot goes to grub > and stops.  I can enter commands so grub appears to be functional,  but doesn't know where to look.

Any help would be appreciated.

---

### Post by oldfred on 2022-04-14
You cannot mix UEFI & BIOS.
System is UEFI, so all installs must be UEFI or must be all BIOS/CSM/Legacy.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Windows only boots in BIOS mode from MBR(msdos) partitioned drives.
Windows only boots \sin UEFI mode from gpt partitioned drives.
Conversion from MBR to gpt typically totally erases a drive, so have good backups.
Ubuntu can be installed in UEFI boot mode to MBR drive, but if Windows is BIOS, system will not work. Only one boot flag per drive & Windows has to have boot flag on its boot partition, but UEFI's ESP will have boot/esp flags on the ESP.

---

