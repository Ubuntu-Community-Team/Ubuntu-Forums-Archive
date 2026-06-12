---
title: "kernel problem"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by irakla7777777 on 2010-08-11
hi all
I have compiled a new kernel 2.6.35 and I can not boot because same error :
kernel panic - Unable to mount root fs on unknown-block(0,0).
i have motherboard ga-p55a-ud3r and controlleris sata .now i use channel in ACHI mode. when i change it in ide mode it boots but in low graphic mode. then i have compiled modules again with support ACHI_SATA mdoe in xconfig of kernel. but same error occur.
can anyone help me


thanks

---

### Post by Fludizz on 2010-08-11
Did you compile the AHCI_SATA support into the kernel or specific as a module? In the last case, did you generate a propper initrd image for your kernel to boot from?

I have had the same issue but then when booting for md raid ;) abbandoned the attempts and used stock kernels before I figured my initrd image wasn't generated for the custom kernel.

---

### Post by irakla7777777 on 2010-08-11
yes i compined it for ACHI_SATA but same error occurs

---

### Post by irakla7777777 on 2010-08-11
nobody knows about this ?

---

### Post by regala on 2010-08-11
> **irakla7777777 said:**
> nobody knows about this ?

could you at least attach your kernel config, and your dmesg ? not every single reader here has got his own crystal ball to try and guess what is the problem...

---

### Post by irakla7777777 on 2010-08-11
ika@unix:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fbe0000 (usable)
[    0.000000]  BIOS-e820: 000000007fbe0000 - 000000007fbe1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fbe1000 - 000000007fbf0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fbf0000 - 000000007fc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7fbe0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fbe0000 (usable)
[    0.000000]  modified: 000000007fbe0000 - 000000007fbe1000 (ACPI NVS)
[    0.000000]  modified: 000000007fbe1000 - 000000007fbf0000 (ACPI data)
[    0.000000]  modified: 000000007fbf0000 - 000000007fc00000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37858000 - 37fefd45
[    0.000000] Allocated new RAMDISK: 008e0000 - 01077d45
[    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fefd44 to 008e0000 - 01077d44
[    0.000000] ACPI: RSDP 000f70f0 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 7fbe1040 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 7fbe10c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 7fbe1180 0529E (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 7fbe0000 00040
[    0.000000] ACPI: HPET 7fbe6580 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 7fbe6600 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: EUDS 7fbe6640 00560 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 7fbe6ba0 00A32 (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 7fbe6480 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 7fbe7600 01AF0 (v01  INTEL PPM RCM  80000001 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1155MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df0f6]              BRK ==> [00008dc000 - 00008df0f6]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e0000 - 0001077d45]      NEW RAMDISK ==> [00008e0000 - 0001077d45]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f5730] f5730
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fbe0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007fbe0
[    0.000000] On node 0 totalpages: 523129
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c1079000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2312 pages used for memmap
[    0.000000]   HighMem zone: 293594 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7fc00000 (gap: 7fc00000:70400000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u524288
[    0.000000] pcpu-alloc: s36056 r0 d21288 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519041
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=9eb1451f-5810-4508-b99e-bc1a5e42c94d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10464640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fbe0)
[    0.000000] Memory: 2047408k/2092928k available (4679k kernel code, 43728k reserved, 2116k data, 660k init, 1183624k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:472
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 25 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 26 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 27 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000]   alloc irq_desc for 28 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2664.734 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5329.46 BogoMIPS (lpj=10658936)
[    0.000012] Security Framework initialized
[    0.000024] AppArmor: AppArmor initialized
[    0.000028] Mount-cache hash table entries: 512
[    0.000101] Initializing cgroup subsys ns
[    0.000104] Initializing cgroup subsys cpuacct
[    0.000107] Initializing cgroup subsys memory
[    0.000110] Initializing cgroup subsys devices
[    0.000112] Initializing cgroup subsys freezer
[    0.000113] Initializing cgroup subsys net_cls
[    0.000124] CPU: Physical Processor ID: 0
[    0.000125] CPU: Processor Core ID: 0
[    0.000128] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000129] CPU: L2 cache: 256K
[    0.000130] CPU: L3 cache: 8192K
[    0.000133] mce: CPU supports 9 MCE banks
[    0.000141] CPU0: Thermal monitoring enabled (TM1)
[    0.000144] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 CMCI:8
[    0.000150] using mwait in idle threads.
[    0.000153] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
[    0.000158] ... version:                3
[    0.000159] ... bit width:              48
[    0.000160] ... generic registers:      4
[    0.000161] ... value mask:             0000ffffffffffff
[    0.000162] ... max period:             000000007fffffff
[    0.000164] ... fixed-purpose events:   3
[    0.000165] ... event mask:             000000070000000f
[    0.000167] Checking 'hlt' instruction... OK.
[    0.014328] ACPI: Core revision 20090903
[    0.022443] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.022446] ftrace: allocating 21780 entries in 43 pages
[    0.027798] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028124] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067778] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.172531] Booting processor 1 APIC 0x2 ip 0x6000
[    0.183134] Initializing CPU#1
[    0.260388] CPU: Physical Processor ID: 0
[    0.260389] CPU: Processor Core ID: 1
[    0.260391] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.260392] CPU: L2 cache: 256K
[    0.260393] CPU: L3 cache: 8192K
[    0.260402] CPU1: Thermal monitoring enabled (TM1)
[    0.260405] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.260495] CPU1: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.260505] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280558] Booting processor 2 APIC 0x4 ip 0x6000
[    0.290829] Initializing CPU#2
[    0.368306] CPU: Physical Processor ID: 0
[    0.368307] CPU: Processor Core ID: 2
[    0.368309] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.368310] CPU: L2 cache: 256K
[    0.368311] CPU: L3 cache: 8192K
[    0.368320] CPU2: Thermal monitoring enabled (TM1)
[    0.368323] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.368427] CPU2: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.368438] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.388488] Booting processor 3 APIC 0x6 ip 0x6000
[    0.398760] Initializing CPU#3
[    0.476224] CPU: Physical Processor ID: 0
[    0.476225] CPU: Processor Core ID: 3
[    0.476227] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.476228] CPU: L2 cache: 256K
[    0.476229] CPU: L3 cache: 8192K
[    0.476238] CPU3: Thermal monitoring enabled (TM1)
[    0.476241] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.476251] CPU3: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.476263] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.496264] Brought up 4 CPUs
[    0.496266] Total of 4 processors activated (21317.44 BogoMIPS).
[    0.497554] CPU0 attaching sched-domain:
[    0.497557]  domain 0: span 0-3 level MC
[    0.497558]   groups: 0 1 2 3
[    0.497563] CPU1 attaching sched-domain:
[    0.497565]  domain 0: span 0-3 level MC
[    0.497566]   groups: 1 2 3 0
[    0.497569] CPU2 attaching sched-domain:
[    0.497570]  domain 0: span 0-3 level MC
[    0.497572]   groups: 2 3 0 1
[    0.497575] CPU3 attaching sched-domain:
[    0.497576]  domain 0: span 0-3 level MC
[    0.497577]   groups: 3 0 1 2
[    0.497740] devtmpfs: initialized
[    0.497991] regulator: core version 0.5
[    0.498015] Time: 23:06:06  Date: 08/11/10
[    0.498044] NET: Registered protocol family 16
[    0.498107] Trying to unpack rootfs image as initramfs...
[    0.498117] EISA bus registered
[    0.498123] ACPI: bus type pci registered
[    0.498165] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.498167] PCI: MCFG area at f0000000 reserved in E820
[    0.498168] PCI: Using MMCONFIG for extended config space
[    0.498169] PCI: Using configuration type 1 for base access
[    0.498737] bio: create slab <bio-0> at 0
[    0.499238] ACPI: EC: Look up EC in DSDT
[    0.503372] ACPI: Interpreter enabled
[    0.503384] ACPI: (supports S0 S3 S4 S5)
[    0.503398] ACPI: Using IOAPIC for interrupt routing
[    0.507338] ACPI Warning: Incorrect checksum in table [TAMG] - 10, should be 0F (20090903/tbutils-314)
[    0.507432] ACPI: No dock devices found.
[    0.507493] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.507589] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.507592] pci 0000:00:03.0: PME# disabled
[    0.507837] pci 0000:00:1a.0: reg 20 io port: [0xff00-0xff1f]
[    0.507898] pci 0000:00:1a.1: reg 20 io port: [0xfe00-0xfe1f]
[    0.507960] pci 0000:00:1a.2: reg 20 io port: [0xfd00-0xfd1f]
[    0.508024] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfbfff000-0xfbfff3ff]
[    0.508074] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.508077] pci 0000:00:1a.7: PME# disabled
[    0.508114] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfbff8000-0xfbffbfff]
[    0.508151] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.508154] pci 0000:00:1b.0: PME# disabled
[    0.508213] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.508216] pci 0000:00:1c.0: PME# disabled
[    0.508275] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.508278] pci 0000:00:1c.1: PME# disabled
[    0.508329] pci 0000:00:1d.0: reg 20 io port: [0xfc00-0xfc1f]
[    0.508390] pci 0000:00:1d.1: reg 20 io port: [0xfb00-0xfb1f]
[    0.508451] pci 0000:00:1d.2: reg 20 io port: [0xfa00-0xfa1f]
[    0.508512] pci 0000:00:1d.3: reg 20 io port: [0xf900-0xf91f]
[    0.508576] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfbffe000-0xfbffe3ff]
[    0.508625] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.508629] pci 0000:00:1d.7: PME# disabled
[    0.508794] pci 0000:00:1f.2: reg 10 io port: [0xf800-0xf807]
[    0.508799] pci 0000:00:1f.2: reg 14 io port: [0xf700-0xf703]
[    0.508804] pci 0000:00:1f.2: reg 18 io port: [0xf600-0xf607]
[    0.508808] pci 0000:00:1f.2: reg 1c io port: [0xf500-0xf503]
[    0.508813] pci 0000:00:1f.2: reg 20 io port: [0xf400-0xf41f]
[    0.508818] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfbffd000-0xfbffd7ff]
[    0.508846] pci 0000:00:1f.2: PME# supported from D3hot
[    0.508848] pci 0000:00:1f.2: PME# disabled
[    0.508873] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfbffc000-0xfbffc0ff]
[    0.508884] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.508926] pci 0000:01:00.0: reg 10 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.508933] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.508941] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf6000000-0xf7ffffff]
[    0.508946] pci 0000:01:00.0: reg 24 io port: [0xcf00-0xcf7f]
[    0.508950] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.508993] pci 0000:00:03.0: bridge io port: [0xc000-0xcfff]
[    0.508995] pci 0000:00:03.0: bridge 32bit mmio: [0xf6000000-0xf9ffffff]
[    0.508999] pci 0000:00:03.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.509033] pci 0000:00:1c.0: bridge io port: [0xe000-0xefff]
[    0.509036] pci 0000:00:1c.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.509081] pci 0000:03:00.0: reg 10 io port: [0xde00-0xdeff]
[    0.509099] pci 0000:03:00.0: reg 18 64bit mmio pref: [0xfbcff000-0xfbcfffff]
[    0.509112] pci 0000:03:00.0: reg 20 64bit mmio pref: [0xfbcf8000-0xfbcfbfff]
[    0.509120] pci 0000:03:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.509157] pci 0000:03:00.0: supports D1 D2
[    0.509158] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.509162] pci 0000:03:00.0: PME# disabled
[    0.509213] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.509217] pci 0000:00:1c.1: bridge 32bit mmio: [0xfbd00000-0xfbdfffff]
[    0.509221] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfbc00000-0xfbcfffff]
[    0.509263] pci 0000:00:1e.0: transparent bridge
[    0.509284] pci_bus 0000:00: on NUMA node 0
[    0.509287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.509478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.509517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.509570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.525890] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.525962] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.526032] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.526102] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.526172] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.526243] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.526313] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.526384] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.526453] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.526455] vgaarb: loaded
[    0.526522] SCSI subsystem initialized
[    0.526579] libata version 3.00 loaded.
[    0.526620] usbcore: registered new interface driver usbfs
[    0.526627] usbcore: registered new interface driver hub
[    0.526643] usbcore: registered new device driver usb
[    0.526719] ACPI: WMI: Mapper loaded
[    0.526720] PCI: Using ACPI for IRQ routing
[    0.526831] NetLabel: Initializing
[    0.526832] NetLabel:  domain hash size = 128
[    0.526833] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.526841] NetLabel:  unlabeled traffic allowed by default
[    0.526866] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
[    0.526871] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.532191] hpet: hpet2 irq 24 for MSI
[    0.532536] hpet: hpet3 irq 25 for MSI
[    0.536343] hpet: hpet4 irq 26 for MSI
[    0.540247] hpet: hpet5 irq 27 for MSI
[    0.540266] Switching to clocksource tsc
[    0.541950] AppArmor: AppArmor Filesystem Enabled
[    0.541957] pnp: PnP ACPI init
[    0.541966] ACPI: bus type pnp registered
[    0.543978] pnp: PnP ACPI: found 14 devices
[    0.543979] ACPI: ACPI bus type pnp unregistered
[    0.543982] PnPBIOS: Disabled by ACPI PNP
[    0.543990] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.543992] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.543994] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.543995] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.543997] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.544002] system 00:0a: ioport range 0x400-0x4cf has been reserved
[    0.544004] system 00:0a: ioport range 0x4d2-0x4ff has been reserved
[    0.544007] system 00:0b: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.544011] system 00:0c: iomem range 0xcf800-0xcffff has been reserved
[    0.544013] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.544015] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.544017] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.544019] system 00:0c: iomem range 0x7fbe0000-0x7fbeffff could not be reserved
[    0.544021] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.544022] system 00:0c: iomem range 0x100000-0x7fbdffff could not be reserved
[    0.544024] system 00:0c: iomem range 0x7fbf0000-0x7fbfffff has been reserved
[    0.544026] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.544028] system 00:0c: iomem range 0xfed10000-0xfed1dfff has been reserved
[    0.544030] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.544032] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.544034] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.544036] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[    0.544037] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.578631] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.578634] pci 0000:00:03.0:   IO window: 0xc000-0xcfff
[    0.578638] pci 0000:00:03.0:   MEM window: 0xf6000000-0xf9ffffff
[    0.578640] pci 0000:00:03.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.578644] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.578647] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
[    0.578651] pci 0000:00:1c.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.578654] pci 0000:00:1c.0:   PREFETCH window: 0x00000080000000-0x000000801fffff
[    0.578659] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.578661] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.578665] pci 0000:00:1c.1:   MEM window: 0xfbd00000-0xfbdfffff
[    0.578668] pci 0000:00:1c.1:   PREFETCH window: 0x000000fbc00000-0x000000fbcfffff
[    0.578673] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.578674] pci 0000:00:1e.0:   IO window: disabled
[    0.578678] pci 0000:00:1e.0:   MEM window: disabled
[    0.578681] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.578692]   alloc irq_desc for 16 on node -1
[    0.578693]   alloc kstat_irqs on node -1
[    0.578697] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.578701] pci 0000:00:03.0: setting latency timer to 64
[    0.578708] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.578711] pci 0000:00:1c.0: setting latency timer to 64
[    0.578717]   alloc irq_desc for 17 on node -1
[    0.578718]   alloc kstat_irqs on node -1
[    0.578721] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.578724] pci 0000:00:1c.1: setting latency timer to 64
[    0.578730] pci 0000:00:1e.0: setting latency timer to 64
[    0.578733] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.578735] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.578737] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.578738] pci_bus 0000:01: resource 1 mem: [0xf6000000-0xf9ffffff]
[    0.578740] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.578742] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.578743] pci_bus 0000:02: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.578745] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x801fffff]
[    0.578747] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.578748] pci_bus 0000:03: resource 1 mem: [0xfbd00000-0xfbdfffff]
[    0.578750] pci_bus 0000:03: resource 2 pref mem [0xfbc00000-0xfbcfffff]
[    0.578752] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.578753] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.578776] NET: Registered protocol family 2
[    0.578838] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.579017] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.579541] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.579802] TCP: Hash tables configured (established 131072 bind 65536)
[    0.579804] TCP reno registered
[    0.579854] NET: Registered protocol family 1
[    0.608422] pci 0000:01:00.0: Boot video device
[    0.608612] cpufreq-nforce2: No nForce2 chipset.
[    0.608627] Scanning for low memory corruption every 60 seconds
[    0.608694] audit: initializing netlink socket (disabled)
[    0.608700] type=2000 audit(1281567965.460:1): initialized
[    0.616165] highmem bounce pool size: 64 pages
[    0.616168] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.617119] VFS: Disk quotas dquot_6.5.2
[    0.617153] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.617505] fuse init (API version 7.13)
[    0.617557] msgmni has been set to 1689
[    0.617711] alg: No test for stdrng (krng)
[    0.617745] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.617747] io scheduler noop registered
[    0.617749] io scheduler anticipatory registered
[    0.617750] io scheduler deadline registered
[    0.617774] io scheduler cfq registered (default)
[    0.617870]   alloc irq_desc for 29 on node -1
[    0.617872]   alloc kstat_irqs on node -1
[    0.617878] pcieport 0000:00:03.0: irq 29 for MSI/MSI-X
[    0.617883] pcieport 0000:00:03.0: setting latency timer to 64
[    0.617966]   alloc irq_desc for 30 on node -1
[    0.617967]   alloc kstat_irqs on node -1
[    0.617972] pcieport 0000:00:1c.0: irq 30 for MSI/MSI-X
[    0.617978] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.618062]   alloc irq_desc for 31 on node -1
[    0.618063]   alloc kstat_irqs on node -1
[    0.618068] pcieport 0000:00:1c.1: irq 31 for MSI/MSI-X
[    0.618074] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.618131] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    0.618138] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.618181] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.618236] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.618238] ACPI: Power Button [PWRB]
[    0.618272] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.618274] ACPI: Power Button [PWRF]
[    0.618888] Monitor-Mwait will be used to enter C-1 state
[    0.618905] Monitor-Mwait will be used to enter C-2 state
[    0.618920] Monitor-Mwait will be used to enter C-3 state
[    0.618947] processor LNXCPU:00: registered as cooling_device0
[    0.628512] processor LNXCPU:01: registered as cooling_device1
[    0.628997] processor LNXCPU:02: registered as cooling_device2
[    0.629503] processor LNXCPU:03: registered as cooling_device3
[    0.631082] isapnp: Scanning for PnP cards...
[    0.631823] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.631915] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.632177] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.632828] brd: module loaded
[    0.633105] loop: module loaded
[    0.633154] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.633379] Fixed MDIO Bus: probed
[    0.633398] PPP generic driver version 2.4.2
[    0.633417] tun: Universal TUN/TAP device driver, 1.6
[    0.633418] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.633467] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.633481]   alloc irq_desc for 18 on node -1
[    0.633483]   alloc kstat_irqs on node -1
[    0.633487] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.633494] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.633497] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.633515] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.633534] ehci_hcd 0000:00:1a.7: debug port 2
[    0.637427] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.637447] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbfff000
[    0.648377] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.648432] usb usb1: configuration #1 chosen from 1 choice
[    0.648449] hub 1-0:1.0: USB hub found
[    0.648454] hub 1-0:1.0: 6 ports detected
[    0.648495]   alloc irq_desc for 23 on node -1
[    0.648497]   alloc kstat_irqs on node -1
[    0.648500] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.648508] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.648511] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.648530] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.648549] ehci_hcd 0000:00:1d.7: debug port 2
[    0.652430] Freeing initrd memory: 7775k freed
[    0.652434] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.652445] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbffe000
[    0.664370] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.664441] usb usb2: configuration #1 chosen from 1 choice
[    0.664458] hub 2-0:1.0: USB hub found
[    0.664464] hub 2-0:1.0: 8 ports detected
[    0.664511] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.664522] uhci_hcd: USB Universal Host Controller Interface driver
[    0.664550] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.664556] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.664559] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.664579] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.664607] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    0.664660] usb usb3: configuration #1 chosen from 1 choice
[    0.664675] hub 3-0:1.0: USB hub found
[    0.664679] hub 3-0:1.0: 2 ports detected
[    0.664709]   alloc irq_desc for 21 on node -1
[    0.664710]   alloc kstat_irqs on node -1
[    0.664715] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.664719] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.664721] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.664739] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.664766] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    0.664818] usb usb4: configuration #1 chosen from 1 choice
[    0.664833] hub 4-0:1.0: USB hub found
[    0.664836] hub 4-0:1.0: 2 ports detected
[    0.664863] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.664867] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.664870] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.664887] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.664907] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
[    0.664959] usb usb5: configuration #1 chosen from 1 choice
[    0.664973] hub 5-0:1.0: USB hub found
[    0.664977] hub 5-0:1.0: 2 ports detected
[    0.665005] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.665009] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.665011] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.665032] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.665052] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    0.665111] usb usb6: configuration #1 chosen from 1 choice
[    0.665126] hub 6-0:1.0: USB hub found
[    0.665129] hub 6-0:1.0: 2 ports detected
[    0.665156]   alloc irq_desc for 19 on node -1
[    0.665157]   alloc kstat_irqs on node -1
[    0.665160] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.665166] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.665168] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.665186] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.665212] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    0.665264] usb usb7: configuration #1 chosen from 1 choice
[    0.665279] hub 7-0:1.0: USB hub found
[    0.665283] hub 7-0:1.0: 2 ports detected
[    0.665310] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.665314] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.665316] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.665335] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.665355] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    0.665407] usb usb8: configuration #1 chosen from 1 choice
[    0.665425] hub 8-0:1.0: USB hub found
[    0.665428] hub 8-0:1.0: 2 ports detected
[    0.665457] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.665461] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.665463] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.665481] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 9
[    0.665500] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000f900
[    0.665551] usb usb9: configuration #1 chosen from 1 choice
[    0.665566] hub 9-0:1.0: USB hub found
[    0.665569] hub 9-0:1.0: 2 ports detected
[    0.665630] PNP: No PS/2 controller found. Probing ports directly.
[    0.698710] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.698711] If AUX port is really absent please use the 'i8042.noaux' option.
[    0.948237] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.948286] mice: PS/2 mouse device common for all mice
[    0.948350] rtc_cmos 00:04: RTC can wake from S4
[    0.948371] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.948395] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.948454] device-mapper: uevent: version 1.0.3
[    0.948538] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.948603] device-mapper: multipath: version 1.1.0 loaded
[    0.948605] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.948672] EISA: Probing bus 0 at eisa.0
[    0.948695] EISA: Detected 0 cards.
[    0.948863] cpuidle: using governor ladder
[    0.948986] cpuidle: using governor menu
[    0.949253] TCP cubic registered
[    0.949346] NET: Registered protocol family 10
[    0.949621] lo: Disabled Privacy Extensions
[    0.949806] NET: Registered protocol family 17
[    0.950469] Using IPI No-Shortcut mode
[    0.950508] PM: Resume from disk failed.
[    0.950515] registered taskstats version 1
[    0.950844]   Magic number: 6:344:150
[    0.950856] bdi 1:2: hash matches
[    0.950871] acpi INT0800:00: hash matches
[    0.950903] rtc_cmos 00:04: setting system clock to 2010-08-11 23:06:06 UTC (1281567966)
[    0.950906] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.950907] EDD information not available.
[    0.996774] isapnp: No Plug & Play device found
[    0.996783] Freeing unused kernel memory: 660k freed
[    0.996946] Write protecting the kernel text: 4680k
[    0.996967] Write protecting the kernel read-only data: 1840k
[    1.006486] udev: starting version 151
[    1.025854] ahci 0000:00:1f.2: version 3.0
[    1.025868] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.025894]   alloc irq_desc for 32 on node -1
[    1.025896]   alloc kstat_irqs on node -1
[    1.025903] ahci 0000:00:1f.2: irq 32 for MSI/MSI-X
[    1.025933] ahci: SSS flag set, parallel bus scan disabled
[    1.031024] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.031036] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.031062] r8169 0000:03:00.0: setting latency timer to 64
[    1.031100]   alloc irq_desc for 33 on node -1
[    1.031102]   alloc kstat_irqs on node -1
[    1.031112] r8169 0000:03:00.0: irq 33 for MSI/MSI-X
[    1.031481] eth0: RTL8168d/8111d at 0xf8080000, 6c:f0:49:01:fb:d5, XID 083000c0 IRQ 33
[    1.037121] Floppy drive(s): fd0 is 1.44M
[    1.040138] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.040141] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems apst 
[    1.040145] ahci 0000:00:1f.2: setting latency timer to 64
[    1.055742] FDC 0 is a post-1991 82077
[    1.080101] scsi0 : ahci
[    1.080169] scsi1 : ahci
[    1.080204] scsi2 : ahci
[    1.080238] scsi3 : ahci
[    1.080272] scsi4 : ahci
[    1.080304] scsi5 : ahci
[    1.080410] ata1: SATA max UDMA/133 abar m2048@0xfbffd000 port 0xfbffd100 irq 32
[    1.080413] ata2: SATA max UDMA/133 abar m2048@0xfbffd000 port 0xfbffd180 irq 32
[    1.080415] ata3: SATA max UDMA/133 abar m2048@0xfbffd000 port 0xfbffd200 irq 32
[    1.080417] ata4: SATA max UDMA/133 abar m2048@0xfbffd000 port 0xfbffd280 irq 32
[    1.080419] ata5: SATA max UDMA/133 abar m2048@0xfbffd000 port 0xfbffd300 irq 32
[    1.080421] ata6: SATA max UDMA/133 abar m2048@0xfbffd000 port 0xfbffd380 irq 32
[    1.199976] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.374199] usb 3-1: configuration #1 chosen from 1 choice
[    1.539833] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.548222] ata1.00: ATA-8: WDC WD5000AAKS-22V1A0, 05.01D05, max UDMA/133
[    1.548228] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.549705] ata1.00: configured for UDMA/133
[    1.563929] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 05.0 PQ: 0 ANSI: 5
[    1.564056] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.564111] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.564138] sd 0:0:0:0: [sda] Write Protect is off
[    1.564140] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.564154] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.564232]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    1.590701] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.623730] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    1.835967] usb 3-2: configuration #1 chosen from 1 choice
[    1.842684] usbcore: registered new interface driver hiddev
[    1.855971] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input3
[    1.856012] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1a.0-1/input0
[    1.869033] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input4
[    1.869067] generic-usb 0003:1C4F:0002.0002: input,hidraw1: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:1a.0-2/input0
[    1.883542] ata2: SATA link down (SStatus 0 SControl 300)
[    2.219296] ata3: SATA link down (SStatus 0 SControl 300)
[    3.122642] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.124368] ata4.00: ATAPI: Optiarc DVD RW AD-7241S, 1.01, max UDMA/100
[    3.126462] ata4.00: configured for UDMA/100
[    3.143969] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7241S  1.01 PQ: 0 ANSI: 5
[    3.148827] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.148832] Uniform CD-ROM driver Revision: 3.20
[    3.148950] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.149015] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.466394] ata5: SATA link down (SStatus 0 SControl 300)
[    3.802147] ata6: SATA link down (SStatus 0 SControl 300)
[    4.235922] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   11.877699] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   11.877779] generic-usb 0003:1C4F:0002.0003: timeout initializing reports
[   11.877907] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input5
[   11.877968] generic-usb 0003:1C4F:0002.0003: input,hidraw2: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:1a.0-2/input1
[   11.877982] usbcore: registered new interface driver usbhid
[   11.877984] usbhid: v2.6:USB HID core driver
[   12.832072] udev: starting version 151
[   12.861221] lp: driver loaded but no devices found
[   12.879108] vga16fb: initializing
[   12.879110] vga16fb: mapped to 0xc00a0000
[   12.879165] fb0: VGA16 VGA frame buffer device
[   12.903607] Linux agpgart interface v0.103
[   12.924583] nvidia: module license 'NVIDIA' taints kernel.
[   12.924585] Disabling lock debugging due to kernel taint
[   12.939846] type=1505 audit(1281553578.497:2):  operation="profile_load" pid=632 name="/sbin/dhclient3"
[   12.940226] type=1505 audit(1281553578.497:3):  operation="profile_load" pid=632 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.940427] type=1505 audit(1281553578.497:4):  operation="profile_load" pid=632 name="/usr/lib/connman/scripts/dhclient-script"
[   13.393916] r8169: eth0: link up
[   13.393920] r8169: eth0: link up
[   13.432693] it87: Found IT8720F chip at 0x290, revision 8
[   13.432703] it87: in3 is VCC (+5V)
[   13.439295] parport_pc 00:09: reported by Plug and Play ACPI
[   13.439369] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   13.443117] ppdev: user-space parallel port driver
[   13.489802]   alloc irq_desc for 22 on node -1
[   13.489804]   alloc kstat_irqs on node -1
[   13.489809] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.489832] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.527146] lp0: using parport0 (interrupt-driven).
[   13.565985] hda_codec: ALC889: BIOS auto-probing.
[   13.567447] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   13.623047] Console: switching to colour frame buffer device 80x30
[   13.679868] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.679874] nvidia 0000:01:00.0: setting latency timer to 64
[   13.679878] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.679997] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   16.399850] CPU0 attaching NULL sched-domain.
[   16.399853] CPU1 attaching NULL sched-domain.
[   16.399855] CPU2 attaching NULL sched-domain.
[   16.399856] CPU3 attaching NULL sched-domain.
[   16.425034] CPU0 attaching sched-domain:
[   16.425037]  domain 0: span 0-3 level MC
[   16.425038]   groups: 0 1 2 3
[   16.425042] CPU1 attaching sched-domain:
[   16.425043]  domain 0: span 0-3 level MC
[   16.425045]   groups: 1 2 3 0
[   16.425050] CPU2 attaching sched-domain:
[   16.425051]  domain 0: span 0-3 level MC
[   16.425052]   groups: 2 3 0 1
[   16.425055] CPU3 attaching sched-domain:
[   16.425056]  domain 0: span 0-3 level MC
[   16.425057]   groups: 3 0 1 2
[   24.083418] eth0: no IPv6 routers present
[  333.861901] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  333.862532] SGI XFS Quota Management subsystem
[  333.887460] JFS: nTxBlock = 8192, nTxLock = 65536
[  333.938021] NTFS driver 2.1.29 [Flags: R/O MODULE].
[  333.969045] QNX4 filesystem 0.2.3 registered.
[  334.027512] Btrfs loaded
[  589.939550] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  677.205306] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  677.205309] vboxdrv: Successfully done.
[  677.205310] vboxdrv: Found 4 processor cores.
[  677.205408] vboxdrv: fAsync=0 offMin=0x248 offMax=0x1390
[  677.205450] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  677.205452] vboxdrv: Successfully loaded version 3.2.6 (interface 0x00140001).
[  686.939021] device eth0 entered promiscuous mode
[ 1147.453804] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1225.066022] end_request: I/O error, dev fd0, sector 0
[ 1237.233190] end_request: I/O error, dev fd0, sector 0
[ 1237.233194] Buffer I/O error on device fd0, logical block 0
[ 1249.395384] end_request: I/O error, dev fd0, sector 0
[ 1249.395389] Buffer I/O error on device fd0, logical block 0
[ 1261.554682] end_request: I/O error, dev fd0, sector 0
[ 1261.554690] Buffer I/O error on device fd0, logical block 0
[ 1273.717886] end_request: I/O error, dev fd0, sector 0
[ 1273.717895] Buffer I/O error on device fd0, logical block 0
[ 1285.881192] end_request: I/O error, dev fd0, sector 0
[ 1285.881196] Buffer I/O error on device fd0, logical block 0
[ 1298.032818] end_request: I/O error, dev fd0, sector 0
[ 1298.032823] Buffer I/O error on device fd0, logical block 0
[ 1310.191460] end_request: I/O error, dev fd0, sector 0
[ 1310.191465] Buffer I/O error on device fd0, logical block 0
[ 1322.354361] end_request: I/O error, dev fd0, sector 0
[ 1322.354366] Buffer I/O error on device fd0, logical block 0
[ 1334.513766] end_request: I/O error, dev fd0, sector 0
[ 1334.513774] Buffer I/O error on device fd0, logical block 0
[ 1346.677159] end_request: I/O error, dev fd0, sector 0
[ 1346.677167] Buffer I/O error on device fd0, logical block 0
[ 1358.836476] end_request: I/O error, dev fd0, sector 0
[ 1358.836481] Buffer I/O error on device fd0, logical block 0
[ 1370.999480] end_request: I/O error, dev fd0, sector 0
[ 1370.999488] Buffer I/O error on device fd0, logical block 0
[ 1383.158212] end_request: I/O error, dev fd0, sector 0
[ 1383.158217] Buffer I/O error on device fd0, logical block 0
[ 1395.321183] end_request: I/O error, dev fd0, sector 0
[ 1395.321188] Buffer I/O error on device fd0, logical block 0
[ 1407.484793] end_request: I/O error, dev fd0, sector 0
[ 1407.484802] Buffer I/O error on device fd0, logical block 0
[ 1419.644085] end_request: I/O error, dev fd0, sector 0
[ 1419.644090] Buffer I/O error on device fd0, logical block 0
[ 1431.808154] end_request: I/O error, dev fd0, sector 0
[ 1431.808163] Buffer I/O error on device fd0, logical block 0
[ 1443.974629] end_request: I/O error, dev fd0, sector 0
[ 1443.974638] Buffer I/O error on device fd0, logical block 0
[ 1456.136999] end_request: I/O error, dev fd0, sector 0
[ 1456.137008] Buffer I/O error on device fd0, logical block 0
[ 1468.297596] end_request: I/O error, dev fd0, sector 0
[ 1468.297604] Buffer I/O error on device fd0, logical block 0
[ 1480.455232] end_request: I/O error, dev fd0, sector 0
[ 1480.455237] Buffer I/O error on device fd0, logical block 0
[ 1492.619344] end_request: I/O error, dev fd0, sector 0
[ 1492.619348] Buffer I/O error on device fd0, logical block 0
[ 1504.783678] end_request: I/O error, dev fd0, sector 0
[ 1504.783683] Buffer I/O error on device fd0, logical block 0
[ 1516.949839] end_request: I/O error, dev fd0, sector 0
[ 1516.949844] Buffer I/O error on device fd0, logical block 0
[ 1529.112636] end_request: I/O error, dev fd0, sector 0
[ 1529.112641] Buffer I/O error on device fd0, logical block 0
[ 1541.272759] end_request: I/O error, dev fd0, sector 0
[ 1541.272763] Buffer I/O error on device fd0, logical block 0
[ 1553.435179] end_request: I/O error, dev fd0, sector 0
[ 1553.435184] Buffer I/O error on device fd0, logical block 0
[ 1565.602608] end_request: I/O error, dev fd0, sector 0
[ 1565.602613] Buffer I/O error on device fd0, logical block 0
[ 1577.765409] end_request: I/O error, dev fd0, sector 0
[ 1577.765414] Buffer I/O error on device fd0, logical block 0
[ 1589.912938] end_request: I/O error, dev fd0, sector 0
[ 1589.912943] Buffer I/O error on device fd0, logical block 0
[ 1602.071756] end_request: I/O error, dev fd0, sector 0
[ 1602.071761] Buffer I/O error on device fd0, logical block 0
[ 1614.227080] end_request: I/O error, dev fd0, sector 0
[ 1614.227085] Buffer I/O error on device fd0, logical block 0
[ 1626.378954] end_request: I/O error, dev fd0, sector 0
[ 1626.378959] Buffer I/O error on device fd0, logical block 0
[ 1638.541285] end_request: I/O error, dev fd0, sector 0
[ 1638.541290] Buffer I/O error on device fd0, logical block 0
[ 1650.696541] end_request: I/O error, dev fd0, sector 0
[ 1650.696546] Buffer I/O error on device fd0, logical block 0
[ 1662.863667] end_request: I/O error, dev fd0, sector 0
[ 1662.863672] Buffer I/O error on device fd0, logical block 0
[ 1675.031235] end_request: I/O error, dev fd0, sector 0
[ 1675.031240] Buffer I/O error on device fd0, logical block 0
[ 1687.194154] end_request: I/O error, dev fd0, sector 0
[ 1687.194159] Buffer I/O error on device fd0, logical block 0
[ 1699.357331] end_request: I/O error, dev fd0, sector 0
[ 1699.357335] Buffer I/O error on device fd0, logical block 0
[ 1711.504889] end_request: I/O error, dev fd0, sector 0
[ 1711.504895] Buffer I/O error on device fd0, logical block 0
[ 1723.680401] end_request: I/O error, dev fd0, sector 0
[ 1735.846790] end_request: I/O error, dev fd0, sector 0
[ 1748.010450] end_request: I/O error, dev fd0, sector 0
[ 1748.010455] Buffer I/O error on device fd0, logical block 0
[ 1760.161260] end_request: I/O error, dev fd0, sector 0
[ 1760.161265] Buffer I/O error on device fd0, logical block 0
[ 1772.324720] end_request: I/O error, dev fd0, sector 0
[ 1772.324725] Buffer I/O error on device fd0, logical block 0
[ 1784.487866] end_request: I/O error, dev fd0, sector 0
[ 1784.487871] Buffer I/O error on device fd0, logical block 0
[ 1796.646906] end_request: I/O error, dev fd0, sector 0
[ 1796.646911] Buffer I/O error on device fd0, logical block 0
[ 1808.814071] end_request: I/O error, dev fd0, sector 0
[ 1808.814076] Buffer I/O error on device fd0, logical block 0
[ 1820.977137] end_request: I/O error, dev fd0, sector 0
[ 1820.977142] Buffer I/O error on device fd0, logical block 0
[ 1833.140588] end_request: I/O error, dev fd0, sector 0
[ 1833.140593] Buffer I/O error on device fd0, logical block 0
[ 1845.299975] end_request: I/O error, dev fd0, sector 0
[ 1845.299979] Buffer I/O error on device fd0, logical block 0
[ 1857.462779] end_request: I/O error, dev fd0, sector 0
[ 1857.462784] Buffer I/O error on device fd0, logical block 0
[ 1869.622100] end_request: I/O error, dev fd0, sector 0
[ 1869.622105] Buffer I/O error on device fd0, logical block 0
[ 1881.785325] end_request: I/O error, dev fd0, sector 0
[ 1881.785333] Buffer I/O error on device fd0, logical block 0
[ 1893.944460] end_request: I/O error, dev fd0, sector 0
[ 1893.944464] Buffer I/O error on device fd0, logical block 0
[ 1906.111113] end_request: I/O error, dev fd0, sector 0
[ 1906.111119] Buffer I/O error on device fd0, logical block 0
[ 1918.270485] end_request: I/O error, dev fd0, sector 0
[ 1918.270489] Buffer I/O error on device fd0, logical block 0
[ 1930.438453] end_request: I/O error, dev fd0, sector 0
[ 1930.438457] Buffer I/O error on device fd0, logical block 0
[ 1942.592990] end_request: I/O error, dev fd0, sector 0
[ 1942.592995] Buffer I/O error on device fd0, logical block 0
[ 1954.756072] end_request: I/O error, dev fd0, sector 0
[ 1954.756076] Buffer I/O error on device fd0, logical block 0
[ 1966.919133] end_request: I/O error, dev fd0, sector 0
[ 1966.919141] Buffer I/O error on device fd0, logical block 0
[ 1979.082634] end_request: I/O error, dev fd0, sector 0
[ 1979.082640] Buffer I/O error on device fd0, logical block 0
[ 1991.250288] end_request: I/O error, dev fd0, sector 0
[ 1991.250294] Buffer I/O error on device fd0, logical block 0
[ 2003.408662] end_request: I/O error, dev fd0, sector 0
[ 2003.408666] Buffer I/O error on device fd0, logical block 0
[ 2015.567750] end_request: I/O error, dev fd0, sector 0
[ 2015.567756] Buffer I/O error on device fd0, logical block 0
[ 2027.734908] end_request: I/O error, dev fd0, sector 0
[ 2027.734913] Buffer I/O error on device fd0, logical block 0
[ 2039.894890] end_request: I/O error, dev fd0, sector 0
[ 2039.894895] Buffer I/O error on device fd0, logical block 0
[ 2052.057276] end_request: I/O error, dev fd0, sector 0
[ 2052.057281] Buffer I/O error on device fd0, logical block 0
[ 2064.221180] end_request: I/O error, dev fd0, sector 0
[ 2064.221185] Buffer I/O error on device fd0, logical block 0
[ 2076.379293] end_request: I/O error, dev fd0, sector 0
[ 2076.379301] Buffer I/O error on device fd0, logical block 0
[ 2088.543278] end_request: I/O error, dev fd0, sector 0
[ 2088.543286] Buffer I/O error on device fd0, logical block 0
[ 2100.709677] end_request: I/O error, dev fd0, sector 0
[ 2100.709684] Buffer I/O error on device fd0, logical block 0
[ 2112.864623] end_request: I/O error, dev fd0, sector 0
[ 2112.864628] Buffer I/O error on device fd0, logical block 0
[ 2125.032390] end_request: I/O error, dev fd0, sector 0
[ 2125.032394] Buffer I/O error on device fd0, logical block 0
[ 2137.199209] end_request: I/O error, dev fd0, sector 0
[ 2137.199214] Buffer I/O error on device fd0, logical block 0
[ 2149.362232] end_request: I/O error, dev fd0, sector 0
[ 2149.362237] Buffer I/O error on device fd0, logical block 0
[ 2161.529625] end_request: I/O error, dev fd0, sector 0
[ 2161.529634] Buffer I/O error on device fd0, logical block 0
[ 2173.697777] end_request: I/O error, dev fd0, sector 0
[ 2173.697785] Buffer I/O error on device fd0, logical block 0
[ 2185.860450] end_request: I/O error, dev fd0, sector 0
[ 2185.860454] Buffer I/O error on device fd0, logical block 0
[ 2198.015503] end_request: I/O error, dev fd0, sector 0
[ 2198.015511] Buffer I/O error on device fd0, logical block 0
[ 2210.166705] end_request: I/O error, dev fd0, sector 0
[ 2210.166711] Buffer I/O error on device fd0, logical block 0
[ 2222.334526] end_request: I/O error, dev fd0, sector 0
[ 2222.334534] Buffer I/O error on device fd0, logical block 0
[ 2234.517770] end_request: I/O error, dev fd0, sector 0
[ 2246.680627] end_request: I/O error, dev fd0, sector 0
[ 2246.680717] FAT: Unrecognized mount option "utf8" or missing value
[ 2258.847671] end_request: I/O error, dev fd0, sector 0
[ 2271.014150] end_request: I/O error, dev fd0, sector 1
[ 2271.014158] qnx4: unable to read the superblock

