---
title: "Kernel Panic - installing edgy on via vb6002 motherboard"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by professordes on 2007-03-13
The 2.6.17 kernel in Edgy generates a kernel panic on boot when attempting to install on a Via VB6002 Mini-ITX motherboard. 

Has anyone out there succeeded in getting the Edgy kernel to boot on this MB?
It has a VIA VN800 North Bridge and a VT8237R  South Bridge. I'm
not sure if either of these chipsets cause problems generally.

I can get it to run with a 2.6.20 kernel pulled from the Feisty git repository,
but it's a bit of a pain installing on a disk elsewhere, putting this later kernel
in and then putting the disk back with the motherboard....

---

### Post by Daveski on 2007-03-16
2.6.17 gives *Kernel panic - not syncing:  Attempted to kill init!* on a machine with a VIA KT400/KT600 chipset.

Adding *acpi=force* option in /boot/grub/menu.lst solved the problem and the machine works fine now. It seems that the VIA chipsets have some problems with this kernel.

---

