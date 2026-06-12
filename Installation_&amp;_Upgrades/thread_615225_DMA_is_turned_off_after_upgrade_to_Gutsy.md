---
title: "DMA is turned off after upgrade to Gutsy"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by tgcUbuntu on 2007-11-16
When I upgrade to Gutsy 7..10 I initially had problems when booting up and got dumped into BusyBox. I ended up finding a solution which involed inserting a new module into my /etc/initramfs-tools/modules file (ide_generic). I can now boot up into Gutsy but while booting I see the message "Warning: dma is turned off on hard drive". Once booted up I checked both my internal ide drive and my external usb drive and both hae DMA turned off.

I tried to turn on dma for one drive and got this message:

sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)

My /etc/initramfs-tools/modules file:
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
piix
ide-core
ide_generic

blacklist ata_piix


Any ideas what's going wrong here?

---

### Post by Pumalite on 2007-11-16
Post you specs. Raid?. BIOS?

---

### Post by tgcUbuntu on 2007-11-16
I am not using a Raid system.
The internal drive is a ide drive and I also have an external usb drive.

Here are the specs for the drives:

22: IDE 00.0: 10600 Disk                                        
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_serial_WD_WMAEH2026618
  Unique ID: Fffu.QhTYdMzeSy6
  Parent ID: 3p2J.mCg4nggHnv5
  SysFS ID: /block/hda
  SysFS BusID: 0.0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/ide0/0.0
  Hardware Class: disk
  Model: "WDC WD2000BB-00DWA0"
  Vendor: "WDC"
  Device: "WD2000BB-00DWA0"
  Revision: "15.05R15"
  Serial ID: "WD-WMAEH2026618"
  Driver: "PIIX_IDE", "ide-disk"
  Driver Modules: "piix", "ide_disk"
  Device File: /dev/hda
  Device Files: /dev/hda, /dev/disk/by-id/ata-WDC_WD2000BB-00DWA0_WD-WMAEH2026618, /dev/disk/by-path/pci-0000:00:1f.1-ide-0:0
  Device Number: block 3:0-3:63
  Size: 390721968 sectors a 512 bytes
  Geometry (Physical): CHS 387621/16/63
  Geometry (Logical): CHS 24321/255/63
  Cache: 2048 kb
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (IDE interface)

25: SCSI 00.0: 10600 Disk
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_serial_Maxtor_OneTouch_II_L507HCHG_0_0
  Unique ID: wn1q.EmGe3z+9Rp4
  Parent ID: 5YuN.Lu7rTSAG4N5
  SysFS ID: /block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.7/usb5/5-2/5-2:1.0/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "Maxtor OneTouch II"
  Vendor: usb 0x0d49 "Maxtor"
  Device: usb 0x7100 "OneTouch II"
  Revision: "023g"
  Serial ID: "L507HCHG"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sda (/dev/sg0)
  Device Files: /dev/sda, /dev/disk/by-id/usb-Maxtor_OneTouch_II_L507HCHG-0:0, /dev/disk/by-path/pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0
  Device Number: block 8:0-8:15 (char 21:0)
  Features: Hotpluggable
  Geometry (Logical): CHS 30515/255/63
  Size: 490234752 sectors a 512 bytes
  Speed: 480 Mbps
  Module Alias: "usb:v0D49p7100d0203dc00dsc00dp00ic08isc06ip50"
  Driver Info #0:
    Driver Status: libusual is active
    Driver Activation Cmd: "modprobe libusual"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (USB Controller)

