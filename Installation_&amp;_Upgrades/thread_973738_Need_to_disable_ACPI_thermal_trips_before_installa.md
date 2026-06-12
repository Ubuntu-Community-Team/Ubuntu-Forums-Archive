---
title: "Need to disable ACPI thermal trips before installation, no ACPI = no IDE"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by Gyruss on 2008-11-07
I have an ECS KM400-M2 with a broken BIOS (the latest one, unfortunately) which lies that the processor thermal zone temperature is always 70C. I'm trying to install Intrepid on it. During the install CD boot, as soon as the ACPI modules load, the temperature trips ACPI's thermal protection and immediately sends a halt to the system.

Typically the way to deal with this problem is to use noapic nolapic acpi=off, boot and install, then add thermal.nocrt=1 to /etc/modules.d/options and enable ACPI again. However, on this board disabling ACPI makes the kernel panic with "can't find rootfs."

I know that at least some of the init scripts get to run before the thermal trip occurs when I boot with ACPI, so I know that the rootfs is just fine when ACPI is enabled. However, I've never heard of IDE being tied to ACPI like this.

Since I can't just disable ACPI, is it possible to disable ACPI's thermal trips from the kernel boot line? Despite myself I tried "thermal.nocrt=1" at the end of it and it's not recognized.

---

