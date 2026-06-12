---
title: "Camera not being recognised?"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2007-06-21
I am trying to work out why my fujifilm s5000 s not being recognised by Ubuntu with the result that no pictures can be downloaded. Following advice else where I typed

dmseg

This is the response but  I can not work out which device is the camera. Can someone point it to me?
```
    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Detected 2667.056 MHz processor.
[   28.303900] Built 1 zonelists.  Total pages: 520145
[   28.303903] Kernel command line: root=UUID=221d448e-c456-4e67-b1f4-675a654e16c8 ro quiet splash rootflags=data=writeback
[   28.304074] mapped APIC to ffffd000 (fee00000)
[   28.304077] mapped IOAPIC to ffffc000 (fec00000)
[   28.304080] Enabling fast FPU save and restore... done.
[   28.304083] Enabling unmasked SIMD FPU exception support... done.
[   28.304092] Initializing CPU#0
[   28.304171] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   28.304203] spurious 8259A interrupt: IRQ7.
[   28.305714] Console: colour VGA+ 80x25
[   28.306069] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.306451] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.370192] Memory: 2068140k/2096960k available (1917k kernel code, 27496k reserved, 868k data, 328k init, 1179456k highmem)
[   28.370203] virtual kernel memory layout:
[   28.370204]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[   28.370206]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.370207]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.370208]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.370209]       .init : 0xc03bc000 - 0xc040e000   ( 328 kB)
[   28.370211]       .data : 0xc02df423 - 0xc03b8434   ( 868 kB)
[   28.370212]       .text : 0xc0100000 - 0xc02df423   (1917 kB)
[   28.370215] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.370388] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   28.370394] hpet0: 3 32-bit timers, 25000000 Hz
[   28.371401] Using HPET for base-timer
[   28.450182] Calibrating delay using timer specific routine.. 5340.04 BogoMIPS (lpj=10680098)
[   28.450218] Security Framework v1.0.0 initialized
[   28.450224] SELinux:  Disabled at boot.
[   28.450235] Mount-cache hash table entries: 512
[   28.450337] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000001
[   28.450345] monitor/mwait feature present.
[   28.450347] using mwait in idle threads.
[   28.450352] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   28.450354] CPU: L2 cache: 1024K
[   28.450357] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000651d 00000000 00000001
[   28.450366] Compat vDSO mapped to ffffe000.
[   28.450370] Remapping vsyscall page to ffffe000
[   28.450384] CPU: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[   28.450391] Checking 'hlt' instruction... OK.
[   28.466535] Early unpacking initramfs... done
[   28.771624] ACPI: Core revision 20060707
[   28.771773] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   28.775598] ENABLING IO-APIC IRQs
[   28.775831] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.921118] Booting paravirtualized kernel on bare hardware
[   28.921200] Time:  7:43:46  Date: 05/20/107
[   28.921224] NET: Registered protocol family 16
[   28.921295] EISA bus registered
[   28.921299] ACPI: bus type pci registered
[   28.921540] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   28.921543] PCI: Using configuration type 1
[   28.921544] Setting up standard PCI resources
[   28.937461] ACPI: Interpreter enabled
[   28.937464] ACPI: Using IOAPIC for interrupt routing
[   28.938119] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.938124] PCI: Probing PCI hardware (bus 00)
[   28.940330] Boot video device is 0000:01:00.0
[   28.940955] PCI: Transparent bridge - 0000:00:10.0
[   28.941030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.967547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   28.968248] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   28.968456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PB._PRT]
[   28.968621] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[   28.969697] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[   28.970219] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[   28.970738] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *5
[   28.971261] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *10
[   28.971782] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
[   28.972304] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   28.972846] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[   28.973362] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   28.973878] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[   28.974393] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[   28.974907] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[   28.975423] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[   28.975971] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[   28.976493] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[   28.977041] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[   28.977560] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[   28.978081] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[   28.978617] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *5
[   28.979223] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   28.979323] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.979331] pnp: PnP ACPI init
[   28.986705] pnp: PnP ACPI: found 16 devices
[   28.986710] PnPBIOS: Disabled by ACPI PNP
[   28.986749] PCI: Using ACPI for IRQ routing
[   28.986752] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.030066] NET: Registered protocol family 8
[   29.030069] NET: Registered protocol family 20
[   29.031578] pnp: 00:0d: ioport range 0xa00-0xadf has been reserved
[   29.031582] pnp: 00:0d: ioport range 0xae0-0xaef has been reserved
[   29.031875] PCI: Bridge: 0000:00:03.0
[   29.031878]   IO window: d000-dfff
[   29.031883]   MEM window: fb000000-fdbfffff
[   29.031887]   PREFETCH window: d0000000-dfffffff
[   29.031891] PCI: Bridge: 0000:00:06.0
[   29.031893]   IO window: disabled.
[   29.031896]   MEM window: disabled.
[   29.031899]   PREFETCH window: disabled.
[   29.031903] PCI: Bridge: 0000:00:07.0
[   29.031905]   IO window: disabled.
[   29.031908]   MEM window: disabled.
[   29.031911]   PREFETCH window: disabled.
[   29.031916] PCI: Bridge: 0000:00:10.0
[   29.031920]   IO window: e000-efff
[   29.031926]   MEM window: fdc00000-febfffff
[   29.031931]   PREFETCH window: 88000000-880fffff
[   29.031951] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   29.031963] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   29.031974] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   29.031990] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   29.032011] NET: Registered protocol family 2
[   29.068600] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.068726] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   29.069026] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   29.069176] TCP: Hash tables configured (established 131072 bind 65536)
[   29.069178] TCP reno registered
[   29.080651] checking if image is initramfs... it is
[   29.674712] Freeing initrd memory: 6776k freed
[   29.675057] audit: initializing netlink socket (disabled)
[   29.675070] audit(1182325426.388:1): initialized
[   29.675131] highmem bounce pool size: 64 pages
[   29.675178] VFS: Disk quotas dquot_6.5.1
[   29.675194] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.675236] io scheduler noop registered
[   29.675239] io scheduler anticipatory registered
[   29.675241] io scheduler deadline registered
[   29.675249] io scheduler cfq registered (default)
[   29.707085] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   29.707135] assign_interrupt_mode Found MSI capability
[   29.707138] Allocate Port Service[0000:00:03.0:pcie00]
[   29.707243] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   29.707292] assign_interrupt_mode Found MSI capability
[   29.707294] Allocate Port Service[0000:00:06.0:pcie00]
[   29.707394] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   29.707443] assign_interrupt_mode Found MSI capability
[   29.707446] Allocate Port Service[0000:00:07.0:pcie00]
[   29.707592] isapnp: Scanning for PnP cards...
[   30.058852] isapnp: No Plug & Play device found
[   30.083051] hpet_resources: 0xfed00000 is busy
[   30.083071] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.083233] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.083939] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.084224] mice: PS/2 mouse device common for all mice
[   30.084747] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.084960] input: Macintosh mouse button emulation as /class/input/input0
[   30.084995] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.084999] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.085256] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   30.087685] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.087690] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.087811] EISA: Probing bus 0 at eisa.0
[   30.087823] Cannot allocate resource for EISA slot 2
[   30.087830] Cannot allocate resource for EISA slot 4
[   30.087833] Cannot allocate resource for EISA slot 5
[   30.087835] Cannot allocate resource for EISA slot 6
[   30.087845] EISA: Detected 0 cards.
[   30.117859] TCP cubic registered
[   30.117866] NET: Registered protocol family 1
[   30.117885] Using IPI Shortcut mode
[   30.117939] ACPI: (supports S0 S1 S3 S4 S5)
[   30.117994]   Magic number: 11:925:723
[   30.118284] Freeing unused kernel memory: 328k freed
[   30.121798] Time: tsc clocksource has been installed.
[   30.131269] input: AT Translated Set 2 keyboard as /class/input/input1
[   31.337080] Capability LSM initialized
[   32.007755] usbcore: registered new interface driver usbfs
[   32.007779] usbcore: registered new interface driver hub
[   32.007800] usbcore: registered new device driver usb
[   32.009217] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[   32.009224] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 23 (level, low) -> IRQ 16
[   32.009237] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   32.009241] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   32.009361] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   32.009395] ehci_hcd 0000:00:0b.1: debug port 1
[   32.009402] PCI: cache line size of 128 is not supported by device 0000:00:0b.1
[   32.009413] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xfaffec00
[   32.009425] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.009510] usb usb1: configuration #1 chosen from 1 choice
[   32.009542] hub 1-0:1.0: USB hub found
[   32.009549] hub 1-0:1.0: 8 ports detected
[   32.073603] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.090005] SCSI subsystem initialized
[   32.090671] 3ware Storage Controller device driver for Linux v1.26.02.002.
[   32.109719] ieee1394: Initialized config rom entry `ip1394'
[   32.135308] libata version 2.20 loaded.
[   32.137188] sata_nv 0000:00:0e.0: version 3.3
[   32.137721] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[   32.137729] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 22 (level, low) -> IRQ 17
[   32.137750] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   32.137799] ata1: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001c482 bmdma 0x0001c000 irq 17
[   32.137827] ata2: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c082 bmdma 0x0001c008 irq 17
[   32.137842] scsi0 : sata_nv
[   32.147234] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   32.185616] Floppy drive(s): fd0 is 1.44M
[   32.255944] FDC 0 is a post-1991 82077
[   32.447713] ata1: SATA link down (SStatus 0 SControl 300)
[   32.457860] ATA: abnormal status 0x7F on port 0x0001c807
[   32.457889] scsi1 : sata_nv
[   32.539472] usb 1-3: new high speed USB device using ehci_hcd and address 3
[   32.673762] usb 1-3: configuration #1 chosen from 1 choice
[   32.766877] ata2: SATA link down (SStatus 0 SControl 300)
[   32.777022] ATA: abnormal status 0x7F on port 0x0001c407
[   32.778398] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 21
[   32.778405] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LSA1] -> GSI 21 (level, low) -> IRQ 18
[   32.778431] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   32.778463] ata3: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001b882 bmdma 0x0001b400 irq 18
[   32.778490] ata4: SATA max UDMA/133 cmd 0x0001b800 ctl 0x0001b482 bmdma 0x0001b408 irq 18
[   32.778507] scsi2 : sata_nv
[   33.086039] ata3: SATA link down (SStatus 0 SControl 300)
[   33.096183] ATA: abnormal status 0x7F on port 0x0001bc07
[   33.096209] scsi3 : sata_nv
[   33.405203] ata4: SATA link down (SStatus 0 SControl 300)
[   33.415345] ATA: abnormal status 0x7F on port 0x0001b807
[   33.420589] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[   33.420596] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 20 (level, low) -> IRQ 19
[   33.420610] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   33.420615] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   33.420763] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   33.420782] ohci_hcd 0000:00:0b.0: irq 19, io mem 0xfafff000
[   33.475141] usb usb2: configuration #1 chosen from 1 choice
[   33.475175] hub 2-0:1.0: USB hub found
[   33.475187] hub 2-0:1.0: 8 ports detected
[   33.577863] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[   33.577871] ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [LNKB] -> GSI 19 (level, low) -> IRQ 20
[   33.577901] scsi_proc_hostdir_add: proc_mkdir failed for <NULL>
[   33.879955] usb 2-2: new low speed USB device using ohci_hcd and address 2
[   34.093491] usb 2-2: configuration #1 chosen from 1 choice
[   34.107640] usbcore: registered new interface driver hiddev
[   34.114578] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input2
[   34.114683] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-2
[   34.114698] usbcore: registered new interface driver usbhid
[   34.114701] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   39.664797] 3w-xxxx: AEN: ERROR: DCB checksum error: Port #0.
[   40.111626] scsi4 : 3ware Storage Controller
[   40.111788] 3w-xxxx: scsi4: Found a 3ware Storage Controller at 0xec00, IRQ: 20.
[   40.112243] scsi 4:0:1:0: Direct-Access     3ware    Logical Disk 1   1.2  PQ: 0 ANSI: 0
[   40.112673] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 18
[   40.112680] ACPI: PCI Interrupt 0000:04:09.0[A] -> Link [LNKD] -> GSI 18 (level, low) -> IRQ 21
[   40.163188] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   40.163215] NFORCE-MCP51: chipset revision 161
[   40.163217] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   40.163223] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   40.163231] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   40.163242]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[   40.163256]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[   40.163264] Probing IDE interface ide0...
[   40.174300] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   40.187340] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   40.187440] sda: Write Protect is off
[   40.187443] sda: Mode Sense: 00 00 00 00
[   40.187753] SCSI device sda: write cache: enabled, read cache: disabled, supports DPO and FUA
[   40.188104] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   40.188162] sda: Write Protect is off
[   40.188164] sda: Mode Sense: 00 00 00 00
[   40.188466] SCSI device sda: write cache: enabled, read cache: disabled, supports DPO and FUA
[   40.188470]  sda: sda1
[   40.194864] sd 4:0:1:0: Attached scsi disk sda
[   40.199134] sd 4:0:1:0: Attached scsi generic sg0 type 0
[   40.450908] hda: WDC WD1200BB-00DAA3, ATA DISK drive
[   40.730175] hdb: ExcelStor Technology J340, ATA DISK drive
[   40.788732] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   40.812539] Probing IDE interface ide1...
[   41.444244] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000010dc0106bb70]
[   41.544044] hdc: PIONEER DVD-RW DVR-111D, ATAPI CD/DVD-ROM drive
[   41.823311] hdd: ExcelStor Technology J340, ATA DISK drive
[   41.880074] ide1 at 0x170-0x177,0x376 on irq 15
[   41.897082] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[   41.897087] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 23 (level, low) -> IRQ 16
[   41.897096] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   41.897104] forcedeth: using HIGHDMA
[   41.902812] hda: max request size: 512KiB
[   41.916409] hda: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   41.917828] hda: cache flushes supported
[   41.917868]  hda: hda1 hda2 < hda5 >
[   41.945853] hdb: max request size: 512KiB
[   41.946198] hdb: 80418240 sectors (41174 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
[   41.946630] hdb: cache flushes supported
[   41.946655]  hdb: hdb1 hdb2 < hdb5 hdb6 hdb7 >
[   42.010946] hdd: max request size: 512KiB
[   42.011314] hdd: 80418240 sectors (41174 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
[   42.011744] hdd: cache flushes supported
[   42.011767]  hdd: hdd1 hdd2 < hdd5 >
[   42.051110] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[   42.051120] Uniform CD-ROM driver Revision: 3.20
[   42.413898] eth0: forcedeth.c: subsystem: 01462:7350 bound to 0000:00:14.0
[   42.465204] Attempting manual resume
[   42.465208] swsusp: Resume From Partition 3:5
[   42.465210] PM: Checking swsusp image.
[   42.487864] PM: Resume from disk failed.
[   42.539126] kjournald starting.  Commit interval 5 seconds
[   42.539136] EXT3-fs: mounted filesystem with writeback data mode.
[   53.908070] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   53.913095] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.923712] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   53.923749] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x6000
[   54.955736] Real Time Clock Driver v1.12ac
[   54.966928] input: PC Speaker as /class/input/input3
[   55.017021] Linux agpgart interface v0.102 (c) Dave Jones
[   55.263104] nvidia: module license 'NVIDIA' taints kernel.
[   55.517071] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 17
[   55.517080] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNEA] -> GSI 17 (level, low) -> IRQ 22
[   55.517091] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   55.517276] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   55.620449] parport: PnPBIOS parport detected.
[   55.620520] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   55.842966] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   55.842972] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 22 (level, low) -> IRQ 17
[   55.842989] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   56.049870] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   60.626058] fuse init (API version 7.8)
[   60.652853] lp0: using parport0 (interrupt-driven).
[   60.678127] Adding 3028212k swap on /dev/disk/by-uuid/5abbef3f-03f4-4927-868f-93ec33fe1a6f.  Priority:-1 extents:1 across:3028212k
[   60.814355] EXT3 FS on hda1, internal journal
[   60.987627] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   74.250777] NET: Registered protocol family 17
[   78.187889] Using specific hotkey driver
[   78.320471] No dock devices found.
[   78.377464] ibm_acpi: ec object not found
[   78.439403] input: Power Button (FF) as /class/input/input4
[   78.443335] ACPI: Power Button (FF) [PWRF]
[   78.480015] input: Power Button (CM) as /class/input/input5
[   78.483939] ACPI: Power Button (CM) [PWRB]
[   78.498375] pcc_acpi: loading...
[   82.339918] ppdev: user-space parallel port driver
[   84.037071] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   84.037076] apm: overridden by ACPI.
[   88.196249] Bluetooth: Core ver 2.11
[   88.196302] NET: Registered protocol family 31
[   88.196304] Bluetooth: HCI device and connection manager initialized
[   88.196307] Bluetooth: HCI socket layer initialized
[   88.321909] Bluetooth: L2CAP ver 2.8
[   88.321914] Bluetooth: L2CAP socket layer initialized
[   88.389736] Bluetooth: RFCOMM socket layer initialized
[   88.389747] Bluetooth: RFCOMM TTY layer initialized
[   88.389749] Bluetooth: RFCOMM ver 1.8
[   89.978252] /dev/vmmon[6872]: VMCI: Driver initialized.
[   89.980332] /dev/vmmon[6872]: Module vmmon: registered with major=10 minor=165
[   89.980589] /dev/vmmon[6872]: Module vmmon: initialized
[   90.387423] /dev/vmnet: open called by PID 6914 (vmnet-bridge)
[   90.387652] /dev/vmnet: hub 0 does not exist, allocating memory.
[   90.387815] /dev/vmnet: port on hub 0 successfully opened
[   90.387972] bridge-eth1: enabling the bridge
[   90.388096] bridge-eth1: up
[   90.388199] bridge-eth1: already up
[   90.388317] bridge-eth1: attached
[   90.761106] /dev/vmnet: open called by PID 6930 (vmnet-dhcpd)
[   90.761281] /dev/vmnet: hub 1 does not exist, allocating memory.
[   90.761463] /dev/vmnet: port on hub 1 successfully opened
[   90.803849] /dev/vmnet: open called by PID 6941 (vmnet-dhcpd)
[   90.804024] /dev/vmnet: hub 8 does not exist, allocating memory.
[   90.804184] /dev/vmnet: port on hub 8 successfully opened
[   90.818945] /dev/vmnet: open called by PID 6946 (vmnet-natd)
[   90.819169] /dev/vmnet: port on hub 8 successfully opened
[  100.431066] /dev/vmnet: open called by PID 7098 (vmnet-netifup)
[  100.431211] /dev/vmnet: port on hub 1 successfully opened
[  100.745439] /dev/vmnet: open called by PID 7114 (vmnet-netifup)
[  100.745546] /dev/vmnet: port on hub 8 successfully opened
[32668.180136] /dev/vmnet: open called by PID 11786 (vmware-vmx)
[32668.180273] device eth1 entered promiscuous mode
[32668.180281] audit(1182354545.979:2): dev=eth1 prom=256 old_prom=0 auid=4294967295
[32668.180284] bridge-eth1: enabled promiscuous mode
[32668.180287] /dev/vmnet: port on hub 0 successfully opened
[32668.412814] /dev/vmmon[11800]: host clock rate change request 0 -> 19
[32668.412946] /dev/vmmon[11800]: host clock rate change request 19 -> 83
[39840.171442] device eth1 left promiscuous mode
[39840.171453] audit(1182361735.641:3): dev=eth1 prom=0 old_prom=256 auid=4294967295
[39840.171456] bridge-eth1: disabled promiscuous mode
[39840.326022] /dev/vmmon[11786]: host clock rate change request 83 -> 0
[39840.334794] vmmon: Had to deallocate locked 15384 pages from vm driver e443e000
[39840.339697] vmmon: Had to deallocate AWE 4270 pages from vm driver e443e000
[110113.243079] /dev/vmnet: open called by PID 19235 (vmware-vmx)
[110113.243215] device eth1 entered promiscuous mode
[110113.243223] audit(1182432181.912:4): dev=eth1 prom=256 old_prom=0 auid=4294967295
[110113.243227] bridge-eth1: enabled promiscuous mode
[110113.243229] /dev/vmnet: port on hub 0 successfully opened
[110113.489479] /dev/vmmon[19249]: host clock rate change request 0 -> 19
[110113.489502] /dev/vmmon[19249]: host clock rate change request 19 -> 83
[110167.031809] device eth1 left promiscuous mode
[110167.031820] audit(1182432235.835:5): dev=eth1 prom=0 old_prom=256 auid=4294967295
[110167.031823] bridge-eth1: disabled promiscuous mode
[110167.198133] /dev/vmmon[19235]: host clock rate change request 83 -> 0
[110167.205413] vmmon: Had to deallocate locked 11108 pages from vm driver f320d000
[110167.209960] vmmon: Had to deallocate AWE 3450 pages from vm driver f320d000
[118910.632255] /dev/vmnet: open called by PID 26484 (vmware-vmx)
[118910.632392] device eth1 entered promiscuous mode
[118910.632400] audit(1182441000.986:6): dev=eth1 prom=256 old_prom=0 auid=4294967295
[118910.632403] bridge-eth1: enabled promiscuous mode
[118910.632406] /dev/vmnet: port on hub 0 successfully opened
[118910.956906] /dev/vmmon[26494]: host clock rate change request 0 -> 19
[118910.956929] /dev/vmmon[26494]: host clock rate change request 19 -> 83
[131699.494605] usb 2-4: new full speed USB device using ohci_hcd and address 3
[131699.716117] usb 2-4: configuration #1 chosen from 1 choice
[131699.884947] usbcore: registered new interface driver libusual
[131699.915307] Initializing USB Mass Storage driver...
[131699.915376] scsi5 : SCSI emulation for USB Mass Storage devices
[131699.915422] usb-storage: device found at 3
[131699.915425] usb-storage: waiting for device to settle before scanning
[131699.915433] usbcore: registered new interface driver usb-storage
[131699.915436] USB Mass Storage support registered.
[131704.902460] usb-storage: device scan complete
[131704.909452] scsi 5:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[131704.931373] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[131704.944338] sdb: Write Protect is off
[131704.944342] sdb: Mode Sense: 07 00 00 00
[131704.944345] sdb: assuming drive cache: write through
[131704.963286] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[131704.976261] sdb: Write Protect is off
[131704.976265] sdb: Mode Sense: 07 00 00 00
[131704.976267] sdb: assuming drive cache: write through
[131704.976273]  sdb: sdb1
[131704.991250] sd 5:0:0:0: Attached scsi removable disk sdb
[131704.991301] sd 5:0:0:0: Attached scsi generic sg1 type 0
[131805.845852] usb 2-4: USB disconnect, address 3
[133078.720769] usb 2-4: new full speed USB device using ohci_hcd and address 4
[133078.942278] usb 2-4: configuration #1 chosen from 1 choice
[133078.946745] scsi6 : SCSI emulation for USB Mass Storage devices
[133078.951407] usb-storage: device found at 4
[133078.951412] usb-storage: waiting for device to settle before scanning
[133083.937125] usb-storage: device scan complete
[133083.944115] scsi 6:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[133083.966033] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[133083.979099] sdb: Write Protect is off
[133083.979104] sdb: Mode Sense: 07 00 00 00
[133083.979106] sdb: assuming drive cache: write through
[133083.997949] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[133084.010924] sdb: Write Protect is off
[133084.010928] sdb: Mode Sense: 07 00 00 00
[133084.010930] sdb: assuming drive cache: write through
[133084.010935]  sdb: sdb1
[133084.025913] sd 6:0:0:0: Attached scsi removable disk sdb
[133084.025963] sd 6:0:0:0: Attached scsi generic sg1 type 0
robin@robin-desktop:~$ 


