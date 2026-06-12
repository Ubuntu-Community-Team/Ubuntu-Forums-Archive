---
title: "Recent Updates to Ubuntu 12.04.1 break suspend/sleep"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2013-01-25
I run Ubuntu 12.04.1 on my Dell Latitude D610 laptop.  Sometime within the last month (Jan 2013) I did a normal update.  Now suspend/sleep and hibernate no longer work.  If I close the laptop lid (suspend) the screen goes blank, but the cpu (and fan) continue to run.  When I open the lid, the screen once again is powered and the laptop continues to run.  But obviously this behavior is unacceptable as it exhausts the battery and overheats the laptop if I put it in my backpack. In addition, the cpu mode is always set to "Performace" not to "OnDemand" as it used to be (and should be) set. I have been running Ubuntu for the last 6 years and have never had this problem.  I understand that there is a concerted effort to improve battery life in linux computers, and that linux is now demanding that the bios's strictly follow the interface standard, so I am suspicious that this is the cause of my problem (I don't really know this).  This battery life extension is a noble effort, but if it results in computers that won't run linux, it is a major problem.  I don't understand the boot process and have been unable to fix the problem.

Does anyone else out there running Dell Latitude D610's (or any similar computer) have the same problem?  There are a lot of Dell's out there so I would suspect that somebody else would see this.

Any help is very much appreciated.

