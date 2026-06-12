---
title: "Ubuntu 8.04 can't detect all my IDE harddisks"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by xylitol on 2008-05-18
My PC has 1 SATA, 2 PATA, 1 DVD-ROM.

Previously Mepis detected well on all my hard drives as sda (SATA), hda (primary master), hdc (secondary master). The DVD-ROM is secondary slave.

When I tried to install Ubuntu 8.04 into it, the Live CD could not detect all my drives,
sda -> sda (fine)
hda -> (missing)
hdc -> sdb

See below for the most suspicious messages found in dmesg command, which looks like complaining slow response from the device.

Anyone know the possible cause of slow response? 
Both the BIOS and the installed Mepis can detect it (primary master, hda) well.

```
[  175.126545] pata_via 0000:00:0f.1: version 0.3.3
[  175.128725] scsi2 : pata_via
[  175.129605] scsi3 : pata_via
[  175.129650] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[  175.129654] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[COLOR="Red"][  180.314255] ata3: port is slow to respond, please be patient (Status 0xd0)
[  185.123038] ata3: SRST failed (errno=-16)[/COLOR]
[  185.830544] ata4.00: ATA-6: ST380023A, 3.31, max UDMA/100
[  185.830549] ata4.00: 156301488 sectors, multi 16: LBA 
[  185.830569] ata4.01: ATAPI: JLMS XJ-HD166S, DS1E, max UDMA/33
[  185.830581] ata4.00: limited to UDMA/33 due to 40-wire cable
[  185.846817] ata4.00: configured for UDMA/33
[  186.009921] ata4.01: configured for UDMA/33
[  186.010031] scsi 3:0:0:0: Direct-Access     ATA      ST380023A        3.31 PQ: 0 ANSI: 5
```



Thanks. :)


