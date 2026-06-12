---
title: "Hard Disk not recognized by installed"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by cdaringe on 2011-08-24
Hi all:

I've done a big load of googling/forum scouring for this, with no success quite yet, so I'm posting up my unique occurrence.

Objective: allow ubuntu installer to see my /dev/sdax disk when partitioning & configuring grub.

Problem statement: ubuntu installer see's only my /dev/sdb disk in the installer when booting from liveusb or livecd

Troubleshooting:
[LIST]
[1]Well, you can't really call it trouble shooting if you don't truly understand what you are doing, but let's call it that
[2]Loaded ubuntu 32 live cd, found that only my sdb disk showed up in installer.  BOTH hard disks + bootable thumb drive are visible in gparted, and all in good standing.
[3]Attempted with the 64 bit version of 10.04 livecd, and w/ 32 alternate cd.  disabled sata raid & acpi=off in the alternate.  acpi=off also attempted in std 10.04 LTS livecds (all of these iso's are 10.04--newer versions of ubunutu seem to hate my gfx card, thus i am sticking with the goods!)
[4]Moved my previous ext4 partition around and also made it primary vs. extended.
[/LIST]

Any tips, recommendations?

```

cdaringe@cdaringe-desktop:~$ sudo hdparm -i /dev/sda
[sudo] password for cdaringe: 

/dev/sda:

 Model=Hitachi, FwRev=JP4OA3EA, SerialNo=JP2940HD01BH2C
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=56
 BuffType=DualPortCache, BuffSize=29999kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

cdaringe@cdaringe-desktop:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       Hitachi HDS721010CLA332                 
    Serial Number:      JP2940HD01BH2C
    Firmware Revision:  JP4OA3EA
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6; Revision: ATA8-AST T13 Project D1697 Revision 0b
Standards:
    Used: unknown (minor revision code 0x0029) 
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors: 1953525168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      953869 MBytes
    device size with M = 1000*1000:     1000204 MBytes (1000 GB)
    cache/buffer size  = 29999 KBytes (type=DualPortCache)
    Form Factor: 3.5 inch
    Nominal Media Rotation Rate: 7200
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: disabled
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    DOWNLOAD_MICROCODE
            Advanced Power Management feature set
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
            Media Card Pass-Through
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    URG for READ_STREAM[_DMA]_EXT
       *    URG for WRITE_STREAM[_DMA]_EXT
       *    WRITE_UNCORRECTABLE_EXT command
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    NCQ priority information
            Non-Zero buffer offsets in DMA Setup FIS
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
            In-order data delivery
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT LBA Segment Access (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
    not    supported: enhanced erase
    232min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000cca373c09f7d
    NAA        : 5
    IEEE OUI    : 000cca
    Unique ID    : 373c09f7d
Checksum: correct


```

---

