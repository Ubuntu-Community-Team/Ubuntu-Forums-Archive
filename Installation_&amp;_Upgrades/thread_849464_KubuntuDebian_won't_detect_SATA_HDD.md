---
title: "Kubuntu/Debian won't detect SATA HDD"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by Javaguy on 2008-07-04
Hi,

I recently bought a new Hard Disk to install linux on to. It's totally blank, on its own, on my Abit IP-35E motherboard with an intel IHC9 SATA Driver, as far as I can tell.

The problem is that neither the Kubuntu or the Debian Linux install programs detect the HDD at all (an 80GB Seagate model)

The partition manager in the Kubuntu setup just appears blank.

My full system specs are:

Intel Core 2 Duo E6420
P35 Motherboard
80GB Seagate SATA HDD (totally new)
2GB DDR2 RAM
Inno3d Geforce 8800GTS

Any help would be much appreciated, thanks!

---

### Post by logos34 on 2008-07-04
Check the Bios settings.  Hard disk detect should be set for 'Auto'.  If necessary try different sata modes (but disable RAID):

>Integrated peripherals>On-Chip SATA

> OnChip SATA Controller
This item enables or disables the onchip SATA controller.
      OnChip SATA Mode (For model &#8220;IP35&#8221; only)
-
This item selects the mode for devices connected through SATA ports.
[**IDE**]: The on-chip Serial ATA served as IDE mode.
IP35/IP35-E                                                          2-11
[RAID]: The on-chip Serial ATA served as RAID mode.
[**AHCI**]: The on-chip Serial ATA served as AHCI (Advanced Host Controller Interface) mode for
advanced performance and usability.

---

### Post by twodollaz on 2008-08-07
I had the same problem - your motherboard 'double books' the irqs for the first four sata devices with the pata. Windows can tell what's going on with the JMicron chip, but some versions of linux can't. If you use the sata plugs numbered 5 and 6 the problem will disappear. The IP-35e doesn't have the BIOS setting mentioned in the previous post. Hope this helps.

---

### Post by balcis on 2009-02-21
> **twodollaz said:**
> I had the same problem - your motherboard 'double books' the irqs for the first four sata devices with the pata. Windows can tell what's going on with the JMicron chip, but some versions of linux can't. If you use the sata plugs numbered 5 and 6 the problem will disappear. The IP-35e doesn't have the BIOS setting mentioned in the previous post. Hope this helps.

same problem with 4 sata connections on mainboard? asus a8v-mx. how to reorganize irqs for that, any idea?

---

