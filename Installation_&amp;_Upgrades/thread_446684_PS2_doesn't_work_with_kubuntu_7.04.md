---
title: "PS/2 doesn't work with kubuntu 7.04"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by enriquejimenez on 2007-05-17
My mouse doesn't work with kubuntu 7.04. With 6.10 works fine.

Compaq presario 2274. AMD K7 300 Mhz.

Linux K7 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i586 GNU/Linux

**Dmesg**:
> [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000eb400 size: 0000000000014c00 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000013d00000 end: 0000000013e00000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000fffeb400 size: 0000000000014c00 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000eb400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000013e00000 (usable)
[    0.000000]  BIOS-e820: 00000000fffeb400 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 318MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 81408) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    81408
[    0.000000]   HighMem     81408 ->    81408
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    81408
[    0.000000] On node 0 totalpages: 81408
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 604 pages used for memmap
[    0.000000]   Normal zone: 76708 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 13e00000:ec1eb400)
[    0.000000] Detected 300.679 MHz processor.
[   28.697208] Built 1 zonelists.  Total pages: 80772
[   28.697236] Kernel command line: root=/dev/hda1 ro quiet splash acpi=off apm=on apm=power-off noapic
[   28.698911] No local APIC present or hardware disabled
[   28.698999] mapped APIC to ffffd000 (0128a000)
[   28.699116] Initializing CPU#0
[   28.699445] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   28.701613] Console: colour VGA+ 80x25
[   28.705920] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.710314] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.804276] Memory: 311360k/325632k available (1992k kernel code, 13648k reserved, 893k data, 328k init, 0k highmem)
[   28.804346] virtual kernel memory layout:
[   28.804354]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.804363]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.804373]     vmalloc : 0xd4800000 - 0xff7fe000   ( 687 MB)
[   28.804382]     lowmem  : 0xc0000000 - 0xd3e00000   ( 318 MB)
[   28.804392]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   28.804401]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   28.804410]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   28.804439] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.883429] Calibrating delay using timer specific routine.. 602.50 BogoMIPS (lpj=1205014)
[   28.883916] Security Framework v1.0.0 initialized
[   28.883966] SELinux:  Disabled at boot.
[   28.884140] Mount-cache hash table entries: 512
[   28.885826] CPU: After generic identify, caps: 008001bf 808009bf 00000000 00000000 00000000 00000000 00000000
[   28.885907] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)
[   28.885929] CPU: After all inits, caps: 008001bf 808009bf 00000000 00000000 00000000 00000000 00000000
[   28.886059] Compat vDSO mapped to ffffe000.
[   28.886140] Remapping vsyscall page to ffffe000
[   28.886191] Checking 'hlt' instruction... OK.
[   28.899621] SMP alternatives: switching to UP code
[   28.901147] Freeing SMP alternatives: 11k freed
[   28.902662] Early unpacking initramfs... done
[   31.952347] CPU0: AMD-K6(tm) 3D processor stepping 00
[   31.952405] SMP motherboard not detected.
[   31.952428] Local APIC not detected. Using dummy APIC emulation.
[   31.953013] Brought up 1 CPUs
[   31.956001] Booting paravirtualized kernel on bare hardware
[   31.956615] Time: 16:21:38  Date: 04/16/107
[   31.956935] NET: Registered protocol family 16
[   31.958131] EISA bus registered
[   31.961037] PCI: PCI BIOS revision 2.10 entry at 0xfd9d4, last bus=0
[   31.961057] PCI: Using configuration type 1
[   31.961072] Setting up standard PCI resources
[   31.977437] ACPI: Interpreter disabled.
[   31.977468] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.977560] pnp: PnP ACPI: disabled
[   31.977585] PnPBIOS: Scanning system for PnP BIOS support...
[   31.978043] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7620
[   31.978076] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa672, dseg 0x400
[   32.643362] PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
[   32.643942] PCI: Probing PCI hardware
[   32.643976] PCI: Probing PCI hardware (bus 00)
[   32.645261] Boot video device is 0000:00:0d.0
[   32.650206] PCI: Using IRQ router SIS [1039/0008] at 0000:00:01.0
[   32.658799] NET: Registered protocol family 8
[   32.658818] NET: Registered protocol family 20
[   32.659587] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   32.659614] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[   32.659664] pnp: 00:0b: ioport range 0x3f0-0x3f0 has been reserved
[   32.659686] pnp: 00:0b: ioport range 0x3f1-0x3f1 has been reserved
[   32.664653] NET: Registered protocol family 2
[   32.699953] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   32.700929] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   32.702930] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   32.703985] TCP: Hash tables configured (established 16384 bind 8192)
[   32.704008] TCP reno registered
[   32.715976] checking if image is initramfs... it is
[   38.235751] Freeing initrd memory: 6995k freed
[   38.239842] audit: initializing netlink socket (disabled)
[   38.239960] audit(1179332504.116:1): initialized
[   38.241571] VFS: Disk quotas dquot_6.5.1
[   38.241816] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.242425] io scheduler noop registered
[   38.242451] io scheduler anticipatory registered
[   38.242470] io scheduler deadline registered
[   38.242598] io scheduler cfq registered (default)
[   38.242671] Disabling direct PCI/PCI transfers.
[   38.244424] isapnp: Scanning for PnP cards...
[   38.599946] isapnp: No Plug & Play device found
[   39.129125] Real Time Clock Driver v1.12ac
[   39.130203] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   39.131045] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.138751] 00:16: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.141712] mice: PS/2 mouse device common for all mice
[   39.150859] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   39.152753] input: Macintosh mouse button emulation as /class/input/input0
[   39.153273] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   39.153309] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   39.155085] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   39.406296] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.407984] EISA: Probing bus 0 at eisa.0
[   39.408099] Cannot allocate resource for EISA slot 8
[   39.408115] EISA: Detected 0 cards.
[   39.408792] TCP cubic registered
[   39.408855] NET: Registered protocol family 1
[   39.409034] Using IPI No-Shortcut mode
[   39.409233]   Magic number: 7:714:388
[   39.410208] Time: tsc clocksource has been installed.
[   39.414827] Freeing unused kernel memory: 328k freed
[   39.433952] input: AT Translated Set 2 keyboard as /class/input/input1
[   43.849383] Capability LSM initialized
[   44.432605] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   51.817388] SIS5513: IDE controller at PCI slot 0000:00:01.1
[   51.817480] PCI: setting IRQ 9 as level-triggered
[   51.817500] PCI: Assigned IRQ 9 for device 0000:00:01.1
[   51.817544] PCI: Sharing IRQ 9 with 0000:00:01.2
[   51.817618] SIS5513: chipset revision 208
[   51.817635] SIS5513: not 100% native mode: will probe irqs later
[   51.817679] SIS5513: SiS5597 ATA 33 controller
[   51.817756]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:pio, hdb:DMA
[   51.817854]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:DMA, hdd:pio
[   51.817935] Probing IDE interface ide0...
[   52.190346] usbcore: registered new interface driver usbfs
[   52.190581] usbcore: registered new interface driver hub
[   52.190941] usbcore: registered new device driver usb
[   52.200783] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   52.244911] hda: ST36531A, ATA DISK drive
[   52.258618] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   52.524935] hdb: ST34323A, ATA DISK drive
[   52.581797] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   52.582341] Probing IDE interface ide1...
[   53.316754] hdc: Polaroid BurnMAX48, ATAPI CD/DVD-ROM drive
[   53.654331] ide1 at 0x170-0x177,0x376 on irq 15
[   53.672001] PCI: Found IRQ 9 for device 0000:00:01.2
[   53.672045] PCI: Sharing IRQ 9 with 0000:00:01.1
[   53.672141] PCI: Setting latency timer of device 0000:00:01.2 to 32
[   53.672165] ohci_hcd 0000:00:01.2: OHCI Host Controller
[   53.673478] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[   53.673593] ohci_hcd 0000:00:01.2: irq 9, io mem 0xfedff000
[   53.740094] usb usb1: configuration #1 chosen from 1 choice
[   53.740437] hub 1-0:1.0: USB hub found
[   53.740792] hub 1-0:1.0: 2 ports detected
[   53.743212] SCSI subsystem initialized
[   53.822178] libata version 2.20 loaded.
[   53.846164] 8139cp 0000:00:12.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   53.846192] 8139cp 0000:00:12.0: Try the "8139too" driver instead.
[   53.867968] 8139too Fast Ethernet driver 0.9.28
[   53.868268] PCI: Enabling device 0000:00:12.0 (0004 -> 0007)
[   53.868320] PCI: Assigned IRQ 9 for device 0000:00:12.0
[   53.868413] PCI: Setting latency timer of device 0000:00:12.0 to 32
[   53.869166] eth0: RealTek RTL8139 at 0xd4828c00, 00:80:5a:29:bb:db, IRQ 9
[   53.869190] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   54.992478] hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   54.992548] Uniform CD-ROM driver Revision: 3.20
[   55.085078] hda: max request size: 128KiB
[   55.085108] hda: 12706470 sectors (6505 MB) w/128KiB Cache, CHS=13446/15/63, UDMA(33)
[   55.085152] hda: cache flushes not supported
[   55.085433]  hda: hda1 hda2
[   55.313388] hdb: max request size: 128KiB
[   55.313417] hdb: 8421840 sectors (4311 MB) w/128KiB Cache, CHS=8912/15/63, UDMA(33)
[   55.313461] hdb: cache flushes not supported
[   55.313720]  hdb: hdb1
[   57.079236] Attempting manual resume
[   57.079264] swsusp: Resume From Partition 3:2
[   57.079280] PM: Checking swsusp image.
[   57.104963] PM: Resume from disk failed.
[   57.321326] kjournald starting.  Commit interval 5 seconds
[   57.321445] EXT3-fs: mounted filesystem with ordered data mode.
[   83.867209] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   85.785703] NET: Registered protocol family 10
[   85.786679] lo: Disabled Privacy Extensions
[   96.551542] eth0: no IPv6 routers present
[  100.068293] Linux agpgart interface v0.102 (c) Dave Jones
[  100.756045] voodoo3_smbus 0000:00:0d.0: Using Banshee/Voodoo3 I2C device at d485a000
[  100.823199] **sis5595_smbus 0000:00:01.0: Looked for SIS5595 but found unsupported device 5597**
[  100.823238]** sis5595_smbus 0000:00:01.0: SIS5595 not detected, module not inserted.**
[  101.664041] input: PC Speaker as /class/input/input2
[  103.123534] sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module not inserted.
[  103.231898] pci 0000:00:00.0: Looked for SIS5595 but found unsupported device 5597
[  105.481179] parport: PnPBIOS parport detected.
[  105.481301] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  106.869557] gameport: NS558 PnP Gameport is pnp00:1b/gameport0, io 0x201, speed 552kHz
[  109.362198] fuse init (API version 7.8)
[  109.490411] lp0: using parport0 (interrupt-driven).
[  109.686084] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  113.882639] Adding 489972k swap on /dev/disk/by-uuid/87750b80-f7e4-4bbb-bf95-dcf6d0ee833a.  Priority:-1 extents:1 across:489972k
[  114.431329] EXT3 FS on hda1, internal journal
[  116.030884] kjournald starting.  Commit interval 5 seconds
[  116.031587] EXT3 FS on hdb1, internal journal
[  116.031640] EXT3-fs: mounted filesystem with ordered data mode.
[  120.126068] NET: Registered protocol family 17
[  133.597746] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  133.598408] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  133.599932] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  133.600750] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  146.595393] ppdev: user-space parallel port driver
[  158.677910] Bluetooth: Core ver 2.11
[  158.678506] NET: Registered protocol family 31
[  158.678525] Bluetooth: HCI device and connection manager initialized
[  158.678553] Bluetooth: HCI socket layer initialized
[  158.939625] Bluetooth: L2CAP ver 2.8
[  158.939653] Bluetooth: L2CAP socket layer initialized
[  159.251642] Bluetooth: RFCOMM socket layer initialized
[  159.251766] Bluetooth: RFCOMM TTY layer initialized
[  159.251783] Bluetooth: RFCOMM ver 1.8


