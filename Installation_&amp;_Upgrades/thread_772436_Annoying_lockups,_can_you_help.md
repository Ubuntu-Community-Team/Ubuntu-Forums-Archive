---
title: "Annoying lockups, can you help?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Paqman on 2008-04-28
I'm having a lot of annoying lockups. The whole system will lock up within a few seconds of logging in. Needs a hard reset.

I can boot into a stable system with no lockups if I use:  acpi=off noapic nolapic irqpoll, but that leaves me with no USB, which on my mobo also means no sound. Not very helpful, really.

My dmesg suggests to use acpi_use_timer_override and pci=biosirq, but these don't seem to be any help. Where do I go with this?

Running Hardy
AMD Athlon 64 X2 6000
Asus M2N-E SLI
2GB RAM
SATA HD

dmesg:
```

[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=eb83863b-73f3-4d13-96f6-d999763615dd ro quiet splash acpi=off noapic nolapic irqpoll
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1208 pages reserved
[    0.000000]   DMA zone: 2735 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: OEM00000 MPTABLE: Product ID: PROD00000000 MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] I/O APIC #2 at 0xFEC00000.
[    0.000000] Setting APIC routing to flat
[    0.000000] Processors: 2
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515531
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=eb83863b-73f3-4d13-96f6-d999763615dd ro quiet splash acpi=off noapic nolapic irqpoll
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PIT
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.000000] time.c: Detected 3015.501 MHz processor.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ b200000000 size 32 MB
[    0.000000] Aperture too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] Memory: 2054400k/2096000k available (2466k kernel code, 41212k reserved, 1309k data, 316k init)
[    0.000000] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] Calibrating delay using timer specific routine.. 6045.54 BogoMIPS (lpj=12091080)
[    0.000000] Security Framework initialized
[    0.000000] SELinux:  Disabled at boot.
[    0.000000] AppArmor: AppArmor initialized
[    0.000000] Failure registering capabilities with primary security module.
[    0.000000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.000000] Mount-cache hash table entries: 256
[    0.000000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.000000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.000000] CPU 0/0 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 0
[    0.000000] SMP alternatives: switching to UP code
[    0.000000] Early unpacking initramfs... done
[    0.000000] Using local APIC timer interrupts.
[    0.000000] APIC timer calibration result 12564594
[    0.000000] Detected 12.564 MHz APIC timer.
[    0.000000] SMP alternatives: switching to SMP code
[    0.000000] Booting processor 1/2 APIC 0x1
[    0.000000] Initializing CPU#1
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Calibrating delay using timer specific routine.. 6031.04 BogoMIPS (lpj=12062086)
[    0.000000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.000000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.000000] CPU 1/1 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 1
[    0.000000] AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 03
[    0.000000] Brought up 2 CPUs
[    0.000000] CPU0 attaching sched-domain:
[    0.000000]  domain 0: span 03
[    0.000000]   groups: 01 02
[    0.000000]   domain 1: span 03
[    0.000000]    groups: 03
[    0.000000] CPU1 attaching sched-domain:
[    0.000000]  domain 0: span 03
[    0.000000]   groups: 02 01
[    0.000000]   domain 1: span 03
[    0.000000]    groups: 03
[    0.000000] net_namespace: 120 bytes
[    0.000000] Time: 15:28:46  Date: 04/28/08
[    0.000000] NET: Registered protocol family 16
[    0.000000] PCI: Using configuration type 1
[    0.000000] ACPI: Interpreter disabled.
[    0.000000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.000000] pnp: PnP ACPI: disabled
[    0.000000] PCI: Probing PCI hardware
[    0.000000] PCI: Probing PCI hardware (bus 00)
[    0.000000] PCI: Transparent bridge - 0000:00:09.0
[    0.000000] PCI: Using IRQ router default [10de/005e] at 0000:00:00.0
[    0.000000] NET: Registered protocol family 8
[    0.000000] NET: Registered protocol family 20
[    0.000000] AppArmor: AppArmor Filesystem Enabled
[    0.000000] PCI: Bridge: 0000:00:09.0
[    0.000000]   IO window: a000-afff
[    0.000000]   MEM window: fdf00000-fdffffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:0b.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:0c.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:0d.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:0e.0
[    0.000000]   IO window: 9000-9fff
[    0.000000]   MEM window: fa000000-fcffffff
[    0.000000]   PREFETCH window: d0000000-dfffffff
[    0.000000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.000000] NET: Registered protocol family 2
[    0.000000] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.000000] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.000000] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.000000] TCP: Hash tables configured (established 262144 bind 65536)
[    0.000000] TCP reno registered
[    0.000000] checking if image is initramfs... it is
[    0.000000] Freeing initrd memory: 7518k freed
[    0.000000] audit: initializing netlink socket (disabled)
[    0.000000] audit(1209396525.852:1): initialized
[    0.000000] VFS: Disk quotas dquot_6.5.1
[    0.000000] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.000000] io scheduler noop registered
[    0.000000] io scheduler anticipatory registered
[    0.000000] io scheduler deadline registered
[    0.000000] io scheduler cfq registered (default)
[    0.000000] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[    0.000000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    0.000000] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[    0.000000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    0.000000] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[    0.000000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    0.000000] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[    0.000000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    0.000000] Boot video device is 0000:05:00.0
[    0.000000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0b.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0c.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0d.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0e.0:pcie00]
[    0.000000] Real Time Clock Driver v1.12ac
[    0.000000] Linux agpgart interface v0.102
[    0.000000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    0.000000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.000000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.000000] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.000000] PNP: No PS/2 controller found. Probing ports directly.
[    0.000000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.000000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.000000] mice: PS/2 mouse device common for all mice
[    0.000000] cpuidle: using governor ladder
[    0.000000] cpuidle: using governor menu
[    0.000000] NET: Registered protocol family 1
[    0.000000] registered taskstats version 1
[    0.000000]   Magic number: 4:608:488
[    0.000000] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.000000] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.000000] EDD information not available.
[    0.000000] Freeing unused kernel memory: 316k freed
[    0.000000] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.000000] fuse init (API version 7.9)
[    0.000000] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    0.000000] usbcore: registered new interface driver usbfs
[    0.000000] usbcore: registered new interface driver hub
[    0.000000] usbcore: registered new device driver usb
[    0.000000] SCSI subsystem initialized
[    0.000000] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    0.000000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    0.000000] libata version 3.00 loaded.
[    0.000000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.000000] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x1374 @ 0, addr 00:1b:fc:ed:86:5c
[    0.000000] forcedeth 0000:00:0a.0: highdma csum timirq gbit lnktim desc-v3
[    0.000000] PCI: No IRQ known for interrupt pin B of device 0000:00:02.1. Please try using pci=biosirq.
[    0.000000] ehci_hcd 0000:00:02.1: Found HC with no IRQ.  Check BIOS/PCI 0000:00:02.1 setup!
[    0.000000] ehci_hcd 0000:00:02.1: init 0000:00:02.1 fail, -19
[    0.000000] PCI: No IRQ known for interrupt pin A of device 0000:00:02.0. Please try using pci=biosirq.
[    0.000000] ohci_hcd 0000:00:02.0: Found HC with no IRQ.  Check BIOS/PCI 0000:00:02.0 setup!
[    0.000000] ohci_hcd 0000:00:02.0: init 0000:00:02.0 fail, -19
[    0.000000] pata_amd 0000:00:06.0: version 0.3.10
[    0.000000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.000000] scsi0 : pata_amd
[    0.000000] scsi1 : pata_amd
[    0.000000] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
[    0.000000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
[    0.000000] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H552U, US03, max UDMA/33
[    0.000000] ata2.00: configured for UDMA/33
[    0.000000] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552U US03 PQ: 0 ANSI: 5
[    0.000000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    0.000000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    0.000000] sata_nv 0000:00:07.0: version 3.5
[    0.000000] sata_nv 0000:00:07.0: Using ADMA mode
[    0.000000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.000000] scsi2 : sata_nv
[    0.000000] scsi3 : sata_nv
[    0.000000] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 11
[    0.000000] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 11
[    0.000000] Driver 'sr' needs updating - please use bus_type methods
[    0.000000] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[    0.000000] Uniform CD-ROM driver Revision: 3.20
[    0.000000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.000000] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    0.000000] ata3: SATA link down (SStatus 0 SControl 300)
[    0.000000] ata4: SATA link down (SStatus 0 SControl 300)
[    0.000000] sata_nv 0000:00:08.0: Using ADMA mode
[    0.000000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    0.000000] scsi4 : sata_nv
[    0.000000] scsi5 : sata_nv
[    0.000000] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 5
[    0.000000] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 5
[    0.000000] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.000000] ata5.00: ATA-7: ST3160815AS, 3.AAC, max UDMA/133
[    0.000000] ata5.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    0.000000] ata5.00: configured for UDMA/133
[    0.000000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000134ad9f]
[    0.000000] ata6: SATA link down (SStatus 0 SControl 300)
[    0.000000] scsi 4:0:0:0: Direct-Access     ATA      ST3160815AS      3.AA PQ: 0 ANSI: 5
[    0.000000] ata5: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[    0.000000] scsi 4:0:0:0: Attached scsi generic sg1 type 0
[    0.000000] Driver 'sd' needs updating - please use bus_type methods
[    0.000000] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    0.000000] sd 4:0:0:0: [sda] Write Protect is off
[    0.000000] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.000000] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    0.000000] sd 4:0:0:0: [sda] Write Protect is off
[    0.000000] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.000000] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3 sda4
[    0.000000] sd 4:0:0:0: [sda] Attached SCSI disk
[    0.000000] Attempting manual resume
[    0.000000] swsusp: Resume From Partition 8:5
[    0.000000] PM: Checking swsusp image.
[    0.000000] PM: Resume from disk failed.
[    0.000000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    0.000000] EXT3-fs: write access will be enabled during recovery.
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3-fs: sda6: orphan cleanup on readonly fs
[    0.000000] ext3_orphan_cleanup: deleting unreferenced inode 49342
[    0.000000] EXT3-fs: sda6: 1 orphan inode deleted
[    0.000000] EXT3-fs: recovery complete.
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.000000] input: PC Speaker as /devices/platform/pcspkr/input/input2
[    0.000000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[    0.000000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[    0.000000] nvidia: module license 'NVIDIA' taints kernel.
[    0.000000] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[    0.000000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[    0.000000] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[    0.000000] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
[    0.000000] lp0: using parport0 (polling).
[    0.000000] Adding 1052216k swap on /dev/sda5.  Priority:-1 extents:1 across:1052216k
[    0.000000] EXT3 FS on sda6, internal journal
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3 FS on sda3, internal journal
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3 FS on sda4, internal journal
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] ip_tables: (C) 2000-2006 Netfilter Core Team
[    0.000000]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[    0.000000]  CIFS VFS: cifs_mount failed w/return code = -101
[    0.000000]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[    0.000000]  CIFS VFS: cifs_mount failed w/return code = -101
[    0.000000] powernow_k8: Unknown symbol acpi_processor_notify_smm
[    0.000000] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[    0.000000] powernow_k8: Unknown symbol acpi_processor_register_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[    0.000000] ppdev: user-space parallel port driver
[    0.000000] audit(1209392944.204:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4445 profile="/usr/sbin/cupsd" namespace="default"
[    0.000000] Bluetooth: Core ver 2.11
[    0.000000] NET: Registered protocol family 31
[    0.000000] Bluetooth: HCI device and connection manager initialized
[    0.000000] Bluetooth: HCI socket layer initialized
[    0.000000] Bluetooth: L2CAP ver 2.9
[    0.000000] Bluetooth: L2CAP socket layer initialized
[    0.000000] Bluetooth: RFCOMM socket layer initialized
[    0.000000] Bluetooth: RFCOMM TTY layer initialized
[    0.000000] Bluetooth: RFCOMM ver 1.8
[    0.000000] NET: Registered protocol family 17
[    0.000000] NET: Registered protocol family 10
[    0.000000] lo: Disabled Privacy Extensions
[    0.000000] eth0: no IPv6 routers present

```

