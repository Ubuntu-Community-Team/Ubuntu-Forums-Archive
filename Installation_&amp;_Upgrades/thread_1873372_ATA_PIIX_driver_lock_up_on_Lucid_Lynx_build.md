---
title: "ATA_PIIX driver lock up on Lucid Lynx build"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by pauldemet on 2011-11-01
I have built a Lucid Lynx drive with LXDE on a proprietary platform. Everything works great but occasionally the OS will lock up during boot. The last message on the creen is 
"[SIZE=2]ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18[/SIZE]"
 
I have an emulator hooked up to the platform but the processor does not respond so it is not caught in some kind of loop.
 
I would like to debug the driver and step through the code using the emulator, but I cannot find the ata_piix source on the system.
 
Any ideas what could be the problem?
 
Also, how is this driver built by the OS without the source code?
 
Thanks.

---

### Post by pauldemet on 2011-12-06
Still chasing this issue.
 
Now have it narrowed down to the pcibios_enable_device function. It appears that this function calls acpi_pci_irq_enable and never returns. Any ideas would be appreciated.

---

