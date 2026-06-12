---
title: "Problem Installing Ubuntu on SATA Computer"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by Gago on 2005-08-10
Hi, I'm new in linux world. I install Ubuntu on my work desktop and everything goes perfect.
The problem begins when I boght my home computer wich is a P4, mother board Intel D915GEV, WD 80Gb SATA HD and MSI XA52P CD-W DVD-R Combo SATA also, I boot with the install cd of Ubuntu and press enter to begin the installation, after a few seconds the sistem hang. The last words on the screen are:


ata2: dev0 configurated for UDMA/100 
ata2: dev1 configurated for UDMA/100
scsi1: ata_piix
elevator: using anticipatory as default io scheduler
Vendor: ATA                           Model: WDC.....                         Rev:0.5
Type: direct-access                                Ansi scsi rev:05
Vendor: ATAPI                         Model: COMBO52XMAX                      Rev:1.10
Type: CDROM                                        Ansi scsi rev:05
ata2: dev1:ATAPI check failed
ata2: PIO error, drv_stat 0x58
ATA: abnormal status 0x58 on port 0xE007
         ata_piix loaded successfully
             [success]
scsi device sda: 156250000 512-byte hdwr sectors (80000 MB)
scsi device sda: drive cache: write back
scsi device sda: 156250000 512-byte hdwr sectors (80000 MB)
scsi device sda: drive cache: write back
/dev/scsi/host1/bus0/target 0/lun0:<4> ATA:abnormal status 0x58 on port 0xE007 p1
Attached scsi disk sda at scsi1, chanel0, id0,lun0
         sd_mod: loaded successfully
ATA: abnormal status 0x58 on port 0xE007
ata2: command 0xa0 timeout, stat 0x58 host_stat 0x0


I up to date the BIOS and play around with the BIOS configuration and get the same results, tried also with the live cd of Ubuntu, Knoppix and Kubuntu getting the same.
By my short knowledge presume is an CD Reader problem so I install a PATA (IDE) cd Reader to install Ubunto but nothing different happens.

Any help will be appreciated.

---