Here is dmesg after booting: 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-36-generic-pae (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #57-Ubuntu SMP Tue Jan 8 22:01:06 UTC 2013 (Ubuntu 3.2.0-36.57-generic-pae 3.2.35)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7d1800 (usable)
[    0.000000]  BIOS-e820: 000000003f7d1800 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Dell Inc. Latitude D610                   /0U8082, BIOS A06 10/02/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f7d1 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffa000-2000000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 000fc9b0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 3f7d1f90 00040 (v01 DELL    CPi R   27D50A02 ASL  00000061)
[    0.000000] ACPI: FACP 3f7d2c00 00074 (v01 DELL    CPi R   27D50A02 ASL  00000061)
[    0.000000] ACPI: DSDT 3f7d3800 03C51 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f7e2000 00040
[    0.000000] ACPI: APIC 3f7d3400 00068 (v01 DELL    CPi R   27D50A02 ASL  00000047)
[    0.000000] ACPI: ASF! 3f7d3000 0005B (v16 DELL    CPi R   27D50A02 ASL  00000061)
[    0.000000] ACPI: MCFG 3f7d33c0 0003E (v16 DELL    CPi R   27D50A02 ASL  00000061)
[    0.000000] ACPI: SSDT 3f7d23e6 00280 (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] ACPI: SSDT 3f7d220e 001D8 (v01  PmRef  Cpu0Cst 00003001 INTL 20030522)
[    0.000000] ACPI: SSDT 3f7d2013 001FB (v01  PmRef    CpuPm 00003000 INTL 20030522)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 123MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003f7d1
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f7d1
[    0.000000] On node 0 totalpages: 259936
[    0.000000] free_area_init_node: node 0, pgdat c186b400, node_mem_map f740d200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 248 pages used for memmap
[    0.000000]   HighMem zone: 31451 pages, LIFO batch:7
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73eb000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257904
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-36-generic-pae root=UUID=3d2b3c2c-46e0-45a2-be21-c0d54e6df96f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4160528 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003f7d1)
[    0.000000] Memory: 1002392k/1040196k available (5826k kernel code, 37352k reserved, 2848k data, 744k init, 126796k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1933000   ( 744 kB)
[    0.000000]       .data : 0xc15b0afc - 0xc1878c40   (2848 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b0afc   (5826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1862.025 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3724.05 BogoMIPS (lpj=7448100)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004038] Security Framework initialized
[    0.004064] AppArmor: AppArmor initialized
[    0.004067] Yama: becoming mindful.
[    0.004165] Mount-cache hash table entries: 512
[    0.004353] Initializing cgroup subsys cpuacct
[    0.004361] Initializing cgroup subsys memory
[    0.004373] Initializing cgroup subsys devices
[    0.004377] Initializing cgroup subsys freezer
[    0.004380] Initializing cgroup subsys blkio
[    0.004391] Initializing cgroup subsys perf_event
[    0.004422] Disabled fast string operations
[    0.004430] mce: CPU supports 5 MCE banks
[    0.004440] CPU0: Thermal monitoring enabled (TM1)
[    0.004806] SMP alternatives: switching to UP code
[    0.018422] ACPI: Core revision 20110623
[    0.024014] ftrace: allocating 26584 entries in 53 pages
[    0.028081] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028527] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071252] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    0.072003] Performance Events: p6 PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              32
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             00000000ffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             0000000000000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] Brought up 1 CPUs
[    0.072003] Total of 1 processors activated (3724.05 BogoMIPS).
[    0.072003] devtmpfs: initialized
[    0.072003] EVM: security.selinux
[    0.072003] EVM: security.SMACK64
[    0.072003] EVM: security.capability
[    0.072003] print_constraints: dummy: 
[    0.072003] RTC time: 14:01:14, date: 01/25/13
[    0.072003] NET: Registered protocol family 16
[    0.072003] EISA bus registered
[    0.072003] ACPI: bus type pci registered
[    0.072003] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.072003] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.072003] PCI: Using MMCONFIG for extended config space
[    0.072003] PCI: Using configuration type 1 for base access
[    0.072003] dmi type 0xB1 record - unknown flag
[    0.073409] bio: create slab <bio-0> at 0
[    0.073516] ACPI: Added _OSI(Module Device)
[    0.073519] ACPI: Added _OSI(Processor Device)
[    0.073522] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.073525] ACPI: Added _OSI(Processor Aggregator Device)
[    0.074645] ACPI: EC: Look up EC in DSDT
[    0.083180] ACPI: SSDT 3f7d1fd0 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20030522)
[    0.083440] ACPI: Dynamic OEM Table Load:
[    0.083444] ACPI: SSDT   (null) 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20030522)
[    0.083739] ACPI: Interpreter enabled
[    0.083749] ACPI: (supports S0 S3 S4 S5)
[    0.083772] ACPI: Using IOAPIC for interrupt routing
[    0.115217] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.115220] HEST: Table not found.
[    0.115227] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.122428] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.136603] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.136607] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.136611] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.136615] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.136618] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xdfffffff] (ignored)
[    0.136622] pci_root PNP0A03:00: host bridge window [mem 0xf0007000-0xf0007fff] (ignored)
[    0.136625] pci_root PNP0A03:00: host bridge window [mem 0xf000c000-0xfebfffff] (ignored)
[    0.136629] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfed1ffff] (ignored)
[    0.136632] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xffafffff] (ignored)
[    0.136646] pci 0000:00:00.0: [8086:2590] type 0 class 0x000600
[    0.136698] pci 0000:00:02.0: [8086:2592] type 0 class 0x000300
[    0.136709] pci 0000:00:02.0: reg 10: [mem 0xdff00000-0xdff7ffff]
[    0.136717] pci 0000:00:02.0: reg 14: [io  0xec38-0xec3f]
[    0.136724] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
[    0.136731] pci 0000:00:02.0: reg 1c: [mem 0xdfec0000-0xdfefffff]
[    0.136769] pci 0000:00:02.1: [8086:2792] type 0 class 0x000380
[    0.136779] pci 0000:00:02.1: reg 10: [mem 0xdff80000-0xdfffffff]
[    0.136880] pci 0000:00:1c.0: [8086:2660] type 1 class 0x000604
[    0.136987] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.136993] pci 0000:00:1c.0: PME# disabled
[    0.137030] pci 0000:00:1d.0: [8086:2658] type 0 class 0x000c03
[    0.137085] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
[    0.137128] pci 0000:00:1d.1: [8086:2659] type 0 class 0x000c03
[    0.137184] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
[    0.137225] pci 0000:00:1d.2: [8086:265a] type 0 class 0x000c03
[    0.137281] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
[    0.137322] pci 0000:00:1d.3: [8086:265b] type 0 class 0x000c03
[    0.137378] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
[    0.137431] pci 0000:00:1d.7: [8086:265c] type 0 class 0x000c03
[    0.137456] pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]
[    0.137559] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.137566] pci 0000:00:1d.7: PME# disabled
[    0.137589] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.137682] pci 0000:00:1e.2: [8086:266e] type 0 class 0x000401
[    0.137703] pci 0000:00:1e.2: reg 10: [io  0xed00-0xedff]
[    0.137715] pci 0000:00:1e.2: reg 14: [io  0xec40-0xec7f]
[    0.137728] pci 0000:00:1e.2: reg 18: [mem 0xdfebfe00-0xdfebffff]
[    0.137741] pci 0000:00:1e.2: reg 1c: [mem 0xdfebfd00-0xdfebfdff]
[    0.137803] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.137809] pci 0000:00:1e.2: PME# disabled
[    0.137829] pci 0000:00:1e.3: [8086:266d] type 0 class 0x000703
[    0.137850] pci 0000:00:1e.3: reg 10: [io  0xee00-0xeeff]
[    0.137862] pci 0000:00:1e.3: reg 14: [io  0xec80-0xecff]
[    0.137945] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.137950] pci 0000:00:1e.3: PME# disabled
[    0.137974] pci 0000:00:1f.0: [8086:2641] type 0 class 0x000601
[    0.138083] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.138093] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.138100] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.138106] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0900-097f
[    0.138111] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 0280-028f
[    0.138139] pci 0000:00:1f.2: [8086:2653] type 0 class 0x000101
[    0.138160] pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
[    0.138173] pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
[    0.138186] pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
[    0.138198] pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
[    0.138211] pci 0000:00:1f.2: reg 20: [io  0xbfa0-0xbfaf]
[    0.138265] pci 0000:00:1f.2: PME# supported from D3hot
[    0.138271] pci 0000:00:1f.2: PME# disabled
[    0.138374] pci 0000:02:00.0: [14e4:1677] type 0 class 0x000200
[    0.138406] pci 0000:02:00.0: reg 10: [mem 0xdfdf0000-0xdfdfffff 64bit]
[    0.138572] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.138579] pci 0000:02:00.0: PME# disabled
[    0.138602] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.138617] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.138627] pci 0000:00:1c.0:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.138683] pci 0000:03:01.0: [104c:8036] type 2 class 0x000607
[    0.138709] pci 0000:03:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.138752] pci 0000:03:01.0: supports D1 D2
[    0.138755] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.138762] pci 0000:03:01.0: PME# disabled
[    0.138794] pci 0000:03:01.5: [104c:8038] type 0 class 0x000780
[    0.138820] pci 0000:03:01.5: reg 10: [mem 0xdfcfd000-0xdfcfdfff]
[    0.138835] pci 0000:03:01.5: reg 14: [mem 0xdfcfe000-0xdfcfefff]
[    0.138939] pci 0000:03:01.5: supports D1 D2
[    0.138941] pci 0000:03:01.5: PME# supported from D0 D1 D2 D3hot
[    0.138948] pci 0000:03:01.5: PME# disabled
[    0.138977] pci 0000:03:03.0: [8086:4220] type 0 class 0x000280
[    0.139004] pci 0000:03:03.0: reg 10: [mem 0xdfcff000-0xdfcfffff]
[    0.139120] pci 0000:03:03.0: PME# supported from D0 D3hot D3cold
[    0.139126] pci 0000:03:03.0: PME# disabled
[    0.139187] pci 0000:00:1e.0: PCI bridge to [bus 03-04] (subtractive decode)
[    0.139196] pci 0000:00:1e.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.139204] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.139208] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.139262] pci_bus 0000:04: [bus 04-07] partially hidden behind transparent bridge 0000:03 [bus 03-04]
[    0.139280] pci_bus 0000:00: on NUMA node 0
[    0.139284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.139662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.139828]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.139832]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.139835] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.156262] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.156354] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.156444] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.156533] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.156608] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.156687] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.156766] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.156938] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.156952] vgaarb: loaded
[    0.156954] vgaarb: bridge control possible 0000:00:02.0
[    0.157112] i2c-core: driver [aat2870] using legacy suspend method
[    0.157114] i2c-core: driver [aat2870] using legacy resume method
[    0.157216] SCSI subsystem initialized
[    0.157265] libata version 3.00 loaded.
[    0.157327] usbcore: registered new interface driver usbfs
[    0.157344] usbcore: registered new interface driver hub
[    0.157374] usbcore: registered new device driver usb
[    0.157492] PCI: Using ACPI for IRQ routing
[    0.167862] PCI: pci_cache_line_size set to 64 bytes
[    0.167953] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.167957] reserve RAM buffer: 000000003f7d1800 - 000000003fffffff 
[    0.168103] NetLabel: Initializing
[    0.168106] NetLabel:  domain hash size = 128
[    0.168108] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.168121] NetLabel:  unlabeled traffic allowed by default
[    0.168298] hpet clockevent registered
[    0.168303] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.168310] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.168316] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.172035] Switching to clocksource hpet
[    0.183504] AppArmor: AppArmor Filesystem Enabled
[    0.183564] pnp: PnP ACPI init
[    0.183593] ACPI: bus type pnp registered
[    0.192584] pnp 00:00: [mem 0x00000000-0x0009fbff]
[    0.192588] pnp 00:00: [mem 0x0009fc00-0x0009ffff]
[    0.192591] pnp 00:00: [mem 0x000c0000-0x000cffff]
[    0.192594] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.192597] pnp 00:00: [mem 0x00100000-0x3f7d17ff]
[    0.192600] pnp 00:00: [mem 0x3f7d1800-0x3f7fffff]
[    0.192603] pnp 00:00: [mem 0x3f800000-0x3fffffff]
[    0.192606] pnp 00:00: [mem 0xfeda0000-0xfedfffff]
[    0.192609] pnp 00:00: [mem 0xffb00000-0xffffffff]
[    0.192612] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
[    0.192615] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
[    0.192618] pnp 00:00: [mem 0xfed20000-0xfed9ffff]
[    0.192621] pnp 00:00: [mem 0xf0000000-0xf0003fff]
[    0.192624] pnp 00:00: [mem 0xf0004000-0xf0004fff]
[    0.192627] pnp 00:00: [mem 0xf0005000-0xf0005fff]
[    0.192630] pnp 00:00: [mem 0xf0006000-0xf0006fff]
[    0.192633] pnp 00:00: [mem 0xf0008000-0xf000bfff]
[    0.192636] pnp 00:00: [mem 0xe0000000-0xefffffff]
[    0.192739] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.192743] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.192747] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.192751] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.192755] system 00:00: [mem 0x00100000-0x3f7d17ff] could not be reserved
[    0.192759] system 00:00: [mem 0x3f7d1800-0x3f7fffff] has been reserved
[    0.192763] system 00:00: [mem 0x3f800000-0x3fffffff] has been reserved
[    0.192767] system 00:00: [mem 0xfeda0000-0xfedfffff] has been reserved
[    0.192771] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.192775] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.192779] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.192783] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.192786] system 00:00: [mem 0xf0000000-0xf0003fff] has been reserved
[    0.192790] system 00:00: [mem 0xf0004000-0xf0004fff] has been reserved
[    0.192794] system 00:00: [mem 0xf0005000-0xf0005fff] has been reserved
[    0.192798] system 00:00: [mem 0xf0006000-0xf0006fff] has been reserved
[    0.192802] system 00:00: [mem 0xf0008000-0xf000bfff] has been reserved
[    0.192806] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.192811] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.199843] pnp 00:01: [bus 00-ff]
[    0.199853] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.199856] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.199859] pnp 00:01: [io  0x0d00-0xffff window]
[    0.199862] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.199865] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.199868] pnp 00:01: [mem 0x40000000-0xdfffffff window]
[    0.199872] pnp 00:01: [mem 0xf0007000-0xf0007fff window]
[    0.199875] pnp 00:01: [mem 0xf000c000-0xfebfffff window]
[    0.199878] pnp 00:01: [mem 0xfec10000-0xfed1ffff window]
[    0.199881] pnp 00:01: [mem 0xfeda0000-0xfed9ffff window disabled]
[    0.199885] pnp 00:01: [mem 0xfee10000-0xffafffff window]
[    0.199978] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.200020] pnp 00:02: [io  0x0092]
[    0.200023] pnp 00:02: [io  0x00b2]
[    0.200026] pnp 00:02: [io  0x0020-0x0021]
[    0.200029] pnp 00:02: [io  0x00a0-0x00a1]
[    0.200032] pnp 00:02: [irq 0 disabled]
[    0.200035] pnp 00:02: [io  0x04d0-0x04d1]
[    0.200038] pnp 00:02: [io  0x1000-0x1005]
[    0.200041] pnp 00:02: [io  0x1008-0x100f]
[    0.200061] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.200065] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.200115] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.200120] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.200142] pnp 00:03: [io  0xf400-0xf4fe]
[    0.200145] pnp 00:03: [io  0x0086]
[    0.200148] pnp 00:03: [io  0x00b3]
[    0.200150] pnp 00:03: [io  0x1006-0x1007]
[    0.200153] pnp 00:03: [io  0x100a-0x1059]
[    0.200156] pnp 00:03: [io  0x1060-0x107f]
[    0.200158] pnp 00:03: [io  0x1080-0x10bf]
[    0.200161] pnp 00:03: [io  0x10c0-0x10df]
[    0.200164] pnp 00:03: [io  0x10e0-0x10ff]
[    0.200183] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.200187] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.200192] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.200239] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.200243] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.200247] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.200250] system 00:03: [io  0x10e0-0x10ff] has been reserved
[    0.200254] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.200292] pnp 00:04: [irq 12]
[    0.200336] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.200356] pnp 00:05: [io  0x0060]
[    0.200359] pnp 00:05: [io  0x0064]
[    0.200362] pnp 00:05: [io  0x0062]
[    0.200364] pnp 00:05: [io  0x0066]
[    0.200371] pnp 00:05: [irq 1]
[    0.200413] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.200434] pnp 00:06: [io  0x0070-0x0071]
[    0.200441] pnp 00:06: [irq 8]
[    0.200443] pnp 00:06: [io  0x0072-0x0077]
[    0.200483] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.200505] pnp 00:07: [io  0x0061]
[    0.200508] pnp 00:07: [io  0x0063]
[    0.200511] pnp 00:07: [io  0x0065]
[    0.200513] pnp 00:07: [io  0x0067]
[    0.200557] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.200578] pnp 00:08: [io  0x002e-0x002f]
[    0.200581] pnp 00:08: [io  0x004e-0x004f]
[    0.200584] pnp 00:08: [io  0x0900-0x090f]
[    0.200587] pnp 00:08: [io  0x0910-0x091f]
[    0.200589] pnp 00:08: [io  0x0920-0x092f]
[    0.200592] pnp 00:08: [io  0x093c-0x093f]
[    0.200595] pnp 00:08: [io  0x0940-0x097f]
[    0.200658] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.200662] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.200666] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.200669] system 00:08: [io  0x093c-0x093f] has been reserved
[    0.200673] system 00:08: [io  0x0940-0x097f] has been reserved
[    0.200677] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.200701] pnp 00:09: [dma 4]
[    0.200704] pnp 00:09: [io  0x0000-0x000f]
[    0.200707] pnp 00:09: [io  0x0080-0x0085]
[    0.200710] pnp 00:09: [io  0x0087-0x008f]
[    0.200713] pnp 00:09: [io  0x00c0-0x00df]
[    0.200715] pnp 00:09: [io  0x0010-0x001f]
[    0.200722] pnp 00:09: [io  0x0090-0x0091]
[    0.200725] pnp 00:09: [io  0x0093-0x009f]
[    0.200771] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.200791] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.200797] pnp 00:0a: [irq 13]
[    0.200839] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.205521] pnp 00:0b: [irq 4]
[    0.205524] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.205611] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.212591] pnp 00:0c: [irq 3]
[    0.212594] pnp 00:0c: [io  0x02f8-0x02ff]
[    0.212597] pnp 00:0c: [io  0x0280-0x0287]
[    0.212600] pnp 00:0c: [dma 3]
[    0.212753] pnp 00:0c: Plug and Play ACPI device, IDs SMCf010 (active)
[    0.219435] pnp 00:0d: [dma 1]
[    0.219442] pnp 00:0d: [irq 7]
[    0.219449] pnp 00:0d: [io  0x0378-0x037f]
[    0.219452] pnp 00:0d: [io  0x0778-0x077b]
[    0.219581] pnp 00:0d: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.225009] pnp 00:0e: [io  0x0930-0x093b]
[    0.225081] system 00:0e: [io  0x0930-0x093b] has been reserved
[    0.225085] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.226130] pnp 00:0f: [io  0x07b0-0x07bb]
[    0.226133] pnp 00:0f: [io  0x07c0-0x07df]
[    0.226136] pnp 00:0f: [io  0x0bb0-0x0bbb]
[    0.226139] pnp 00:0f: [io  0x0bc0-0x0bdf]
[    0.226142] pnp 00:0f: [io  0x0fb0-0x0fbb]
[    0.226144] pnp 00:0f: [io  0x0fc0-0x0fdf]
[    0.226147] pnp 00:0f: [io  0x13b0-0x13bb]
[    0.226150] pnp 00:0f: [io  0x13c0-0x13df]
[    0.226153] pnp 00:0f: [io  0x17b0-0x17bb]
[    0.226155] pnp 00:0f: [io  0x17c0-0x17df]
[    0.226158] pnp 00:0f: [io  0x1bb0-0x1bbb]
[    0.226161] pnp 00:0f: [io  0x1bc0-0x1bdf]
[    0.226164] pnp 00:0f: [io  0x1fb0-0x1fbb]
[    0.226166] pnp 00:0f: [io  0x1fc0-0x1fdf]
[    0.226169] pnp 00:0f: [io  0x23b0-0x23bb]
[    0.226172] pnp 00:0f: [io  0x23c0-0x23df]
[    0.226175] pnp 00:0f: [io  0x27b0-0x27bb]
[    0.226177] pnp 00:0f: [io  0x27c0-0x27df]
[    0.226180] pnp 00:0f: [io  0x2bb0-0x2bbb]
[    0.226183] pnp 00:0f: [io  0x2bc0-0x2bdf]
[    0.226185] pnp 00:0f: [io  0x2fb0-0x2fbb]
[    0.226188] pnp 00:0f: [io  0x2fc0-0x2fdf]
[    0.226191] pnp 00:0f: [io  0x33b0-0x33bb]
[    0.226194] pnp 00:0f: [io  0x33c0-0x33df]
[    0.226201] pnp 00:0f: [io  0x37b0-0x37bb]
[    0.226203] pnp 00:0f: [io  0x37c0-0x37df]
[    0.226206] pnp 00:0f: [io  0x3bb0-0x3bbb]
[    0.226209] pnp 00:0f: [io  0x3bc0-0x3bdf]
[    0.226212] pnp 00:0f: [io  0x3fb0-0x3fbb]
[    0.226214] pnp 00:0f: [io  0x3fc0-0x3fdf]
[    0.226217] pnp 00:0f: [io  0x43b0-0x43bb]
[    0.226220] pnp 00:0f: [io  0x43c0-0x43df]
[    0.226223] pnp 00:0f: [io  0x47b0-0x47bb]
[    0.226225] pnp 00:0f: [io  0x47c0-0x47df]
[    0.226228] pnp 00:0f: [io  0x4bb0-0x4bbb]
[    0.226231] pnp 00:0f: [io  0x4bc0-0x4bdf]
[    0.226234] pnp 00:0f: [io  0x4fb0-0x4fbb]
[    0.226236] pnp 00:0f: [io  0x4fc0-0x4fdf]
[    0.226239] pnp 00:0f: [io  0x53b0-0x53bb]
[    0.226242] pnp 00:0f: [io  0x53c0-0x53df]
[    0.226244] pnp 00:0f: [io  0x57b0-0x57bb]
[    0.226247] pnp 00:0f: [io  0x57c0-0x57df]
[    0.226250] pnp 00:0f: [io  0x5bb0-0x5bbb]
[    0.226253] pnp 00:0f: [io  0x5bc0-0x5bdf]
[    0.226255] pnp 00:0f: [io  0x5fb0-0x5fbb]
[    0.226258] pnp 00:0f: [io  0x5fc0-0x5fdf]
[    0.226261] pnp 00:0f: [io  0x63b0-0x63bb]
[    0.226264] pnp 00:0f: [io  0x63c0-0x63df]
[    0.226266] pnp 00:0f: [io  0x67b0-0x67bb]
[    0.226269] pnp 00:0f: [io  0x67c0-0x67df]
[    0.226272] pnp 00:0f: [io  0x6bb0-0x6bbb]
[    0.226275] pnp 00:0f: [io  0x6bc0-0x6bdf]
[    0.226277] pnp 00:0f: [io  0x6fb0-0x6fbb]
[    0.226280] pnp 00:0f: [io  0x6fc0-0x6fdf]
[    0.226283] pnp 00:0f: [io  0x73b0-0x73bb]
[    0.226285] pnp 00:0f: [io  0x73c0-0x73df]
[    0.226288] pnp 00:0f: [io  0x77b0-0x77bb]
[    0.226291] pnp 00:0f: [io  0x77c0-0x77df]
[    0.226294] pnp 00:0f: [io  0x7bb0-0x7bbb]
[    0.226296] pnp 00:0f: [io  0x7bc0-0x7bdf]
[    0.226299] pnp 00:0f: [io  0x7fb0-0x7fbb]
[    0.226302] pnp 00:0f: [io  0x7fc0-0x7fdf]
[    0.226305] pnp 00:0f: [io  0x83b0-0x83bb]
[    0.226307] pnp 00:0f: [io  0x83c0-0x83df]
[    0.226310] pnp 00:0f: [io  0x87b0-0x87bb]
[    0.226313] pnp 00:0f: [io  0x87c0-0x87df]
[    0.226316] pnp 00:0f: [io  0x8bb0-0x8bbb]
[    0.226318] pnp 00:0f: [io  0x8bc0-0x8bdf]
[    0.226321] pnp 00:0f: [io  0x8fb0-0x8fbb]
[    0.226324] pnp 00:0f: [io  0x8fc0-0x8fdf]
[    0.226326] pnp 00:0f: [io  0x93b0-0x93bb]
[    0.226329] pnp 00:0f: [io  0x93c0-0x93df]
[    0.226332] pnp 00:0f: [io  0x97b0-0x97bb]
[    0.226335] pnp 00:0f: [io  0x97c0-0x97df]
[    0.226337] pnp 00:0f: [io  0x9bb0-0x9bbb]
[    0.226340] pnp 00:0f: [io  0x9bc0-0x9bdf]
[    0.226343] pnp 00:0f: [io  0x9fb0-0x9fbb]
[    0.226346] pnp 00:0f: [io  0x9fc0-0x9fdf]
[    0.226348] pnp 00:0f: [io  0xa3b0-0xa3bb]
[    0.226351] pnp 00:0f: [io  0xa3c0-0xa3df]
[    0.226354] pnp 00:0f: [io  0xa7b0-0xa7bb]
[    0.226357] pnp 00:0f: [io  0xa7c0-0xa7df]
[    0.226359] pnp 00:0f: [io  0xabb0-0xabbb]
[    0.226362] pnp 00:0f: [io  0xabc0-0xabdf]
[    0.226365] pnp 00:0f: [io  0xafb0-0xafbb]
[    0.226367] pnp 00:0f: [io  0xafc0-0xafdf]
[    0.226370] pnp 00:0f: [io  0xb3b0-0xb3bb]
[    0.226373] pnp 00:0f: [io  0xb3c0-0xb3df]
[    0.226379] pnp 00:0f: [io  0xb7b0-0xb7bb]
[    0.226382] pnp 00:0f: [io  0xb7c0-0xb7df]
[    0.226385] pnp 00:0f: [io  0xbbb0-0xbbbb]
[    0.226387] pnp 00:0f: [io  0xbbc0-0xbbdf]
[    0.226390] pnp 00:0f: [io  0xbfb0-0xbfbb]
[    0.226393] pnp 00:0f: [io  0xbfc0-0xbfdf]
[    0.226395] pnp 00:0f: [io  0xc3b0-0xc3bb]
[    0.226398] pnp 00:0f: [io  0xc3c0-0xc3df]
[    0.226401] pnp 00:0f: [io  0xc7b0-0xc7bb]
[    0.226404] pnp 00:0f: [io  0xc7c0-0xc7df]
[    0.226406] pnp 00:0f: [io  0xcbb0-0xcbbb]
[    0.226409] pnp 00:0f: [io  0xcbc0-0xcbdf]
[    0.226412] pnp 00:0f: [io  0xcfb0-0xcfbb]
[    0.226415] pnp 00:0f: [io  0xcfc0-0xcfdf]
[    0.226417] pnp 00:0f: [io  0xd3b0-0xd3bb]
[    0.226420] pnp 00:0f: [io  0xd3c0-0xd3df]
[    0.226423] pnp 00:0f: [io  0xd7b0-0xd7bb]
[    0.226426] pnp 00:0f: [io  0xd7c0-0xd7df]
[    0.226428] pnp 00:0f: [io  0xdbb0-0xdbbb]
[    0.226431] pnp 00:0f: [io  0xdbc0-0xdbdf]
[    0.226434] pnp 00:0f: [io  0xdfb0-0xdfbb]
[    0.226436] pnp 00:0f: [io  0xdfc0-0xdfdf]
[    0.226439] pnp 00:0f: [io  0xe3b0-0xe3bb]
[    0.226442] pnp 00:0f: [io  0xe3c0-0xe3df]
[    0.226445] pnp 00:0f: [io  0xe7b0-0xe7bb]
[    0.226447] pnp 00:0f: [io  0xe7c0-0xe7df]
[    0.226450] pnp 00:0f: [io  0xebb0-0xebbb]
[    0.226453] pnp 00:0f: [io  0xebc0-0xebdf]
[    0.226456] pnp 00:0f: [io  0xefb0-0xefbb]
[    0.226458] pnp 00:0f: [io  0xefc0-0xefdf]
[    0.226461] pnp 00:0f: [io  0xf3b0-0xf3bb]
[    0.226464] pnp 00:0f: [io  0xf3c0-0xf3df]
[    0.226467] pnp 00:0f: [io  0xf7b0-0xf7bb]
[    0.226469] pnp 00:0f: [io  0xf7c0-0xf7df]
[    0.226472] pnp 00:0f: [io  0xfbb0-0xfbbb]
[    0.226475] pnp 00:0f: [io  0xfbc0-0xfbdf]
[    0.226477] pnp 00:0f: [io  0xffb0-0xffbb]
[    0.226480] pnp 00:0f: [io  0xffc0-0xffdf]
[    0.226960] system 00:0f: [io  0x07b0-0x07bb] has been reserved
[    0.226964] system 00:0f: [io  0x07c0-0x07df] has been reserved
[    0.226967] system 00:0f: [io  0x0bb0-0x0bbb] has been reserved
[    0.226971] system 00:0f: [io  0x0bc0-0x0bdf] has been reserved
[    0.226975] system 00:0f: [io  0x0fb0-0x0fbb] has been reserved
[    0.226978] system 00:0f: [io  0x0fc0-0x0fdf] has been reserved
[    0.226982] system 00:0f: [io  0x13b0-0x13bb] has been reserved
[    0.226986] system 00:0f: [io  0x13c0-0x13df] has been reserved
[    0.226989] system 00:0f: [io  0x17b0-0x17bb] has been reserved
[    0.226993] system 00:0f: [io  0x17c0-0x17df] has been reserved
[    0.226997] system 00:0f: [io  0x1bb0-0x1bbb] has been reserved
[    0.227001] system 00:0f: [io  0x1bc0-0x1bdf] has been reserved
[    0.227004] system 00:0f: [io  0x1fb0-0x1fbb] has been reserved
[    0.227008] system 00:0f: [io  0x1fc0-0x1fdf] has been reserved
[    0.227012] system 00:0f: [io  0x23b0-0x23bb] has been reserved
[    0.227015] system 00:0f: [io  0x23c0-0x23df] has been reserved
[    0.227019] system 00:0f: [io  0x27b0-0x27bb] has been reserved
[    0.227023] system 00:0f: [io  0x27c0-0x27df] has been reserved
[    0.227027] system 00:0f: [io  0x2bb0-0x2bbb] has been reserved
[    0.227030] system 00:0f: [io  0x2bc0-0x2bdf] has been reserved
[    0.227034] system 00:0f: [io  0x2fb0-0x2fbb] has been reserved
[    0.227038] system 00:0f: [io  0x2fc0-0x2fdf] has been reserved
[    0.227042] system 00:0f: [io  0x33b0-0x33bb] has been reserved
[    0.227045] system 00:0f: [io  0x33c0-0x33df] has been reserved
[    0.227049] system 00:0f: [io  0x37b0-0x37bb] has been reserved
[    0.227053] system 00:0f: [io  0x37c0-0x37df] has been reserved
[    0.227061] system 00:0f: [io  0x3bb0-0x3bbb] has been reserved
[    0.227064] system 00:0f: [io  0x3bc0-0x3bdf] has been reserved
[    0.227068] system 00:0f: [io  0x3fb0-0x3fbb] has been reserved
[    0.227072] system 00:0f: [io  0x3fc0-0x3fdf] has been reserved
[    0.227076] system 00:0f: [io  0x43b0-0x43bb] has been reserved
[    0.227080] system 00:0f: [io  0x43c0-0x43df] has been reserved
[    0.227083] system 00:0f: [io  0x47b0-0x47bb] has been reserved
[    0.227087] system 00:0f: [io  0x47c0-0x47df] has been reserved
[    0.227091] system 00:0f: [io  0x4bb0-0x4bbb] has been reserved
[    0.227095] system 00:0f: [io  0x4bc0-0x4bdf] has been reserved
[    0.227099] system 00:0f: [io  0x4fb0-0x4fbb] has been reserved
[    0.227103] system 00:0f: [io  0x4fc0-0x4fdf] has been reserved
[    0.227107] system 00:0f: [io  0x53b0-0x53bb] has been reserved
[    0.227111] system 00:0f: [io  0x53c0-0x53df] has been reserved
[    0.227114] system 00:0f: [io  0x57b0-0x57bb] has been reserved
[    0.227118] system 00:0f: [io  0x57c0-0x57df] has been reserved
[    0.227122] system 00:0f: [io  0x5bb0-0x5bbb] has been reserved
[    0.227126] system 00:0f: [io  0x5bc0-0x5bdf] has been reserved
[    0.227130] system 00:0f: [io  0x5fb0-0x5fbb] has been reserved
[    0.227134] system 00:0f: [io  0x5fc0-0x5fdf] has been reserved
[    0.227138] system 00:0f: [io  0x63b0-0x63bb] has been reserved
[    0.227142] system 00:0f: [io  0x63c0-0x63df] has been reserved
[    0.227146] system 00:0f: [io  0x67b0-0x67bb] has been reserved
[    0.227150] system 00:0f: [io  0x67c0-0x67df] has been reserved
[    0.227154] system 00:0f: [io  0x6bb0-0x6bbb] has been reserved
[    0.227158] system 00:0f: [io  0x6bc0-0x6bdf] has been reserved
[    0.227162] system 00:0f: [io  0x6fb0-0x6fbb] has been reserved
[    0.227166] system 00:0f: [io  0x6fc0-0x6fdf] has been reserved
[    0.227170] system 00:0f: [io  0x73b0-0x73bb] has been reserved
[    0.227174] system 00:0f: [io  0x73c0-0x73df] has been reserved
[    0.227178] system 00:0f: [io  0x77b0-0x77bb] has been reserved
[    0.227182] system 00:0f: [io  0x77c0-0x77df] has been reserved
[    0.227186] system 00:0f: [io  0x7bb0-0x7bbb] has been reserved
[    0.227190] system 00:0f: [io  0x7bc0-0x7bdf] has been reserved
[    0.227194] system 00:0f: [io  0x7fb0-0x7fbb] has been reserved
[    0.227198] system 00:0f: [io  0x7fc0-0x7fdf] has been reserved
[    0.227202] system 00:0f: [io  0x83b0-0x83bb] has been reserved
[    0.227206] system 00:0f: [io  0x83c0-0x83df] has been reserved
[    0.227210] system 00:0f: [io  0x87b0-0x87bb] has been reserved
[    0.227214] system 00:0f: [io  0x87c0-0x87df] has been reserved
[    0.227218] system 00:0f: [io  0x8bb0-0x8bbb] has been reserved
[    0.227222] system 00:0f: [io  0x8bc0-0x8bdf] has been reserved
[    0.227226] system 00:0f: [io  0x8fb0-0x8fbb] has been reserved
[    0.227230] system 00:0f: [io  0x8fc0-0x8fdf] has been reserved
[    0.227234] system 00:0f: [io  0x93b0-0x93bb] has been reserved
[    0.227238] system 00:0f: [io  0x93c0-0x93df] has been reserved
[    0.227242] system 00:0f: [io  0x97b0-0x97bb] has been reserved
[    0.227247] system 00:0f: [io  0x97c0-0x97df] has been reserved
[    0.227251] system 00:0f: [io  0x9bb0-0x9bbb] has been reserved
[    0.227255] system 00:0f: [io  0x9bc0-0x9bdf] has been reserved
[    0.227259] system 00:0f: [io  0x9fb0-0x9fbb] has been reserved
[    0.227263] system 00:0f: [io  0x9fc0-0x9fdf] has been reserved
[    0.227267] system 00:0f: [io  0xa3b0-0xa3bb] has been reserved
[    0.227271] system 00:0f: [io  0xa3c0-0xa3df] has been reserved
[    0.227276] system 00:0f: [io  0xa7b0-0xa7bb] has been reserved
[    0.227280] system 00:0f: [io  0xa7c0-0xa7df] has been reserved
[    0.227284] system 00:0f: [io  0xabb0-0xabbb] has been reserved
[    0.227288] system 00:0f: [io  0xabc0-0xabdf] has been reserved
[    0.227292] system 00:0f: [io  0xafb0-0xafbb] has been reserved
[    0.227297] system 00:0f: [io  0xafc0-0xafdf] has been reserved
[    0.227301] system 00:0f: [io  0xb3b0-0xb3bb] has been reserved
[    0.227305] system 00:0f: [io  0xb3c0-0xb3df] has been reserved
[    0.227309] system 00:0f: [io  0xb7b0-0xb7bb] has been reserved
[    0.227313] system 00:0f: [io  0xb7c0-0xb7df] has been reserved
[    0.227321] system 00:0f: [io  0xbbb0-0xbbbb] has been reserved
[    0.227326] system 00:0f: [io  0xbbc0-0xbbdf] has been reserved
[    0.227330] system 00:0f: [io  0xbfb0-0xbfbb] has been reserved
[    0.227334] system 00:0f: [io  0xbfc0-0xbfdf] has been reserved
[    0.227339] system 00:0f: [io  0xc3b0-0xc3bb] has been reserved
[    0.227343] system 00:0f: [io  0xc3c0-0xc3df] has been reserved
[    0.227347] system 00:0f: [io  0xc7b0-0xc7bb] has been reserved
[    0.227352] system 00:0f: [io  0xc7c0-0xc7df] has been reserved
[    0.227356] system 00:0f: [io  0xcbb0-0xcbbb] has been reserved
[    0.227360] system 00:0f: [io  0xcbc0-0xcbdf] has been reserved
[    0.227365] system 00:0f: [io  0xcfb0-0xcfbb] has been reserved
[    0.227369] system 00:0f: [io  0xcfc0-0xcfdf] has been reserved
[    0.227374] system 00:0f: [io  0xd3b0-0xd3bb] has been reserved
[    0.227378] system 00:0f: [io  0xd3c0-0xd3df] has been reserved
[    0.227382] system 00:0f: [io  0xd7b0-0xd7bb] has been reserved
[    0.227387] system 00:0f: [io  0xd7c0-0xd7df] has been reserved
[    0.227391] system 00:0f: [io  0xdbb0-0xdbbb] has been reserved
[    0.227396] system 00:0f: [io  0xdbc0-0xdbdf] has been reserved
[    0.227400] system 00:0f: [io  0xdfb0-0xdfbb] has been reserved
[    0.227404] system 00:0f: [io  0xdfc0-0xdfdf] has been reserved
[    0.227409] system 00:0f: [io  0xe3b0-0xe3bb] has been reserved
[    0.227413] system 00:0f: [io  0xe3c0-0xe3df] has been reserved
[    0.227418] system 00:0f: [io  0xe7b0-0xe7bb] has been reserved
[    0.227422] system 00:0f: [io  0xe7c0-0xe7df] has been reserved
[    0.227427] system 00:0f: [io  0xebb0-0xebbb] has been reserved
[    0.227431] system 00:0f: [io  0xebc0-0xebdf] has been reserved
[    0.227436] system 00:0f: [io  0xefb0-0xefbb] has been reserved
[    0.227440] system 00:0f: [io  0xefc0-0xefdf] has been reserved
[    0.227445] system 00:0f: [io  0xf3b0-0xf3bb] has been reserved
[    0.227449] system 00:0f: [io  0xf3c0-0xf3df] has been reserved
[    0.227454] system 00:0f: [io  0xf7b0-0xf7bb] has been reserved
[    0.227458] system 00:0f: [io  0xf7c0-0xf7df] has been reserved
[    0.227463] system 00:0f: [io  0xfbb0-0xfbbb] has been reserved
[    0.227467] system 00:0f: [io  0xfbc0-0xfbdf] has been reserved
[    0.227472] system 00:0f: [io  0xffb0-0xffbb] has been reserved
[    0.227476] system 00:0f: [io  0xffc0-0xffdf] has been reserved
[    0.227481] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.228182] pnp: PnP ACPI: found 16 devices
[    0.228185] ACPI: ACPI bus type pnp unregistered
[    0.228190] PnPBIOS: Disabled by ACPI PNP
[    0.265417] PCI: max bus depth: 2 pci_try_num: 3
[    0.265468] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.265481] pci 0000:00:1e.0: BAR 13: can't assign io (size 0x1000)
[    0.265486] pci 0000:00:1c.0: BAR 15: assigned [mem 0x44000000-0x441fffff 64bit pref]
[    0.265497] pci 0000:00:1c.0: BAR 13: can't assign io (size 0x1000)
[    0.265501] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.265509] pci 0000:00:1c.0:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.265515] pci 0000:00:1c.0:   bridge window [mem 0x44000000-0x441fffff 64bit pref]
[    0.265527] pci 0000:03:01.0: BAR 0: assigned [mem 0x48000000-0x48000fff]
[    0.265535] pci 0000:03:01.0: BAR 0: set to [mem 0x48000000-0x48000fff] (PCI address [0x48000000-0x48000fff])
[    0.265540] pci 0000:03:01.0: BAR 16: assigned [mem 0x4c000000-0x4fffffff]
[    0.265544] pci 0000:03:01.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.265549] pci 0000:03:01.0: BAR 14: assigned [io  0x1400-0x14ff]
[    0.265555] pci 0000:03:01.0: BAR 13: assigned [io  0x1800-0x18ff]
[    0.265558] pci 0000:03:01.0: CardBus bridge to [bus 04-07]
[    0.265561] pci 0000:03:01.0:   bridge window [io  0x1800-0x18ff]
[    0.265567] pci 0000:03:01.0:   bridge window [io  0x1400-0x14ff]
[    0.265574] pci 0000:03:01.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.265581] pci 0000:03:01.0:   bridge window [mem 0x4c000000-0x4fffffff]
[    0.265587] pci 0000:00:1e.0: PCI bridge to [bus 03-04]
[    0.265594] pci 0000:00:1e.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.265601] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.265631] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.265638] pci 0000:00:1c.0: setting latency timer to 64
[    0.265647] pci 0000:00:1e.0: setting latency timer to 64
[    0.265656] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.265665] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.265674] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.265678] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.265681] pci_bus 0000:02: resource 1 [mem 0xdfd00000-0xdfdfffff]
[    0.265685] pci_bus 0000:02: resource 2 [mem 0x44000000-0x441fffff 64bit pref]
[    0.265688] pci_bus 0000:03: resource 1 [mem 0xdfc00000-0xdfcfffff]
[    0.265692] pci_bus 0000:03: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.265695] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.265698] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.265701] pci_bus 0000:04: resource 0 [io  0x1800-0x18ff]
[    0.265704] pci_bus 0000:04: resource 1 [io  0x1400-0x14ff]
[    0.265708] pci_bus 0000:04: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.265711] pci_bus 0000:04: resource 3 [mem 0x4c000000-0x4fffffff]
[    0.265771] NET: Registered protocol family 2
[    0.265876] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.266189] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.267275] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.267973] TCP: Hash tables configured (established 131072 bind 65536)
[    0.267977] TCP reno registered
[    0.267985] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.268071] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.268238] NET: Registered protocol family 1
[    0.268266] pci 0000:00:02.0: Boot video device
[    0.268291] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.268314] pci 0000:00:1d.0: PCI INT A disabled
[    0.268337] pci 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.268358] pci 0000:00:1d.1: PCI INT B disabled
[    0.268372] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.268392] pci 0000:00:1d.2: PCI INT C disabled
[    0.268403] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.268422] pci 0000:00:1d.3: PCI INT D disabled
[    0.268433] pci 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.268470] pci 0000:00:1d.7: PCI INT A disabled
[    0.268505] PCI: CLS 64 bytes, default 64
[    0.268998] audit: initializing netlink socket (disabled)
[    0.269015] type=2000 audit(1359122474.268:1): initialized
[    0.296388] Trying to unpack rootfs image as initramfs...
[    0.328608] highmem bounce pool size: 64 pages
[    0.328617] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.340231] VFS: Disk quotas dquot_6.5.2
[    0.340333] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.341180] fuse init (API version 7.17)
[    0.341313] msgmni has been set to 1710
[    0.352364] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.352400] io scheduler noop registered
[    0.352403] io scheduler deadline registered
[    0.352412] io scheduler cfq registered (default)
[    0.352588] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.352655] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.352787] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.352823] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.353416] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.353920] ACPI: AC Adapter [AC] (on-line)
[    0.354955] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.355429] ACPI: Lid Switch [LID]
[    0.355498] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.355505] ACPI: Power Button [PBTN]
[    0.355564] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.355568] ACPI: Sleep Button [SBTN]
[    0.355812] Marking TSC unstable due to TSC halts in idle
[    0.355831] ACPI: acpi_idle registered with cpuidle
[    0.386685] thermal LNXTHERM:00: registered as thermal_zone0
[    0.386690] ACPI: Thermal Zone [THM] (46 C)
[    0.386721] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.386742] ACPI: Battery Slot [BAT0] (battery present)
[    0.386802] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.386810] ACPI: Battery Slot [BAT1] (battery present)
[    0.386861] ERST: Table is not found!
[    0.386864] GHES: HEST is not enabled!
[    0.386996] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.407530] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.420067] isapnp: Scanning for PnP cards...
[    0.528986] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.570459] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.636270] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.636309] serial 0000:00:1e.3: PCI INT B disabled
[    0.636525] Linux agpgart interface v0.103
[    0.636619] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    0.636679] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.637604] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.640204] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.642298] brd: module loaded
[    0.648789] loop: module loaded
[    0.649004] ahci 0000:00:1f.2: version 3.0
[    0.649021] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.649048] ahci 0000:00:1f.2: PCI INT B disabled
[    0.649052] ahci: probe of 0000:00:1f.2 failed with error -22
[    0.649103] ata_piix 0000:00:1f.2: version 2.13
[    0.649113] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.649119] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.807615] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.812311] scsi0 : ata_piix
[    0.812434] scsi1 : ata_piix
[    1.020720] ACPI: Battery Slot [BAT0] (battery present)
[    1.020931] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.020935] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.021531] Fixed MDIO Bus: probed
[    1.021561] tun: Universal TUN/TAP device driver, 1.6
[    1.021563] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.021649] PPP generic driver version 2.4.2
[    1.021790] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.021820] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.021848] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.021853] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.021920] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.021956] ehci_hcd 0000:00:1d.7: debug port 1
[    1.025850] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.026342] ACPI: Battery Slot [BAT1] (battery present)
[    1.026500] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    1.040092] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.040334] hub 1-0:1.0: USB hub found
[    1.040340] hub 1-0:1.0: 8 ports detected
[    1.040472] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.040497] uhci_hcd: USB Universal Host Controller Interface driver
[    1.040551] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.040571] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.040576] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.040645] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.040681] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    1.040856] hub 2-0:1.0: USB hub found
[    1.040861] hub 2-0:1.0: 2 ports detected
[    1.040950] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.040962] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.040966] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.041021] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.041068] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    1.041235] hub 3-0:1.0: USB hub found
[    1.041240] hub 3-0:1.0: 2 ports detected
[    1.041327] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.041338] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.041342] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.041390] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.041430] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    1.041604] hub 4-0:1.0: USB hub found
[    1.041609] hub 4-0:1.0: 2 ports detected
[    1.041701] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.041713] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.041718] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.041773] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.041814] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    1.041989] hub 5-0:1.0: USB hub found
[    1.041993] hub 5-0:1.0: 2 ports detected
[    1.042154] usbcore: registered new interface driver libusual
[    1.042234] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.092684] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.092697] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.092886] mousedev: PS/2 mouse device common for all mice
[    1.093603] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.093636] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.093740] device-mapper: uevent: version 1.0.3
[    1.093836] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.093890] EISA: Probing bus 0 at eisa.0
[    1.093900] Cannot allocate resource for EISA slot 1
[    1.093939] EISA: Detected 0 cards.
[    1.093954] cpufreq-nforce2: No nForce2 chipset.
[    1.094014] cpuidle: using governor ladder
[    1.094102] cpuidle: using governor menu
[    1.094104] EFI Variables Facility v0.08 2004-May-17
[    1.094451] TCP cubic registered
[    1.095728] NET: Registered protocol family 10
[    1.096888] NET: Registered protocol family 17
[    1.096896] Registering the dns_resolver key type
[    1.096929] Using IPI No-Shortcut mode
[    1.097806] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.098115] PM: Hibernation image not present or could not be loaded.
[    1.098130] registered taskstats version 1
[    1.183867] isapnp: No Plug & Play device found
[    1.192716] ata1.00: ATA-6: TOSHIBA MK1032GAX, AB211A, max UDMA/100
[    1.192722] ata1.00: 195371568 sectors, multi 8: LBA48 
[    1.192726] ata1.00: applying bridge limits
[    1.201181] ata1.00: configured for UDMA/100
[    1.201388] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1032GA AB21 PQ: 0 ANSI: 5
[    1.201658] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.201773] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    1.201841] sd 0:0:0:0: [sda] Write Protect is off
[    1.201845] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.201875] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.203681] Freeing initrd memory: 13840k freed
[    1.223146]   Magic number: 13:293:31
[    1.223317] rtc_cmos 00:06: setting system clock to 2013-01-25 14:01:15 UTC (1359122475)
[    1.223733] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.223736] EDD information not available.
[    1.351960]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 > sda3 sda4
[    1.352904] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.352972] Freeing unused kernel memory: 744k freed
[    1.353363] Write protecting the kernel text: 5828k
[    1.353382] Write protecting the kernel read-only data: 2380k
[    1.353384] NX-protecting the kernel data: 4412k
[    1.372309] udevd[84]: starting version 175
[    1.577333] tg3.c:v3.121 (November 2, 2011)
[    1.577361] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.577374] tg3 0000:02:00.0: setting latency timer to 64
[    1.615771] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:14:22:ca:59:c3
[    1.615778] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.615783] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.615786] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.777370] EXT4-fs (sda9): orphan cleanup on readonly fs
[    2.847956] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 7124
[    2.923095] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 2027
[    2.937864] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 10404
[    2.937887] EXT4-fs (sda9): 3 orphan inodes deleted
[    2.937890] EXT4-fs (sda9): recovery complete
[    3.007857] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[   39.021287] Adding 1533948k swap on /dev/sda5.  Priority:-1 extents:1 across:1533948k 
[   39.364641] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.426982] udevd[339]: starting version 175
[   39.597258] lp: driver loaded but no devices found
[   39.940547] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4
[   39.957075] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   39.957119] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   39.961970] intel_rng: FWH not detected
[   40.041219] lib80211: common routines for IEEE802.11 drivers
[   40.041224] lib80211_crypt: registered algorithm 'NULL'
[   40.053815] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[   40.053822] Disabling lock debugging due to kernel taint
[   40.177968] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0182]
[   40.177992] yenta_cardbus 0000:03:01.0: Using CSCINT to route CSC interrupts to PCI
[   40.177996] yenta_cardbus 0000:03:01.0: Routing CardBus interrupts to PCI
[   40.178003] yenta_cardbus 0000:03:01.0: TI: mfunc 0x01111122, devctl 0x64
[   40.178496] [drm] Initialized drm 1.1.0 20060810
[   40.235157] cfg80211: Calling CRDA to update world regulatory domain
[   40.273931] hsfich 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   40.274155] libipw: 802.11 data/management/control stack, git-1.1.13
[   40.274158] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   40.274469] parport_pc 00:0d: reported by Plug and Play ACPI
[   40.274534] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   40.312245] irda_init()
[   40.312262] NET: Registered protocol family 23
[   40.373472] lp0: using parport0 (interrupt-driven).
[   40.402963] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   40.402968] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   40.408783] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0c78, PCI irq 19
[   40.408789] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   40.408794] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   40.408806] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xdfc00000-0xdfcfffff]
[   40.408811] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdfc00000-0xdfcfffff: excluding 0xdfcf0000-0xdfcfffff
[   40.408829] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[   40.408833] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
[   40.420787] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   40.420820] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   40.564187] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   40.680468] ppdev: user-space parallel port driver
[   40.844596] type=1400 audit(1359151315.116:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=581 comm="apparmor_parser"
[   40.845183] type=1400 audit(1359151315.116:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581 comm="apparmor_parser"
[   40.845521] type=1400 audit(1359151315.116:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
[   40.890461] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x280-0x287 0x2f8-0x2ff 0x370-0x37f
[   40.893320] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   40.894013] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   40.894603] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   40.895260] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xf0000-0xfffff
[   40.895297] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   40.895330] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   40.895363] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   41.106466] cfg80211: failed to add phy80211 symlink to netdev!
[   41.106621] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   41.106625] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106629] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   41.106633] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106636] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   41.106639] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106642] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   41.106646] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106649] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   41.106653] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106656] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   41.106660] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106663] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   41.106666] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106669] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   41.106673] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106676] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   41.106680] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106683] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   41.106686] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.106689] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   41.106693] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   41.107352] udevd[438]: renamed network interface eth0 to rename2
[   41.107434] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   41.135159] udevd[434]: renamed network interface eth1 to eth2
[   41.158007] udevd[438]: renamed network interface rename2 to eth1
[   41.516477] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input5
[   41.542454] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input6
[   41.548901] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   41.548906] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548910] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   41.548914] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548917] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   41.548920] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548923] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   41.548927] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548930] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   41.548934] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548937] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   41.548941] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548944] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   41.548947] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548950] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   41.548954] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548957] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   41.548961] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548964] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   41.548967] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548971] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   41.548974] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548978] cfg80211: World regulatory domain updated:
[   41.548981] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   41.548984] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548988] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   41.548991] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   41.548995] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.548998] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.700601] hsfich 0000:00:1e.3: setting latency timer to 64
[   43.124350] ttySHSF0 at I/O 0xee00 (irq = 17) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[   43.125298] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   43.125306] i915 0000:00:02.0: setting latency timer to 64
[   43.132917] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   43.132921] [drm] Driver supports precise vblank timestamp query.
[   43.169430] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   43.222308] composite sync not supported
[   43.861911] [drm] initialized overlay support
[   43.869172] composite sync not supported
[   44.163729] fbcon: inteldrmfb (fb0) is primary device
[   44.164841] Console: switching to colour frame buffer device 175x65
[   44.164899] fb0: inteldrmfb frame buffer device
[   44.164901] drm: registered panic notifier
[   44.164954] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   44.165004] snd_intel8x0 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   44.165037] snd_intel8x0 0000:00:1e.2: setting latency timer to 64
[   44.678893] composite sync not supported
[   44.686052] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
[   44.992036] intel8x0_measure_ac97_clock: measured 55454 usecs (2672 samples)
[   44.992041] intel8x0: clocking to 48000
[   45.654774] kjournald starting.  Commit interval 5 seconds
[   45.672089] EXT3-fs (sda7): using internal journal
[   45.672095] EXT3-fs (sda7): mounted filesystem with ordered data mode
[   50.936174] init: failsafe main process (809) killed by TERM signal
[   51.640192] Bluetooth: Core ver 2.16
[   51.640225] NET: Registered protocol family 31
[   51.640227] Bluetooth: HCI device and connection manager initialized
[   51.640231] Bluetooth: HCI socket layer initialized
[   51.640234] Bluetooth: L2CAP socket layer initialized
[   51.640862] Bluetooth: SCO socket layer initialized
[   51.660752] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   51.660756] Bluetooth: BNEP filters: protocol multicast
[   51.715763] type=1400 audit(1359151325.984:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=891 comm="apparmor_parser"
[   51.724838] type=1400 audit(1359151325.996:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=891 comm="apparmor_parser"
[   51.874587] Bluetooth: RFCOMM TTY layer initialized
[   51.874600] Bluetooth: RFCOMM socket layer initialized
[   51.874602] Bluetooth: RFCOMM ver 1.11
[   51.934729] type=1400 audit(1359151326.204:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=881 comm="apparmor_parser"
[   51.938197] type=1400 audit(1359151326.208:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=911 comm="apparmor_parser"
[   51.938482] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   51.939724] type=1400 audit(1359151326.208:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=911 comm="apparmor_parser"
[   51.940266] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   51.941583] type=1400 audit(1359151326.212:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=911 comm="apparmor_parser"
[   52.028168] type=1400 audit(1359151326.300:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=912 comm="apparmor_parser"
[   52.035530] type=1400 audit(1359151326.304:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=912 comm="apparmor_parser"
[   52.037271] type=1400 audit(1359151326.308:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=912 comm="apparmor_parser"
[   52.038596] type=1400 audit(1359151326.308:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=912 comm="apparmor_parser"
[   52.479908] composite sync not supported
[   52.519269] hsfich 0000:00:1e.3: PCI INT B disabled
[   52.726534] hsfich 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   52.733507] hsfich 0000:00:1e.3: setting latency timer to 64
[   53.173274] ttySHSF0 at I/O 0xee00 (irq = 17) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[   53.197575] usbcore: registered new interface driver hsfusbcd2
[   53.304234] composite sync not supported
[   56.115451] init: plymouth-stop pre-start process (1469) terminated with status 1
[   57.541385] composite sync not supported
[   59.734811] composite sync not supported
[   63.152023] eth2: no IPv6 routers present
[   82.541618] composite sync not supported
```
The only lines in dmesg that looked suspicious to me were:```
[   52.038596] type=1400 audit(1359151326.308:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=912 comm="apparmor_parser"
[   52.479908] composite sync not supported
[   52.519269] hsfich 0000:00:1e.3: PCI INT B disabled
[   52.726534] hsfich 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   52.733507] hsfich 0000:00:1e.3: setting latency timer to 64
[   53.173274] ttySHSF0 at I/O 0xee00 (irq = 17) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[   53.197575] usbcore: registered new interface driver hsfusbcd2
[   53.304234] composite sync not supported
[   56.115451] init: plymouth-stop pre-start process (1469) terminated with status 1
[   57.541385] composite sync not supported
[   59.734811] composite sync not supported
[   63.152023] eth2: no IPv6 routers present
[   82.541618] composite sync not supported

```

---

### Post by Ralph L on 2013-03-15
I did a clean install, did an update, and then did my customization, and everything worked.  Don't know what caused the problem.

---