------------------------------------------------------------

ika@unix:~$ sudo cat /usr/src/linux-2.6.35/.config 
[sudo] password for ika: 
#
# Automatically generated make config: don't edit
# Linux kernel version: 2.6.35
# Wed Aug 11 23:29:21 2010
#
# CONFIG_64BIT is not set
CONFIG_X86_32=y
# CONFIG_X86_64 is not set
CONFIG_X86=y
CONFIG_INSTRUCTION_DECODER=y
CONFIG_OUTPUT_FORMAT="elf32-i386"
CONFIG_ARCH_DEFCONFIG="arch/x86/configs/i386_defconfig"
CONFIG_GENERIC_TIME=y
CONFIG_GENERIC_CMOS_UPDATE=y
CONFIG_CLOCKSOURCE_WATCHDOG=y
CONFIG_GENERIC_CLOCKEVENTS=y
CONFIG_GENERIC_CLOCKEVENTS_BROADCAST=y
CONFIG_LOCKDEP_SUPPORT=y
CONFIG_STACKTRACE_SUPPORT=y
CONFIG_HAVE_LATENCYTOP_SUPPORT=y
CONFIG_MMU=y
CONFIG_ZONE_DMA=y
# CONFIG_NEED_DMA_MAP_STATE is not set
CONFIG_NEED_SG_DMA_LENGTH=y
CONFIG_GENERIC_ISA_DMA=y
CONFIG_GENERIC_IOMAP=y
CONFIG_GENERIC_BUG=y
CONFIG_GENERIC_HWEIGHT=y
CONFIG_GENERIC_GPIO=y
CONFIG_ARCH_MAY_HAVE_PC_FDC=y
# CONFIG_RWSEM_GENERIC_SPINLOCK is not set
CONFIG_RWSEM_XCHGADD_ALGORITHM=y
CONFIG_ARCH_HAS_CPU_IDLE_WAIT=y
CONFIG_GENERIC_CALIBRATE_DELAY=y
# CONFIG_GENERIC_TIME_VSYSCALL is not set
CONFIG_ARCH_HAS_CPU_RELAX=y
CONFIG_ARCH_HAS_DEFAULT_IDLE=y
CONFIG_ARCH_HAS_CACHE_LINE_SIZE=y
CONFIG_HAVE_SETUP_PER_CPU_AREA=y
CONFIG_NEED_PER_CPU_EMBED_FIRST_CHUNK=y
CONFIG_NEED_PER_CPU_PAGE_FIRST_CHUNK=y
# CONFIG_HAVE_CPUMASK_OF_CPU_MAP is not set
CONFIG_ARCH_HIBERNATION_POSSIBLE=y
CONFIG_ARCH_SUSPEND_POSSIBLE=y
# CONFIG_ZONE_DMA32 is not set
CONFIG_ARCH_POPULATES_NODE_MAP=y
# CONFIG_AUDIT_ARCH is not set
CONFIG_ARCH_SUPPORTS_OPTIMIZED_INLINING=y
CONFIG_ARCH_SUPPORTS_DEBUG_PAGEALLOC=y
CONFIG_HAVE_EARLY_RES=y
CONFIG_GENERIC_HARDIRQS=y
CONFIG_GENERIC_HARDIRQS_NO__DO_IRQ=y
CONFIG_GENERIC_IRQ_PROBE=y
CONFIG_GENERIC_PENDING_IRQ=y
CONFIG_USE_GENERIC_SMP_HELPERS=y
CONFIG_X86_32_SMP=y
CONFIG_X86_HT=y
CONFIG_X86_TRAMPOLINE=y
CONFIG_ARCH_HWEIGHT_CFLAGS="-fcall-saved-ecx -fcall-saved-edx"
CONFIG_KTIME_SCALAR=y
CONFIG_DEFCONFIG_LIST="/lib/modules/$UNAME_RELEASE/.config"
CONFIG_CONSTRUCTORS=y

#
# General setup
#
CONFIG_EXPERIMENTAL=y
CONFIG_LOCK_KERNEL=y
CONFIG_INIT_ENV_ARG_LIMIT=32
CONFIG_CROSS_COMPILE=""
CONFIG_LOCALVERSION=""
# CONFIG_LOCALVERSION_AUTO is not set
CONFIG_HAVE_KERNEL_GZIP=y
CONFIG_HAVE_KERNEL_BZIP2=y
CONFIG_HAVE_KERNEL_LZMA=y
CONFIG_HAVE_KERNEL_LZO=y
CONFIG_KERNEL_GZIP=y
# CONFIG_KERNEL_BZIP2 is not set
# CONFIG_KERNEL_LZMA is not set
# CONFIG_KERNEL_LZO is not set
CONFIG_SWAP=y
CONFIG_SYSVIPC=y
CONFIG_SYSVIPC_SYSCTL=y
CONFIG_POSIX_MQUEUE=y
CONFIG_POSIX_MQUEUE_SYSCTL=y
CONFIG_BSD_PROCESS_ACCT=y
CONFIG_BSD_PROCESS_ACCT_V3=y
CONFIG_TASKSTATS=y
# CONFIG_TASK_DELAY_ACCT is not set
CONFIG_TASK_XACCT=y
CONFIG_TASK_IO_ACCOUNTING=y
CONFIG_AUDIT=y
CONFIG_AUDITSYSCALL=y
CONFIG_AUDIT_TREE=y

#
# RCU Subsystem
#
CONFIG_TREE_RCU=y
# CONFIG_TREE_PREEMPT_RCU is not set
# CONFIG_TINY_RCU is not set
# CONFIG_RCU_TRACE is not set
CONFIG_RCU_FANOUT=32
# CONFIG_RCU_FANOUT_EXACT is not set
# CONFIG_RCU_FAST_NO_HZ is not set
# CONFIG_TREE_RCU_TRACE is not set
# CONFIG_IKCONFIG is not set
CONFIG_LOG_BUF_SHIFT=17
CONFIG_HAVE_UNSTABLE_SCHED_CLOCK=y
CONFIG_CGROUPS=y
# CONFIG_CGROUP_DEBUG is not set
CONFIG_CGROUP_NS=y
CONFIG_CGROUP_FREEZER=y
CONFIG_CGROUP_DEVICE=y
CONFIG_CPUSETS=y
CONFIG_PROC_PID_CPUSET=y
CONFIG_CGROUP_CPUACCT=y
CONFIG_RESOURCE_COUNTERS=y
CONFIG_CGROUP_MEM_RES_CTLR=y
CONFIG_CGROUP_MEM_RES_CTLR_SWAP=y
CONFIG_CGROUP_SCHED=y
CONFIG_FAIR_GROUP_SCHED=y
CONFIG_RT_GROUP_SCHED=y
# CONFIG_BLK_CGROUP is not set
CONFIG_MM_OWNER=y
# CONFIG_SYSFS_DEPRECATED_V2 is not set
CONFIG_RELAY=y
CONFIG_NAMESPACES=y
CONFIG_UTS_NS=y
CONFIG_IPC_NS=y
CONFIG_USER_NS=y
CONFIG_PID_NS=y
CONFIG_NET_NS=y
CONFIG_BLK_DEV_INITRD=y
CONFIG_INITRAMFS_SOURCE=""
CONFIG_RD_GZIP=y
CONFIG_RD_BZIP2=y
CONFIG_RD_LZMA=y
CONFIG_RD_LZO=y
# CONFIG_CC_OPTIMIZE_FOR_SIZE is not set
CONFIG_SYSCTL=y
CONFIG_ANON_INODES=y
# CONFIG_EMBEDDED is not set
CONFIG_UID16=y
CONFIG_SYSCTL_SYSCALL=y
CONFIG_KALLSYMS=y
CONFIG_KALLSYMS_ALL=y
# CONFIG_KALLSYMS_EXTRA_PASS is not set
CONFIG_HOTPLUG=y
CONFIG_PRINTK=y
CONFIG_BUG=y
CONFIG_ELF_CORE=y
CONFIG_PCSPKR_PLATFORM=y
CONFIG_BASE_FULL=y
CONFIG_FUTEX=y
CONFIG_EPOLL=y
CONFIG_SIGNALFD=y
CONFIG_TIMERFD=y
CONFIG_EVENTFD=y
CONFIG_SHMEM=y
CONFIG_AIO=y
CONFIG_HAVE_PERF_EVENTS=y

#
# Kernel Performance Events And Counters
#
CONFIG_PERF_EVENTS=y
CONFIG_PERF_COUNTERS=y
# CONFIG_DEBUG_PERF_USE_VMALLOC is not set
CONFIG_VM_EVENT_COUNTERS=y
CONFIG_PCI_QUIRKS=y
CONFIG_SLUB_DEBUG=y
# CONFIG_COMPAT_BRK is not set
# CONFIG_SLAB is not set
CONFIG_SLUB=y
# CONFIG_SLOB is not set
CONFIG_PROFILING=y
CONFIG_TRACEPOINTS=y
CONFIG_OPROFILE=m
# CONFIG_OPROFILE_EVENT_MULTIPLEX is not set
CONFIG_HAVE_OPROFILE=y
CONFIG_KPROBES=y
CONFIG_OPTPROBES=y
CONFIG_HAVE_EFFICIENT_UNALIGNED_ACCESS=y
CONFIG_KRETPROBES=y
CONFIG_USER_RETURN_NOTIFIER=y
CONFIG_HAVE_IOREMAP_PROT=y
CONFIG_HAVE_KPROBES=y
CONFIG_HAVE_KRETPROBES=y
CONFIG_HAVE_OPTPROBES=y
CONFIG_HAVE_ARCH_TRACEHOOK=y
CONFIG_HAVE_DMA_ATTRS=y
CONFIG_HAVE_REGS_AND_STACK_ACCESS_API=y
CONFIG_HAVE_DMA_API_DEBUG=y
CONFIG_HAVE_HW_BREAKPOINT=y
CONFIG_HAVE_MIXED_BREAKPOINTS_REGS=y
CONFIG_HAVE_USER_RETURN_NOTIFIER=y

#
# GCOV-based kernel profiling
#
# CONFIG_GCOV_KERNEL is not set
CONFIG_SLOW_WORK=y
# CONFIG_SLOW_WORK_DEBUG is not set
CONFIG_HAVE_GENERIC_DMA_COHERENT=y
CONFIG_SLABINFO=y
CONFIG_RT_MUTEXES=y
CONFIG_BASE_SMALL=0
CONFIG_MODULES=y
# CONFIG_MODULE_FORCE_LOAD is not set
CONFIG_MODULE_UNLOAD=y
# CONFIG_MODULE_FORCE_UNLOAD is not set
CONFIG_MODVERSIONS=y
CONFIG_MODULE_SRCVERSION_ALL=y
CONFIG_STOP_MACHINE=y
CONFIG_BLOCK=y
CONFIG_LBDAF=y
CONFIG_BLK_DEV_BSG=y
CONFIG_BLK_DEV_INTEGRITY=y

#
# IO Schedulers
#
CONFIG_IOSCHED_NOOP=y
CONFIG_IOSCHED_DEADLINE=y
CONFIG_IOSCHED_CFQ=y
# CONFIG_DEFAULT_DEADLINE is not set
CONFIG_DEFAULT_CFQ=y
# CONFIG_DEFAULT_NOOP is not set
CONFIG_DEFAULT_IOSCHED="cfq"
CONFIG_PREEMPT_NOTIFIERS=y
# CONFIG_INLINE_SPIN_TRYLOCK is not set
# CONFIG_INLINE_SPIN_TRYLOCK_BH is not set
# CONFIG_INLINE_SPIN_LOCK is not set
# CONFIG_INLINE_SPIN_LOCK_BH is not set
# CONFIG_INLINE_SPIN_LOCK_IRQ is not set
# CONFIG_INLINE_SPIN_LOCK_IRQSAVE is not set
CONFIG_INLINE_SPIN_UNLOCK=y
# CONFIG_INLINE_SPIN_UNLOCK_BH is not set
CONFIG_INLINE_SPIN_UNLOCK_IRQ=y
# CONFIG_INLINE_SPIN_UNLOCK_IRQRESTORE is not set
# CONFIG_INLINE_READ_TRYLOCK is not set
# CONFIG_INLINE_READ_LOCK is not set
# CONFIG_INLINE_READ_LOCK_BH is not set
# CONFIG_INLINE_READ_LOCK_IRQ is not set
# CONFIG_INLINE_READ_LOCK_IRQSAVE is not set
CONFIG_INLINE_READ_UNLOCK=y
# CONFIG_INLINE_READ_UNLOCK_BH is not set
CONFIG_INLINE_READ_UNLOCK_IRQ=y
# CONFIG_INLINE_READ_UNLOCK_IRQRESTORE is not set
# CONFIG_INLINE_WRITE_TRYLOCK is not set
# CONFIG_INLINE_WRITE_LOCK is not set
# CONFIG_INLINE_WRITE_LOCK_BH is not set
# CONFIG_INLINE_WRITE_LOCK_IRQ is not set
# CONFIG_INLINE_WRITE_LOCK_IRQSAVE is not set
CONFIG_INLINE_WRITE_UNLOCK=y
# CONFIG_INLINE_WRITE_UNLOCK_BH is not set
CONFIG_INLINE_WRITE_UNLOCK_IRQ=y
# CONFIG_INLINE_WRITE_UNLOCK_IRQRESTORE is not set
CONFIG_MUTEX_SPIN_ON_OWNER=y
CONFIG_FREEZER=y

#
# Processor type and features
#
CONFIG_TICK_ONESHOT=y
CONFIG_NO_HZ=y
CONFIG_HIGH_RES_TIMERS=y
CONFIG_GENERIC_CLOCKEVENTS_BUILD=y
CONFIG_SMP=y
CONFIG_SPARSE_IRQ=y
CONFIG_X86_MPPARSE=y
# CONFIG_X86_BIGSMP is not set
CONFIG_X86_EXTENDED_PLATFORM=y
# CONFIG_X86_ELAN is not set
CONFIG_X86_MRST=y
# CONFIG_X86_RDC321X is not set
# CONFIG_X86_32_NON_STANDARD is not set
CONFIG_X86_SUPPORTS_MEMORY_FAILURE=y
CONFIG_SCHED_OMIT_FRAME_POINTER=y
CONFIG_PARAVIRT_GUEST=y
CONFIG_VMI=y
CONFIG_KVM_CLOCK=y
CONFIG_KVM_GUEST=y
# CONFIG_LGUEST_GUEST is not set
CONFIG_PARAVIRT=y
CONFIG_PARAVIRT_SPINLOCKS=y
CONFIG_PARAVIRT_CLOCK=y
# CONFIG_PARAVIRT_DEBUG is not set
CONFIG_NO_BOOTMEM=y
# CONFIG_MEMTEST is not set
# CONFIG_M386 is not set
# CONFIG_M486 is not set
CONFIG_M586=y
# CONFIG_M586TSC is not set
# CONFIG_M586MMX is not set
# CONFIG_M686 is not set
# CONFIG_MPENTIUMII is not set
# CONFIG_MPENTIUMIII is not set
# CONFIG_MPENTIUMM is not set
# CONFIG_MPENTIUM4 is not set
# CONFIG_MK6 is not set
# CONFIG_MK7 is not set
# CONFIG_MK8 is not set
# CONFIG_MCRUSOE is not set
# CONFIG_MEFFICEON is not set
# CONFIG_MWINCHIPC6 is not set
# CONFIG_MWINCHIP3D is not set
# CONFIG_MGEODEGX1 is not set
# CONFIG_MGEODE_LX is not set
# CONFIG_MCYRIXIII is not set
# CONFIG_MVIAC3_2 is not set
# CONFIG_MVIAC7 is not set
# CONFIG_MPSC is not set
# CONFIG_MCORE2 is not set
# CONFIG_MATOM is not set
# CONFIG_GENERIC_CPU is not set
CONFIG_X86_GENERIC=y
CONFIG_X86_CPU=y
CONFIG_X86_INTERNODE_CACHE_SHIFT=6
CONFIG_X86_CMPXCHG=y
CONFIG_X86_L1_CACHE_SHIFT=6
CONFIG_X86_XADD=y
CONFIG_X86_PPRO_FENCE=y
CONFIG_X86_F00F_BUG=y
CONFIG_X86_WP_WORKS_OK=y
CONFIG_X86_INVLPG=y
CONFIG_X86_BSWAP=y
CONFIG_X86_POPAD_OK=y
CONFIG_X86_ALIGNMENT_16=y
CONFIG_X86_INTEL_USERCOPY=y
CONFIG_X86_MINIMUM_CPU_FAMILY=4
CONFIG_CPU_SUP_INTEL=y
CONFIG_CPU_SUP_CYRIX_32=y
CONFIG_CPU_SUP_AMD=y
CONFIG_CPU_SUP_CENTAUR=y
CONFIG_CPU_SUP_TRANSMETA_32=y
CONFIG_CPU_SUP_UMC_32=y
CONFIG_HPET_TIMER=y
CONFIG_HPET_EMULATE_RTC=y
CONFIG_APB_TIMER=y
CONFIG_DMI=y
# CONFIG_IOMMU_HELPER is not set
# CONFIG_IOMMU_API is not set
CONFIG_NR_CPUS=8
CONFIG_SCHED_SMT=y
CONFIG_SCHED_MC=y
# CONFIG_PREEMPT_NONE is not set
CONFIG_PREEMPT_VOLUNTARY=y
# CONFIG_PREEMPT is not set
CONFIG_X86_LOCAL_APIC=y
CONFIG_X86_IO_APIC=y
CONFIG_X86_REROUTE_FOR_BROKEN_BOOT_IRQS=y
CONFIG_X86_MCE=y
CONFIG_X86_MCE_INTEL=y
CONFIG_X86_MCE_AMD=y
# CONFIG_X86_ANCIENT_MCE is not set
CONFIG_X86_MCE_THRESHOLD=y
CONFIG_X86_MCE_INJECT=m
CONFIG_X86_THERMAL_VECTOR=y
CONFIG_VM86=y
# CONFIG_TOSHIBA is not set
CONFIG_I8K=m
CONFIG_X86_REBOOTFIXUPS=y
CONFIG_MICROCODE=m
CONFIG_MICROCODE_INTEL=y
CONFIG_MICROCODE_AMD=y
CONFIG_MICROCODE_OLD_INTERFACE=y
CONFIG_X86_MSR=m
CONFIG_X86_CPUID=m
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
CONFIG_PAGE_OFFSET=0xC0000000
CONFIG_HIGHMEM=y
# CONFIG_ARCH_PHYS_ADDR_T_64BIT is not set
CONFIG_ARCH_FLATMEM_ENABLE=y
CONFIG_ARCH_SPARSEMEM_ENABLE=y
CONFIG_ARCH_SELECT_MEMORY_MODEL=y
CONFIG_ILLEGAL_POINTER_VALUE=0
CONFIG_SELECT_MEMORY_MODEL=y
CONFIG_FLATMEM_MANUAL=y
# CONFIG_DISCONTIGMEM_MANUAL is not set
# CONFIG_SPARSEMEM_MANUAL is not set
CONFIG_FLATMEM=y
CONFIG_FLAT_NODE_MEM_MAP=y
CONFIG_SPARSEMEM_STATIC=y
CONFIG_PAGEFLAGS_EXTENDED=y
CONFIG_SPLIT_PTLOCK_CPUS=4
# CONFIG_COMPACTION is not set
# CONFIG_PHYS_ADDR_T_64BIT is not set
CONFIG_ZONE_DMA_FLAG=1
CONFIG_BOUNCE=y
CONFIG_VIRT_TO_BUS=y
CONFIG_MMU_NOTIFIER=y
CONFIG_KSM=y
CONFIG_DEFAULT_MMAP_MIN_ADDR=65536
CONFIG_ARCH_SUPPORTS_MEMORY_FAILURE=y
CONFIG_MEMORY_FAILURE=y
# CONFIG_HWPOISON_INJECT is not set
CONFIG_HIGHPTE=y
CONFIG_X86_CHECK_BIOS_CORRUPTION=y
CONFIG_X86_BOOTPARAM_MEMORY_CORRUPTION_CHECK=y
CONFIG_X86_RESERVE_LOW_64K=y
# CONFIG_MATH_EMULATION is not set
CONFIG_MTRR=y
CONFIG_MTRR_SANITIZER=y
CONFIG_MTRR_SANITIZER_ENABLE_DEFAULT=0
CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1
CONFIG_X86_PAT=y
CONFIG_ARCH_USES_PG_UNCACHED=y
CONFIG_EFI=y
CONFIG_SECCOMP=y
CONFIG_CC_STACKPROTECTOR=y
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
# CONFIG_HZ_300 is not set
# CONFIG_HZ_1000 is not set
CONFIG_HZ=250
CONFIG_SCHED_HRTICK=y
CONFIG_KEXEC=y
CONFIG_CRASH_DUMP=y
CONFIG_KEXEC_JUMP=y
CONFIG_PHYSICAL_START=0x100000
CONFIG_RELOCATABLE=y
CONFIG_X86_NEED_RELOCS=y
CONFIG_PHYSICAL_ALIGN=0x100000
CONFIG_HOTPLUG_CPU=y
# CONFIG_COMPAT_VDSO is not set
# CONFIG_CMDLINE_BOOL is not set
CONFIG_ARCH_ENABLE_MEMORY_HOTPLUG=y

#
# Power management and ACPI options
#
CONFIG_PM=y
CONFIG_PM_DEBUG=y
# CONFIG_PM_ADVANCED_DEBUG is not set
# CONFIG_PM_VERBOSE is not set
CONFIG_CAN_PM_TRACE=y
CONFIG_PM_TRACE=y
CONFIG_PM_TRACE_RTC=y
CONFIG_PM_SLEEP_SMP=y
CONFIG_PM_SLEEP=y
CONFIG_SUSPEND_NVS=y
CONFIG_SUSPEND=y
CONFIG_PM_TEST_SUSPEND=y
CONFIG_SUSPEND_FREEZER=y
CONFIG_HIBERNATION=y
CONFIG_PM_STD_PARTITION=""
CONFIG_PM_RUNTIME=y
CONFIG_PM_OPS=y
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
CONFIG_ACPI_PROCFS=y
CONFIG_ACPI_PROCFS_POWER=y
CONFIG_ACPI_POWER_METER=m
CONFIG_ACPI_SYSFS_POWER=y
CONFIG_ACPI_PROC_EVENT=y
CONFIG_ACPI_AC=y
CONFIG_ACPI_BATTERY=y
CONFIG_ACPI_BUTTON=y
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_FAN=y
CONFIG_ACPI_DOCK=y
CONFIG_ACPI_PROCESSOR=y
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_PROCESSOR_AGGREGATOR=m
CONFIG_ACPI_THERMAL=y
CONFIG_ACPI_CUSTOM_DSDT_FILE=""
# CONFIG_ACPI_CUSTOM_DSDT is not set
CONFIG_ACPI_BLACKLIST_YEAR=2000
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_PCI_SLOT=y
CONFIG_X86_PM_TIMER=y
CONFIG_ACPI_CONTAINER=y
CONFIG_ACPI_SBS=y
# CONFIG_ACPI_HED is not set
# CONFIG_ACPI_APEI is not set
CONFIG_SFI=y
CONFIG_X86_APM_BOOT=y
CONFIG_APM=m
# CONFIG_APM_IGNORE_USER_SUSPEND is not set
# CONFIG_APM_DO_ENABLE is not set
# CONFIG_APM_CPU_IDLE is not set
# CONFIG_APM_DISPLAY_BLANK is not set
# CONFIG_APM_ALLOW_INTS is not set

#
# CPU Frequency scaling
#
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=y
# CONFIG_CPU_FREQ_DEBUG is not set
CONFIG_CPU_FREQ_STAT=y
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_POWERSAVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=y
CONFIG_CPU_FREQ_GOV_USERSPACE=y
CONFIG_CPU_FREQ_GOV_ONDEMAND=y
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=y

#
# CPUFreq processor drivers
#
# CONFIG_X86_PCC_CPUFREQ is not set
CONFIG_X86_ACPI_CPUFREQ=y
CONFIG_X86_POWERNOW_K6=y
CONFIG_X86_POWERNOW_K7=y
CONFIG_X86_POWERNOW_K7_ACPI=y
CONFIG_X86_POWERNOW_K8=y
CONFIG_X86_GX_SUSPMOD=y
CONFIG_X86_SPEEDSTEP_CENTRINO=y
CONFIG_X86_SPEEDSTEP_CENTRINO_TABLE=y
CONFIG_X86_SPEEDSTEP_ICH=y
CONFIG_X86_SPEEDSTEP_SMI=y
CONFIG_X86_P4_CLOCKMOD=m
CONFIG_X86_CPUFREQ_NFORCE2=y
CONFIG_X86_LONGRUN=y
CONFIG_X86_LONGHAUL=y
CONFIG_X86_E_POWERSAVER=m

#
# shared options
#
CONFIG_X86_SPEEDSTEP_LIB=y
CONFIG_X86_SPEEDSTEP_RELAXED_CAP_CHECK=y
CONFIG_CPU_IDLE=y
CONFIG_CPU_IDLE_GOV_LADDER=y
CONFIG_CPU_IDLE_GOV_MENU=y
# CONFIG_INTEL_IDLE is not set

#
# Bus options (PCI etc.)
#
CONFIG_PCI=y
# CONFIG_PCI_GOBIOS is not set
# CONFIG_PCI_GOMMCONFIG is not set
# CONFIG_PCI_GODIRECT is not set
# CONFIG_PCI_GOOLPC is not set
CONFIG_PCI_GOANY=y
CONFIG_PCI_BIOS=y
CONFIG_PCI_DIRECT=y
CONFIG_PCI_MMCONFIG=y
CONFIG_PCI_OLPC=y
CONFIG_PCI_DOMAINS=y
# CONFIG_PCI_CNB20LE_QUIRK is not set
# CONFIG_DMAR is not set
CONFIG_PCIEPORTBUS=y
CONFIG_HOTPLUG_PCI_PCIE=y
CONFIG_PCIEAER=y
# CONFIG_PCIE_ECRC is not set
# CONFIG_PCIEAER_INJECT is not set
# CONFIG_PCIEASPM is not set
CONFIG_PCIE_PME=y
CONFIG_ARCH_SUPPORTS_MSI=y
CONFIG_PCI_MSI=y
# CONFIG_PCI_DEBUG is not set
CONFIG_PCI_STUB=m
CONFIG_HT_IRQ=y
CONFIG_PCI_IOV=y
CONFIG_PCI_IOAPIC=y
CONFIG_ISA_DMA_API=y
CONFIG_ISA=y
CONFIG_EISA=y
CONFIG_EISA_VLB_PRIMING=y
CONFIG_EISA_PCI_EISA=y
CONFIG_EISA_VIRTUAL_ROOT=y
CONFIG_EISA_NAMES=y
CONFIG_MCA=y
CONFIG_MCA_LEGACY=y
# CONFIG_MCA_PROC_FS is not set
CONFIG_SCx200=m
CONFIG_SCx200HR_TIMER=m
CONFIG_OLPC=y
CONFIG_K8_NB=y
CONFIG_PCCARD=m
CONFIG_PCMCIA=m
CONFIG_PCMCIA_LOAD_CIS=y
CONFIG_CARDBUS=y

#
# PC-card bridges
#
CONFIG_YENTA=m
CONFIG_YENTA_O2=y
CONFIG_YENTA_RICOH=y
CONFIG_YENTA_TI=y
CONFIG_YENTA_ENE_TUNE=y
CONFIG_YENTA_TOSHIBA=y
CONFIG_PD6729=m
CONFIG_I82092=m
CONFIG_I82365=m
CONFIG_TCIC=m
CONFIG_PCMCIA_PROBE=y
CONFIG_PCCARD_NONSTATIC=y
CONFIG_HOTPLUG_PCI=y
CONFIG_HOTPLUG_PCI_FAKE=m
CONFIG_HOTPLUG_PCI_COMPAQ=m
CONFIG_HOTPLUG_PCI_COMPAQ_NVRAM=y
CONFIG_HOTPLUG_PCI_IBM=m
CONFIG_HOTPLUG_PCI_ACPI=m
CONFIG_HOTPLUG_PCI_ACPI_IBM=m
CONFIG_HOTPLUG_PCI_CPCI=y
CONFIG_HOTPLUG_PCI_CPCI_ZT5550=m
CONFIG_HOTPLUG_PCI_CPCI_GENERIC=m
CONFIG_HOTPLUG_PCI_SHPC=m

#
# Executable file formats / Emulations
#
CONFIG_BINFMT_ELF=y
# CONFIG_CORE_DUMP_DEFAULT_ELF_HEADERS is not set
CONFIG_HAVE_AOUT=y
CONFIG_BINFMT_AOUT=m
CONFIG_BINFMT_MISC=m
CONFIG_HAVE_ATOMIC_IOMAP=y
CONFIG_NET=y

