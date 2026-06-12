---
title: "Installation With Adaptec 2005S RAID"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by joelrob on 2007-06-25
I have an Adaptec 2005S hardware RAID controller (I20) and am trying to install Feisty Ubuntu (7.04) Server. The install goes fine, have tried both hardware and software configurations, but after the install, I get the following messages on boot:

MP-BIOS bug: 8254 timer not connected to IO-APIC
ACPI: Wrong _BBN value, reboot and use option 'pci=noacpi'
mdadm: No devices listed in conf file were found.
adpt_config_hba: pci request region failed
Could not Init an I20 RAID device

Buffer I/O error on device i2o/hda, logical block 1
Buffer I/O error on device i2o/hda, logical block 0

ldm_validate_partition_table(): Disk read failed.


it then drops me out to an initramfs prompt after hanging for a few minutes.

I've read several posts by users with similar issues and most of them say to mount the volume. However, fdisk -l doesn't work in the initframs shell so I can't see the hard drives the system is listing. I've tried mounting \dev\hda1 which is where I installed the OS, but that fails too.

Anyone found a workaround to this?

---

