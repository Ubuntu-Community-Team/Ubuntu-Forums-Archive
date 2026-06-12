---
title: "Raid 0 with western digital raid card (promise controller)  HELP with EE installation"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by citrusfizz on 2006-12-31
hello  guys..

need some help

i just got a raid card last night... its an older western digital  raid card
and i have 2 baracudas in a raid 0 set up
i installed windows just fine 
i went to install kubuntu now

and it shows me both the drives   not one big drive

what do i need to apt-get or  modprobe.. or whatever to get this working correctly?

---

### Post by citrusfizz on 2006-12-31
the card is a fasttrak s150 tx   if that helps

btw is this card true hard ware based  as opposed to my onboard nvidia raid?

---

### Post by citrusfizz on 2007-01-01
bump!

---

### Post by citrusfizz on 2007-01-03
please help

---

### Post by b0b138 on 2008-02-06
bump... I have the same thing going on. promise fast track, raid 1. Linux sees 2 drives. Anyone? Bueller?  Bueller?

---

### Post by kcmozu on 2008-03-25
I have a similar raid card - Promise SATA150 SX4 setup in a RAID 10 config in Bios.  Running 7.10 and the card is recognized by the system, but the drives are disabled.  Ran 

Sudo dmesg | more 

and got this output

[   10.196000] sata_sx4 0000:00:09.0: version 0.11
[   10.196000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 4 (level, low) -> IRQ 4
[   13.304000] scsi0 : sata_sx4
[   13.304000] scsi1 : sata_sx4
[   13.304000] scsi2 : sata_sx4
[   13.304000] scsi3 : sata_sx4
[   13.304000] ata1: SATA max UDMA/133 cmd 0xd0a40200 ctl 0xd0a40238 bmdma 0x00000000 irq 4
[   13.304000] ata2: SATA max UDMA/133 cmd 0xd0a40280 ctl 0xd0a402b8 bmdma 0x00000000 irq 4
[   13.304000] ata3: SATA max UDMA/133 cmd 0xd0a40300 ctl 0xd0a40338 bmdma 0x00000000 irq 4
[   13.304000] ata4: SATA max UDMA/133 cmd 0xd0a40380 ctl 0xd0a403b8 bmdma 0x00000000 irq 4
[   13.468000] ata1.00: ATA-7: SAMSUNG SP1614C, SW100-34, max UDMA7
[   13.468000] ata1.00: 312581808 sectors, multi 0: LBA48 
[   43.468000] ata1.00: qc timeout (cmd 0xef)
[   43.468000] ata1.00: failed to set xfermode (err_mask=0x4)
[   43.632000] ata1.00: ATA-7: SAMSUNG SP1614C, SW100-34, max UDMA7
[   43.632000] ata1.00: 312581808 sectors, multi 0: LBA48 
[   73.632000] ata1.00: qc timeout (cmd 0xef)
[   73.632000] ata1.00: failed to set xfermode (err_mask=0x4)
[   73.632000] ata1.00: limiting speed to UDMA/133:PIO3
[   73.796000] ata1.00: ATA-7: SAMSUNG SP1614C, SW100-34, max UDMA7
[   73.796000] ata1.00: 312581808 sectors, multi 0: LBA48 
[  103.796000] ata1.00: qc timeout (cmd 0xef)
[  103.796000] ata1.00: failed to set xfermode (err_mask=0x4)
[  103.796000] ata1.00: disabled
[  104.116000] ata2.00: ATA-7: SAMSUNG SP1614C, SW100-34, max UDMA7
[  104.116000] ata2.00: 312581808 sectors, multi 0: LBA48 
[  134.116000] ata2.00: qc timeout (cmd 0xef)
[  134.116000] ata2.00: failed to set xfermode (err_mask=0x4)
[  134.280000] ata2.00: ATA-7: SAMSUNG SP1614C, SW100-34, max UDMA7
[  134.280000] ata2.00: 312581808 sectors, multi 0: LBA48 
[  164.280000] ata2.00: qc timeout (cmd 0xef)
[  164.280000] ata2.00: failed to set xfermode (err_mask=0x4)
[  164.280000] ata2.00: limiting speed to UDMA/133:PIO3
[  164.444000] ata2.00: ATA-7: SAMSUNG SP1614C, SW100-34, max UDMA7
[  164.444000] ata2.00: 312581808 sectors, multi 0: LBA48 

Is this controller supported on 7.10 in a raid10 config?  Looks like it is seeing the disks and the controller but appears to be disabling due to xfermode error.  Each of these drives are similar make/model/size (160 GB SATA).  Any help greatly appreciated.

---