**lspci-vvnn**

> 00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 5597 [SiS5582] [1039:5597] (rev 10)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 16

00:01.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) [1039:0008] (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:01.1 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev d0) (prog-if 8a [Master SecP PriP])
	Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step) [1039:5513]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 9
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at fcf0 [size=16]

00:01.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 10) (prog-if 10 [OHCI])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at fedff000 (32-bit, non-prefetchable) [size=4K]

00:0d.0 VGA compatible controller [0300]: 3Dfx Interactive, Inc. Voodoo 3 [121a:0005] (rev 01) (prog-if 00 [VGA])
	Subsystem: 3Dfx Interactive, Inc. Voodoo3 2000 PCI [121a:0036]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=32M]
	Region 1: Memory at fa000000 (32-bit, prefetchable) [size=32M]
	Region 2: I/O ports at f800 [size=256]
	[virtual] Expansion ROM at 20000000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 1
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:12.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RT8139 [10ec:8139]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 9
	Region 0: I/O ports at f400 [size=256]
	Region 1: Memory at fedfec00 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 20010000 [disabled] [size=64K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:14.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 5597/5598/6326 VGA [1039:0200] (rev 68) (prog-if 00 [VGA])
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Region 0: Memory at fe800000 (32-bit, prefetchable) [disabled] [size=4M]
	Region 1: Memory at fede0000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Region 2: I/O ports at fc00 [disabled] [size=128]
	[virtual] Expansion ROM at 20020000 [disabled] [size=32K]



---

### Post by timothy_duncan on 2007-08-06
same problem here,.. i tried the live ubuntu feisty cd, and my mouse is not working.  this mouse was working before at dapper.  any help pls

---

### Post by timothy_duncan on 2007-08-06
i've seen this link at launchpad and saying:

This bug fix is now available as an official Ubuntu update.

Thanks to everyone who tried the test kernel, and reported their experiences. I'm marking this bug as fixed.


[https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221]("https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221")

How could i apply any of this updates if i can not use my mouse to install feisty..  please help

---

### Post by gridsleep on 2007-08-07
Now, please patch the patch so it works in MS Virtual PC 2007.  Thank you.

---

### Post by timothy_duncan on 2007-08-07
how could i use the patch when i can't get the mouse to move and install feisty...:mad:

---

