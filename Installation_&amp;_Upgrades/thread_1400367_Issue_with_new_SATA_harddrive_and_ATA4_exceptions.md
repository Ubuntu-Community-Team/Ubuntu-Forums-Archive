---
title: "Issue with new SATA harddrive and ATA4 exceptions"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by vinooj on 2010-02-06
Having problem with a newly replaced Seagate SATA drive. 

I did read a few forum post around similar issue, but none of them seems to explain clearly the problem and a solution.

[COLOR="DarkSlateGray"]Based on the system log posted below, I'm not sure whether this is a benign issue or is this something that I should worry about. If is not an issue, is there a way to configure the kernel to use the last working configuration.[/COLOR]


[1.220024] ata1: SATA link down (SStatus 0 SControl 300)
[    1.481018] usb 2-9: new low speed USB device using ohci_hcd and address 2
[    1.689025] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.693099] usb 2-9: configuration #1 chosen from 1 choice
[    1.728104] ata2.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.728110] ata2.00: ATA-8: ST3500418AS, CC38, max UDMA/133
[    1.728113] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.744304] ata2.00: configured for UDMA/133
[    1.744414] scsi 1:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
[    1.744524] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.744653] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.744699] sd 1:0:0:0: [sda] Write Protect is off
[    1.744702] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.744726] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.744854]  sda: sda1 sda2 < sda5 >
[    1.792666] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.908296] ata4.00: ATAPI: _NEC DVD_RW ND-3540A, 1.01, max UDMA/33
[    1.908318] ata4: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:600:0x13)
[    1.924244] ata4.00: configured for UDMA/33
[   22.804025] ata4: lost interrupt (Status 0x58)
[   22.808012] ata4: drained 32768 bytes to clear DRQ.
[   22.838605] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   22.838616] ata4.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   22.838618]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   22.838619]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   22.838622] ata4.00: status: { DRDY }
[   22.838636] ata4: soft resetting link
[   23.000314] ata4: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:600:0x13)
[   23.016243] ata4.00: configured for UDMA/33
[   23.016465] ata4: EH complete
[   43.804024] ata4: lost interrupt (Status 0x58)
[   43.808012] ata4: drained 32768 bytes to clear DRQ.
[   43.838600] ata4.00: limiting speed to UDMA/25:PIO4
[   43.838604] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   43.838613] ata4.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   43.838615]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   43.838616]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   43.838619] ata4.00: status: { DRDY }
[   43.838632] ata4: soft resetting link
[   44.000312] ata4: nv_mode_filter: 0x339f&0x739f->0x339f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:600:0x13)
[   44.016296] ata4.00: configured for UDMA/25
[   44.016627] ata4: EH complete
[   64.804023] ata4: lost interrupt (Status 0x58)
[   64.808012] ata4: drained 32768 bytes to clear DRQ.
[   64.838598] ata4.00: limiting speed to PIO4
[   64.838601] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   64.838611] ata4.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   64.838612]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   64.838614]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   64.838617] ata4.00: status: { DRDY }
[   64.838629] ata4: soft resetting link
[   65.000312] ata4: nv_mode_filter: 0x1f&0x739f->0x1f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:600:0x13)
[COLOR="RoyalBlue"][   65.016244] ata4.00: configured for PIO4
[   65.016480] ata4: EH complete[/COLOR]
[   65.016976] scsi 3:0:0:0: CD-ROM            _NEC     DVD_RW ND-3540A  1.01 PQ: 0 ANSI: 5
[   65.019898] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray


Here are some useful information,

sudo hdparm -I /dev/sda

/dev/sda:
ATA device, with non-removable media
	Model Number:       ST3500418AS                             
	Serial Number:      9VM84GEX
	Firmware Revision:  CC38    
	Transport:          Serial
Capabilities:
        ..
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 254, current value: 0
	[COLOR="RoyalBlue"]DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6[/COLOR] 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
..


cat /proc/scsi/scsi

Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3500418AS      Rev: CC38
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: _NEC     Model: DVD_RW ND-3540A  Rev: 1.01
  Type:   CD-ROM                           ANSI  SCSI revision: 05

Tried to set the DMA using the following command,
sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

---

### Post by vinooj on 2010-02-10
It was a wild goose chase..

What I figured out is that the above error is a very generic error and occurs mostly because to hardware ( bad drives, bad cables, not enough power..)

Problem was with my old CR-ROM drive connected to my IDE port. 
[65.016976] scsi 3:0:0:0: CD-ROM _NEC DVD_RW..

So I replaced it with a new $25 Sony SATA OEM drive and it resolved my issue.

---

