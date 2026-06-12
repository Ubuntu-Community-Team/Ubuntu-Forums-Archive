---
title: "SATA DVD drive not detected: TEST_UNIT_READY failed"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gtdaqua on 2009-03-17
Ever since moving to Jaunty, the SATA DVD drive has not been detected. When the system boots up right after the GRUB screen, it will pause for 4 seconds and the dvd drive light will flash. 

My PC is a Dell Optiplex 740. The kernel is x86 2.6.28-9.31-generic

When running in recovery mode I noticed the following:
```

[ 3.492191] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1A, max UDMA/33
[ 3.492201] ata2.00: applying bridge limits
[ 3.524206] ata2.00: configured for UDMA/33
[ 8.524024] ata2.00: qc timeout (cmd 0xa0)
[ 8.524028] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[ 9.404041] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 9.460210] ata2.00: configured for UDMA/33
[ 14.460023] ata2.00: qc timeout (cmd 0xa0)
[ 14.460026] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[ 14.460029] ata2: limiting SATA link speed to 1.5 Gbps
[ 14.460032] ata2.00: limiting speed to UDMA/33:PIO3
[ 15.340041] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 15.396210] ata2.00: configured for UDMA/33
[ 20.396023] ata2.00: qc timeout (cmd 0xa0)
[ 20.396026] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[ 20.396028] ata2.00: disabled
[ 20.396038] ata2: hard resetting link
[ 21.276039] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 21.276045] ata2: EH complete
[ 21.338514] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[ 21.338517] sata_nv 0000:00:0f.0: Using SWNCQ mode
[ 21.338567] sata_nv 0000:00:0f.0: setting latency timer to 64
[ 21.338723] scsi2 : sata_nv
[ 21.338855] scsi3 : sata_nv
[ 21.339071] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
[ 21.339074] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
[ 22.070434] ata3: SATA link down (SStatus 0 SControl 300)
[ 22.802431] ata4: SATA link down (SStatus 0 SControl 300)

```

The drive works perfectly on previous distros and other operating systems are seeing the drive.

The all_generic_ide parameter didnt help either. I have reported the bug in Launchpad: [Bug 344128: SATA DVD drive not detected]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344128")

Has anybody else experienced a similar problem?

---

### Post by walaric on 2009-04-04
I have the same problem since 8.04. With LILO instead of GRUB, the dvd driver will be found but u will lost usplash and u will have to reconfigure lilo each time you will update the kernel. Another temporary tip is to add acpi=off at the end of kernel line on grub but the system will be unstable and u will lose acpi management especially important with laptop.

I don't find any others solutions. If u find some, let me know...

---