Here's some BIOS info:
1: None 00.0: 10105 BIOS                                       
  [Created at bios.174]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Serial Port 0: 0x3f8
  Parallel Port 0: 0x378
  Base Memory: 639 kB
  PnP BIOS: @@@0000
  MP spec rev 1.4 info:
    OEM id: "ASUSTek"
    Product id: "Stringray"
    0 CPUs (0 disabled)
  BIOS32 Service Directory Entry: 0xf0010
  SMBIOS Version: 2.3
  BIOS Info: #0
    Vendor: "American Megatrends Inc."
    Version: "3.19"
    Date: "12/12/2003"
    Start Address: 0xf0000
    ROM Size: 512 kB
    Features: 0x0377000000017f8bde90
      ISA supported
      PCI supported
      PnP supported
      APM supported
      BIOS flashable
      BIOS shadowing allowed
      ESCD supported
      CD boot supported
      Selectable boot supported
      BIOS ROM socketed
      EDD spec supported
      1.2MB Floppy supported
      720kB Floppy supported
      2.88MB Floppy supported
      Print Screen supported
      8042 Keyboard Services supported
      Serial Services supported
      Printer Services supported
      CGA/Mono Video supported
      ACPI supported
      USB Legacy supported
      AGP supported
      LS-120 boot supported
      ATAPI ZIP boot supported
      IEEE1394 boot supported
      BIOS Boot Spec supported
      F12 Network boot supported
  System Info: #1
    Manufacturer: "HP Pavilion 061"
    Product: "D7222G-ABA M300Y"
    Version: "0qr1112RE101YALE 10"
    Serial: "MXP40203SX NA350"
    UUID: undefined, but settable
    Wake-up: 0x06 (Power Switch)
  Board Info: #2
    Manufacturer: "ASUSTeK Computer INC."
    Product: "'P4SD-LA'"
    Version: "Rev 1.xx"
    Serial: "X312345678"

---

### Post by tgcUbuntu on 2007-11-18
*bump*

Any ideas about this?

---

### Post by Pumalite on 2007-11-18
I'd save /home and data and do a clean install.

---

### Post by wanchai on 2007-12-02
tgcUbuntu, did you re-install and did it solve your problem?

I seem the have the same problem. After I upgraded my desk machine to Feisty it seemed to become sluggish, but I didn't investigate. Now the machine is running Gutsy and I found out that DMA is off and that I can't turn it on. Hard drives (IDE or PATA) are recognized as /dev/hdx (my laptop has its PATA drive as /dev/sda and it's running very well). When I boot the machine in Debian Etch, DMA is on and disk throughput is good.

I googled around and searched the Forums, found lots of similar problems, but no solution. Is there really none except ditching Gutsy for Edgy or Etch? I think this degradation of disk performance is quite serious.

When running Ubuntu 7.10 I have this:

> {root@queens}[/root]uname -a
Linux queens 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

{root@queens}[/root]hdparm -abcdmtT /dev/hda

/dev/hda:
 multcount     =  0 (off)
 IO_support    =  0 (default 16-bit)
 using_dma     =  0 (off)
 readahead     = 256 (on)
 busstate      =  1 (on)
 Timing cached reads:   436 MB in  2.01 seconds = 217.32 MB/sec
 Timing buffered disk reads:    8 MB in  3.09 seconds =   2.59 MB/sec

{root@queens}[/root]hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)

{root@queens}[/root]hdparm -i /dev/hda

/dev/hda:

 Model=WDC WD1600JB-00REA0, FwRev=20.00K20, SerialNo=WD-WCANMD843628
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode



Under Debian Etch, the same disk looks like this:

> queens:/home/dirk# uname -a
Linux queens 2.6.18-4-686 #1 SMP Mon Mar 26 17:17:36 UTC 2007 i686 GNU/Linux

queens:/home/dirk# hdparm -abcdmtT /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 using_dma    =  1 (on)
 readahead    = 256 (on)
 busstate     =  1 (on)
 Timing cached reads:   452 MB in  2.00 seconds = 225.92 MB/sec
 Timing buffered disk reads:  174 MB in  3.03 seconds =  57.46 MB/sec

queens:/home/dirk# hdparm -i /dev/hda

/dev/hda:

 Model=WDC WD1600JB-00REA0, FwRev=20.00K20, SerialNo=WD-WCANMD843628
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode


---

### Post by Pumalite on 2007-12-02
Maybe in upgrades but not in clean installs. Mine is fine.

---

### Post by wanchai on 2007-12-02
Ok, I did a clean install in an empty partition that I still had. Now the disks are recognized as /dev/sd? and the speed is good.

---

