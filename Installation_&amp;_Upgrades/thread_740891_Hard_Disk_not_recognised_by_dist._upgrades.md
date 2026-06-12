---
title: "Hard Disk not recognised by dist. upgrades"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by blokkendoos on 2008-03-31
Hello there,

I was building a new machine (specs later) and wanted to install Ubuntu 7.10. The one and only hard disk (western digital wdc400bb; ide) was not found.
What I could install was version 6.10. Though it boots very slow. But once it is up and running it is performing OK.

I tried to search for a solution or known problem on several fora but found nothing that looked like something I was looking for.

I tried several other installations, but none of them see the hard disk.
Here are some snippets from dmesg:
[17179575.444000] libata version 1.20 loaded.
[17179575.444000] sata_sis 0000:00:05.0: version 0.5
[17179575.444000] sata_sis 0000:00:05.0: Detected SiS 180/181 chipset in SATA mode
[17179575.444000] ata1: SATA max UDMA/133 cmd 0xC800 ctl 0xC402 bmdma 0xB400 irq 169
[17179575.444000] ata2: SATA max UDMA/133 cmd 0xC000 ctl 0xB802 bmdma 0xB408 irq 169
[17179575.648000] ata1: SATA link down (SStatus 0)
[17179575.648000] scsi0 : sata_sis
[17179575.852000] ata2: SATA link down (SStatus 0)
[17179575.852000] scsi1 : sata_sis
[17179579.800000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.068000] EXT3-fs: mounted filesystem with ordered data mode.
--------------------
[17179573.400000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179573.400000] SIS5513: chipset revision 1
[17179573.400000] SIS5513: not 100% native mode: will probe irqs later
[17179573.400000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179573.400000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179573.400000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179573.400000] Probing IDE interface ide0...
[17179573.688000] hda: WDC WD400BB-60JKC0, ATA DISK drive
[17179574.024000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.024000] Probing IDE interface ide1...
[17179574.760000] hdc: CD-ROM 36X/AKW, ATAPI CD/DVD-ROM drive
[17179575.096000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.100000] hda: max request size: 128KiB
[17179575.108000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179575.108000] hda: cache flushes supported
[17179575.108000]  hda: hda1 hda2 hda3
[17179575.148000] hdc: ATAPI 36X CD-ROM drive, 128kB Cache, DMA
[17179575.148000] Uniform CD-ROM driver Revision: 3.20
[17179575.440000] SCSI subsystem initialized
===================
What can be done to amend this problem??

Please advise,

pablo k

---

