---
title: "sdb (second drive): bad geometry after upgrade to 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by gcmelzi on 2011-05-09
Hello team, 
I upgraded my 10.10 system to 11.04: the upgrade failed and I was unable to boot at all. Having my home on sdb, I tried a fresh install and it went nearly fine, but at the end I was unable to mount my sdb device and make it the /home again. 
See below what I got from dmesg: 
```
[    0.615918] ata_piix 0000:00:1f.1: version 2.13
[    0.616161] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.620690] scsi0 : ata_piix
[    0.621162] scsi1 : ata_piix
[    0.622357] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.622365] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15

[    0.817091] ata1.00: ATA-4: QUANTUM FIREBALLlct08 13, A05.0X00, max UDMA/66
[    0.817099] ata1.00: 25429824 sectors, multi 16: LBA 
[    0.817352] ata1.01: HPA detected: current 160084415, native 160086528
[    0.817365] ata1.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    0.817369] ata1.01: 160084415 sectors, multi 16: LBA 

[    1.044811] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL A05. PQ: 0 ANSI: 5
[    1.045433] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.045942] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    1.046455] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.046859] sd 0:0:0:0: [sda] 25429824 512-byte logical blocks: (13.0 GB/12.1 GiB)
[    1.047229] sd 0:0:0:0: [sda] Write Protect is off
[    1.047237] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.047389] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.092460]  sda: sda1 sda2 < sda5 >
[    1.093269] sd 0:0:1:0: [sdb] 160084415 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    1.093678] sd 0:0:1:0: [sdb] Write Protect is off
[    1.093687] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.093846] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.115970] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.116129]  sdb: unknown partition table
[    1.116996] sd 0:0:1:0: [sdb] Attached SCSI disk

[   31.649664] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0

[ 2080.081606] EXT4-fs (sdb): bad geometry: block count 20010816 exceeds size of device (20010551 blocks)
```

Any idea, please?
Thanks in advance.

---

### Post by binary00mind on 2011-05-09
Wow...
I would do this first. Go to live Ubuntu CD...install the testdisk and go from there. You may be able to restore the old partition table. 
If you have never used testdisk (must use terminal and command since testdisk have no GUI) read documentation carefully.

---

### Post by gcmelzi on 2011-05-09
Thanks binary00mind. I'll give it a try tonight.
Does testdisk work even if I boot from sda (standard boot)?

---

### Post by binary00mind on 2011-05-09
Testdisk works on any Hard Disk/Drive SD Cards Any Partition any label any File system format. I would suggest to go to advance and specify 
Cylinders, Heads ,Sectors and Sectors size. 
Options.Expert Mode...up to you...you know how much you know about partitioning and MBR's 
Anyhow the options are 
#1 Cylinder boundry 
#2 Allow partial last cylinder 
and you can dumped all the surface info, if you have time for it. 
Expert mode is not that crucial..
If there are errors with your home partition then it will tell you. and you will have the option to overwrite PT from CHS or EMBR 

It is really easy tool....before you do anything play around..make backups and create the log 

P.S. 
the command line for testdisk is: sudo /usr/sbin/testdisk

First thing you do is to Analyze and depending what you find you go from there.. 

Are you sure there was no hidden compartment? 

Have fun

---

### Post by gcmelzi on 2011-05-10
Dear binary00mind, thanks for your tips but I gave up: I tried with Ubuntu 10.10 installation disk and sdb was perfect. In addition WLAN was not working at all, so I suspect a number of drivers for my old iron are missing in this version. As I don't have much time and I need the desktop working I reinstalled 10.10: a couple of hours and everything is now fine. 

Thanks indeed. 
Will give a try to 11.10, but with some more testing before installing it. 

Giancarlo

---

