---
title: "Errors after recompiling"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by hisdudeness on 2006-06-22
Hi to all,
I'm a new ubuntu user and some days ago I decided to recompile my kernel to make it lighter.
After recompiling I get some errors at boot time. Here's part of my dmesg:


ata1: SATA max UDMA/133 cmd 0xF80 ctl 0xF02 bmdma 0xE000 irq 16
ata2: SATA max UDMA/133 cmd 0xE80 ctl 0xE02 bmdma 0xE008 irq 16
ata1: SATA link up 3.0 Gbps (SStatus 123)
ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4773 85:7c69 86:3e01 87:4763 88:407f
ata1: dev 0 ATA-7, max UDMA/133, 312581808 sectors: LBA48
ata1: dev 0 configured for UDMA/133
scsi0 : sata_nv
ata2: SATA link down (SStatus 0)
scsi1 : sata_nv
  Vendor: ATA       Model: Maxtor 6V160E0    Rev: VA11
  Type:   Direct-Access                      ANSI SCSI revision: 05
 0:0:0:0: Attached scsi generic sg0 type 0
SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
 sda: sda1 sda2 < sda5 sda6 sda7 > sda3 sda4
sd 0:0:0:0: Attached scsi disk sda
[B]FAT: invalid media value (0x2b)
VFS: Can't find a valid FAT filesystem on dev sda4.
FAT: invalid media value (0x2b)
VFS: Can't find a valid FAT filesystem on dev sda4.
Unable to identify CD-ROM format.
NTFS-fs warning (device sda4): is_boot_sector_ntfs(): Invalid boot sector checksum.
NTFS-fs error (device sda4): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sda4): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sda4): ntfs_fill_super(): Not an NTFS volume.
UDF-fs: No partition found (1)[/B]
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 18
GSI 21 sharing vector 0xD9 and IRQ 21
ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNEC] -> GSI 18 (level, low) -> IRQ 21
PCI: Setting latency timer of device 0000:00:05.0 to 64
NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8762  Mon May 15 13:58:14 PDT 2006
Adding 522104k swap on /dev/sda3.  Priority:-1 extents:1 across:522104k
EXT3 FS on sda4, internal journal
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda7, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
NTFS volume version 3.1.
NTFS volume version 3.1.
NTFS volume version 3.1.


The lines I'm talking about are the bolded ones. I can't understand the reason of these errors.
Anyway the system starts and I can do anything. I just want to understand the reason of these warnings.
Can someone help me?
Cheers

---

