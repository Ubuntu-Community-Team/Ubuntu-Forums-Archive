---
title: "No sound on DELL Dimension 5000"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by jrohde on 2005-08-12
Hi,

I've just installed Hoary on my DELL Dimension 5000 with a Creative SB audigy LS (as reported by HAL). When I try to launch the mixer, it says that it has not found any sound devices.

The only thing I can find in dmesg thats might have something to do with this are these lines:

pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5

Lspci shows: 0000:04:00.0 Multimedia audio controller: Creative Labs SB Audigy LS


Any suggestions?

Jakob

---

### Post by jrohde on 2005-08-13
Hi,

I've gone through the instructions in this post: [http://ubuntuforums.org/showpost.php?p=100951&postcount=1](http://ubuntuforums.org/showpost.php?p=100951&postcount=1)

But it didn't change anything.

Jakob

---

### Post by jrohde on 2005-08-13
Anybody?

This is the last problem I need to solve before I give up and return ti Windows XP.......

Is that a threat or what?

Jakob

---

