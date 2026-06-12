---
title: "No DMA for DVD in Intrepid"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MMMan on 2008-10-05
I just upgraded my Hardy Kubuntu installation to the Intrepid beta and DMA no longer works for my DVD drive, making reading and writing of DVDs both CPU intensive and very slow.

motherboard: ASUS A8R-MX-Vintage
CPU: AMD Athlon(tm) 64 Processor 3200+
RAM: 2GB
IDE controller: ALi M5229
DVD drive: BENQ DW1650
SATA controller: ULi 5287 RAID
HDD: ST3300831AS

(The SATA drive works fine.)

```
hdparm -i /dev/scd0

/dev/scd0:

 Model=BENQ    DVD DD DW1650                   , FwRev=BCDC    , SerialNo=KWG2611445SC0
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,6

 * signifies the current active mode

```


```
sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```


```
dmesg | grep ata
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                    
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data                   
[    0.004000] Memory: 2062788k/2096832k available (2660k kernel code, 32660k reserved, 1180k data, 428k init, 1179328k highmem)                                
[    0.004000]       .data : 0xc0399388 - 0xc04c0640   (1180 kB)                
[    2.289907] Write protecting the kernel read-only data: 952k                 
[    4.429741] libata version 3.00 loaded.                                      
[    5.144357] pata_acpi 0000:00:1f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.144429] pata_acpi 0000:00:1f.0: PCI INT A disabled
[    5.203411] sata_uli 0000:00:1f.1: version 1.3
[    5.203421] sata_uli 0000:00:1f.1: enabling device (0105 -> 0107)
[    5.203426] sata_uli 0000:00:1f.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.203604] scsi0 : sata_uli
[    5.212185] scsi1 : sata_uli
[    5.221384] scsi2 : sata_uli
[    5.221499] scsi3 : sata_uli
[    5.221540] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 21
[    5.221545] ata2: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 21
[    5.221549] ata3: SATA max UDMA/133 cmd 0xec08 ctl 0xe886 bmdma 0xe410 cmd 0xe809 ctl 0xe486 bmdma 0xe418 irq 21
[    5.221553] ata4: SATA max UDMA/133 irq 21
[    5.688073] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.696454] ata1.00: ATA-7: ST3300831AS, 3.06, max UDMA/133
[    5.696457] ata1.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.712467] ata1.00: configured for UDMA/133
[    6.651575] pata_ali 0000:00:1f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    6.652302] scsi4 : pata_ali
[    6.652829] scsi5 : pata_ali
[    6.654312] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    6.654315] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    6.872685] ata5.00: ATA-6: ST3200822A, 3.01, max UDMA/100
[    6.872689] ata5.00: 390721968 sectors, multi 16: LBA48
[    6.888595] ata5.00: configured for UDMA/100
[    7.052695] ata6.01: ATAPI: BENQ    DVD DD DW1650, BCDC, max UDMA/33
[    7.052706] ata6.01: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    7.052709] ata6.01: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    7.052713] ata6.01: simplex DMA is claimed by other device, disabling DMA
[    7.068673] ata6.01: configured for PIO4
[    7.335212] EXT3-fs: mounted filesystem with ordered data mode.
```

I found a recommendation [_here_]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=749776") to add the following to /etc/modprobe.d/aliases but it didn't help. ```
alias ata_generic off
alias pata_atiixp on
```

I also found a bug [_here_]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636") that seems to indicate that there has been a similar problem since Feisty, but I did not see the problem until I upgraded from Hardy to Intrepid.  That thread also recommends the following as possible workarounds:

* Recommended (where BIOS permits): Change BIOS IDE mode from "legacy" or "combined" mode to "AHCI" (recommended), "RAID" or "native".
    * Boot with the kernel commandline parameter "combined_mode=libata" or "combined_mode=ide" to allow the specified driver to claim all IDE ports.

I have tried these with no success.

Has anyone else run into this problem?  Does anyone have any suggestions how to fix it?

---

### Post by diskotek on 2008-10-08
i have the same problem and i couldn't fix it with the follwing solution that you've posted.

```
 Model=HL-DT-ST DVDRAM GSA-4163B               , FwRev=A103    , SerialNo=K4D532J4151         
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode

```

```
[    0.000000]  BIOS-e820: 0000000037fd0000 - 0000000037fde000 (ACPI data)
[    0.000000] Kernel command line: root=UUID=37911b3c-0d0e-4eaf-a2ba-e3a9a5875ffc ro quiet splash root flags=data=writeback noapic--
[   34.602477] Memory: 897284k/917312k available (2177k kernel code, 19404k reserved, 1006k data, 368k init, 0k highmem)
[   34.602493]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   38.328800] libata version 3.00 loaded.
[   38.352837] sata_sil 0000:00:11.0: version 2.3
[   38.376739] scsi0 : sata_sil
[   38.404689] scsi1 : sata_sil
[   38.404753] ata1: SATA max UDMA/100 mmio m512@0xfe9fbc00 tf 0xfe9fbc80 irq 16
[   38.404758] ata2: SATA max UDMA/100 mmio m512@0xfe9fbc00 tf 0xfe9fbcc0 irq 16
[   38.716949] ata1: SATA link down (SStatus 0 SControl 310)
[   39.027701] ata2: SATA link down (SStatus 0 SControl 310)
[   39.027894] scsi2 : sata_sil
[   39.028115] scsi3 : sata_sil
[   39.028144] ata3: SATA max UDMA/100 mmio m512@0xfe9fb800 tf 0xfe9fb880 irq 17
[   39.028148] ata4: SATA max UDMA/100 mmio m512@0xfe9fb800 tf 0xfe9fb8c0 irq 17
[   39.339206] ata3: SATA link down (SStatus 0 SControl 310)
[   39.650714] ata4: SATA link down (SStatus 0 SControl 310)
[   40.175617] scsi4 : pata_atiixp
[   40.175960] scsi5 : pata_atiixp
[   40.176743] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   40.176747] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   40.346286] ata5.00: ATA-6: ST340015A, 3.01, max UDMA/100
[   40.346290] ata5.00: 78165360 sectors, multi 16: LBA 
[   40.346440] ata5.01: ATA-7: SAMSUNG SP1213N, TL100-30, max UDMA/100
[   40.346442] ata5.01: 234493056 sectors, multi 16: LBA48 
[   40.362242] ata5.00: configured for UDMA/100
[   40.370183] ata5.01: configured for UDMA/100
[   40.845345] ata6.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A103, max UDMA/33
[   40.845365] ata6.01: ATAPI: HL-DT-ST GCE-8526B, 1.02, max UDMA/33
[   40.845375] ata6.00: simplex DMA is claimed by other device, disabling DMA
[   40.845378] ata6.01: simplex DMA is claimed by other device, disabling DMA
[   41.017047] ata6.00: configured for PIO4
[   41.188776] ata6.01: configured for PIO4
[   41.866342] EXT3-fs: mounted filesystem with writeback data mode.
[   57.255638] EXT3-fs: mounted filesystem with ordered data mode.
[   57.272515] EXT3-fs: mounted filesystem with ordered data mode.

```

```
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

---

### Post by gp2x on 2008-10-19
Ive also got this issue.

Any progress on this?

---

### Post by psyke83 on 2008-10-19
Guys,

While it may be true that DMA isn't enabled on your systems, you need to keep something in mind: since the inclusion of libata in the kernel (which is a SCSI -> IDE/SATA layer), hdparm can no longer control DMA setting for IDE devices.

The warnings you see (HDIO_SET_DMA failed: Inappropriate ioctl for device) do *not* indicate that DMA is not functioning. The [libata FAQ]("http://linux-ata.org/faq.html") explains this under the section "Older, unsupported ioctls":

> Why does HDIO_SET_DMA fail? I want to use DMA!
Why does HDIO_SET_UNMASKINTR fail?

libata intentionally does not support all the HDIO_xxx ioctls that were supported by the older IDE driver. It is now preferred to use SG_IO as a generalized ATA command submission method, rather than creating a myriad of ioctls for each specific purpose.

The design decision was made only to support the HDIO_xxx ioctls that were heavily used by other programs. Generally the driver always programs the hardware to its maximum capability automatically, completely without user intervention. Therefore, for example, HDIO_SET_DMA is not needed for the vast majority of users because DMA is automatically enabled and used where available.

The suggested settings mentioned in this thread are indeed be the solution, but they are not honoured in the /etc/modprobe.d/aliases file. Give me a while to investigate the proper place to insert these module parameters (it eludes me at the moment ;)).

---

### Post by gp2x on 2008-10-19
thanks psyke - i tried passing pata_ali.atapi_dma=1 to the kernel from grub on a whim (Im a noob) but no go....

the message:

[    6.312371] ata6.01: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    6.312374] ata6.01: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.

mentions the sysfs node...... any clues as to which node is speaks of?

and yes, DMA is definitely disabled..... its not a false positive or anything. 

thanks again!

---

### Post by gp2x on 2008-10-19
BTW, here's a related page - looks like the kernel.....


[http://www.redhat.com/archives/fedora-extras-commits/2008-June/msg01488.html](http://www.redhat.com/archives/fedora-extras-commits/2008-June/msg01488.html)

---

### Post by gp2x on 2008-10-27
<bump!>

This is a very bad issue for me, does anyone have any ideas at all?

thanks

---

### Post by psyke83 on 2008-10-27
> **gp2x said:**
> <bump!>

This is a very bad issue for me, does anyone have any ideas at all?

thanks

In your case, you can edit /etc/initramfs-tools/modules, and add to the end of this file:

```
pata_ali atapi_dma=1
```

Then, update your initramfs:

```
$ sudo update-initramfs
```

N.B. I don't recommend this at all. I have an old laptop (Compaq NX9010) which uses the pata_ali driver, and also disables ATAPI DMA. When I enable DMA for the DVD drive, the drive no longer works correctly at all, spewing lots of errors.

**Instead** of the above, you can try using the generic driver by adding "all_generic_ide" to the end of your boot prompt.

---

