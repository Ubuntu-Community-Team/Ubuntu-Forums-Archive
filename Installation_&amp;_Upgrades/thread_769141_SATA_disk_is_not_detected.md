---
title: "SATA disk is not detected"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by ivancruz on 2008-04-26
Ok. Definitively I'm not the only one with these problem, but I'm making a new thread anyway hoping someone have a insight on it.

My configuration is pretty mixed:
1. my main disk is a old SCSI U160 Seagate.
2. i have an aditional Samsung SATA 250MB for backup and media files.
3. and finally there is an LD IDE DVD Multi recorder.
4. main board is ASUS A8X with 4 SATA ports.

Had many problems when upgrading using 8.04 DVD but managed to solve most by myself. The one I need a urgent solution is my SATA disk not being detected. I will supply some syslog excerpts before and after the upgrade.

Before upgrade
```

... Detecting SATA disk ...
Apr 26 01:18:20 IvanAMD32 kernel: [   29.354193] ata1: SATA max UDMA/133 cmd 0xf8818d00 ctl 0x00000000 bmdma 0x00000000 irq 16
Apr 26 01:18:20 IvanAMD32 kernel: [   29.354197] ata2: SATA max UDMA/133 cmd 0xf8818d80 ctl 0x00000000 bmdma 0x00000000 irq 16
Apr 26 01:18:20 IvanAMD32 kernel: [   29.354200] ata3: SATA max UDMA/133 cmd 0xf8818e00 ctl 0x00000000 bmdma 0x00000000 irq 16
Apr 26 01:18:20 IvanAMD32 kernel: [   29.354204] ata4: SATA max UDMA/133 cmd 0xf8818e80 ctl 0x00000000 bmdma 0x00000000 irq 16
Apr 26 01:18:20 IvanAMD32 kernel: [   29.836222] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 26 01:18:20 IvanAMD32 kernel: [   29.836796] ata1.00: ATA-7: MAXTOR STM3250310AS, 3.AAA, max UDMA/133
Apr 26 01:18:20 IvanAMD32 kernel: [   29.836799] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr 26 01:18:20 IvanAMD32 kernel: [   29.837489] ata1.00: configured for UDMA/133
Apr 26 01:18:20 IvanAMD32 kernel: [   30.147735] ata2: SATA link down (SStatus 0 SControl 300)
Apr 26 01:18:20 IvanAMD32 kernel: [   30.459250] ata3: SATA link down (SStatus 0 SControl 300)
Apr 26 01:18:20 IvanAMD32 kernel: [   30.770764] ata4: SATA link down (SStatus 0 SControl 300)
Apr 26 01:18:20 IvanAMD32 kernel: [   30.770851] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM325031 3.AA PQ: 0 ANSI: 5
... Detecting IDE DVD ...
Apr 26 01:18:20 IvanAMD32 kernel: [   30.771289] Probing IDE interface ide0...
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789101] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789113] sd 0:0:0:0: [sda] Write Protect is off
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789116] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789127] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789170] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789177] sd 0:0:0:0: [sda] Write Protect is off
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789179] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789189] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 26 01:18:20 IvanAMD32 kernel: [   30.789193]  sda: sda1
Apr 26 01:18:20 IvanAMD32 kernel: [   30.807775] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 26 01:18:20 IvanAMD32 kernel: [   30.811998] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 26 01:18:20 IvanAMD32 kernel: [   31.337885] Probing IDE interface ide1...
Apr 26 01:18:20 IvanAMD32 kernel: [   32.200626] hdc: HL-DT-ST DVDRAM GSA-4167B, ATAPI CD/DVD-ROM drive
Apr 26 01:18:20 IvanAMD32 kernel: [   32.537001] ide1 at 0x170-0x177,0x376 on irq 15

```

