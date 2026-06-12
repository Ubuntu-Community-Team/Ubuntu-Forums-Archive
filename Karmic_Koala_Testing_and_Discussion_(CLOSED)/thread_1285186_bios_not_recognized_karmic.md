---
title: "bios not recognized karmic"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Supr-me on 2009-10-07
Dear all, 

Today I installed the Karmic Koala beta release on a Acer TravelMate 4001 laptop, everything works fine except for one thing: If you shutdown the laptop it not actually shuts down but enters a state where it seems to have shutdown but a cursor keeps blinking and you can't do anything but hold the power button to give it the final kick.

There is one thing worth mentioning: After grub there is a message that the bios is not recognized, see below for the dmesg output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-11-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu3) ) #36-Ubuntu SMP Fri Sep 25 06:37:51 UTC 2009 (Ubuntu 2.6.31-11.36-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fee0000 (usable)
[    0.000000]  BIOS-e820: 000000001fee0000 - 000000001feec000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feec000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x1fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 01FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fee0000 (usable)
[    0.000000]  modified: 000000001fee0000 - 000000001feec000 (ACPI data)
[    0.000000]  modified: 000000001feec000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  modified: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001fee0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001fee0000 page 4k
[    0.000000] kernel direct mapping tables up to 1fee0000 @ 7000-c000
[    0.000000] RAMDISK: 178ed000 - 17f6717b
[    0.000000] ACPI: RSDP 000f62c0 00014 (v00 ACER  )
[    0.000000] ACPI: RSDT 1fee6205 00030 (v01 ACER   Kestrel  20021012  LTP 00000000)
[    0.000000] ACPI: FACP 1feebf2c 00074 (v01 ACER   Kestrel  20021012 PTL  00000050)
[    0.000000] ACPI: DSDT 1fee6235 05CF7 (v01 ACER   Kestrel  20021012 MSFT 0100000E)
[    0.000000] ACPI: FACS 1fefcfc0 00040
[    0.000000] ACPI: HPET 1feebfa0 00038 (v01 ACER   Kestrel  20021012 PTL  00000000)
[    0.000000] ACPI: BOOT 1feebfd8 00028 (v01 ACER   Kestrel  20021012  LTP 00000001)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fee0000
[    0.000000]   low ram: 0 - 1fee0000
[    0.000000]   node 0 low ram: 00000000 - 1fee0000
[    0.000000]   node 0 bootmap 00008000 - 0000bfdc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000089f080]    TEXT DATA BSS ==> [0000100000 - 000089f080]
[    0.000000]   #4 [00178ed000 - 0017f6717b]          RAMDISK ==> [00178ed000 - 0017f6717b]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008a0000 - 00008a3170]              BRK ==> [00008a0000 - 00008a3170]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fee0
[    0.000000]   HighMem  0x0001fee0 -> 0x0001fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fee0
[    0.000000] On node 0 totalpages: 130683
[    0.000000] free_area_init_node: node 0, pgdat c077b840, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125698 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0 is invalid
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec10000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1402000, static data 35068 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129661
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-11-generic root=UUID=04b62f2d-5469-4d3a-bfbe-a653cc26576c ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2615680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 500792k/523136k available (4543k kernel code, 21604k reserved, 2128k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe06e0000 - 0xff7fe000   ( 497 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdfee0000   ( 510 MB)
[    0.000000]       .init : 0xc0785000 - 0xc080c000   ( 540 kB)
[    0.000000]       .data : 0xc056ff84 - 0xc07841a8   (2128 kB)
[    0.000000]       .text : 0xc0100000 - 0xc056ff84   (4543 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1498.654 MHz processor.
[    0.000969] Console: colour VGA+ 80x25
[    0.000974] console [tty0] enabled
[    0.001033] Calibrating delay loop (skipped), value calculated using timer frequency.. 2997.30 BogoMIPS (lpj=5994616)
[    0.001056] Security Framework initialized
[    0.001087] AppArmor: AppArmor initialized
[    0.001096] Mount-cache hash table entries: 512
[    0.001251] Initializing cgroup subsys ns
[    0.001257] Initializing cgroup subsys cpuacct
[    0.001263] Initializing cgroup subsys memory
[    0.001274] Initializing cgroup subsys freezer
[    0.001277] Initializing cgroup subsys net_cls
[    0.001295] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001299] CPU: L2 cache: 1024K
[    0.001310] Performance Counters: 
[    0.001313] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.001316] no hardware sampling interrupt available.
[    0.001319] p6 PMU driver.
[    0.001337] ... version:                 0
[    0.001339] ... bit width:               32
[    0.001342] ... generic counters:        2
[    0.001345] ... value mask:              00000000ffffffff
[    0.001347] ... max period:              000000007fffffff
[    0.001350] ... fixed-purpose counters:  0
[    0.001353] ... counter mask:            0000000000000003
[    0.001358] Checking 'hlt' instruction... OK.
[    0.016942] SMP alternatives: switching to UP code
[    0.024013] Freeing SMP alternatives: 19k freed
[    0.024023] ACPI: Core revision 20090521
[    0.034990] ACPI: setting ELCR to 0200 (from 0440)
[    0.036075] weird, boot CPU (#0) not listed by the BIOS.
[    0.036078] SMP motherboard not detected.
[    0.036082] Local APIC not detected. Using dummy APIC emulation.
[    0.036084] SMP disabled
[    0.036234] Brought up 1 CPUs
[    0.036237] Total of 1 processors activated (2997.30 BogoMIPS).
[    0.036251] CPU0 attaching NULL sched-domain.
[    0.036509] Booting paravirtualized kernel on bare hardware
[    0.036844] regulator: core version 0.5
[    0.036869] Time: 19:26:51  Date: 10/07/09
[    0.036937] NET: Registered protocol family 16
[    0.037104] EISA bus registered
[    0.037124] ACPI: bus type pci registered
[    0.038262] PCI: PCI BIOS revision 2.10 entry at 0xfd782, last bus=2
[    0.038265] PCI: Using configuration type 1 for base access
[    0.040056] bio: create slab <bio-0> at 0
[    0.040907] ACPI: EC: Look up EC in DSDT
[    0.045179] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.053858] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.364061] ACPI: Interpreter enabled
[    0.364067] ACPI: (supports S0 S3 S4 S5)
[    0.364090] ACPI: Using PIC for interrupt routing
[    0.369351] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.369355] ACPI: EC: driver started in poll mode
[    0.369422] ACPI: Power Resource [PFN0] (off)
[    0.369463] ACPI: Power Resource [PFN1] (off)
[    0.370125] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.370882] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.370937] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[    0.371110] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.371160] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.371212] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.371270] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0000000-0xd00003ff]
[    0.371325] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.371330] pci 0000:00:1d.7: PME# disabled
[    0.371413] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.371418] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.371442] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.371449] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.371457] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.371464] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.371472] pci 0000:00:1f.1: reg 20 io port: [0x1860-0x186f]
[    0.371480] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.371529] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.371570] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.371577] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.371585] pci 0000:00:1f.5: reg 18 32bit mmio: [0xd0000c00-0xd0000dff]
[    0.371592] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xd0000800-0xd00008ff]
[    0.371620] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.371625] pci 0000:00:1f.5: PME# disabled
[    0.371654] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.371661] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.371696] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.371701] pci 0000:00:1f.6: PME# disabled
[    0.371739] pci 0000:01:00.0: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.371745] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.371752] pci 0000:01:00.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]
[    0.371768] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.371787] pci 0000:01:00.0: supports D1 D2
[    0.371820] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.371825] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
[    0.371830] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.371863] pci 0000:02:02.0: reg 10 32bit mmio: [0xd0204000-0xd0205fff]
[    0.371889] pci 0000:02:02.0: reg 30 32bit mmio: [0x000000-0x003fff]
[    0.371905] pci 0000:02:02.0: supports D1 D2
[    0.371908] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.371913] pci 0000:02:02.0: PME# disabled
[    0.371945] pci 0000:02:04.0: reg 10 32bit mmio: [0xd0208000-0xd0208fff]
[    0.371986] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold
[    0.371991] pci 0000:02:04.0: PME# disabled
[    0.372034] pci 0000:02:06.0: reg 10 32bit mmio: [0xd0209000-0xd0209fff]
[    0.372053] pci 0000:02:06.0: supports D1 D2
[    0.372056] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.372061] pci 0000:02:06.0: PME# disabled
[    0.372093] pci 0000:02:06.2: reg 10 32bit mmio: [0xd020a000-0xd020a7ff]
[    0.372101] pci 0000:02:06.2: reg 14 32bit mmio: [0xd0200000-0xd0203fff]
[    0.372140] pci 0000:02:06.2: supports D1 D2
[    0.372143] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot
[    0.372148] pci 0000:02:06.2: PME# disabled
[    0.372178] pci 0000:02:06.3: reg 10 32bit mmio: [0xd0206000-0xd0207fff]
[    0.372219] pci 0000:02:06.3: supports D1 D2
[    0.372222] pci 0000:02:06.3: PME# supported from D0 D1 D2 D3hot
[    0.372227] pci 0000:02:06.3: PME# disabled
[    0.372263] pci 0000:00:1e.0: transparent bridge
[    0.372268] pci 0000:00:1e.0: bridge io port: [0x4000-0x4fff]
[    0.372274] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0200000-0xd05fffff]
[    0.372303] pci_bus 0000:00: on NUMA node 0
[    0.372308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.372488] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.372514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.375185] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    0.375307] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.375426] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.375545] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    0.375663] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.375781] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.375900] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    0.376032] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.376273] SCSI subsystem initialized
[    0.376344] libata version 3.00 loaded.
[    0.376439] usbcore: registered new interface driver usbfs
[    0.376460] usbcore: registered new interface driver hub
[    0.376494] usbcore: registered new device driver usb
[    0.376659] ACPI: WMI: Mapper loaded
[    0.376662] PCI: Using ACPI for IRQ routing
[    0.376850] Bluetooth: Core ver 2.15
[    0.376883] NET: Registered protocol family 31
[    0.376885] Bluetooth: HCI device and connection manager initialized
[    0.376889] Bluetooth: HCI socket layer initialized
[    0.376892] NetLabel: Initializing
[    0.376895] NetLabel:  domain hash size = 128
[    0.376897] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.376916] NetLabel:  unlabeled traffic allowed by default
[    0.379215] pnp: PnP ACPI init
[    0.379248] ACPI: bus type pnp registered
[    0.382965] pnp: PnP ACPI: found 9 devices
[    0.382970] ACPI: ACPI bus type pnp unregistered
[    0.382975] PnPBIOS: Disabled by ACPI PNP
[    0.382993] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.383000] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.383004] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.383008] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.383012] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.383016] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.383021] system 00:04: ioport range 0x1c0-0x1cf has been reserved
[    0.383025] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.383030] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.383034] system 00:04: ioport range 0x610-0x61f has been reserved
[    0.383040] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.383044] system 00:04: iomem range 0xff800000-0xffbfffff has been reserved
[    0.383049] system 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.383053] system 00:04: iomem range 0x0-0x9ffff could not be reserved
[    0.383058] system 00:04: iomem range 0xe0000-0xfffff could not be reserved
[    0.383062] system 00:04: iomem range 0xdf800-0xdffff could not be reserved
[    0.417789] AppArmor: AppArmor Filesystem Enabled
[    0.417828] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.417832] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.417838] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
[    0.417843] pci 0000:00:01.0:   PREFETCH window: 0xd8000000-0xdfffffff
[    0.417851] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.417855] pci 0000:02:06.0:   IO window: 0x004000-0x0040ff
[    0.417860] pci 0000:02:06.0:   IO window: 0x004400-0x0044ff
[    0.417865] pci 0000:02:06.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.417871] pci 0000:02:06.0:   MEM window: 0x28000000-0x2bffffff
[    0.417876] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.417880] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
[    0.417887] pci 0000:00:1e.0:   MEM window: 0xd0200000-0xd05fffff
[    0.417892] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x25ffffff
[    0.417909] pci 0000:00:1e.0: setting latency timer to 64
[    0.417917] pci 0000:02:06.0: enabling device (0104 -> 0107)
[    0.418118] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    0.418122] PCI: setting IRQ 10 as level-triggered
[    0.418128] pci 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    0.418138] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.418142] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.418146] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.418150] pci_bus 0000:01: resource 1 mem: [0xd0100000-0xd01fffff]
[    0.418154] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdfffffff]
[    0.418158] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.418161] pci_bus 0000:02: resource 1 mem: [0xd0200000-0xd05fffff]
[    0.418165] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x25ffffff]
[    0.418169] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.418172] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.418176] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.418180] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.418184] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.418188] pci_bus 0000:03: resource 3 mem: [0x28000000-0x2bffffff]
[    0.418242] NET: Registered protocol family 2
[    0.418382] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.418778] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.418912] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.419044] TCP: Hash tables configured (established 16384 bind 16384)
[    0.419048] TCP reno registered
[    0.419152] NET: Registered protocol family 1
[    0.419236] Trying to unpack rootfs image as initramfs...
[    0.662680] Freeing initrd memory: 6632k freed
[    0.669116] Simple Boot Flag at 0x37 set to 0x1
[    0.669153] cpufreq-nforce2: No nForce2 chipset.
[    0.669197] Scanning for low memory corruption every 60 seconds
[    0.669419] audit: initializing netlink socket (disabled)
[    0.669461] type=2000 audit(1254943611.668:1): initialized
[    0.681512] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.683671] VFS: Disk quotas dquot_6.5.2
[    0.683754] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.684615] fuse init (API version 7.12)
[    0.684740] msgmni has been set to 991
[    0.685018] alg: No test for stdrng (krng)
[    0.685034] io scheduler noop registered
[    0.685037] io scheduler anticipatory registered
[    0.685040] io scheduler deadline registered (default)
[    0.685106] io scheduler cfq registered
[    0.685194] pci 0000:01:00.0: Boot video device
[    0.685325] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.685355] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.685518] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.685524] ACPI: Power Button [PWRF]
[    0.685599] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.908101] ACPI: Lid Switch [LID]
[    0.908170] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.908174] ACPI: Sleep Button [SLPB]
[    0.908341] fan PNP0C0B:00: registered as cooling_device0
[    0.908349] ACPI: Fan [FAN0] (off)
[    0.908479] fan PNP0C0B:01: registered as cooling_device1
[    0.908486] ACPI: Fan [FAN1] (off)
[    0.908647] Marking TSC unstable due to TSC halts in idle
[    0.908667] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.908690] processor LNXCPU:00: registered as cooling_device2
[    0.908695] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.912077] Switched to high resolution mode on CPU 0
[    0.988211] thermal LNXTHERM:01: registered as thermal_zone0
[    0.988222] ACPI: Thermal Zone [THRM] (39 C)
[    0.988308] ACPI: SBS HC: EC = 0xdf849480, offset = 0x18, query_bit = 0x20
[    1.220063] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (off-line)
[    6.532109] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[    7.044108] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT1] (battery absent)
[    7.100069] isapnp: Scanning for PnP cards...
[    7.453799] isapnp: No Plug & Play device found
[    7.455333] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    7.455461] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    7.456047] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    7.456053] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    7.456062] serial 0000:00:1f.6: PCI INT B disabled
[    7.457288] brd: module loaded
[    7.457903] loop: module loaded
[    7.458002] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    7.458138] ata_piix 0000:00:1f.1: version 2.13
[    7.458153] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    7.458158] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    7.458348] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    7.458352] PCI: setting IRQ 6 as level-triggered
[    7.458357] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    7.458402] ata_piix 0000:00:1f.1: setting latency timer to 64
[    7.458490] scsi0 : ata_piix
[    7.458603] scsi1 : ata_piix
[    7.459841] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    7.459846] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    7.461168] Fixed MDIO Bus: probed
[    7.461218] PPP generic driver version 2.4.2
[    7.461336] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    7.461545] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    7.461551] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    7.461568] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    7.461573] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    7.461635] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    7.465542] ehci_hcd 0000:00:1d.7: debug port 1
[    7.465549] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    7.465665] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xd0000000
[    7.480025] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    7.480142] usb usb1: configuration #1 chosen from 1 choice
[    7.480181] hub 1-0:1.0: USB hub found
[    7.480192] hub 1-0:1.0: 6 ports detected
[    7.480271] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    7.480297] uhci_hcd: USB Universal Host Controller Interface driver
[    7.480522] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    7.480527] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    7.480536] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    7.480540] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    7.480599] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    7.480622] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001800
[    7.480729] usb usb2: configuration #1 chosen from 1 choice
[    7.480763] hub 2-0:1.0: USB hub found
[    7.480772] hub 2-0:1.0: 2 ports detected
[    7.481006] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    7.481011] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    7.481018] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    7.481022] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    7.481061] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    7.481082] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001820
[    7.481186] usb usb3: configuration #1 chosen from 1 choice
[    7.481221] hub 3-0:1.0: USB hub found
[    7.481229] hub 3-0:1.0: 2 ports detected
[    7.481285] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    7.481293] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    7.481297] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    7.481339] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    7.481361] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001840
[    7.481476] usb usb4: configuration #1 chosen from 1 choice
[    7.481510] hub 4-0:1.0: USB hub found
[    7.481518] hub 4-0:1.0: 2 ports detected
[    7.481634] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    7.484434] i8042.c: Detected active multiplexing controller, rev 1.1.
[    7.485420] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.485427] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    7.485460] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    7.485490] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    7.485522] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    7.485635] mice: PS/2 mouse device common for all mice
[    7.485821] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    7.485839] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    7.485998] device-mapper: uevent: version 1.0.3
[    7.486122] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    7.486183] device-mapper: multipath: version 1.1.0 loaded
[    7.486186] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.486352] EISA: Probing bus 0 at eisa.0
[    7.486359] Cannot allocate resource for EISA slot 1
[    7.486363] Cannot allocate resource for EISA slot 2
[    7.486366] Cannot allocate resource for EISA slot 3
[    7.486369] Cannot allocate resource for EISA slot 4
[    7.486387] EISA: Detected 0 cards.
[    7.486490] cpuidle: using governor ladder
[    7.486567] cpuidle: using governor menu
[    7.487299] TCP cubic registered
[    7.487534] NET: Registered protocol family 10
[    7.488180] lo: Disabled Privacy Extensions
[    7.488639] NET: Registered protocol family 17
[    7.488660] Bluetooth: L2CAP ver 2.13
[    7.488662] Bluetooth: L2CAP socket layer initialized
[    7.488666] Bluetooth: SCO (Voice Link) ver 0.6
[    7.488668] Bluetooth: SCO socket layer initialized
[    7.488701] Bluetooth: RFCOMM TTY layer initialized
[    7.488705] Bluetooth: RFCOMM socket layer initialized
[    7.488708] Bluetooth: RFCOMM ver 1.11
[    7.489135] Using IPI No-Shortcut mode
[    7.489209] PM: Resume from disk failed.
[    7.489223] registered taskstats version 1
[    7.489356]   Magic number: 13:938:444
[    7.489443] rtc_cmos 00:01: setting system clock to 2009-10-07 19:26:58 UTC (1254943618)
[    7.489447] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    7.489449] EDD information not available.
[    7.519563] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    7.584029] hub 2-0:1.0: over-current change on port 1
[    7.624272] ata2.01: NODEV after polling detection
[    7.624730] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD4A, max UDMA/100
[    7.624734] ata1.00: 117210240 sectors, multi 16: LBA48 
[    7.632627] ata2.00: ATAPI: QSI     DVDRW SDW-042, DX70, max UDMA/33
[    7.640616] ata1.00: configured for UDMA/100
[    7.640737] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[    7.640867] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.640909] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    7.640958] sd 0:0:0:0: [sda] Write Protect is off
[    7.640962] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.640988] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.641128]  sda:
[    7.648480] ata2.00: configured for UDMA/33
[    7.654349] scsi 1:0:0:0: CD-ROM            QSI      DVDRW SDW-042    DX70 PQ: 0 ANSI: 5
[    7.660608] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[    7.660612] Uniform CD-ROM driver Revision: 3.20
[    7.660709] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.660752] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    7.670377]  sda1 sda2 <
[    7.688030] hub 2-0:1.0: over-current change on port 2
[    7.697510]  sda5 >
[    7.697760] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.697777] Freeing unused kernel memory: 540k freed
[    7.698128] Write protecting the kernel text: 4544k
[    7.698173] Write protecting the kernel read-only data: 1832k
[    8.149273] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    8.208102] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    8.208135] b44.c:v2.0
[    8.208255] ohci1394 0000:02:06.2: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    8.228821] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:47:d9:73
[    8.264052] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d020a000-d020a7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    8.411377] PM: Starting manual resume from disk
[    8.411382] PM: Resume from partition 8:5
[    8.411384] PM: Checking hibernation image.
[    8.411606] PM: Resume from disk failed.
[    8.440413] EXT4-fs (sda1): barriers enabled
[    8.455083] kjournald2 starting: pid 269, dev sda1:8, commit interval 5 seconds
[    8.455096] EXT4-fs (sda1): delayed allocation enabled
[    8.455099] EXT4-fs: file extents enabled
[    8.464884] EXT4-fs: mballoc enabled
[    8.464901] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    9.415421] type=1505 audit(1254943620.422:2): operation="profile_load" pid=289 name=/usr/lib/cups/backend/cups-pdf
[    9.416444] type=1505 audit(1254943620.426:3): operation="profile_load" pid=289 name=/usr/sbin/cupsd
[    9.440833] type=1505 audit(1254943620.450:4): operation="profile_load" pid=290 name=/usr/sbin/tcpdump
[    9.443060] type=1505 audit(1254943620.450:5): operation="profile_load" pid=291 name=/usr/share/gdm/guest-session/Xsession
[    9.481561] type=1505 audit(1254943620.490:6): operation="profile_load" pid=292 name=/usr/bin/evince
[    9.493564] type=1505 audit(1254943620.502:7): operation="profile_load" pid=292 name=/usr/bin/evince-previewer
[    9.500882] type=1505 audit(1254943620.510:8): operation="profile_load" pid=292 name=/usr/bin/evince-thumbnailer
[    9.519171] type=1505 audit(1254943620.526:9): operation="profile_load" pid=293 name=/sbin/dhclient3
[    9.520036] type=1505 audit(1254943620.530:10): operation="profile_load" pid=293 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.520447] type=1505 audit(1254943620.530:11): operation="profile_load" pid=293 name=/usr/lib/connman/scripts/dhclient-script
[    9.536183] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00001daab5]
[   20.421611] udev: starting version 147
[   25.428786] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:03/input/input5
[   25.428877] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.728589] acer-wmi: Acer Laptop ACPI-WMI Extras
[   25.728606] acer-wmi: [B]No or unsupported WMI interface, unable to load
[   26.608725] irda_init()[/B]
[   26.608743] NET: Registered protocol family 23
[   26.649779] acerhdf: Acer Aspire One Fan driver, v.0.5.16
[   26.649785] acerhdf: **unknown (unsupported) BIOS version Acer/TravelMate 4000/3A10, please report, aborting!**
[   26.662618] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.751482] lp: driver loaded but no devices found
[   26.832910] Linux agpgart interface v0.103
[   26.832987] intel_rng: FWH not detected
[   26.844655] lib80211: common routines for IEEE802.11 drivers
[   26.844659] lib80211_crypt: registered algorithm 'NULL'
[   26.845917] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.935157] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   26.970537] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   27.032276] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   27.032304] nsc-ircc, chip->init
[   27.032312] nsc-ircc, Found chip at base=0x164e
[   27.032334] nsc-ircc, driver loaded (Dag Brattli)
[   27.032645] nsc_ircc_open(), can't get iobase of 0x2f8
[   27.032670] nsc-ircc, Found chip at base=0x164e
[   27.032691] nsc-ircc, driver loaded (Dag Brattli)
[   27.032695] nsc_ircc_open(), can't get iobase of 0x2f8
[   27.033225] nsc-ircc 00:08: disabled
[   27.172854] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   27.172858] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   27.238038] tifm_7xx1 0000:02:06.3: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[   27.250721] yenta_cardbus 0000:02:06.0: CardBus bridge found [1025:0064]
[   27.250736] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   27.250741] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   27.250744] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   27.250749] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01a21b22, devctl 0x64
[   27.340186] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   27.340192] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   27.466001] [drm] Initialized drm 1.1.0 20060810
[   27.480561] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x08b8, PCI irq 10
[   27.480566] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   27.480571] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   27.480580] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   27.480585] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: clean.
[   27.480839] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd05fffff
[   27.480843] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x25ffffff
[   27.482127] ipw2200 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   27.485195] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   27.485254] ipw2200 0000:02:04.0: firmware: requesting ipw2200-bss.fw
[   27.687953] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   27.730983] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   28.010427] [drm] radeon default to kernel modesetting DISABLED.
[   28.010555] pci 0000:01:00.0: power state changed by ACPI to D0
[   28.010566] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[   28.011077] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[   28.145620] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   28.280615] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   28.282128] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   28.282731] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   28.283234] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   28.284393] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   28.470120] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k 
[   28.471381] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   28.471425] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   28.522090] EXT4-fs (sda1): internal journal on sda1:8
[   28.788035] intel8x0_measure_ac97_clock: measured 54092 usecs (2606 samples)
[   28.788040] intel8x0: clocking to 48000
[   30.301378] type=1505 audit(1254936441.310:12): operation="profile_replace" pid=725 name=/usr/lib/cups/backend/cups-pdf
[   30.302285] type=1505 audit(1254936441.310:13): operation="profile_replace" pid=725 name=/usr/sbin/cupsd
[   30.317436] type=1505 audit(1254936441.326:14): operation="profile_replace" pid=726 name=/usr/sbin/tcpdump
[   30.319236] type=1505 audit(1254936441.326:15): operation="profile_replace" pid=727 name=/usr/share/gdm/guest-session/Xsession
[   30.333768] type=1505 audit(1254936441.342:16): operation="profile_replace" pid=765 name=/usr/bin/evince
[   30.357034] type=1505 audit(1254936441.366:17): operation="profile_replace" pid=765 name=/usr/bin/evince-previewer
[   30.364441] type=1505 audit(1254936441.374:18): operation="profile_replace" pid=765 name=/usr/bin/evince-thumbnailer
[   30.372832] type=1505 audit(1254936441.382:19): operation="profile_replace" pid=768 name=/sbin/dhclient3
[   30.373556] type=1505 audit(1254936441.382:20): operation="profile_replace" pid=768 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   30.373969] type=1505 audit(1254936441.382:21): operation="profile_replace" pid=768 name=/usr/lib/connman/scripts/dhclient-script
[   30.391113] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.584854] lib80211_crypt: registered algorithm 'CCMP'
[   31.605001] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   31.605019] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[   31.605055] pci 0000:01:00.0: putting AGP V2 device into 1x mode
[   31.674458] padlock: VIA PadLock not detected.
[   31.958486] ttyS1: LSR safety check engaged!
[   32.007882] [drm] Setting GART location based on new memory map
[   32.007890] [drm] Loading R300 Microcode
[   32.007932] [drm] Num pipes: 1
[   32.007938] [drm] writeback test succeeded in 1 usecs
[   32.734240] ppdev: user-space parallel port driver
[   41.300028] eth1: no IPv6 routers present
[   58.416238] Clocksource tsc unstable (delta = -368307584 ns)


```

Could anybody give me a solution to this? There is one particular thing I already highlighted in the dmesg output and think it's relevant: "unknown (unsupported) BIOS version Acer/TravelMate 4000/3A10, please report, aborting!" I would like to report it, but I have no clue where :P

Is this in anyway related to the trouble I get when shutting down?
Please let me know if there is additional information needed to fix this problem.

Thanks in advance!

---

### Post by moster on 2009-10-07
You are running beta state Ubuntu. There is 90% chance THAT is reason. I would try jaunty to see if it shutdown good. If he report error too, only then you have a real problem.

---

### Post by Sylslay on 2009-10-07
Karmic usesr now, 
I got the same sotry for 1,2,3 rd October,,
than doing upgrate, the problem is gone,
Now 7 th october , linux is update and erything working fine like in Juanty,
but beter firfox performance wahan play flash view

todays upgrate (in softwerw  source change from Main server instead local contry)
where : 2.6.31-12-generic #40-Ubuntu SMP Wed Oct 7 04:14:43 UTC 2009 i686 GNU/Linux, and latest xorg, and intel graphic driver, works fine with 845 chipset.

---

