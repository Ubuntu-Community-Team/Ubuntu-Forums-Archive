---
title: "Failure during Lucid Lynx installation"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by steyr22 on 2010-05-17
I have downloaded the ISO files several times, burnt to disk at different speeds, validated data and yet still cannot install Ubuntu 10.04.

Install crashes at 43% of Copying New Files (from any of my disks - says I/O error - unable to continue.

System Log file shows:

May 17 21:26:44 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
May 17 21:26:44 ubuntu kernel: [    0.000000] MTRR default type: uncachable
May 17 21:26:44 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
May 17 21:26:44 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
May 17 21:26:44 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
May 17 21:26:44 ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
May 17 21:26:44 ubuntu kernel: [    0.000000]   C8000-FFFFF uncachable
May 17 21:26:44 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
May 17 21:26:44 ubuntu kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
May 17 21:26:44 ubuntu kernel: [    0.000000]   1 base 040000000 mask FF0000000 write-back
May 17 21:26:44 ubuntu kernel: [    0.000000]   2 base 0E0000000 mask FFC000000 write-combining
May 17 21:26:44 ubuntu kernel: [    0.000000]   3 disabled
May 17 21:26:44 ubuntu kernel: [    0.000000]   4 disabled
May 17 21:26:44 ubuntu kernel: [    0.000000]   5 disabled
May 17 21:26:44 ubuntu kernel: [    0.000000]   6 disabled
May 17 21:26:44 ubuntu kernel: [    0.000000]   7 disabled
May 17 21:26:44 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
May 17 21:26:44 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
May 17 21:26:44 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
May 17 21:26:44 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
May 17 21:26:44 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
May 17 21:26:44 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 17 21:26:44 ubuntu kernel: [    0.000000] On node 0 totalpages: 327551
May 17 21:26:44 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c11ce200
May 17 21:26:44 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 17 21:26:44 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May 17 21:26:44 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
May 17 21:26:44 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
May 17 21:26:44 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
May 17 21:26:44 ubuntu kernel: [    0.000000]   HighMem zone: 784 pages used for memmap
May 17 21:26:44 ubuntu kernel: [    0.000000]   HighMem zone: 99554 pages, LIFO batch:31
May 17 21:26:44 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 17 21:26:44 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
May 17 21:26:44 ubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
May 17 21:26:44 ubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
May 17 21:26:44 ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
May 17 21:26:44 ubuntu kernel: [    0.080001] CPU0 attaching NULL sched-domain.
May 17 21:26:44 ubuntu kernel: [    0.110517] ACPI: EC: Look up EC in DSDT
May 17 21:26:44 ubuntu kernel: [    0.124642] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
May 17 21:26:44 ubuntu kernel: [    0.124849] pci 0000:00:01.1: reg 10 io port: [0xdc00-0xdc1f]
May 17 21:26:44 ubuntu kernel: [    0.124918] pci 0000:00:02.0: reg 10 32bit mmio: [0xe9087000-0xe9087fff]
May 17 21:26:44 ubuntu kernel: [    0.124951] pci 0000:00:02.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.124982] pci 0000:00:02.1: reg 10 32bit mmio: [0xe9082000-0xe9082fff]
May 17 21:26:44 ubuntu kernel: [    0.125015] pci 0000:00:02.1: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125053] pci 0000:00:02.2: reg 10 32bit mmio: [0xe9083000-0xe90830ff]
May 17 21:26:44 ubuntu kernel: [    0.125091] pci 0000:00:02.2: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125130] pci 0000:00:04.0: reg 10 32bit mmio: [0xe9086000-0xe9086fff]
May 17 21:26:44 ubuntu kernel: [    0.125136] pci 0000:00:04.0: reg 14 io port: [0xe000-0xe007]
May 17 21:26:44 ubuntu kernel: [    0.125166] pci 0000:00:04.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125198] pci 0000:00:05.0: reg 10 32bit mmio: [0xe9000000-0xe907ffff]
May 17 21:26:44 ubuntu kernel: [    0.125230] pci 0000:00:05.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125256] pci 0000:00:06.0: reg 10 io port: [0xe400-0xe4ff]
May 17 21:26:44 ubuntu kernel: [    0.125262] pci 0000:00:06.0: reg 14 io port: [0xd000-0xd07f]
May 17 21:26:44 ubuntu kernel: [    0.125268] pci 0000:00:06.0: reg 18 32bit mmio: [0xe9080000-0xe9080fff]
May 17 21:26:44 ubuntu kernel: [    0.125294] pci 0000:00:06.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125357] pci 0000:00:09.0: reg 20 io port: [0xf000-0xf00f]
May 17 21:26:44 ubuntu kernel: [    0.125403] pci 0000:00:0d.0: reg 10 32bit mmio: [0xe9084000-0xe90847ff]
May 17 21:26:44 ubuntu kernel: [    0.125410] pci 0000:00:0d.0: reg 14 32bit mmio: [0xe9085000-0xe908503f]
May 17 21:26:44 ubuntu kernel: [    0.125440] pci 0000:00:0d.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125528] pci 0000:01:08.0: reg 10 io port: [0x9000-0x90ff]
May 17 21:26:44 ubuntu kernel: [    0.125536] pci 0000:01:08.0: reg 14 32bit mmio: [0xe8000000-0xe80003ff]
May 17 21:26:44 ubuntu kernel: [    0.125564] pci 0000:01:08.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
May 17 21:26:44 ubuntu kernel: [    0.125583] pci 0000:01:08.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125626] pci 0000:01:0a.0: reg 10 io port: [0x9400-0x941f]
May 17 21:26:44 ubuntu kernel: [    0.125674] pci 0000:01:0a.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125709] pci 0000:01:0b.0: reg 10 io port: [0x9800-0x9807]
May 17 21:26:44 ubuntu kernel: [    0.125717] pci 0000:01:0b.0: reg 14 io port: [0x9c00-0x9c03]
May 17 21:26:44 ubuntu kernel: [    0.125724] pci 0000:01:0b.0: reg 18 io port: [0xa000-0xa007]
May 17 21:26:44 ubuntu kernel: [    0.125732] pci 0000:01:0b.0: reg 1c io port: [0xa400-0xa403]
May 17 21:26:44 ubuntu kernel: [    0.125740] pci 0000:01:0b.0: reg 20 io port: [0xa800-0xa80f]
May 17 21:26:44 ubuntu kernel: [    0.125747] pci 0000:01:0b.0: reg 24 32bit mmio: [0xe8001000-0xe80011ff]
May 17 21:26:44 ubuntu kernel: [    0.125755] pci 0000:01:0b.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
May 17 21:26:44 ubuntu kernel: [    0.125774] pci 0000:01:0b.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125808] pci 0000:00:08.0: bridge io port: [0x9000-0xafff]
May 17 21:26:44 ubuntu kernel: [    0.125812] pci 0000:00:08.0: bridge 32bit mmio: [0xe7000000-0xe8ffffff]
May 17 21:26:44 ubuntu kernel: [    0.125862] pci 0000:03:00.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
May 17 21:26:44 ubuntu kernel: [    0.125870] pci 0000:03:00.0: reg 14 io port: [0xc000-0xc0ff]
May 17 21:26:44 ubuntu kernel: [    0.125877] pci 0000:03:00.0: reg 18 32bit mmio: [0xe6000000-0xe600ffff]
May 17 21:26:44 ubuntu kernel: [    0.125896] pci 0000:03:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
May 17 21:26:44 ubuntu kernel: [    0.125924] pci 0000:03:00.0: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.125964] pci 0000:03:00.1: reg 10 32bit mmio: [0xe6010000-0xe601ffff]
May 17 21:26:44 ubuntu kernel: [    0.126007] pci 0000:03:00.1: supports D1 D2
May 17 21:26:44 ubuntu kernel: [    0.126047] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
May 17 21:26:44 ubuntu kernel: [    0.126051] pci 0000:00:1e.0: bridge 32bit mmio: [0xe5000000-0xe6ffffff]
May 17 21:26:44 ubuntu kernel: [    0.126055] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
May 17 21:26:44 ubuntu kernel: [    0.126065] pci_bus 0000:00: on NUMA node 0
May 17 21:26:44 ubuntu kernel: [    0.126070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 17 21:26:44 ubuntu kernel: [    0.126199] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May 17 21:26:44 ubuntu kernel: [    0.126470] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
May 17 21:26:44 ubuntu kernel: [    0.184605] libata version 3.00 loaded.
May 17 21:26:44 ubuntu kernel: [    0.226199] pci 0000:00:08.0: setting latency timer to 64
May 17 21:26:44 ubuntu kernel: [    0.226207] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
May 17 21:26:44 ubuntu kernel: [    0.226210] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
May 17 21:26:44 ubuntu kernel: [    0.226213] pci_bus 0000:01: resource 0 io:  [0x9000-0xafff]
May 17 21:26:44 ubuntu kernel: [    0.226216] pci_bus 0000:01: resource 1 mem: [0xe7000000-0xe8ffffff]
May 17 21:26:44 ubuntu kernel: [    0.226219] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x500fffff]
May 17 21:26:44 ubuntu kernel: [    0.226222] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
May 17 21:26:44 ubuntu kernel: [    0.226225] pci_bus 0000:03: resource 1 mem: [0xe5000000-0xe6ffffff]
May 17 21:26:44 ubuntu kernel: [    0.226228] pci_bus 0000:03: resource 2 pref mem [0xd0000000-0xdfffffff]
May 17 21:26:44 ubuntu kernel: [    0.282883] pci 0000:03:00.0: Boot video device
May 17 21:26:44 ubuntu kernel: [    2.464273] pata_acpi 0000:00:09.0: setting latency timer to 64
May 17 21:26:44 ubuntu kernel: [    2.465098]   alloc irq_desc for 22 on node -1
May 17 21:26:44 ubuntu kernel: [    2.465100]   alloc kstat_irqs on node -1
May 17 21:26:44 ubuntu kernel: [    2.465128] ehci_hcd 0000:00:02.2: setting latency timer to 64
May 17 21:26:44 ubuntu kernel: [    2.465220] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
May 17 21:26:44 ubuntu kernel: [    2.509089]   alloc irq_desc for 21 on node -1
May 17 21:26:44 ubuntu kernel: [    2.509091]   alloc kstat_irqs on node -1
May 17 21:26:44 ubuntu kernel: [    2.509106] ohci_hcd 0000:00:02.0: setting latency timer to 64
May 17 21:26:44 ubuntu kernel: [    2.598282]   alloc irq_desc for 20 on node -1
May 17 21:26:44 ubuntu kernel: [    2.598284]   alloc kstat_irqs on node -1
May 17 21:26:44 ubuntu kernel: [    2.598298] ohci_hcd 0000:00:02.1: setting latency timer to 64
May 17 21:26:44 ubuntu kernel: [    2.735931] PM: Resume from disk failed.
May 17 21:26:44 ubuntu kernel: [    3.209964] forcedeth 0000:00:04.0: setting latency timer to 64
May 17 21:26:44 ubuntu kernel: [    3.210022] nv_probe: set workaround bit for reversed mac addr
May 17 21:26:44 ubuntu kernel: [    3.244578]   alloc irq_desc for 18 on node -1
May 17 21:26:44 ubuntu kernel: [    3.244581]   alloc kstat_irqs on node -1
May 17 21:26:44 ubuntu kernel: [    3.255077] sata_sil 0000:01:0b.0: version 2.4
May 17 21:26:44 ubuntu kernel: [    3.269033] usb-storage: device found at 2
May 17 21:26:44 ubuntu kernel: [    3.269035] usb-storage: waiting for device to settle before scanning
May 17 21:26:44 ubuntu kernel: [    3.289097] usb-storage: device found at 3
May 17 21:26:44 ubuntu kernel: [    3.289099] usb-storage: waiting for device to settle before scanning
May 17 21:26:44 ubuntu kernel: [    3.729121] pata_amd 0000:00:09.0: version 0.4.1
May 17 21:26:44 ubuntu kernel: [    3.729180] pata_amd 0000:00:09.0: setting latency timer to 64
May 17 21:26:44 ubuntu kernel: [    3.734828] ohci1394 0000:00:0d.0: setting latency timer to 64
May 17 21:26:44 ubuntu kernel: [    3.896537] ata3: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (20:600:0x13)
May 17 21:26:44 ubuntu kernel: [    3.937480] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May 17 21:26:44 ubuntu kernel: [    3.937702] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 17 21:26:44 ubuntu kernel: [    4.100436] ata4: nv_mode_filter: 0x1f39f&0x739f->0x739f, BIOS=0x7000 (0xc600c000) ACPI=0x701f (60:600:0x13)
May 17 21:26:44 ubuntu kernel: [    4.120515] sr 5:0:0:0: Attached scsi CD-ROM sr0
May 17 21:26:44 ubuntu kernel: [    4.184682]   alloc irq_desc for 19 on node -1
May 17 21:26:44 ubuntu kernel: [    4.184684]   alloc kstat_irqs on node -1
May 17 21:26:44 ubuntu kernel: [    4.190684]   alloc irq_desc for 24 on node -1
May 17 21:26:44 ubuntu kernel: [    4.190686]   alloc kstat_irqs on node -1
May 17 21:26:44 ubuntu kernel: [    4.190698] radeon 0000:03:00.0: irq 24 for MSI/MSI-X
May 17 21:26:44 ubuntu kernel: [    4.469939] vga16fb: initializing
May 17 21:26:44 ubuntu kernel: [    5.172152] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000717c6d]
May 17 21:26:44 ubuntu kernel: [    8.268282] usb-storage: device scan complete
May 17 21:26:44 ubuntu kernel: [    8.288263] usb-storage: device scan complete
May 17 21:26:44 ubuntu kernel: [    8.297872] sd 3:0:0:1: [sde] Mode Sense: 00 00 00 00
May 17 21:26:44 ubuntu kernel: [   10.939723] ISO 9660 Extensions: Microsoft Joliet Level 3
May 17 21:26:44 ubuntu kernel: [   10.982082] ISO 9660 Extensions: RRIP_1991A
May 17 21:26:48 ubuntu kernel: [   66.781893] psmouse serio1: ID: 10 00 64
May 17 21:26:54 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1:1.1
May 17 21:26:54 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.2/usb1/1-1
May 17 21:26:54 ubuntu udev-configure-printer: Device vendor/product is 04B8:081A
May 17 21:26:54 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1:1.1/usb/lp0
May 17 21:26:54 ubuntu udev-configure-printer: failed to claim interface
May 17 21:26:54 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.2/usb1/1-1
May 17 21:26:54 ubuntu udev-configure-printer: MFG:EPSON MDL:Stylus Photo RX530 SERN:- serial:C22P20509141852420
May 17 21:26:55 ubuntu kernel: [   73.399455]   alloc irq_desc for 16 on node -1
May 17 21:26:55 ubuntu kernel: [   73.399457]   alloc kstat_irqs on node -1
May 17 21:26:55 ubuntu kernel: [   73.463126] Intel ICH 0000:00:06.0: setting latency timer to 64
May 17 21:26:56 ubuntu udev-configure-printer: failed to connect to CUPS server; giving up
May 17 21:26:58 ubuntu kernel: [   76.341966] 0000:01:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
May 17 21:27:05 ubuntu kernel: [   83.560016] eth0: no IPv6 routers present
May 17 21:27:05 ubuntu udev-configure-printer: add /module/lp
May 17 21:27:05 ubuntu udev-configure-printer: add /devices/pnp0/00:0c/printer/lp0
May 17 21:27:09 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1:1.1
May 17 21:27:09 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.2/usb1/1-1
May 17 21:27:09 ubuntu udev-configure-printer: Device vendor/product is 04B8:081A
May 17 21:27:09 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1:1.1/usb/lp0
May 17 21:27:09 ubuntu udev-configure-printer: failed to claim interface
May 17 21:27:09 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.2/usb1/1-1
May 17 21:27:09 ubuntu udev-configure-printer: MFG:EPSON MDL:Stylus Photo RX530 SERN:- serial:C22P20509141852420
May 17 21:27:13 ubuntu udev-configure-printer: URI matches without serial number: usb://EPSON/Stylus%20Photo%20RX530
May 17 21:27:13 ubuntu udev-configure-printer: No serial number URI matches so using those without
May 17 21:27:13 ubuntu udev-configure-printer: About to add queue for usb://EPSON/Stylus%20Photo%20RX530
May 17 11:57:03 ubuntu udev-add-printer: add_queue: URIs=['usb://EPSON/Stylus%20Photo%20RX530']
May 17 11:57:03 ubuntu udev-add-printer: D-Bus method call failed: org.freedesktop.DBus.Error.ServiceUnknown: The name com.redhat.NewPrinterNotification was not provided by any .service files
May 17 11:57:28 ubuntu kernel: [  120.040935] <3>00 ff ff ff ff ff ff 00 0e 11 47 14 12 06 ab ca  ..........G.....
May 17 11:57:28 ubuntu kernel: [  120.040938] <3>11 0c 01 03 68 24 1b a7 ea e4 91 a2 53 49 9a 24  ....h$......SI.$
May 17 11:57:28 ubuntu kernel: [  120.040941] <3>0f 48 4d a0 43 10 31 59 45 59 61 59 81 99 a9 4f  .HM.C.1YEYaY...O
May 17 11:57:28 ubuntu kernel: [  120.040943] <3>01 01 01 01 01 01 86 3d 00 c0 51 00 30 40 40 a0  .......=..Q.0@@.
May 17 11:57:28 ubuntu kernel: [  120.040946] <3>13 00 5e 06 11 00 00 1e 00 00 00 fd 00 32 a0 1e  ..^..........2..
May 17 11:57:28 ubuntu kernel: [  120.040949] <3>60 15 00 0a 20 20 20 20 20 20 00 00 00 fc 00 43  `...      .....C
May 17 11:57:28 ubuntu kernel: [  120.040951] <3>4f 4d 50 41 51 20 39 35 30 30 0a 20 00 00 00 0d  OMPAQ 9500. ....
May 17 11:57:28 ubuntu kernel: [  120.040954] <3>00 02 01 1a 05 22 02 eb 13 f0 00 07 03 1d 00 81  ....."..........
May 17 11:57:58 ubuntu udev-add-printer: PPD: gutenprint.5.2://escp2-rx510/simple; Status: 1
May 17 11:58:02 ubuntu rtkit-daemon[3254]: Sucessfully called chroot.
May 17 11:58:02 ubuntu rtkit-daemon[3254]: Sucessfully dropped privileges.
May 17 11:58:02 ubuntu rtkit-daemon[3254]: Sucessfully limited resources.
May 17 11:58:02 ubuntu rtkit-daemon[3254]: Running.
May 17 11:58:02 ubuntu rtkit-daemon[3254]: Watchdog thread running.
May 17 11:58:02 ubuntu rtkit-daemon[3254]: Canary thread running.
May 17 11:58:20 ubuntu ubiquity[3225]: debconffilter_done: ubi-language (current: ubi-language)
May 17 11:58:55 ubuntu ubiquity[3225]: debconffilter_done: ubi-timezone (current: ubi-timezone)
May 17 11:59:01 ubuntu ubiquity[3225]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
May 17 12:01:41 ubuntu ubiquity[3225]: debconffilter_done: ubi-partman (current: ubi-partman)
May 17 12:02:06 ubuntu ubiquity[3225]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
May 17 12:02:24 ubuntu ubiquity[3225]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
May 17 12:02:26 ubuntu ubiquity[3225]: debconffilter_done: ubi-summary (current: ubi-summary)
May 17 12:02:35 ubuntu ubiquity[3225]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
May 17 12:02:38 ubuntu ubiquity[3225]: debconffilter_done: ubi-summary (current: ubi-summary)
May 17 12:02:54 ubuntu ubiquity[3225]: debconffilter_done: ubiquity.components.partman_commit (current: None)
May 17 12:05:52 ubuntu ubiquity[3225]: debconffilter_done: ubiquity.components.install (current: None)
May 17 12:06:29 ubuntu kernel: [  661.224070] <3>00 ff ff ff ff ff ff 00 0e 11 47 14 12 06 ab ca  ..........G.....
May 17 12:06:29 ubuntu kernel: [  661.224073] <3>11 0c 01 03 68 24 1b a7 ea e4 91 a2 53 49 9a 24  ....h$......SI.$
May 17 12:06:29 ubuntu kernel: [  661.224076] <3>0f 48 4d a0 43 00 31 59 45 59 61 5b 81 99 a9 4f  .HM.C.1YEYa[...O
May 17 12:06:29 ubuntu kernel: [  661.224078] <3>01 01 01 01 01 01 86 3d 00 c0 51 00 30 40 40 a0  .......=..Q.0@@.
May 17 12:06:29 ubuntu kernel: [  661.224081] <3>13 00 5e 06 11 00 00 1e 00 00 00 fd 00 32 a0 1e  ..^..........2..
May 17 12:06:29 ubuntu kernel: [  661.224084] <3>60 15 00 0a 20 20 20 20 20 20 00 00 00 fc 00 43  `...      .....C
May 17 12:06:29 ubuntu kernel: [  661.224087] <3>4f 4d 50 41 51 20 39 35 30 30 0a 20 00 00 00 0d  OMPAQ 9500. ....
May 17 12:06:29 ubuntu kernel: [  661.224089] <3>00 02 01 1a 05 22 02 eb 13 f0 00 07 03 1d 00 81  ....."..........
May 17 12:06:29 ubuntu kernel: [  661.329931] <3>00 ff ff ff ff ff ff 00 0e 11 47 14 12 06 ab ca  ..........G.....
May 17 12:06:29 ubuntu kernel: [  661.329934] <3>11 0c 01 03 68 24 1b a7 ea e4 91 a2 53 49 9a 24  ....h$......SI.$
May 17 12:06:29 ubuntu kernel: [  661.329937] <3>0f 48 4d a0 43 00 31 59 45 59 61 79 81 99 a9 4f  .HM.C.1YEYay...O
May 17 12:06:29 ubuntu kernel: [  661.329939] <3>01 01 01 01 01 01 86 3d 00 c0 51 00 30 40 40 a0  .......=..Q.0@@.
May 17 12:06:29 ubuntu kernel: [  661.329942] <3>13 00 5e 06 11 00 00 1e 00 00 00 fd 00 32 a0 1e  ..^..........2..
May 17 12:06:29 ubuntu kernel: [  661.329945] <3>60 15 00 0a 20 20 20 20 20 20 00 00 00 fc 00 43  `...      .....C
May 17 12:06:29 ubuntu kernel: [  661.329947] <3>4f 4d 50 41 51 20 39 35 30 30 0a 20 00 00 00 0d  OMPAQ 9500. ....
May 17 12:06:29 ubuntu kernel: [  661.329950] <3>00 02 01 1a 05 22 02 eb 13 f0 00 07 03 1d 00 81  ....."..........
May 17 12:19:32 ubuntu kernel: [ 1443.738631] UDP: bad checksum. From 208.105.163.98:28810 to 192.168.2.2:12287 ulen 73



HELP!  Any suggestions?

---

### Post by kansasnoob on 2010-05-17
First of all be aware of this:

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](http://www.ubuntu.com/getubuntu/releasenotes/1004#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

**Boot options hidden by default on Desktop and Netbook CDs **

> The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is noninteractive by default. To configure advanced boot options, press any key at the first boot screen.   

So, if you display the boot options at the beginning have you selected "Check CD for defects"?

It takes several minutes to run. I ask because of this:

> May 17 12:19:32 ubuntu kernel: [ 1443.738631] UDP: **[COLOR="Red"]bad checksum[/COLOR]**. From 208.105.163.98:28810 to 192.168.2.2:12287 ulen 73


I'm also curious if you've been able to "run" the Live Desktop without attempting to install?

---

