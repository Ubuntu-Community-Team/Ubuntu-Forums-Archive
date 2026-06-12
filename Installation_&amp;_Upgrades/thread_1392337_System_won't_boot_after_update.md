---
title: "System won't boot after update"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by sf9753 on 2010-01-28
Ubuntu won't start on this system since I allowed the recent suggested updates.  

Update manager had been prompting me to okay a number of updates.  Honestly, I don't really recall what they were.  After the updates my screen started slowly oscillating between a general graying out and normal brightness in slow cycles while on Google through Firefox.  I tried to shut down and restart, but since then the system won't boot.  I see the usual POST stuff, the a brief Grub options message, then a dark gray screen with a cursor in the top left corner, then the cursor goes away, and nothing more happens.  It won't boot with a 9.10 disk trial version either-same sequence happens.  I'm on the machine right now with the 8.04 disk trial version, which started up and runs just fine, repeatedly.  It's a rebuild with a Gigabyte motherboard and an AMD64.  The hard drive shows config files 2.6.31-14 through -17, and Grub version 0.97-29ubuntu53, if those matter.  Ubuntu is whatever 32 bit version came after the last kernel update.  I tried searching, and can't find this problem mentioned elsewhere.  Thanks in advance for any insights.  Please be gentle - I'm not in my element here.

---

### Post by lidex on 2010-01-28
Since you can boot up 8.04 live session, do so and have a look at your logfiles on disk. /var/log/ directory. Try dmesg, messages and debug. If you post the text from those files here, select (highlight) the text and click the # in the toolbar to enclose in code tags please.

---

