---
title: "grub-install doesn't recognize /dev/sda"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2013-01-27
I'm reconstructing my dual-boot system with Kubuntu 12.10 and Windows 7.  I first installed Windows 7.  I'm now running Kubuntu and trying to install it.  (I started it by using SuperGrub.)  I've already run **update-grub**.  But when I try to use **grub-install** I get this:
```
sudo grub-install /dev/sda
source dir doesn't exist.  Please specify --target or --directory
```
What am I missing?

---

### Post by Bucky Ball on 2013-01-27
Not sure. The command is correct. Sounds silly but you do have the sda device installed and working? No cables loose or popped off?

You might try Boot Repair which, if it doesn't work, can give us a lot more info about your machine and what is happening:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by pwabrahams on 2013-01-28
I solved the problem by installing grub-pc, which forced the deinstallation of grub-efi. After doing that, install-grub worked as it was supposed to. That's puzzling since my BIOS has UEFI activated.  There are several architectural variants of grub, it seems, and I don't understand how you're supposed to choose the right one.  In any event, the Kubuntu installation didn't choose the right one.

---

### Post by oldfred on 2013-01-28
How you boot install media is how it installs for both Windows and Ubuntu. And both really have to be installed in the same mode or dual booting is a real hassle, by going into UEFI/BIOS and changing each time.

Boot-Repair also does the same in either installing grub-pc or grub-efi to convert an install from BIOS to UEFI or vice-versa.

Window will normally only install in UEFI mode on gpt drives. Ubuntu will work in either UEFI or BIOS from gpt partitioned drives.

---

