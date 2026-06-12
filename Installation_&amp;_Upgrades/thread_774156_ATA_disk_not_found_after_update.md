---
title: "ATA disk not found after update"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by g0ng on 2008-04-29
Hello,

I upgraded my ubuntu box to hardy. This computer has one SATA disk and one IDE.

After the upgrade the IDE drive isn't found. There isn't any /dev/hda. 
I tried dmesg|grep ATA and I get:

```
[  135.023679] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[  135.023695] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[  145.504297] ata2.00: ATAPI: SONY DVD-ROM DDU1612, DYS3, max UDMA/33
[  145.688548] ata3: SATA max UDMA/133 mmio m4096@0xdf020000 port 0xdf020200 irq 19
[  145.688552] ata4: SATA max UDMA/133 mmio m4096@0xdf020000 port 0xdf020280 irq 19
[  145.688555] ata5: PATA max UDMA/133 mmio m4096@0xdf020000 port 0xdf020300 irq 19
[  146.155406] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  146.165179] ata3.00: ATA-6: WDC WD1200JD-00GBB0, 02.05D02, max UDMA/100
[  146.491133] ata4: SATA link down (SStatus 0 SControl 0)
[  146.647145] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200JD-00G 02.0 PQ: 0 ANSI: 5

```

(the 120GB disk is the sata one)

This computer has no monitor to see the BIOS messages, but before the upgrade it was OK. 

Any ideas please?

---

### Post by dstew on 2008-04-29
What is the output of ```
lspci
```?

---

### Post by g0ng on 2008-04-29
```
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:0b.0 RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

---

### Post by dstew on 2008-04-29
It seems the IDE interface hardware is detected. What is the output of ```
sudo fdisk -l
```?

---

### Post by benjisan on 2008-04-29
edit &#8230; [oops -- my problem was different; nevermind :)]

---

