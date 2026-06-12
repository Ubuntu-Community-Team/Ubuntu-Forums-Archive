---
title: "Another LiveCD Boot Problem"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by SamGorden on 2007-11-12
The answer might be out there on the forums and i might have missed it but lets face it, there's a lot going on in these forums.

I have

Dell Latitude 131L
AMD 64 TL52
1g DDR2
Ati x1150 Graphic card
Broadcom 4306 (4310 possibly the same)
60g sata
and a trusty 24x DVD-R / CD-R/RW

When I load my 7.04 32bit LiveCD  it always gets to 


```
[      8.976000]  SB600_PATA: chipset revision 0
[      8.980000]  SB600_PATA: not 100% native mode: with probe irqs later
[      8.984000]  ide0:BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[      9.728000]  hda:  TSSTcorp DVD+/-RW TS-L632D, ATAPI CD/DVD-ROM drive
[    10.404000]  ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    10.436000]  hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048 kB Cache, UDMA(33)
[    10.440000]  Uniform CD-ROM driver Revision: 3.20

```


And thats where it stops. I've tried   noapic     nolapic  and   pci=nomsi

Now My 64bit 7.04 LiveCD   stops there too  but then the drive starts back up and it finishes booting in to ubuntu

My cd is pretty new and I've tried reburning it and all copies work on my desktop

I currently have the 64bit on the laptop atm but i would rather have the 32bit on there. Any help would be appreciated.

---

### Post by SamGorden on 2007-11-12
Atlease point me in the right direction... Or a good tutorial on how to install the 32bit from inside the 64bit

---

### Post by torgrot on 2007-11-12
I am unfamiliar with your PC but here are the command line qualifiers that I use on my Dell ro pci=biosirq acpi=off reboot=b quiet splash  That is what goes on the kernel line in my grub menu.lst  It just won't boot with out the acpi=off and pci=biosirq 

torgrot

---

### Post by SamGorden on 2007-11-12
I added the acpi=off and pci=biosirq   to the line and it worked

Thank you very much Torgrot !

---

