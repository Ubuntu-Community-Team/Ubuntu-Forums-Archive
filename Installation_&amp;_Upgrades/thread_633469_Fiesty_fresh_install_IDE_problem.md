---
title: "Fiesty fresh install: IDE problem??"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by jdt141 on 2007-12-06
So I've been trying to do a fresh install of Fiesty Destkop for a couple of days now, and I can't get the installer to recognize the drives. I believe its an IDE problem. I can only get the installer to go to X when I have the following settings

BIOS:
ATA/IDE Config: Enhanced (Disabled, Compat.)
 Configure SATA as IDE (RAID, AHCI)
 Config. SATA Channels: BEFORE PATA (Behind PATA)

At the "grub" point I use the all_generic_ide flag.

In X, I cannot mount either hard drive. I *think* I need to force the ata_piix drivers instead of the generic ones. But I'm not sure this will remedy the problem.

here's my lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
02:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
```


here's my lsmod | grep ata
```

ata_piix               15492  0
ata_generic             9092  2
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 sr_mod,usb_storage,sg,sd_mod,libata

```


```

/dev/sda:

 Model=CF8GHS                                  , FwRev=20070504, SerialNo=00000000000100000075
 Config={ HardSect NotMFM Fixed DTR>10Mbs }
 RawCHS=15506/16/63, TrkSize=0, SectSize=576, ECCbytes=4
 BuffType=DualPort, BuffSize=1kB, MaxMultSect=1, MultSect=?0?
 CurCHS=15506/16/63, CurSects=15630048, LBA=yes, LBAsects=15630048
 IORDY=no, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4
 AdvancedPM=yes: disabled (255)
 Drive conforms to: Unspecified:  ATA/ATAPI-4

 * signifies the current active mode

/dev/sdb:

 Model=ST98823AS                               , FwRev=3.06    , SerialNo=            5PK3HWWS
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode


```

Your thoughts would be most greatly appreciated. Thanks!

---

### Post by jdt141 on 2007-12-07
bump. please?

---

### Post by jdt141 on 2007-12-07
My resolution to this topic was to go back and install Dapper 6.06.1-386. (kernel 2.6.15-26)  Not quite there yet, but X starts up and I can run synaptic.  I attempted to pull down upgrades and it upgraded my kernel to 2.6.15-29-386, and that results in kernel panic. Now I just remembered that I need the 686 package to get SMP to work on my Intel Core Duo T2500.... Upgrading to the default (2.6.15-29-686) also results in kernel panic. I removed 29-686, and attempted to force 2.6.15-22-686 (search for linux-686-smp in synaptic and force 22 from the Package menu). It still wants to boot 29-686.... more kernel panic. I'm about to throw this thing on to the highway. :-(

---

### Post by jdt141 on 2007-12-17
While that version of the kernel seemed to work well, it had major stability problems on my machine. I finally found the source of the problem. The Motherboard supported both a SATA drive and a Compact Flash (CF) as the bootable device. Once I removed the CF card and installed to the SATA drive, things started to move quickly. I haven't got X up (yet) but I can get to a bash shell, and that, really, is all I need for this application. Does anyone know why the CF card would be giving me so much trouble?

---