#
# Networking options
#
CONFIG_PACKET=y
CONFIG_UNIX=y
CONFIG_XFRM=y
CONFIG_XFRM_USER=m
# CONFIG_XFRM_SUB_POLICY is not set
# CONFIG_XFRM_MIGRATE is not set
# CONFIG_XFRM_STATISTICS is not set
CONFIG_XFRM_IPCOMP=m
CONFIG_NET_KEY=m
# CONFIG_NET_KEY_MIGRATE is not set
CONFIG_INET=y
CONFIG_IP_MULTICAST=y
CONFIG_IP_ADVANCED_ROUTER=y
CONFIG_ASK_IP_FIB_HASH=y
# CONFIG_IP_FIB_TRIE is not set
CONFIG_IP_FIB_HASH=y
CONFIG_IP_MULTIPLE_TABLES=y
CONFIG_IP_ROUTE_MULTIPATH=y
CONFIG_IP_ROUTE_VERBOSE=y
# CONFIG_IP_PNP is not set
CONFIG_NET_IPIP=m
CONFIG_NET_IPGRE=m
CONFIG_NET_IPGRE_BROADCAST=y
CONFIG_IP_MROUTE=y
# CONFIG_IP_MROUTE_MULTIPLE_TABLES is not set
CONFIG_IP_PIMSM_V1=y
CONFIG_IP_PIMSM_V2=y
# CONFIG_ARPD is not set
CONFIG_SYN_COOKIES=y
CONFIG_INET_AH=m
CONFIG_INET_ESP=m
CONFIG_INET_IPCOMP=m
CONFIG_INET_XFRM_TUNNEL=m
CONFIG_INET_TUNNEL=m
CONFIG_INET_XFRM_MODE_TRANSPORT=m
CONFIG_INET_XFRM_MODE_TUNNEL=m
CONFIG_INET_XFRM_MODE_BEET=m
CONFIG_INET_LRO=y
CONFIG_INET_DIAG=y
CONFIG_INET_TCP_DIAG=y
CONFIG_TCP_CONG_ADVANCED=y
CONFIG_TCP_CONG_BIC=m
CONFIG_TCP_CONG_CUBIC=y
CONFIG_TCP_CONG_WESTWOOD=m
CONFIG_TCP_CONG_HTCP=m
CONFIG_TCP_CONG_HSTCP=m
CONFIG_TCP_CONG_HYBLA=m
CONFIG_TCP_CONG_VEGAS=m
CONFIG_TCP_CONG_SCALABLE=m
CONFIG_TCP_CONG_LP=m
CONFIG_TCP_CONG_VENO=m
CONFIG_TCP_CONG_YEAH=m
CONFIG_TCP_CONG_ILLINOIS=m
# CONFIG_DEFAULT_BIC is not set
CONFIG_DEFAULT_CUBIC=y
# CONFIG_DEFAULT_HTCP is not set
# CONFIG_DEFAULT_HYBLA is not set
# CONFIG_DEFAULT_VEGAS is not set
# CONFIG_DEFAULT_VENO is not set
# CONFIG_DEFAULT_WESTWOOD is not set
# CONFIG_DEFAULT_RENO is not set
CONFIG_DEFAULT_TCP_CONG="cubic"
CONFIG_TCP_MD5SIG=y
CONFIG_IPV6=y
CONFIG_IPV6_PRIVACY=y
# CONFIG_IPV6_ROUTER_PREF is not set
# CONFIG_IPV6_OPTIMISTIC_DAD is not set
CONFIG_INET6_AH=m
CONFIG_INET6_ESP=m
CONFIG_INET6_IPCOMP=m
# CONFIG_IPV6_MIP6 is not set
CONFIG_INET6_XFRM_TUNNEL=m
CONFIG_INET6_TUNNEL=m
CONFIG_INET6_XFRM_MODE_TRANSPORT=m
CONFIG_INET6_XFRM_MODE_TUNNEL=m
CONFIG_INET6_XFRM_MODE_BEET=m
CONFIG_INET6_XFRM_MODE_ROUTEOPTIMIZATION=m
CONFIG_IPV6_SIT=m
# CONFIG_IPV6_SIT_6RD is not set
CONFIG_IPV6_NDISC_NODETYPE=y
CONFIG_IPV6_TUNNEL=m
CONFIG_IPV6_MULTIPLE_TABLES=y
# CONFIG_IPV6_SUBTREES is not set
# CONFIG_IPV6_MROUTE is not set
CONFIG_NETLABEL=y
CONFIG_NETWORK_SECMARK=y
CONFIG_NETFILTER=y
# CONFIG_NETFILTER_DEBUG is not set
CONFIG_NETFILTER_ADVANCED=y
CONFIG_BRIDGE_NETFILTER=y

#
# Core Netfilter Configuration
#
CONFIG_NETFILTER_NETLINK=m
CONFIG_NETFILTER_NETLINK_QUEUE=m
CONFIG_NETFILTER_NETLINK_LOG=m
CONFIG_NF_CONNTRACK=m
CONFIG_NF_CT_ACCT=y
CONFIG_NF_CONNTRACK_MARK=y
CONFIG_NF_CONNTRACK_SECMARK=y
CONFIG_NF_CONNTRACK_EVENTS=y
CONFIG_NF_CT_PROTO_DCCP=m
CONFIG_NF_CT_PROTO_GRE=m
CONFIG_NF_CT_PROTO_SCTP=m
CONFIG_NF_CT_PROTO_UDPLITE=m
CONFIG_NF_CONNTRACK_AMANDA=m
CONFIG_NF_CONNTRACK_FTP=m
CONFIG_NF_CONNTRACK_H323=m
CONFIG_NF_CONNTRACK_IRC=m
CONFIG_NF_CONNTRACK_NETBIOS_NS=m
CONFIG_NF_CONNTRACK_PPTP=m
CONFIG_NF_CONNTRACK_SANE=m
CONFIG_NF_CONNTRACK_SIP=m
CONFIG_NF_CONNTRACK_TFTP=m
CONFIG_NF_CT_NETLINK=m
CONFIG_NETFILTER_TPROXY=m
CONFIG_NETFILTER_XTABLES=m

#
# Xtables combined modules
#
CONFIG_NETFILTER_XT_MARK=m
CONFIG_NETFILTER_XT_CONNMARK=m

#
# Xtables targets
#
CONFIG_NETFILTER_XT_TARGET_CLASSIFY=m
CONFIG_NETFILTER_XT_TARGET_CONNMARK=m
CONFIG_NETFILTER_XT_TARGET_CONNSECMARK=m
# CONFIG_NETFILTER_XT_TARGET_CT is not set
CONFIG_NETFILTER_XT_TARGET_DSCP=m
CONFIG_NETFILTER_XT_TARGET_HL=m
CONFIG_NETFILTER_XT_TARGET_LED=m
CONFIG_NETFILTER_XT_TARGET_MARK=m
CONFIG_NETFILTER_XT_TARGET_NFLOG=m
CONFIG_NETFILTER_XT_TARGET_NFQUEUE=m
CONFIG_NETFILTER_XT_TARGET_NOTRACK=m
CONFIG_NETFILTER_XT_TARGET_RATEEST=m
# CONFIG_NETFILTER_XT_TARGET_TEE is not set
CONFIG_NETFILTER_XT_TARGET_TPROXY=m
CONFIG_NETFILTER_XT_TARGET_TRACE=m
CONFIG_NETFILTER_XT_TARGET_SECMARK=m
CONFIG_NETFILTER_XT_TARGET_TCPMSS=m
# CONFIG_NETFILTER_XT_TARGET_TCPOPTSTRIP is not set

#
# Xtables matches
#
CONFIG_NETFILTER_XT_MATCH_CLUSTER=m
CONFIG_NETFILTER_XT_MATCH_COMMENT=m
CONFIG_NETFILTER_XT_MATCH_CONNBYTES=m
CONFIG_NETFILTER_XT_MATCH_CONNLIMIT=m
CONFIG_NETFILTER_XT_MATCH_CONNMARK=m
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
CONFIG_NETFILTER_XT_MATCH_DCCP=m
CONFIG_NETFILTER_XT_MATCH_DSCP=m
CONFIG_NETFILTER_XT_MATCH_ESP=m
CONFIG_NETFILTER_XT_MATCH_HASHLIMIT=m
CONFIG_NETFILTER_XT_MATCH_HELPER=m
CONFIG_NETFILTER_XT_MATCH_HL=m
CONFIG_NETFILTER_XT_MATCH_IPRANGE=m
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
CONFIG_NETFILTER_XT_MATCH_MULTIPORT=m
CONFIG_NETFILTER_XT_MATCH_OSF=m
CONFIG_NETFILTER_XT_MATCH_OWNER=m
CONFIG_NETFILTER_XT_MATCH_POLICY=m
CONFIG_NETFILTER_XT_MATCH_PHYSDEV=m
CONFIG_NETFILTER_XT_MATCH_PKTTYPE=m
CONFIG_NETFILTER_XT_MATCH_QUOTA=m
CONFIG_NETFILTER_XT_MATCH_RATEEST=m
CONFIG_NETFILTER_XT_MATCH_REALM=m
CONFIG_NETFILTER_XT_MATCH_RECENT=m
CONFIG_NETFILTER_XT_MATCH_SCTP=m
CONFIG_NETFILTER_XT_MATCH_SOCKET=m
CONFIG_NETFILTER_XT_MATCH_STATE=m
CONFIG_NETFILTER_XT_MATCH_STATISTIC=m
CONFIG_NETFILTER_XT_MATCH_STRING=m
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m
CONFIG_NETFILTER_XT_MATCH_TIME=m
CONFIG_NETFILTER_XT_MATCH_U32=m
CONFIG_IP_VS=m
CONFIG_IP_VS_IPV6=y
# CONFIG_IP_VS_DEBUG is not set
CONFIG_IP_VS_TAB_BITS=12

#
# IPVS transport protocol load balancing support
#
CONFIG_IP_VS_PROTO_TCP=y
CONFIG_IP_VS_PROTO_UDP=y
CONFIG_IP_VS_PROTO_AH_ESP=y
CONFIG_IP_VS_PROTO_ESP=y
CONFIG_IP_VS_PROTO_AH=y
# CONFIG_IP_VS_PROTO_SCTP is not set

#
# IPVS scheduler
#
CONFIG_IP_VS_RR=m
CONFIG_IP_VS_WRR=m
CONFIG_IP_VS_LC=m
CONFIG_IP_VS_WLC=m
CONFIG_IP_VS_LBLC=m
CONFIG_IP_VS_LBLCR=m
CONFIG_IP_VS_DH=m
CONFIG_IP_VS_SH=m
CONFIG_IP_VS_SED=m
CONFIG_IP_VS_NQ=m

#
# IPVS application helper
#
CONFIG_IP_VS_FTP=m

#
# IP: Netfilter Configuration
#
CONFIG_NF_DEFRAG_IPV4=m
CONFIG_NF_CONNTRACK_IPV4=m
CONFIG_NF_CONNTRACK_PROC_COMPAT=y
CONFIG_IP_NF_QUEUE=m
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_ADDRTYPE=m
CONFIG_IP_NF_MATCH_AH=m
CONFIG_IP_NF_MATCH_ECN=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_NF_NAT=m
CONFIG_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_NETMAP=m
CONFIG_IP_NF_TARGET_REDIRECT=m
CONFIG_NF_NAT_SNMP_BASIC=m
CONFIG_NF_NAT_PROTO_DCCP=m
CONFIG_NF_NAT_PROTO_GRE=m
CONFIG_NF_NAT_PROTO_UDPLITE=m
CONFIG_NF_NAT_PROTO_SCTP=m
CONFIG_NF_NAT_FTP=m
CONFIG_NF_NAT_IRC=m
CONFIG_NF_NAT_TFTP=m
CONFIG_NF_NAT_AMANDA=m
CONFIG_NF_NAT_PPTP=m
CONFIG_NF_NAT_H323=m
CONFIG_NF_NAT_SIP=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_CLUSTERIP=m
CONFIG_IP_NF_TARGET_ECN=m
CONFIG_IP_NF_TARGET_TTL=m
CONFIG_IP_NF_RAW=m
CONFIG_IP_NF_SECURITY=m
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
CONFIG_IP_NF_ARP_MANGLE=m

#
# IPv6: Netfilter Configuration
#
CONFIG_NF_CONNTRACK_IPV6=m
CONFIG_IP6_NF_QUEUE=m
CONFIG_IP6_NF_IPTABLES=m
CONFIG_IP6_NF_MATCH_AH=m
CONFIG_IP6_NF_MATCH_EUI64=m
CONFIG_IP6_NF_MATCH_FRAG=m
CONFIG_IP6_NF_MATCH_OPTS=m
CONFIG_IP6_NF_MATCH_HL=m
CONFIG_IP6_NF_MATCH_IPV6HEADER=m
CONFIG_IP6_NF_MATCH_MH=m
CONFIG_IP6_NF_MATCH_RT=m
CONFIG_IP6_NF_TARGET_HL=m
CONFIG_IP6_NF_TARGET_LOG=m
CONFIG_IP6_NF_FILTER=m
CONFIG_IP6_NF_TARGET_REJECT=m
CONFIG_IP6_NF_MANGLE=m
CONFIG_IP6_NF_RAW=m
CONFIG_IP6_NF_SECURITY=m

#
# DECnet: Netfilter Configuration
#
CONFIG_DECNET_NF_GRABULATOR=m
CONFIG_BRIDGE_NF_EBTABLES=m
CONFIG_BRIDGE_EBT_BROUTE=m
CONFIG_BRIDGE_EBT_T_FILTER=m
CONFIG_BRIDGE_EBT_T_NAT=m
CONFIG_BRIDGE_EBT_802_3=m
CONFIG_BRIDGE_EBT_AMONG=m
CONFIG_BRIDGE_EBT_ARP=m
CONFIG_BRIDGE_EBT_IP=m
CONFIG_BRIDGE_EBT_IP6=m
CONFIG_BRIDGE_EBT_LIMIT=m
CONFIG_BRIDGE_EBT_MARK=m
CONFIG_BRIDGE_EBT_PKTTYPE=m
CONFIG_BRIDGE_EBT_STP=m
CONFIG_BRIDGE_EBT_VLAN=m
CONFIG_BRIDGE_EBT_ARPREPLY=m
CONFIG_BRIDGE_EBT_DNAT=m
CONFIG_BRIDGE_EBT_MARK_T=m
CONFIG_BRIDGE_EBT_REDIRECT=m
CONFIG_BRIDGE_EBT_SNAT=m
CONFIG_BRIDGE_EBT_LOG=m
CONFIG_BRIDGE_EBT_ULOG=m
CONFIG_BRIDGE_EBT_NFLOG=m
CONFIG_IP_DCCP=m
CONFIG_INET_DCCP_DIAG=m

#
# DCCP CCIDs Configuration (EXPERIMENTAL)
#
# CONFIG_IP_DCCP_CCID2_DEBUG is not set
CONFIG_IP_DCCP_CCID3=y
# CONFIG_IP_DCCP_CCID3_DEBUG is not set
CONFIG_IP_DCCP_CCID3_RTO=100
CONFIG_IP_DCCP_TFRC_LIB=y

#
# DCCP Kernel Hacking
#
# CONFIG_IP_DCCP_DEBUG is not set
CONFIG_NET_DCCPPROBE=m
CONFIG_IP_SCTP=m
# CONFIG_NET_SCTPPROBE is not set
# CONFIG_SCTP_DBG_MSG is not set
# CONFIG_SCTP_DBG_OBJCNT is not set
# CONFIG_SCTP_HMAC_NONE is not set
# CONFIG_SCTP_HMAC_SHA1 is not set
CONFIG_SCTP_HMAC_MD5=y
CONFIG_RDS=m
CONFIG_RDS_RDMA=m
CONFIG_RDS_TCP=m
# CONFIG_RDS_DEBUG is not set
CONFIG_TIPC=m
# CONFIG_TIPC_ADVANCED is not set
# CONFIG_TIPC_DEBUG is not set
CONFIG_ATM=m
CONFIG_ATM_CLIP=m
# CONFIG_ATM_CLIP_NO_ICMP is not set
CONFIG_ATM_LANE=m
CONFIG_ATM_MPOA=m
CONFIG_ATM_BR2684=m
# CONFIG_ATM_BR2684_IPFILTER is not set
# CONFIG_L2TP is not set
CONFIG_STP=m
CONFIG_GARP=m
CONFIG_BRIDGE=m
CONFIG_BRIDGE_IGMP_SNOOPING=y
CONFIG_NET_DSA=y
CONFIG_NET_DSA_TAG_DSA=y
CONFIG_NET_DSA_TAG_EDSA=y
CONFIG_NET_DSA_TAG_TRAILER=y
CONFIG_NET_DSA_MV88E6XXX=y
CONFIG_NET_DSA_MV88E6060=y
CONFIG_NET_DSA_MV88E6XXX_NEED_PPU=y
CONFIG_NET_DSA_MV88E6131=y
CONFIG_NET_DSA_MV88E6123_61_65=y
CONFIG_VLAN_8021Q=m
CONFIG_VLAN_8021Q_GVRP=y
CONFIG_DECNET=m
# CONFIG_DECNET_ROUTER is not set
CONFIG_LLC=y
CONFIG_LLC2=m
CONFIG_IPX=m
# CONFIG_IPX_INTERN is not set
CONFIG_ATALK=m
CONFIG_DEV_APPLETALK=m
CONFIG_LTPC=m
# CONFIG_COPS is not set
CONFIG_IPDDP=m
CONFIG_IPDDP_ENCAP=y
CONFIG_IPDDP_DECAP=y
CONFIG_X25=m
CONFIG_LAPB=m
CONFIG_ECONET=m
CONFIG_ECONET_AUNUDP=y
CONFIG_ECONET_NATIVE=y
CONFIG_WAN_ROUTER=m
CONFIG_PHONET=m
CONFIG_IEEE802154=m
CONFIG_NET_SCHED=y

#
# Queueing/Scheduling
#
CONFIG_NET_SCH_CBQ=m
CONFIG_NET_SCH_HTB=m
CONFIG_NET_SCH_HFSC=m
CONFIG_NET_SCH_ATM=m
CONFIG_NET_SCH_PRIO=m
CONFIG_NET_SCH_MULTIQ=m
CONFIG_NET_SCH_RED=m
CONFIG_NET_SCH_SFQ=m
CONFIG_NET_SCH_TEQL=m
CONFIG_NET_SCH_TBF=m
CONFIG_NET_SCH_GRED=m
CONFIG_NET_SCH_DSMARK=m
CONFIG_NET_SCH_NETEM=m
CONFIG_NET_SCH_DRR=m
CONFIG_NET_SCH_INGRESS=m

#
# Classification
#
CONFIG_NET_CLS=y
CONFIG_NET_CLS_BASIC=m
CONFIG_NET_CLS_TCINDEX=m
CONFIG_NET_CLS_ROUTE4=m
CONFIG_NET_CLS_ROUTE=y
CONFIG_NET_CLS_FW=m
CONFIG_NET_CLS_U32=m
# CONFIG_CLS_U32_PERF is not set
CONFIG_CLS_U32_MARK=y
CONFIG_NET_CLS_RSVP=m
CONFIG_NET_CLS_RSVP6=m
CONFIG_NET_CLS_FLOW=m
CONFIG_NET_CLS_CGROUP=y
CONFIG_NET_EMATCH=y
CONFIG_NET_EMATCH_STACK=32
CONFIG_NET_EMATCH_CMP=m
CONFIG_NET_EMATCH_NBYTE=m
CONFIG_NET_EMATCH_U32=m
CONFIG_NET_EMATCH_META=m
CONFIG_NET_EMATCH_TEXT=m
CONFIG_NET_CLS_ACT=y
CONFIG_NET_ACT_POLICE=m
CONFIG_NET_ACT_GACT=m
CONFIG_GACT_PROB=y
CONFIG_NET_ACT_MIRRED=m
CONFIG_NET_ACT_IPT=m
CONFIG_NET_ACT_NAT=m
CONFIG_NET_ACT_PEDIT=m
CONFIG_NET_ACT_SIMP=m
CONFIG_NET_ACT_SKBEDIT=m
# CONFIG_NET_CLS_IND is not set
CONFIG_NET_SCH_FIFO=y
CONFIG_DCB=y
CONFIG_RPS=y

#
# Network testing
#
CONFIG_NET_PKTGEN=m
CONFIG_NET_TCPPROBE=m
# CONFIG_NET_DROP_MONITOR is not set
CONFIG_HAMRADIO=y

#
# Packet Radio protocols
#
CONFIG_AX25=m
CONFIG_AX25_DAMA_SLAVE=y
CONFIG_NETROM=m
CONFIG_ROSE=m

#
# AX.25 network device drivers
#
CONFIG_MKISS=m
CONFIG_6PACK=m
CONFIG_BPQETHER=m
CONFIG_SCC=m
# CONFIG_SCC_DELAY is not set
# CONFIG_SCC_TRXECHO is not set
CONFIG_BAYCOM_SER_FDX=m
CONFIG_BAYCOM_SER_HDX=m
CONFIG_BAYCOM_PAR=m
CONFIG_BAYCOM_EPP=m
CONFIG_YAM=m
CONFIG_CAN=m
CONFIG_CAN_RAW=m
CONFIG_CAN_BCM=m

#
# CAN Device Drivers
#
CONFIG_CAN_VCAN=m
CONFIG_CAN_DEV=m
# CONFIG_CAN_CALC_BITTIMING is not set
# CONFIG_CAN_MCP251X is not set
CONFIG_CAN_SJA1000=m
CONFIG_CAN_SJA1000_ISA=m
CONFIG_CAN_SJA1000_PLATFORM=m
CONFIG_CAN_EMS_PCI=m
CONFIG_CAN_KVASER_PCI=m
# CONFIG_CAN_PLX_PCI is not set

#
# CAN USB interfaces
#
CONFIG_CAN_EMS_USB=m
# CONFIG_CAN_DEBUG_DEVICES is not set
CONFIG_IRDA=m

#
# IrDA protocols
#
CONFIG_IRLAN=m
CONFIG_IRNET=m
CONFIG_IRCOMM=m
CONFIG_IRDA_ULTRA=y

#
# IrDA options
#
CONFIG_IRDA_CACHE_LAST_LSAP=y
CONFIG_IRDA_FAST_RR=y
CONFIG_IRDA_DEBUG=y

#
# Infrared-port device drivers
#

#
# SIR device drivers
#
CONFIG_IRTTY_SIR=m

#
# Dongle support
#
CONFIG_DONGLE=y
CONFIG_ESI_DONGLE=m
CONFIG_ACTISYS_DONGLE=m
CONFIG_TEKRAM_DONGLE=m
CONFIG_TOIM3232_DONGLE=m
CONFIG_LITELINK_DONGLE=m
CONFIG_MA600_DONGLE=m
CONFIG_GIRBIL_DONGLE=m
CONFIG_MCP2120_DONGLE=m
CONFIG_OLD_BELKIN_DONGLE=m
CONFIG_ACT200L_DONGLE=m
CONFIG_KINGSUN_DONGLE=m
CONFIG_KSDAZZLE_DONGLE=m
CONFIG_KS959_DONGLE=m

#
# FIR device drivers
#
CONFIG_USB_IRDA=m
CONFIG_SIGMATEL_FIR=m
CONFIG_NSC_FIR=m
CONFIG_WINBOND_FIR=m
CONFIG_TOSHIBA_FIR=m
CONFIG_SMC_IRCC_FIR=m
CONFIG_ALI_FIR=m
CONFIG_VLSI_FIR=m
CONFIG_VIA_FIR=m
CONFIG_MCS_FIR=m
CONFIG_BT=m
CONFIG_BT_L2CAP=m
# CONFIG_BT_L2CAP_EXT_FEATURES is not set
CONFIG_BT_SCO=m
CONFIG_BT_RFCOMM=m
CONFIG_BT_RFCOMM_TTY=y
CONFIG_BT_BNEP=m
CONFIG_BT_BNEP_MC_FILTER=y
CONFIG_BT_BNEP_PROTO_FILTER=y
CONFIG_BT_CMTP=m
CONFIG_BT_HIDP=m

#
# Bluetooth device drivers
#
CONFIG_BT_HCIBTUSB=m
CONFIG_BT_HCIBTSDIO=m
CONFIG_BT_HCIUART=m
CONFIG_BT_HCIUART_H4=y
CONFIG_BT_HCIUART_BCSP=y
CONFIG_BT_HCIUART_LL=y
CONFIG_BT_HCIBCM203X=m
CONFIG_BT_HCIBPA10X=m
CONFIG_BT_HCIBFUSB=m
CONFIG_BT_HCIDTL1=m
CONFIG_BT_HCIBT3C=m
CONFIG_BT_HCIBLUECARD=m
CONFIG_BT_HCIBTUART=m
CONFIG_BT_HCIVHCI=m
CONFIG_BT_MRVL=m
CONFIG_BT_MRVL_SDIO=m
# CONFIG_BT_ATH3K is not set
CONFIG_AF_RXRPC=m
# CONFIG_AF_RXRPC_DEBUG is not set
CONFIG_RXKAD=m
CONFIG_FIB_RULES=y
CONFIG_WIRELESS=y
CONFIG_WIRELESS_EXT=y
CONFIG_WEXT_CORE=y
CONFIG_WEXT_PROC=y
CONFIG_WEXT_SPY=y
CONFIG_WEXT_PRIV=y
CONFIG_CFG80211=m
CONFIG_NL80211_TESTMODE=y
# CONFIG_CFG80211_DEVELOPER_WARNINGS is not set
CONFIG_CFG80211_REG_DEBUG=y
CONFIG_CFG80211_DEFAULT_PS=y
CONFIG_CFG80211_DEBUGFS=y
# CONFIG_CFG80211_INTERNAL_REGDB is not set
CONFIG_CFG80211_WEXT=y
CONFIG_WIRELESS_EXT_SYSFS=y
CONFIG_LIB80211=m
CONFIG_LIB80211_CRYPT_WEP=m
CONFIG_LIB80211_CRYPT_CCMP=m
CONFIG_LIB80211_CRYPT_TKIP=m
# CONFIG_LIB80211_DEBUG is not set
CONFIG_MAC80211=m
CONFIG_MAC80211_HAS_RC=y
CONFIG_MAC80211_RC_MINSTREL=y
# CONFIG_MAC80211_RC_DEFAULT_PID is not set
CONFIG_MAC80211_RC_DEFAULT_MINSTREL=y
CONFIG_MAC80211_RC_DEFAULT="minstrel"
CONFIG_MAC80211_MESH=y
CONFIG_MAC80211_LEDS=y
CONFIG_MAC80211_DEBUGFS=y
# CONFIG_MAC80211_DEBUG_MENU is not set
CONFIG_WIMAX=m
CONFIG_WIMAX_DEBUG_LEVEL=8
CONFIG_RFKILL=y
CONFIG_RFKILL_LEDS=y
CONFIG_RFKILL_INPUT=y
CONFIG_NET_9P=m
CONFIG_NET_9P_VIRTIO=m
CONFIG_NET_9P_RDMA=m
# CONFIG_NET_9P_DEBUG is not set
# CONFIG_CAIF is not set

#
# Device Drivers
#

#
# Generic Driver Options
#
CONFIG_UEVENT_HELPER_PATH=""
CONFIG_DEVTMPFS=y
CONFIG_DEVTMPFS_MOUNT=y
# CONFIG_STANDALONE is not set
CONFIG_PREVENT_FIRMWARE_BUILD=y
CONFIG_FW_LOADER=y
CONFIG_FIRMWARE_IN_KERNEL=y
CONFIG_EXTRA_FIRMWARE=""
# CONFIG_DEBUG_DRIVER is not set
# CONFIG_DEBUG_DEVRES is not set
# CONFIG_SYS_HYPERVISOR is not set
CONFIG_CONNECTOR=y
CONFIG_PROC_EVENTS=y
CONFIG_MTD=m
# CONFIG_MTD_DEBUG is not set
CONFIG_MTD_TESTS=m
CONFIG_MTD_CONCAT=m
CONFIG_MTD_PARTITIONS=y
CONFIG_MTD_REDBOOT_PARTS=m
CONFIG_MTD_REDBOOT_DIRECTORY_BLOCK=-1
# CONFIG_MTD_REDBOOT_PARTS_UNALLOCATED is not set
# CONFIG_MTD_REDBOOT_PARTS_READONLY is not set
CONFIG_MTD_AR7_PARTS=m

#
# User Modules And Translation Layers
#
CONFIG_MTD_CHAR=m
CONFIG_HAVE_MTD_OTP=y
CONFIG_MTD_BLKDEVS=m
CONFIG_MTD_BLOCK=m
CONFIG_MTD_BLOCK_RO=m
CONFIG_FTL=m
CONFIG_NFTL=m
CONFIG_NFTL_RW=y
CONFIG_INFTL=m
CONFIG_RFD_FTL=m
CONFIG_SSFDC=m
# CONFIG_SM_FTL is not set
CONFIG_MTD_OOPS=m

#
# RAM/ROM/Flash chip drivers
#
CONFIG_MTD_CFI=m
CONFIG_MTD_JEDECPROBE=m
CONFIG_MTD_GEN_PROBE=m
# CONFIG_MTD_CFI_ADV_OPTIONS is not set
CONFIG_MTD_MAP_BANK_WIDTH_1=y
CONFIG_MTD_MAP_BANK_WIDTH_2=y
CONFIG_MTD_MAP_BANK_WIDTH_4=y
# CONFIG_MTD_MAP_BANK_WIDTH_8 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_16 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_32 is not set
CONFIG_MTD_CFI_I1=y
CONFIG_MTD_CFI_I2=y
# CONFIG_MTD_CFI_I4 is not set
# CONFIG_MTD_CFI_I8 is not set
CONFIG_MTD_CFI_INTELEXT=m
CONFIG_MTD_CFI_AMDSTD=m
CONFIG_MTD_CFI_STAA=m
CONFIG_MTD_CFI_UTIL=m
CONFIG_MTD_RAM=m
CONFIG_MTD_ROM=m
CONFIG_MTD_ABSENT=m

#
# Mapping drivers for chip access
#
CONFIG_MTD_COMPLEX_MAPPINGS=y
CONFIG_MTD_PHYSMAP=m
# CONFIG_MTD_PHYSMAP_COMPAT is not set
CONFIG_MTD_SC520CDP=m
CONFIG_MTD_NETSC520=m
CONFIG_MTD_TS5500=m
CONFIG_MTD_SBC_GXX=m
CONFIG_MTD_SCx200_DOCFLASH=m
CONFIG_MTD_AMD76XROM=m
CONFIG_MTD_ICHXROM=m
CONFIG_MTD_ESB2ROM=m
CONFIG_MTD_CK804XROM=m
CONFIG_MTD_SCB2_FLASH=m
CONFIG_MTD_NETtel=m
CONFIG_MTD_L440GX=m
CONFIG_MTD_PCI=m
# CONFIG_MTD_PCMCIA is not set
CONFIG_MTD_GPIO_ADDR=m
CONFIG_MTD_INTEL_VR_NOR=m
CONFIG_MTD_PLATRAM=m

#
# Self-contained MTD device drivers
#
CONFIG_MTD_PMC551=m
# CONFIG_MTD_PMC551_BUGFIX is not set
# CONFIG_MTD_PMC551_DEBUG is not set
CONFIG_MTD_DATAFLASH=m
# CONFIG_MTD_DATAFLASH_WRITE_VERIFY is not set
CONFIG_MTD_DATAFLASH_OTP=y
CONFIG_MTD_M25P80=m
CONFIG_M25PXX_USE_FAST_READ=y
CONFIG_MTD_SST25L=m
CONFIG_MTD_SLRAM=m
CONFIG_MTD_PHRAM=m
CONFIG_MTD_MTDRAM=m
CONFIG_MTDRAM_TOTAL_SIZE=4096
CONFIG_MTDRAM_ERASE_SIZE=128
CONFIG_MTD_BLOCK2MTD=m

#
# Disk-On-Chip Device Drivers
#
CONFIG_MTD_DOC2000=m
CONFIG_MTD_DOC2001=m
CONFIG_MTD_DOC2001PLUS=m
CONFIG_MTD_DOCPROBE=m
CONFIG_MTD_DOCECC=m
# CONFIG_MTD_DOCPROBE_ADVANCED is not set
CONFIG_MTD_DOCPROBE_ADDRESS=0
CONFIG_MTD_NAND_ECC=m
# CONFIG_MTD_NAND_ECC_SMC is not set
CONFIG_MTD_NAND=m
# CONFIG_MTD_NAND_VERIFY_WRITE is not set
# CONFIG_MTD_SM_COMMON is not set
# CONFIG_MTD_NAND_MUSEUM_IDS is not set
# CONFIG_MTD_NAND_DENALI is not set
CONFIG_MTD_NAND_DENALI_SCRATCH_REG_ADDR=0xFF108018
CONFIG_MTD_NAND_IDS=m
# CONFIG_MTD_NAND_RICOH is not set
CONFIG_MTD_NAND_DISKONCHIP=m
# CONFIG_MTD_NAND_DISKONCHIP_PROBE_ADVANCED is not set
CONFIG_MTD_NAND_DISKONCHIP_PROBE_ADDRESS=0
# CONFIG_MTD_NAND_DISKONCHIP_BBTWRITE is not set
CONFIG_MTD_NAND_CAFE=m
CONFIG_MTD_NAND_CS553X=m
CONFIG_MTD_NAND_NANDSIM=m
CONFIG_MTD_NAND_PLATFORM=m
CONFIG_MTD_ALAUDA=m
CONFIG_MTD_ONENAND=m
CONFIG_MTD_ONENAND_VERIFY_WRITE=y
CONFIG_MTD_ONENAND_GENERIC=m
# CONFIG_MTD_ONENAND_OTP is not set
CONFIG_MTD_ONENAND_2X_PROGRAM=y
CONFIG_MTD_ONENAND_SIM=m

#
# LPDDR flash memory drivers
#
CONFIG_MTD_LPDDR=m
CONFIG_MTD_QINFO_PROBE=m

#
# UBI - Unsorted block images
#
CONFIG_MTD_UBI=m
CONFIG_MTD_UBI_WL_THRESHOLD=4096
CONFIG_MTD_UBI_BEB_RESERVE=1
CONFIG_MTD_UBI_GLUEBI=m

#
# UBI debugging options
#
# CONFIG_MTD_UBI_DEBUG is not set
CONFIG_PARPORT=m
CONFIG_PARPORT_PC=m
CONFIG_PARPORT_SERIAL=m
CONFIG_PARPORT_PC_FIFO=y
# CONFIG_PARPORT_PC_SUPERIO is not set
CONFIG_PARPORT_PC_PCMCIA=m
# CONFIG_PARPORT_GSC is not set
CONFIG_PARPORT_AX88796=m
CONFIG_PARPORT_1284=y
CONFIG_PARPORT_NOT_PC=y
CONFIG_PNP=y
CONFIG_PNP_DEBUG_MESSAGES=y

#
# Protocols
#
CONFIG_ISAPNP=y
CONFIG_PNPBIOS=y
CONFIG_PNPBIOS_PROC_FS=y
CONFIG_PNPACPI=y
CONFIG_BLK_DEV=y
CONFIG_BLK_DEV_FD=m
# CONFIG_BLK_DEV_XD is not set
CONFIG_PARIDE=m

#
# Parallel IDE high-level drivers
#
CONFIG_PARIDE_PD=m
CONFIG_PARIDE_PCD=m
CONFIG_PARIDE_PF=m
CONFIG_PARIDE_PT=m
CONFIG_PARIDE_PG=m