---

### Post by martrn on 2008-04-28
> **Paqman said:**
> I'm having a lot of annoying lockups. The whole system will lock up within a few seconds of logging in. Needs a hard reset.

I can boot into a stable system with no lockups if I use:  acpi=off noapic nolapic irqpoll, but that leaves me with no USB, which on my mobo also means no sound. Not very helpful, really.

My dmesg suggests to use acpi_use_timer_override and pci=biosirq, but these don't seem to be any help. Where do I go with this?


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996")

Try Launchpad + file a bug report
if ask for package hint type your Linux kernel lockup

makesure you know the kernel you are using (2.6.24-16-generic)
```
uname -r
```
+ what kernel modules are loaded and hardware etc....

---

### Post by Paqman on 2008-04-29
Have done, but I was wondering if anyone had any ideas about getting the USB working. I'd be quite happy to lose acpi, etc while waiting for a proper fix, if only I could get sound and USB working.

---

### Post by martrn on 2008-04-29
> I'm having a lot of annoying lockups. The whole system will lock up within a few seconds of logging in...... Needs a hard reset.Have done, but I was wondering if anyone had any ideas about getting the USB working.... [...] .... I'd be quite happy to lose acpi, etc while waiting for a proper fix, if only I could get sound and USB working.

Its a ubuntu  linux-generic kernel issue....

