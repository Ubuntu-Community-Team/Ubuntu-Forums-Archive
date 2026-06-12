---
title: "Help please 9.10 won't detect all hard drives"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cogvos on 2009-10-17
Dear all,

I have upgraded to 9.04 and have a test 7.10 partition on the same box. I have a number internal and external drives as I do a lot of video and sound work. Problem is that 9.10 is not detecting all the drives. 7.10 does, but I want to junk this. 

If I go to the file system and select one of the drives Ubumtu has not mounted nothing happens, zilch. Yet windowz and 7.10 can see this drive without any problems. 

Help? I'm totally baffled!

J.

---

### Post by Merk42 on 2009-10-17
Given this is about 9.10 which is unreleased, you may be better off posting in the Karmic forum
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)
Or a mod move this thread there, either way.

---

### Post by Seventh Reign on 2009-10-17
It helps if you give a little more info.  Like Which drives are showing and which ones arent. Internal IDE, Internal SATA, External USB/Firewire, E-SATA 

For example on the PC I am using right now, I have 2 internal SATA Drives.  I have to add "pci=nomsi" to the boot-line or they arent detected.  Prior to Ubuntu 8.04, I never needed to add the line.

---

### Post by cogvos on 2009-10-17
OOPS!

Sorry I'm using 9.04 not 9.10 a typo on my part. The drive that is not being detected is an internal SATA - but the one that Linux is on is also an internal SATA. What does the dwitch do? I have a PCI express graphics card and a quick search suggests that this may stop working with the switch on.

Below is, I think, the relevant output of dmsg. I don't understand it, but as far as I can tell nothing is marked as failed. Below that is a list from /sbin/fdisk

    1.534396] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.535228] brd: module loaded
[    1.535510] loop: module loaded
[    1.535570] Fixed MDIO Bus: probed
[    1.535576] PPP generic driver version 2.4.2
[    1.535628] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.535650] Driver 'sd' needs updating - please use bus_type methods
[    1.535658] Driver 'sr' needs updating - please use bus_type methods
[    1.535749] sata_sil 0000:00:12.0: version 2.3
[    1.535796] sata_sil 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.535912] scsi0 : sata_sil
[    1.536028] scsi1 : sata_sil
[    1.536114] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 22
[    1.536117] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 22
[    1.856058] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.864615] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[    1.864617] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.872622] ata1.00: configured for UDMA/100
[    2.192057] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.200598] ata2.00: ATA-7: SAMSUNG SP0812C, SU100-34, max UDMA7
[    2.200600] ata2.00: 156368016 sectors, multi 16: LBA48 
[    2.208614] ata2.00: configured for UDMA/100
[    2.208723] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    2.208801] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.208815] sd 0:0:0:0: [sda] Write Protect is off
[    2.208817] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.208837] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.208890] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.208901] sd 0:0:0:0: [sda] Write Protect is off
[    2.208904] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.208922] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.208926]  sda: sda1 < sda5 sda6 sda7 sda8 sda9 >
[    2.258113] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.258156] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.258222] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SP0812C  SU10 PQ: 0 ANSI: 5
[    2.258293] sd 1:0:0:0: [sdb] 156368016 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.258305] sd 1:0:0:0: [sdb] Write Protect is off
[    2.258307] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.258325] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.258364] sd 1:0:0:0: [sdb] 156368016 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.258376] sd 1:0:0:0: [sdb] Write Protect is off
[    2.258378] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.258396] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.258399]  sdb: sdb1 < sdb5 sdb6 sdb7 sdb8 >
[    2.311025] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.311054] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.311206] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.311324] scsi2 : pata_atiixp
[    2.311375] scsi3 : pata_atiixp
[    2.312363] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf800 irq 14
[    2.312366] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf808 irq 15
[    2.476571] ata3.00: ATA-6: ST3160021A, 8.11, max UDMA/100
[    2.476574] ata3.00: 312581808 sectors, multi 16: LBA48 
[    2.492523] ata3.00: configured for UDMA/100
[    2.656540] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-H552B, HP08, max UDMA/33
[    2.672526] ata4.00: configured for UDMA/33
[    2.672831] scsi 2:0:0:0: Direct-Access     ATA      ST3160021A       8.11 PQ: 0 ANSI: 5
[    2.672899] sd 2:0:0:0: [sdc] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.672911] sd 2:0:0:0: [sdc] Write Protect is off
[    2.672914] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.672933] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.672985] sd 2:0:0:0: [sdc] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.672996] sd 2:0:0:0: [sdc] Write Protect is off
[    2.672998] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.673016] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.673020]  sdc: sdc1 sdc2
[    2.676560] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.676603] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.677156] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552B HP08 PQ: 0 ANSI: 5
[    2.678807] sr0: scsi3-mmc drive: 125x/125x writer cd/rw xa/form2 cdda tray
[    2.678810] Uniform CD-ROM driver Revision: 3.20
[    2.678895] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.678925] sr 3:0:0:0: Attached scsi generic sg3 type 5

/sbin/fdisk -l output
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4485e66d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sda5               2        5101    40965718+   7  HPFS/NTFS
/dev/sda6            5102        5709     4883728+  82  Linux swap / Solaris
/dev/sda7            5710        7168    11719386   83  Linux
/dev/sda8            7169       10933    30242331   83  Linux
/dev/sda9           10934       60801   400564678+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x021fe081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9733    78172290    f  W95 Ext'd (LBA)
/dev/sdb5               2        4868    39094146    7  HPFS/NTFS
/dev/sdb6   *        4869        8499    29165976   83  Linux
/dev/sdb7            8500        8761     2104483+  82  Linux swap / Solaris
/dev/sdb8            8762        9733     7807558+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sdc2   *         833       20672   149990400    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0185bece

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x696d3e52

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               2     1938021   976762080    f  W95 Ext'd (LBA)
/dev/sde5               2     1938021   976762048+   7  HPFS/NTFS

Disk /dev/sdj: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f4d7faf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               2       36483   293041665    f  W95 Ext'd (LBA)
/dev/sdj5               2       18242   146520801    b  W95 FAT32
/dev/sdj6           18243       36483   146520801    b  W95 FAT32


J.

---

### Post by cogvos on 2009-10-17
Note to Mods

Please move this back to the beguinners forum. It does *not* relate to Karmic Koala - I got the version wrong in my initial post!

Thanks

---