#
# Parallel IDE protocol modules
#
CONFIG_PARIDE_ATEN=m
CONFIG_PARIDE_BPCK=m
CONFIG_PARIDE_BPCK6=m
CONFIG_PARIDE_COMM=m
CONFIG_PARIDE_DSTR=m
CONFIG_PARIDE_FIT2=m
CONFIG_PARIDE_FIT3=m
CONFIG_PARIDE_EPAT=m
# CONFIG_PARIDE_EPATC8 is not set
CONFIG_PARIDE_EPIA=m
CONFIG_PARIDE_FRIQ=m
CONFIG_PARIDE_FRPW=m
CONFIG_PARIDE_KBIC=m
CONFIG_PARIDE_KTTI=m
CONFIG_PARIDE_ON20=m
CONFIG_PARIDE_ON26=m
CONFIG_BLK_CPQ_DA=m
CONFIG_BLK_CPQ_CISS_DA=m
CONFIG_CISS_SCSI_TAPE=y
CONFIG_BLK_DEV_DAC960=m
CONFIG_BLK_DEV_UMEM=m
# CONFIG_BLK_DEV_COW_COMMON is not set
CONFIG_BLK_DEV_LOOP=y
CONFIG_BLK_DEV_CRYPTOLOOP=m
# CONFIG_BLK_DEV_DRBD is not set
CONFIG_BLK_DEV_NBD=m
CONFIG_BLK_DEV_OSD=m
CONFIG_BLK_DEV_SX8=m
# CONFIG_BLK_DEV_UB is not set
CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_RAM_COUNT=16
CONFIG_BLK_DEV_RAM_SIZE=65536
# CONFIG_BLK_DEV_XIP is not set
CONFIG_CDROM_PKTCDVD=y
CONFIG_CDROM_PKTCDVD_BUFFERS=8
# CONFIG_CDROM_PKTCDVD_WCACHE is not set
CONFIG_ATA_OVER_ETH=m
CONFIG_VIRTIO_BLK=m
# CONFIG_BLK_DEV_HD is not set
CONFIG_MISC_DEVICES=y
# CONFIG_AD525X_DPOT is not set
CONFIG_IBM_ASM=m
CONFIG_PHANTOM=m
CONFIG_SGI_IOC4=m
CONFIG_TIFM_CORE=m
CONFIG_TIFM_7XX1=m
CONFIG_ICS932S401=m
CONFIG_ENCLOSURE_SERVICES=m
# CONFIG_CS5535_MFGPT is not set
CONFIG_HP_ILO=m
CONFIG_ISL29003=m
CONFIG_SENSORS_TSL2550=m
CONFIG_DS1682=m
# CONFIG_TI_DAC7512 is not set
# CONFIG_VMWARE_BALLOON is not set
CONFIG_C2PORT=m
CONFIG_C2PORT_DURAMAR_2150=m

#
# EEPROM support
#
CONFIG_EEPROM_AT24=m
CONFIG_EEPROM_AT25=m
CONFIG_EEPROM_LEGACY=m
CONFIG_EEPROM_MAX6875=m
CONFIG_EEPROM_93CX6=m
CONFIG_CB710_CORE=m
# CONFIG_CB710_DEBUG is not set
CONFIG_CB710_DEBUG_ASSUMPTIONS=y
CONFIG_IWMC3200TOP=m
# CONFIG_IWMC3200TOP_DEBUG is not set
# CONFIG_IWMC3200TOP_DEBUGFS is not set
CONFIG_HAVE_IDE=y
# CONFIG_IDE is not set

#
# SCSI device support
#
CONFIG_SCSI_MOD=y
CONFIG_RAID_ATTRS=m
CONFIG_SCSI=y
CONFIG_SCSI_DMA=y
CONFIG_SCSI_TGT=m
CONFIG_SCSI_NETLINK=y
CONFIG_SCSI_PROC_FS=y

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=y
CONFIG_CHR_DEV_ST=m
CONFIG_CHR_DEV_OSST=m
CONFIG_BLK_DEV_SR=y
# CONFIG_BLK_DEV_SR_VENDOR is not set
CONFIG_CHR_DEV_SG=y
CONFIG_CHR_DEV_SCH=m
CONFIG_SCSI_ENCLOSURE=m
CONFIG_SCSI_MULTI_LUN=y
CONFIG_SCSI_CONSTANTS=y
CONFIG_SCSI_LOGGING=y
CONFIG_SCSI_SCAN_ASYNC=y
CONFIG_SCSI_WAIT_SCAN=m

#
# SCSI Transports
#
CONFIG_SCSI_SPI_ATTRS=m
CONFIG_SCSI_FC_ATTRS=m
CONFIG_SCSI_FC_TGT_ATTRS=y
CONFIG_SCSI_ISCSI_ATTRS=m
CONFIG_SCSI_SAS_ATTRS=m
CONFIG_SCSI_SAS_LIBSAS=m
CONFIG_SCSI_SAS_ATA=y
CONFIG_SCSI_SAS_HOST_SMP=y
# CONFIG_SCSI_SAS_LIBSAS_DEBUG is not set
CONFIG_SCSI_SRP_ATTRS=m
CONFIG_SCSI_SRP_TGT_ATTRS=y
CONFIG_SCSI_LOWLEVEL=y
CONFIG_ISCSI_TCP=m
CONFIG_SCSI_CXGB3_ISCSI=m
CONFIG_SCSI_BNX2_ISCSI=m
CONFIG_BE2ISCSI=m
CONFIG_BLK_DEV_3W_XXXX_RAID=m
# CONFIG_SCSI_HPSA is not set
CONFIG_SCSI_3W_9XXX=m
# CONFIG_SCSI_3W_SAS is not set
CONFIG_SCSI_7000FASST=m
CONFIG_SCSI_ACARD=m
CONFIG_SCSI_AHA152X=m
CONFIG_SCSI_AHA1542=m
CONFIG_SCSI_AHA1740=m
CONFIG_SCSI_AACRAID=m
CONFIG_SCSI_AIC7XXX=m
CONFIG_AIC7XXX_CMDS_PER_DEVICE=8
CONFIG_AIC7XXX_RESET_DELAY_MS=15000
CONFIG_AIC7XXX_DEBUG_ENABLE=y
CONFIG_AIC7XXX_DEBUG_MASK=0
CONFIG_AIC7XXX_REG_PRETTY_PRINT=y
# CONFIG_SCSI_AIC7XXX_OLD is not set
CONFIG_SCSI_AIC79XX=m
CONFIG_AIC79XX_CMDS_PER_DEVICE=32
CONFIG_AIC79XX_RESET_DELAY_MS=5000
CONFIG_AIC79XX_DEBUG_ENABLE=y
CONFIG_AIC79XX_DEBUG_MASK=0
CONFIG_AIC79XX_REG_PRETTY_PRINT=y
CONFIG_SCSI_AIC94XX=m
# CONFIG_AIC94XX_DEBUG is not set
CONFIG_SCSI_MVSAS=m
CONFIG_SCSI_MVSAS_DEBUG=y
CONFIG_SCSI_DPT_I2O=m
CONFIG_SCSI_ADVANSYS=m
CONFIG_SCSI_IN2000=m
CONFIG_SCSI_ARCMSR=m
CONFIG_SCSI_ARCMSR_AER=y
CONFIG_MEGARAID_NEWGEN=y
CONFIG_MEGARAID_MM=m
CONFIG_MEGARAID_MAILBOX=m
CONFIG_MEGARAID_LEGACY=m
CONFIG_MEGARAID_SAS=m
CONFIG_SCSI_MPT2SAS=m
CONFIG_SCSI_MPT2SAS_MAX_SGE=128
# CONFIG_SCSI_MPT2SAS_LOGGING is not set
CONFIG_SCSI_HPTIOP=m
CONFIG_SCSI_BUSLOGIC=m
# CONFIG_SCSI_FLASHPOINT is not set
CONFIG_VMWARE_PVSCSI=m
CONFIG_LIBFC=m
CONFIG_LIBFCOE=m
CONFIG_FCOE=m
CONFIG_FCOE_FNIC=m
CONFIG_SCSI_DMX3191D=m
CONFIG_SCSI_DTC3280=m
CONFIG_SCSI_EATA=m
CONFIG_SCSI_EATA_TAGGED_QUEUE=y
CONFIG_SCSI_EATA_LINKED_COMMANDS=y
CONFIG_SCSI_EATA_MAX_TAGS=16
CONFIG_SCSI_FUTURE_DOMAIN=m
CONFIG_SCSI_FD_MCS=m
CONFIG_SCSI_GDTH=m
CONFIG_SCSI_GENERIC_NCR5380=m
CONFIG_SCSI_GENERIC_NCR5380_MMIO=m
CONFIG_SCSI_GENERIC_NCR53C400=y
CONFIG_SCSI_IBMMCA=m
CONFIG_IBMMCA_SCSI_ORDER_STANDARD=y
# CONFIG_IBMMCA_SCSI_DEV_RESET is not set
CONFIG_SCSI_IPS=m
CONFIG_SCSI_INITIO=m
CONFIG_SCSI_INIA100=m
CONFIG_SCSI_PPA=m
CONFIG_SCSI_IMM=m
# CONFIG_SCSI_IZIP_EPP16 is not set
# CONFIG_SCSI_IZIP_SLOW_CTR is not set
CONFIG_SCSI_NCR53C406A=m
CONFIG_SCSI_NCR_D700=m
CONFIG_SCSI_STEX=m
CONFIG_SCSI_SYM53C8XX_2=m
CONFIG_SCSI_SYM53C8XX_DMA_ADDRESSING_MODE=1
CONFIG_SCSI_SYM53C8XX_DEFAULT_TAGS=16
CONFIG_SCSI_SYM53C8XX_MAX_TAGS=64
CONFIG_SCSI_SYM53C8XX_MMIO=y
CONFIG_SCSI_IPR=m
# CONFIG_SCSI_IPR_TRACE is not set
# CONFIG_SCSI_IPR_DUMP is not set
CONFIG_SCSI_NCR_Q720=m
CONFIG_SCSI_NCR53C8XX_DEFAULT_TAGS=8
CONFIG_SCSI_NCR53C8XX_MAX_TAGS=4
CONFIG_SCSI_NCR53C8XX_SYNC=5
CONFIG_SCSI_PAS16=m
CONFIG_SCSI_QLOGIC_FAS=m
CONFIG_SCSI_QLOGIC_1280=m
CONFIG_SCSI_QLA_FC=m
CONFIG_SCSI_QLA_ISCSI=m
CONFIG_SCSI_LPFC=m
CONFIG_SCSI_LPFC_DEBUG_FS=y
CONFIG_SCSI_SIM710=m
CONFIG_SCSI_SYM53C416=m
CONFIG_SCSI_DC395x=m
CONFIG_SCSI_DC390T=m
CONFIG_SCSI_T128=m
CONFIG_SCSI_U14_34F=m
CONFIG_SCSI_U14_34F_TAGGED_QUEUE=y
CONFIG_SCSI_U14_34F_LINKED_COMMANDS=y
CONFIG_SCSI_U14_34F_MAX_TAGS=8
CONFIG_SCSI_ULTRASTOR=m
CONFIG_SCSI_NSP32=m
CONFIG_SCSI_DEBUG=m
CONFIG_SCSI_PMCRAID=m
# CONFIG_SCSI_PM8001 is not set
CONFIG_SCSI_SRP=m
CONFIG_SCSI_BFA_FC=m
CONFIG_SCSI_LOWLEVEL_PCMCIA=y
CONFIG_PCMCIA_AHA152X=m
CONFIG_PCMCIA_FDOMAIN=m
CONFIG_PCMCIA_NINJA_SCSI=m
CONFIG_PCMCIA_QLOGIC=m
CONFIG_PCMCIA_SYM53C500=m
CONFIG_SCSI_DH=y
CONFIG_SCSI_DH_RDAC=m
CONFIG_SCSI_DH_HP_SW=m
CONFIG_SCSI_DH_EMC=m
CONFIG_SCSI_DH_ALUA=m
CONFIG_SCSI_OSD_INITIATOR=m
CONFIG_SCSI_OSD_ULD=m
CONFIG_SCSI_OSD_DPRINT_SENSE=1
# CONFIG_SCSI_OSD_DEBUG is not set
CONFIG_ATA=y
# CONFIG_ATA_NONSTANDARD is not set
CONFIG_ATA_VERBOSE_ERROR=y
CONFIG_ATA_ACPI=y
CONFIG_SATA_PMP=y

#
# Controllers with non-SFF native interface
#
CONFIG_SATA_AHCI=y
CONFIG_SATA_AHCI_PLATFORM=y
CONFIG_SATA_INIC162X=m
CONFIG_SATA_SIL24=m
CONFIG_ATA_SFF=y

#
# SFF controllers with custom DMA interface
#
CONFIG_PDC_ADMA=y
CONFIG_SATA_QSTOR=m
CONFIG_SATA_SX4=m
CONFIG_ATA_BMDMA=y

#
# SATA SFF controllers with BMDMA
#
CONFIG_ATA_PIIX=y
CONFIG_SATA_MV=y
CONFIG_SATA_NV=m
CONFIG_SATA_PROMISE=m
CONFIG_SATA_SIL=m
CONFIG_SATA_SIS=m
CONFIG_SATA_SVW=m
CONFIG_SATA_ULI=m
CONFIG_SATA_VIA=m
CONFIG_SATA_VITESSE=m

#
# PATA SFF controllers with BMDMA
#
CONFIG_PATA_ALI=m
CONFIG_PATA_AMD=m
CONFIG_PATA_ARTOP=m
CONFIG_PATA_ATIIXP=m
CONFIG_PATA_ATP867X=m
CONFIG_PATA_CMD64X=m
CONFIG_PATA_CS5520=m
CONFIG_PATA_CS5530=m
CONFIG_PATA_CS5535=m
CONFIG_PATA_CS5536=m
CONFIG_PATA_CYPRESS=m
CONFIG_PATA_EFAR=m
CONFIG_PATA_HPT366=m
CONFIG_PATA_HPT37X=m
CONFIG_PATA_HPT3X2N=m
CONFIG_PATA_HPT3X3=m
# CONFIG_PATA_HPT3X3_DMA is not set
CONFIG_PATA_IT8213=m
CONFIG_PATA_IT821X=m
CONFIG_PATA_JMICRON=m
CONFIG_PATA_MARVELL=m
CONFIG_PATA_NETCELL=m
CONFIG_PATA_NINJA32=m
CONFIG_PATA_NS87415=m
CONFIG_PATA_OLDPIIX=m
CONFIG_PATA_OPTIDMA=m
CONFIG_PATA_PDC2027X=m
CONFIG_PATA_PDC_OLD=m
CONFIG_PATA_RADISYS=m
CONFIG_PATA_RDC=m
CONFIG_PATA_SC1200=m
CONFIG_PATA_SCH=m
CONFIG_PATA_SERVERWORKS=m
CONFIG_PATA_SIL680=m
CONFIG_PATA_SIS=y
# CONFIG_PATA_TOSHIBA is not set
CONFIG_PATA_TRIFLEX=m
CONFIG_PATA_VIA=m
CONFIG_PATA_WINBOND=m

#
# PIO-only SFF controllers
#
CONFIG_PATA_CMD640_PCI=m
CONFIG_PATA_ISAPNP=m
CONFIG_PATA_MPIIX=m
CONFIG_PATA_NS87410=m
CONFIG_PATA_OPTI=m
CONFIG_PATA_PCMCIA=m
CONFIG_PATA_QDI=m
CONFIG_PATA_RZ1000=m
CONFIG_PATA_WINBOND_VLB=m

#
# Generic fallback / legacy drivers
#
CONFIG_PATA_ACPI=y
CONFIG_ATA_GENERIC=y
CONFIG_PATA_LEGACY=m
CONFIG_MD=y
CONFIG_BLK_DEV_MD=y
CONFIG_MD_AUTODETECT=y
CONFIG_MD_LINEAR=m
CONFIG_MD_RAID0=m
CONFIG_MD_RAID1=m
CONFIG_MD_RAID10=m
CONFIG_MD_RAID456=m
# CONFIG_MULTICORE_RAID456 is not set
CONFIG_MD_RAID6_PQ=m
CONFIG_ASYNC_RAID6_TEST=m
CONFIG_MD_MULTIPATH=m
CONFIG_MD_FAULTY=m
CONFIG_BLK_DEV_DM=y
# CONFIG_DM_DEBUG is not set
CONFIG_DM_CRYPT=m
CONFIG_DM_SNAPSHOT=y
CONFIG_DM_MIRROR=y
# CONFIG_DM_LOG_USERSPACE is not set
CONFIG_DM_ZERO=m
CONFIG_DM_MULTIPATH=y
CONFIG_DM_MULTIPATH_QL=m
CONFIG_DM_MULTIPATH_ST=m
# CONFIG_DM_DELAY is not set
CONFIG_DM_UEVENT=y
CONFIG_FUSION=y
CONFIG_FUSION_SPI=m
CONFIG_FUSION_FC=m
CONFIG_FUSION_SAS=m
CONFIG_FUSION_MAX_SGE=128
CONFIG_FUSION_CTL=m
CONFIG_FUSION_LAN=m
CONFIG_FUSION_LOGGING=y

#
# IEEE 1394 (FireWire) support
#

#
# You can enable one or both FireWire driver stacks.
#

#
# The newer stack is recommended.
#
CONFIG_FIREWIRE=m
CONFIG_FIREWIRE_OHCI=m
CONFIG_FIREWIRE_OHCI_DEBUG=y
CONFIG_FIREWIRE_SBP2=m
CONFIG_FIREWIRE_NET=m
CONFIG_IEEE1394=m
CONFIG_IEEE1394_OHCI1394=m
CONFIG_IEEE1394_PCILYNX=m
CONFIG_IEEE1394_SBP2=m
# CONFIG_IEEE1394_SBP2_PHYS_DMA is not set
CONFIG_IEEE1394_ETH1394_ROM_ENTRY=y
CONFIG_IEEE1394_ETH1394=m
CONFIG_IEEE1394_RAWIO=m
CONFIG_IEEE1394_VIDEO1394=m
CONFIG_IEEE1394_DV1394=m
# CONFIG_IEEE1394_VERBOSEDEBUG is not set
CONFIG_I2O=m
CONFIG_I2O_LCT_NOTIFY_ON_CHANGES=y
CONFIG_I2O_EXT_ADAPTEC=y
CONFIG_I2O_CONFIG=m
CONFIG_I2O_CONFIG_OLD_IOCTL=y
CONFIG_I2O_BUS=m
CONFIG_I2O_BLOCK=m
CONFIG_I2O_SCSI=m
CONFIG_I2O_PROC=m
CONFIG_MACINTOSH_DRIVERS=y
CONFIG_MAC_EMUMOUSEBTN=y
CONFIG_NETDEVICES=y
CONFIG_IFB=m
CONFIG_DUMMY=m
CONFIG_BONDING=m
CONFIG_MACVLAN=m
# CONFIG_MACVTAP is not set
CONFIG_EQUALIZER=m
CONFIG_TUN=y
CONFIG_VETH=m
CONFIG_NET_SB1000=m
CONFIG_ARCNET=m
CONFIG_ARCNET_1201=m
CONFIG_ARCNET_1051=m
CONFIG_ARCNET_RAW=m
CONFIG_ARCNET_CAP=m
CONFIG_ARCNET_COM90xx=m
CONFIG_ARCNET_COM90xxIO=m
CONFIG_ARCNET_RIM_I=m
CONFIG_ARCNET_COM20020=m
CONFIG_ARCNET_COM20020_ISA=m
CONFIG_ARCNET_COM20020_PCI=m
CONFIG_PHYLIB=y

#
# MII PHY device drivers
#
CONFIG_MARVELL_PHY=y
CONFIG_DAVICOM_PHY=y
CONFIG_QSEMI_PHY=y
CONFIG_LXT_PHY=y
CONFIG_CICADA_PHY=y
CONFIG_VITESSE_PHY=y
CONFIG_SMSC_PHY=y
CONFIG_BROADCOM_PHY=y
CONFIG_ICPLUS_PHY=y
CONFIG_REALTEK_PHY=y
CONFIG_NATIONAL_PHY=y
CONFIG_STE10XP=y
CONFIG_LSI_ET1011C_PHY=y
# CONFIG_MICREL_PHY is not set
CONFIG_FIXED_PHY=y
CONFIG_MDIO_BITBANG=y
CONFIG_MDIO_GPIO=y
CONFIG_NET_ETHERNET=y
CONFIG_MII=m
CONFIG_HAPPYMEAL=m
CONFIG_SUNGEM=m
CONFIG_CASSINI=m
CONFIG_NET_VENDOR_3COM=y
CONFIG_EL1=m
CONFIG_EL2=m
CONFIG_ELPLUS=m
CONFIG_EL16=m
CONFIG_EL3=m
CONFIG_3C515=m
CONFIG_ELMC=m
CONFIG_ELMC_II=m
CONFIG_VORTEX=m
CONFIG_TYPHOON=m
CONFIG_LANCE=m
CONFIG_NET_VENDOR_SMC=y
CONFIG_WD80x3=m
CONFIG_ULTRAMCA=m
CONFIG_ULTRA=m
CONFIG_ULTRA32=m
CONFIG_SMC9194=m
# CONFIG_ENC28J60 is not set
CONFIG_ETHOC=m
CONFIG_NET_VENDOR_RACAL=y
CONFIG_NI52=m
CONFIG_NI65=m
CONFIG_DNET=m
CONFIG_NET_TULIP=y
CONFIG_DE2104X=m
CONFIG_DE2104X_DSL=0
CONFIG_TULIP=m
# CONFIG_TULIP_MWI is not set
# CONFIG_TULIP_MMIO is not set
# CONFIG_TULIP_NAPI is not set
CONFIG_DE4X5=m
CONFIG_WINBOND_840=m
CONFIG_DM9102=m
CONFIG_ULI526X=m
CONFIG_PCMCIA_XIRCOM=m
CONFIG_AT1700=m
CONFIG_DEPCA=m
CONFIG_HP100=m
CONFIG_NET_ISA=y
CONFIG_E2100=m
CONFIG_EWRK3=m
CONFIG_EEXPRESS=m
CONFIG_EEXPRESS_PRO=m
CONFIG_HPLAN_PLUS=m
CONFIG_HPLAN=m
CONFIG_LP486E=m
CONFIG_ETH16I=m
CONFIG_NE2000=m
CONFIG_ZNET=m
CONFIG_SEEQ8005=m
CONFIG_NE2_MCA=m
CONFIG_IBMLANA=m
# CONFIG_IBM_NEW_EMAC_ZMII is not set
# CONFIG_IBM_NEW_EMAC_RGMII is not set
# CONFIG_IBM_NEW_EMAC_TAH is not set
# CONFIG_IBM_NEW_EMAC_EMAC4 is not set
# CONFIG_IBM_NEW_EMAC_NO_FLOW_CTRL is not set
# CONFIG_IBM_NEW_EMAC_MAL_CLR_ICINTSTAT is not set
# CONFIG_IBM_NEW_EMAC_MAL_COMMON_ERR is not set
CONFIG_NET_PCI=y
CONFIG_PCNET32=m
CONFIG_AMD8111_ETH=m
CONFIG_ADAPTEC_STARFIRE=m
CONFIG_AC3200=m
# CONFIG_KSZ884X_PCI is not set
CONFIG_APRICOT=m
CONFIG_B44=m
CONFIG_B44_PCI_AUTOSELECT=y
CONFIG_B44_PCICORE_AUTOSELECT=y
CONFIG_B44_PCI=y
CONFIG_FORCEDETH=m
CONFIG_CS89x0=m
CONFIG_E100=m
CONFIG_LNE390=m
CONFIG_FEALNX=m
CONFIG_NATSEMI=m
CONFIG_NE2K_PCI=m
CONFIG_NE3210=m
CONFIG_ES3210=m
CONFIG_8139CP=m
CONFIG_8139TOO=m
CONFIG_8139TOO_PIO=y
# CONFIG_8139TOO_TUNE_TWISTER is not set
CONFIG_8139TOO_8129=y
# CONFIG_8139_OLD_RX_RESET is not set
# CONFIG_R6040 is not set
CONFIG_SIS900=m
CONFIG_EPIC100=m
CONFIG_SMSC9420=m
CONFIG_SUNDANCE=m
# CONFIG_SUNDANCE_MMIO is not set
CONFIG_TLAN=m
CONFIG_KS8842=m
CONFIG_KS8851=m
CONFIG_KS8851_MLL=m
CONFIG_VIA_RHINE=m
CONFIG_VIA_RHINE_MMIO=y
CONFIG_SC92031=m
CONFIG_NET_POCKET=y
CONFIG_ATP=m
CONFIG_DE600=m
CONFIG_DE620=m
CONFIG_ATL2=m
CONFIG_NETDEV_1000=y
CONFIG_ACENIC=m
# CONFIG_ACENIC_OMIT_TIGON_I is not set
# CONFIG_DL2K is not set
CONFIG_E1000=m
CONFIG_E1000E=m
CONFIG_IP1000=m
CONFIG_IGB=m
CONFIG_IGB_DCA=y
CONFIG_IGBVF=m
CONFIG_NS83820=m
CONFIG_HAMACHI=m
CONFIG_YELLOWFIN=m
CONFIG_R8169=m
CONFIG_R8169_VLAN=y
CONFIG_SIS190=m
CONFIG_SKGE=m
# CONFIG_SKGE_DEBUG is not set
CONFIG_SKY2=m
# CONFIG_SKY2_DEBUG is not set
CONFIG_VIA_VELOCITY=m
CONFIG_TIGON3=m
CONFIG_BNX2=m
CONFIG_CNIC=m
CONFIG_QLA3XXX=m
CONFIG_ATL1=m
CONFIG_ATL1E=m
CONFIG_ATL1C=m
CONFIG_JME=m
CONFIG_NETDEV_10000=y
CONFIG_MDIO=m
CONFIG_CHELSIO_T1=m
CONFIG_CHELSIO_T1_1G=y
CONFIG_CHELSIO_T3_DEPENDS=y
CONFIG_CHELSIO_T3=m
CONFIG_CHELSIO_T4_DEPENDS=y
# CONFIG_CHELSIO_T4 is not set
CONFIG_ENIC=m
CONFIG_IXGBE=m
CONFIG_IXGBE_DCA=y
CONFIG_IXGBE_DCB=y
# CONFIG_IXGBEVF is not set
CONFIG_IXGB=m
CONFIG_S2IO=m
CONFIG_VXGE=m
# CONFIG_VXGE_DEBUG_TRACE_ALL is not set
CONFIG_MYRI10GE=m
CONFIG_MYRI10GE_DCA=y
CONFIG_NETXEN_NIC=m
CONFIG_NIU=m
CONFIG_MLX4_EN=m
CONFIG_MLX4_CORE=m
CONFIG_MLX4_DEBUG=y
CONFIG_TEHUTI=m
CONFIG_BNX2X=m
# CONFIG_QLCNIC is not set
CONFIG_QLGE=m
CONFIG_SFC=m
CONFIG_SFC_MTD=y
CONFIG_BE2NET=m
CONFIG_TR=y
CONFIG_IBMTR=m
CONFIG_IBMOL=m
CONFIG_IBMLS=m
CONFIG_3C359=m
CONFIG_TMS380TR=m
CONFIG_TMSPCI=m
CONFIG_SKISA=m
CONFIG_PROTEON=m
CONFIG_ABYSS=m
CONFIG_MADGEMC=m
CONFIG_SMCTR=m
CONFIG_WLAN=y
CONFIG_PCMCIA_RAYCS=m
CONFIG_LIBERTAS_THINFIRM=m
# CONFIG_LIBERTAS_THINFIRM_DEBUG is not set
CONFIG_LIBERTAS_THINFIRM_USB=m
CONFIG_AIRO=m
CONFIG_ATMEL=m
CONFIG_PCI_ATMEL=m
CONFIG_PCMCIA_ATMEL=m
CONFIG_AT76C50X_USB=m
CONFIG_AIRO_CS=m
CONFIG_PCMCIA_WL3501=m
CONFIG_PRISM54=m
CONFIG_USB_ZD1201=m
CONFIG_USB_NET_RNDIS_WLAN=m
CONFIG_RTL8180=m
CONFIG_RTL8187=m
CONFIG_RTL8187_LEDS=y
CONFIG_ADM8211=m
CONFIG_MAC80211_HWSIM=m
CONFIG_MWL8K=m
CONFIG_ATH_COMMON=m
# CONFIG_ATH_DEBUG is not set
CONFIG_ATH5K=m
# CONFIG_ATH5K_DEBUG is not set
CONFIG_ATH9K_HW=m
CONFIG_ATH9K_COMMON=m
CONFIG_ATH9K=m
# CONFIG_ATH9K_DEBUGFS is not set
# CONFIG_ATH9K_HTC is not set
CONFIG_AR9170_USB=m
CONFIG_AR9170_LEDS=y
CONFIG_B43=m
CONFIG_B43_PCI_AUTOSELECT=y
CONFIG_B43_PCICORE_AUTOSELECT=y
# CONFIG_B43_PCMCIA is not set
# CONFIG_B43_SDIO is not set
CONFIG_B43_PIO=y
CONFIG_B43_PHY_LP=y
CONFIG_B43_LEDS=y
CONFIG_B43_HWRNG=y
# CONFIG_B43_DEBUG is not set
CONFIG_B43LEGACY=m
CONFIG_B43LEGACY_PCI_AUTOSELECT=y
CONFIG_B43LEGACY_PCICORE_AUTOSELECT=y
CONFIG_B43LEGACY_LEDS=y
CONFIG_B43LEGACY_HWRNG=y
CONFIG_B43LEGACY_DEBUG=y
CONFIG_B43LEGACY_DMA=y
CONFIG_B43LEGACY_PIO=y
CONFIG_B43LEGACY_DMA_AND_PIO_MODE=y
# CONFIG_B43LEGACY_DMA_MODE is not set
# CONFIG_B43LEGACY_PIO_MODE is not set
CONFIG_HOSTAP=m
CONFIG_HOSTAP_FIRMWARE=y
CONFIG_HOSTAP_FIRMWARE_NVRAM=y
CONFIG_HOSTAP_PLX=m
CONFIG_HOSTAP_PCI=m
CONFIG_HOSTAP_CS=m
CONFIG_IPW2100=m
CONFIG_IPW2100_MONITOR=y
# CONFIG_IPW2100_DEBUG is not set
CONFIG_IPW2200=m
CONFIG_IPW2200_MONITOR=y
CONFIG_IPW2200_RADIOTAP=y
CONFIG_IPW2200_PROMISCUOUS=y
CONFIG_IPW2200_QOS=y
# CONFIG_IPW2200_DEBUG is not set
CONFIG_LIBIPW=m
CONFIG_LIBIPW_DEBUG=y
CONFIG_IWLWIFI=m
# CONFIG_IWLWIFI_DEBUG is not set
# CONFIG_IWLWIFI_DEVICE_TRACING is not set
CONFIG_IWLAGN=m
CONFIG_IWL4965=y
CONFIG_IWL5000=y
CONFIG_IWL3945=m
CONFIG_IWM=m
# CONFIG_IWM_DEBUG is not set
# CONFIG_IWM_TRACING is not set
CONFIG_LIBERTAS=m
CONFIG_LIBERTAS_USB=m
CONFIG_LIBERTAS_CS=m
CONFIG_LIBERTAS_SDIO=m
CONFIG_LIBERTAS_SPI=m
# CONFIG_LIBERTAS_DEBUG is not set
# CONFIG_LIBERTAS_MESH is not set
CONFIG_HERMES=m
# CONFIG_HERMES_PRISM is not set
CONFIG_HERMES_CACHE_FW_ON_INIT=y
CONFIG_PLX_HERMES=m
CONFIG_TMD_HERMES=m
CONFIG_NORTEL_HERMES=m
CONFIG_PCMCIA_HERMES=m
CONFIG_PCMCIA_SPECTRUM=m
# CONFIG_ORINOCO_USB is not set
CONFIG_P54_COMMON=m
CONFIG_P54_USB=m
CONFIG_P54_PCI=m
CONFIG_P54_SPI=m
CONFIG_P54_LEDS=y
CONFIG_RT2X00=m
CONFIG_RT2400PCI=m
CONFIG_RT2500PCI=m
CONFIG_RT61PCI=m
CONFIG_RT2800PCI_PCI=y
# CONFIG_RT2800PCI is not set
CONFIG_RT2500USB=m
CONFIG_RT73USB=m
CONFIG_RT2800USB=m
CONFIG_RT2800USB_RT30XX=y
# CONFIG_RT2800USB_RT35XX is not set
# CONFIG_RT2800USB_UNKNOWN is not set
CONFIG_RT2800_LIB=m
CONFIG_RT2X00_LIB_PCI=m
CONFIG_RT2X00_LIB_USB=m
CONFIG_RT2X00_LIB=m
CONFIG_RT2X00_LIB_HT=y
CONFIG_RT2X00_LIB_FIRMWARE=y
CONFIG_RT2X00_LIB_CRYPTO=y
CONFIG_RT2X00_LIB_LEDS=y
# CONFIG_RT2X00_LIB_DEBUGFS is not set
# CONFIG_RT2X00_DEBUG is not set
CONFIG_WL12XX=m
CONFIG_WL1251=m
CONFIG_WL1251_SPI=m
CONFIG_WL1251_SDIO=m
CONFIG_WL1271=m
# CONFIG_WL1271_SPI is not set
CONFIG_ZD1211RW=m
# CONFIG_ZD1211RW_DEBUG is not set

#
# WiMAX Wireless Broadband devices
#
CONFIG_WIMAX_I2400M=m
CONFIG_WIMAX_I2400M_USB=m
CONFIG_WIMAX_I2400M_SDIO=m
# CONFIG_WIMAX_IWMC3200_SDIO is not set
CONFIG_WIMAX_I2400M_DEBUG_LEVEL=8