### Post by sf9753 on 2010-01-29
[CODE][/COD[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfde0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfde0000 - 00000000bfde3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfde3000 - 00000000bfdf0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdf0000 - 00000000bfe00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbfde0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00BFE00000 mask FFFFE00000 uncachable
[    0.000000]   3 base 0100000000 mask FFE0000000 write-back
[    0.000000]   4 base 0120000000 mask FFF0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfde0000 (usable)
[    0.000000]  modified: 00000000bfde0000 - 00000000bfde3000 (ACPI NVS)
[    0.000000]  modified: 00000000bfde3000 - 00000000bfdf0000 (ACPI data)
[    0.000000]  modified: 00000000bfdf0000 - 00000000bfe00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a4000 - 37fef047
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff8047
[    0.000000] Move RAMDISK from 00000000378a4000 - 0000000037fef046 to 008ad000 - 00ff8046
[    0.000000] ACPI: RSDP 000f7090 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT bfde3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP bfde3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT bfde30c0 06550 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS bfde0000 00040
[    0.000000] ACPI: SSDT bfde9700 002CC (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET bfde9a00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG bfde9a40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC bfde9640 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2181MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac116]              BRK ==> [00008a9000 - 00008ac116]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000ff8047]      NEW RAMDISK ==> [00008ad000 - 0000ff8047]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f5740] f5740
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfde0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfde0
[    0.000000] On node 0 totalpages: 785787
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4364 pages used for memmap
[    0.000000]   HighMem zone: 554198 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bfe00000 (gap: bfe00000:20200000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2810000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779647
[    0.000000] Kernel command line: root=UUID=b9706f2d-958e-437e-a8da-b5a609325459 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15717760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfde0)
[    0.000000] Memory: 3085936k/3143552k available (4566k kernel code, 56368k reserved, 2142k data, 540k init, 2234248k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2805.608 MHz processor.
[    0.000952] Console: colour VGA+ 80x25
[    0.000955] console [tty0] enabled
[    0.001096] hpet clockevent registered
[    0.001103]   alloc irq_desc for 24 on node 0
[    0.001105]   alloc kstat_irqs on node 0
[    0.001112] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.001116] Calibrating delay loop (skipped), value calculated using timer frequency.. 5611.21 BogoMIPS (lpj=11222432)
[    0.001131] Security Framework initialized
[    0.001145] AppArmor: AppArmor initialized
[    0.001151] Mount-cache hash table entries: 512
[    0.001242] Initializing cgroup subsys ns
[    0.001245] Initializing cgroup subsys cpuacct
[    0.001248] Initializing cgroup subsys memory
[    0.001253] Initializing cgroup subsys freezer
[    0.001254] Initializing cgroup subsys net_cls
[    0.001263] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.001265] CPU: L2 Cache: 512K (64 bytes/line)
[    0.001266] CPU: Physical Processor ID: 0
[    0.001268] CPU: Processor Core ID: 0
[    0.001270] mce: CPU supports 5 MCE banks
[    0.001277] using C1E aware idle routine
[    0.001282] Performance Counters: AMD PMU driver.
[    0.001286] ... version:                 0
[    0.001287] ... bit width:               48
[    0.001289] ... generic counters:        4
[    0.001290] ... value mask:              0000ffffffffffff
[    0.001292] ... max period:              00007fffffffffff
[    0.001293] ... fixed-purpose counters:  0
[    0.001294] ... counter mask:            000000000000000f
[    0.001297] Checking 'hlt' instruction... OK.
[    0.017525] ACPI: Core revision 20090521
[    0.028138] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067810] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ stepping 02
[    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5611.95 BogoMIPS (lpj=11223908)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.152367] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ stepping 02
[    0.152387] Brought up 2 CPUs
[    0.152390] Total of 2 processors activated (11223.17 BogoMIPS).
[    0.152493] CPU0 attaching sched-domain:
[    0.152495]  domain 0: span 0-1 level MC
[    0.152497]   groups: 0 1
[    0.152501] CPU1 attaching sched-domain:
[    0.152503]  domain 0: span 0-1 level MC
[    0.152505]   groups: 1 0
[    0.152554] Booting paravirtualized kernel on bare hardware
[    0.152554] regulator: core version 0.5
[    0.152554] Time:  2:46:05  Date: 01/14/10
[    0.152554] NET: Registered protocol family 16
[    0.152554] EISA bus registered
[    0.152554] ACPI: bus type pci registered
[    0.152554] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.152554] PCI: MCFG area at e0000000 reserved in E820
[    0.152554] PCI: Using MMCONFIG for extended config space
[    0.152554] PCI: Using configuration type 1 for base access
[    0.152866] bio: create slab <bio-0> at 0
[    0.152866] ACPI: EC: Look up EC in DSDT
[    0.159422] ACPI: Interpreter enabled
[    0.159429] ACPI: (supports S0 S1 S4 S5)
[    0.159448] ACPI: Using IOAPIC for interrupt routing
[    0.162888] ACPI: No dock devices found.
[    0.162972] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.163015] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.163104] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.163107] pci 0000:00:0a.0: PME# disabled
[    0.163168] pci 0000:00:11.0: reg 10 io port: [0xff00-0xff07]
[    0.163175] pci 0000:00:11.0: reg 14 io port: [0xfe00-0xfe03]
[    0.163182] pci 0000:00:11.0: reg 18 io port: [0xfd00-0xfd07]
[    0.163189] pci 0000:00:11.0: reg 1c io port: [0xfc00-0xfc03]
[    0.163196] pci 0000:00:11.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.163203] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f3ff]
[    0.163263] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.163318] pci 0000:00:12.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.163391] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe02c000-0xfe02c0ff]
[    0.163444] pci 0000:00:12.2: supports D1 D2
[    0.163446] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.163450] pci 0000:00:12.2: PME# disabled
[    0.163482] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.163537] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02a000-0xfe02afff]
[    0.163610] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe029000-0xfe0290ff]
[    0.163663] pci 0000:00:13.2: supports D1 D2
[    0.163665] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.163669] pci 0000:00:13.2: PME# disabled
[    0.163786] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.163793] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.163800] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.163806] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.163813] pci 0000:00:14.1: reg 20 io port: [0xfa00-0xfa0f]
[    0.163880] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe024000-0xfe027fff]
[    0.163923] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.163927] pci 0000:00:14.2: PME# disabled
[    0.164061] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe028000-0xfe028fff]
[    0.164184] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.164188] pci 0000:01:05.0: reg 14 io port: [0xee00-0xeeff]
[    0.164192] pci 0000:01:05.0: reg 18 32bit mmio: [0xfdfe0000-0xfdfeffff]
[    0.164199] pci 0000:01:05.0: reg 24 32bit mmio: [0xfde00000-0xfdefffff]
[    0.164211] pci 0000:01:05.0: supports D1 D2
[    0.164228] pci 0000:01:05.1: reg 10 32bit mmio: [0xfdffc000-0xfdffffff]
[    0.164249] pci 0000:01:05.1: supports D1 D2
[    0.164290] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.164293] pci 0000:00:01.0: bridge 32bit mmio: [0xfde00000-0xfdffffff]
[    0.164296] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.164331] pci 0000:02:00.0: reg 10 io port: [0xde00-0xdeff]
[    0.164346] pci 0000:02:00.0: reg 18 64bit mmio: [0xfdaff000-0xfdafffff]
[    0.164357] pci 0000:02:00.0: reg 20 64bit mmio: [0xfdae0000-0xfdaeffff]
[    0.164364] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.164393] pci 0000:02:00.0: supports D1 D2
[    0.164395] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164399] pci 0000:02:00.0: PME# disabled
[    0.164459] pci 0000:00:0a.0: bridge io port: [0xd000-0xdfff]
[    0.164462] pci 0000:00:0a.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.164466] pci 0000:00:0a.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
[    0.164520] pci 0000:03:06.0: reg 10 32bit mmio: [0xfdce0000-0xfdceffff]
[    0.164639] pci 0000:03:0e.0: reg 10 32bit mmio: [0xfdcff000-0xfdcff7ff]
[    0.164648] pci 0000:03:0e.0: reg 14 32bit mmio: [0xfdcf8000-0xfdcfbfff]
[    0.164706] pci 0000:03:0e.0: supports D1 D2
[    0.164708] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.164713] pci 0000:03:0e.0: PME# disabled
[    0.164748] pci 0000:00:14.4: transparent bridge
[    0.164752] pci 0000:00:14.4: bridge io port: [0xc000-0xcfff]
[    0.164756] pci 0000:00:14.4: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.164761] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.164772] pci_bus 0000:00: on NUMA node 0
[    0.164776] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.164996] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.165079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.165122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.177925] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178004] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178077] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178150] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178223] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178297] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178370] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178443] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178576] SCSI subsystem initialized
[    0.178610] libata version 3.00 loaded.
[    0.178610] usbcore: registered new interface driver usbfs
[    0.178610] usbcore: registered new interface driver hub
[    0.178610] usbcore: registered new device driver usb
[    0.178610] ACPI: WMI: Mapper loaded
[    0.178610] PCI: Using ACPI for IRQ routing
[    0.178610] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.178610] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.188005] Bluetooth: Core ver 2.15
[    0.188017] NET: Registered protocol family 31
[    0.188017] Bluetooth: HCI device and connection manager initialized
[    0.188017] Bluetooth: HCI socket layer initialized
[    0.188017] NetLabel: Initializing
[    0.188017] NetLabel:  domain hash size = 128
[    0.188017] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.188027] NetLabel:  unlabeled traffic allowed by default
[    0.188058] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.188063] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.192027] hpet: hpet2 irq 24 for MSI
[    0.196030] Switched to high resolution mode on CPU 0
[    0.196351] Switched to high resolution mode on CPU 1
[    0.204023] pnp: PnP ACPI init
[    0.204036] ACPI: bus type pnp registered
[    0.206254] pnp 00:0c: mem resource (0xd1800-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206258] pnp 00:0c: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206261] pnp 00:0c: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206263] pnp 00:0c: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206266] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206269] pnp 00:0c: mem resource (0x100000-0xbfddffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206336] pnp: PnP ACPI: found 13 devices
[    0.206337] ACPI: ACPI bus type pnp unregistered
[    0.206340] PnPBIOS: Disabled by ACPI PNP
[    0.206349] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.206351] system 00:01: ioport range 0x220-0x225 has been reserved
[    0.206353] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.206358] system 00:02: ioport range 0x4100-0x411f has been reserved
[    0.206360] system 00:02: ioport range 0x228-0x22f has been reserved
[    0.206362] system 00:02: ioport range 0x238-0x23f has been reserved
[    0.206365] system 00:02: ioport range 0x40b-0x40b has been reserved
[    0.206367] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.206370] system 00:02: ioport range 0xc00-0xc01 has been reserved
[    0.206372] system 00:02: ioport range 0xc14-0xc14 has been reserved
[    0.206374] system 00:02: ioport range 0xc50-0xc52 has been reserved
[    0.206379] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[    0.206381] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[    0.206384] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[    0.206386] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[    0.206389] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[    0.206391] system 00:02: ioport range 0x4000-0x40fe has been reserved
[    0.206393] system 00:02: ioport range 0x4210-0x4217 has been reserved
[    0.206396] system 00:02: ioport range 0xb00-0xb0f has been reserved
[    0.206398] system 00:02: ioport range 0xb10-0xb1f has been reserved
[    0.206401] system 00:02: ioport range 0xb20-0xb3f has been reserved
[    0.206406] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.206411] system 00:0c: iomem range 0xbfde0000-0xbfdfffff could not be reserved
[    0.206413] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.206416] system 00:0c: iomem range 0xbfef0000-0xcfeeffff could not be reserved
[    0.206418] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.206421] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.206423] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.241049] AppArmor: AppArmor Filesystem Enabled
[    0.241076] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.241079] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.241082] pci 0000:00:01.0:   MEM window: 0xfde00000-0xfdffffff
[    0.241085] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.241090] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.241092] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
[    0.241095] pci 0000:00:0a.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.241098] pci 0000:00:0a.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.241102] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.241105] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.241111] pci 0000:00:14.4:   MEM window: 0xfdc00000-0xfdcfffff
[    0.241115] pci 0000:00:14.4:   PREFETCH window: 0xfdb00000-0xfdbfffff
[    0.241128]   alloc irq_desc for 18 on node -1
[    0.241129]   alloc kstat_irqs on node -1
[    0.241138] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.241141] pci 0000:00:0a.0: setting latency timer to 64
[    0.241149] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.241151] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.241153] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.241155] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdffffff]
[    0.241157] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.241159] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.241161] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.241163] pci_bus 0000:02: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.241165] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.241167] pci_bus 0000:03: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.241169] pci_bus 0000:03: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.241171] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.241173] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.241201] NET: Registered protocol family 2
[    0.241274] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.241521] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.242022] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.242278] TCP: Hash tables configured (established 131072 bind 65536)
[    0.242280] TCP reno registered
[    0.242354] NET: Registered protocol family 1
[    0.242404] Trying to unpack rootfs image as initramfs...
[    0.393693] Freeing initrd memory: 7468k freed
[    0.397300] cpufreq-nforce2: No nForce2 chipset.
[    0.397320] Scanning for low memory corruption every 60 seconds
[    0.397398] audit: initializing netlink socket (disabled)
[    0.397408] type=2000 audit(1263437164.396:1): initialized
[    0.404026] highmem bounce pool size: 64 pages
[    0.404030] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.405133] VFS: Disk quotas dquot_6.5.2
[    0.405175] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.405596] fuse init (API version 7.12)
[    0.405657] msgmni has been set to 1679
[    0.405850] alg: No test for stdrng (krng)
[    0.405868] io scheduler noop registered
[    0.405870] io scheduler anticipatory registered
[    0.405871] io scheduler deadline registered
[    0.405904] io scheduler cfq registered (default)
[    1.232028] pci 0000:00:12.1: OHCI: BIOS handoff failed (BIOS bug?) 00000184
[    1.304045] pci 0000:01:05.0: Boot video device
[    1.304153]   alloc irq_desc for 25 on node -1
[    1.304155]   alloc kstat_irqs on node -1
[    1.304161] pcieport-driver 0000:00:0a.0: irq 25 for MSI/MSI-X
[    1.304167] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.304227] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.304244] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.304336] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.304339] ACPI: Power Button [PWRF]
[    1.304375] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.304377] ACPI: Power Button [PWRB]
[    1.304616] processor LNXCPU:00: registered as cooling_device0
[    1.304646] processor LNXCPU:01: registered as cooling_device1
[    1.305989] isapnp: Scanning for PnP cards...
[    1.659725] isapnp: No Plug & Play device found
[    1.660602] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.660715] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.660990] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.661726] brd: module loaded
[    1.662066] loop: module loaded
[    1.662120] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.662171] ahci 0000:00:11.0: version 3.0
[    1.662186]   alloc irq_desc for 22 on node -1
[    1.662188]   alloc kstat_irqs on node -1
[    1.662197] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.662233]   alloc irq_desc for 26 on node -1
[    1.662234]   alloc kstat_irqs on node -1
[    1.662244] ahci 0000:00:11.0: irq 26 for MSI/MSI-X
[    1.662361] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.662364] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.662906] scsi0 : ahci
[    1.663014] scsi1 : ahci
[    1.663069] scsi2 : ahci
[    1.663123] scsi3 : ahci
[    1.663179] scsi4 : ahci
[    1.663234] scsi5 : ahci
[    1.663345] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 26
[    1.663349] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 26
[    1.663352] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 26
[    1.663356] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 26
[    1.663359] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 26
[    1.663363] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 26
[    1.663568]   alloc irq_desc for 16 on node -1
[    1.663570]   alloc kstat_irqs on node -1
[    1.663578] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.663695] scsi6 : pata_atiixp
[    1.663753] scsi7 : pata_atiixp
[    1.664571] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.664574] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.665114] Fixed MDIO Bus: probed
[    1.665141] PPP generic driver version 2.4.2
[    1.665220] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.665235]   alloc irq_desc for 17 on node -1
[    1.665237]   alloc kstat_irqs on node -1
[    1.665245] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.665260] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.665300] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.665320] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.665338] ehci_hcd 0000:00:12.2: debug port 1
[    1.665362] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.676030] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.676082] usb usb1: configuration #1 chosen from 1 choice
[    1.676105] hub 1-0:1.0: USB hub found
[    1.676112] hub 1-0:1.0: 6 ports detected
[    1.676162]   alloc irq_desc for 19 on node -1
[    1.676163]   alloc kstat_irqs on node -1
[    1.676170] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.676177] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.676200] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.676217] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.676234] ehci_hcd 0000:00:13.2: debug port 1
[    1.676256] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.688027] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.688069] usb usb2: configuration #1 chosen from 1 choice
[    1.688087] hub 2-0:1.0: USB hub found
[    1.688092] hub 2-0:1.0: 6 ports detected
[    1.688141] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.688153] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.688160] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.688187] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.688215] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.748059] usb usb3: configuration #1 chosen from 1 choice
[    1.748078] hub 3-0:1.0: USB hub found
[    1.748086] hub 3-0:1.0: 3 ports detected
[    1.748127] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.748134] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.748158] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.748172] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.808061] usb usb4: configuration #1 chosen from 1 choice
[    1.808080] hub 4-0:1.0: USB hub found
[    1.808088] hub 4-0:1.0: 3 ports detected
[    1.808127] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.808134] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.808156] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.808182] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.868058] usb usb5: configuration #1 chosen from 1 choice
[    1.868077] hub 5-0:1.0: USB hub found
[    1.868089] hub 5-0:1.0: 3 ports detected
[    1.868130] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.868137] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.868163] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.868176] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    1.928056] usb usb6: configuration #1 chosen from 1 choice
[    1.928075] hub 6-0:1.0: USB hub found
[    1.928083] hub 6-0:1.0: 3 ports detected
[    1.928127] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.928134] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.928156] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.928169] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    1.948977] ata7.00: ATAPI: HITACHI DVD-ROM GD-7500, 0008, max UDMA/33
[    1.948998] ata7.01: ATAPI: R/RW 8x4x32,     D2,2, max MWDMA2
[    1.964431] ata7.00: configured for UDMA/33
[    1.980036] ata4: SATA link down (SStatus 0 SControl 300)
[    1.980064] ata3: SATA link down (SStatus 0 SControl 300)
[    1.980111] ata6: SATA link down (SStatus 0 SControl 300)
[    1.980138] ata2: SATA link down (SStatus 0 SControl 300)
[    1.980164] ata5: SATA link down (SStatus 0 SControl 300)
[    1.980716] ata7.01: configured for MWDMA2
[    1.988053] usb usb7: configuration #1 chosen from 1 choice
[    1.988072] hub 7-0:1.0: USB hub found
[    1.988080] hub 7-0:1.0: 2 ports detected
[    1.988128] uhci_hcd: USB Universal Host Controller Interface driver
[    1.988196] PNP: No PS/2 controller found. Probing ports directly.
[    2.022630] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    2.022632] If AUX port is really absent please use the 'i8042.noaux' option.
[    2.144016] ata1: softreset failed (device not ready)
[    2.144019] ata1: applying SB600 PMP SRST workaround and retrying
[    2.272116] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.272165] mice: PS/2 mouse device common for all mice
[    2.272245] rtc_cmos 00:05: RTC can wake from S4
[    2.272272] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.272307] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.272385] device-mapper: uevent: version 1.0.3
[    2.272468] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.272558] device-mapper: multipath: version 1.1.0 loaded
[    2.272560] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.272667] EISA: Probing bus 0 at eisa.0
[    2.272684] Cannot allocate resource for EISA slot 4
[    2.272701] EISA: Detected 0 cards.
[    2.272824] cpuidle: using governor ladder
[    2.272826] cpuidle: using governor menu
[    2.273194] TCP cubic registered
[    2.273305] NET: Registered protocol family 10
[    2.273653] lo: Disabled Privacy Extensions
[    2.273883] NET: Registered protocol family 17
[    2.273896] Bluetooth: L2CAP ver 2.13
[    2.273898] Bluetooth: L2CAP socket layer initialized
[    2.273900] Bluetooth: SCO (Voice Link) ver 0.6
[    2.273902] Bluetooth: SCO socket layer initialized
[    2.273934] Bluetooth: RFCOMM TTY layer initialized
[    2.273936] Bluetooth: RFCOMM socket layer initialized
[    2.273938] Bluetooth: RFCOMM ver 1.11
[    2.273952] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ processors (2 cpu cores) (version 2.20.00)
[    2.273994] powernow-k8:    0 : fid 0x14 (2800 MHz), vid 0xa
[    2.273996] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xc
[    2.273998] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xe
[    2.274000] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0x10
[    2.274002] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x10
[    2.274004] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x10
[    2.274006] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
[    2.274037] Using IPI No-Shortcut mode
[    2.274085] PM: Resume from disk failed.
[    2.274096] registered taskstats version 1
[    2.274210]   Magic number: 10:464:763
[    2.274299] rtc_cmos 00:05: setting system clock to 2010-01-14 02:46:07 UTC (1263437167)
[    2.274302] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.274304] EDD information not available.
[    2.284513] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    2.309990] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.310701] ata1.00: ATA-8: WDC WD5000AACS-00G8B1, 05.04C05, max UDMA/133
[    2.310703] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.311956] ata1.00: configured for UDMA/133
[    2.324102] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 05.0 PQ: 0 ANSI: 5
[    2.324199] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.324231] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.324264] sd 0:0:0:0: [sda] Write Protect is off
[    2.324266] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.324283] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.324377]  sda:
[    2.330690] scsi 6:0:0:0: CD-ROM            HITACHI  DVD-ROM GD-7500  0008 PQ: 0 ANSI: 5
[    2.332438]  sda1 sda2 <sr0: scsi3-mmc drive: 14x/40x cd/rw xa/form2 cdda tray
[    2.343321] Uniform CD-ROM driver Revision: 3.20
[    2.343385] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    2.343415] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    2.345052] scsi 6:0:1:0: CD-ROM            IDE-CD   R/RW 8x4x32      D2,2 PQ: 0 ANSI: 5
[    2.350682] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    2.350731] sr 6:0:1:0: Attached scsi CD-ROM sr1
[    2.350758] sr 6:0:1:0: Attached scsi generic sg2 type 5
[    2.357783]  sda5 >
[    2.357954] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.452122] usb 3-1: configuration #1 chosen from 1 choice
[    2.504599] Freeing unused kernel memory: 540k freed
[    2.504923] Write protecting the kernel text: 4568k
[    2.504954] Write protecting the kernel read-only data: 1836k
[    2.618529] Floppy drive(s): fd0 is 1.44M
[    2.633558] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.633577] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.633610] r8169 0000:02:00.0: setting latency timer to 64
[    2.633643]   alloc irq_desc for 27 on node -1
[    2.633645]   alloc kstat_irqs on node -1
[    2.633657] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    2.634129] eth0: RTL8168c/8111c at 0xf8050000, 00:1f:d0:5b:f5:64, XID 3c4000c0 IRQ 27
[    2.648153] ohci1394 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.658834] FDC 0 is a post-1991 82077
[    2.676775] usbcore: registered new interface driver hiddev
[    2.681829] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input3
[    2.681890] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.0-1/input0
[    2.681904] usbcore: registered new interface driver usbhid
[    2.681907] usbhid: v2.6:USB HID core driver
[    2.704074] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.724526] usb 3-2: new low speed USB device using ohci_hcd and address 3
[    2.905164] usb 3-2: configuration #1 chosen from 1 choice
[    2.918325] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4
[    2.918377] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:12.0-2/input0
[    2.934223] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input5
[    2.934283] microsoft 0003:045E:00DB.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:12.0-2/input1
[    3.278614] PM: Starting manual resume from disk
[    3.278618] PM: Resume from partition 8:5
[    3.278619] PM: Checking hibernation image.
[    3.278744] PM: Resume from disk failed.
[    3.284178] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.284181] EXT3-fs: write access will be enabled during recovery.
[    3.976115] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0072d77200001fd0]
[    5.875191] kjournald starting.  Commit interval 5 seconds
[    5.875205] EXT3-fs: sda1: orphan cleanup on readonly fs
[    5.875210] ext3_orphan_cleanup: deleting unreferenced inode 6725730
[    5.875244] ext3_orphan_cleanup: deleting unreferenced inode 6725727
[    5.889325] ext3_orphan_cleanup: deleting unreferenced inode 6725721
[    5.889333] ext3_orphan_cleanup: deleting unreferenced inode 6725717
[    5.889341] ext3_orphan_cleanup: deleting unreferenced inode 6725713
[    5.889348] ext3_orphan_cleanup: deleting unreferenced inode 6725712
[    5.897423] ext3_orphan_cleanup: deleting unreferenced inode 6725700
[    5.900577] ext3_orphan_cleanup: deleting unreferenced inode 6701111
[    5.911906] EXT3-fs: sda1: 8 orphan inodes deleted
[    5.911908] EXT3-fs: recovery complete.
[    5.916789] EXT3-fs: mounted filesystem with writeback data mode.
[    6.487031] type=1505 audit(1263437171.709:2): operation="profile_load" pid=453 name=/usr/share/gdm/guest-session/Xsession
[    6.511873] type=1505 audit(1263437171.734:3): operation="profile_load" pid=454 name=/sbin/dhclient3
[    6.512084] type=1505 audit(1263437171.734:4): operation="profile_load" pid=454 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.512203] type=1505 audit(1263437171.734:5): operation="profile_load" pid=454 name=/usr/lib/connman/scripts/dhclient-script
[    6.540243] type=1505 audit(1263437171.762:6): operation="profile_load" pid=455 name=/usr/bin/evince
[    6.543790] type=1505 audit(1263437171.766:7): operation="profile_load" pid=455 name=/usr/bin/evince-previewer
[    6.545916] type=1505 audit(1263437171.770:8): operation="profile_load" pid=455 name=/usr/bin/evince-thumbnailer
[    6.565205] type=1505 audit(1263437171.790:9): operation="profile_load" pid=457 name=/usr/lib/cups/backend/cups-pdf
[    6.565468] type=1505 audit(1263437171.790:10): operation="profile_load" pid=457 name=/usr/sbin/cupsd
[    6.571699] type=1505 audit(1263437171.794:11): operation="profile_load" pid=458 name=/usr/sbin/tcpdump
[    7.451934] Adding 9060620k swap on /dev/sda5.  Priority:-1 extents:1 across:9060620k 
[    7.717289] udev: starting version 147
[    8.314897] EXT3 FS on sda1, internal journal
[    9.048831] parport_pc 00:0a: reported by Plug and Play ACPI
[    9.048892] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.058526] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    9.058528] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    9.058552] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.060710] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    9.068992] Linux agpgart interface v0.103
[    9.079733] ppdev: user-space parallel port driver
[    9.105985] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    9.105989] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.119239] lp: driver loaded but no devices found
[    9.152139] lp0: using parport0 (interrupt-driven).
[    9.384476] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.384481] Disabling lock debugging due to kernel taint
[    9.402729] [fglrx] Maximum main memory to use for locked dma buffers: 2876 MBytes.
[    9.402749] [fglrx]   vendor: 1002 device: 9610 count: 1
[    9.402991] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[    9.403004] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.403008] pci 0000:01:05.0: setting latency timer to 64
[    9.403264] [fglrx] Kernel PAT support is enabled
[    9.403283] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[    9.715645] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.148401] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.247681] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
[   10.247864] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   10.251570] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   10.251590] HDA Intel 0000:01:05.1: setting latency timer to 64
[   13.769214] r8169: eth0: link up
[   13.769220] r8169: eth0: link upE]

