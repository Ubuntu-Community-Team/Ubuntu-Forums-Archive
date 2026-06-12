---
title: "error invalid EFI file path."
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by jorovifi on 2013-05-19
Hi I do not know why my boot loader stop working. I've  been using dual boot for long time and after installing a windows  software (AutoCAD) my system reboot and restarts on grub loading  creating always a loop.


When trying to repair with a  recovery CD, my Windows 7 partition says "error invalid EFI file path",  with the recovery file I can get in into Ubuntu. 


this is the generated file by the tool: [http://paste.ubuntu.com/5682358/](http://paste.ubuntu.com/5682358/)

I've tried reinstalling grub, from ubuntu and a recovery CD, nothing yet.


Thank you very much in advanced.

---

### Post by oldfred on 2013-05-20
Your installs are all BIOS with MBR(msdos) partitioning. 
But it does look like you booted Boot-Repair in UEFI mode. Do you then have a UEFI/BIOS that works either way and you changed settings in UEFI to boot in UEFI mode not BIOS/CSM/Legacy mode?

It looks like you have an older grub in sdb's MBR and the newer grub in sda. 
I would install the newer grub from sdb7 into sdb and install a Windows boot loader into the MBR of sda, so you could boot it directly if sdb ever has issues.

---