#
# USB Network Adapters
#
CONFIG_USB_CATC=m
CONFIG_USB_KAWETH=m
CONFIG_USB_PEGASUS=m
CONFIG_USB_RTL8150=m
CONFIG_USB_USBNET=m
CONFIG_USB_NET_AX8817X=m
CONFIG_USB_NET_CDCETHER=m
CONFIG_USB_NET_CDC_EEM=m
CONFIG_USB_NET_DM9601=m
# CONFIG_USB_NET_SMSC75XX is not set
CONFIG_USB_NET_SMSC95XX=m
CONFIG_USB_NET_GL620A=m
CONFIG_USB_NET_NET1080=m
CONFIG_USB_NET_PLUSB=m
CONFIG_USB_NET_MCS7830=m
CONFIG_USB_NET_RNDIS_HOST=m
CONFIG_USB_NET_CDC_SUBSET=m
CONFIG_USB_ALI_M5632=y
CONFIG_USB_AN2720=y
CONFIG_USB_BELKIN=y
CONFIG_USB_ARMLINUX=y
CONFIG_USB_EPSON2888=y
CONFIG_USB_KC2190=y
CONFIG_USB_NET_ZAURUS=m
CONFIG_USB_HSO=m
CONFIG_USB_NET_INT51X1=m
CONFIG_USB_CDC_PHONET=m
# CONFIG_USB_IPHETH is not set
# CONFIG_USB_SIERRA_NET is not set
CONFIG_NET_PCMCIA=y
CONFIG_PCMCIA_3C589=m
CONFIG_PCMCIA_3C574=m
CONFIG_PCMCIA_FMVJ18X=m
CONFIG_PCMCIA_PCNET=m
CONFIG_PCMCIA_NMCLAN=m
CONFIG_PCMCIA_SMC91C92=m
CONFIG_PCMCIA_XIRC2PS=m
CONFIG_PCMCIA_AXNET=m
CONFIG_ARCNET_COM20020_CS=m
CONFIG_PCMCIA_IBMTR=m
CONFIG_WAN=y
CONFIG_HOSTESS_SV11=m
CONFIG_COSA=m
CONFIG_LANMEDIA=m
CONFIG_SEALEVEL_4021=m
CONFIG_HDLC=m
CONFIG_HDLC_RAW=m
CONFIG_HDLC_RAW_ETH=m
CONFIG_HDLC_CISCO=m
CONFIG_HDLC_FR=m
CONFIG_HDLC_PPP=m
CONFIG_HDLC_X25=m
CONFIG_PCI200SYN=m
CONFIG_WANXL=m
# CONFIG_PC300TOO is not set
CONFIG_N2=m
CONFIG_C101=m
CONFIG_FARSYNC=m
CONFIG_DSCC4=m
CONFIG_DSCC4_PCISYNC=y
CONFIG_DSCC4_PCI_RST=y
CONFIG_DLCI=m
CONFIG_DLCI_MAX=8
CONFIG_SDLA=m
CONFIG_WAN_ROUTER_DRIVERS=m
CONFIG_CYCLADES_SYNC=m
CONFIG_CYCLOMX_X25=y
CONFIG_LAPBETHER=m
CONFIG_X25_ASY=m
CONFIG_SBNI=m
# CONFIG_SBNI_MULTILINE is not set
CONFIG_ATM_DRIVERS=y
# CONFIG_ATM_DUMMY is not set
CONFIG_ATM_TCP=m
CONFIG_ATM_LANAI=m
CONFIG_ATM_ENI=m
# CONFIG_ATM_ENI_DEBUG is not set
# CONFIG_ATM_ENI_TUNE_BURST is not set
CONFIG_ATM_FIRESTREAM=m
CONFIG_ATM_ZATM=m
# CONFIG_ATM_ZATM_DEBUG is not set
CONFIG_ATM_NICSTAR=m
# CONFIG_ATM_NICSTAR_USE_SUNI is not set
# CONFIG_ATM_NICSTAR_USE_IDT77105 is not set
CONFIG_ATM_IDT77252=m
# CONFIG_ATM_IDT77252_DEBUG is not set
# CONFIG_ATM_IDT77252_RCV_ALL is not set
CONFIG_ATM_IDT77252_USE_SUNI=y
CONFIG_ATM_AMBASSADOR=m
# CONFIG_ATM_AMBASSADOR_DEBUG is not set
CONFIG_ATM_HORIZON=m
# CONFIG_ATM_HORIZON_DEBUG is not set
CONFIG_ATM_IA=m
# CONFIG_ATM_IA_DEBUG is not set
CONFIG_ATM_FORE200E=m
# CONFIG_ATM_FORE200E_USE_TASKLET is not set
CONFIG_ATM_FORE200E_TX_RETRY=16
CONFIG_ATM_FORE200E_DEBUG=0
CONFIG_ATM_HE=m
CONFIG_ATM_HE_USE_SUNI=y
CONFIG_ATM_SOLOS=m
CONFIG_IEEE802154_DRIVERS=m
# CONFIG_IEEE802154_FAKEHARD is not set
CONFIG_FDDI=y
CONFIG_DEFXX=m
# CONFIG_DEFXX_MMIO is not set
CONFIG_SKFP=m
CONFIG_HIPPI=y
CONFIG_ROADRUNNER=m
# CONFIG_ROADRUNNER_LARGE_RINGS is not set
CONFIG_PLIP=m
CONFIG_PPP=y
CONFIG_PPP_MULTILINK=y
CONFIG_PPP_FILTER=y
CONFIG_PPP_ASYNC=m
CONFIG_PPP_SYNC_TTY=m
CONFIG_PPP_DEFLATE=m
CONFIG_PPP_BSDCOMP=m
CONFIG_PPP_MPPE=m
CONFIG_PPPOE=m
CONFIG_PPPOATM=m
CONFIG_SLIP=m
CONFIG_SLIP_COMPRESSED=y
CONFIG_SLHC=y
CONFIG_SLIP_SMART=y
CONFIG_SLIP_MODE_SLIP6=y
CONFIG_NET_FC=y
CONFIG_NETCONSOLE=m
CONFIG_NETCONSOLE_DYNAMIC=y
CONFIG_NETPOLL=y
# CONFIG_NETPOLL_TRAP is not set
CONFIG_NET_POLL_CONTROLLER=y
CONFIG_VIRTIO_NET=m
CONFIG_VMXNET3=m
CONFIG_ISDN=y
CONFIG_ISDN_I4L=m
CONFIG_ISDN_PPP=y
CONFIG_ISDN_PPP_VJ=y
CONFIG_ISDN_MPP=y
CONFIG_IPPP_FILTER=y
CONFIG_ISDN_PPP_BSDCOMP=m
CONFIG_ISDN_AUDIO=y
CONFIG_ISDN_TTY_FAX=y
CONFIG_ISDN_X25=y

#
# ISDN feature submodules
#
CONFIG_ISDN_DIVERSION=m

#
# ISDN4Linux hardware drivers
#

#
# Passive cards
#
CONFIG_ISDN_DRV_HISAX=m

#
# D-channel protocol features
#
CONFIG_HISAX_EURO=y
CONFIG_DE_AOC=y
# CONFIG_HISAX_NO_SENDCOMPLETE is not set
# CONFIG_HISAX_NO_LLC is not set
# CONFIG_HISAX_NO_KEYPAD is not set
CONFIG_HISAX_1TR6=y
CONFIG_HISAX_NI1=y
CONFIG_HISAX_MAX_CARDS=8

#
# HiSax supported cards
#
CONFIG_HISAX_16_0=y
CONFIG_HISAX_16_3=y
CONFIG_HISAX_TELESPCI=y
CONFIG_HISAX_S0BOX=y
CONFIG_HISAX_AVM_A1=y
CONFIG_HISAX_FRITZPCI=y
CONFIG_HISAX_AVM_A1_PCMCIA=y
CONFIG_HISAX_ELSA=y
CONFIG_HISAX_IX1MICROR2=y
CONFIG_HISAX_DIEHLDIVA=y
CONFIG_HISAX_ASUSCOM=y
CONFIG_HISAX_TELEINT=y
CONFIG_HISAX_HFCS=y
CONFIG_HISAX_SEDLBAUER=y
CONFIG_HISAX_SPORTSTER=y
CONFIG_HISAX_MIC=y
CONFIG_HISAX_NETJET=y
CONFIG_HISAX_NETJET_U=y
CONFIG_HISAX_NICCY=y
CONFIG_HISAX_ISURF=y
CONFIG_HISAX_HSTSAPHIR=y
CONFIG_HISAX_BKM_A4T=y
CONFIG_HISAX_SCT_QUADRO=y
CONFIG_HISAX_GAZEL=y
CONFIG_HISAX_HFC_PCI=y
CONFIG_HISAX_W6692=y
CONFIG_HISAX_HFC_SX=y
CONFIG_HISAX_ENTERNOW_PCI=y
# CONFIG_HISAX_DEBUG is not set

#
# HiSax PCMCIA card service modules
#
CONFIG_HISAX_SEDLBAUER_CS=m
CONFIG_HISAX_ELSA_CS=m
CONFIG_HISAX_AVM_A1_CS=m
CONFIG_HISAX_TELES_CS=m

#
# HiSax sub driver modules
#
CONFIG_HISAX_ST5481=m
CONFIG_HISAX_HFCUSB=m
CONFIG_HISAX_HFC4S8S=m
CONFIG_HISAX_FRITZ_PCIPNP=m

#
# Active cards
#
CONFIG_ISDN_DRV_ICN=m
CONFIG_ISDN_DRV_PCBIT=m
CONFIG_ISDN_DRV_SC=m
CONFIG_ISDN_DRV_ACT2000=m
CONFIG_ISDN_CAPI=m
CONFIG_ISDN_DRV_AVMB1_VERBOSE_REASON=y
CONFIG_CAPI_TRACE=y
CONFIG_ISDN_CAPI_MIDDLEWARE=y
CONFIG_ISDN_CAPI_CAPI20=m
CONFIG_ISDN_CAPI_CAPIFS_BOOL=y
CONFIG_ISDN_CAPI_CAPIFS=m
CONFIG_ISDN_CAPI_CAPIDRV=m

#
# CAPI hardware drivers
#
CONFIG_CAPI_AVM=y
CONFIG_ISDN_DRV_AVMB1_B1ISA=m
CONFIG_ISDN_DRV_AVMB1_B1PCI=m
CONFIG_ISDN_DRV_AVMB1_B1PCIV4=y
CONFIG_ISDN_DRV_AVMB1_T1ISA=m
CONFIG_ISDN_DRV_AVMB1_B1PCMCIA=m
CONFIG_ISDN_DRV_AVMB1_AVM_CS=m
CONFIG_ISDN_DRV_AVMB1_T1PCI=m
CONFIG_ISDN_DRV_AVMB1_C4=m
CONFIG_CAPI_EICON=y
CONFIG_ISDN_DIVAS=m
CONFIG_ISDN_DIVAS_BRIPCI=y
CONFIG_ISDN_DIVAS_PRIPCI=y
CONFIG_ISDN_DIVAS_DIVACAPI=m
CONFIG_ISDN_DIVAS_USERIDI=m
CONFIG_ISDN_DIVAS_MAINT=m
CONFIG_ISDN_DRV_GIGASET=m
# CONFIG_GIGASET_CAPI is not set
CONFIG_GIGASET_I4L=y
# CONFIG_GIGASET_DUMMYLL is not set
CONFIG_GIGASET_BASE=m
CONFIG_GIGASET_M105=m
CONFIG_GIGASET_M101=m
# CONFIG_GIGASET_DEBUG is not set
CONFIG_HYSDN=m
CONFIG_HYSDN_CAPI=y
CONFIG_MISDN=m
CONFIG_MISDN_DSP=m
CONFIG_MISDN_L1OIP=m

#
# mISDN hardware drivers
#
CONFIG_MISDN_HFCPCI=m
CONFIG_MISDN_HFCMULTI=m
CONFIG_MISDN_HFCUSB=m
CONFIG_MISDN_AVMFRITZ=m
CONFIG_MISDN_SPEEDFAX=m
CONFIG_MISDN_INFINEON=m
CONFIG_MISDN_W6692=m
CONFIG_MISDN_NETJET=m
CONFIG_MISDN_IPAC=m
CONFIG_MISDN_ISAR=m
CONFIG_ISDN_HDLC=m
CONFIG_PHONE=m
CONFIG_PHONE_IXJ=m
CONFIG_PHONE_IXJ_PCMCIA=m

#
# Input device support
#
CONFIG_INPUT=y
CONFIG_INPUT_FF_MEMLESS=m
CONFIG_INPUT_POLLDEV=m
CONFIG_INPUT_SPARSEKMAP=m

#
# Userland interfaces
#
CONFIG_INPUT_MOUSEDEV=y
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
CONFIG_INPUT_JOYDEV=m
CONFIG_INPUT_EVDEV=y
CONFIG_INPUT_EVBUG=m

#
# Input Device Drivers
#
CONFIG_INPUT_KEYBOARD=y
CONFIG_KEYBOARD_ADP5588=m
CONFIG_KEYBOARD_ATKBD=y
# CONFIG_KEYBOARD_QT2160 is not set
CONFIG_KEYBOARD_LKKBD=m
CONFIG_KEYBOARD_GPIO=m
# CONFIG_KEYBOARD_TCA6416 is not set
CONFIG_KEYBOARD_MATRIX=m
CONFIG_KEYBOARD_LM8323=m
CONFIG_KEYBOARD_MAX7359=m
CONFIG_KEYBOARD_NEWTON=m
CONFIG_KEYBOARD_OPENCORES=m
CONFIG_KEYBOARD_STOWAWAY=m
CONFIG_KEYBOARD_SUNKBD=m
CONFIG_KEYBOARD_TWL4030=m
CONFIG_KEYBOARD_XTKBD=m
CONFIG_INPUT_MOUSE=y
CONFIG_MOUSE_PS2=m
CONFIG_MOUSE_PS2_ALPS=y
CONFIG_MOUSE_PS2_LOGIPS2PP=y
CONFIG_MOUSE_PS2_SYNAPTICS=y
CONFIG_MOUSE_PS2_LIFEBOOK=y
CONFIG_MOUSE_PS2_TRACKPOINT=y
CONFIG_MOUSE_PS2_ELANTECH=y
CONFIG_MOUSE_PS2_SENTELIC=y
# CONFIG_MOUSE_PS2_TOUCHKIT is not set
CONFIG_MOUSE_PS2_OLPC=y
CONFIG_MOUSE_SERIAL=m
CONFIG_MOUSE_APPLETOUCH=m
CONFIG_MOUSE_BCM5974=m
CONFIG_MOUSE_INPORT=m
# CONFIG_MOUSE_ATIXL is not set
CONFIG_MOUSE_LOGIBM=m
CONFIG_MOUSE_PC110PAD=m
CONFIG_MOUSE_VSXXXAA=m
CONFIG_MOUSE_GPIO=m
CONFIG_MOUSE_SYNAPTICS_I2C=m
CONFIG_INPUT_JOYSTICK=y
CONFIG_JOYSTICK_ANALOG=m
CONFIG_JOYSTICK_A3D=m
CONFIG_JOYSTICK_ADI=m
CONFIG_JOYSTICK_COBRA=m
CONFIG_JOYSTICK_GF2K=m
CONFIG_JOYSTICK_GRIP=m
CONFIG_JOYSTICK_GRIP_MP=m
CONFIG_JOYSTICK_GUILLEMOT=m
CONFIG_JOYSTICK_INTERACT=m
CONFIG_JOYSTICK_SIDEWINDER=m
CONFIG_JOYSTICK_TMDC=m
CONFIG_JOYSTICK_IFORCE=m
CONFIG_JOYSTICK_IFORCE_USB=y
CONFIG_JOYSTICK_IFORCE_232=y
CONFIG_JOYSTICK_WARRIOR=m
CONFIG_JOYSTICK_MAGELLAN=m
CONFIG_JOYSTICK_SPACEORB=m
CONFIG_JOYSTICK_SPACEBALL=m
CONFIG_JOYSTICK_STINGER=m
CONFIG_JOYSTICK_TWIDJOY=m
CONFIG_JOYSTICK_ZHENHUA=m
CONFIG_JOYSTICK_DB9=m
CONFIG_JOYSTICK_GAMECON=m
CONFIG_JOYSTICK_TURBOGRAFX=m
CONFIG_JOYSTICK_JOYDUMP=m
CONFIG_JOYSTICK_XPAD=m
CONFIG_JOYSTICK_XPAD_FF=y
CONFIG_JOYSTICK_XPAD_LEDS=y
CONFIG_JOYSTICK_WALKERA0701=m
CONFIG_INPUT_TABLET=y
CONFIG_TABLET_USB_ACECAD=m
CONFIG_TABLET_USB_AIPTEK=m
CONFIG_TABLET_USB_GTCO=m
CONFIG_TABLET_USB_KBTAB=m
CONFIG_TABLET_USB_WACOM=m
CONFIG_INPUT_TOUCHSCREEN=y
CONFIG_TOUCHSCREEN_ADS7846=m
CONFIG_TOUCHSCREEN_AD7877=m
CONFIG_TOUCHSCREEN_AD7879_I2C=m
CONFIG_TOUCHSCREEN_AD7879=m
CONFIG_TOUCHSCREEN_DA9034=m
# CONFIG_TOUCHSCREEN_DYNAPRO is not set
# CONFIG_TOUCHSCREEN_HAMPSHIRE is not set
CONFIG_TOUCHSCREEN_EETI=m
CONFIG_TOUCHSCREEN_FUJITSU=m
CONFIG_TOUCHSCREEN_GUNZE=m
CONFIG_TOUCHSCREEN_ELO=m
CONFIG_TOUCHSCREEN_WACOM_W8001=m
CONFIG_TOUCHSCREEN_MCS5000=m
CONFIG_TOUCHSCREEN_MTOUCH=m
CONFIG_TOUCHSCREEN_INEXIO=m
CONFIG_TOUCHSCREEN_MK712=m
CONFIG_TOUCHSCREEN_HTCPEN=m
CONFIG_TOUCHSCREEN_PENMOUNT=m
CONFIG_TOUCHSCREEN_TOUCHRIGHT=m
CONFIG_TOUCHSCREEN_TOUCHWIN=m
CONFIG_TOUCHSCREEN_UCB1400=m
CONFIG_TOUCHSCREEN_WM97XX=m
CONFIG_TOUCHSCREEN_WM9705=y
CONFIG_TOUCHSCREEN_WM9712=y
CONFIG_TOUCHSCREEN_WM9713=y
CONFIG_TOUCHSCREEN_USB_COMPOSITE=m
# CONFIG_TOUCHSCREEN_MC13783 is not set
CONFIG_TOUCHSCREEN_USB_EGALAX=y
CONFIG_TOUCHSCREEN_USB_PANJIT=y
CONFIG_TOUCHSCREEN_USB_3M=y
CONFIG_TOUCHSCREEN_USB_ITM=y
CONFIG_TOUCHSCREEN_USB_ETURBO=y
CONFIG_TOUCHSCREEN_USB_GUNZE=y
CONFIG_TOUCHSCREEN_USB_DMC_TSC10=y
CONFIG_TOUCHSCREEN_USB_IRTOUCH=y
CONFIG_TOUCHSCREEN_USB_IDEALTEK=y
CONFIG_TOUCHSCREEN_USB_GENERAL_TOUCH=y
CONFIG_TOUCHSCREEN_USB_GOTOP=y
CONFIG_TOUCHSCREEN_USB_JASTEC=y
CONFIG_TOUCHSCREEN_USB_E2I=y
CONFIG_TOUCHSCREEN_USB_ZYTRONIC=y
CONFIG_TOUCHSCREEN_USB_ETT_TC5UH=y
CONFIG_TOUCHSCREEN_USB_NEXIO=y
CONFIG_TOUCHSCREEN_TOUCHIT213=m
CONFIG_TOUCHSCREEN_TSC2007=m
# CONFIG_TOUCHSCREEN_TPS6507X is not set
CONFIG_INPUT_MISC=y
# CONFIG_INPUT_AD714X is not set
CONFIG_INPUT_PCSPKR=m
# CONFIG_INPUT_APANEL is not set
CONFIG_INPUT_WISTRON_BTNS=m
CONFIG_INPUT_ATLAS_BTNS=m
CONFIG_INPUT_ATI_REMOTE=m
CONFIG_INPUT_ATI_REMOTE2=m
CONFIG_INPUT_KEYSPAN_REMOTE=m
CONFIG_INPUT_POWERMATE=m
CONFIG_INPUT_YEALINK=m
CONFIG_INPUT_CM109=m
CONFIG_INPUT_TWL4030_PWRBUTTON=m
# CONFIG_INPUT_TWL4030_VIBRA is not set
CONFIG_INPUT_UINPUT=m
CONFIG_INPUT_WINBOND_CIR=m
CONFIG_INPUT_PCF50633_PMU=m
# CONFIG_INPUT_PCF8574 is not set
CONFIG_INPUT_GPIO_ROTARY_ENCODER=m

#
# Hardware I/O ports
#
CONFIG_SERIO=y
CONFIG_SERIO_I8042=y
CONFIG_SERIO_SERPORT=m
CONFIG_SERIO_CT82C710=m
CONFIG_SERIO_PARKBD=m
CONFIG_SERIO_PCIPS2=m
CONFIG_SERIO_LIBPS2=y
CONFIG_SERIO_RAW=m
# CONFIG_SERIO_ALTERA_PS2 is not set
CONFIG_GAMEPORT=m
CONFIG_GAMEPORT_NS558=m
CONFIG_GAMEPORT_L4=m
CONFIG_GAMEPORT_EMU10K1=m
CONFIG_GAMEPORT_FM801=m

#
# Character devices
#
CONFIG_VT=y
CONFIG_CONSOLE_TRANSLATIONS=y
CONFIG_VT_CONSOLE=y
CONFIG_HW_CONSOLE=y
CONFIG_VT_HW_CONSOLE_BINDING=y
# CONFIG_DEVKMEM is not set
CONFIG_SERIAL_NONSTANDARD=y
CONFIG_COMPUTONE=m
CONFIG_ROCKETPORT=m
CONFIG_CYCLADES=m
# CONFIG_CYZ_INTR is not set
CONFIG_DIGIEPCA=m
CONFIG_MOXA_INTELLIO=m
CONFIG_MOXA_SMARTIO=m
# CONFIG_ISI is not set
CONFIG_SYNCLINK=m
CONFIG_SYNCLINKMP=m
CONFIG_SYNCLINK_GT=m
CONFIG_N_HDLC=m
# CONFIG_N_GSM is not set
CONFIG_RISCOM8=m
CONFIG_SPECIALIX=m
CONFIG_STALDRV=y
CONFIG_STALLION=m
CONFIG_ISTALLION=m
CONFIG_NOZOMI=m

#
# Serial drivers
#
CONFIG_SERIAL_8250=y
CONFIG_SERIAL_8250_CONSOLE=y
CONFIG_FIX_EARLYCON_MEM=y
CONFIG_SERIAL_8250_PCI=y
CONFIG_SERIAL_8250_PNP=y
CONFIG_SERIAL_8250_CS=m
CONFIG_SERIAL_8250_NR_UARTS=48
CONFIG_SERIAL_8250_RUNTIME_UARTS=4
CONFIG_SERIAL_8250_EXTENDED=y
CONFIG_SERIAL_8250_MANY_PORTS=y
CONFIG_SERIAL_8250_FOURPORT=m
CONFIG_SERIAL_8250_ACCENT=m
CONFIG_SERIAL_8250_BOCA=m
CONFIG_SERIAL_8250_EXAR_ST16C554=m
CONFIG_SERIAL_8250_HUB6=m
CONFIG_SERIAL_8250_SHARE_IRQ=y
# CONFIG_SERIAL_8250_DETECT_IRQ is not set
CONFIG_SERIAL_8250_RSA=y
CONFIG_SERIAL_8250_MCA=m

#
# Non-8250 serial port support
#
CONFIG_SERIAL_MAX3100=m
CONFIG_SERIAL_CORE=y
CONFIG_SERIAL_CORE_CONSOLE=y
CONFIG_CONSOLE_POLL=y
CONFIG_SERIAL_JSM=m
# CONFIG_SERIAL_TIMBERDALE is not set
# CONFIG_SERIAL_ALTERA_JTAGUART is not set
# CONFIG_SERIAL_ALTERA_UART is not set
CONFIG_UNIX98_PTYS=y
CONFIG_DEVPTS_MULTIPLE_INSTANCES=y
CONFIG_LEGACY_PTYS=y
CONFIG_LEGACY_PTY_COUNT=0
CONFIG_PRINTER=m
# CONFIG_LP_CONSOLE is not set
CONFIG_PPDEV=m
CONFIG_HVC_DRIVER=y
CONFIG_VIRTIO_CONSOLE=m
CONFIG_IPMI_HANDLER=m
# CONFIG_IPMI_PANIC_EVENT is not set
CONFIG_IPMI_DEVICE_INTERFACE=m
CONFIG_IPMI_SI=m
CONFIG_IPMI_WATCHDOG=m
CONFIG_IPMI_POWEROFF=m
CONFIG_HW_RANDOM=y
CONFIG_HW_RANDOM_TIMERIOMEM=m
CONFIG_HW_RANDOM_INTEL=m
CONFIG_HW_RANDOM_AMD=m
CONFIG_HW_RANDOM_GEODE=m
CONFIG_HW_RANDOM_VIA=m
CONFIG_HW_RANDOM_VIRTIO=m
CONFIG_NVRAM=m
CONFIG_DTLK=m
CONFIG_R3964=m
CONFIG_APPLICOM=m
CONFIG_SONYPI=m

#
# PCMCIA character devices
#
CONFIG_SYNCLINK_CS=m
CONFIG_CARDMAN_4000=m
CONFIG_CARDMAN_4040=m
CONFIG_IPWIRELESS=m
CONFIG_MWAVE=m
CONFIG_SCx200_GPIO=m
CONFIG_PC8736x_GPIO=m
CONFIG_NSC_GPIO=m
CONFIG_CS5535_GPIO=m
CONFIG_RAW_DRIVER=m
CONFIG_MAX_RAW_DEVS=256
CONFIG_HPET=y
CONFIG_HPET_MMAP=y
CONFIG_HANGCHECK_TIMER=m
CONFIG_TCG_TPM=m
CONFIG_TCG_TIS=m
CONFIG_TCG_NSC=m
CONFIG_TCG_ATMEL=m
CONFIG_TCG_INFINEON=m
CONFIG_TELCLOCK=m
CONFIG_DEVPORT=y
# CONFIG_RAMOOPS is not set
CONFIG_I2C=y
CONFIG_I2C_BOARDINFO=y
CONFIG_I2C_COMPAT=y
CONFIG_I2C_CHARDEV=m
# CONFIG_I2C_HELPER_AUTO is not set
CONFIG_I2C_SMBUS=m

#
# I2C Algorithms
#
CONFIG_I2C_ALGOBIT=m
CONFIG_I2C_ALGOPCF=m
CONFIG_I2C_ALGOPCA=m

#
# I2C Hardware Bus support
#

#
# PC SMBus host controller drivers
#
CONFIG_I2C_ALI1535=m
CONFIG_I2C_ALI1563=m
CONFIG_I2C_ALI15X3=m
CONFIG_I2C_AMD756=m
CONFIG_I2C_AMD756_S4882=m
CONFIG_I2C_AMD8111=m
CONFIG_I2C_I801=m
CONFIG_I2C_ISCH=m
CONFIG_I2C_PIIX4=m
CONFIG_I2C_NFORCE2=m
CONFIG_I2C_NFORCE2_S4985=m
CONFIG_I2C_SIS5595=m
CONFIG_I2C_SIS630=m
CONFIG_I2C_SIS96X=m
CONFIG_I2C_VIA=m
CONFIG_I2C_VIAPRO=m

#
# ACPI drivers
#
CONFIG_I2C_SCMI=m

#
# I2C system bus drivers (mostly embedded / system-on-chip)
#
CONFIG_I2C_GPIO=m
CONFIG_I2C_OCORES=m
CONFIG_I2C_PCA_PLATFORM=m
CONFIG_I2C_SIMTEC=m
# CONFIG_I2C_XILINX is not set

#
# External I2C/SMBus adapter drivers
#
CONFIG_I2C_PARPORT=m
CONFIG_I2C_PARPORT_LIGHT=m
CONFIG_I2C_TAOS_EVM=m
CONFIG_I2C_TINY_USB=m

#
# Other I2C/SMBus bus drivers
#
CONFIG_I2C_PCA_ISA=m
CONFIG_I2C_STUB=m
CONFIG_SCx200_I2C=m
CONFIG_SCx200_I2C_SCL=12
CONFIG_SCx200_I2C_SDA=13
CONFIG_SCx200_ACB=m
# CONFIG_I2C_DEBUG_CORE is not set
# CONFIG_I2C_DEBUG_ALGO is not set
# CONFIG_I2C_DEBUG_BUS is not set
CONFIG_SPI=y
# CONFIG_SPI_DEBUG is not set
CONFIG_SPI_MASTER=y

#
# SPI Master Controller Drivers
#
CONFIG_SPI_BITBANG=m
CONFIG_SPI_BUTTERFLY=m
CONFIG_SPI_GPIO=m
CONFIG_SPI_LM70_LLP=m
# CONFIG_SPI_XILINX is not set
# CONFIG_SPI_DESIGNWARE is not set

#
# SPI Protocol Masters
#
CONFIG_SPI_SPIDEV=m
CONFIG_SPI_TLE62X0=m

#
# PPS support
#
CONFIG_PPS=m
# CONFIG_PPS_DEBUG is not set

#
# PPS clients support
#
# CONFIG_PPS_CLIENT_KTIMER is not set
# CONFIG_PPS_CLIENT_LDISC is not set
CONFIG_ARCH_WANT_OPTIONAL_GPIOLIB=y
CONFIG_GPIOLIB=y
# CONFIG_DEBUG_GPIO is not set
CONFIG_GPIO_SYSFS=y
CONFIG_GPIO_MAX730X=m

#
# Memory mapped GPIO expanders:
#
# CONFIG_GPIO_IT8761E is not set
# CONFIG_GPIO_SCH is not set

#
# I2C GPIO expanders:
#
# CONFIG_GPIO_MAX7300 is not set
CONFIG_GPIO_MAX732X=m
CONFIG_GPIO_PCA953X=m
CONFIG_GPIO_PCF857X=m
CONFIG_GPIO_TWL4030=m
# CONFIG_GPIO_ADP5588 is not set

#
# PCI GPIO expanders:
#
# CONFIG_GPIO_CS5535 is not set
CONFIG_GPIO_LANGWELL=y
# CONFIG_GPIO_RDC321X is not set

#
# SPI GPIO expanders:
#
CONFIG_GPIO_MAX7301=m
CONFIG_GPIO_MCP23S08=m
CONFIG_GPIO_MC33880=m

#
# AC97 GPIO expanders:
#
CONFIG_GPIO_UCB1400=y

#
# MODULbus GPIO expanders:
#
CONFIG_W1=m
CONFIG_W1_CON=y

#
# 1-wire Bus Masters
#
CONFIG_W1_MASTER_MATROX=m
CONFIG_W1_MASTER_DS2490=m
CONFIG_W1_MASTER_DS2482=m
CONFIG_W1_MASTER_GPIO=m

#
# 1-wire Slaves
#
CONFIG_W1_SLAVE_THERM=m
CONFIG_W1_SLAVE_SMEM=m
CONFIG_W1_SLAVE_DS2431=m
CONFIG_W1_SLAVE_DS2433=m
# CONFIG_W1_SLAVE_DS2433_CRC is not set
CONFIG_W1_SLAVE_DS2760=m
CONFIG_W1_SLAVE_BQ27000=m
CONFIG_POWER_SUPPLY=y
# CONFIG_POWER_SUPPLY_DEBUG is not set
CONFIG_PDA_POWER=m
# CONFIG_TEST_POWER is not set
CONFIG_BATTERY_DS2760=m
CONFIG_BATTERY_DS2782=m
CONFIG_BATTERY_OLPC=m
CONFIG_BATTERY_BQ27x00=m
CONFIG_BATTERY_DA9030=m
CONFIG_BATTERY_MAX17040=m
CONFIG_CHARGER_PCF50633=m
CONFIG_HWMON=y
CONFIG_HWMON_VID=m
# CONFIG_HWMON_DEBUG_CHIP is not set

#
# Native drivers
#
CONFIG_SENSORS_ABITUGURU=m
CONFIG_SENSORS_ABITUGURU3=m
CONFIG_SENSORS_AD7414=m
CONFIG_SENSORS_AD7418=m
CONFIG_SENSORS_ADCXX=m
CONFIG_SENSORS_ADM1021=m
CONFIG_SENSORS_ADM1025=m
CONFIG_SENSORS_ADM1026=m
CONFIG_SENSORS_ADM1029=m
CONFIG_SENSORS_ADM1031=m
CONFIG_SENSORS_ADM9240=m
# CONFIG_SENSORS_ADT7411 is not set
CONFIG_SENSORS_ADT7462=m
CONFIG_SENSORS_ADT7470=m
CONFIG_SENSORS_ADT7475=m
# CONFIG_SENSORS_ASC7621 is not set
CONFIG_SENSORS_K8TEMP=m
# CONFIG_SENSORS_K10TEMP is not set
CONFIG_SENSORS_ASB100=m
CONFIG_SENSORS_ATXP1=m
CONFIG_SENSORS_DS1621=m
CONFIG_SENSORS_I5K_AMB=m
CONFIG_SENSORS_F71805F=m
CONFIG_SENSORS_F71882FG=m
CONFIG_SENSORS_F75375S=m
CONFIG_SENSORS_FSCHMD=m
CONFIG_SENSORS_G760A=m
CONFIG_SENSORS_GL518SM=m
CONFIG_SENSORS_GL520SM=m
CONFIG_SENSORS_CORETEMP=m
CONFIG_SENSORS_IBMAEM=m
CONFIG_SENSORS_IBMPEX=m
CONFIG_SENSORS_IT87=m
CONFIG_SENSORS_LM63=m
CONFIG_SENSORS_LM70=m
# CONFIG_SENSORS_LM73 is not set
CONFIG_SENSORS_LM75=m
CONFIG_SENSORS_LM77=m
CONFIG_SENSORS_LM78=m
CONFIG_SENSORS_LM80=m
CONFIG_SENSORS_LM83=m
CONFIG_SENSORS_LM85=m
CONFIG_SENSORS_LM87=m
CONFIG_SENSORS_LM90=m
CONFIG_SENSORS_LM92=m
CONFIG_SENSORS_LM93=m
CONFIG_SENSORS_LTC4215=m
CONFIG_SENSORS_LTC4245=m
CONFIG_SENSORS_LM95241=m
CONFIG_SENSORS_MAX1111=m
CONFIG_SENSORS_MAX1619=m
CONFIG_SENSORS_MAX6650=m
CONFIG_SENSORS_PC87360=m
CONFIG_SENSORS_PC87427=m
CONFIG_SENSORS_PCF8591=m
CONFIG_SENSORS_SHT15=m
CONFIG_SENSORS_SIS5595=m
CONFIG_SENSORS_DME1737=m
# CONFIG_SENSORS_EMC1403 is not set
CONFIG_SENSORS_SMSC47M1=m
CONFIG_SENSORS_SMSC47M192=m
CONFIG_SENSORS_SMSC47B397=m
CONFIG_SENSORS_ADS7828=m
# CONFIG_SENSORS_ADS7871 is not set
# CONFIG_SENSORS_AMC6821 is not set
CONFIG_SENSORS_THMC50=m
# CONFIG_SENSORS_TMP102 is not set
CONFIG_SENSORS_TMP401=m
CONFIG_SENSORS_TMP421=m
# CONFIG_SENSORS_VIA_CPUTEMP is not set
CONFIG_SENSORS_VIA686A=m
CONFIG_SENSORS_VT1211=m
CONFIG_SENSORS_VT8231=m
CONFIG_SENSORS_W83781D=m
CONFIG_SENSORS_W83791D=m
CONFIG_SENSORS_W83792D=m
CONFIG_SENSORS_W83793=m
CONFIG_SENSORS_W83L785TS=m
CONFIG_SENSORS_W83L786NG=m
CONFIG_SENSORS_W83627HF=m
CONFIG_SENSORS_W83627EHF=m
CONFIG_SENSORS_HDAPS=m
# CONFIG_SENSORS_LIS3_I2C is not set
CONFIG_SENSORS_APPLESMC=m
# CONFIG_SENSORS_MC13783_ADC is not set

#
# ACPI drivers
#
CONFIG_SENSORS_ATK0110=m
CONFIG_SENSORS_LIS3LV02D=m
CONFIG_THERMAL=y
CONFIG_THERMAL_HWMON=y
CONFIG_WATCHDOG=y
# CONFIG_WATCHDOG_NOWAYOUT is not set

#
# Watchdog Device Drivers
#
CONFIG_SOFT_WATCHDOG=m
CONFIG_TWL4030_WATCHDOG=m
CONFIG_ACQUIRE_WDT=m
CONFIG_ADVANTECH_WDT=m
CONFIG_ALIM1535_WDT=m
CONFIG_ALIM7101_WDT=m
CONFIG_SC520_WDT=m
CONFIG_SBC_FITPC2_WATCHDOG=m
CONFIG_EUROTECH_WDT=m
CONFIG_IB700_WDT=m
CONFIG_IBMASR=m
CONFIG_WAFER_WDT=m
CONFIG_I6300ESB_WDT=m
CONFIG_ITCO_WDT=m
CONFIG_ITCO_VENDOR_SUPPORT=y
CONFIG_IT8712F_WDT=m
CONFIG_IT87_WDT=m
# CONFIG_HP_WATCHDOG is not set
CONFIG_SC1200_WDT=m
CONFIG_SCx200_WDT=m
CONFIG_PC87413_WDT=m
CONFIG_60XX_WDT=m
CONFIG_SBC8360_WDT=m
CONFIG_SBC7240_WDT=m
CONFIG_CPU5_WDT=m
CONFIG_SMSC_SCH311X_WDT=m
CONFIG_SMSC37B787_WDT=m
CONFIG_W83627HF_WDT=m
CONFIG_W83697HF_WDT=m
CONFIG_W83697UG_WDT=m
CONFIG_W83877F_WDT=m
CONFIG_W83977F_WDT=m
CONFIG_MACHZ_WDT=m
CONFIG_SBC_EPX_C3_WATCHDOG=m

