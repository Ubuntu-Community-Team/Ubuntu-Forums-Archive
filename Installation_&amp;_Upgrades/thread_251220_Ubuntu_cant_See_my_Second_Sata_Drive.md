---
title: "Ubuntu cant See my Second Sata Drive"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by Wasca on 2006-09-05
HELP!!

I have a second 400GB Sata installed that is not being detected by Ubuntu

My ubuntu installed successfully on my first Sata disk 40GB and it appears as sda

here is some out put from dmesg

[42949376.080000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[42949376.080000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[42949376.080000] ICH5: chipset revision 2
[42949376.080000] ICH5: not 100% native mode: will probe irqs later
[42949376.080000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[42949376.080000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[42949376.080000] Probing IDE interface ide0...
[42949376.860000] hda: CD-RW CRX100E, ATAPI CD/DVD-ROM drive
[42949377.580000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[42949377.580000] Probing IDE interface ide1...
[42949378.210000] hda: ATAPI 24X CD-ROM CD-R/RW drive, 1024kB Cache, DMA
[42949378.210000] Uniform CD-ROM driver Revision: 3.20
[42949392.720000] SCSI subsystem initialized
[42949392.720000] ACPI: bus type scsi registered
[42949392.720000] libata version 1.20 loaded.
[42949392.720000] ata_piix 0000:00:1f.2: version 1.05
[42949392.720000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[42949392.720000] ata_pci_init_one: NO_LEGACY == 0
[42949392.720000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
[42949392.720000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[42949392.730000] ata1: PATA max UDMA/133 cmd 0xE000 ctl 0xDC02 bmdma 0xD000 irq 169
[42949392.730000] ata2: PATA max UDMA/133 cmd 0xD800 ctl 0xD402 bmdma 0xD008 irq 169
[42949392.970000] ata1: dev 0 cfg 00:0c5a 49:2f00 82:346b 83:7f01 84:4003 85:3469 86:3e01 87:4003 88:207f 93:0000
[42949392.970000] ata1: dev 0 ATA-6, max UDMA/133, 78125000 sectors: LBA48
[42949392.970000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe6f00
[42949392.970000] ata1: dev 0 configured for UDMA/133
[42949392.970000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe6f00
[42949392.970000] scsi0 : ata_piix
[42949423.130000] ata2: qc timeout (cmd 0xec)
[42949423.130000] scsi1 : ata_piix
[42949423.130000]   Vendor: ATA       Model: ST340014AS        Rev: 8.05
[42949423.130000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[42949423.140000] Driver 'sd' needs updating - please use bus_type methods
[42949423.140000] SCSI device sda: 78125000 512-byte hdwr sectors (40000 MB)
[42949423.140000] SCSI device sda: drive cache: write back
[42949423.140000] SCSI device sda: 78125000 512-byte hdwr sectors (40000 MB)
[42949423.140000] SCSI device sda: drive cache: write back
[42949423.140000]  sda: sda1 sda2 < sda5 >
[42949423.180000] sd 0:0:0:0: Attached scsi disk sda
[42949423.510000] Probing IDE interface ide1...
[42949424.170000] Attempting manual resume
[42949424.220000] kjournald starting.  Commit interval 5 seconds
[42949424.220000] EXT3-fs: mounted filesystem with ordered data mode.
[42949427.150000] sd 0:0:0:0: Attached scsi generic sg0 type 0



Why can't my second Sata disk be identified by Ubuntu?

Oh yeah I can see the second disk in my BIOS just fine.

Thanks

---

### Post by petri on 2006-09-05
What does ```
gedit /etc/fstab
``` and ```
sudo fdisk -l
``` say?

---

