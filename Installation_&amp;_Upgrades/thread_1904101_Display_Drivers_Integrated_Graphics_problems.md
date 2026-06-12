---
title: "Display Drivers Integrated Graphics problems"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by KoEDeath on 2012-01-04
ok, so ive been looking for a while for some form of Display Drivers for my integrated graphics, i have a mobile GM965/GL960 if some one could tell me were to obtain drivers for this it would be greatly appreciated.
sorry if this is in the wrong section i wasn't to sure which to put it in.


Thank you in advance. and for taking the time to assist me (a first time ubuntu user)

---

### Post by carl4926 on 2012-01-04
They are part of the kernel

Post result of

```
lspci -nnk
```

The driver will probably be : i915

---

### Post by mikewhatever on 2012-01-04
With Linux, most of the drivers are included, so that you don't have to look for them. In some cases, a printer or scanner driver may need to be downloaded for the vendor's website. Some wireless cards may also require looking around for drivers. Intel has all its chipsets drivers built into the kernel, with only the Poulsbo one being an exception.

---

### Post by KoEDeath on 2012-01-04
> **carl4926 said:**
> They are part of the kernel

Post result of

```
lspci -nnk
```The driver will probably be : i915

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Kernel modules: iTCO_wdt
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
    Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Kernel modules: i2c-i801
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
    Kernel driver in use: sky2
    Kernel modules: sky2
07:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
08:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
08:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc
08:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
08:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

These are my results, i assumed i didn't have any drivers because my performance on graphical interfaces is rather slow :/ TYVM for your responses. it is indeed I915 So that means i already have drivers installed, sry im new to ubuntu >.<.

---

### Post by carl4926 on 2012-01-04
Some intel chips are better than others

Yours should be OK. I have it on a R61
Works well

---

### Post by KoEDeath on 2012-01-04
> **carl4926 said:**
> Some intel chips are better than others

Yours should be OK. I have it on a R61
Works well

Ok tyvm for the help! :D i was also wondering, is it possible for me to get a virus with ubuntu ive heardmultiple answers of yeses and nos

---

### Post by carl4926 on 2012-01-04
> **KoEDeath said:**
> Ok tyvm for the help! :D i was also wondering, is it possible for me to get a virus with ubuntu ive heardmultiple answers of yeses and nos

No

You could become a carrier of one that could infect windows though. But that could apply to anyone.

Virus' that affect windows are no risk in Linux. I mean they will not deploy/run.

---

### Post by Mark Phelps on 2012-01-05
> **KoEDeath said:**
> i was also wondering, is it possible for me to get a virus with ubuntu ive heardmultiple answers of yeses and nos

Actually, despite what others will tell you, the actual answer is YES -- it's possible.  But the design of the Linux kernel, the limitations of the Linux filesystems, and the relatively low presence of Linux distros in the world PC space all combine to make it very unlikely that you WILL get a virus.

But, it actually IS possible.

---

### Post by carl4926 on 2012-01-05
Technically you more at risk from a rootkit.

Even if you managed to find a Virus and it were deployed, it'll not get far, because you'll not be running as root.

---

