---
title: "Extremely slow boot speed"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by warbl on 2009-10-11
In jaunty my boot speed was about 11 seconds. After getting karmic, the boot speed is 5-7 minutes. I see the white ubuntu logo, than the screen goes black, for a while, than I see the login screen, so I'm seeing xflash, but no uflash. I'm using an old dell laptop, intel centrino, and a legacy ati graphics card. I think it's the latter that's been causing problems, as I've noticed other people reporting difficulties with ati drivers. Yesterday I noticed sometimes the screen would turn yellow, with tons of black lines, so I think it's problem with graphics.

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-13-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu7) ) #44-Ubuntu SMP Sat Oct 10 15:27:55 UTC 2009 (Ubuntu 2.6.31-13.44-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd1800 (usable)
[    0.000000]  BIOS-e820: 000000001ffd1800 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x1ffd1 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 0FEDA0000 mask FFFFE0000 write-through
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
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ffd1800 (usable)
[    0.000000]  modified: 000000001ffd1800 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ffd1000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ffd1000 page 4k
[    0.000000] kernel direct mapping tables up to 1ffd1000 @ 7000-c000
[    0.000000] RAMDISK: 1f82c000 - 1ffc12df
[    0.000000] ACPI: RSDP 000fc9b0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 1ffd1f90 00040 (v01 DELL    CPi R   27D5080B ASL  00000061)
[    0.000000] ACPI: FACP 1ffd2c00 00074 (v01 DELL    CPi R   27D5080B ASL  00000061)
[    0.000000] ACPI: DSDT 1ffd3800 03C51 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 1ffe2000 00040
[    0.000000] ACPI: APIC 1ffd3400 00068 (v01 DELL    CPi R   27D5080B ASL  00000047)
[    0.000000] ACPI: ASF! 1ffd3000 0005B (v16 DELL    CPi R   27D5080B ASL  00000061)
[    0.000000] ACPI: MCFG 1ffd33c0 0003E (v16 DELL    CPi R   27D5080B ASL  00000061)
[    0.000000] ACPI: SSDT 1ffd23e6 0023E (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] ACPI: SSDT 1ffd220e 001D8 (v01  PmRef  Cpu0Cst 00003001 INTL 20030522)
[    0.000000] ACPI: SSDT 1ffd2013 001FB (v01  PmRef    CpuPm 00003000 INTL 20030522)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ffd1000
[    0.000000]   low ram: 0 - 1ffd1000
[    0.000000]   node 0 low ram: 00000000 - 1ffd1000
[    0.000000]   node 0 bootmap 00008000 - 0000bffc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ffd1000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000089f080]    TEXT DATA BSS ==> [0000100000 - 000089f080]
[    0.000000]   #4 [001f82c000 - 001ffc12df]          RAMDISK ==> [001f82c000 - 001ffc12df]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [00008a0000 - 00008a3188]              BRK ==> [00008a0000 - 00008a3188]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ffd1
[    0.000000]   HighMem  0x0001ffd1 -> 0x0001ffd1
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ffd1
[    0.000000] On node 0 totalpages: 130924
[    0.000000] free_area_init_node: node 0, pgdat c077b840, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125937 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1402000, static data 35068 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129900
[    0.000000] Kernel command line: root=UUID=CE00A3241887E334 loop=/ubuntu/disks/root.disk ro quiet splash 
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2620500 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 500664k/524100k available (4544k kernel code, 22796k reserved, 2127k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07d1000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdffd1000   ( 511 MB)
[    0.000000]       .init : 0xc0785000 - 0xc080c000   ( 540 kB)
[    0.000000]       .data : 0xc05701f4 - 0xc07841a8   (2127 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05701f4   (4544 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1729.038 MHz processor.
[    0.001133] Console: colour VGA+ 80x25
[    0.001137] console [tty0] enabled
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3458.07 BogoMIPS (lpj=6916152)
[    0.004033] Security Framework initialized
[    0.004055] AppArmor: AppArmor initialized
[    0.004063] Mount-cache hash table entries: 512
[    0.004204] Initializing cgroup subsys ns
[    0.004209] Initializing cgroup subsys cpuacct
[    0.004213] Initializing cgroup subsys memory
[    0.004221] Initializing cgroup subsys freezer
[    0.004224] Initializing cgroup subsys net_cls
[    0.004241] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004244] CPU: L2 cache: 2048K
[    0.004253] Performance Counters: p6 PMU driver.
[    0.004269] ... version:                 0
[    0.004272] ... bit width:               32
[    0.004274] ... generic counters:        2
[    0.004276] ... value mask:              00000000ffffffff
[    0.004278] ... max period:              000000007fffffff
[    0.004281] ... fixed-purpose counters:  0
[    0.004283] ... counter mask:            0000000000000003
[    0.004287] Checking 'hlt' instruction... OK.
[    0.020820] SMP alternatives: switching to UP code
[    0.027561] ACPI: Core revision 20090521
[    0.036428] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076968] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (3458.07 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] Booting paravirtualized kernel on bare hardware
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 10:57:32  Date: 10/11/09
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.080001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.080001] PCI: MCFG area at e0000000 reserved in E820
[    0.080001] PCI: Using MMCONFIG for extended config space
[    0.080001] PCI: Using configuration type 1 for base access
[    0.080001] bio: create slab <bio-0> at 0
[    0.080001] ACPI: EC: Look up EC in DSDT
[    0.100878] ACPI: SSDT 1ffd1fd0 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20030522)
[    0.101470] ACPI: Interpreter enabled
[    0.101477] ACPI: (supports S0 S3 S4 S5)
[    0.101499] ACPI: Using IOAPIC for interrupt routing
[    0.136947] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.150596] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.150701] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.150705] pci 0000:00:01.0: PME# disabled
[    0.150814] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.150820] pci 0000:00:1c.0: PME# disabled
[    0.150887] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.150948] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[    0.151010] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[    0.151071] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[    0.151137] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[    0.151197] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.151203] pci 0000:00:1d.7: PME# disabled
[    0.151305] pci 0000:00:1e.2: reg 10 io port: [0xed00-0xedff]
[    0.151313] pci 0000:00:1e.2: reg 14 io port: [0xec40-0xec7f]
[    0.151322] pci 0000:00:1e.2: reg 18 32bit mmio: [0xdffffe00-0xdfffffff]
[    0.151330] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xdffffd00-0xdffffdff]
[    0.151368] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.151373] pci 0000:00:1e.2: PME# disabled
[    0.151411] pci 0000:00:1e.3: reg 10 io port: [0xee00-0xeeff]
[    0.151420] pci 0000:00:1e.3: reg 14 io port: [0xec80-0xecff]
[    0.151468] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.151473] pci 0000:00:1e.3: PME# disabled
[    0.151563] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.151571] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.151576] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.151581] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0900-097f
[    0.151625] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[    0.151633] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[    0.151642] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[    0.151650] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[    0.151658] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[    0.151692] pci 0000:00:1f.2: PME# supported from D3hot
[    0.151697] pci 0000:00:1f.2: PME# disabled
[    0.151758] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.151819] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.151825] pci 0000:01:00.0: reg 14 io port: [0xde00-0xdeff]
[    0.151832] pci 0000:01:00.0: reg 18 32bit mmio: [0xdfdf0000-0xdfdfffff]
[    0.151848] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.151866] pci 0000:01:00.0: supports D1 D2
[    0.151919] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.151923] pci 0000:00:01.0: bridge 32bit mmio: [0xdfd00000-0xdfefffff]
[    0.151928] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.152009] pci 0000:02:00.0: reg 10 64bit mmio: [0xdfcf0000-0xdfcfffff]
[    0.152103] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.152109] pci 0000:02:00.0: PME# disabled
[    0.152176] pci 0000:00:1c.0: bridge 32bit mmio: [0xdfc00000-0xdfcfffff]
[    0.152231] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.152259] pci 0000:03:01.0: supports D1 D2
[    0.152261] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.152267] pci 0000:03:01.0: PME# disabled
[    0.152322] pci 0000:03:01.5: reg 10 32bit mmio: [0xdfbfd000-0xdfbfdfff]
[    0.152332] pci 0000:03:01.5: reg 14 32bit mmio: [0xdfbfe000-0xdfbfefff]
[    0.152393] pci 0000:03:01.5: supports D1 D2
[    0.152396] pci 0000:03:01.5: PME# supported from D0 D1 D2 D3hot
[    0.152402] pci 0000:03:01.5: PME# disabled
[    0.152454] pci 0000:03:03.0: reg 10 32bit mmio: [0xdfbff000-0xdfbfffff]
[    0.152522] pci 0000:03:03.0: PME# supported from D0 D3hot D3cold
[    0.152528] pci 0000:03:03.0: PME# disabled
[    0.152586] pci 0000:00:1e.0: transparent bridge
[    0.152594] pci 0000:00:1e.0: bridge 32bit mmio: [0xdfb00000-0xdfbfffff]
[    0.152638] pci_bus 0000:00: on NUMA node 0
[    0.152642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.152949] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.153018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.172244] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.172374] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.172502] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.172629] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.172742] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.172857] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.172971] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.173175] SCSI subsystem initialized
[    0.173218] libata version 3.00 loaded.
[    0.173298] usbcore: registered new interface driver usbfs
[    0.173315] usbcore: registered new interface driver hub
[    0.173341] usbcore: registered new device driver usb
[    0.173479] ACPI: WMI: Mapper loaded
[    0.173482] PCI: Using ACPI for IRQ routing
[    0.173650] Bluetooth: Core ver 2.15
[    0.173677] NET: Registered protocol family 31
[    0.173680] Bluetooth: HCI device and connection manager initialized
[    0.173683] Bluetooth: HCI socket layer initialized
[    0.173685] NetLabel: Initializing
[    0.173687] NetLabel:  domain hash size = 128
[    0.173689] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.173705] NetLabel:  unlabeled traffic allowed by default
[    0.173864] hpet clockevent registered
[    0.173868] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.173876] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.173881] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.181821] pnp: PnP ACPI init
[    0.181837] ACPI: bus type pnp registered
[    0.212581] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.212586] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.212662] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.212667] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.212671] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.239638] pnp: PnP ACPI: found 14 devices
[    0.239641] ACPI: ACPI bus type pnp unregistered
[    0.239646] PnPBIOS: Disabled by ACPI PNP
[    0.239658] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.239662] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.239666] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.239670] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.239674] system 00:00: iomem range 0x100000-0x1ffd17ff could not be reserved
[    0.239677] system 00:00: iomem range 0x1ffd1800-0x1fffffff has been reserved
[    0.239681] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.239685] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.239689] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.239692] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.239696] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.239700] system 00:00: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.239703] system 00:00: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.239707] system 00:00: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.239711] system 00:00: iomem range 0xf0006000-0xf0006fff has been reserved
[    0.239714] system 00:00: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.239718] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.239726] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.239732] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.239736] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.239740] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.239743] system 00:03: ioport range 0x10e0-0x10ff has been reserved
[    0.239751] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.239754] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.239758] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.239761] system 00:08: ioport range 0x93c-0x93f has been reserved
[    0.239765] system 00:08: ioport range 0x940-0x97f has been reserved
[    0.239772] system 00:0d: ioport range 0x930-0x93b has been reserved
[    0.274456] AppArmor: AppArmor Filesystem Enabled
[    0.274499] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.274503] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.274507] pci 0000:00:01.0:   MEM window: 0xdfd00000-0xdfefffff
[    0.274512] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xd7ffffff
[    0.274516] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.274518] pci 0000:00:1c.0:   IO window: disabled
[    0.274525] pci 0000:00:1c.0:   MEM window: 0xdfc00000-0xdfcfffff
[    0.274530] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.274541] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    0.274544] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
[    0.274550] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
[    0.274556] pci 0000:03:01.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.274562] pci 0000:03:01.0:   MEM window: 0x24000000-0x27ffffff
[    0.274568] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.274572] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.274579] pci 0000:00:1e.0:   MEM window: 0xdfb00000-0xdfbfffff
[    0.274585] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.274598]   alloc irq_desc for 16 on node -1
[    0.274600]   alloc kstat_irqs on node -1
[    0.274607] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.274612] pci 0000:00:01.0: setting latency timer to 64
[    0.274621] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.274627] pci 0000:00:1c.0: setting latency timer to 64
[    0.274635] pci 0000:00:1e.0: setting latency timer to 64
[    0.274645] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.274650]   alloc irq_desc for 19 on node -1
[    0.274652]   alloc kstat_irqs on node -1
[    0.274656] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.274666] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.274669] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.274673] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.274676] pci_bus 0000:01: resource 1 mem: [0xdfd00000-0xdfefffff]
[    0.274679] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]
[    0.274683] pci_bus 0000:02: resource 1 mem: [0xdfc00000-0xdfcfffff]
[    0.274686] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
[    0.274689] pci_bus 0000:03: resource 1 mem: [0xdfb00000-0xdfbfffff]
[    0.274693] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.274696] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.274699] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.274702] pci_bus 0000:04: resource 0 io:  [0x2000-0x20ff]
[    0.274705] pci_bus 0000:04: resource 1 io:  [0x2400-0x24ff]
[    0.274708] pci_bus 0000:04: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.274712] pci_bus 0000:04: resource 3 mem: [0x24000000-0x27ffffff]
[    0.274749] NET: Registered protocol family 2
[    0.274850] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.275136] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.275242] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.275342] TCP: Hash tables configured (established 16384 bind 16384)
[    0.275345] TCP reno registered
[    0.275416] NET: Registered protocol family 1
[    0.275480] Trying to unpack rootfs image as initramfs...
[    0.525291] Freeing initrd memory: 7764k freed
[    0.531655] cpufreq-nforce2: No nForce2 chipset.
[    0.531706] Scanning for low memory corruption every 60 seconds
[    0.531883] audit: initializing netlink socket (disabled)
[    0.531906] type=2000 audit(1255258652.528:1): initialized
[    0.542150] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.543780] VFS: Disk quotas dquot_6.5.2
[    0.543843] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.544476] fuse init (API version 7.12)
[    0.544568] msgmni has been set to 993
[    0.544789] alg: No test for stdrng (krng)
[    0.544802] io scheduler noop registered
[    0.544805] io scheduler anticipatory registered
[    0.544807] io scheduler deadline registered
[    0.544852] io scheduler cfq registered (default)
[    0.544967] pci 0000:01:00.0: Boot video device
[    0.545083]   alloc irq_desc for 24 on node -1
[    0.545086]   alloc kstat_irqs on node -1
[    0.545097] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.545104] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.545216]   alloc irq_desc for 25 on node -1
[    0.545219]   alloc kstat_irqs on node -1
[    0.545228] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.545238] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.545348] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.545413] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.546042] ACPI: AC Adapter [AC] (on-line)
[    0.546148] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.546688] ACPI: Lid Switch [LID]
[    0.546738] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.546745] ACPI: Power Button [PBTN]
[    0.546799] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.546802] ACPI: Sleep Button [SBTN]
[    0.547279] Marking TSC unstable due to TSC halts in idle
[    0.547313] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    0.547345] processor LNXCPU:00: registered as cooling_device0
[    0.547349] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.551351] Switched to high resolution mode on CPU 0
[    0.566708] thermal LNXTHERM:01: registered as thermal_zone0
[    0.566717] ACPI: Thermal Zone [THM] (68 C)
[    0.566769] isapnp: Scanning for PnP cards...
[    0.860761] ACPI: Battery Slot [BAT0] (battery present)
[    0.860808] ACPI: Battery Slot [BAT1] (battery absent)
[    0.948253] isapnp: No Plug & Play device found
[    0.949445] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.949568] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.950025] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.950121]   alloc irq_desc for 17 on node -1
[    0.950124]   alloc kstat_irqs on node -1
[    0.950131] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.950138] serial 0000:00:1e.3: PCI INT B disabled
[    0.951150] brd: module loaded
[    0.951638] loop: module loaded
[    0.951719] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.951799] ahci 0000:00:1f.2: version 3.0
[    0.951810] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.951821] ahci 0000:00:1f.2: PCI INT B disabled
[    0.951826] ahci: probe of 0000:00:1f.2 failed with error -22
[    0.951868] ata_piix 0000:00:1f.2: version 2.13
[    0.951875] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.951881] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.104028] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.104183] scsi0 : ata_piix
[    1.104265] scsi1 : ata_piix
[    1.106328] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.106332] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.107623] Fixed MDIO Bus: probed
[    1.107662] PPP generic driver version 2.4.2
[    1.107749] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.107767] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.107782] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.107786] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.107837] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.111740] ehci_hcd 0000:00:1d.7: debug port 1
[    1.111748] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.111764] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    1.124018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.124117] usb usb1: configuration #1 chosen from 1 choice
[    1.124150] hub 1-0:1.0: USB hub found
[    1.124159] hub 1-0:1.0: 8 ports detected
[    1.124241] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.124262] uhci_hcd: USB Universal Host Controller Interface driver
[    1.124285] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.124292] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.124296] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.124326] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.124353] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    1.124433] usb usb2: configuration #1 chosen from 1 choice
[    1.124461] hub 2-0:1.0: USB hub found
[    1.124469] hub 2-0:1.0: 2 ports detected
[    1.124519] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.124526] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.124530] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.124563] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.124598] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    1.124677] usb usb3: configuration #1 chosen from 1 choice
[    1.124705] hub 3-0:1.0: USB hub found
[    1.124712] hub 3-0:1.0: 2 ports detected
[    1.124761]   alloc irq_desc for 18 on node -1
[    1.124764]   alloc kstat_irqs on node -1
[    1.124769] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.124776] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.124780] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.124817] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.124852] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    1.124938] usb usb4: configuration #1 chosen from 1 choice
[    1.124969] hub 4-0:1.0: USB hub found
[    1.124976] hub 4-0:1.0: 2 ports detected
[    1.125021] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.125027] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.125032] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.125061] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.125095] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    1.125180] usb usb5: configuration #1 chosen from 1 choice
[    1.125211] hub 5-0:1.0: USB hub found
[    1.125218] hub 5-0:1.0: 2 ports detected
[    1.125323] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.130404] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.130410] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.130472] mice: PS/2 mouse device common for all mice
[    1.130621] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.130652] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.130773] device-mapper: uevent: version 1.0.3
[    1.130866] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.130948] device-mapper: multipath: version 1.1.0 loaded
[    1.130951] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.131072] EISA: Probing bus 0 at eisa.0
[    1.131079] Cannot allocate resource for EISA slot 1
[    1.131082] Cannot allocate resource for EISA slot 2
[    1.131106] EISA: Detected 0 cards.
[    1.131206] cpuidle: using governor ladder
[    1.131294] cpuidle: using governor menu
[    1.131807] TCP cubic registered
[    1.131985] NET: Registered protocol family 10
[    1.132458] lo: Disabled Privacy Extensions
[    1.132784] NET: Registered protocol family 17
[    1.132803] Bluetooth: L2CAP ver 2.13
[    1.132805] Bluetooth: L2CAP socket layer initialized
[    1.132808] Bluetooth: SCO (Voice Link) ver 0.6
[    1.132810] Bluetooth: SCO socket layer initialized
[    1.132841] Bluetooth: RFCOMM TTY layer initialized
[    1.132845] Bluetooth: RFCOMM socket layer initialized
[    1.132847] Bluetooth: RFCOMM ver 1.11
[    1.133076] Using IPI No-Shortcut mode
[    1.133140] PM: Resume from disk failed.
[    1.133153] registered taskstats version 1
[    1.133279]   Magic number: 13:352:982
[    1.133365] rtc_cmos 00:06: setting system clock to 2009-10-11 10:57:33 UTC (1255258653)
[    1.133369] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.133372] EDD information not available.
[    1.143008] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.268971] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM SCB5265, TD17, max UDMA/33
[    1.269412] ata1.00: ATA-6: TOSHIBA MK4026GAX, PA102D, max UDMA/100
[    1.269416] ata1.00: 78140160 sectors, multi 8: LBA 
[    1.269431] ata1.00: applying bridge limits
[    1.284739] ata2.00: configured for UDMA/33
[    1.285115] ata1.00: configured for UDMA/100
[    1.285252] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4026GA PA10 PQ: 0 ANSI: 5
[    1.285378] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.285422] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.285474] sd 0:0:0:0: [sda] Write Protect is off
[    1.285477] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.285504] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.285634]  sda:
[    1.288323] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD SCB5265 TD17 PQ: 0 ANSI: 5
[    1.295576] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    1.295580] Uniform CD-ROM driver Revision: 3.20
[    1.295661] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.295700] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.346289]  sda1
[    1.346483] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.346499] Freeing unused kernel memory: 540k freed
[    1.346826] Write protecting the kernel text: 4548k
[    1.346867] Write protecting the kernel read-only data: 1828k
[    1.505202] Linux agpgart interface v0.103
[    1.544263] tg3.c:v3.99 (April 20, 2009)
[    1.544287] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.544298] tg3 0000:02:00.0: setting latency timer to 64
[    1.567772] tg3 0000:02:00.0: wake-up capability disabled by ACPI
[    1.567780] tg3 0000:02:00.0: PME# disabled
[    1.640216] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.644592] eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:12:3f:1f:4d:69
[    1.644598] eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.644602] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.644604] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.655175] [drm] Initialized drm 1.1.0 20060810
[    1.672013] Clocksource tsc unstable (delta = -104464440 ns)
[    1.680429] [drm] radeon default to kernel modesetting DISABLED.
[    1.680565] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.680571] pci 0000:01:00.0: setting latency timer to 64
[    1.680716] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    1.686456] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/device:23/input/input5
[    1.686496] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.808999] usb 4-1: configuration #1 chosen from 1 choice
[    1.818767] usbcore: registered new interface driver hiddev
[    1.831304] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6
[    1.831394] generic-usb 0003:0461:4D15.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.2-1/input0
[    1.831408] usbcore: registered new interface driver usbhid
[    1.831411] usbhid: v2.6:USB HID core driver
[    2.800512] EXT3-fs: INFO: recovery required on readonly filesystem.
[    2.800516] EXT3-fs: write access will be enabled during recovery.
[    3.575462] kjournald starting.  Commit interval 5 seconds
[    3.575485] EXT3-fs: recovery complete.
[    3.575675] EXT3-fs: mounted filesystem with writeback data mode.
[    5.103334] type=1505 audit(1255258657.469:2): operation="profile_load" pid=415 name=/usr/share/gdm/guest-session/Xsession
[    5.123810] type=1505 audit(1255258657.486:3): operation="profile_load" pid=416 name=/sbin/dhclient3
[    5.124559] type=1505 audit(1255258657.490:4): operation="profile_load" pid=416 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.125037] type=1505 audit(1255258657.490:5): operation="profile_load" pid=416 name=/usr/lib/connman/scripts/dhclient-script
[    5.260531] type=1505 audit(1255258657.626:6): operation="profile_load" pid=417 name=/usr/bin/evince
[    5.270616] type=1505 audit(1255258657.634:7): operation="profile_load" pid=417 name=/usr/bin/evince-previewer
[    5.276616] type=1505 audit(1255258657.642:8): operation="profile_load" pid=417 name=/usr/bin/evince-thumbnailer
[    5.302680] type=1505 audit(1255258657.666:9): operation="profile_load" pid=419 name=/usr/lib/cups/backend/cups-pdf
[    5.303540] type=1505 audit(1255258657.666:10): operation="profile_load" pid=419 name=/usr/sbin/cupsd
[   14.827920] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   14.827925] ata1.00: BMDMA stat 0x24
[   14.827935] ata1.00: cmd c8/00:20:b7:ec:ca/00:00:00:00:00/e2 tag 0 dma 16384 in
[   14.827937]          res 51/40:09:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   14.827940] ata1.00: status: { DRDY ERR }
[   14.827943] ata1.00: error: { UNC }
[   14.844758] ata1.00: configured for UDMA/100
[   14.844768] ata1: EH complete
[   21.595599] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   21.595602] ata1.00: BMDMA stat 0x24
[   21.595610] ata1.00: cmd c8/00:20:b7:ec:ca/00:00:00:00:00/e2 tag 0 dma 16384 in
[   21.595612]          res 51/40:09:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   21.595615] ata1.00: status: { DRDY ERR }
[   21.595618] ata1.00: error: { UNC }
[   21.608754] ata1.00: configured for UDMA/100
[   21.608760] ata1: EH complete
[   28.352179] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   28.352182] ata1.00: BMDMA stat 0x24
[   28.352190] ata1.00: cmd c8/00:20:b7:ec:ca/00:00:00:00:00/e2 tag 0 dma 16384 in
[   28.352191]          res 51/40:09:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   28.352195] ata1.00: status: { DRDY ERR }
[   28.352197] ata1.00: error: { UNC }
[   28.368774] ata1.00: configured for UDMA/100
[   28.368779] ata1: EH complete
[   35.119840] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   35.119843] ata1.00: BMDMA stat 0x24
[   35.119850] ata1.00: cmd c8/00:20:b7:ec:ca/00:00:00:00:00/e2 tag 0 dma 16384 in
[   35.119852]          res 51/40:09:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   35.119856] ata1.00: status: { DRDY ERR }
[   35.119858] ata1.00: error: { UNC }
[   35.136781] ata1.00: configured for UDMA/100
[   35.136787] ata1: EH complete
[   41.876395] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   41.876398] ata1.00: BMDMA stat 0x24
[   41.876405] ata1.00: cmd c8/00:20:b7:ec:ca/00:00:00:00:00/e2 tag 0 dma 16384 in
[   41.876407]          res 51/40:09:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   41.876411] ata1.00: status: { DRDY ERR }
[   41.876413] ata1.00: error: { UNC }
[   41.892759] ata1.00: configured for UDMA/100
[   41.892765] ata1: EH complete
[   48.610751] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   48.610754] ata1.00: BMDMA stat 0x24
[   48.610761] ata1.00: cmd c8/00:20:b7:ec:ca/00:00:00:00:00/e2 tag 0 dma 16384 in
[   48.610763]          res 51/40:09:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   48.610767] ata1.00: status: { DRDY ERR }
[   48.610769] ata1.00: error: { UNC }
[   48.624791] ata1.00: configured for UDMA/100
[   48.624804] sd 0:0:0:0: [sda] Unhandled sense code
[   48.624807] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   48.624812] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   48.624817] Descriptor sense data with sense descriptors (in hex):
[   48.624820]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   48.624831]         02 ca ec ce 
[   48.624835] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   48.624842] end_request: I/O error, dev sda, sector 46853326
[   48.624845] __ratelimit: 3 callbacks suppressed
[   48.624849] Buffer I/O error on device sda1, logical block 5856657
[   48.624852] Buffer I/O error on device sda1, logical block 5856658
[   48.624861] ata1: EH complete
[   55.400549] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   55.400552] ata1.00: BMDMA stat 0x24
[   55.400560] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[   55.400561]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   55.400565] ata1.00: status: { DRDY ERR }
[   55.400567] ata1.00: error: { UNC }
[   55.416759] ata1.00: configured for UDMA/100
[   55.416765] ata1: EH complete
[   62.168172] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   62.168176] ata1.00: BMDMA stat 0x24
[   62.168183] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[   62.168185]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   62.168188] ata1.00: status: { DRDY ERR }
[   62.168191] ata1.00: error: { UNC }
[   62.184790] ata1.00: configured for UDMA/100
[   62.184795] ata1: EH complete
[   68.913610] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   68.913613] ata1.00: BMDMA stat 0x24
[   68.913621] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[   68.913623]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   68.913627] ata1.00: status: { DRDY ERR }
[   68.913629] ata1.00: error: { UNC }
[   68.928756] ata1.00: configured for UDMA/100
[   68.928764] ata1: EH complete
[   75.681222] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   75.681225] ata1.00: BMDMA stat 0x24
[   75.681232] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[   75.681234]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   75.681237] ata1.00: status: { DRDY ERR }
[   75.681240] ata1.00: error: { UNC }
[   75.696786] ata1.00: configured for UDMA/100
[   75.696792] ata1: EH complete
[   82.426642] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   82.426645] ata1.00: BMDMA stat 0x24
[   82.426652] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[   82.426654]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   82.426658] ata1.00: status: { DRDY ERR }
[   82.426660] ata1.00: error: { UNC }
[   82.440753] ata1.00: configured for UDMA/100
[   82.440759] ata1: EH complete
[   89.183153] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   89.183156] ata1.00: BMDMA stat 0x24
[   89.183164] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[   89.183165]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   89.183169] ata1.00: status: { DRDY ERR }
[   89.183171] ata1.00: error: { UNC }
[   89.196773] ata1.00: configured for UDMA/100
[   89.196782] sd 0:0:0:0: [sda] Unhandled sense code
[   89.196784] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   89.196788] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   89.196793] Descriptor sense data with sense descriptors (in hex):
[   89.196795]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   89.196806]         02 ca ec ce 
[   89.196811] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   89.196817] end_request: I/O error, dev sda, sector 46853326
[   89.196821] Buffer I/O error on device sda1, logical block 5856657
[   89.196832] ata1: EH complete
[   95.950754] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   95.950757] ata1.00: BMDMA stat 0x24
[   95.950765] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[   95.950767]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[   95.950770] ata1.00: status: { DRDY ERR }
[   95.950773] ata1.00: error: { UNC }
[   95.964754] ata1.00: configured for UDMA/100
[   95.964760] ata1: EH complete
[  102.696161] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  102.696164] ata1.00: BMDMA stat 0x24
[  102.696171] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  102.696173]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  102.696176] ata1.00: status: { DRDY ERR }
[  102.696179] ata1.00: error: { UNC }
[  102.712786] ata1.00: configured for UDMA/100
[  102.712792] ata1: EH complete
[  109.441562] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  109.441565] ata1.00: BMDMA stat 0x24
[  109.441572] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  109.441574]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  109.441577] ata1.00: status: { DRDY ERR }
[  109.441580] ata1.00: error: { UNC }
[  109.456786] ata1.00: configured for UDMA/100
[  109.456792] ata1: EH complete
[  116.186960] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  116.186963] ata1.00: BMDMA stat 0x24
[  116.186970] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  116.186972]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  116.186976] ata1.00: status: { DRDY ERR }
[  116.186978] ata1.00: error: { UNC }
[  116.200787] ata1.00: configured for UDMA/100
[  116.200793] ata1: EH complete
[  122.932352] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  122.932355] ata1.00: BMDMA stat 0x24
[  122.932363] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  122.932364]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  122.932368] ata1.00: status: { DRDY ERR }
[  122.932370] ata1.00: error: { UNC }
[  122.948754] ata1.00: configured for UDMA/100
[  122.948759] ata1: EH complete
[  129.688837] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  129.688840] ata1.00: BMDMA stat 0x24
[  129.688847] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  129.688849]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  129.688852] ata1.00: status: { DRDY ERR }
[  129.688855] ata1.00: error: { UNC }
[  129.704766] ata1.00: configured for UDMA/100
[  129.704772] sd 0:0:0:0: [sda] Unhandled sense code
[  129.704775] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  129.704778] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  129.704783] Descriptor sense data with sense descriptors (in hex):
[  129.704786]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  129.704796]         02 ca ec ce 
[  129.704801] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  129.704807] end_request: I/O error, dev sda, sector 46853326
[  129.704810] Buffer I/O error on device sda1, logical block 5856657
[  129.704819] ata1: EH complete
[  136.467502] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  136.467505] ata1.00: BMDMA stat 0x24
[  136.467513] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  136.467515]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  136.467518] ata1.00: status: { DRDY ERR }
[  136.467521] ata1.00: error: { UNC }
[  136.480773] ata1.00: configured for UDMA/100
[  136.480779] ata1: EH complete
[  143.201785] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  143.201788] ata1.00: BMDMA stat 0x24
[  143.201796] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  143.201798]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  143.201801] ata1.00: status: { DRDY ERR }
[  143.201804] ata1.00: error: { UNC }
[  143.216790] ata1.00: configured for UDMA/100
[  143.216796] ata1: EH complete
[  149.969350] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  149.969353] ata1.00: BMDMA stat 0x24
[  149.969360] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  149.969362]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  149.969365] ata1.00: status: { DRDY ERR }
[  149.969368] ata1.00: error: { UNC }
[  149.984756] ata1.00: configured for UDMA/100
[  149.984761] ata1: EH complete
[  156.725815] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  156.725818] ata1.00: BMDMA stat 0x24
[  156.725825] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  156.725827]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  156.725830] ata1.00: status: { DRDY ERR }
[  156.725833] ata1.00: error: { UNC }
[  156.740756] ata1.00: configured for UDMA/100
[  156.740762] ata1: EH complete
[  163.482276] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  163.482279] ata1.00: BMDMA stat 0x24
[  163.482286] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  163.482288]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  163.482291] ata1.00: status: { DRDY ERR }
[  163.482294] ata1.00: error: { UNC }
[  163.496756] ata1.00: configured for UDMA/100
[  163.496762] ata1: EH complete
[  170.216544] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  170.216547] ata1.00: BMDMA stat 0x24
[  170.216554] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  170.216556]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  170.216560] ata1.00: status: { DRDY ERR }
[  170.216562] ata1.00: error: { UNC }
[  170.232754] ata1.00: configured for UDMA/100
[  170.232760] sd 0:0:0:0: [sda] Unhandled sense code
[  170.232763] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  170.232766] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  170.232771] Descriptor sense data with sense descriptors (in hex):
[  170.232774]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  170.232784]         02 ca ec ce 
[  170.232789] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  170.232795] end_request: I/O error, dev sda, sector 46853326
[  170.232798] Buffer I/O error on device sda1, logical block 5856657
[  170.232807] ata1: EH complete
[  183.773817] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  183.773821] ata1.00: BMDMA stat 0x24
[  183.773829] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  183.773831]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  183.773834] ata1.00: status: { DRDY ERR }
[  183.773837] ata1.00: error: { UNC }
[  183.788758] ata1.00: configured for UDMA/100
[  183.788764] ata1: EH complete
[  190.519161] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  190.519164] ata1.00: BMDMA stat 0x24
[  190.519171] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  190.519173]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  190.519176] ata1.00: status: { DRDY ERR }
[  190.519179] ata1.00: error: { UNC }
[  190.532778] ata1.00: configured for UDMA/100
[  190.532784] ata1: EH complete
[  197.264504] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  197.264507] ata1.00: BMDMA stat 0x24
[  197.264515] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  197.264516]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  197.264520] ata1.00: status: { DRDY ERR }
[  197.264522] ata1.00: error: { UNC }
[  197.280782] ata1.00: configured for UDMA/100
[  197.280788] ata1: EH complete
[  204.020939] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  204.020943] ata1.00: BMDMA stat 0x24
[  204.020950] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  204.020952]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  204.020955] ata1.00: status: { DRDY ERR }
[  204.020958] ata1.00: error: { UNC }
[  204.036759] ata1.00: configured for UDMA/100
[  204.036765] ata1: EH complete
[  210.788464] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  210.788468] ata1.00: BMDMA stat 0x24
[  210.788475] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  210.788477]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  210.788480] ata1.00: status: { DRDY ERR }
[  210.788483] ata1.00: error: { UNC }
[  210.804756] ata1.00: configured for UDMA/100
[  210.804762] ata1: EH complete
[  217.544893] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  217.544896] ata1.00: BMDMA stat 0x24
[  217.544903] ata1.00: cmd c8/00:08:c7:ec:ca/00:00:00:00:00/e2 tag 0 dma 4096 in
[  217.544905]          res 51/40:01:ce:ec:ca/00:00:00:00:00/e2 Emask 0x9 (media error)
[  217.544908] ata1.00: status: { DRDY ERR }
[  217.544911] ata1.00: error: { UNC }
[  217.560753] ata1.00: configured for UDMA/100
[  217.560759] sd 0:0:0:0: [sda] Unhandled sense code
[  217.560761] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  217.560765] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  217.560770] Descriptor sense data with sense descriptors (in hex):
[  217.560773]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  217.560783]         02 ca ec ce 
[  217.560788] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  217.560794] end_request: I/O error, dev sda, sector 46853326
[  217.560798] Buffer I/O error on device sda1, logical block 5856657
[  217.560807] ata1: EH complete
[  219.044912] udev: starting version 147
[  219.822082] parport_pc 00:0c: reported by Plug and Play ACPI
[  219.822152] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  219.832192] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[  221.813437] lp0: using parport0 (interrupt-driven).
[  221.850785] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0182]
[  221.850811] yenta_cardbus 0000:03:01.0: Using CSCINT to route CSC interrupts to PCI
[  221.850814] yenta_cardbus 0000:03:01.0: Routing CardBus interrupts to PCI
[  221.850820] yenta_cardbus 0000:03:01.0: TI: mfunc 0x01111122, devctl 0x64
[  222.057857] ppdev: user-space parallel port driver
[  222.080681] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0c78, PCI irq 19
[  222.080687] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[  222.080692] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[  222.080702] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[  222.080706] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[  222.080943] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xdfb00000 - 0xdfbfffff
[  222.080946] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[  222.111387] lib80211: common routines for IEEE802.11 drivers
[  222.111391] lib80211_crypt: registered algorithm 'NULL'
[  222.415826] intel_rng: FWH not detected
[  222.554313] dell-wmi: No known WMI GUID found
[  223.032478] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input7
[  223.056200] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input8
[  223.409573] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  223.409578] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  223.445218] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  223.445223] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  223.445334] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  223.445413] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  223.445455] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[  223.460531] ip_tables: (C) 2000-2006 Netfilter Core Team
[  223.534662] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[  223.536352] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[  223.537049] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[  223.537651] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[  223.538420] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[  224.225337] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  224.549182] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  224.549223] Intel ICH 0000:00:1e.2: setting latency timer to 64
[  225.376034] intel8x0_measure_ac97_clock: measured 55435 usecs (2671 samples)
[  225.376039] intel8x0: clocking to 48000
[  246.732061] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:2 across:3884432k 
[  246.886579] EXT3 FS on loop0, internal journal
[  247.690284] tg3 0000:02:00.0: wake-up capability disabled by ACPI
[  247.690294] tg3 0000:02:00.0: PME# disabled
[  247.746763] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  248.251596] type=1505 audit(1255273300.614:12): operation="profile_replace" pid=966 name=/usr/share/gdm/guest-session/Xsession
[  248.253369] type=1505 audit(1255273300.618:13): operation="profile_replace" pid=967 name=/sbin/dhclient3
[  248.254100] type=1505 audit(1255273300.618:14): operation="profile_replace" pid=967 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  248.254505] type=1505 audit(1255273300.618:15): operation="profile_replace" pid=967 name=/usr/lib/connman/scripts/dhclient-script
[  248.258210] type=1505 audit(1255273300.622:16): operation="profile_replace" pid=968 name=/usr/bin/evince
[  248.269384] type=1505 audit(1255273300.634:17): operation="profile_replace" pid=968 name=/usr/bin/evince-previewer
[  248.275357] type=1505 audit(1255273300.638:18): operation="profile_replace" pid=968 name=/usr/bin/evince-thumbnailer
[  248.284121] type=1505 audit(1255273300.650:19): operation="profile_replace" pid=970 name=/usr/lib/cups/backend/cups-pdf
[  248.285028] type=1505 audit(1255273300.650:20): operation="profile_replace" pid=970 name=/usr/sbin/cupsd
[  248.287677] type=1505 audit(1255273300.650:21): operation="profile_replace" pid=971 name=/usr/sbin/tcpdump
[  249.862301] [drm] Setting GART location based on new memory map
[  249.864348] [drm] Loading R300 Microcode
[  249.864389] [drm] Num pipes: 1
[  249.864398] [drm] writeback test succeeded in 1 usecs

```Attempting recovery mode will output several errors.

I'd appreciate any suggestions or help...

---

