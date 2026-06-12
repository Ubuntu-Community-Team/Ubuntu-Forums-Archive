---
title: "Two OS's on one computer"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by The-Valk on 2016-01-11
I used to dual boot Windows and Ubuntu using grub to select the OS on boot up.
These days I prefer to install each OS onto its own disk by disconnecting any other drive from the PC and then reconnecting it after I had finished installing the new OS onto a fresh drive.
This allows me to select any of the installed drives I want to boot from by using F12 at the BIOS screen.
I am concerned though that if a Kernel update on Ubuntu requires grub to rework its magic this separation of each drives independent boot would be compromised.
Should I worry?

---

### Post by grahammechanical on 2016-01-11
No.

Grub would installed in the MBR of the Ubuntu drive. It looks for its configuration files in /boot/grub. When we are in Ubuntu and the Grub configuration files are updated it is the Grub files on the Ubuntu drive, in fact in the Ubuntu partition that are altered. Nothing will be done to the Windows drive.

A re-install of Grub as part of an update will re-install to the present location on the Ubuntu drive. We ourselves can issue certain commands that will update Grub and re-install Grub. And that is the time when we can direct Grub to be installed to the wrong drive. I have done this myself.

Another area that you might want to take note of. Re-installing Ubuntu or installing another Linux OS. The installer usually defaults to installing Grub into the MBR of the first hard disk (sda). If sda is the Windows drive, then the Windows boot loader will be over-written by Grub. So, we are either very careful about where Grub is installed or  we disconnect the Windows drive when installing Linux. 

Regards.

---

### Post by The-Valk on 2016-01-11
Thanks for the very helpful information.
I can now let Ubuntu upgrade its Kernel without the need to unplug the Windows drive.

---

### Post by howefield on 2016-01-11
> **The-Valk said:**
> I can now let Ubuntu upgrade its Kernel without the need to unplug the Windows drive.

A grub update will pick up the Windows install and add it to the grub boot menu, however you'll still have the separation of the boot loaders on each disk.

---

### Post by pfeiffep on 2016-01-11
I have 2 internal drives on my HP desktop, I use the HP boot menu (accessed by depressing 'esc' on power up) to choose from which drive to boot. I've found that not using grub to boot Win 7 has prevented some Win upgrades from failing.
Grub is installed only on the 'Ubuntu' drive and does provide the option to boot Windows.

---

