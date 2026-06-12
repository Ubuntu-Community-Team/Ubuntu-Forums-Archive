---
title: "Bootable device not found after install of ubuntu"
date: 2014-10-29
forum: Installation &amp; Upgrades
---

### Post by 4plaay on 2014-10-29
I am trying to install Ubuntu on a hard drive by itself but after install the computer reboots and says "boot device missing or failed". After this happened I booted with live cd and tried to run boot-repair. Below is a link to what I got from boot info after trying to run boot-repair and getting an error. It didn't tell me what the error was, just that it encountered errors. Hoping to get this fixed soon because I have a 4tb drive that's ext3 and need a Linux machine to watch all the movies on it.

[http://paste.ubuntu.com/8694966/](http://paste.ubuntu.com/8694966/)

Thank you

---

### Post by grahammechanical on 2014-10-29
At first glance I would say that the problems was that Grub was not installed into the MBR of sda. No boot loader. No loading of an OS.

At second glance I failed to see which partition Ubuntu was installed into. I guess it was installed into sda3 which is a LVM2. I suppose that should not be a problem. But when you installed Ubuntu did you tell the installer to put the boot loader into sda3 and not allow it to install Grub into the MBR of sda? That may be the problem and Boot Repair tripped up trying to fix it.

I am mostly guessing. No experience of Logical Volume Management (LVM).

Regards.

---

### Post by yancek on 2014-10-29
Your boot repair output shows nothing in the master boot record which could be because of an EFI install.  You do have an EFI partition (sda1) but there are no boot files there.  I don't know what sda2 is supposed to be.  I don't use LVM but generally there is a separate boot partition and the system files are in the LVM partition.  You need to either install the EFI boot files or reinstall Grub to the MBR and create a separate boot partition.  Might be easier just to reinstall.  Do you remember what option you selected during the installation?

---