#
# ISA-based Watchdog Cards
#
CONFIG_PCWATCHDOG=m
CONFIG_MIXCOMWD=m
CONFIG_WDT=m

#
# PCI-based Watchdog Cards
#
CONFIG_PCIPCWATCHDOG=m
CONFIG_WDTPCI=m

#
# USB-based Watchdog Cards
#
CONFIG_USBPCWATCHDOG=m
CONFIG_SSB_POSSIBLE=y

#
# Sonics Silicon Backplane
#
CONFIG_SSB=m
CONFIG_SSB_SPROM=y
CONFIG_SSB_BLOCKIO=y
CONFIG_SSB_PCIHOST_POSSIBLE=y
CONFIG_SSB_PCIHOST=y
CONFIG_SSB_B43_PCI_BRIDGE=y
CONFIG_SSB_PCMCIAHOST_POSSIBLE=y
# CONFIG_SSB_PCMCIAHOST is not set
CONFIG_SSB_SDIOHOST_POSSIBLE=y
CONFIG_SSB_SDIOHOST=y
# CONFIG_SSB_DEBUG is not set
CONFIG_SSB_DRIVER_PCICORE_POSSIBLE=y
CONFIG_SSB_DRIVER_PCICORE=y
CONFIG_MFD_SUPPORT=y
CONFIG_MFD_CORE=y
# CONFIG_MFD_88PM860X is not set
CONFIG_MFD_SM501=m
# CONFIG_MFD_SM501_GPIO is not set
CONFIG_HTC_PASIC3=m
# CONFIG_HTC_I2CPLD is not set
CONFIG_UCB1400_CORE=m
CONFIG_TPS65010=m
# CONFIG_TPS6507X is not set
CONFIG_TWL4030_CORE=y
CONFIG_TWL4030_CODEC=y
# CONFIG_MFD_TC35892 is not set
# CONFIG_MFD_TMIO is not set
CONFIG_PMIC_DA903X=y
# CONFIG_PMIC_ADP5520 is not set
# CONFIG_MFD_MAX8925 is not set
CONFIG_MFD_WM8400=m
# CONFIG_MFD_WM831X is not set
# CONFIG_MFD_WM8350_I2C is not set
# CONFIG_MFD_WM8994 is not set
CONFIG_MFD_PCF50633=m
CONFIG_MFD_MC13783=m
CONFIG_PCF50633_ADC=m
CONFIG_PCF50633_GPIO=m
# CONFIG_ABX500_CORE is not set
# CONFIG_EZX_PCAP is not set
# CONFIG_AB8500_CORE is not set
# CONFIG_MFD_TIMBERDALE is not set
CONFIG_LPC_SCH=m
# CONFIG_MFD_RDC321X is not set
# CONFIG_MFD_JANZ_CMODIO is not set
CONFIG_REGULATOR=y
CONFIG_REGULATOR_DEBUG=y
# CONFIG_REGULATOR_DUMMY is not set
# CONFIG_REGULATOR_FIXED_VOLTAGE is not set
CONFIG_REGULATOR_VIRTUAL_CONSUMER=m
CONFIG_REGULATOR_USERSPACE_CONSUMER=m
CONFIG_REGULATOR_BQ24022=m
CONFIG_REGULATOR_MAX1586=m
# CONFIG_REGULATOR_MAX8649 is not set
# CONFIG_REGULATOR_MAX8660 is not set
CONFIG_REGULATOR_TWL4030=y
CONFIG_REGULATOR_WM8400=m
CONFIG_REGULATOR_DA903X=m
CONFIG_REGULATOR_PCF50633=m
CONFIG_REGULATOR_LP3971=m
CONFIG_REGULATOR_MC13783=m
CONFIG_REGULATOR_TPS65023=m
CONFIG_REGULATOR_TPS6507X=m
CONFIG_MEDIA_SUPPORT=m

#
# Multimedia core support
#
CONFIG_VIDEO_DEV=m
CONFIG_VIDEO_V4L2_COMMON=m
CONFIG_VIDEO_ALLOW_V4L1=y
CONFIG_VIDEO_V4L1_COMPAT=y
CONFIG_DVB_CORE=m
CONFIG_VIDEO_MEDIA=m

#
# Multimedia drivers
#
CONFIG_VIDEO_SAA7146=m
CONFIG_VIDEO_SAA7146_VV=m
CONFIG_IR_CORE=m
CONFIG_VIDEO_IR=m
CONFIG_RC_MAP=m
CONFIG_IR_NEC_DECODER=m
CONFIG_IR_RC5_DECODER=m
CONFIG_IR_RC6_DECODER=m
CONFIG_IR_JVC_DECODER=m
CONFIG_IR_SONY_DECODER=m
# CONFIG_IR_IMON is not set
CONFIG_MEDIA_ATTACH=y
CONFIG_MEDIA_TUNER=m
# CONFIG_MEDIA_TUNER_CUSTOMISE is not set
CONFIG_MEDIA_TUNER_SIMPLE=m
CONFIG_MEDIA_TUNER_TDA8290=m
CONFIG_MEDIA_TUNER_TDA827X=m
CONFIG_MEDIA_TUNER_TDA18271=m
CONFIG_MEDIA_TUNER_TDA9887=m
CONFIG_MEDIA_TUNER_TEA5761=m
CONFIG_MEDIA_TUNER_TEA5767=m
CONFIG_MEDIA_TUNER_MT20XX=m
CONFIG_MEDIA_TUNER_MT2060=m
CONFIG_MEDIA_TUNER_MT2266=m
CONFIG_MEDIA_TUNER_MT2131=m
CONFIG_MEDIA_TUNER_QT1010=m
CONFIG_MEDIA_TUNER_XC2028=m
CONFIG_MEDIA_TUNER_XC5000=m
CONFIG_MEDIA_TUNER_MXL5005S=m
CONFIG_MEDIA_TUNER_MXL5007T=m
CONFIG_MEDIA_TUNER_MC44S803=m
CONFIG_MEDIA_TUNER_MAX2165=m
CONFIG_VIDEO_V4L2=m
CONFIG_VIDEO_V4L1=m
CONFIG_VIDEOBUF_GEN=m
CONFIG_VIDEOBUF_DMA_SG=m
CONFIG_VIDEOBUF_VMALLOC=m
CONFIG_VIDEOBUF_DVB=m
CONFIG_VIDEO_BTCX=m
CONFIG_VIDEO_TVEEPROM=m
CONFIG_VIDEO_TUNER=m
CONFIG_VIDEO_CAPTURE_DRIVERS=y
# CONFIG_VIDEO_ADV_DEBUG is not set
# CONFIG_VIDEO_FIXED_MINOR_RANGES is not set
CONFIG_VIDEO_HELPER_CHIPS_AUTO=y
CONFIG_VIDEO_IR_I2C=m
CONFIG_VIDEO_TVAUDIO=m
CONFIG_VIDEO_TDA7432=m
CONFIG_VIDEO_TDA9840=m
CONFIG_VIDEO_TEA6415C=m
CONFIG_VIDEO_TEA6420=m
CONFIG_VIDEO_MSP3400=m
CONFIG_VIDEO_CS5345=m
CONFIG_VIDEO_CS53L32A=m
CONFIG_VIDEO_M52790=m
CONFIG_VIDEO_WM8775=m
CONFIG_VIDEO_WM8739=m
CONFIG_VIDEO_VP27SMPX=m
CONFIG_VIDEO_SAA6588=m
CONFIG_VIDEO_BT819=m
CONFIG_VIDEO_BT856=m
CONFIG_VIDEO_BT866=m
CONFIG_VIDEO_KS0127=m
CONFIG_VIDEO_OV7670=m
CONFIG_VIDEO_MT9V011=m
CONFIG_VIDEO_SAA7110=m
CONFIG_VIDEO_SAA711X=m
CONFIG_VIDEO_SAA717X=m
CONFIG_VIDEO_TVP5150=m
CONFIG_VIDEO_VPX3220=m
CONFIG_VIDEO_CX25840=m
CONFIG_VIDEO_CX2341X=m
CONFIG_VIDEO_SAA7127=m
CONFIG_VIDEO_SAA7185=m
CONFIG_VIDEO_ADV7170=m
CONFIG_VIDEO_ADV7175=m
CONFIG_VIDEO_UPD64031A=m
CONFIG_VIDEO_UPD64083=m
CONFIG_VIDEO_BT848=m
CONFIG_VIDEO_BT848_DVB=y
CONFIG_VIDEO_PMS=m
CONFIG_VIDEO_BWQCAM=m
CONFIG_VIDEO_CQCAM=m
CONFIG_VIDEO_W9966=m
CONFIG_VIDEO_CPIA=m
CONFIG_VIDEO_CPIA_PP=m
CONFIG_VIDEO_CPIA_USB=m
CONFIG_VIDEO_CPIA2=m
CONFIG_VIDEO_SAA5246A=m
CONFIG_VIDEO_SAA5249=m
CONFIG_VIDEO_STRADIS=m
CONFIG_VIDEO_ZORAN=m
CONFIG_VIDEO_ZORAN_DC30=m
CONFIG_VIDEO_ZORAN_ZR36060=m
CONFIG_VIDEO_ZORAN_BUZ=m
CONFIG_VIDEO_ZORAN_DC10=m
CONFIG_VIDEO_ZORAN_LML33=m
CONFIG_VIDEO_ZORAN_LML33R10=m
CONFIG_VIDEO_ZORAN_AVS6EYES=m
CONFIG_VIDEO_MEYE=m
CONFIG_VIDEO_SAA7134=m
CONFIG_VIDEO_SAA7134_ALSA=m
CONFIG_VIDEO_SAA7134_DVB=m
CONFIG_VIDEO_MXB=m
CONFIG_VIDEO_HEXIUM_ORION=m
CONFIG_VIDEO_HEXIUM_GEMINI=m
CONFIG_VIDEO_CX88=m
CONFIG_VIDEO_CX88_ALSA=m
CONFIG_VIDEO_CX88_BLACKBIRD=m
CONFIG_VIDEO_CX88_DVB=m
CONFIG_VIDEO_CX88_MPEG=m
CONFIG_VIDEO_CX88_VP3054=m
CONFIG_VIDEO_CX23885=m
CONFIG_VIDEO_AU0828=m
CONFIG_VIDEO_IVTV=m
CONFIG_VIDEO_FB_IVTV=m
CONFIG_VIDEO_CX18=m
# CONFIG_VIDEO_CX18_ALSA is not set
CONFIG_VIDEO_SAA7164=m
CONFIG_VIDEO_CAFE_CCIC=m
CONFIG_SOC_CAMERA=m
CONFIG_SOC_CAMERA_MT9M001=m
CONFIG_SOC_CAMERA_MT9M111=m
CONFIG_SOC_CAMERA_MT9T031=m
# CONFIG_SOC_CAMERA_MT9T112 is not set
CONFIG_SOC_CAMERA_MT9V022=m
# CONFIG_SOC_CAMERA_RJ54N1 is not set
CONFIG_SOC_CAMERA_TW9910=m
CONFIG_SOC_CAMERA_PLATFORM=m
CONFIG_SOC_CAMERA_OV772X=m
# CONFIG_SOC_CAMERA_OV9640 is not set
CONFIG_V4L_USB_DRIVERS=y
CONFIG_USB_VIDEO_CLASS=m
CONFIG_USB_VIDEO_CLASS_INPUT_EVDEV=y
CONFIG_USB_GSPCA=m
CONFIG_USB_M5602=m
CONFIG_USB_STV06XX=m
CONFIG_USB_GL860=m
# CONFIG_USB_GSPCA_BENQ is not set
CONFIG_USB_GSPCA_CONEX=m
# CONFIG_USB_GSPCA_CPIA1 is not set
CONFIG_USB_GSPCA_ETOMS=m
CONFIG_USB_GSPCA_FINEPIX=m
CONFIG_USB_GSPCA_JEILINJ=m
CONFIG_USB_GSPCA_MARS=m
CONFIG_USB_GSPCA_MR97310A=m
CONFIG_USB_GSPCA_OV519=m
CONFIG_USB_GSPCA_OV534=m
# CONFIG_USB_GSPCA_OV534_9 is not set
CONFIG_USB_GSPCA_PAC207=m
# CONFIG_USB_GSPCA_PAC7302 is not set
CONFIG_USB_GSPCA_PAC7311=m
# CONFIG_USB_GSPCA_SN9C2028 is not set
CONFIG_USB_GSPCA_SN9C20X=m
CONFIG_USB_GSPCA_SONIXB=m
CONFIG_USB_GSPCA_SONIXJ=m
CONFIG_USB_GSPCA_SPCA500=m
CONFIG_USB_GSPCA_SPCA501=m
CONFIG_USB_GSPCA_SPCA505=m
CONFIG_USB_GSPCA_SPCA506=m
CONFIG_USB_GSPCA_SPCA508=m
CONFIG_USB_GSPCA_SPCA561=m
CONFIG_USB_GSPCA_SQ905=m
CONFIG_USB_GSPCA_SQ905C=m
CONFIG_USB_GSPCA_STK014=m
# CONFIG_USB_GSPCA_STV0680 is not set
CONFIG_USB_GSPCA_SUNPLUS=m
CONFIG_USB_GSPCA_T613=m
CONFIG_USB_GSPCA_TV8532=m
CONFIG_USB_GSPCA_VC032X=m
CONFIG_USB_GSPCA_ZC3XX=m
CONFIG_VIDEO_PVRUSB2=m
CONFIG_VIDEO_PVRUSB2_SYSFS=y
CONFIG_VIDEO_PVRUSB2_DVB=y
# CONFIG_VIDEO_PVRUSB2_DEBUGIFC is not set
CONFIG_VIDEO_HDPVR=m
CONFIG_VIDEO_EM28XX=m
CONFIG_VIDEO_EM28XX_ALSA=m
CONFIG_VIDEO_EM28XX_DVB=m
# CONFIG_VIDEO_TLG2300 is not set
CONFIG_VIDEO_CX231XX=m
CONFIG_VIDEO_CX231XX_ALSA=m
CONFIG_VIDEO_CX231XX_DVB=m
CONFIG_VIDEO_USBVISION=m
CONFIG_VIDEO_USBVIDEO=m
CONFIG_USB_VICAM=m
CONFIG_USB_IBMCAM=m
CONFIG_USB_KONICAWC=m
CONFIG_USB_QUICKCAM_MESSENGER=m
CONFIG_USB_ET61X251=m
CONFIG_VIDEO_OVCAMCHIP=m
CONFIG_USB_W9968CF=m
# CONFIG_USB_OV511 is not set
CONFIG_USB_SE401=m
CONFIG_USB_SN9C102=m
CONFIG_USB_STV680=m
CONFIG_USB_ZC0301=m
CONFIG_USB_PWC=m
# CONFIG_USB_PWC_DEBUG is not set
CONFIG_USB_PWC_INPUT_EVDEV=y
CONFIG_USB_ZR364XX=m
CONFIG_USB_STKWEBCAM=m
CONFIG_USB_S2255=m
# CONFIG_V4L_MEM2MEM_DRIVERS is not set
CONFIG_RADIO_ADAPTERS=y
CONFIG_RADIO_CADET=m
CONFIG_RADIO_RTRACK=m
CONFIG_RADIO_RTRACK2=m
CONFIG_RADIO_AZTECH=m
CONFIG_RADIO_GEMTEK=m
CONFIG_RADIO_GEMTEK_PCI=m
CONFIG_RADIO_MAXIRADIO=m
CONFIG_RADIO_MAESTRO=m
# CONFIG_RADIO_MIROPCM20 is not set
CONFIG_RADIO_SF16FMI=m
CONFIG_RADIO_SF16FMR2=m
CONFIG_RADIO_TERRATEC=m
CONFIG_RADIO_TRUST=m
CONFIG_RADIO_TYPHOON=m
CONFIG_RADIO_ZOLTRIX=m
CONFIG_I2C_SI4713=m
CONFIG_RADIO_SI4713=m
CONFIG_USB_DSBR=m
CONFIG_RADIO_SI470X=y
CONFIG_USB_SI470X=m
CONFIG_I2C_SI470X=m
CONFIG_USB_MR800=m
CONFIG_RADIO_TEA5764=m
# CONFIG_RADIO_SAA7706H is not set
# CONFIG_RADIO_TEF6862 is not set
CONFIG_DVB_MAX_ADAPTERS=8
CONFIG_DVB_DYNAMIC_MINORS=y
CONFIG_DVB_CAPTURE_DRIVERS=y

#
# Supported SAA7146 based PCI Adapters
#
CONFIG_TTPCI_EEPROM=m
CONFIG_DVB_AV7110=m
CONFIG_DVB_AV7110_OSD=y
CONFIG_DVB_BUDGET_CORE=m
CONFIG_DVB_BUDGET=m
CONFIG_DVB_BUDGET_CI=m
CONFIG_DVB_BUDGET_AV=m
CONFIG_DVB_BUDGET_PATCH=m

#
# Supported USB Adapters
#
CONFIG_DVB_USB=m
# CONFIG_DVB_USB_DEBUG is not set
CONFIG_DVB_USB_A800=m
CONFIG_DVB_USB_DIBUSB_MB=m
# CONFIG_DVB_USB_DIBUSB_MB_FAULTY is not set
CONFIG_DVB_USB_DIBUSB_MC=m
CONFIG_DVB_USB_DIB0700=m
CONFIG_DVB_USB_UMT_010=m
CONFIG_DVB_USB_CXUSB=m
CONFIG_DVB_USB_M920X=m
CONFIG_DVB_USB_GL861=m
CONFIG_DVB_USB_AU6610=m
CONFIG_DVB_USB_DIGITV=m
CONFIG_DVB_USB_VP7045=m
CONFIG_DVB_USB_VP702X=m
CONFIG_DVB_USB_GP8PSK=m
CONFIG_DVB_USB_NOVA_T_USB2=m
CONFIG_DVB_USB_TTUSB2=m
CONFIG_DVB_USB_DTT200U=m
CONFIG_DVB_USB_OPERA1=m
CONFIG_DVB_USB_AF9005=m
CONFIG_DVB_USB_AF9005_REMOTE=m
CONFIG_DVB_USB_DW2102=m
CONFIG_DVB_USB_CINERGY_T2=m
CONFIG_DVB_USB_ANYSEE=m
CONFIG_DVB_USB_DTV5100=m
CONFIG_DVB_USB_AF9015=m
CONFIG_DVB_USB_CE6230=m
CONFIG_DVB_USB_FRIIO=m
# CONFIG_DVB_USB_EC168 is not set
# CONFIG_DVB_USB_AZ6027 is not set
CONFIG_DVB_TTUSB_BUDGET=m
CONFIG_DVB_TTUSB_DEC=m
CONFIG_SMS_SIANO_MDTV=m

#
# Siano module components
#
CONFIG_SMS_USB_DRV=m
CONFIG_SMS_SDIO_DRV=m

#
# Supported FlexCopII (B2C2) Adapters
#
CONFIG_DVB_B2C2_FLEXCOP=m
CONFIG_DVB_B2C2_FLEXCOP_PCI=m
CONFIG_DVB_B2C2_FLEXCOP_USB=m
# CONFIG_DVB_B2C2_FLEXCOP_DEBUG is not set

#
# Supported BT878 Adapters
#
CONFIG_DVB_BT8XX=m

#
# Supported Pluto2 Adapters
#
CONFIG_DVB_PLUTO2=m

#
# Supported SDMC DM1105 Adapters
#
CONFIG_DVB_DM1105=m

#
# Supported FireWire (IEEE 1394) Adapters
#
CONFIG_DVB_FIREDTV=m
CONFIG_DVB_FIREDTV_FIREWIRE=y
CONFIG_DVB_FIREDTV_IEEE1394=y
CONFIG_DVB_FIREDTV_INPUT=y

#
# Supported Earthsoft PT1 Adapters
#
CONFIG_DVB_PT1=m

#
# Supported Mantis Adapters
#
# CONFIG_MANTIS_CORE is not set

#
# Supported nGene Adapters
#
# CONFIG_DVB_NGENE is not set

#
# Supported DVB Frontends
#
# CONFIG_DVB_FE_CUSTOMISE is not set
CONFIG_DVB_STB0899=m
CONFIG_DVB_STB6100=m
CONFIG_DVB_STV090x=m
CONFIG_DVB_STV6110x=m
CONFIG_DVB_CX24110=m
CONFIG_DVB_CX24123=m
CONFIG_DVB_MT312=m
CONFIG_DVB_ZL10036=m
CONFIG_DVB_ZL10039=m
CONFIG_DVB_S5H1420=m
CONFIG_DVB_STV0288=m
CONFIG_DVB_STB6000=m
CONFIG_DVB_STV0299=m
CONFIG_DVB_STV6110=m
CONFIG_DVB_STV0900=m
CONFIG_DVB_TDA8083=m
CONFIG_DVB_TDA10086=m
CONFIG_DVB_TDA8261=m
CONFIG_DVB_VES1X93=m
CONFIG_DVB_TUNER_ITD1000=m
CONFIG_DVB_TUNER_CX24113=m
CONFIG_DVB_TDA826X=m
CONFIG_DVB_TUA6100=m
CONFIG_DVB_CX24116=m
CONFIG_DVB_SI21XX=m
CONFIG_DVB_DS3000=m
CONFIG_DVB_SP8870=m
CONFIG_DVB_SP887X=m
CONFIG_DVB_CX22700=m
CONFIG_DVB_CX22702=m
CONFIG_DVB_L64781=m
CONFIG_DVB_TDA1004X=m
CONFIG_DVB_NXT6000=m
CONFIG_DVB_MT352=m
CONFIG_DVB_ZL10353=m
CONFIG_DVB_DIB3000MB=m
CONFIG_DVB_DIB3000MC=m
CONFIG_DVB_DIB7000M=m
CONFIG_DVB_DIB7000P=m
CONFIG_DVB_TDA10048=m
CONFIG_DVB_AF9013=m
CONFIG_DVB_VES1820=m
CONFIG_DVB_TDA10021=m
CONFIG_DVB_TDA10023=m
CONFIG_DVB_STV0297=m
CONFIG_DVB_NXT200X=m
CONFIG_DVB_OR51211=m
CONFIG_DVB_OR51132=m
CONFIG_DVB_BCM3510=m
CONFIG_DVB_LGDT330X=m
CONFIG_DVB_LGDT3305=m
CONFIG_DVB_S5H1409=m
CONFIG_DVB_AU8522=m
CONFIG_DVB_S5H1411=m
CONFIG_DVB_DIB8000=m
CONFIG_DVB_PLL=m
CONFIG_DVB_TUNER_DIB0070=m
CONFIG_DVB_TUNER_DIB0090=m
CONFIG_DVB_LNBP21=m
CONFIG_DVB_ISL6405=m
CONFIG_DVB_ISL6421=m
CONFIG_DVB_ISL6423=m
CONFIG_DVB_LGS8GXX=m
CONFIG_DVB_ATBM8830=m
CONFIG_DAB=y
CONFIG_USB_DABUSB=m

#
# Graphics support
#
CONFIG_AGP=m
CONFIG_AGP_ALI=m
CONFIG_AGP_ATI=m
CONFIG_AGP_AMD=m
CONFIG_AGP_AMD64=m
CONFIG_AGP_INTEL=m
CONFIG_AGP_NVIDIA=m
CONFIG_AGP_SIS=m
CONFIG_AGP_SWORKS=m
CONFIG_AGP_VIA=m
CONFIG_AGP_EFFICEON=m
CONFIG_VGA_ARB=y
CONFIG_VGA_ARB_MAX_GPUS=16
# CONFIG_VGA_SWITCHEROO is not set
CONFIG_DRM=m
CONFIG_DRM_KMS_HELPER=m
CONFIG_DRM_TTM=m
CONFIG_DRM_TDFX=m
CONFIG_DRM_R128=m
CONFIG_DRM_RADEON=m
CONFIG_DRM_RADEON_KMS=y
CONFIG_DRM_I810=m
CONFIG_DRM_I830=m
CONFIG_DRM_I915=m
CONFIG_DRM_I915_KMS=y
CONFIG_DRM_MGA=m
CONFIG_DRM_SIS=m
CONFIG_DRM_VIA=m
CONFIG_DRM_SAVAGE=m
CONFIG_VGASTATE=m
CONFIG_VIDEO_OUTPUT_CONTROL=m
CONFIG_FB=y
CONFIG_FIRMWARE_EDID=y
CONFIG_FB_DDC=m
# CONFIG_FB_BOOT_VESA_SUPPORT is not set
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
# CONFIG_FB_CFB_REV_PIXELS_IN_BYTE is not set
CONFIG_FB_SYS_FILLRECT=m
CONFIG_FB_SYS_COPYAREA=m
CONFIG_FB_SYS_IMAGEBLIT=m
# CONFIG_FB_FOREIGN_ENDIAN is not set
CONFIG_FB_SYS_FOPS=m
CONFIG_FB_DEFERRED_IO=y
CONFIG_FB_HECUBA=m
CONFIG_FB_SVGALIB=m
# CONFIG_FB_MACMODES is not set
CONFIG_FB_BACKLIGHT=y
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_TILEBLITTING=y

#
# Frame buffer hardware drivers
#
CONFIG_FB_CIRRUS=m
CONFIG_FB_PM2=m
CONFIG_FB_PM2_FIFO_DISCONNECT=y
CONFIG_FB_CYBER2000=m
CONFIG_FB_ARC=m
CONFIG_FB_ASILIANT=y
CONFIG_FB_IMSTT=y
CONFIG_FB_VGA16=m
CONFIG_FB_UVESA=m
# CONFIG_FB_VESA is not set
CONFIG_FB_EFI=y
CONFIG_FB_N411=m
CONFIG_FB_HGA=m
# CONFIG_FB_HGA_ACCEL is not set
CONFIG_FB_S1D13XXX=m
CONFIG_FB_NVIDIA=m
CONFIG_FB_NVIDIA_I2C=y
# CONFIG_FB_NVIDIA_DEBUG is not set
CONFIG_FB_NVIDIA_BACKLIGHT=y
CONFIG_FB_RIVA=m
CONFIG_FB_RIVA_I2C=y
# CONFIG_FB_RIVA_DEBUG is not set
CONFIG_FB_RIVA_BACKLIGHT=y
CONFIG_FB_I810=m
# CONFIG_FB_I810_GTF is not set
CONFIG_FB_LE80578=m
CONFIG_FB_CARILLO_RANCH=m
CONFIG_FB_MATROX=m
CONFIG_FB_MATROX_MILLENIUM=y
CONFIG_FB_MATROX_MYSTIQUE=y
CONFIG_FB_MATROX_G=y
CONFIG_FB_MATROX_I2C=m
CONFIG_FB_MATROX_MAVEN=m
CONFIG_FB_RADEON=m
CONFIG_FB_RADEON_I2C=y
CONFIG_FB_RADEON_BACKLIGHT=y
# CONFIG_FB_RADEON_DEBUG is not set
CONFIG_FB_ATY128=m
CONFIG_FB_ATY128_BACKLIGHT=y
CONFIG_FB_ATY=m
CONFIG_FB_ATY_CT=y
CONFIG_FB_ATY_GENERIC_LCD=y
CONFIG_FB_ATY_GX=y
CONFIG_FB_ATY_BACKLIGHT=y
CONFIG_FB_S3=m
CONFIG_FB_SAVAGE=m
CONFIG_FB_SAVAGE_I2C=y
CONFIG_FB_SAVAGE_ACCEL=y
CONFIG_FB_SIS=m
CONFIG_FB_SIS_300=y
CONFIG_FB_SIS_315=y
CONFIG_FB_VIA=m
# CONFIG_FB_VIA_DIRECT_PROCFS is not set
CONFIG_FB_NEOMAGIC=m
CONFIG_FB_KYRO=m
CONFIG_FB_3DFX=m
# CONFIG_FB_3DFX_ACCEL is not set
CONFIG_FB_3DFX_I2C=y
CONFIG_FB_VOODOO1=m
CONFIG_FB_VT8623=m
CONFIG_FB_TRIDENT=m
CONFIG_FB_ARK=m
CONFIG_FB_PM3=m
CONFIG_FB_CARMINE=m
CONFIG_FB_CARMINE_DRAM_EVAL=y
# CONFIG_CARMINE_DRAM_CUSTOM is not set
CONFIG_FB_GEODE=y
CONFIG_FB_GEODE_LX=m
CONFIG_FB_GEODE_GX=m
CONFIG_FB_GEODE_GX1=m
CONFIG_FB_TMIO=m
CONFIG_FB_TMIO_ACCELL=y
CONFIG_FB_SM501=m
# CONFIG_FB_VIRTUAL is not set
CONFIG_FB_METRONOME=m
CONFIG_FB_MB862XX=m
CONFIG_FB_MB862XX_PCI_GDC=y
CONFIG_FB_BROADSHEET=m
CONFIG_BACKLIGHT_LCD_SUPPORT=y
CONFIG_LCD_CLASS_DEVICE=m
# CONFIG_LCD_L4F00242T03 is not set
CONFIG_LCD_LMS283GF05=m
CONFIG_LCD_LTV350QV=m
CONFIG_LCD_ILI9320=m
CONFIG_LCD_TDO24M=m
CONFIG_LCD_VGG2432A4=m
CONFIG_LCD_PLATFORM=m
# CONFIG_LCD_S6E63M0 is not set
CONFIG_BACKLIGHT_CLASS_DEVICE=y
CONFIG_BACKLIGHT_GENERIC=m
CONFIG_BACKLIGHT_PROGEAR=m
CONFIG_BACKLIGHT_CARILLO_RANCH=m
CONFIG_BACKLIGHT_DA903X=m
CONFIG_BACKLIGHT_MBP_NVIDIA=m
CONFIG_BACKLIGHT_SAHARA=m
# CONFIG_BACKLIGHT_ADP8860 is not set
# CONFIG_BACKLIGHT_PCF50633 is not set

#
# Display device support
#
CONFIG_DISPLAY_SUPPORT=m

#
# Display hardware drivers
#

