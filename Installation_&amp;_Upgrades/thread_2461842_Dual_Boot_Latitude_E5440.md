---
title: "Dual Boot Latitude E5440"
date: 2021-05-08
forum: Installation &amp; Upgrades
---

### Post by wajdyz on 2021-05-08
Hello
I need help with dual boot on Dell E5440, Windows 10 installed and Ubuntu.

When i change bios boot to Legacy, i get bad partition table message and it boots ubuntu
on UEFI it boots windows only

Boot-Repair log here
[https://paste.ubuntu.com/p/c3dNPsxT6k/](https://paste.ubuntu.com/p/c3dNPsxT6k/)

---

### Post by grahammechanical on 2021-05-08
Windows 10 is installed in UEFI mode and I think that you have installed Ubuntu in BIOS/CSM/legacy mode. The two boot modes are incompatible. If we load the Ubuntu live/install ISO image in UEFI mode then Ubuntu will install in UEFI mode. But if we load the Install image in BIOS mode then Ubuntu will install in BIOS mode and we get the result that you are experiencing. This wiki page is old. This situation has been known since the introduction of Windows 8. The information here may help you.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by oldfred on 2021-05-08
Since Windows is UEFI, you need to always boot system & any repair, or install flash drives in UEFI mode.

> BIOS is EFI-compatible, but it is not setup in EFI-mode for this installed-session.

> WindowsEFI detected. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. 


I typically suggest using Ubuntu live installer & add Boot-Repair using ppa to the live installer.

So Boot-Repair has suggested a fix.

---

### Post by wajdyz on 2021-05-08
So I can reinstall Ubuntu in UEFI mode.

Will try it thanks for help

---

### Post by oldfred on 2021-05-08
You can do a total reinstall of Ubuntu.
But only have to totally reinstall grub.
That converts from using grub-pc which is for BIOS/CSM/Legacy to grub-efi-amd64 which is for UEFI boot on most PCs.

---

