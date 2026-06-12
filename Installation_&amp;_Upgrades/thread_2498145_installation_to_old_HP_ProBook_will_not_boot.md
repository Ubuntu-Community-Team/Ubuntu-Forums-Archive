---
title: "installation to old HP ProBook will not boot"
date: 2024-06-01
forum: Installation &amp; Upgrades
---

### Post by gadjet0 on 2024-06-01
Hi,
I'm trying to install ubuntu 24.04 on an HP ProBook that was running windows, I used the USB boot to try Ubuntu then installed it but then it will not reboot, it just says "Install an operating system on you drive" or something similar.

I then installed Boot-Repair from the live USB disk and after the repair finished it now says "boot device not found", I've tried to get into the BIOS to change the boot options but I just get stuck in a loop whenre it asks UEFI file or laptop drive to boot from.

I have this log from boot repair: [https://paste.ubuntu.com/p/Rm43PxM6Ts/](https://paste.ubuntu.com/p/Rm43PxM6Ts/) but I'm not experienced enough with Linux to figure out what's going on, any suggestions as to what I could try? any help greatfully recieved.

Phil

---

### Post by oldfred on 2024-06-01
You have installed in old BIOS boot mode on a newer gpt partitioned drive.
Since you have the required bios_grub partition it should work.

HPs typically have issues, but most will work.
Some systems in BIOS mode, need a boot flag. Grub does not use boot flag, but Windows does.
You can use gparted to put a boot flag on sda2.

Is HP set to boot in Legacy/BIOS/CSM boot mode, or whatever it calls it.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Do you  have latest UEFI/BIOS from HP for your system?

UEFI systems on HP have to have boot order set in UEFI settings (not boot), do you have something similar for BIOS boot settings.
HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings

New systems starting in 2020 are UEFI only, but may still call it BIOS.
My Dell says BIOS, but once in Settings it says UEFI only.

Exactly what model HP?

---

### Post by gadjet0 on 2024-06-01
Hi, it's HP ProBook 455 G2

---

### Post by tea for one on 2024-06-02
Given the age of your PC, perhaps Xubuntu may be worth a shot.

You could try an installation with only one partition (without a BIOS Boot partition):-
Remove all disks – only the target disk available

Boot into a “Try Xubuntu” live session in Legacy mode
Open terminal and check boot mode
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Open Gparted > Devices > Create a _msdos_ partition table on the target disk.
Open the installer
Installation type = Manual Installation (Something Else)
Select free space and click the + sign
Create one Primary partition with Ext4 file system and Mount point = / (system root)
Install Grub bootloader to device not to a partition (e.g sda not sda1)
(i.e. do not let the installer "Erase Disk and Install")
If you see a message/warning about ESP not found, ignore it and continue the installation.
The installer will show that only one partition is to be created and formatted.
Continue the installation
Rarely, you may need to flag the partition as boot or bls_boot

---

### Post by peterpaxaxelsson on 2024-08-10
Had the same issue on an old Zbook. Disabled Fast Boot did the trick.

---