#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
# CONFIG_VGACON_SOFT_SCROLLBACK is not set
CONFIG_MDA_CONSOLE=m
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=m
# CONFIG_FRAMEBUFFER_CONSOLE_DETECT_PRIMARY is not set
# CONFIG_FRAMEBUFFER_CONSOLE_ROTATION is not set
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y
# CONFIG_LOGO is not set
CONFIG_SOUND=m
CONFIG_SOUND_OSS_CORE=y
CONFIG_SOUND_OSS_CORE_PRECLAIM=y
CONFIG_SND=m
CONFIG_SND_TIMER=m
CONFIG_SND_PCM=m
CONFIG_SND_HWDEP=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_JACK=y
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=m
CONFIG_SND_PCM_OSS=m
CONFIG_SND_PCM_OSS_PLUGINS=y
CONFIG_SND_SEQUENCER_OSS=y
CONFIG_SND_HRTIMER=m
CONFIG_SND_SEQ_HRTIMER_DEFAULT=y
CONFIG_SND_DYNAMIC_MINORS=y
CONFIG_SND_SUPPORT_OLD_API=y
CONFIG_SND_VERBOSE_PROCFS=y
# CONFIG_SND_VERBOSE_PRINTK is not set
# CONFIG_SND_DEBUG is not set
CONFIG_SND_VMASTER=y
CONFIG_SND_DMA_SGBUF=y
CONFIG_SND_RAWMIDI_SEQ=m
CONFIG_SND_OPL3_LIB_SEQ=m
CONFIG_SND_OPL4_LIB_SEQ=m
CONFIG_SND_SBAWE_SEQ=m
CONFIG_SND_EMU10K1_SEQ=m
CONFIG_SND_MPU401_UART=m
CONFIG_SND_OPL3_LIB=m
CONFIG_SND_OPL4_LIB=m
CONFIG_SND_VX_LIB=m
CONFIG_SND_AC97_CODEC=m
CONFIG_SND_DRIVERS=y
CONFIG_SND_PCSP=m
CONFIG_SND_DUMMY=m
CONFIG_SND_VIRMIDI=m
CONFIG_SND_MTPAV=m
CONFIG_SND_MTS64=m
CONFIG_SND_SERIAL_U16550=m
CONFIG_SND_MPU401=m
CONFIG_SND_PORTMAN2X4=m
CONFIG_SND_AC97_POWER_SAVE=y
CONFIG_SND_AC97_POWER_SAVE_DEFAULT=0
CONFIG_SND_WSS_LIB=m
CONFIG_SND_SB_COMMON=m
CONFIG_SND_SB8_DSP=m
CONFIG_SND_SB16_DSP=m
CONFIG_SND_ISA=y
CONFIG_SND_ADLIB=m
CONFIG_SND_AD1816A=m
CONFIG_SND_AD1848=m
CONFIG_SND_ALS100=m
CONFIG_SND_AZT2320=m
CONFIG_SND_CMI8330=m
CONFIG_SND_CS4231=m
CONFIG_SND_CS4236=m
CONFIG_SND_ES1688=m
CONFIG_SND_ES18XX=m
CONFIG_SND_SC6000=m
CONFIG_SND_GUSCLASSIC=m
CONFIG_SND_GUSEXTREME=m
CONFIG_SND_GUSMAX=m
CONFIG_SND_INTERWAVE=m
CONFIG_SND_INTERWAVE_STB=m
# CONFIG_SND_JAZZ16 is not set
CONFIG_SND_OPL3SA2=m
CONFIG_SND_OPTI92X_AD1848=m
CONFIG_SND_OPTI92X_CS4231=m
CONFIG_SND_OPTI93X=m
CONFIG_SND_MIRO=m
CONFIG_SND_SB8=m
CONFIG_SND_SB16=m
CONFIG_SND_SBAWE=m
CONFIG_SND_SB16_CSP=y
CONFIG_SND_SGALAXY=m
CONFIG_SND_SSCAPE=m
CONFIG_SND_WAVEFRONT=m
CONFIG_SND_MSND_PINNACLE=m
CONFIG_SND_MSND_CLASSIC=m
CONFIG_SND_PCI=y
CONFIG_SND_AD1889=m
CONFIG_SND_ALS300=m
CONFIG_SND_ALS4000=m
CONFIG_SND_ALI5451=m
# CONFIG_SND_ASIHPI is not set
CONFIG_SND_ATIIXP=m
CONFIG_SND_ATIIXP_MODEM=m
CONFIG_SND_AU8810=m
CONFIG_SND_AU8820=m
CONFIG_SND_AU8830=m
CONFIG_SND_AW2=m
CONFIG_SND_AZT3328=m
CONFIG_SND_BT87X=m
# CONFIG_SND_BT87X_OVERCLOCK is not set
CONFIG_SND_CA0106=m
CONFIG_SND_CMIPCI=m
CONFIG_SND_OXYGEN_LIB=m
CONFIG_SND_OXYGEN=m
CONFIG_SND_CS4281=m
CONFIG_SND_CS46XX=m
CONFIG_SND_CS46XX_NEW_DSP=y
CONFIG_SND_CS5530=m
CONFIG_SND_CS5535AUDIO=m
CONFIG_SND_CTXFI=m
CONFIG_SND_DARLA20=m
CONFIG_SND_GINA20=m
CONFIG_SND_LAYLA20=m
CONFIG_SND_DARLA24=m
CONFIG_SND_GINA24=m
CONFIG_SND_LAYLA24=m
CONFIG_SND_MONA=m
CONFIG_SND_MIA=m
CONFIG_SND_ECHO3G=m
CONFIG_SND_INDIGO=m
CONFIG_SND_INDIGOIO=m
CONFIG_SND_INDIGODJ=m
CONFIG_SND_INDIGOIOX=m
CONFIG_SND_INDIGODJX=m
CONFIG_SND_EMU10K1=m
CONFIG_SND_EMU10K1X=m
CONFIG_SND_ENS1370=m
CONFIG_SND_ENS1371=m
CONFIG_SND_ES1938=m
CONFIG_SND_ES1968=m
# CONFIG_SND_ES1968_INPUT is not set
CONFIG_SND_FM801=m
CONFIG_SND_FM801_TEA575X_BOOL=y
CONFIG_SND_FM801_TEA575X=m
CONFIG_SND_HDA_INTEL=m
CONFIG_SND_HDA_HWDEP=y
CONFIG_SND_HDA_RECONFIG=y
CONFIG_SND_HDA_INPUT_BEEP=y
CONFIG_SND_HDA_INPUT_BEEP_MODE=1
CONFIG_SND_HDA_INPUT_JACK=y
CONFIG_SND_HDA_PATCH_LOADER=y
CONFIG_SND_HDA_CODEC_REALTEK=y
CONFIG_SND_HDA_CODEC_ANALOG=y
CONFIG_SND_HDA_CODEC_SIGMATEL=y
CONFIG_SND_HDA_CODEC_VIA=y
CONFIG_SND_HDA_CODEC_ATIHDMI=y
CONFIG_SND_HDA_CODEC_NVHDMI=y
CONFIG_SND_HDA_CODEC_INTELHDMI=y
CONFIG_SND_HDA_ELD=y
CONFIG_SND_HDA_CODEC_CIRRUS=y
CONFIG_SND_HDA_CODEC_CONEXANT=y
CONFIG_SND_HDA_CODEC_CA0110=y
CONFIG_SND_HDA_CODEC_CMEDIA=y
CONFIG_SND_HDA_CODEC_SI3054=y
CONFIG_SND_HDA_GENERIC=y
CONFIG_SND_HDA_POWER_SAVE=y
CONFIG_SND_HDA_POWER_SAVE_DEFAULT=0
CONFIG_SND_HDSP=m
CONFIG_SND_HDSPM=m
CONFIG_SND_HIFIER=m
CONFIG_SND_ICE1712=m
CONFIG_SND_ICE1724=m
CONFIG_SND_INTEL8X0=m
CONFIG_SND_INTEL8X0M=m
CONFIG_SND_KORG1212=m
CONFIG_SND_LX6464ES=m
CONFIG_SND_MAESTRO3=m
# CONFIG_SND_MAESTRO3_INPUT is not set
CONFIG_SND_MIXART=m
CONFIG_SND_NM256=m
CONFIG_SND_PCXHR=m
CONFIG_SND_RIPTIDE=m
CONFIG_SND_RME32=m
CONFIG_SND_RME96=m
CONFIG_SND_RME9652=m
CONFIG_SND_SIS7019=m
CONFIG_SND_SONICVIBES=m
CONFIG_SND_TRIDENT=m
CONFIG_SND_VIA82XX=m
CONFIG_SND_VIA82XX_MODEM=m
CONFIG_SND_VIRTUOSO=m
CONFIG_SND_VX222=m
CONFIG_SND_YMFPCI=m
CONFIG_SND_SPI=y
CONFIG_SND_USB=y
CONFIG_SND_USB_AUDIO=m
# CONFIG_SND_USB_UA101 is not set
CONFIG_SND_USB_USX2Y=m
CONFIG_SND_USB_CAIAQ=m
CONFIG_SND_USB_CAIAQ_INPUT=y
CONFIG_SND_USB_US122L=m
CONFIG_SND_PCMCIA=y
CONFIG_SND_VXPOCKET=m
CONFIG_SND_PDAUDIOCF=m
CONFIG_SND_SOC=m
CONFIG_SND_SOC_I2C_AND_SPI=m
CONFIG_SND_SOC_ALL_CODECS=m
CONFIG_SND_SOC_WM_HUBS=m
CONFIG_SND_SOC_AD1836=m
CONFIG_SND_SOC_AD193X=m
CONFIG_SND_SOC_AD73311=m
CONFIG_SND_SOC_ADS117X=m
CONFIG_SND_SOC_AK4104=m
CONFIG_SND_SOC_AK4535=m
CONFIG_SND_SOC_AK4642=m
CONFIG_SND_SOC_AK4671=m
CONFIG_SND_SOC_CS4270=m
CONFIG_SND_SOC_DA7210=m
CONFIG_SND_SOC_L3=m
CONFIG_SND_SOC_PCM3008=m
CONFIG_SND_SOC_SPDIF=m
CONFIG_SND_SOC_SSM2602=m
CONFIG_SND_SOC_TLV320AIC23=m
CONFIG_SND_SOC_TLV320AIC26=m
CONFIG_SND_SOC_TLV320AIC3X=m
CONFIG_SND_SOC_TLV320DAC33=m
CONFIG_SND_SOC_TWL4030=m
CONFIG_SND_SOC_TWL6040=m
CONFIG_SND_SOC_UDA134X=m
CONFIG_SND_SOC_UDA1380=m
CONFIG_SND_SOC_WM8400=m
CONFIG_SND_SOC_WM8510=m
CONFIG_SND_SOC_WM8523=m
CONFIG_SND_SOC_WM8580=m
CONFIG_SND_SOC_WM8711=m
CONFIG_SND_SOC_WM8727=m
CONFIG_SND_SOC_WM8728=m
CONFIG_SND_SOC_WM8731=m
CONFIG_SND_SOC_WM8750=m
CONFIG_SND_SOC_WM8753=m
CONFIG_SND_SOC_WM8776=m
CONFIG_SND_SOC_WM8900=m
CONFIG_SND_SOC_WM8903=m
CONFIG_SND_SOC_WM8904=m
CONFIG_SND_SOC_WM8940=m
CONFIG_SND_SOC_WM8955=m
CONFIG_SND_SOC_WM8960=m
CONFIG_SND_SOC_WM8961=m
CONFIG_SND_SOC_WM8971=m
CONFIG_SND_SOC_WM8974=m
CONFIG_SND_SOC_WM8978=m
CONFIG_SND_SOC_WM8988=m
CONFIG_SND_SOC_WM8990=m
CONFIG_SND_SOC_WM8993=m
CONFIG_SND_SOC_WM9081=m
CONFIG_SND_SOC_MAX9877=m
CONFIG_SND_SOC_TPA6130A2=m
CONFIG_SND_SOC_WM2000=m
CONFIG_SND_SOC_WM9090=m
CONFIG_SOUND_PRIME=m
CONFIG_SOUND_MSNDCLAS=m
CONFIG_MSNDCLAS_INIT_FILE="/etc/sound/msndinit.bin"
CONFIG_MSNDCLAS_PERM_FILE="/etc/sound/msndperm.bin"
CONFIG_SOUND_MSNDPIN=m
CONFIG_MSNDPIN_INIT_FILE="/etc/sound/pndspini.bin"
CONFIG_MSNDPIN_PERM_FILE="/etc/sound/pndsperm.bin"
CONFIG_SOUND_OSS=m
# CONFIG_SOUND_TRACEINIT is not set
CONFIG_SOUND_DMAP=y
CONFIG_SOUND_VMIDI=m
CONFIG_SOUND_TRIX=m
CONFIG_SOUND_MSS=m
CONFIG_SOUND_MPU401=m
CONFIG_SOUND_PAS=m
CONFIG_SOUND_PSS=m
CONFIG_PSS_MIXER=y
# CONFIG_PSS_HAVE_BOOT is not set
CONFIG_SOUND_SB=m
CONFIG_SOUND_YM3812=m
CONFIG_SOUND_UART6850=m
CONFIG_SOUND_AEDSP16=m
CONFIG_SC6600=y
CONFIG_SC6600_JOY=y
CONFIG_SC6600_CDROM=4
CONFIG_SC6600_CDROMBASE=0
CONFIG_SOUND_KAHLUA=m
CONFIG_AC97_BUS=m
CONFIG_HID_SUPPORT=y
CONFIG_HID=m
CONFIG_HIDRAW=y

#
# USB Input Devices
#
CONFIG_USB_HID=m
CONFIG_HID_PID=y
CONFIG_USB_HIDDEV=y

#
# Special HID drivers
#
CONFIG_HID_3M_PCT=m
CONFIG_HID_A4TECH=m
CONFIG_HID_APPLE=m
CONFIG_HID_BELKIN=m
# CONFIG_HID_CANDO is not set
CONFIG_HID_CHERRY=m
CONFIG_HID_CHICONY=m
# CONFIG_HID_PRODIKEYS is not set
CONFIG_HID_CYPRESS=m
CONFIG_HID_DRAGONRISE=m
CONFIG_DRAGONRISE_FF=y
# CONFIG_HID_EGALAX is not set
CONFIG_HID_EZKEY=m
CONFIG_HID_KYE=m
CONFIG_HID_GYRATION=m
CONFIG_HID_TWINHAN=m
CONFIG_HID_KENSINGTON=m
CONFIG_HID_LOGITECH=m
CONFIG_LOGITECH_FF=y
CONFIG_LOGIRUMBLEPAD2_FF=y
# CONFIG_LOGIG940_FF is not set
# CONFIG_HID_MAGICMOUSE is not set
CONFIG_HID_MICROSOFT=m
CONFIG_HID_MOSART=m
CONFIG_HID_MONTEREY=m
CONFIG_HID_NTRIG=m
CONFIG_HID_ORTEK=m
CONFIG_HID_PANTHERLORD=m
CONFIG_PANTHERLORD_FF=y
CONFIG_HID_PETALYNX=m
# CONFIG_HID_PICOLCD is not set
CONFIG_HID_QUANTA=m
# CONFIG_HID_ROCCAT is not set
# CONFIG_HID_ROCCAT_KONE is not set
CONFIG_HID_SAMSUNG=m
CONFIG_HID_SONY=m
CONFIG_HID_STANTUM=m
CONFIG_HID_SUNPLUS=m
CONFIG_HID_GREENASIA=m
CONFIG_GREENASIA_FF=y
CONFIG_HID_SMARTJOYPLUS=m
CONFIG_SMARTJOYPLUS_FF=y
CONFIG_HID_TOPSEED=m
CONFIG_HID_THRUSTMASTER=m
CONFIG_THRUSTMASTER_FF=y
CONFIG_HID_WACOM=m
# CONFIG_HID_WACOM_POWER_SUPPLY is not set
CONFIG_HID_ZEROPLUS=m
CONFIG_ZEROPLUS_FF=y
# CONFIG_HID_ZYDACRON is not set
CONFIG_USB_SUPPORT=y
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB_ARCH_HAS_OHCI=y
CONFIG_USB_ARCH_HAS_EHCI=y
CONFIG_USB=y
# CONFIG_USB_DEBUG is not set
# CONFIG_USB_ANNOUNCE_NEW_DEVICES is not set

#
# Miscellaneous USB options
#
# CONFIG_USB_DEVICEFS is not set
# CONFIG_USB_DEVICE_CLASS is not set
# CONFIG_USB_DYNAMIC_MINORS is not set
CONFIG_USB_SUSPEND=y
# CONFIG_USB_OTG is not set
CONFIG_USB_MON=y
CONFIG_USB_WUSB=m
CONFIG_USB_WUSB_CBAF=m
# CONFIG_USB_WUSB_CBAF_DEBUG is not set

#
# USB Host Controller Drivers
#
CONFIG_USB_C67X00_HCD=m
CONFIG_USB_XHCI_HCD=m
# CONFIG_USB_XHCI_HCD_DEBUGGING is not set
CONFIG_USB_EHCI_HCD=y
CONFIG_USB_EHCI_ROOT_HUB_TT=y
CONFIG_USB_EHCI_TT_NEWSCHED=y
CONFIG_USB_OXU210HP_HCD=m
CONFIG_USB_ISP116X_HCD=m
CONFIG_USB_ISP1760_HCD=m
CONFIG_USB_ISP1362_HCD=m
CONFIG_USB_OHCI_HCD=y
# CONFIG_USB_OHCI_BIG_ENDIAN_DESC is not set
# CONFIG_USB_OHCI_BIG_ENDIAN_MMIO is not set
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
CONFIG_USB_UHCI_HCD=y
CONFIG_USB_U132_HCD=m
CONFIG_USB_SL811_HCD=m
CONFIG_USB_SL811_CS=m
CONFIG_USB_R8A66597_HCD=m
CONFIG_USB_WHCI_HCD=m
CONFIG_USB_HWA_HCD=m
# CONFIG_USB_GADGET_MUSB_HDRC is not set

#
# USB Device Class drivers
#
CONFIG_USB_ACM=m
CONFIG_USB_PRINTER=m
CONFIG_USB_WDM=m
CONFIG_USB_TMC=m

#
# NOTE: USB_STORAGE depends on SCSI but BLK_DEV_SD may
#

#
# also be needed; see USB_STORAGE Help for more info
#
CONFIG_USB_STORAGE=m
# CONFIG_USB_STORAGE_DEBUG is not set
CONFIG_USB_STORAGE_DATAFAB=m
CONFIG_USB_STORAGE_FREECOM=m
CONFIG_USB_STORAGE_ISD200=m
CONFIG_USB_STORAGE_USBAT=m
CONFIG_USB_STORAGE_SDDR09=m
CONFIG_USB_STORAGE_SDDR55=m
CONFIG_USB_STORAGE_JUMPSHOT=m
CONFIG_USB_STORAGE_ALAUDA=m
CONFIG_USB_STORAGE_ONETOUCH=m
CONFIG_USB_STORAGE_KARMA=m
CONFIG_USB_STORAGE_CYPRESS_ATACB=m
# CONFIG_USB_LIBUSUAL is not set

#
# USB Imaging devices
#
CONFIG_USB_MDC800=m
CONFIG_USB_MICROTEK=m

#
# USB port drivers
#
CONFIG_USB_USS720=m
CONFIG_USB_SERIAL=m
CONFIG_USB_EZUSB=y
CONFIG_USB_SERIAL_GENERIC=y
CONFIG_USB_SERIAL_AIRCABLE=m
CONFIG_USB_SERIAL_ARK3116=m
CONFIG_USB_SERIAL_BELKIN=m
CONFIG_USB_SERIAL_CH341=m
CONFIG_USB_SERIAL_WHITEHEAT=m
CONFIG_USB_SERIAL_DIGI_ACCELEPORT=m
CONFIG_USB_SERIAL_CP210X=m
CONFIG_USB_SERIAL_CYPRESS_M8=m
CONFIG_USB_SERIAL_EMPEG=m
CONFIG_USB_SERIAL_FTDI_SIO=m
CONFIG_USB_SERIAL_FUNSOFT=m
CONFIG_USB_SERIAL_VISOR=m
CONFIG_USB_SERIAL_IPAQ=m
CONFIG_USB_SERIAL_IR=m
CONFIG_USB_SERIAL_EDGEPORT=m
CONFIG_USB_SERIAL_EDGEPORT_TI=m
CONFIG_USB_SERIAL_GARMIN=m
CONFIG_USB_SERIAL_IPW=m
CONFIG_USB_SERIAL_IUU=m
CONFIG_USB_SERIAL_KEYSPAN_PDA=m
CONFIG_USB_SERIAL_KEYSPAN=m
CONFIG_USB_SERIAL_KEYSPAN_MPR=y
CONFIG_USB_SERIAL_KEYSPAN_USA28=y
CONFIG_USB_SERIAL_KEYSPAN_USA28X=y
CONFIG_USB_SERIAL_KEYSPAN_USA28XA=y
CONFIG_USB_SERIAL_KEYSPAN_USA28XB=y
CONFIG_USB_SERIAL_KEYSPAN_USA19=y
CONFIG_USB_SERIAL_KEYSPAN_USA18X=y
CONFIG_USB_SERIAL_KEYSPAN_USA19W=y
CONFIG_USB_SERIAL_KEYSPAN_USA19QW=y
CONFIG_USB_SERIAL_KEYSPAN_USA19QI=y
CONFIG_USB_SERIAL_KEYSPAN_USA49W=y
CONFIG_USB_SERIAL_KEYSPAN_USA49WLC=y
CONFIG_USB_SERIAL_KLSI=m
CONFIG_USB_SERIAL_KOBIL_SCT=m
CONFIG_USB_SERIAL_MCT_U232=m
CONFIG_USB_SERIAL_MOS7720=m
# CONFIG_USB_SERIAL_MOS7715_PARPORT is not set
CONFIG_USB_SERIAL_MOS7840=m
CONFIG_USB_SERIAL_MOTOROLA=m
CONFIG_USB_SERIAL_NAVMAN=m
CONFIG_USB_SERIAL_PL2303=m
CONFIG_USB_SERIAL_OTI6858=m
# CONFIG_USB_SERIAL_QCAUX is not set
CONFIG_USB_SERIAL_QUALCOMM=m
CONFIG_USB_SERIAL_SPCP8X5=m
CONFIG_USB_SERIAL_HP4X=m
CONFIG_USB_SERIAL_SAFE=m
# CONFIG_USB_SERIAL_SAFE_PADDED is not set
CONFIG_USB_SERIAL_SIEMENS_MPI=m
CONFIG_USB_SERIAL_SIERRAWIRELESS=m
CONFIG_USB_SERIAL_SYMBOL=m
CONFIG_USB_SERIAL_TI=m
CONFIG_USB_SERIAL_CYBERJACK=m
CONFIG_USB_SERIAL_XIRCOM=m
CONFIG_USB_SERIAL_WWAN=m
CONFIG_USB_SERIAL_OPTION=m
CONFIG_USB_SERIAL_OMNINET=m
CONFIG_USB_SERIAL_OPTICON=m
# CONFIG_USB_SERIAL_VIVOPAY_SERIAL is not set
# CONFIG_USB_SERIAL_ZIO is not set
CONFIG_USB_SERIAL_DEBUG=m

#
# USB Miscellaneous drivers
#
CONFIG_USB_EMI62=m
CONFIG_USB_EMI26=m
CONFIG_USB_ADUTUX=m
CONFIG_USB_SEVSEG=m
CONFIG_USB_RIO500=m
CONFIG_USB_LEGOTOWER=m
CONFIG_USB_LCD=m
CONFIG_USB_LED=m
CONFIG_USB_CYPRESS_CY7C63=m
CONFIG_USB_CYTHERM=m
CONFIG_USB_IDMOUSE=m
CONFIG_USB_FTDI_ELAN=m
CONFIG_USB_APPLEDISPLAY=m
CONFIG_USB_SISUSBVGA=m
# CONFIG_USB_SISUSBVGA_CON is not set
CONFIG_USB_LD=m
CONFIG_USB_TRANCEVIBRATOR=m
CONFIG_USB_IOWARRIOR=m
CONFIG_USB_TEST=m
CONFIG_USB_ISIGHTFW=m
CONFIG_USB_ATM=m
CONFIG_USB_SPEEDTOUCH=m
CONFIG_USB_CXACRU=m
CONFIG_USB_UEAGLEATM=m
CONFIG_USB_XUSBATM=m
CONFIG_USB_GADGET=m
# CONFIG_USB_GADGET_DEBUG is not set
# CONFIG_USB_GADGET_DEBUG_FILES is not set
# CONFIG_USB_GADGET_DEBUG_FS is not set
CONFIG_USB_GADGET_VBUS_DRAW=2
CONFIG_USB_GADGET_SELECTED=y
# CONFIG_USB_GADGET_AT91 is not set
# CONFIG_USB_GADGET_ATMEL_USBA is not set
# CONFIG_USB_GADGET_FSL_USB2 is not set
# CONFIG_USB_GADGET_LH7A40X is not set
# CONFIG_USB_GADGET_OMAP is not set
# CONFIG_USB_GADGET_PXA25X is not set
# CONFIG_USB_GADGET_R8A66597 is not set
# CONFIG_USB_GADGET_PXA27X is not set
# CONFIG_USB_GADGET_S3C_HSOTG is not set
# CONFIG_USB_GADGET_IMX is not set
# CONFIG_USB_GADGET_S3C2410 is not set
# CONFIG_USB_GADGET_M66592 is not set
# CONFIG_USB_GADGET_AMD5536UDC is not set
# CONFIG_USB_GADGET_FSL_QE is not set
# CONFIG_USB_GADGET_CI13XXX is not set
# CONFIG_USB_GADGET_NET2280 is not set
# CONFIG_USB_GADGET_GOKU is not set
# CONFIG_USB_GADGET_LANGWELL is not set
CONFIG_USB_GADGET_DUMMY_HCD=y
CONFIG_USB_DUMMY_HCD=m
CONFIG_USB_GADGET_DUALSPEED=y
CONFIG_USB_ZERO=m
CONFIG_USB_AUDIO=m
CONFIG_USB_ETH=m
CONFIG_USB_ETH_RNDIS=y
# CONFIG_USB_ETH_EEM is not set
CONFIG_USB_GADGETFS=m
# CONFIG_USB_FUNCTIONFS is not set
CONFIG_USB_FILE_STORAGE=m
# CONFIG_USB_FILE_STORAGE_TEST is not set
# CONFIG_USB_MASS_STORAGE is not set
CONFIG_USB_G_SERIAL=m
CONFIG_USB_MIDI_GADGET=m
CONFIG_USB_G_PRINTER=m
CONFIG_USB_CDC_COMPOSITE=m
# CONFIG_USB_G_NOKIA is not set
# CONFIG_USB_G_MULTI is not set
# CONFIG_USB_G_HID is not set
# CONFIG_USB_G_WEBCAM is not set

#
# OTG and related infrastructure
#
CONFIG_USB_OTG_UTILS=y
CONFIG_USB_GPIO_VBUS=m
CONFIG_TWL4030_USB=m
CONFIG_NOP_USB_XCEIV=m
CONFIG_UWB=m
CONFIG_UWB_HWA=m
CONFIG_UWB_WHCI=m
CONFIG_UWB_WLP=m
CONFIG_UWB_I1480U=m
CONFIG_UWB_I1480U_WLP=m
CONFIG_MMC=y
# CONFIG_MMC_DEBUG is not set
# CONFIG_MMC_UNSAFE_RESUME is not set

#
# MMC/SD/SDIO Card Drivers
#
CONFIG_MMC_BLOCK=m
CONFIG_MMC_BLOCK_BOUNCE=y
CONFIG_SDIO_UART=m
# CONFIG_MMC_TEST is not set

#
# MMC/SD/SDIO Host Controller Drivers
#
CONFIG_MMC_SDHCI=m
CONFIG_MMC_SDHCI_PCI=m
# CONFIG_MMC_RICOH_MMC is not set
CONFIG_MMC_SDHCI_PLTFM=m
CONFIG_MMC_WBSD=m
CONFIG_MMC_TIFM_SD=m
CONFIG_MMC_SDRICOH_CS=m
CONFIG_MMC_CB710=m
CONFIG_MMC_VIA_SDMMC=m
CONFIG_MEMSTICK=m
# CONFIG_MEMSTICK_DEBUG is not set

#
# MemoryStick drivers
#
# CONFIG_MEMSTICK_UNSAFE_RESUME is not set
CONFIG_MSPRO_BLOCK=m

#
# MemoryStick Host Controller Drivers
#
CONFIG_MEMSTICK_TIFM_MS=m
CONFIG_MEMSTICK_JMICRON_38X=m
CONFIG_NEW_LEDS=y
CONFIG_LEDS_CLASS=m

#
# LED drivers
#
CONFIG_LEDS_NET48XX=m
CONFIG_LEDS_WRAP=m
CONFIG_LEDS_ALIX2=m
CONFIG_LEDS_PCA9532=m
CONFIG_LEDS_GPIO=m
CONFIG_LEDS_GPIO_PLATFORM=y
CONFIG_LEDS_LP3944=m
# CONFIG_LEDS_CLEVO_MAIL is not set
CONFIG_LEDS_PCA955X=m
CONFIG_LEDS_DA903X=m
CONFIG_LEDS_DAC124S085=m
# CONFIG_LEDS_REGULATOR is not set
CONFIG_LEDS_BD2802=m
# CONFIG_LEDS_INTEL_SS4200 is not set
# CONFIG_LEDS_LT3593 is not set
CONFIG_LEDS_DELL_NETBOOKS=m
# CONFIG_LEDS_MC13783 is not set
CONFIG_LEDS_TRIGGERS=y

#
# LED Triggers
#
CONFIG_LEDS_TRIGGER_TIMER=m
CONFIG_LEDS_TRIGGER_HEARTBEAT=m
CONFIG_LEDS_TRIGGER_BACKLIGHT=m
CONFIG_LEDS_TRIGGER_GPIO=m
CONFIG_LEDS_TRIGGER_DEFAULT_ON=m

#
# iptables trigger is under Netfilter config (LED target)
#
# CONFIG_ACCESSIBILITY is not set
CONFIG_INFINIBAND=m
CONFIG_INFINIBAND_USER_MAD=m
CONFIG_INFINIBAND_USER_ACCESS=m
CONFIG_INFINIBAND_USER_MEM=y
CONFIG_INFINIBAND_ADDR_TRANS=y
CONFIG_INFINIBAND_MTHCA=m
CONFIG_INFINIBAND_MTHCA_DEBUG=y
CONFIG_INFINIBAND_AMSO1100=m
CONFIG_INFINIBAND_AMSO1100_DEBUG=y
CONFIG_INFINIBAND_CXGB3=m
# CONFIG_INFINIBAND_CXGB3_DEBUG is not set
CONFIG_MLX4_INFINIBAND=m
# CONFIG_INFINIBAND_NES is not set
CONFIG_INFINIBAND_IPOIB=m
CONFIG_INFINIBAND_IPOIB_CM=y
CONFIG_INFINIBAND_IPOIB_DEBUG=y
# CONFIG_INFINIBAND_IPOIB_DEBUG_DATA is not set
CONFIG_INFINIBAND_SRP=m
CONFIG_INFINIBAND_ISER=m
CONFIG_EDAC=y

#
# Reporting subsystems
#
# CONFIG_EDAC_DEBUG is not set
CONFIG_EDAC_DECODE_MCE=m
CONFIG_EDAC_MM_EDAC=m
CONFIG_EDAC_AMD76X=m
CONFIG_EDAC_E7XXX=m
CONFIG_EDAC_E752X=m
CONFIG_EDAC_I82875P=m
CONFIG_EDAC_I82975X=m
CONFIG_EDAC_I3000=m
CONFIG_EDAC_I3200=m
CONFIG_EDAC_X38=m
CONFIG_EDAC_I5400=m
# CONFIG_EDAC_I7CORE is not set
CONFIG_EDAC_I82860=m
CONFIG_EDAC_R82600=m
CONFIG_EDAC_I5000=m
CONFIG_EDAC_I5100=m
CONFIG_RTC_LIB=y
CONFIG_RTC_CLASS=y
CONFIG_RTC_HCTOSYS=y
CONFIG_RTC_HCTOSYS_DEVICE="rtc0"
# CONFIG_RTC_DEBUG is not set

#
# RTC interfaces
#
CONFIG_RTC_INTF_SYSFS=y
CONFIG_RTC_INTF_PROC=y
CONFIG_RTC_INTF_DEV=y
CONFIG_RTC_INTF_DEV_UIE_EMUL=y
CONFIG_RTC_DRV_TEST=m

#
# I2C RTC drivers
#
CONFIG_RTC_DRV_DS1307=m
CONFIG_RTC_DRV_DS1374=m
CONFIG_RTC_DRV_DS1672=m
CONFIG_RTC_DRV_MAX6900=m
CONFIG_RTC_DRV_RS5C372=m
CONFIG_RTC_DRV_ISL1208=m
CONFIG_RTC_DRV_X1205=m
CONFIG_RTC_DRV_PCF8563=m
CONFIG_RTC_DRV_PCF8583=m
CONFIG_RTC_DRV_M41T80=m
CONFIG_RTC_DRV_M41T80_WDT=y
# CONFIG_RTC_DRV_BQ32K is not set
CONFIG_RTC_DRV_TWL4030=m
CONFIG_RTC_DRV_S35390A=m
CONFIG_RTC_DRV_FM3130=m
CONFIG_RTC_DRV_RX8581=m
CONFIG_RTC_DRV_RX8025=m

#
# SPI RTC drivers
#
CONFIG_RTC_DRV_M41T94=m
CONFIG_RTC_DRV_DS1305=m
CONFIG_RTC_DRV_DS1390=m
CONFIG_RTC_DRV_MAX6902=m
CONFIG_RTC_DRV_R9701=m
CONFIG_RTC_DRV_RS5C348=m
CONFIG_RTC_DRV_DS3234=m
CONFIG_RTC_DRV_PCF2123=m

#
# Platform RTC drivers
#
CONFIG_RTC_DRV_CMOS=y
CONFIG_RTC_DRV_DS1286=m
CONFIG_RTC_DRV_DS1511=m
CONFIG_RTC_DRV_DS1553=m
CONFIG_RTC_DRV_DS1742=m
CONFIG_RTC_DRV_STK17TA8=m
CONFIG_RTC_DRV_M48T86=m
CONFIG_RTC_DRV_M48T35=m
CONFIG_RTC_DRV_M48T59=m
# CONFIG_RTC_DRV_MSM6242 is not set
CONFIG_RTC_DRV_BQ4802=m
# CONFIG_RTC_DRV_RP5C01 is not set
CONFIG_RTC_DRV_V3020=m
CONFIG_RTC_DRV_PCF50633=m

#
# on-CPU RTC drivers
#
# CONFIG_RTC_DRV_MC13783 is not set
CONFIG_DMADEVICES=y
# CONFIG_DMADEVICES_DEBUG is not set

#
# DMA Devices
#
CONFIG_ASYNC_TX_DISABLE_CHANNEL_SWITCH=y
CONFIG_INTEL_IOATDMA=m
# CONFIG_TIMB_DMA is not set
CONFIG_DMA_ENGINE=y

#
# DMA Clients
#
CONFIG_NET_DMA=y
CONFIG_ASYNC_TX_DMA=y
# CONFIG_DMATEST is not set
CONFIG_DCA=m
CONFIG_AUXDISPLAY=y
CONFIG_KS0108=m
CONFIG_KS0108_PORT=0x378
CONFIG_KS0108_DELAY=2
CONFIG_CFAG12864B=m
CONFIG_CFAG12864B_RATE=20
CONFIG_UIO=m
CONFIG_UIO_CIF=m
CONFIG_UIO_PDRV=m
CONFIG_UIO_PDRV_GENIRQ=m
CONFIG_UIO_AEC=m
CONFIG_UIO_SERCOS3=m
CONFIG_UIO_PCI_GENERIC=m
# CONFIG_UIO_NETX is not set
CONFIG_STAGING=y
# CONFIG_STAGING_EXCLUDE_BUILD is not set
CONFIG_ET131X=m
# CONFIG_ET131X_DEBUG is not set
CONFIG_SLICOSS=m
CONFIG_VIDEO_GO7007=m
CONFIG_VIDEO_GO7007_USB=m
CONFIG_VIDEO_GO7007_USB_S2250_BOARD=m
CONFIG_VIDEO_GO7007_OV7640=m
CONFIG_VIDEO_GO7007_SAA7113=m
CONFIG_VIDEO_GO7007_SAA7115=m
CONFIG_VIDEO_GO7007_TW9903=m
CONFIG_VIDEO_GO7007_UDA1342=m
CONFIG_VIDEO_GO7007_SONY_TUNER=m
CONFIG_VIDEO_GO7007_TW2804=m
CONFIG_VIDEO_CX25821=m
CONFIG_VIDEO_CX25821_ALSA=m
# CONFIG_VIDEO_TM6000 is not set
CONFIG_USB_IP_COMMON=m
CONFIG_USB_IP_VHCI_HCD=m
CONFIG_USB_IP_HOST=m
# CONFIG_USB_IP_DEBUG_ENABLE is not set
CONFIG_W35UND=m
CONFIG_PRISM2_USB=m
CONFIG_ECHO=m
# CONFIG_OTUS is not set
CONFIG_RT2860=m
CONFIG_RT2870=m
CONFIG_COMEDI=m
# CONFIG_COMEDI_DEBUG is not set
# CONFIG_COMEDI_MISC_DRIVERS is not set
# CONFIG_COMEDI_ISA_DRIVERS is not set
CONFIG_COMEDI_PCI_DRIVERS=m
# CONFIG_COMEDI_ADDI_APCI_035 is not set
# CONFIG_COMEDI_ADDI_APCI_1032 is not set
# CONFIG_COMEDI_ADDI_APCI_1500 is not set
# CONFIG_COMEDI_ADDI_APCI_1516 is not set
# CONFIG_COMEDI_ADDI_APCI_1564 is not set
# CONFIG_COMEDI_ADDI_APCI_16XX is not set
# CONFIG_COMEDI_ADDI_APCI_2016 is not set
# CONFIG_COMEDI_ADDI_APCI_2032 is not set
# CONFIG_COMEDI_ADDI_APCI_2200 is not set
# CONFIG_COMEDI_ADDI_APCI_3001 is not set
# CONFIG_COMEDI_ADDI_APCI_3120 is not set
# CONFIG_COMEDI_ADDI_APCI_3501 is not set
# CONFIG_COMEDI_ADDI_APCI_3XXX is not set
# CONFIG_COMEDI_ADL_PCI6208 is not set
# CONFIG_COMEDI_ADL_PCI7230 is not set
# CONFIG_COMEDI_ADL_PCI7296 is not set
# CONFIG_COMEDI_ADL_PCI7432 is not set
# CONFIG_COMEDI_ADL_PCI8164 is not set
# CONFIG_COMEDI_ADL_PCI9111 is not set
# CONFIG_COMEDI_ADL_PCI9118 is not set
# CONFIG_COMEDI_ADV_PCI1710 is not set
# CONFIG_COMEDI_ADV_PCI1723 is not set
# CONFIG_COMEDI_ADV_PCI_DIO is not set
# CONFIG_COMEDI_AMPLC_DIO200 is not set
# CONFIG_COMEDI_AMPLC_PC236 is not set
# CONFIG_COMEDI_AMPLC_PC263 is not set
# CONFIG_COMEDI_AMPLC_PCI224 is not set
# CONFIG_COMEDI_AMPLC_PCI230 is not set
# CONFIG_COMEDI_CONTEC_PCI_DIO is not set
# CONFIG_COMEDI_DT3000 is not set
# CONFIG_COMEDI_UNIOXX5 is not set
# CONFIG_COMEDI_GSC_HPDI is not set
# CONFIG_COMEDI_ICP_MULTI is not set
# CONFIG_COMEDI_II_PCI20KC is not set
# CONFIG_COMEDI_DAQBOARD2000 is not set
# CONFIG_COMEDI_JR3_PCI is not set
# CONFIG_COMEDI_KE_COUNTER is not set
# CONFIG_COMEDI_CB_PCIDAS64 is not set
# CONFIG_COMEDI_CB_PCIDAS is not set
# CONFIG_COMEDI_CB_PCIDDA is not set
# CONFIG_COMEDI_CB_PCIDIO is not set
# CONFIG_COMEDI_CB_PCIMDAS is not set
# CONFIG_COMEDI_CB_PCIMDDA is not set
# CONFIG_COMEDI_ME4000 is not set
# CONFIG_COMEDI_ME_DAQ is not set
# CONFIG_COMEDI_RTD520 is not set
# CONFIG_COMEDI_S526 is not set
# CONFIG_COMEDI_S626 is not set
# CONFIG_COMEDI_SSV_DNP is not set
CONFIG_COMEDI_PCMCIA_DRIVERS=m
# CONFIG_COMEDI_CB_DAS16_CS is not set
# CONFIG_COMEDI_DAS08_CS is not set
# CONFIG_COMEDI_QUATECH_DAQP_CS is not set
CONFIG_COMEDI_USB_DRIVERS=m
# CONFIG_COMEDI_DT9812 is not set
# CONFIG_COMEDI_USBDUX is not set
# CONFIG_COMEDI_USBDUXFAST is not set
# CONFIG_COMEDI_VMK80XX is not set
# CONFIG_COMEDI_NI_COMMON is not set
# CONFIG_COMEDI_8255 is not set
# CONFIG_COMEDI_DAS08 is not set
# CONFIG_COMEDI_FC is not set
CONFIG_ASUS_OLED=m
CONFIG_PANEL=m
CONFIG_PANEL_PARPORT=0
CONFIG_PANEL_PROFILE=5
# CONFIG_PANEL_CHANGE_MESSAGE is not set
# CONFIG_R8187SE is not set
CONFIG_RTL8192SU=m
# CONFIG_RTL8192U is not set
CONFIG_RTL8192E=m
CONFIG_TRANZPORT=m
CONFIG_POHMELFS=m
# CONFIG_POHMELFS_DEBUG is not set
CONFIG_POHMELFS_CRYPTO=y
CONFIG_IDE_PHISON=m
CONFIG_LINE6_USB=m
# CONFIG_DRM_VMWGFX is not set
CONFIG_DRM_NOUVEAU=m
CONFIG_DRM_NOUVEAU_BACKLIGHT=y
CONFIG_DRM_NOUVEAU_DEBUG=y