```

---

### Post by cwgpress on 2007-06-22
> **Robbyx said:**
> I am trying to work out why my fujifilm s5000 s not being recognised by Ubuntu with the result that no pictures can be downloaded. Following advice else where I typed

dmseg

This is the response but  I can not work out which device is the camera. Can someone point it to me?
```

[131699.494605] usb 2-4: new full speed USB device using ohci_hcd and address 3
[131699.716117] usb 2-4: configuration #1 chosen from 1 choice
[131699.884947] usbcore: registered new interface driver libusual
[131699.915307] Initializing USB Mass Storage driver...
[131699.915376] scsi5 : SCSI emulation for USB Mass Storage devices
[131699.915422] usb-storage: device found at 3
[131699.915425] usb-storage: waiting for device to settle before scanning
[131699.915433] usbcore: registered new interface driver usb-storage
[131699.915436] USB Mass Storage support registered.
[131704.902460] usb-storage: device scan complete
[131704.909452] scsi 5:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[131704.931373] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[131704.944338] sdb: Write Protect is off
[131704.944342] sdb: Mode Sense: 07 00 00 00
[131704.944345] sdb: assuming drive cache: write through
[131704.963286] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[131704.976261] sdb: Write Protect is off
[131704.976265] sdb: Mode Sense: 07 00 00 00
[131704.976267] sdb: assuming drive cache: write through
[131704.976273]  sdb: sdb1
[131704.991250] sd 5:0:0:0: Attached scsi removable disk sdb
[131704.991301] sd 5:0:0:0: Attached scsi generic sg1 type 0
[131805.845852] usb 2-4: USB disconnect, address 3
[133078.720769] usb 2-4: new full speed USB device using ohci_hcd and address 4
[133078.942278] usb 2-4: configuration #1 chosen from 1 choice
[133078.946745] scsi6 : SCSI emulation for USB Mass Storage devices
[133078.951407] usb-storage: device found at 4
[133078.951412] usb-storage: waiting for device to settle before scanning
[133083.937125] usb-storage: device scan complete
[133083.944115] scsi 6:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[133083.966033] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[133083.979099] sdb: Write Protect is off
[133083.979104] sdb: Mode Sense: 07 00 00 00
[133083.979106] sdb: assuming drive cache: write through
[133083.997949] SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
[133084.010924] sdb: Write Protect is off
[133084.010928] sdb: Mode Sense: 07 00 00 00
[133084.010930] sdb: assuming drive cache: write through
[133084.010935]  sdb: sdb1
[133084.025913] sd 6:0:0:0: Attached scsi removable disk sdb
[133084.025963] sd 6:0:0:0: Attached scsi generic sg1 type 0
robin@robin-desktop:~$ 


```

I'm a newbie here but unless I miss my guess this is it, and your camera should appear as /dev/sdb1 which will need to be mounted to /media/ with a name of your choice.

---

### Post by Robbyx on 2007-06-22
I am not clear what to do next. I tried the disk mounter but it dioes not show the camera. Next I tried editing fstab but can not find the exact wording needed in the file for a usb camera.

Does anyone know the string for a digital camera in fsatb?

---

### Post by Robbyx on 2007-06-23
bump

---

### Post by Robbyx on 2007-08-14
I am still unable to connect my Fujifilm s5000 camera to Linux. I wonder if any one can help me to get it to connect? The details are as above.

---