ps. Further see below for the FULL dmesg output, just in case it is useful.

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005bee0000 (usable)
[    0.000000]  BIOS-e820: 000000005bee0000 - 000000005bee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005bee3000 - 000000005bef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005bef0000 - 000000005bf00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 574MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5070
[    0.000000] Entering add_active_range(0, 0, 376544) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   376544
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   376544
[    0.000000] On node 0 totalpages: 376544
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1149 pages used for memmap
[    0.000000]   HighMem zone: 146019 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] Processor #0 15:12 APIC version 17
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] I/O APIC #3 Version 17 at 0xFECC0000.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5bf00000:84100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 373603
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz acpi=off noapic file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --  locale=zh_TW
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1600.062 MHz processor.
[  170.110702] Console: colour VGA+ 80x25
[  170.110706] console [tty0] enabled
[  170.111215] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[  170.112096] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[  170.173387] Memory: 1480716k/1506176k available (2157k kernel code, 24360k reserved, 998k data, 364k init, 588672k highmem)
[  170.173397] virtual kernel memory layout:
[  170.173398]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[  170.173399]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  170.173401]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[  170.173402]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[  170.173403]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[  170.173405]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[  170.173406]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[  170.173409] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  170.173454] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[  170.253360] Calibrating delay using timer specific routine.. 3203.46 BogoMIPS (lpj=6406924)
[  170.253391] Security Framework initialized
[  170.253399] SELinux:  Disabled at boot.
[  170.253417] AppArmor: AppArmor initialized
[  170.253421] Failure registering capabilities with primary security module.
[  170.253430] Mount-cache hash table entries: 512
[  170.253565] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[  170.253575] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  170.253577] CPU: L2 Cache: 256K (64 bytes/line)
[  170.253581] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[  170.253592] Compat vDSO mapped to ffffe000.
[  170.253605] Checking 'hlt' instruction... OK.
[  170.269659] SMP alternatives: switching to UP code
[  170.270925] Freeing SMP alternatives: 11k freed
[  170.271061] Early unpacking initramfs... done
[  170.670365] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
[  170.670389] Total of 1 processors activated (3203.46 BogoMIPS).
[  170.884469] Brought up 1 CPUs
[  170.884491] CPU0 attaching sched-domain:
[  170.884493]  domain 0: span 01
[  170.884495]   groups: 01
[  170.884671] net_namespace: 64 bytes
[  170.884677] Booting paravirtualized kernel on bare hardware
[  170.885198] Time: 21:28:52  Date: 05/18/08
[  170.885224] NET: Registered protocol family 16
[  170.885402] EISA bus registered
[  170.893934] PCI: PCI BIOS revision 3.00 entry at 0xfb820, last bus=3
[  170.893936] PCI: Using configuration type 1
[  170.893938] Setting up standard PCI resources
[  170.896598] ACPI: Interpreter disabled.
[  170.896602] Linux Plug and Play Support v0.97 (c) Adam Belay
[  170.896629] pnp: PnP ACPI: disabled
[  170.896633] PnPBIOS: Scanning system for PnP BIOS support...
[  170.896916] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc450
[  170.896923] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc480, dseg 0xf0000
[  170.897708] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[  170.897898] PCI: Probing PCI hardware
[  170.897903] PCI: Probing PCI hardware (bus 00)
[  170.968397] NET: Registered protocol family 8
[  170.968400] NET: Registered protocol family 20
[  170.968469] AppArmor: AppArmor Filesystem Enabled
[  170.968511] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[  170.968515] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[  170.968518] system 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[  170.968522] system 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[  170.968525] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[  170.968532] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[  170.968535] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[  170.968538] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
[  170.968541] system 00:08: iomem range 0xd1000-0xd3fff has been reserved
[  170.968908] PCI: Bridge: 0000:00:01.0
[  170.968911]   IO window: c000-cfff
[  170.968916]   MEM window: dd000000-deffffff
[  170.968920]   PREFETCH window: c0000000-cfffffff
[  170.968925] PCI: Bridge: 0000:00:02.0
[  170.968927]   IO window: e000-efff
[  170.968932]   MEM window: dfc00000-dfcfffff
[  170.968935]   PREFETCH window: dfb00000-dfbfffff
[  170.968939] PCI: Bridge: 0000:00:03.0
[  170.968942]   IO window: d000-dfff
[  170.968947]   MEM window: dfe00000-dfefffff
[  170.968951]   PREFETCH window: dfd00000-dfdfffff
[  170.968969] PCI: Setting latency timer of device 0000:00:01.0 to 64
[  170.968984] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  170.969002] PCI: Setting latency timer of device 0000:00:03.0 to 64
[  170.969014] NET: Registered protocol family 2
[  170.972296] Time: tsc clocksource has been installed.
[  171.004334] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[  171.004671] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[  171.005909] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[  171.006539] TCP: Hash tables configured (established 131072 bind 65536)
[  171.006543] TCP reno registered
[  171.016384] checking if image is initramfs... it is
[  171.786134] Freeing initrd memory: 7665k freed
[  171.786756] audit: initializing netlink socket (disabled)
[  171.786770] audit(1211146132.508:1): initialized
[  171.786927] highmem bounce pool size: 64 pages
[  171.788614] VFS: Disk quotas dquot_6.5.1
[  171.788687] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  171.788873] io scheduler noop registered
[  171.788875] io scheduler anticipatory registered
[  171.788878] io scheduler deadline registered
[  171.788888] io scheduler cfq registered (default)
[  171.788901] PCI: VIA PCI bridge detected. Disabling DAC.
[  171.788976] Boot video device is 0000:01:00.0
[  171.789087] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  171.789122] assign_interrupt_mode Found MSI capability
[  171.789166] Allocate Port Service[0000:00:02.0:pcie00]
[  171.789199] Allocate Port Service[0000:00:02.0:pcie02]
[  171.789272] PCI: Setting latency timer of device 0000:00:03.0 to 64
[  171.789313] assign_interrupt_mode Found MSI capability
[  171.789360] Allocate Port Service[0000:00:03.0:pcie00]
[  171.789389] Allocate Port Service[0000:00:03.0:pcie02]
[  171.789581] isapnp: Scanning for PnP cards...
[  172.143257] isapnp: No Plug & Play device found
[  172.170120] Real Time Clock Driver v1.12ac
[  172.170189] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  172.170304] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  172.170922] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  172.171631] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  172.171698] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[  172.171792] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[  172.172101] serio: i8042 KBD port at 0x60,0x64 irq 1
[  172.172106] serio: i8042 AUX port at 0x60,0x64 irq 12
[  172.174763] mice: PS/2 mouse device common for all mice
[  172.174877] EISA: Probing bus 0 at eisa.0
[  172.174916] EISA: Detected 0 cards.
[  172.174919] cpuidle: using governor ladder
[  172.174921] cpuidle: using governor menu
[  172.175016] NET: Registered protocol family 1
[  172.175045] Using IPI No-Shortcut mode
[  172.175075] registered taskstats version 1
[  172.175169]   Magic number: 8:500:500
[  172.175321] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[  172.175323] EDD information not available.
[  172.175591] Freeing unused kernel memory: 364k freed
[  172.206461] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[  173.477419] fuse init (API version 7.9)
[  173.525225] thermal: Unknown symbol acpi_processor_set_thermal_limit
[  173.924642] SCSI subsystem initialized
[  173.988418] libata version 3.00 loaded.
[  174.003840] usbcore: registered new interface driver usbfs
[  174.003862] usbcore: registered new interface driver hub
[  174.035739] usbcore: registered new device driver usb
[  174.055772] sata_via 0000:00:0f.0: version 2.3
[  174.055827] sata_via 0000:00:0f.0: routed to hard irq line 11
[  174.077324] scsi0 : sata_via
[  174.085337] USB Universal Host Controller Interface driver v3.0
[  174.095995] scsi1 : sata_via
[  174.096044] ata1: SATA max UDMA/133 cmd 0xff00 ctl 0xfe00 bmdma 0xfb00 irq 11
[  174.096047] ata2: SATA max UDMA/133 cmd 0xfd00 ctl 0xfc00 bmdma 0xfb08 irq 11
[  174.146982] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[  174.146989] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[  174.299309] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  174.355597] FDC 0 is a post-1991 82077
[  174.490397] ata1.00: ATA-7: WDC WD3200YS-01PGB0, 21.00M21, max UDMA/133
[  174.490403] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
[  174.495415] ata1.00: configured for UDMA/133
[  174.698715] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[  174.710111] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200YS-01P 21.0 PQ: 0 ANSI: 5
[  174.710336] uhci_hcd 0000:00:10.0: UHCI Host Controller
[  174.710560] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[  174.710586] uhci_hcd 0000:00:10.0: irq 10, io base 0x0000f900
[  174.710729] usb usb1: configuration #1 chosen from 1 choice
[  174.710755] hub 1-0:1.0: USB hub found
[  174.710761] hub 1-0:1.0: 2 ports detected
[  174.814652] uhci_hcd 0000:00:10.1: UHCI Host Controller
[  174.814678] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[  174.814701] uhci_hcd 0000:00:10.1: irq 10, io base 0x0000f800
[  174.814823] usb usb2: configuration #1 chosen from 1 choice
[  174.814848] hub 2-0:1.0: USB hub found
[  174.814853] hub 2-0:1.0: 2 ports detected
[  174.918488] uhci_hcd 0000:00:10.2: UHCI Host Controller
[  174.918514] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[  174.918537] uhci_hcd 0000:00:10.2: irq 11, io base 0x0000f700
[  174.918656] usb usb3: configuration #1 chosen from 1 choice
[  174.918679] hub 3-0:1.0: USB hub found
[  174.918685] hub 3-0:1.0: 2 ports detected
[  175.018587] Driver 'sd' needs updating - please use bus_type methods
[  175.018672] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[  175.018685] sd 0:0:0:0: [sda] Write Protect is off
[  175.018688] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  175.018704] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  175.018749] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[  175.018758] sd 0:0:0:0: [sda] Write Protect is off
[  175.018761] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  175.018774] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  175.018778]  sda:<6>uhci_hcd 0000:00:10.3: UHCI Host Controller
[  175.022360] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[  175.022385] uhci_hcd 0000:00:10.3: irq 11, io base 0x0000f600
[  175.022548] usb usb4: configuration #1 chosen from 1 choice
[  175.022572] hub 4-0:1.0: USB hub found
[  175.022578] hub 4-0:1.0: 2 ports detected
[  175.022600]  sda1 sda2 < sda5 sda6 sda7 >
[  175.054813] sd 0:0:0:0: [sda] Attached SCSI disk
[  175.061519] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  175.126545] pata_via 0000:00:0f.1: version 0.3.3
[  175.128725] scsi2 : pata_via
[  175.129605] scsi3 : pata_via
[  175.129650] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[  175.129654] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[  180.314255] ata3: port is slow to respond, please be patient (Status 0xd0)
[  185.123038] ata3: SRST failed (errno=-16)
[  185.830544] ata4.00: ATA-6: ST380023A, 3.31, max UDMA/100
[  185.830549] ata4.00: 156301488 sectors, multi 16: LBA 
[  185.830569] ata4.01: ATAPI: JLMS XJ-HD166S, DS1E, max UDMA/33
[  185.830581] ata4.00: limited to UDMA/33 due to 40-wire cable
[  185.846817] ata4.00: configured for UDMA/33
[  186.009921] ata4.01: configured for UDMA/33
[  186.010031] scsi 3:0:0:0: Direct-Access     ATA      ST380023A        3.31 PQ: 0 ANSI: 5
[  186.010440] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[  186.010453] sd 3:0:0:0: [sdb] Write Protect is off
[  186.010456] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  186.010472] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  186.010520] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[  186.010530] sd 3:0:0:0: [sdb] Write Protect is off
[  186.010532] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  186.010547] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  186.010551]  sdb: sdb1
[  186.019086] sd 3:0:0:0: [sdb] Attached SCSI disk
[  186.019121] sd 3:0:0:0: Attached scsi generic sg1 type 0
[  186.019883] scsi 3:0:1:0: CD-ROM            JLMS     XJ-HD166S        DS1E PQ: 0 ANSI: 5
[  186.019952] scsi 3:0:1:0: Attached scsi generic sg2 type 5
[  186.020109] ehci_hcd 0000:00:10.4: EHCI Host Controller
[  186.020138] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[  186.020183] ehci_hcd 0000:00:10.4: irq 5, io mem 0xdffff000
[  186.029697] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  186.029818] usb usb5: configuration #1 chosen from 1 choice
[  186.029844] hub 5-0:1.0: USB hub found
[  186.029850] hub 5-0:1.0: 8 ports detected
[  186.041714] Driver 'sr' needs updating - please use bus_type methods
[  186.042978] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[  186.042984] Uniform CD-ROM driver Revision: 3.20
[  186.043040] sr 3:0:1:0: Attached scsi CD-ROM sr0
[  186.133992] eth0: VIA Rhine II at 0xdfffe000, 00:30:18:a0:36:87, IRQ 10.
[  186.134704] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[  186.416348] kjournald starting.  Commit interval 5 seconds
[  186.416364] EXT3-fs: mounted filesystem with ordered data mode.
[  186.765571] ISO 9660 Extensions: Microsoft Joliet Level 3
[  186.789324] ISO 9660 Extensions: RRIP_1991A
[  186.994864] Registering unionfs 1.4
[  186.994868] unionfs: debugging is not enabled
[  187.008463] loop: module loaded
[  187.253068] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[  254.512399] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  254.693400] Linux agpgart interface v0.102
[  254.884237] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  255.143248] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  255.196122] agpgart: Detected VIA VT3336 chipset
[  255.200387] agpgart: AGP aperture is 128M @ 0xd0000000
[  256.247572] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[  257.602812] parport_pc 00:0d: reported by Plug and Play BIOS
[  257.602865] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  258.947808] PCI: Setting latency timer of device 0000:00:11.5 to 64
[  261.769313] Adding 2096440k swap on /dev/sda5.  Priority:-1 extents:1 across:2096440k
[  263.700531] ip_tables: (C) 2000-2006 Netfilter Core Team
[  265.896789] powernow_k8: Unknown symbol acpi_processor_notify_smm
[  265.896844] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[  265.896941] powernow_k8: Unknown symbol acpi_processor_register_performance
[  265.940713] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  265.940765] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  265.940926] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  265.941001] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  268.885434] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  269.120000] lp0: using parport0 (interrupt-driven).
[  269.212575] ppdev: user-space parallel port driver
[  277.063813] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  277.260765] Bluetooth: Core ver 2.11
[  277.275868] NET: Registered protocol family 31
[  277.275874] Bluetooth: HCI device and connection manager initialized
[  277.275879] Bluetooth: HCI socket layer initialized
[  277.468486] Bluetooth: L2CAP ver 2.9
[  277.468491] Bluetooth: L2CAP socket layer initialized
[  277.635721] Bluetooth: RFCOMM socket layer initialized
[  277.635740] Bluetooth: RFCOMM TTY layer initialized
[  277.635742] Bluetooth: RFCOMM ver 1.8
[  285.998179] NET: Registered protocol family 17
[  289.435078] [drm] Initialized drm 1.1.0 20060810
[  289.506212] [drm] Initialized via 2.11.1 20070202 on minor 0
[  289.512127] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  289.512153] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  289.512236] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  291.696263] NET: Registered protocol family 10
[  291.697161] lo: Disabled Privacy Extensions
[  302.234657] eth0: no IPv6 routers present
[  355.987386] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO

