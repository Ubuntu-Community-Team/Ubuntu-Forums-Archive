---
title: "Ubuntu installation alongside Windows 7 - cannot boot Windows anymore"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by urban-zaletel on 2016-05-10
Hi,

I have installed ubuntu alongside with Windows 7. Installation was successful, but I cannot log into the windows any more. I used boot-repair, but I still cannot log into the windows...
Do you have any idea, what could I do?
Report from boot-repair [http://paste.ubuntu.com/16346758/](http://paste.ubuntu.com/16346758/)

Thank you for your answers...

---

### Post by oldfred on 2016-05-10
It says you have a newer UEFI system, but both Windows & Ubuntu are installed in BIOS boot mode on MBR partitioned drives.
You should then always boot in BIOS mode. But you booted Boot-Repair in UEFI mode.

Did you use Windows to shrink the NTFS partition and reboot so it can run chkdsk? Or use installer.
Windows always needs chkdsk after a resize and you cannot run chkdsk or make most Windows repairs from Linux. You generally need a Windows repair flash drive.

Linux will not normally mount nor see NTFS partitions that are hibernated or need chkdsk to prevent further damage that might prevent chkdsk from repairing it.

First try this:
sudo update-grub

If that does not work then you probably need to run chkdsk on the NTFS partition.
Easiest to do from your Windows repair disk.
If not you may be able to temporarily reinstall a Windows type boot loader with Boot-Repair and see if f8 gets you to its internal repair console. Then reinstall grub with Boot-Repair.

---