#
# I2C encoder or helper chips
#
CONFIG_DRM_I2C_CH7006=m
CONFIG_USB_SERIAL_QUATECH2=m
CONFIG_USB_SERIAL_QUATECH_USB2=m
# CONFIG_VT6655 is not set
CONFIG_VT6656=m
CONFIG_FB_UDL=m
CONFIG_HYPERV=m
CONFIG_HYPERV_STORAGE=m
CONFIG_HYPERV_BLOCK=m
CONFIG_HYPERV_NET=m
CONFIG_HYPERV_UTILS=m
CONFIG_VME_BUS=m

#
# VME Bridge Drivers
#
CONFIG_VME_CA91CX42=m
CONFIG_VME_TSI148=m

#
# VME Device Drivers
#
CONFIG_VME_USER=m

#
# VME Board Drivers
#
# CONFIG_VMIVME_7805 is not set

#
# RAR Register Driver
#
CONFIG_RAR_REGISTER=m
# CONFIG_MRST_RAR_HANDLER is not set
CONFIG_DX_SEP=m
CONFIG_IIO=m
CONFIG_IIO_RING_BUFFER=y
CONFIG_IIO_SW_RING=m
CONFIG_IIO_TRIGGER=y

#
# Accelerometers
#
# CONFIG_ADIS16209 is not set
# CONFIG_ADIS16220 is not set
# CONFIG_ADIS16240 is not set
CONFIG_KXSD9=m
CONFIG_LIS3L02DQ=m
# CONFIG_SCA3000 is not set

#
# Analog to digital convertors
#
CONFIG_MAX1363=m
CONFIG_MAX1363_RING_BUFFER=y

#
# Digital gyroscope sensors
#
# CONFIG_ADIS16260 is not set

#
# Inertial measurement units
#
# CONFIG_ADIS16300 is not set
# CONFIG_ADIS16350 is not set
# CONFIG_ADIS16400 is not set

#
# Light sensors
#
# CONFIG_SENSORS_TSL2563 is not set

#
# Triggers - standalone
#
# CONFIG_IIO_PERIODIC_RTC_TRIGGER is not set
# CONFIG_IIO_GPIO_TRIGGER is not set
# CONFIG_RAMZSWAP is not set
# CONFIG_WLAGS49_H2 is not set
# CONFIG_WLAGS49_H25 is not set
# CONFIG_BATMAN_ADV is not set
# CONFIG_SAMSUNG_LAPTOP is not set
# CONFIG_FB_SM7XX is not set
# CONFIG_DT3155 is not set
# CONFIG_VIDEO_DT3155 is not set
# CONFIG_CRYSTALHD is not set
# CONFIG_CXT1E1 is not set

#
# Texas Instruments shared transport line discipline
#
# CONFIG_TI_ST is not set
# CONFIG_ST_BT is not set
# CONFIG_ADIS16255 is not set
# CONFIG_FB_XGI is not set
CONFIG_TOUCHSCREEN_INTEL_MID=y
CONFIG_X86_PLATFORM_DEVICES=y
CONFIG_ACER_WMI=m
CONFIG_ACERHDF=m
CONFIG_ASUS_LAPTOP=m
CONFIG_DELL_LAPTOP=m
CONFIG_DELL_WMI=m
CONFIG_FUJITSU_LAPTOP=m
# CONFIG_FUJITSU_LAPTOP_DEBUG is not set
CONFIG_TC1100_WMI=m
CONFIG_HP_WMI=m
CONFIG_MSI_LAPTOP=m
CONFIG_PANASONIC_LAPTOP=m
CONFIG_COMPAL_LAPTOP=m
CONFIG_SONY_LAPTOP=m
CONFIG_SONYPI_COMPAT=y
CONFIG_THINKPAD_ACPI=m
CONFIG_THINKPAD_ACPI_ALSA_SUPPORT=y
CONFIG_THINKPAD_ACPI_DEBUGFACILITIES=y
# CONFIG_THINKPAD_ACPI_DEBUG is not set
# CONFIG_THINKPAD_ACPI_UNSAFE_LEDS is not set
CONFIG_THINKPAD_ACPI_VIDEO=y
CONFIG_THINKPAD_ACPI_HOTKEY_POLL=y
CONFIG_INTEL_MENLOW=m
CONFIG_EEEPC_LAPTOP=m
# CONFIG_EEEPC_WMI is not set
CONFIG_ACPI_WMI=y
# CONFIG_MSI_WMI is not set
# CONFIG_ACPI_ASUS is not set
CONFIG_TOPSTAR_LAPTOP=m
CONFIG_ACPI_TOSHIBA=m
# CONFIG_TOSHIBA_BT_RFKILL is not set
# CONFIG_ACPI_CMPC is not set
CONFIG_INTEL_SCU_IPC=y

#
# Firmware Drivers
#
CONFIG_EDD=y
CONFIG_EDD_OFF=y
CONFIG_FIRMWARE_MEMMAP=y
CONFIG_EFI_VARS=y
CONFIG_DELL_RBU=m
CONFIG_DCDBAS=m
CONFIG_DMIID=y
CONFIG_ISCSI_IBFT_FIND=y
CONFIG_ISCSI_IBFT=m

#
# File systems
#
CONFIG_EXT2_FS=y
CONFIG_EXT2_FS_XATTR=y
CONFIG_EXT2_FS_POSIX_ACL=y
CONFIG_EXT2_FS_SECURITY=y
# CONFIG_EXT2_FS_XIP is not set
CONFIG_EXT3_FS=y
CONFIG_EXT3_DEFAULTS_TO_ORDERED=y
CONFIG_EXT3_FS_XATTR=y
CONFIG_EXT3_FS_POSIX_ACL=y
CONFIG_EXT3_FS_SECURITY=y
CONFIG_EXT4_FS=y
CONFIG_EXT4_FS_XATTR=y
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
# CONFIG_EXT4_DEBUG is not set
CONFIG_JBD=y
# CONFIG_JBD_DEBUG is not set
CONFIG_JBD2=y
# CONFIG_JBD2_DEBUG is not set
CONFIG_FS_MBCACHE=y
CONFIG_REISERFS_FS=m
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y
CONFIG_JFS_FS=m
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
# CONFIG_JFS_DEBUG is not set
CONFIG_JFS_STATISTICS=y
CONFIG_FS_POSIX_ACL=y
CONFIG_XFS_FS=m
CONFIG_XFS_QUOTA=y
CONFIG_XFS_POSIX_ACL=y
CONFIG_XFS_RT=y
# CONFIG_XFS_DEBUG is not set
CONFIG_GFS2_FS=m
CONFIG_GFS2_FS_LOCKING_DLM=y
CONFIG_OCFS2_FS=m
CONFIG_OCFS2_FS_O2CB=m
CONFIG_OCFS2_FS_USERSPACE_CLUSTER=m
CONFIG_OCFS2_FS_STATS=y
CONFIG_OCFS2_DEBUG_MASKLOG=y
# CONFIG_OCFS2_DEBUG_FS is not set
CONFIG_BTRFS_FS=m
CONFIG_BTRFS_FS_POSIX_ACL=y
CONFIG_NILFS2_FS=m
CONFIG_FILE_LOCKING=y
CONFIG_FSNOTIFY=y
CONFIG_DNOTIFY=y
CONFIG_INOTIFY=y
CONFIG_INOTIFY_USER=y
CONFIG_QUOTA=y
CONFIG_QUOTA_NETLINK_INTERFACE=y
# CONFIG_PRINT_QUOTA_WARNING is not set
# CONFIG_QUOTA_DEBUG is not set
CONFIG_QUOTA_TREE=m
CONFIG_QFMT_V1=m
CONFIG_QFMT_V2=m
CONFIG_QUOTACTL=y
CONFIG_AUTOFS_FS=m
CONFIG_AUTOFS4_FS=m
CONFIG_FUSE_FS=y
CONFIG_CUSE=m
CONFIG_GENERIC_ACL=y

#
# Caches
#
CONFIG_FSCACHE=m
# CONFIG_FSCACHE_STATS is not set
# CONFIG_FSCACHE_HISTOGRAM is not set
# CONFIG_FSCACHE_DEBUG is not set
# CONFIG_FSCACHE_OBJECT_LIST is not set
CONFIG_CACHEFILES=m
# CONFIG_CACHEFILES_DEBUG is not set
# CONFIG_CACHEFILES_HISTOGRAM is not set

#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=m
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_UDF_FS=m
CONFIG_UDF_NLS=y

#
# DOS/FAT/NT Filesystems
#
CONFIG_FAT_FS=m
CONFIG_MSDOS_FS=m
CONFIG_VFAT_FS=m
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="iso8859-1"
CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
# CONFIG_NTFS_RW is not set

#
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_PROC_VMCORE=y
CONFIG_PROC_SYSCTL=y
CONFIG_PROC_PAGE_MONITOR=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
CONFIG_TMPFS_POSIX_ACL=y
CONFIG_HUGETLBFS=y
CONFIG_HUGETLB_PAGE=y
CONFIG_CONFIGFS_FS=m
CONFIG_MISC_FILESYSTEMS=y
CONFIG_ADFS_FS=m
# CONFIG_ADFS_FS_RW is not set
CONFIG_AFFS_FS=m
CONFIG_ECRYPT_FS=y
CONFIG_HFS_FS=m
CONFIG_HFSPLUS_FS=m
CONFIG_BEFS_FS=m
# CONFIG_BEFS_DEBUG is not set
CONFIG_BFS_FS=m
CONFIG_EFS_FS=m
CONFIG_JFFS2_FS=m
CONFIG_JFFS2_FS_DEBUG=0
CONFIG_JFFS2_FS_WRITEBUFFER=y
# CONFIG_JFFS2_FS_WBUF_VERIFY is not set
# CONFIG_JFFS2_SUMMARY is not set
# CONFIG_JFFS2_FS_XATTR is not set
CONFIG_JFFS2_COMPRESSION_OPTIONS=y
CONFIG_JFFS2_ZLIB=y
CONFIG_JFFS2_LZO=y
CONFIG_JFFS2_RTIME=y
# CONFIG_JFFS2_RUBIN is not set
# CONFIG_JFFS2_CMODE_NONE is not set
# CONFIG_JFFS2_CMODE_PRIORITY is not set
# CONFIG_JFFS2_CMODE_SIZE is not set
CONFIG_JFFS2_CMODE_FAVOURLZO=y
CONFIG_UBIFS_FS=m
CONFIG_UBIFS_FS_XATTR=y
# CONFIG_UBIFS_FS_ADVANCED_COMPR is not set
CONFIG_UBIFS_FS_LZO=y
CONFIG_UBIFS_FS_ZLIB=y
# CONFIG_UBIFS_FS_DEBUG is not set
# CONFIG_LOGFS is not set
CONFIG_CRAMFS=m
CONFIG_SQUASHFS=m
# CONFIG_SQUASHFS_XATTRS is not set
# CONFIG_SQUASHFS_EMBEDDED is not set
CONFIG_SQUASHFS_FRAGMENT_CACHE_SIZE=3
CONFIG_VXFS_FS=m
CONFIG_MINIX_FS=m
CONFIG_OMFS_FS=m
CONFIG_HPFS_FS=m
CONFIG_QNX4FS_FS=m
CONFIG_ROMFS_FS=m
CONFIG_ROMFS_BACKED_BY_BLOCK=y
# CONFIG_ROMFS_BACKED_BY_MTD is not set
# CONFIG_ROMFS_BACKED_BY_BOTH is not set
CONFIG_ROMFS_ON_BLOCK=y
CONFIG_SYSV_FS=m
CONFIG_UFS_FS=m
# CONFIG_UFS_FS_WRITE is not set
# CONFIG_UFS_DEBUG is not set
CONFIG_EXOFS_FS=m
# CONFIG_EXOFS_DEBUG is not set
CONFIG_NETWORK_FILESYSTEMS=y
CONFIG_NFS_FS=m
CONFIG_NFS_V3=y
CONFIG_NFS_V3_ACL=y
CONFIG_NFS_V4=y
# CONFIG_NFS_V4_1 is not set
# CONFIG_NFS_FSCACHE is not set
CONFIG_NFSD=m
CONFIG_NFSD_V2_ACL=y
CONFIG_NFSD_V3=y
CONFIG_NFSD_V3_ACL=y
CONFIG_NFSD_V4=y
CONFIG_LOCKD=m
CONFIG_LOCKD_V4=y
CONFIG_EXPORTFS=m
CONFIG_NFS_ACL_SUPPORT=m
CONFIG_NFS_COMMON=y
CONFIG_SUNRPC=m
CONFIG_SUNRPC_GSS=m
CONFIG_SUNRPC_XPRT_RDMA=m
CONFIG_RPCSEC_GSS_KRB5=m
CONFIG_RPCSEC_GSS_SPKM3=m
CONFIG_SMB_FS=m
# CONFIG_SMB_NLS_DEFAULT is not set
# CONFIG_CEPH_FS is not set
CONFIG_CIFS=m
# CONFIG_CIFS_STATS is not set
CONFIG_CIFS_WEAK_PW_HASH=y
CONFIG_CIFS_UPCALL=y
CONFIG_CIFS_XATTR=y
CONFIG_CIFS_POSIX=y
# CONFIG_CIFS_DEBUG2 is not set
CONFIG_CIFS_DFS_UPCALL=y
CONFIG_CIFS_EXPERIMENTAL=y
CONFIG_NCP_FS=m
CONFIG_NCPFS_PACKET_SIGNING=y
CONFIG_NCPFS_IOCTL_LOCKING=y
CONFIG_NCPFS_STRONG=y
CONFIG_NCPFS_NFS_NS=y
CONFIG_NCPFS_OS2_NS=y
# CONFIG_NCPFS_SMALLDOS is not set
CONFIG_NCPFS_NLS=y
CONFIG_NCPFS_EXTRAS=y
CONFIG_CODA_FS=m
CONFIG_AFS_FS=m
# CONFIG_AFS_DEBUG is not set
# CONFIG_AFS_FSCACHE is not set
CONFIG_9P_FS=m
# CONFIG_9P_FSCACHE is not set

#
# Partition Types
#
CONFIG_PARTITION_ADVANCED=y
CONFIG_ACORN_PARTITION=y
# CONFIG_ACORN_PARTITION_CUMANA is not set
# CONFIG_ACORN_PARTITION_EESOX is not set
CONFIG_ACORN_PARTITION_ICS=y
# CONFIG_ACORN_PARTITION_ADFS is not set
# CONFIG_ACORN_PARTITION_POWERTEC is not set
CONFIG_ACORN_PARTITION_RISCIX=y
CONFIG_OSF_PARTITION=y
CONFIG_AMIGA_PARTITION=y
CONFIG_ATARI_PARTITION=y
CONFIG_MAC_PARTITION=y
CONFIG_MSDOS_PARTITION=y
CONFIG_BSD_DISKLABEL=y
CONFIG_MINIX_SUBPARTITION=y
CONFIG_SOLARIS_X86_PARTITION=y
CONFIG_UNIXWARE_DISKLABEL=y
CONFIG_LDM_PARTITION=y
# CONFIG_LDM_DEBUG is not set
CONFIG_SGI_PARTITION=y
CONFIG_ULTRIX_PARTITION=y
CONFIG_SUN_PARTITION=y
CONFIG_KARMA_PARTITION=y
CONFIG_EFI_PARTITION=y
CONFIG_SYSV68_PARTITION=y
CONFIG_NLS=y
CONFIG_NLS_DEFAULT="cp437"
CONFIG_NLS_CODEPAGE_437=m
CONFIG_NLS_CODEPAGE_737=m
CONFIG_NLS_CODEPAGE_775=m
CONFIG_NLS_CODEPAGE_850=m
CONFIG_NLS_CODEPAGE_852=m
CONFIG_NLS_CODEPAGE_855=m
CONFIG_NLS_CODEPAGE_857=m
CONFIG_NLS_CODEPAGE_860=m
CONFIG_NLS_CODEPAGE_861=m
CONFIG_NLS_CODEPAGE_862=m
CONFIG_NLS_CODEPAGE_863=m
CONFIG_NLS_CODEPAGE_864=m
CONFIG_NLS_CODEPAGE_865=m
CONFIG_NLS_CODEPAGE_866=m
CONFIG_NLS_CODEPAGE_869=m
CONFIG_NLS_CODEPAGE_936=m
CONFIG_NLS_CODEPAGE_950=m
CONFIG_NLS_CODEPAGE_932=m
CONFIG_NLS_CODEPAGE_949=m
CONFIG_NLS_CODEPAGE_874=m
CONFIG_NLS_ISO8859_8=m
CONFIG_NLS_CODEPAGE_1250=m
CONFIG_NLS_CODEPAGE_1251=m
CONFIG_NLS_ASCII=m
CONFIG_NLS_ISO8859_1=m
CONFIG_NLS_ISO8859_2=m
CONFIG_NLS_ISO8859_3=m
CONFIG_NLS_ISO8859_4=m
CONFIG_NLS_ISO8859_5=m
CONFIG_NLS_ISO8859_6=m
CONFIG_NLS_ISO8859_7=m
CONFIG_NLS_ISO8859_9=m
CONFIG_NLS_ISO8859_13=m
CONFIG_NLS_ISO8859_14=m
CONFIG_NLS_ISO8859_15=m
CONFIG_NLS_KOI8_R=m
CONFIG_NLS_KOI8_U=m
CONFIG_NLS_UTF8=m
CONFIG_DLM=m
# CONFIG_DLM_DEBUG is not set

#
# Kernel hacking
#
CONFIG_TRACE_IRQFLAGS_SUPPORT=y
CONFIG_PRINTK_TIME=y
# CONFIG_ENABLE_WARN_DEPRECATED is not set
# CONFIG_ENABLE_MUST_CHECK is not set
CONFIG_FRAME_WARN=1024
CONFIG_MAGIC_SYSRQ=y
# CONFIG_STRIP_ASM_SYMS is not set
CONFIG_UNUSED_SYMBOLS=y
CONFIG_DEBUG_FS=y
# CONFIG_HEADERS_CHECK is not set
CONFIG_DEBUG_KERNEL=y
# CONFIG_DEBUG_SHIRQ is not set
CONFIG_DETECT_SOFTLOCKUP=y
# CONFIG_BOOTPARAM_SOFTLOCKUP_PANIC is not set
CONFIG_BOOTPARAM_SOFTLOCKUP_PANIC_VALUE=0
CONFIG_DETECT_HUNG_TASK=y
# CONFIG_BOOTPARAM_HUNG_TASK_PANIC is not set
CONFIG_BOOTPARAM_HUNG_TASK_PANIC_VALUE=0
CONFIG_SCHED_DEBUG=y
CONFIG_SCHEDSTATS=y
CONFIG_TIMER_STATS=y
# CONFIG_DEBUG_OBJECTS is not set
# CONFIG_SLUB_DEBUG_ON is not set
# CONFIG_SLUB_STATS is not set
# CONFIG_DEBUG_KMEMLEAK is not set
# CONFIG_DEBUG_RT_MUTEXES is not set
# CONFIG_RT_MUTEX_TESTER is not set
# CONFIG_DEBUG_SPINLOCK is not set
# CONFIG_DEBUG_MUTEXES is not set
# CONFIG_DEBUG_LOCK_ALLOC is not set
# CONFIG_PROVE_LOCKING is not set
# CONFIG_LOCK_STAT is not set
# CONFIG_DEBUG_SPINLOCK_SLEEP is not set
# CONFIG_DEBUG_LOCKING_API_SELFTESTS is not set
CONFIG_STACKTRACE=y
# CONFIG_DEBUG_KOBJECT is not set
# CONFIG_DEBUG_HIGHMEM is not set
CONFIG_DEBUG_BUGVERBOSE=y
CONFIG_DEBUG_INFO=y
# CONFIG_DEBUG_VM is not set
# CONFIG_DEBUG_VIRTUAL is not set
# CONFIG_DEBUG_WRITECOUNT is not set
CONFIG_DEBUG_MEMORY_INIT=y
# CONFIG_DEBUG_LIST is not set
# CONFIG_DEBUG_SG is not set
# CONFIG_DEBUG_NOTIFIERS is not set
# CONFIG_DEBUG_CREDENTIALS is not set
CONFIG_ARCH_WANT_FRAME_POINTERS=y
CONFIG_FRAME_POINTER=y
# CONFIG_BOOT_PRINTK_DELAY is not set
# CONFIG_RCU_TORTURE_TEST is not set
# CONFIG_RCU_CPU_STALL_DETECTOR is not set
# CONFIG_KPROBES_SANITY_TEST is not set
# CONFIG_BACKTRACE_SELF_TEST is not set
# CONFIG_DEBUG_BLOCK_EXT_DEVT is not set
# CONFIG_DEBUG_FORCE_WEAK_PER_CPU is not set
# CONFIG_LKDTM is not set
# CONFIG_CPU_NOTIFIER_ERROR_INJECT is not set
# CONFIG_FAULT_INJECTION is not set
CONFIG_LATENCYTOP=y
CONFIG_SYSCTL_SYSCALL_CHECK=y
# CONFIG_DEBUG_PAGEALLOC is not set
CONFIG_USER_STACKTRACE_SUPPORT=y
CONFIG_NOP_TRACER=y
CONFIG_HAVE_FTRACE_NMI_ENTER=y
CONFIG_HAVE_FUNCTION_TRACER=y
CONFIG_HAVE_FUNCTION_GRAPH_TRACER=y
CONFIG_HAVE_FUNCTION_GRAPH_FP_TEST=y
CONFIG_HAVE_FUNCTION_TRACE_MCOUNT_TEST=y
CONFIG_HAVE_DYNAMIC_FTRACE=y
CONFIG_HAVE_FTRACE_MCOUNT_RECORD=y
CONFIG_HAVE_SYSCALL_TRACEPOINTS=y
CONFIG_RING_BUFFER=y
CONFIG_FTRACE_NMI_ENTER=y
CONFIG_EVENT_TRACING=y
CONFIG_CONTEXT_SWITCH_TRACER=y
CONFIG_RING_BUFFER_ALLOW_SWAP=y
CONFIG_TRACING=y
CONFIG_GENERIC_TRACER=y
CONFIG_TRACING_SUPPORT=y
CONFIG_FTRACE=y
CONFIG_FUNCTION_TRACER=y
CONFIG_FUNCTION_GRAPH_TRACER=y
# CONFIG_IRQSOFF_TRACER is not set
# CONFIG_SYSPROF_TRACER is not set
# CONFIG_SCHED_TRACER is not set
# CONFIG_FTRACE_SYSCALLS is not set
# CONFIG_BOOT_TRACER is not set
CONFIG_BRANCH_PROFILE_NONE=y
# CONFIG_PROFILE_ANNOTATED_BRANCHES is not set
# CONFIG_PROFILE_ALL_BRANCHES is not set
# CONFIG_KSYM_TRACER is not set
# CONFIG_STACK_TRACER is not set
# CONFIG_KMEMTRACE is not set
# CONFIG_WORKQUEUE_TRACER is not set
CONFIG_BLK_DEV_IO_TRACE=y
CONFIG_KPROBE_EVENT=y
CONFIG_DYNAMIC_FTRACE=y
CONFIG_FUNCTION_PROFILER=y
CONFIG_FTRACE_MCOUNT_RECORD=y
# CONFIG_FTRACE_STARTUP_TEST is not set
CONFIG_MMIOTRACE=y
# CONFIG_MMIOTRACE_TEST is not set
# CONFIG_RING_BUFFER_BENCHMARK is not set
# CONFIG_PROVIDE_OHCI1394_DMA_INIT is not set
# CONFIG_FIREWIRE_OHCI_REMOTE_DMA is not set
# CONFIG_DYNAMIC_DEBUG is not set
# CONFIG_DMA_API_DEBUG is not set
# CONFIG_ATOMIC64_SELFTEST is not set
# CONFIG_SAMPLES is not set
CONFIG_HAVE_ARCH_KGDB=y
CONFIG_KGDB=y
CONFIG_KGDB_SERIAL_CONSOLE=y
# CONFIG_KGDB_TESTS is not set
# CONFIG_KGDB_LOW_LEVEL_TRAP is not set
# CONFIG_KGDB_KDB is not set
CONFIG_HAVE_ARCH_KMEMCHECK=y
CONFIG_STRICT_DEVMEM=y
# CONFIG_X86_VERBOSE_BOOTUP is not set
CONFIG_EARLY_PRINTK=y
# CONFIG_EARLY_PRINTK_DBGP is not set
# CONFIG_DEBUG_STACKOVERFLOW is not set
# CONFIG_DEBUG_STACK_USAGE is not set
# CONFIG_DEBUG_PER_CPU_MAPS is not set
# CONFIG_X86_PTDUMP is not set
CONFIG_DEBUG_RODATA=y
# CONFIG_DEBUG_RODATA_TEST is not set
# CONFIG_DEBUG_NX_TEST is not set
# CONFIG_4KSTACKS is not set
CONFIG_DOUBLEFAULT=y
# CONFIG_IOMMU_STRESS is not set
CONFIG_HAVE_MMIOTRACE_SUPPORT=y
# CONFIG_X86_DECODER_SELFTEST is not set
CONFIG_IO_DELAY_TYPE_0X80=0
CONFIG_IO_DELAY_TYPE_0XED=1
CONFIG_IO_DELAY_TYPE_UDELAY=2
CONFIG_IO_DELAY_TYPE_NONE=3
# CONFIG_IO_DELAY_0X80 is not set
CONFIG_IO_DELAY_0XED=y
# CONFIG_IO_DELAY_UDELAY is not set
# CONFIG_IO_DELAY_NONE is not set
CONFIG_DEFAULT_IO_DELAY_TYPE=1
# CONFIG_DEBUG_BOOT_PARAMS is not set
# CONFIG_CPA_DEBUG is not set
CONFIG_OPTIMIZE_INLINING=y
# CONFIG_DEBUG_STRICT_USER_COPY_CHECKS is not set

#
# Security options
#
CONFIG_KEYS=y
# CONFIG_KEYS_DEBUG_PROC_KEYS is not set
CONFIG_SECURITY=y
CONFIG_SECURITYFS=y
CONFIG_SECURITY_NETWORK=y
# CONFIG_SECURITY_NETWORK_XFRM is not set
CONFIG_SECURITY_PATH=y
CONFIG_LSM_MMAP_MIN_ADDR=0
CONFIG_SECURITY_SELINUX=y
CONFIG_SECURITY_SELINUX_BOOTPARAM=y
CONFIG_SECURITY_SELINUX_BOOTPARAM_VALUE=0
CONFIG_SECURITY_SELINUX_DISABLE=y
CONFIG_SECURITY_SELINUX_DEVELOP=y
CONFIG_SECURITY_SELINUX_AVC_STATS=y
CONFIG_SECURITY_SELINUX_CHECKREQPROT_VALUE=1
# CONFIG_SECURITY_SELINUX_POLICYDB_VERSION_MAX is not set
CONFIG_SECURITY_SMACK=y
CONFIG_SECURITY_TOMOYO=y
# CONFIG_IMA is not set
CONFIG_DEFAULT_SECURITY_SELINUX=y
# CONFIG_DEFAULT_SECURITY_SMACK is not set
# CONFIG_DEFAULT_SECURITY_TOMOYO is not set
# CONFIG_DEFAULT_SECURITY_DAC is not set
CONFIG_DEFAULT_SECURITY="selinux"
CONFIG_XOR_BLOCKS=m
CONFIG_ASYNC_CORE=m
CONFIG_ASYNC_MEMCPY=m
CONFIG_ASYNC_XOR=m
CONFIG_ASYNC_PQ=m
CONFIG_ASYNC_RAID6_RECOV=m
CONFIG_ASYNC_TX_DISABLE_PQ_VAL_DMA=y
CONFIG_ASYNC_TX_DISABLE_XOR_VAL_DMA=y
CONFIG_CRYPTO=y

#
# Crypto core or helper
#
CONFIG_CRYPTO_FIPS=y
CONFIG_CRYPTO_ALGAPI=y
CONFIG_CRYPTO_ALGAPI2=y
CONFIG_CRYPTO_AEAD=m
CONFIG_CRYPTO_AEAD2=y
CONFIG_CRYPTO_BLKCIPHER=y
CONFIG_CRYPTO_BLKCIPHER2=y
CONFIG_CRYPTO_HASH=y
CONFIG_CRYPTO_HASH2=y
CONFIG_CRYPTO_RNG=m
CONFIG_CRYPTO_RNG2=y
CONFIG_CRYPTO_PCOMP=y
CONFIG_CRYPTO_MANAGER=y
CONFIG_CRYPTO_MANAGER2=y
CONFIG_CRYPTO_GF128MUL=m
CONFIG_CRYPTO_NULL=m
# CONFIG_CRYPTO_PCRYPT is not set
CONFIG_CRYPTO_WORKQUEUE=y
CONFIG_CRYPTO_CRYPTD=m
CONFIG_CRYPTO_AUTHENC=m
CONFIG_CRYPTO_TEST=m

#
# Authenticated Encryption with Associated Data
#
CONFIG_CRYPTO_CCM=m
CONFIG_CRYPTO_GCM=m
CONFIG_CRYPTO_SEQIV=m

#
# Block modes
#
CONFIG_CRYPTO_CBC=y
CONFIG_CRYPTO_CTR=m
CONFIG_CRYPTO_CTS=m
CONFIG_CRYPTO_ECB=y
CONFIG_CRYPTO_LRW=m
CONFIG_CRYPTO_PCBC=m
CONFIG_CRYPTO_XTS=m

#
# Hash modes
#
CONFIG_CRYPTO_HMAC=y
CONFIG_CRYPTO_XCBC=m
CONFIG_CRYPTO_VMAC=m

#
# Digest
#
CONFIG_CRYPTO_CRC32C=m
CONFIG_CRYPTO_CRC32C_INTEL=m
CONFIG_CRYPTO_GHASH=m
CONFIG_CRYPTO_MD4=m
CONFIG_CRYPTO_MD5=y
CONFIG_CRYPTO_MICHAEL_MIC=m
CONFIG_CRYPTO_RMD128=m
CONFIG_CRYPTO_RMD160=m
CONFIG_CRYPTO_RMD256=m
CONFIG_CRYPTO_RMD320=m
CONFIG_CRYPTO_SHA1=m
CONFIG_CRYPTO_SHA256=m
CONFIG_CRYPTO_SHA512=m
CONFIG_CRYPTO_TGR192=m
CONFIG_CRYPTO_WP512=m

#
# Ciphers
#
CONFIG_CRYPTO_AES=m
CONFIG_CRYPTO_AES_586=m
CONFIG_CRYPTO_ANUBIS=m
CONFIG_CRYPTO_ARC4=m
CONFIG_CRYPTO_BLOWFISH=m
CONFIG_CRYPTO_CAMELLIA=m
CONFIG_CRYPTO_CAST5=m
CONFIG_CRYPTO_CAST6=m
CONFIG_CRYPTO_DES=m
CONFIG_CRYPTO_FCRYPT=m
CONFIG_CRYPTO_KHAZAD=m
CONFIG_CRYPTO_SALSA20=m
CONFIG_CRYPTO_SALSA20_586=m
CONFIG_CRYPTO_SEED=m
CONFIG_CRYPTO_SERPENT=m
CONFIG_CRYPTO_TEA=m
CONFIG_CRYPTO_TWOFISH=m
CONFIG_CRYPTO_TWOFISH_COMMON=m
CONFIG_CRYPTO_TWOFISH_586=m

#
# Compression
#
CONFIG_CRYPTO_DEFLATE=m
CONFIG_CRYPTO_ZLIB=m
CONFIG_CRYPTO_LZO=m

#
# Random Number Generation
#
CONFIG_CRYPTO_ANSI_CPRNG=m
CONFIG_CRYPTO_HW=y
CONFIG_CRYPTO_DEV_PADLOCK=y
CONFIG_CRYPTO_DEV_PADLOCK_AES=m
CONFIG_CRYPTO_DEV_PADLOCK_SHA=m
CONFIG_CRYPTO_DEV_GEODE=m
CONFIG_CRYPTO_DEV_HIFN_795X=m
CONFIG_CRYPTO_DEV_HIFN_795X_RNG=y
CONFIG_HAVE_KVM=y
CONFIG_HAVE_KVM_IRQCHIP=y
CONFIG_HAVE_KVM_EVENTFD=y
CONFIG_KVM_APIC_ARCHITECTURE=y
CONFIG_KVM_MMIO=y
CONFIG_VIRTUALIZATION=y
CONFIG_KVM=m
CONFIG_KVM_INTEL=m
CONFIG_KVM_AMD=m
# CONFIG_VHOST_NET is not set
CONFIG_LGUEST=m
CONFIG_VIRTIO=m
CONFIG_VIRTIO_RING=m
CONFIG_VIRTIO_PCI=m
CONFIG_VIRTIO_BALLOON=m
CONFIG_BINARY_PRINTF=y

#
# Library routines
#
CONFIG_BITREVERSE=y
CONFIG_GENERIC_FIND_FIRST_BIT=y
CONFIG_GENERIC_FIND_NEXT_BIT=y
CONFIG_GENERIC_FIND_LAST_BIT=y
CONFIG_CRC_CCITT=m
CONFIG_CRC16=y
CONFIG_CRC_T10DIF=y
CONFIG_CRC_ITU_T=m
CONFIG_CRC32=y
CONFIG_CRC7=m
CONFIG_LIBCRC32C=m
CONFIG_AUDIT_GENERIC=y
CONFIG_ZLIB_INFLATE=y
CONFIG_ZLIB_DEFLATE=m
CONFIG_LZO_COMPRESS=m
CONFIG_LZO_DECOMPRESS=y
CONFIG_DECOMPRESS_GZIP=y
CONFIG_DECOMPRESS_BZIP2=y
CONFIG_DECOMPRESS_LZMA=y
CONFIG_DECOMPRESS_LZO=y
CONFIG_GENERIC_ALLOCATOR=y
CONFIG_REED_SOLOMON=m
CONFIG_REED_SOLOMON_DEC16=y
CONFIG_TEXTSEARCH=y
CONFIG_TEXTSEARCH_KMP=m
CONFIG_TEXTSEARCH_BM=m
CONFIG_TEXTSEARCH_FSM=m
CONFIG_HAS_IOMEM=y
CONFIG_HAS_IOPORT=y
CONFIG_HAS_DMA=y
CONFIG_CHECK_SIGNATURE=y
CONFIG_NLATTR=y



can anyone help me ?

---

