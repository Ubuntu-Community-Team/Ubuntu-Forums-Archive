---
title: "Hardware detection fails on cd boot"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by moleculardeconstruction on 2005-11-04
I'm trying to install breezy on a fairly new laptop. The specs of the laptop are:

[http://www.pioneercomputers.com.au/products/info.asp?c1=3&c2=13&id=479](http://www.pioneercomputers.com.au/products/info.asp?c1=3&c2=13&id=479)


It starts the hardware detection and then stops at this point:


[4294673.128000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[4294673.128000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294673.128000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294673.128000] ehci_hcd 0000:00:1d.7: debug port 15
[4294673.128000] ehci_hcd 0000:00:1d.7: illegal capability!


The hoary CD boots, but has issues with the graphics. Breezy can't make it past this point.

Any help would be appreciated.

Thanks

---