This is a kind of yes, but no, but yeas kind of answer.  If you compiled you own custom kernel then yes I am sure you could get it working.  However compiling you own kernel is a not an easy thing to do if you system locks up, so would be difficult.  However although that is a point in is not two difficult a thing to do.

This is what I do to optimize my system and make sure its running smooth, and ensure the ubuntu kernel is fixed and my motherboard is working and doesn't conflict with a sony-prio or something (I have a via chipset not sony prio), and thus rebuild my kernel.

To rebuild my kernel by just changing a few switches to try to optimize it a bit for my matching a little advice given to me and that from from [http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835") I tried to rebuild my kernel. useing that as a rough guide.  I try/do :-
```

uname -r
sudo apt-get update
sudo apt-get install build-essential gcc libqt3-mt-dev
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
sudo apt-get upgrade
cd /usr/src
ls
sudo tar --bzip2 -xvf linux-source-2.6.24.tar.bz2
ls
sudo ln -s /usr/src/linux-source-2.6.24 /usr/src/linux
cd /usr/src/linux
sudo make oldconfig
sudo make menuconfig
```
I change a few switches here to optimize it for my machine.  And then I continued :-

```
sudo make-kpkg clean
sudo make-kpkg --initrd --append-to-version=-martamdx86athXP kernel_image kernel_headers
```

At this point I go for a cup of hot choclate, and then came back.  And then I go off to read a book and then come back and then I left it because it becones clear this is going to take some time.

After several hours... I did....
```
cd /usr/src
ls
sudo dpkg -i linux-image-2.6.24.9-martamdx86athXP_2.6.24.9-martamdx86athXP-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.24.9-martamdx86athXP_2.6.24.9-martamdx86athXP-10.00.Custom_i386.deb
sudo reboot
```

When I boot up via grub and err the kernel I compiled I can only boot into a terminal with no X11/Xwindows.  I have an nvidia driver the other two ubuntu built kernels one for the server and on generic, and they boot fine into x11/xserver.

So then I have to rebuild my nvidia kernel module.......
And then rebuild the sound kernel module.....

---

### Post by Paqman on 2008-04-30
It's worth a crack, I guess...

---

