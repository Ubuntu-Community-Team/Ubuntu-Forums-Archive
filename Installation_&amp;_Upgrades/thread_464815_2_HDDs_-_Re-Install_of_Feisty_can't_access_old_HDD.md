---
title: "2 HDDs - Re-Install of Feisty can't access old HDD (ata2 errors)"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by Sencer on 2007-06-05
I have a PC with the following IDE HDDs:
 1x Samsung 80GB (SAMSUNG SV0813H)
 1x Seagate 250GB (ST3250623A)

**Background**: The 80G was used for the past years and made several ubuntu-upgradesup to feisty with no problems. Since it had gotten old and slow, I decided to reinstall the system to the new 250G and make use of LVM etc. And copy over the data, and use the 80G for backups etc.

**Current State:** I can boot from either disk by switching the boot-device in the BIOS. Both disks work ok when booted from. One thing I noticed and which apparently has to do with the new kernel is that the disks are recognized as hda and hdc on the old Feisty (upgrade) on the 80G. However when I boot into 250G, the two disks are recognized as sda and sdb. Apparently has to do with moving the IDE drivers to libata system etc. 
**Problem:** This is probably connected to my problem. Because when I boot into the new Feisty on the 250G, I can use fdsik -l to see the partition-table on the 80G, but I cannot see or access the partitions (for mounting, fsck etc.). syslog shows the following errors for the 80G:

```

Jun  5 01:53:50 xpc1-7 kernel: [   31.355322] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   31.363280] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   31.363286] ata2.00: configured for UDMA/100
Jun  5 01:53:50 xpc1-7 kernel: [   31.363318] ata2: EH complete
Jun  5 01:53:50 xpc1-7 kernel: [   31.370758] ata2.00: limiting speed to UDMA/66:PIO4
Jun  5 01:53:50 xpc1-7 kernel: [   31.370766] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Jun  5 01:53:50 xpc1-7 kernel: [   31.370769] ata2.00: (BMDMA stat 0x24)
Jun  5 01:53:50 xpc1-7 kernel: [   31.370777] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 dat
a 4096 in
Jun  5 01:53:50 xpc1-7 kernel: [   31.370779]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA b
us error)
Jun  5 01:53:50 xpc1-7 kernel: [   31.370807] ata2: soft resetting port
Jun  5 01:53:50 xpc1-7 kernel: [   31.531039] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   31.539078] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   31.539091] ata2.00: configured for UDMA/66
Jun  5 01:53:50 xpc1-7 kernel: [   31.539123] ata2: EH complete
Jun  5 01:53:50 xpc1-7 kernel: [   31.548192] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Jun  5 01:53:50 xpc1-7 kernel: [   31.548199] ata2.00: (BMDMA stat 0x24)
Jun  5 01:53:50 xpc1-7 kernel: [   31.548209] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 dat
a 4096 in
Jun  5 01:53:50 xpc1-7 kernel: [   31.548211]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA b
us error)
Jun  5 01:53:50 xpc1-7 kernel: [   31.548241] ata2: soft resetting port
Jun  5 01:53:50 xpc1-7 kernel: [   31.710815] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   31.718820] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   31.718832] ata2.00: configured for UDMA/66
Jun  5 01:53:50 xpc1-7 kernel: [   31.718865] ata2: EH complete
Jun  5 01:53:50 xpc1-7 kernel: [   31.725608] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Jun  5 01:53:50 xpc1-7 kernel: [   31.725613] ata2.00: (BMDMA stat 0x24)
Jun  5 01:53:50 xpc1-7 kernel: [   31.725622] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 dat
a 4096 in
Jun  5 01:53:50 xpc1-7 kernel: [   31.725624]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA b
us error)
Jun  5 01:53:50 xpc1-7 kernel: [   31.725655] ata2: soft resetting port
Jun  5 01:53:50 xpc1-7 kernel: [   31.886470] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   31.894440] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   31.894446] ata2.00: configured for UDMA/66
Jun  5 01:53:50 xpc1-7 kernel: [   31.894477] sd 1:0:0:0: SCSI error: return code = 0x08000002
Jun  5 01:53:50 xpc1-7 kernel: [   31.894482] sdb: Current [descriptor]: sense key: Aborted Command
Jun  5 01:53:50 xpc1-7 kernel: [   31.894488]     Additional sense: Scsi parity error
Jun  5 01:53:50 xpc1-7 kernel: [   31.894499] Descriptor sense data with sense descriptors (in hex):
Jun  5 01:53:50 xpc1-7 kernel: [   31.894503]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun  5 01:53:50 xpc1-7 kernel: [   31.894519]         00 00 00 07 
Jun  5 01:53:50 xpc1-7 kernel: [   31.894526] end_request: I/O error, dev sdb, sector 0
Jun  5 01:53:50 xpc1-7 kernel: [   31.894533] Buffer I/O error on device sdb, logical block 0
Jun  5 01:53:50 xpc1-7 kernel: [   31.894571] ata2: EH complete
Jun  5 01:53:50 xpc1-7 kernel: [   31.903039] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Jun  5 01:53:50 xpc1-7 kernel: [   31.903047] ata2.00: (BMDMA stat 0x24)
Jun  5 01:53:50 xpc1-7 kernel: [   31.903055] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 dat
a 4096 in
Jun  5 01:53:50 xpc1-7 kernel: [   31.903057]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA b
us error)
Jun  5 01:53:50 xpc1-7 kernel: [   31.903085] ata2: soft resetting port
Jun  5 01:53:50 xpc1-7 kernel: [   32.066212] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   32.074176] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   32.074186] ata2.00: configured for UDMA/66
Jun  5 01:53:50 xpc1-7 kernel: [   32.074219] ata2: EH complete
Jun  5 01:53:50 xpc1-7 kernel: [   32.080491] ata2.00: limiting speed to UDMA/33:PIO4
Jun  5 01:53:50 xpc1-7 kernel: [   32.080504] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Jun  5 01:53:50 xpc1-7 kernel: [   32.080507] ata2.00: (BMDMA stat 0x24)
Jun  5 01:53:50 xpc1-7 kernel: [   32.080515] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 dat
a 4096 in
Jun  5 01:53:50 xpc1-7 kernel: [   32.080518]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA b
us error)
Jun  5 01:53:50 xpc1-7 kernel: [   32.080548] ata2: soft resetting port
Jun  5 01:53:50 xpc1-7 kernel: [   32.241909] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   32.249873] ata2.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 1563
68016
Jun  5 01:53:50 xpc1-7 kernel: [   32.249879] ata2.00: configured for UDMA/33
Jun  5 01:53:50 xpc1-7 kernel: [   32.249908] ata2: EH complete
Jun  5 01:53:50 xpc1-7 kernel: [   32.257763] SCSI device sdb: 156368016 512-byte hdwr sectors (80060 MB)
Jun  5 01:53:50 xpc1-7 kernel: [   32.257844] ldm_validate_partition_table(): Disk read failed.
Jun  5 01:53:50 xpc1-7 kernel: [   32.257858] Dev sdb: unable to read RDB block 0
Jun  5 01:53:50 xpc1-7 kernel: [   32.261679] sdb: Write Protect is off
Jun  5 01:53:50 xpc1-7 kernel: [   32.261690] sdb: Mode Sense: 00 3a 00 00
Jun  5 01:53:50 xpc1-7 kernel: [   32.262022]  unknown partition table
Jun  5 01:53:50 xpc1-7 kernel: [   32.262570] sd 1:0:0:0: Attached scsi disk sdb
Jun  5 01:53:50 xpc1-7 kernel: [   32.265645] SCSI device sdb: write cache: enabled, read cache: enabled, doesn'
t support DPO or FUA
Jun  5 01:53:50 xpc1-7 kernel: [   32.273643] SCSI device sdb: 156368016 512-byte hdwr sectors (80060 MB)
Jun  5 01:53:50 xpc1-7 kernel: [   32.275137] sdb: Write Protect is off
Jun  5 01:53:50 xpc1-7 kernel: [   32.275149] sdb: Mode Sense: 00 3a 00 00
Jun  5 01:53:50 xpc1-7 kernel: [   32.275234] SCSI device sdb: write cache: enabled, read cache: enabled, doesn'
t support DPO or FUA
Jun  5 01:53:50 xpc1-7 kernel: [   32.286729] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun  5 01:53:50 xpc1-7 kernel: [   32.287228] sd 1:0:0:0: Attached scsi generic sg1 type 0

```

Given that I can boot from the 80G it is not a problem with cabling or hardware. I am assuming it is a driver problem. Can somebody tell me what exactly is happening and how I can fix it?

Thanks.

---

