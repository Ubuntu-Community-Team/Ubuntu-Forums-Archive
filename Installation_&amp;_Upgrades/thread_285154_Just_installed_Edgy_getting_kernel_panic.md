---
title: "Just installed Edgy getting kernel panic"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by onlybui on 2006-10-26
Just did a fresh install to 6.10 and now I can only boot into recovery mode using generic option... Anyone getting the same results?

---

### Post by onlybui on 2006-10-26
root@onlybui-desktop:~# dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003bf00000 (usable)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 63MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 245504
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 16128 pages, LIFO batch:3
[17179569.184000] DMI 2.4 present.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3bf00000:a4100000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda6 ro single
[17179569.184000] Found and enabled local APIC!
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1791.038 MHz processor.
[   22.798914] Using tsc for high-res timesource
[   22.799758] Console: colour VGA+ 80x25
[   22.801049] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.801477] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.818382] Memory: 963628k/982016k available (1910k kernel code, 17824k reserved, 1070k data, 308k init, 64512k highmem)
[   22.818435] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.894708] Calibrating delay using timer specific routine.. 3589.22 BogoMIPS (lpj=7178449)
[   22.894825] Security Framework v1.0.0 initialized
[   22.894871] SELinux:  Disabled at boot.
[   22.894926] Mount-cache hash table entries: 512
[   22.895089] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   22.895095] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   22.895102] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.895147] CPU: L2 Cache: 512K (64 bytes/line)
[   22.895190] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   22.895206] Checking 'hlt' instruction... OK.
[   22.910811] SMP alternatives: switching to UP code
[   22.911003] Freeing SMP alternatives: 16k freed
[   22.911167] checking if image is initramfs... it is
[   23.480605] Freeing initrd memory: 5564k freed
[   23.480654] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   23.480770] SMP motherboard not detected.
[   23.585830] Brought up 1 CPUs
[   23.585886] migration_cost=0
[   23.586224] NET: Registered protocol family 16
[   23.586289] EISA bus registered
[   23.602852] PCI: PCI BIOS revision 3.00 entry at 0xfa4b0, last bus=2
[   23.602901] PCI: Using configuration type 1
[   23.602943] Setting up standard PCI resources
[   23.605374] ACPI: Interpreter disabled.
[   23.605419] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.605467] pnp: PnP ACPI: disabled
[   23.605510] PnPBIOS: Scanning system for PnP BIOS support...
[   23.605772] PnPBIOS: Found PnP BIOS installation structure at 0xc00fafd0
[   23.605820] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb000, dseg 0xf0000
[   23.606522] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   23.606596] PCI: Probing PCI hardware
[   23.606640] PCI: Probing PCI hardware (bus 00)
[   23.607336] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[   23.607677] Boot video device is 0000:01:05.0
[   23.608434] PCI: Transparent bridge - 0000:00:14.4
[   23.609451] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   23.667435] pnp: 00:0b: ioport range 0x800-0x87f has been reserved
[   23.667630] PCI: Bridge: 0000:00:01.0
[   23.667673]   IO window: e000-efff
[   23.667717]   MEM window: fdd00000-fddfffff
[   23.667760]   PREFETCH window: d8000000-dfffffff
[   23.667805] PCI: Bridge: 0000:00:14.4
[   23.667849]   IO window: d000-dfff
[   23.667895]   MEM window: fdc00000-fdcfffff
[   23.667941]   PREFETCH window: fde00000-fdefffff
[   23.668027] NET: Registered protocol family 2
[   23.697688] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.697878] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.698807] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.699276] TCP: Hash tables configured (established 131072 bind 65536)
[   23.699322] TCP reno registered
[   23.699858] audit: initializing netlink socket (disabled)
[   23.699907] audit(1161869784.932:1): initialized
[   23.700009] highmem bounce pool size: 64 pages
[   23.700125] VFS: Disk quotas dquot_6.5.1
[   23.700186] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.700282] Initializing Cryptographic API
[   23.700326] io scheduler noop registered
[   23.700408] io scheduler anticipatory registered
[   23.700490] io scheduler deadline registered
[   23.700583] io scheduler cfq registered (default)
[   23.700907] isapnp: Scanning for PnP cards...
[   24.055462] isapnp: No Plug & Play device found
[   24.073159] Real Time Clock Driver v1.12ac
[   24.073252] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.073446] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.074024] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.074213] mice: PS/2 mouse device common for all mice
[   24.074664] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.074880] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.074927] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.075213] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   24.075257] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   24.622279] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.622945] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.624225] EISA: Probing bus 0 at eisa.0
[   24.624308] EISA: Detected 0 cards.
[   24.624608] TCP bic registered
[   24.624657] NET: Registered protocol family 1
[   24.624703] NET: Registered protocol family 8
[   24.624746] NET: Registered protocol family 20
[   24.624808] Using IPI No-Shortcut mode
[   24.625078] Freeing unused kernel memory: 308k freed
[   24.664516] input: AT Translated Set 2 keyboard as /class/input/input0
[   24.701935] Capability LSM initialized
[   25.145972] SCSI subsystem initialized
[   25.148824] libata version 1.20 loaded.
[   25.150604] sata_sil 0000:00:11.0: version 0.9
[   25.150674] ata1: SATA max UDMA/100 cmd 0xF8828080 ctl 0xF882808A bmdma 0xF8828000 irq 11
[   25.150745] ata2: SATA max UDMA/100 cmd 0xF88280C0 ctl 0xF88280CA bmdma 0xF8828008 irq 11
[   25.351406] ata1: SATA link down (SStatus 0)
[   25.361439] scsi0 : sata_sil
[   25.563116] ata2: SATA link down (SStatus 0)
[   25.573154] scsi1 : sata_sil
[   25.573360] ata3: SATA max UDMA/100 cmd 0xF882A080 ctl 0xF882A08A bmdma 0xF882A000 irq 10
[   25.573426] ata4: SATA max UDMA/100 cmd 0xF882A0C0 ctl 0xF882A0CA bmdma 0xF882A008 irq 10
[   25.930647] ata3: SATA link up 1.5 Gbps (SStatus 113)
[   25.939090] ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3468 86:3c01 87:4003 88:407f
[   25.939095] ata3: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48
[   25.947075] ata3: dev 0 configured for UDMA/100
[   25.947122] scsi2 : sata_sil
[   26.306142] ata4: SATA link up 1.5 Gbps (SStatus 113)
[   26.314582] ata4: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3468 86:3c01 87:4023 88:407f
[   26.314585] ata4: dev 0 ATA-7, max UDMA/133, 586072368 sectors: LBA48
[   26.322567] ata4: dev 0 configured for UDMA/100
[   26.322614] scsi3 : sata_sil
[   26.323257]   Vendor: ATA       Model: ST3160827AS       Rev: 3.42
[   26.324363]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   26.330111]   Vendor: ATA       Model: ST3300622AS       Rev: 3.AA
[   26.331219]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   26.337973] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   26.338033] sda: Write Protect is off
[   26.338101] sda: Mode Sense: 00 3a 00 00
[   26.338113] SCSI device sda: drive cache: write back
[   26.338206] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   26.338256] sda: Write Protect is off
[   26.338298] sda: Mode Sense: 00 3a 00 00
[   26.338309] SCSI device sda: drive cache: write back
[   26.338355]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[   26.375263] sd 2:0:0:0: Attached scsi disk sda
[   26.379106] SCSI device sdb: 586072368 512-byte hdwr sectors (300069 MB)
[   26.379175] sdb: Write Protect is off
[   26.379218] sdb: Mode Sense: 00 3a 00 00
[   26.386033] SCSI device sdb: drive cache: write back
[   26.389362] SCSI device sdb: 586072368 512-byte hdwr sectors (300069 MB)
[   26.389446] sdb: Write Protect is off
[   26.389489] sdb: Mode Sense: 00 3a 00 00
[   26.389910] SCSI device sdb: drive cache: write back
[   26.389955]  sdb: sdb1 < sdb5 >
[   26.412839] sd 3:0:0:0: Attached scsi disk sdb
[   26.830219] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   26.830289] ATIIXP: chipset revision 0
[   26.830332] ATIIXP: not 100% native mode: will probe irqs later
[   26.830381]     ide0: BM-DMA at 0xf300-0xf307, BIOS settings: hda:pio, hdb:pio
[   26.830510]     ide1: BM-DMA at 0xf308-0xf30f, BIOS settings: hdc:pio, hdd:pio
[   26.830634] Probing IDE interface ide0...
[   27.396644] Probing IDE interface ide1...
[   28.132079] hdc: TOSHIBA DVD-ROM SD-M1502, ATAPI CD/DVD-ROM drive
[   28.915022] hdd: BENQ DVD DD DW1620, ATAPI CD/DVD-ROM drive
[   28.971744] ide1 at 0x170-0x177,0x376 on irq 15
[   28.984241] hdc: ATAPI 48X DVD-ROM drive, 128kB Cache, UDMA(33)
[   28.984500] Uniform CD-ROM driver Revision: 3.20
[   28.993143] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.059356] Probing IDE interface ide0...
[   29.092319] usbcore: registered new driver usbfs
[   29.092382] usbcore: registered new driver hub
[   29.092995] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   29.093042] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   29.093207] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   29.118698] spurious 8259A interrupt: IRQ7.
[   29.118715] ohci_hcd 0000:00:13.0: irq 10, io mem 0xfe02d000
[   29.169539] ieee1394: Initialized config rom entry `ip1394'
[   29.195747] usb usb1: configuration #1 chosen from 1 choice
[   29.195901] hub 1-0:1.0: USB hub found
[   29.195955] hub 1-0:1.0: 4 ports detected
[   29.298287] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   29.298431] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   29.326055] ohci_hcd 0000:00:13.1: irq 10, io mem 0xfe02c000
[   29.386075] usb usb2: configuration #1 chosen from 1 choice
[   29.386218] hub 2-0:1.0: USB hub found
[   29.386269] hub 2-0:1.0: 4 ports detected
[   29.543002] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fdcfe000-fdcfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.568731] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   29.568816] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   29.568921] ehci_hcd 0000:00:13.2: irq 10, io mem 0xfe02b000
[   29.569476] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.569636] usb usb3: configuration #1 chosen from 1 choice
[   29.569734] hub 3-0:1.0: USB hub found
[   29.569781] hub 3-0:1.0: 8 ports detected
[   29.601673] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   29.716498] Attempting manual resume
[   29.745895] kjournald starting.  Commit interval 5 seconds
[   29.745950] EXT3-fs: mounted filesystem with ordered data mode.
[   29.973199] ohci_hcd 0000:00:13.0: wakeup
[   30.356660] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   30.575411] usb 1-2: configuration #1 chosen from 1 choice
[   30.816174] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00009f1ae1]
[   37.039720] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.042213] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.105864] Linux agpgart interface v0.101 (c) Dave Jones
[   38.092642] Floppy drive(s): fd0 is 1.44M
[   38.110886] FDC 0 is a post-1991 82077
[   38.222476] parport: PnPBIOS parport detected.
[   38.222567] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   38.260061] input: PC Speaker as /class/input/input1
[   38.277349] gameport: EMU10K1 is pci0000:02:01.1/gameport0, io 0xde00, speed 497kHz
[   38.278818] usbcore: registered new driver hiddev
[   38.289617] input: Microsoft Microsoft IntelliMouse&#65533; Optical as /class/input/input2
[   38.289696] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Optical] on usb-0000:00:13.0-2
[   38.289825] usbcore: registered new driver usbhid
[   38.289869] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   38.442278] Linux video capture interface: v1.00
[   38.590337] 8139too Fast Ethernet driver 0.9.27
[   38.591127] eth0: RealTek RTL8139 at 0xf8ac4000, 00:11:09:16:05:28, IRQ 5
[   38.591173] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   38.605198] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   38.626197] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   38.626278] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   38.672972] ts: Compaq touchscreen protocol output
[   38.819893] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   38.846516] bttv: driver version 0.9.16 loaded
[   38.846565] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   38.846657] bttv: Bt8xx card found (0).
[   38.846739] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 10, latency: 64, mmio: 0xfdeff000
[   38.846836] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[   38.846887] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[   38.846945] bttv0: gpio: en=00000000, out=00000000 in=00f4ffff [init]
[   38.846991] bttv0: using tuner=4
[   38.872296] bttv0: add subdevice "dvb0"
[   38.874472] bt878: AUDIO driver version 0.0.0 loaded
[   38.874551] bt878: Bt878 AUDIO function found (0).
[   38.874623] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[   38.874679] bt878(0): Bt878 (rev 17) at 02:02.1, irq: 10, latency: 64, memory: 0xfdefe000
[   39.109959] lp0: using parport0 (interrupt-driven).
[   39.131525] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   39.131574] ieee1394: sbp2: Try serialize_io=0 for better performance
[   39.158512] Adding 2080376k swap on /dev/disk/by-uuid/bc4200b3-deb8-4b8e-894b-1dcdb8163ae8.  Priority:-1 extents:1 across:2080376k
[   39.293565] EXT3 FS on sda6, internal journal
[   39.579165] kjournald starting.  Commit interval 5 seconds
[   39.584496] EXT3 FS on sda7, internal journal
[   39.584501] EXT3-fs: mounted filesystem with ordered data mode.
[   39.616353] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   39.663783] NTFS volume version 3.1.
[   39.686047] kjournald starting.  Commit interval 5 seconds
[   39.696255] EXT3 FS on sda3, internal journal
[   39.696259] EXT3-fs: mounted filesystem with ordered data mode.
[   39.704454] kjournald starting.  Commit interval 5 seconds
[   39.716306] EXT3 FS on sdb5, internal journal
[   39.716310] EXT3-fs: mounted filesystem with ordered data mode.
[   39.929793] NET: Registered protocol family 17
[   40.202477] NET: Registered protocol family 10
[   40.202573] lo: Disabled Privacy Extensions
[   40.202714] IPv6 over IPv4 tunneling driver
[   50.226880] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   50.228799] [fglrx] Maximum main memory to use for locked dma buffers: 865 MBytes.
[   50.228818] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[   50.537481] eth0: no IPv6 routers present
[   50.546701] [fglrx] total      GART = 134217728
[   50.546706] [fglrx] free       GART = 118226944
[   50.546708] [fglrx] max single GART = 118226944
[   50.546711] [fglrx] total      LFB  = 59633664
[   50.546713] [fglrx] free       LFB  = 49147904
[   50.546715] [fglrx] max single LFB  = 49147904
[   50.546717] [fglrx] total      Inv  = 0
[   50.546719] [fglrx] free       Inv  = 0
[   50.546720] [fglrx] max single Inv  = 0
[   50.546722] [fglrx] total      TIM  = 0


Hope this might help...

---