After upgrading
```

... Detecting DVD ...
Apr 26 03:28:24 IvanAMD32 kernel: [   28.211806] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Apr 26 03:28:24 IvanAMD32 kernel: [   28.211809] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Apr 26 03:28:24 IvanAMD32 kernel: [   28.237537] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Apr 26 03:28:24 IvanAMD32 kernel: [   28.486381] Floppy drive(s): fd0 is 1.44M
Apr 26 03:28:24 IvanAMD32 kernel: [   28.503417] FDC 0 is a post-1991 82077
Apr 26 03:28:24 IvanAMD32 kernel: [   28.691576] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL10, max UDMA/33
Apr 26 03:28:24 IvanAMD32 kernel: [   28.863248] ata2.00: configured for UDMA/33
Apr 26 03:28:24 IvanAMD32 kernel: [   28.866996] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL10 PQ: 0 ANSI: 5
Apr 26 03:28:24 IvanAMD32 kernel: [   28.867171] ahci 0000:00:0f.0: version 3.0
Apr 26 03:28:24 IvanAMD32 kernel: [   28.867183] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 16
Apr 26 03:28:24 IvanAMD32 kernel: [   28.867228] ahci 0000:00:0f.0: controller can't do NCQ, turning off CAP_NCQ
Apr 26 03:28:24 IvanAMD32 kernel: [   28.867230] ahci 0000:00:0f.0: controller can't do PMP, turning off CAP_PMP
Apr 26 03:28:24 IvanAMD32 kernel: [   29.022088] Driver 'sr' needs updating - please use bus_type methods
Apr 26 03:28:24 IvanAMD32 kernel: [   29.030164] sr0: scsi3-mmc drive: 78x/78x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 26 03:28:24 IvanAMD32 kernel: [   29.030169] Uniform CD-ROM driver Revision: 3.20
Apr 26 03:28:24 IvanAMD32 kernel: [   29.030216] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 26 03:28:24 IvanAMD32 kernel: [   29.034870] sr 1:0:0:0: Attached scsi generic sg0 type 5
... Failing to detect SATA ...
Apr 26 03:28:24 IvanAMD32 kernel: [   29.869411] ahci 0000:00:0f.0: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Apr 26 03:28:24 IvanAMD32 kernel: [   29.869417] ahci 0000:00:0f.0: flags: 64bit pm led clo pio slum part 
Apr 26 03:28:24 IvanAMD32 kernel: [   29.869726] scsi2 : ahci
Apr 26 03:28:24 IvanAMD32 kernel: [   29.869994] scsi3 : ahci
Apr 26 03:28:24 IvanAMD32 kernel: [   29.870114] scsi4 : ahci
Apr 26 03:28:24 IvanAMD32 kernel: [   29.870230] scsi5 : ahci
Apr 26 03:28:24 IvanAMD32 kernel: [   29.870520] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 221
Apr 26 03:28:24 IvanAMD32 kernel: [   29.870523] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 221
Apr 26 03:28:24 IvanAMD32 kernel: [   29.870526] ata5: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 221
Apr 26 03:28:24 IvanAMD32 kernel: [   29.870529] ata6: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 221
Apr 26 03:28:24 IvanAMD32 kernel: [   30.344654] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 26 03:28:24 IvanAMD32 kernel: [   30.345160] APIC error on CPU0: 00(08)
Apr 26 03:28:24 IvanAMD32 kernel: [   60.297971] ata3.00: qc timeout (cmd 0xec)
Apr 26 03:28:24 IvanAMD32 kernel: [   60.297978] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Apr 26 03:28:24 IvanAMD32 kernel: [   60.297981] ata3: failed to recover some devices, retrying in 5 secs
Apr 26 03:28:24 IvanAMD32 kernel: [   65.777433] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 26 03:28:24 IvanAMD32 kernel: [   65.777936] APIC error on CPU0: 08(08)
Apr 26 03:28:24 IvanAMD32 kernel: [   95.730750] ata3.00: qc timeout (cmd 0xec)
Apr 26 03:28:24 IvanAMD32 kernel: [   95.730757] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Apr 26 03:28:24 IvanAMD32 kernel: [   95.730760] ata3: failed to recover some devices, retrying in 5 secs
Apr 26 03:28:24 IvanAMD32 kernel: [  101.210221] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 26 03:28:24 IvanAMD32 kernel: [  101.210705] APIC error on CPU0: 08(08)
Apr 26 03:28:24 IvanAMD32 kernel: [  131.163540] ata3.00: qc timeout (cmd 0xec)
Apr 26 03:28:24 IvanAMD32 kernel: [  131.163548] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Apr 26 03:28:24 IvanAMD32 kernel: [  131.163550] ata3: failed to recover some devices, retrying in 5 secs
Apr 26 03:28:24 IvanAMD32 kernel: [  136.642992] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 26 03:28:24 IvanAMD32 kernel: [  136.954507] ata4: SATA link down (SStatus 0 SControl 300)
Apr 26 03:28:24 IvanAMD32 kernel: [  137.266019] ata5: SATA link down (SStatus 0 SControl 300)
Apr 26 03:28:24 IvanAMD32 kernel: [  137.577533] ata6: SATA link down (SStatus 0 SControl 300)

```

And yes I have tried adding "noapic" and "acpi=off" to grub menu.lst without success.

Any other ideas please????

Ivan.

---

### Post by Pumalite on 2008-04-26
Have you tried getting inside your computer and changing ports?

---

### Post by ivancruz on 2008-04-26
Changing ports just change from ata3 to ata5 on syslog messages. Also adding all-generic-ide to kernel boot options doesn't help. Booting with the old 2.6.22 kernel makes the disk visible again but create other problems with screen resolution.

It's looking more and more as a kernel bug. There is any other thing I could try?

Ivan.

---

### Post by ivancruz on 2008-04-26
Ok giving up and trying to downgrade to kernel 2.6.22!
Thanks for all the help.

Ivan.

---

### Post by ivancruz on 2008-04-26
A final note: after downgrading the kernel, the screen resolution become unusable. The only options offered where 800x600 ou 640x480. The only solution was a "double" downgrade from nVidia driver to generic nv driver. It means goodbye compiz, but at least, after that, everything seems to be working well.

Ivan.

---

### Post by Pumalite on 2008-04-26
You just have to reinstall your driver.

---

### Post by ivancruz on 2008-04-26
Nope. Tried that.

Ivan.

---

### Post by ivancruz on 2008-04-27
Problem solved finally!!!

I was able to boot again with 2.6.24 using a boot time kernel option: all_generic_ide. On a prior try I wrote all-generic-ide following guidance from another thread. When checking related bugs on Launchpad I found the correct form.

Now it's all ok. nVidia drivers and compiz are working again.

Ivan.

---

