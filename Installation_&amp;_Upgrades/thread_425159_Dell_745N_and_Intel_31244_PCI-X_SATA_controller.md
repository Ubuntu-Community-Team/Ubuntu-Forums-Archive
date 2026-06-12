---
title: "Dell 745N and Intel 31244 PCI-X SATA controller"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by vtrac on 2007-04-27
I'm trying to install Ubuntu 6.06 on a Dell Powervault 745N with an intel 31244 PCI-X SATA controller.  The ubuntu CD boots fine, but it doesn't recognize the card.  It loads the proper module - sata_vsc but it doesn't seem to work.  Here is the relevant dmesg when I rmmod and modprobe the sata_vsc module:
```
[17180407.824000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[17180411.640000] libata version 1.20 loaded.
[17180411.644000] sata_vsc 0000:02:02.0: version 1.2
[17180411.644000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 25
(level, low) -> IRQ 177
[17180411.644000] ata1: SATA max UDMA/133 cmd 0xD0820200 ctl
0xD0820229 bmdma 0xD0820270 irq 177
[17180411.644000] ata2: SATA max UDMA/133 cmd 0xD0820400 ctl
0xD0820429 bmdma 0xD0820470 irq 177
[17180411.644000] ata3: SATA max UDMA/133 cmd 0xD0820600 ctl
0xD0820629 bmdma 0xD0820670 irq 177
[17180411.644000] ata4: SATA max UDMA/133 cmd 0xD0820800 ctl
0xD0820829 bmdma 0xD0820870 irq 177
[17180411.848000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17180411.848000] vsc_sata_interrupt: clearing interrupt, status 83;
sata err status 50002
[17180411.864000] ata1: PIO error
[17180411.876000] ata1: dev 0 failed to IDENTIFY (I/O error)
[17180411.876000] scsi8 : sata_vsc
[17180412.080000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17180412.080000] vsc_sata_interrupt: clearing interrupt, status 8300;
sata err status 50002
[17180412.096000] ata2: PIO error
[17180412.108000] ata2: dev 0 failed to IDENTIFY (I/O error)
[17180412.108000] scsi9 : sata_vsc
[17180412.312000] ata3: SATA link down (SStatus 0)
[17180412.312000] scsi10 : sata_vsc
[17180412.516000] ata4: SATA link down (SStatus 0)
[17180412.516000] scsi11 : sata_vsc
```

Any ideas?

---

### Post by gillhamg on 2007-09-28
Hello,
I'm just checking to see if you have been able to install Ubuntu on the Dell 745N using the Intel 31244 PCI-X SATA controller.

Thanks,
-Greg G.

---