```

---

### Post by Pumalite on 2008-05-18
Best is to have all SATA or all IDE. 2nd best: install both OS's in your first drive and use the rest for storage. Checkk your connections and cables, just in case.

---

### Post by juah on 2008-05-29
If you have via chipsets on your motherboard, it could be the still experimental pata_via driver that's causing the problem. I couln't solve the problem without recompiling the kernel having removed pata_via and substituting it with via82cxxx.

---

### Post by juah on 2008-05-29
If you have via chipsets on your motherboard, it could be the still experimental pata_via driver that's causing the problem. I couldn't solve the problem without recompiling the kernel having removed pata_via and substituting it with via82cxxx.

---

### Post by slayer^_^ on 2008-06-05
Today we discovered on launchpad the final solution:

_**!!! THE IDE CABLE !!!**_

the new modules absolutely require a 80-wire ide cable (the one with coloured pins), everyone of us who experienced this bug had 40-wire ide-cables...

...and of course a good cable plugging (blue plug on motherboard, gray on slave and black on master) and a correct setting of the jumpers of the hard disks (disk set as master if it is connected to the black plug of the cable, ecc ecc).

A manually setting of the dma speed and pio mode in the motherboard bios is also a good idea.

Best regards.

---

### Post by Pumalite on 2008-06-05
It's best to have CD-DVD Drive as 2nd Master.

---

### Post by xylitol on 2008-06-06
> **slayer^_^ said:**
> Today we discovered on launchpad the final solution:

_**!!! THE IDE CABLE !!!**_

...and of course a good cable plugging (blue plug on motherboard, gray on slave and black on master) and a correct setting of the jumpers of the hard disks (disk set as master if it is connected to the black plug of the cable, ecc ecc).




Thanks! 
Is the color of the plugs related? 
I thought IDE devices would only be affected by the jumper settings...

---

### Post by juah on 2008-06-10
> **slayer^_^ said:**
> Today we discovered on launchpad the final solution:

_**!!! THE IDE CABLE !!!**_

the new modules absolutely require a 80-wire ide cable (the one with coloured pins), everyone of us who experienced this bug had 40-wire ide-cables...

...and of course a good cable plugging (blue plug on motherboard, gray on slave and black on master) and a correct setting of the jumpers of the hard disks (disk set as master if it is connected to the black plug of the cable, ecc ecc).

A manually setting of the dma speed and pio mode in the motherboard bios is also a good idea.

Best regards.


Yes ! It actually works. Having the right cables (I DID have 40 wire cable and a 80 wire cable attached wrong way) and properly connected all devices are recognized with pata_via. Only that the naming convention is a bit weird: starting from serial ata (sda), then first ide master (sdb) and slave (sdc). I quess this doesn't matter using uuids ? cdrw as ide2 master working also.

---

