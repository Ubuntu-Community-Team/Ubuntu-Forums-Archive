---
title: "ata1: COMRESET failed (errno=-16)"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by odinb on 2013-06-15
Hi!

Just installed on an ASUS P8H77-I motherboard with an Intel X25-E 32GB SSD Drive (SSDSA2SH032G1SB), and see something not right in the logfiles when booting, causing slow boots.

What I see repeatedly are messages like:
ACPI _SDD failed (AE 0x5)
ata1: link is slow to respond, please be patient (ready=0)
ACPI: failed the second time, disabled
ata1: COMRESET failed (errno=-16)

Any ideas on what I am doing wrong/could do to remedy/fix the issues?
The SSD worked just fine previously with a Gigabyte motherboard.
Are these HW compatibility issues, or kernel bugs?

Any hints on what I can do to remedy the situation?
Have checked, and I do have the latest firmware on the SSD (Firmware Revision:  845C8855).

Syslog snippet:

```
Jun 12 11:32:45  kernel: [    6.185593] ata1: link is slow to respond, please be patient (ready=0)
Jun 12 11:32:45  kernel: [    6.457326] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 12 11:32:45  kernel: [    6.457344] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 12 11:32:45  kernel: [    6.457358] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 12 11:32:45  kernel: [    6.457706] ata6.00: ACPI _SDD failed (AE 0x5)
Jun 12 11:32:45  kernel: [    6.457709] ata6.00: ACPI: failed the second time, disabled
Jun 12 11:32:45  kernel: [    6.457729] ata4.00: ACPI _SDD failed (AE 0x5)
Jun 12 11:32:45  kernel: [    6.457732] ata4.00: ACPI: failed the second time, disabled
Jun 12 11:32:45  kernel: [    6.457734] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 12 11:32:45  kernel: [    6.457757] ata3.00: ACPI _SDD failed (AE 0x5)
Jun 12 11:32:45  kernel: [    6.457759] ata3.00: ACPI: failed the second time, disabled
Jun 12 11:32:45  kernel: [    6.458098] ata5.00: ACPI _SDD failed (AE 0x5)
Jun 12 11:32:45  kernel: [    6.458100] ata5.00: ACPI: failed the second time, disabled
Jun 12 11:32:45  kernel: [    6.458109] ata6.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
Jun 12 11:32:45  kernel: [    6.458113] ata6.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jun 12 11:32:45  kernel: [    6.458122] ata4.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
Jun 12 11:32:45  kernel: [    6.458125] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jun 12 11:32:45  kernel: [    6.458168] ata3.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
Jun 12 11:32:45  kernel: [    6.458180] ata3.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jun 12 11:32:45  kernel: [    6.458579] ata5.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
Jun 12 11:32:45  kernel: [    6.458581] ata5.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jun 12 11:32:45  kernel: [    6.459067] ata3.00: configured for UDMA/133
Jun 12 11:32:45  kernel: [    6.459106] ata6.00: configured for UDMA/133
Jun 12 11:32:45  kernel: [    6.459144] ata4.00: configured for UDMA/133
Jun 12 11:32:45  kernel: [    6.459489] ata5.00: configured for UDMA/133
Jun 12 11:32:45  kernel: [    6.469314] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jun 12 11:32:45  kernel: [    6.469675] ata2.00: ACPI _SDD failed (AE 0x5)
Jun 12 11:32:45  kernel: [    6.469677] ata2.00: ACPI: failed the second time, disabled
Jun 12 11:32:45  kernel: [    6.470077] ata2.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
Jun 12 11:32:45  kernel: [    6.470079] ata2.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jun 12 11:32:45  kernel: [    6.470984] ata2.00: configured for UDMA/133
Jun 12 11:32:45  kernel: [   10.828872] ata1: COMRESET failed (errno=-16)
Jun 12 11:32:45  kernel: [   16.191419] ata1: link is slow to respond, please be patient (ready=0)
Jun 12 11:32:45  kernel: [   20.834707] ata1: COMRESET failed (errno=-16)
Jun 12 11:32:45  kernel: [   26.189256] ata1: link is slow to respond, please be patient (ready=0)
Jun 12 11:32:45  kernel: [   55.851096] ata1: COMRESET failed (errno=-16)
Jun 12 11:32:45  kernel: [   55.851142] ata1: limiting SATA link speed to 1.5 Gbps
Jun 12 11:32:45  kernel: [   56.170780] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 12 11:32:45  kernel: [   56.170948] ata1.00: ACPI _SDD failed (AE 0x5)
Jun 12 11:32:45  kernel: [   61.494367] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 12 11:32:45  kernel: [   61.494534] ata1.00: ACPI _SDD failed (AE 0x5)
Jun 12 11:32:45  kernel: [   61.494536] ata1.00: ACPI: failed the second time, disabled
Jun 12 11:32:45  kernel: [   61.494562] ata1.00: ATA-7: SSDSA2SH032G1SB INTEL, 845C8855, max UDMA/133
Jun 12 11:32:45  kernel: [   61.494565] ata1.00: 62500000 sectors, multi 16: LBA48 NCQ (depth 31)
Jun 12 11:32:45  kernel: [   61.494823] ata1.00: configured for UDMA/133
Jun 12 11:32:45  kernel: [   61.494916] scsi 0:0:0:0: Direct-Access     ATA      SSDSA2SH032G1SB  845C PQ: 0 ANSI: 5
Jun 12 11:32:45  kernel: [   61.495027] scsi 1:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
Jun 12 11:32:45  kernel: [   61.495138] scsi 2:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
Jun 12 11:32:45  kernel: [   61.495230] scsi 3:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
Jun 12 11:32:45  kernel: [   61.495324] scsi 4:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
Jun 12 11:32:45  kernel: [   61.495406] scsi 5:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
```

---

