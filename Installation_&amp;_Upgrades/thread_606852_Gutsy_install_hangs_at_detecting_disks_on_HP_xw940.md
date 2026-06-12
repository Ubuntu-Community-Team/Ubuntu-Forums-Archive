---
title: "Gutsy install hangs at detecting disks on HP xw9400"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by kbyrd on 2007-11-08
Using the mini.iso, on an amd64 HP xw9400, I'm trying to install 7.10. The machine has previously run similar kernels (2.6.22/23 from Debian unstable).

I accept the defaults, detect-disk hangs for a while, eventually showing the via82cxxx driver. Dmesg shows me an OOPS, and something about not being able to handle an allocation request. I don't have an easy way to capture the full dmesg output, but here's the call stack that I wrote down:

pci_bus_write_config_byte
new_slab
__slab_alloc
ide_core:init_irq

This box has an LSI MPT SAS/SATA controller and an IDE controller. I'm trying to install from an IDE CD-ROM to a SAS disk. I have SATA disk installed, but I want to leave it alone. 

Help?!?

---

### Post by kbyrd on 2007-11-09
Bump and more info:

I decided to go around the IDE controller, so I created a bootable usb key using the boot.img.gz file in the mini.iso directory. If i disable the IDE controller (NFORCE MCP-55)  in the BIOS and boot from that, I get past disk-detect. 

I haven't completed the install yet for other reasons, I'll post back when I get it running.

---

### Post by kbyrd on 2007-11-16
Gutsy is installed and running, as long as I keep the IDE controller turned off in the BIOS.

Any hope of getting this fixed?

---

