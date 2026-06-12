---
title: "CD/DVD drive DMA getting disabled"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by RichJacot on 2006-07-06
Hello All,

I'm having a problem with my DVD drive dropping its DMA setting.  Upon a reboot DMA is enabled and after using the drive for a bit, i.e. burning several disks, the DMA gets disabled.

**from messages file:**

Jul  6 06:33:14 defiant kernel: [17227369.476000] hda: irq timeout: status=0xd0 { Busy }
Jul  6 06:33:14 defiant kernel: [17227369.476000] ide: failed opcode was: unknown
Jul  6 06:33:14 defiant kernel: [17227369.476000] hda: DMA disabled
Jul  6 06:33:15 defiant kernel: [17227370.052000] hda: ATAPI reset complete

Needless to say once DMA is disabled K3B burns slower than heck!

I have a fresh install of Ubuntu 6.06.  
The DVD drive is hda: PIONEER DVD-RW DVR-110D, ATAPI CD/DVD-ROM drive. (yes, it has an 80 conductor cable)

**Output from hdparam:(after DMA disabled)**

/dev/hda:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

**Output from hdparm -i :**

/dev/hda:

 Model=PIONEER DVD-RW DVR-110D, FwRev=1.11, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode


**sudo dmesg | grep hda**
[17179577.036000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179577.772000] hda: PIONEER DVD-RW DVR-110D, ATAPI CD/DVD-ROM drive
[17179579.032000] hda: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[17227369.476000] hda: irq timeout: status=0xd0 { Busy }
[17227369.476000] hda: DMA disabled
[17227370.052000] hda: ATAPI reset complete


**sudo dmesg | grep -i dma**
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179575.272000] ata1: SATA max UDMA/133 cmd 0xF8860200 ctl 0xF8860238 bmdma 0x0 irq 169
[17179575.276000] ata2: SATA max UDMA/133 cmd 0xF8860280 ctl 0xF88602B8 bmdma 0x0 irq 169
[17179575.276000] ata3: PATA max UDMA/133 cmd 0xF8860300 ctl 0xF8860338 bmdma 0x0 irq 169
[17179577.036000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179577.036000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[17179579.032000] hda: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[17179579.044000] hdd: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[17179579.152000] ata4: PATA max UDMA/133 cmd 0xE400 ctl 0xE502 bmdma 0xE800 irq 177
[17179579.152000] ata5: PATA max UDMA/133 cmd 0xE600 ctl 0xE702 bmdma 0xE808 irq 177
[17179579.316000] ata4: dev 0 ATA-6, max UDMA/133, 72303840 sectors: LBA48
[17179579.320000] ata4: dev 0 configured for UDMA/100
[17179579.488000] ata5: dev 0 ATA-6, max UDMA/133, 145226112 sectors: LBA48
[17179579.492000] ata5: dev 0 configured for UDMA/100
[17179592.140000] eth0: dma_rwctrl[763f0000]
[17179629.924000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[17227369.476000] hda: DMA disabled


I also see in the messages file: 
Jul  6 06:26:20 defiant kernel: [17226955.956000] cdrom: This disc doesn't have any tracks I recognize!
I've determined that this happens when I insert a black DVD prior to burning and I get a popup about inserting a blank disk.  It appears to be normal.


Please let me know need any further information.   I can reboot and provide any of the above after a reboot also.

Thank you,
Rich

---

### Post by dashnak on 2006-07-07
This happens to me as well, funny, since I've even edited hdparm.conf and all.

---

### Post by RichJacot on 2006-07-10
So are you just keeping your eye on it and changing it back to on via the command line when you notice it changes itself to off?  

Apparently others aren't having this issue.  I'll keep researching....

---

### Post by wargames on 2006-07-21
I'm having the same problem as well. When I first boot-up, Dapper reports DMA being on for my dvdrw drive, but as soon as I insert a disc and play it, DMA gets turned off, no matter what I put in my hdparm.conf file. What's weird is that if I use the hdparm command about five times in a row it will eventually turn dma on and leave it on just for that disc, and if I eject the disc and reinsert it, dma gets turned off again. DMA for my hard drive works just fine. I wish I could fix this. :(

---