---

### Post by sf9753 on 2010-01-29
```

```Jan 17 07:50:25 HP-AMD-Gigabyte-rebuild rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="796" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 18 07:47:14 HP-AMD-Gigabyte-rebuild rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="796" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 19 08:02:00 HP-AMD-Gigabyte-rebuild rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="796" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 20 07:39:13 HP-AMD-Gigabyte-rebuild rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="796" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 21 07:58:55 HP-AMD-Gigabyte-rebuild rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="796" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 22 07:44:24 HP-AMD-Gigabyte-rebuild rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="796" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 23 07:52:57 HP-AMD-Gigabyte-rebuild rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="796" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 23 20:03:00 HP-AMD-Gigabyte-rebuild kernel: Kernel logging (proc) stopped.

---

### Post by sf9753 on 2010-01-29
```

```Jan 18 05:28:20 HP-AMD-Gigabyte-rebuild kernel: [376941.217525] UDP: short packet: From 0.0.0.0:138 14627/209 to 0.16.133.246:138

---

### Post by sf9753 on 2010-01-29
I hope these are what you were asking for.  Once again, I'm out of my element.  I appreciate any help.

---

### Post by lidex on 2010-01-29
Go to this page and follow the instructions for the bootinfo script then paste the results file into your next post. Also, if you would please, go back into your dmesg post and fix the code tags so it's in a more readable format. It should look like this: 
[CODE*]text[/CODE] (leave out the asterisk) where text = the entire dmesg file. Thanks.

OOOPS -> here's the link:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by sf9753 on 2010-01-30
The boot info script download leads to the question of what application I should use to open the link.  I'm using the CD to run 8.04, and am not coming up with an application that opens this script.  

Sorry to be so ignorant, but I need help even at this basic level.

---

### Post by lidex on 2010-01-31
You need to follow the instructions on that page. Download the script to your desktop and in a terminal run this command:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
You will now have the file RESULTS.txt in the same directory as the script. You can open that file in a text editor - gedit, for example.

---

