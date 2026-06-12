---
title: "Missing SCSI tape drive"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by frisket on 2010-08-23
I installed 10.4 on an old Dell being thrown out from the office and everything worked, including my old SCSI DAT tape drive and a SCSI disk, via SCSI card. I copied what I needed from tape, packed it all up and brought it home. 

Before restarting, I replaced the CD drive with a DVD drive from another machine, and that now works fine, and so does the SCSI disk...but I've lost the tape drive (no /dev/st0 any more).

dmesg|grep scsi says

[    0.465453] scsi0 : ata_piix
[    0.509133] scsi1 : ata_piix
[    0.509327] scsi2 : ata_piix
[    0.512073] scsi3 : ata_piix
[    0.553453] scsi_host host0: hash matches
[    0.553455] scsi host0: hash matches
[    1.068598] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        8.16 PQ: 0 ANSI: 5
[    1.068828] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.081065] scsi 0:0:1:0: Direct-Access     ATA      HDS722540VLAT20  V31O PQ: 0 ANSI: 5
[    1.081213] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.081697] scsi 1:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-616T  E310 PQ: 0 ANSI: 5
[    1.083407] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    1.083526] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.083586] sr 1:0:0:0: Attached scsi generic sg2 type 5

so the generic driver is recognising it, but there's no mention of it being mapped to /dev/st0 anywhere. 

cat /proc/scsi/scsi* says:

Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST340014A        Rev: 8.16
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: HDS722540VLAT20  Rev: V31O
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: SAMSUNG  Model: DVD-ROM SD-616T  Rev: E310
  Type:   CD-ROM                           ANSI  SCSI revision: 05

Before I take it all to pieces and start poking at it, is there something obvious I have missed that can be fixed in software?

---

