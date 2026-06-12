---
title: "acpi support for intel mobos"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by thechris on 2011-12-23
I can't get intel mobo's to boot the live usb without the acpi=off option.  As this is nearly 2012, this is very undesirable.  ACPI appears responsible for things like actually shutting down the PC.

The first system was an i5 2500k with an MSI P67a-g43 motherboard.  I've since returned the motherboard, as it also would not allow itself to be turned off, and I don't want to deal with flakey HW.

The new motherboard is an ASUS P8Z68-V.  It can be power cycled correctly.  However, the usb key again crashes when it finds itself.  eg, the usb subsystems find a removable scsi device "sdb".

Previously, a similar issue occured when ubuntu was installed.  at scripts /init/boot-bottom or such, the system would just stop.  That issue was solved again with the acpi=off workaround.

How does one get acpi support to work in ubunutu?

---

