---
title: "CDROM makes IO Errors and hangs"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by linuxhelp on 2005-04-11
Hello,

could anyone help? 

Ubuntu 5.04 CD Install April 2005
System IBM Laptop A20 with DVD-ROM IDE normal
how is the right commad at boot to set pio in grub menu.lst
for kernel? (/dev/hdc)

The boot without acpi does not help and ide=nodma too!!

Error in /var/log/messages

ubuntu kernel: hdc: irq timeout: status 0x50 [DriveReady SeekComplete]
ubuntu kernel: hdc: irq timeout error 0x00
ubuntu kernel: hdc: ATAPI reset complete
ubuntu kernel: hdc: end_request I/O Error,dev,hdc,[Flags: R/O Module]
 

Thanks Thomas

---

### Post by linuxhelp on 2005-05-30
Solution:


Install on boot with option to kernel "noapic" and "noacpi"

this surpress the acpi mode on installation and after this

the system is installed without acpi table changes on boot

This is an IBM BIOS LAPTOP PROBLEM!!!

Problem :

No Energysaving and no shut down automatic,

but CDROM an System runs 24hours daily stable

[WWW.LINUXONLINEHELP.DE](WWW.LINUXONLINEHELP.DE)

---

### Post by Jad on 2005-10-19
I have same problem with breezy
any idea how to solve it?

---

