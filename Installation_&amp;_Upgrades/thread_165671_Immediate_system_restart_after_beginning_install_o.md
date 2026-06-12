---
title: "Immediate system restart after beginning install of Dapper Drake"
date: 2006-04-25
forum: Installation &amp; Upgrades
---

### Post by tcsedc on 2006-04-25
Hi,

Using .iso images, I was successful loading Breezy Badger on grandpa's old computer, but am not having success with Dapper Drake or Xubuntu (based upon Breezy Badger).   The problem is with Dapper Drake and Xubuntu: the computer immediately reboots after I select the boot method and press "enter".  The system then just returns to the initial Install screen.  The hardware is Acer Aspire model with an AMD 450 MHz processor, 256M RAM, 20G hard drive.  I have tried acpi=off, pci=noacpi, noapic, no lapic, hw-detect/start_pcmia=false as boot options with no success.  (I have to set acpi=off to get Breezy Badger to complete the install).

Any ideas as to why the Breezy Badger install will work while Dapper Drake and Xubuntu don't?

---

### Post by Bazon on 2006-04-25
Did you try with the new Desktop CD?
Then maybe this:
[https://wiki.ubuntu.com/DapperBeta/PartitionTableCorruption](https://wiki.ubuntu.com/DapperBeta/PartitionTableCorruption)
(also shown in unabelity to finish the installer....)

---

