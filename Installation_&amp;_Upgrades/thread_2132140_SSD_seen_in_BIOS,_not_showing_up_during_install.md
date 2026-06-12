---
title: "SSD seen in BIOS, not showing up during install"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by squishywalrus on 2013-04-03
Building a new system.  The SSD is detected and appears in BIOS, but I can't find it when I got to install (unable to create and new partition, no disk displayed).   In the live environment, fdisk only displays the usb stick the live environment is running on.  Any ideas?

motherboard:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157334](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157334)

ssd:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820171740](http://www.newegg.com/Product/Product.aspx?Item=N82E16820171740)

dmesg output:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-23-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 (Ubuntu 3.5.0-23.35~precise1-generic 3.5.7.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009bbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009bc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009de7afff] usable
[    0.000000] BIOS-e820: [mem 0x000000009de7b000-0x000000009e184fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009e185000-0x000000009e4d3fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009e4d4000-0x000000009ec3ffff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009ec40000-0x000000009ec40fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009ec41000-0x000000009ee46fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009ee47000-0x000000009f262fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f263000-0x000000009f7f2fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009f7f3000-0x000000009f7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed40000-0x00000000fed44fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000013effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./FM2A75 Pro4-M, BIOS P1.80 11/02/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x13f000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-D4FFF write-protect
[    0.000000]   D5000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 00009F800000 mask FFFFFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000013f000000 aka 5104M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2552MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2552M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2552MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0x9f800000-0xffffffff] usable ==> reserved
[    0.000000] found SMP MP-table at [mem 0x000fd810-0x000fd81f] mapped at [c00fd810]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0097000] 97000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x7f070000-0x7fffefff]
[    0.000000] Allocated new RAMDISK: [mem 0x36c6f000-0x37bfda7d]
[    0.000000] Move RAMDISK from [mem 0x7f070000-0x7fffea7d] to [mem 0x36c6f000-0x37bfda7d]
[    0.000000] ACPI: RSDP 000f0490 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 9e4c3078 00074 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 9e4c98f0 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20120320/tbfadt-579)
[    0.000000] ACPI: DSDT 9e4c3188 06766 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 9e4ccd80 00040
[    0.000000] ACPI: APIC 9e4c99e8 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 9e4c9a60 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 9e4c9aa8 0003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
[    0.000000] ACPI: AAFT 9e4c9ae8 000E7 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 9e4c9bd0 00038 (v01 ALASKA    A M I 01072009 AMI  00000005)
[    0.000000] ACPI: SSDT 9e4c9c08 00D40 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 9e4ca948 004B7 (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: CRAT 9e4cae00 002F8 (v01 AMD    AGESA    00000001 AMD  00000001)
[    0.000000] ACPI: BGRT 9e4cb0f8 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4212MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0x9de7afff]
[    0.000000]   node   0: [mem 0x9ec40000-0x9ec40fff]
[    0.000000]   node   0: [mem 0x9ee47000-0x9f262fff]
[    0.000000]   node   0: [mem 0x9f7f3000-0x9f7fffff]
[    0.000000]   node   0: [mem 0x00001000-0x3effffff]
[    0.000000] On node 0 totalpages: 905775
[    0.000000] free_area_init_node: node 0, pgdat c18ca8c0, node_mem_map f448e200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8425 pages used for memmap
[    0.000000]   HighMem zone: 669117 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 5, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0x9f800000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f4444000 s34176 r0 d23168 u57344
[    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 895566
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash -- BOOT_IMAGE=/casper/vmlinuz 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 10452864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0013f000)
[    0.000000] Memory: 3544240k/5226496k available (6060k kernel code, 78860k reserved, 2993k data, 760k init, 2710168k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc18d8000 - 0xc1996000   ( 760 kB)
[    0.000000]       .data : 0xc15eb215 - 0xc18d7780   (2993 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15eb215   (6060 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f340a000 soft=f340c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3727.583 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 7455.16 BogoMIPS (lpj=14910332)
[    0.000057] pid_max: default: 32768 minimum: 301
[    0.000099] Security Framework initialized
[    0.000134] AppArmor: AppArmor initialized
[    0.000161] Yama: becoming mindful.
[    0.000220] Mount-cache hash table entries: 512
[    0.000380] Initializing cgroup subsys cpuacct
[    0.000409] Initializing cgroup subsys memory
[    0.000440] Initializing cgroup subsys devices
[    0.000467] Initializing cgroup subsys freezer
[    0.000494] Initializing cgroup subsys blkio
[    0.000521] Initializing cgroup subsys perf_event
[    0.000565] CPU: Physical Processor ID: 0
[    0.000592] CPU: Processor Core ID: 0
[    0.000621] mce: CPU supports 7 MCE banks
[    0.002067] ACPI: Core revision 20120320
[    0.026840] ftrace: allocating 27176 entries in 54 pages
[    0.035110] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.035414] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075024] CPU0: AMD A8-5500 APU with Radeon(tm) HD Graphics     stepping 01
[    0.180652] Performance Events: AMD Family 15h PMU driver.
[    0.180705] ... version:                0
[    0.180732] ... bit width:              48
[    0.180758] ... generic registers:      6
[    0.180785] ... value mask:             0000ffffffffffff
[    0.180812] ... max period:             00007fffffffffff
[    0.180840] ... fixed-purpose events:   0
[    0.180867] ... event mask:             000000000000003f
[    0.180989] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.181080] CPU 1 irqstacks, hard=f34cc000 soft=f34ce000
[    0.191186] Initializing CPU#1
[    0.181081] Booting Node   0, Processors  #1
[    0.194198] CPU 2 irqstacks, hard=f34e0000 soft=f34e2000
[    0.204190] Initializing CPU#2
[    0.194252]  #2
[    0.207320] CPU 3 irqstacks, hard=f34ec000 soft=f34ee000
[    0.207372]  #3 Ok.
[    0.217358] Initializing CPU#3
[    0.220407] Brought up 4 CPUs
[    0.220460] Total of 4 processors activated (29820.66 BogoMIPS).
[    0.221292] devtmpfs: initialized
[    0.221469] EVM: security.selinux
[    0.221495] EVM: security.SMACK64
[    0.221522] EVM: security.capability
[    0.221679] PM: Registering ACPI NVS region [mem 0x9e185000-0x9e4d3fff] (3469312 bytes)
[    0.221751] PM: Registering ACPI NVS region [mem 0x9ec41000-0x9ee46fff] (2121728 bytes)
[    0.222554] dummy: 
[    0.222600] RTC time:  5:59:02, date: 04/04/13
[    0.222652] NET: Registered protocol family 16
[    0.224343] EISA bus registered
[    0.224369] Trying to unpack rootfs image as initramfs...
[    0.224524] ACPI: bus type pci registered
[    0.224594] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.224625] PCI: not using MMCONFIG
[    0.232077] PCI: Using configuration type 1 for base access
[    0.232104] PCI: Using configuration type 1 for extended access
[    0.232942] bio: create slab <bio-0> at 0
[    0.233034] ACPI: Added _OSI(Module Device)
[    0.233062] ACPI: Added _OSI(Processor Device)
[    0.233090] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.233118] ACPI: Added _OSI(Processor Aggregator Device)
[    0.234000] ACPI: EC: Look up EC in DSDT
[    0.234982] ACPI: Executed 1 blocks of module-level executable AML code
[    0.237260] ACPI: Interpreter enabled
[    0.237290] ACPI: (supports S0 S3 S4 S5)
[    0.237423] ACPI: Using IOAPIC for interrupt routing
[    0.237549] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.237606] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.237636] PCI: Using MMCONFIG for extended config space
[    1.723690] ACPI: No dock devices found.
[    1.723725] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.723946] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.724129] pci_root PNP0A03:00: host bridge window [io  0x0000-0x03af]
[    1.724158] pci_root PNP0A03:00: host bridge window [io  0x03e0-0x0cf7]
[    1.724187] pci_root PNP0A03:00: host bridge window [io  0x03b0-0x03df]
[    1.724217] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    1.724245] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.724276] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    1.724307] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xffffffff]
[    1.724361] PCI host bridge to bus 0000:00
[    1.724390] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    1.724418] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    1.724446] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    1.724475] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.724502] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.724531] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    1.724560] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff]
[    1.724594] pci 0000:00:00.0: [1022:1410] type 00 class 0x060000
[    1.724624] pci 0000:00:01.0: [1002:9904] type 00 class 0x030000
[    1.724631] pci 0000:00:01.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    1.724636] pci 0000:00:01.0: reg 14: [io  0xf000-0xf0ff]
[    1.724640] pci 0000:00:01.0: reg 18: [mem 0xff700000-0xff73ffff]
[    1.724669] pci 0000:00:01.0: supports D1 D2
[    1.724681] pci 0000:00:01.1: [1002:9902] type 00 class 0x040300
[    1.724687] pci 0000:00:01.1: reg 10: [mem 0xff744000-0xff747fff]
[    1.724722] pci 0000:00:01.1: supports D1 D2
[    1.724757] pci 0000:00:10.0: [1022:7812] type 00 class 0x0c0330
[    1.724773] pci 0000:00:10.0: reg 10: [mem 0xff74a000-0xff74bfff 64bit]
[    1.724851] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
[    1.724883] pci 0000:00:10.1: [1022:7812] type 00 class 0x0c0330
[    1.724898] pci 0000:00:10.1: reg 10: [mem 0xff748000-0xff749fff 64bit]
[    1.724977] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
[    1.725005] pci 0000:00:11.0: [1022:7801] type 00 class 0x010601
[    1.725019] pci 0000:00:11.0: reg 10: [io  0xf140-0xf147]
[    1.725026] pci 0000:00:11.0: reg 14: [io  0xf130-0xf133]
[    1.725033] pci 0000:00:11.0: reg 18: [io  0xf120-0xf127]
[    1.725040] pci 0000:00:11.0: reg 1c: [io  0xf110-0xf113]
[    1.725047] pci 0000:00:11.0: reg 20: [io  0xf100-0xf10f]
[    1.725054] pci 0000:00:11.0: reg 24: [mem 0xff751000-0xff7517ff]
[    1.725096] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
[    1.725106] pci 0000:00:12.0: reg 10: [mem 0xff750000-0xff750fff]
[    1.725157] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
[    1.725171] pci 0000:00:12.2: reg 10: [mem 0xff74f000-0xff74f0ff]
[    1.725230] pci 0000:00:12.2: supports D1 D2
[    1.725231] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.725248] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
[    1.725258] pci 0000:00:13.0: reg 10: [mem 0xff74e000-0xff74efff]
[    1.725309] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
[    1.725322] pci 0000:00:13.2: reg 10: [mem 0xff74d000-0xff74d0ff]
[    1.725381] pci 0000:00:13.2: supports D1 D2
[    1.725382] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.725399] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
[    1.725454] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
[    1.725469] pci 0000:00:14.2: reg 10: [mem 0xff740000-0xff743fff 64bit]
[    1.725516] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.725527] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
[    1.725583] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
[    1.725613] pci 0000:00:14.5: [1022:7809] type 00 class 0x0c0310
[    1.725623] pci 0000:00:14.5: reg 10: [mem 0xff74c000-0xff74cfff]
[    1.725674] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
[    1.725727] pci 0000:00:15.0: supports D1 D2
[    1.725746] pci 0000:00:15.3: [1022:43a3] type 01 class 0x060400
[    1.725799] pci 0000:00:15.3: supports D1 D2
[    1.725817] pci 0000:00:18.0: [1022:1400] type 00 class 0x060000
[    1.725832] pci 0000:00:18.1: [1022:1401] type 00 class 0x060000
[    1.725846] pci 0000:00:18.2: [1022:1402] type 00 class 0x060000
[    1.725860] pci 0000:00:18.3: [1022:1403] type 00 class 0x060000
[    1.725878] pci 0000:00:18.4: [1022:1404] type 00 class 0x060000
[    1.725891] pci 0000:00:18.5: [1022:1405] type 00 class 0x060000
[    1.725954] pci 0000:00:14.4: PCI bridge to [bus 01-01] (subtractive decode)
[    1.725988] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    1.725989] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    1.725991] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    1.725993] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.725994] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.725996] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    1.725998] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    1.726032] pci 0000:00:15.0: PCI bridge to [bus 02-02]
[    1.726114] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    1.726128] pci 0000:03:00.0: reg 10: [io  0xe000-0xe0ff]
[    1.726151] pci 0000:03:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    1.726166] pci 0000:03:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    1.726232] pci 0000:03:00.0: supports D1 D2
[    1.726234] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.734264] pci 0000:00:15.3: PCI bridge to [bus 03-03]
[    1.734299] pci 0000:00:15.3:   bridge window [io  0xe000-0xefff]
[    1.734306] pci 0000:00:15.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    1.734319] pci_bus 0000:00: on NUMA node 0
[    1.734325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.734477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    1.734520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE20._PRT]
[    1.734544] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE23._PRT]
[    1.734640]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.734827]  pci0000:00: ACPI _OSC control (0x19) granted
[    1.738607] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 10 11 14 15) *0
[    1.738913] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 10 11 14 15) *0
[    1.739219] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 11 14 15) *0
[    1.739522] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 10 11 14 15) *0
[    1.739821] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
[    1.740110] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
[    1.740397] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
[    1.740684] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
[    1.741018] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    1.741058] vgaarb: loaded
[    1.741084] vgaarb: bridge control possible 0000:00:01.0
[    1.741250] SCSI subsystem initialized
[    1.741333] libata version 3.00 loaded.
[    1.741347] ACPI: bus type usb registered
[    1.741387] usbcore: registered new interface driver usbfs
[    1.741420] usbcore: registered new interface driver hub
[    1.741470] usbcore: registered new device driver usb
[    1.741562] PCI: Using ACPI for IRQ routing
[    1.747556] PCI: pci_cache_line_size set to 64 bytes
[    1.747617] e820: reserve RAM buffer [mem 0x0009bc00-0x0009ffff]
[    1.747619] e820: reserve RAM buffer [mem 0x9de7b000-0x9fffffff]
[    1.747621] e820: reserve RAM buffer [mem 0x9ec41000-0x9fffffff]
[    1.747623] e820: reserve RAM buffer [mem 0x9f263000-0x9fffffff]
[    1.747624] e820: reserve RAM buffer [mem 0x9f800000-0x9fffffff]
[    1.747625] e820: reserve RAM buffer [mem 0x13f000000-0x13fffffff]
[    1.747689] NetLabel: Initializing
[    1.747717] NetLabel:  domain hash size = 128
[    1.747745] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.747778] NetLabel:  unlabeled traffic allowed by default
[    1.747881] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.748004] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    1.750044] Switching to clocksource hpet
[    2.920093] AppArmor: AppArmor Filesystem Enabled
[    2.920144] pnp: PnP ACPI init
[    2.920182] ACPI: bus type pnp registered
[    2.920338] pnp 00:00: [bus 00-ff]
[    2.920340] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.920342] pnp 00:00: [io  0x0000-0x03af window]
[    2.920344] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    2.920345] pnp 00:00: [io  0x03b0-0x03df window]
[    2.920347] pnp 00:00: [io  0x0d00-0xffff window]
[    2.920349] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.920350] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    2.920352] pnp 00:00: [mem 0xc0000000-0xffffffff window]
[    2.920353] pnp 00:00: [mem 0x00000000 window]
[    2.920390] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    2.920413] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    2.920454] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    2.920485] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.920830] pnp 00:02: [io  0x0010-0x001f]
[    2.920832] pnp 00:02: [io  0x0022-0x003f]
[    2.920833] pnp 00:02: [io  0x0063]
[    2.920834] pnp 00:02: [io  0x0065]
[    2.920836] pnp 00:02: [io  0x0067-0x006f]
[    2.920837] pnp 00:02: [io  0x0072-0x007f]
[    2.920838] pnp 00:02: [io  0x0080]
[    2.920840] pnp 00:02: [io  0x0084-0x0086]
[    2.920841] pnp 00:02: [io  0x0088]
[    2.920842] pnp 00:02: [io  0x008c-0x008e]
[    2.920844] pnp 00:02: [io  0x0090-0x009f]
[    2.920845] pnp 00:02: [io  0x00a2-0x00bf]
[    2.920846] pnp 00:02: [io  0x00b1]
[    2.920847] pnp 00:02: [io  0x00e0-0x00ef]
[    2.920849] pnp 00:02: [io  0x04d0-0x04d1]
[    2.920850] pnp 00:02: [io  0x040b]
[    2.920851] pnp 00:02: [io  0x04d6]
[    2.920853] pnp 00:02: [io  0x0c00-0x0c01]
[    2.920854] pnp 00:02: [io  0x0c14]
[    2.920855] pnp 00:02: [io  0x0c50-0x0c51]
[    2.920857] pnp 00:02: [io  0x0c52]
[    2.920858] pnp 00:02: [io  0x0c6c]
[    2.920859] pnp 00:02: [io  0x0c6f]
[    2.920860] pnp 00:02: [io  0x0cd0-0x0cd1]
[    2.920862] pnp 00:02: [io  0x0cd2-0x0cd3]
[    2.920863] pnp 00:02: [io  0x0cd4-0x0cd5]
[    2.920864] pnp 00:02: [io  0x0cd6-0x0cd7]
[    2.920866] pnp 00:02: [io  0x0cd8-0x0cdf]
[    2.920867] pnp 00:02: [io  0x0800-0x089f]
[    2.920869] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    2.920870] pnp 00:02: [io  0x0000-0x000f]
[    2.920872] pnp 00:02: [io  0x0b20-0x0b3f]
[    2.920873] pnp 00:02: [io  0x0900-0x090f]
[    2.920875] pnp 00:02: [io  0x0910-0x091f]
[    2.920876] pnp 00:02: [io  0xfe00-0xfefe]
[    2.920877] pnp 00:02: [io  0x0060-0x005f disabled]
[    2.920879] pnp 00:02: [io  0x0064-0x0063 disabled]
[    2.920880] pnp 00:02: [mem 0xfec00000-0xfec00fff]
[    2.920882] pnp 00:02: [mem 0xfee00000-0xfee00fff]
[    2.920883] pnp 00:02: [mem 0xfed80000-0xfed8ffff]
[    2.920885] pnp 00:02: [mem 0xfed61000-0xfed70fff]
[    2.920886] pnp 00:02: [mem 0xfec10000-0xfec10fff]
[    2.920887] pnp 00:02: [mem 0xfed00000-0xfed00fff]
[    2.920889] pnp 00:02: [mem 0xff800000-0xffffffff]
[    2.920941] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    2.920970] system 00:02: [io  0x040b] has been reserved
[    2.920998] system 00:02: [io  0x04d6] has been reserved
[    2.921027] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    2.921056] system 00:02: [io  0x0c14] has been reserved
[    2.921084] system 00:02: [io  0x0c50-0x0c51] has been reserved
[    2.921112] system 00:02: [io  0x0c52] has been reserved
[    2.921141] system 00:02: [io  0x0c6c] has been reserved
[    2.921169] system 00:02: [io  0x0c6f] has been reserved
[    2.921197] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    2.921226] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    2.921255] system 00:02: [io  0x0cd4-0x0cd5] has been reserved
[    2.921284] system 00:02: [io  0x0cd6-0x0cd7] has been reserved
[    2.921312] system 00:02: [io  0x0cd8-0x0cdf] has been reserved
[    2.921341] system 00:02: [io  0x0800-0x089f] has been reserved
[    2.921370] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    2.921398] system 00:02: [io  0x0900-0x090f] has been reserved
[    2.921427] system 00:02: [io  0x0910-0x091f] has been reserved
[    2.921455] system 00:02: [io  0xfe00-0xfefe] has been reserved
[    2.921484] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    2.921513] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    2.921542] system 00:02: [mem 0xfed80000-0xfed8ffff] has been reserved
[    2.921570] system 00:02: [mem 0xfed61000-0xfed70fff] has been reserved
[    2.921599] system 00:02: [mem 0xfec10000-0xfec10fff] has been reserved
[    2.921628] system 00:02: [mem 0xfed00000-0xfed00fff] has been reserved
[    2.921658] system 00:02: [mem 0xff800000-0xffffffff] has been reserved
[    2.921687] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.921728] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    2.921730] pnp 00:03: [io  0x0290-0x029f]
[    2.921731] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    2.921760] system 00:03: [io  0x0290-0x029f] has been reserved
[    2.921790] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.922029] pnp 00:04: [io  0x0378-0x037f]
[    2.922031] pnp 00:04: [io  0x0778-0x077f]
[    2.922040] pnp 00:04: [irq 5]
[    2.922041] pnp 00:04: [dma 3]
[    2.922132] pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
[    2.922268] pnp 00:05: [dma 4]
[    2.922270] pnp 00:05: [io  0x0000-0x000f]
[    2.922271] pnp 00:05: [io  0x0081-0x0083]
[    2.922273] pnp 00:05: [io  0x0087]
[    2.922274] pnp 00:05: [io  0x0089-0x008b]
[    2.922275] pnp 00:05: [io  0x008f]
[    2.922276] pnp 00:05: [io  0x00c0-0x00df]
[    2.922294] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.922301] pnp 00:06: [io  0x0070-0x0071]
[    2.922304] pnp 00:06: [irq 8]
[    2.922323] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.922329] pnp 00:07: [io  0x0061]
[    2.922346] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    2.922363] pnp 00:08: [io  0x0010-0x001f]
[    2.922365] pnp 00:08: [io  0x0022-0x003f]
[    2.922366] pnp 00:08: [io  0x0044-0x005f]
[    2.922367] pnp 00:08: [io  0x0072-0x007f]
[    2.922368] pnp 00:08: [io  0x0080]
[    2.922370] pnp 00:08: [io  0x0084-0x0086]
[    2.922371] pnp 00:08: [io  0x0088]
[    2.922372] pnp 00:08: [io  0x008c-0x008e]
[    2.922373] pnp 00:08: [io  0x0090-0x009f]
[    2.922375] pnp 00:08: [io  0x00a2-0x00bf]
[    2.922376] pnp 00:08: [io  0x00e0-0x00ef]
[    2.922377] pnp 00:08: [io  0x04d0-0x04d1]
[    2.922422] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    2.922451] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.922457] pnp 00:09: [io  0x00f0-0x00ff]
[    2.922461] pnp 00:09: [irq 13]
[    2.922479] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.922519] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.922694] pnp 00:0b: [io  0x03f8-0x03ff]
[    2.922697] pnp 00:0b: [irq 4]
[    2.922699] pnp 00:0b: [dma 0 disabled]
[    2.922740] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    2.922822] pnp 00:0c: [mem 0xa0000000-0xbfffffff]
[    2.922857] system 00:0c: [mem 0xa0000000-0xbfffffff] has been reserved
[    2.922887] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.922981] pnp 00:0d: [mem 0xfed00000-0xfed003ff]
[    2.923009] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    2.923011] pnp: PnP ACPI: found 14 devices
[    2.923039] ACPI: ACPI bus type pnp unregistered
[    2.923068] PnPBIOS: Disabled by ACPI PNP
[    2.926338] Freeing initrd memory: 15932k freed
[    2.959247] pci 0000:00:14.4: PCI bridge to [bus 01-01]
[    2.959284] pci 0000:00:15.0: PCI bridge to [bus 02-02]
[    2.959318] pci 0000:00:15.3: PCI bridge to [bus 03-03]
[    2.959347] pci 0000:00:15.3:   bridge window [io  0xe000-0xefff]
[    2.959379] pci 0000:00:15.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    2.959428] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    2.959430] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    2.959432] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    2.959433] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    2.959435] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    2.959437] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    2.959438] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
[    2.959440] pci_bus 0000:01: resource 4 [io  0x0000-0x03af]
[    2.959442] pci_bus 0000:01: resource 5 [io  0x03e0-0x0cf7]
[    2.959443] pci_bus 0000:01: resource 6 [io  0x03b0-0x03df]
[    2.959445] pci_bus 0000:01: resource 7 [io  0x0d00-0xffff]
[    2.959446] pci_bus 0000:01: resource 8 [mem 0x000a0000-0x000bffff]
[    2.959448] pci_bus 0000:01: resource 9 [mem 0x000c0000-0x000dffff]
[    2.959450] pci_bus 0000:01: resource 10 [mem 0xc0000000-0xffffffff]
[    2.959452] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    2.959453] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    2.959476] NET: Registered protocol family 2
[    2.959539] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.959661] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.959902] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.960028] TCP: Hash tables configured (established 131072 bind 65536)
[    2.960056] TCP: reno registered
[    2.960083] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    2.960114] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    2.960176] NET: Registered protocol family 1
[    2.960213] pci 0000:00:01.0: Boot video device
[    3.201758] PCI: CLS 64 bytes, default 64
[    3.202101] LVT offset 0 assigned for vector 0x400
[    3.202150] perf: AMD IBS detected (0x000000ff)
[    3.202368] audit: initializing netlink socket (disabled)
[    3.202410] type=2000 audit(1365055145.080:1): initialized
[    3.219455] highmem bounce pool size: 64 pages
[    3.219497] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.221038] VFS: Disk quotas dquot_6.5.2
[    3.221097] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.221565] fuse init (API version 7.19)
[    3.221656] msgmni has been set to 1660
[    3.222037] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    3.222093] io scheduler noop registered
[    3.222121] io scheduler deadline registered (default)
[    3.222152] io scheduler cfq registered
[    3.222327] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.222366] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.222484] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    3.222516] ACPI: Power Button [PWRB]
[    3.222572] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.222604] ACPI: Power Button [PWRF]
[    3.222735] ACPI: acpi_idle registered with cpuidle
[    3.227598] GHES: HEST is not enabled!
[    3.227707] isapnp: Scanning for PnP cards...
[    3.227719] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.247945] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.269055] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.269252] Linux agpgart interface v0.103
[    3.270316] brd: module loaded
[    3.270829] loop: module loaded
[    3.270926] ahci 0000:00:11.0: version 3.0
[    3.270966] ahci 0000:00:11.0: irq 40 for MSI/MSI-X
[    3.271023] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x21 impl SATA mode
[    3.271056] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio slum part sxs 
[    3.271483] scsi0 : ahci
[    3.271567] scsi1 : ahci
[    3.271640] scsi2 : ahci
[    3.271715] scsi3 : ahci
[    3.271788] scsi4 : ahci
[    3.271863] scsi5 : ahci
[    3.272113] ata1: SATA max UDMA/133 abar m2048@0xff751000 port 0xff751100 irq 40
[    3.272144] ata2: DUMMY
[    3.272172] ata3: DUMMY
[    3.272200] ata4: DUMMY
[    3.272227] ata5: DUMMY
[    3.272255] ata6: SATA max UDMA/133 abar m2048@0xff751000 port 0xff751380 irq 40
[    3.272560] Fixed MDIO Bus: probed
[    3.272618] tun: Universal TUN/TAP device driver, 1.6
[    3.272647] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.272707] PPP generic driver version 2.4.2
[    3.274385] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.274433] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.274465] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.274499] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.274544] QUIRK: Enable AMD PLL fix
[    3.274552] ehci_hcd 0000:00:12.2: debug port 1
[    3.274592] ehci_hcd 0000:00:12.2: irq 17, io mem 0xff74f000
[    3.285522] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    3.285582] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.285614] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.285648] usb usb1: Product: EHCI Host Controller
[    3.285675] usb usb1: Manufacturer: Linux 3.5.0-23-generic ehci_hcd
[    3.285704] usb usb1: SerialNumber: 0000:00:12.2
[    3.285828] hub 1-0:1.0: USB hub found
[    3.285858] hub 1-0:1.0: 5 ports detected
[    3.285955] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.285986] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    3.286020] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.286065] ehci_hcd 0000:00:13.2: debug port 1
[    3.286102] ehci_hcd 0000:00:13.2: irq 17, io mem 0xff74d000
[    3.297489] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    3.297539] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    3.297568] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.297599] usb usb2: Product: EHCI Host Controller
[    3.297626] usb usb2: Manufacturer: Linux 3.5.0-23-generic ehci_hcd
[    3.297655] usb usb2: SerialNumber: 0000:00:13.2
[    3.297792] hub 2-0:1.0: USB hub found
[    3.297822] hub 2-0:1.0: 5 ports detected
[    3.297915] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.297976] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    3.298006] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    3.298055] ohci_hcd 0000:00:12.0: irq 18, io mem 0xff750000
[    3.357325] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    3.357358] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.357390] usb usb3: Product: OHCI Host Controller
[    3.357418] usb usb3: Manufacturer: Linux 3.5.0-23-generic ohci_hcd
[    3.357447] usb usb3: SerialNumber: 0000:00:12.0
[    3.357571] hub 3-0:1.0: USB hub found
[    3.357602] hub 3-0:1.0: 5 ports detected
[    3.357691] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.357722] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    3.357764] ohci_hcd 0000:00:13.0: irq 18, io mem 0xff74e000
[    3.417190] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    3.417223] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.417254] usb usb4: Product: OHCI Host Controller
[    3.417283] usb usb4: Manufacturer: Linux 3.5.0-23-generic ohci_hcd
[    3.417311] usb usb4: SerialNumber: 0000:00:13.0
[    3.417448] hub 4-0:1.0: USB hub found
[    3.417479] hub 4-0:1.0: 5 ports detected
[    3.417569] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    3.417600] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
[    3.417641] ohci_hcd 0000:00:14.5: irq 18, io mem 0xff74c000
[    3.477017] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    3.477050] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.477081] usb usb5: Product: OHCI Host Controller
[    3.477109] usb usb5: Manufacturer: Linux 3.5.0-23-generic ohci_hcd
[    3.477137] usb usb5: SerialNumber: 0000:00:14.5
[    3.477264] hub 5-0:1.0: USB hub found
[    3.477295] hub 5-0:1.0: 2 ports detected
[    3.477374] uhci_hcd: USB Universal Host Controller Interface driver
[    3.477442] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    3.477473] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    3.477673] xhci_hcd 0000:00:10.0: irq 18, io mem 0xff74a000
[    3.477742] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
[    3.477746] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    3.477751] xhci_hcd 0000:00:10.0: irq 43 for MSI/MSI-X
[    3.477755] xhci_hcd 0000:00:10.0: irq 44 for MSI/MSI-X
[    3.477759] xhci_hcd 0000:00:10.0: irq 45 for MSI/MSI-X
[    3.477826] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    3.477854] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.477885] usb usb6: Product: xHCI Host Controller
[    3.477914] usb usb6: Manufacturer: Linux 3.5.0-23-generic xhci_hcd
[    3.477943] usb usb6: SerialNumber: 0000:00:10.0
[    3.478018] xHCI xhci_add_endpoint called for root hub
[    3.478019] xHCI xhci_check_bandwidth called for root hub
[    3.478035] hub 6-0:1.0: USB hub found
[    3.478066] hub 6-0:1.0: 2 ports detected
[    3.478130] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    3.478161] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    3.481091] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
[    3.481119] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.481150] usb usb7: Product: xHCI Host Controller
[    3.481177] usb usb7: Manufacturer: Linux 3.5.0-23-generic xhci_hcd
[    3.481206] usb usb7: SerialNumber: 0000:00:10.0
[    3.481278] xHCI xhci_add_endpoint called for root hub
[    3.481279] xHCI xhci_check_bandwidth called for root hub
[    3.481296] hub 7-0:1.0: USB hub found
[    3.481327] hub 7-0:1.0: 2 ports detected
[    3.579961] isapnp: No Plug & Play device found
[    3.580865] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    3.580901] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    3.581106] xhci_hcd 0000:00:10.1: irq 17, io mem 0xff748000
[    3.581175] xhci_hcd 0000:00:10.1: irq 46 for MSI/MSI-X
[    3.581180] xhci_hcd 0000:00:10.1: irq 47 for MSI/MSI-X
[    3.581184] xhci_hcd 0000:00:10.1: irq 48 for MSI/MSI-X
[    3.581188] xhci_hcd 0000:00:10.1: irq 49 for MSI/MSI-X
[    3.581192] xhci_hcd 0000:00:10.1: irq 50 for MSI/MSI-X
[    3.581266] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    3.581296] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.581326] usb usb8: Product: xHCI Host Controller
[    3.581354] usb usb8: Manufacturer: Linux 3.5.0-23-generic xhci_hcd
[    3.581383] usb usb8: SerialNumber: 0000:00:10.1
[    3.581541] xHCI xhci_add_endpoint called for root hub
[    3.581542] xHCI xhci_check_bandwidth called for root hub
[    3.581560] hub 8-0:1.0: USB hub found
[    3.581590] hub 8-0:1.0: 2 ports detected
[    3.581661] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    3.581690] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
[    3.584521] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    3.584549] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.584580] usb usb9: Product: xHCI Host Controller
[    3.584608] usb usb9: Manufacturer: Linux 3.5.0-23-generic xhci_hcd
[    3.584637] usb usb9: SerialNumber: 0000:00:10.1
[    3.584783] xHCI xhci_add_endpoint called for root hub
[    3.584784] xHCI xhci_check_bandwidth called for root hub
[    3.584800] hub 9-0:1.0: USB hub found
[    3.584830] hub 9-0:1.0: 2 ports detected
[    3.584982] usbcore: registered new interface driver libusual
[    3.585044] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    3.587656] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.587689] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.587874] mousedev: PS/2 mouse device common for all mice
[    3.588000] rtc_cmos 00:06: RTC can wake from S4
[    3.588094] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.588138] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.588201] device-mapper: uevent: version 1.0.3
[    3.588269] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    3.588319] EISA: Probing bus 0 at eisa.0
[    3.588347] EISA: Cannot allocate resource for mainboard
[    3.588374] Cannot allocate resource for EISA slot 1
[    3.588401] Cannot allocate resource for EISA slot 2
[    3.588429] Cannot allocate resource for EISA slot 3
[    3.588457] Cannot allocate resource for EISA slot 4
[    3.588485] Cannot allocate resource for EISA slot 5
[    3.588513] Cannot allocate resource for EISA slot 6
[    3.588540] Cannot allocate resource for EISA slot 7
[    3.588568] Cannot allocate resource for EISA slot 8
[    3.588595] EISA: Detected 0 cards.
[    3.588680] cpuidle: using governor ladder
[    3.588737] ata1: SATA link down (SStatus 0 SControl 300)
[    3.588764] cpuidle: using governor menu
[    3.588765] EFI Variables Facility v0.08 2004-May-17
[    3.588853] ata6: SATA link down (SStatus 0 SControl 300)
[    3.588930] ashmem: initialized
[    3.589053] TCP: cubic registered
[    3.589149] NET: Registered protocol family 10
[    3.589293] NET: Registered protocol family 17
[    3.589325] Key type dns_resolver registered
[    3.589409] Using IPI No-Shortcut mode
[    3.589532] PM: Hibernation image not present or could not be loaded.
[    3.589540] registered taskstats version 1
[    3.591506] Key type trusted registered
[    3.593056] Key type encrypted registered
[    3.594848]   Magic number: 9:257:971
[    3.594941] rtc_cmos 00:06: setting system clock to 2013-04-04 05:59:05 UTC (1365055145)
[    3.595021] powernow-k8: Found 1 AMD A8-5500 APU with Radeon(tm) HD Graphics     (4 cpu cores) (version 2.20.00)
[    3.595065] powernow-k8: Core Performance Boosting: on.
[    3.595138] powernow-k8:    0 : pstate 0 (3200 MHz)
[    3.595165] powernow-k8:    1 : pstate 1 (2900 MHz)
[    3.595193] powernow-k8:    2 : pstate 2 (2600 MHz)
[    3.595221] powernow-k8:    3 : pstate 3 (2200 MHz)
[    3.595248] powernow-k8:    4 : pstate 4 (1800 MHz)
[    3.595276] powernow-k8:    5 : pstate 5 (1400 MHz)
[    3.595706] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.595735] EDD information not available.
[    3.595932] Freeing unused kernel memory: 760k freed
[    3.596182] Write protecting the kernel text: 6064k
[    3.596232] Write protecting the kernel read-only data: 2488k
[    3.596260] NX-protecting the kernel data: 4176k
[    3.616131] udevd[117]: starting version 175
[    3.640297] [drm] Initialized drm 1.1.0 20060810
[    3.651284] [drm] radeon defaulting to kernel modesetting.
[    3.651317] [drm] radeon kernel modesetting enabled.
[    3.651582] [drm] initializing kernel modesetting (ARUBA 0x1002:0x9904 0x1849:0x9901).
[    3.651653] [drm] register mmio base: 0xFF700000
[    3.653340] [drm] register mmio size: 262144
[    3.653603] ATOM BIOS: 113
[    3.653652] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    3.653687] radeon 0000:00:01.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[    3.654167] [drm] Detected VRAM RAM=512M, BAR=256M
[    3.654199] [drm] RAM width 64bits DDR
[    3.656350] [TTM] Zone  kernel: Available graphics memory: 425382 kiB
[    3.656384] [TTM] Zone highmem: Available graphics memory: 1780466 kiB
[    3.656413] [TTM] Initializing pool allocator
[    3.656445] [TTM] Initializing DMA pool allocator
[    3.656724] [drm] radeon: 512M of VRAM memory ready
[    3.656755] [drm] radeon: 512M of GTT memory ready.
[    3.656801] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.656833] [drm] Driver supports precise vblank timestamp query.
[    3.656894] radeon 0000:00:01.0: irq 51 for MSI/MSI-X
[    3.656910] radeon 0000:00:01.0: radeon: using MSI.
[    3.657392] [drm] radeon: irq initialized.
[    3.657425] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    3.657990] [drm] Loading ARUBA Microcode
[    3.667712] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.667866] r8169 0000:03:00.0: irq 52 for MSI/MSI-X
[    3.668076] r8169 0000:03:00.0: eth0: RTL8168evl/8111evl at 0xf840e000, bc:5f:f4:83:e7:dd, XID 0c900800 IRQ 52
[    3.668110] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    3.712516] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[    3.712635] radeon 0000:00:01.0: WB enabled
[    3.712664] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffc8ac00
[    3.712697] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffc8ac04
[    3.712729] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffc8ac08
[    3.731349] [drm] ring test on 0 succeeded in 2 usecs
[    3.731913] [drm] ib test on ring 0 succeeded in 0 usecs
[    3.740428] [drm] Radeon Display Connectors
[    3.740458] [drm] Connector 0:
[    3.740486] [drm]   VGA-1
[    3.740515] [drm]   HPD1
[    3.740541] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    3.740571] [drm]   Encoders:
[    3.740598] [drm]     CRT1: INTERNAL_UNIPHY2
[    3.740625] [drm]     CRT1: NUTMEG
[    3.740652] [drm] Connector 1:
[    3.740679] [drm]   HDMI-A-1
[    3.740705] [drm]   HPD2
[    3.740732] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    3.740762] [drm]   Encoders:
[    3.740789] [drm]     DFP1: INTERNAL_UNIPHY2
[    3.740817] [drm] Connector 2:
[    3.740844] [drm]   DVI-D-1
[    3.740870] [drm]   HPD3
[    3.740896] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    3.740927] [drm]   Encoders:
[    3.740954] [drm]     DFP2: INTERNAL_UNIPHY
[    3.789394] [drm] Internal thermal controller without fan control
[    3.789439] [drm] radeon: power management initialized
[    3.931867] usb 3-3: new low-speed USB device number 2 using ohci_hcd
[    4.017400] [drm] fb mappable at 0xC1144000
[    4.017431] [drm] vram apper at 0xC0000000
[    4.017457] [drm] size 8294400
[    4.017484] [drm] fb depth is 24
[    4.017511] [drm]    pitch is 7680
[    4.017662] fbcon: radeondrmfb (fb0) is primary device
[    4.083180] Console: switching to colour frame buffer device 240x67
[    4.088713] fb0: radeondrmfb frame buffer device
[    4.088734] drm: registered panic notifier
[    4.088756] [drm] Initialized radeon 2.18.0 20080528 for 0000:00:01.0 on minor 0
[    4.098477] usb 3-3: New USB device found, idVendor=099a, idProduct=7202
[    4.098479] usb 3-3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    4.098480] usb 3-3: Product: Wireless Keyboard/Mouse
[    4.114453] usbcore: registered new interface driver usbhid
[    4.114484] usbhid: USB HID core driver
[    4.116250] input: Wireless Keyboard/Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input2
[    4.116388] hid-generic 0003:099A:7202.0001: input,hidraw0: USB HID v1.11 Keyboard [Wireless Keyboard/Mouse] on usb-0000:00:12.0-3/input0
[    4.116716] input: Wireless Keyboard/Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input3
[    4.116973] hid-generic 0003:099A:7202.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Wireless Keyboard/Mouse] on usb-0000:00:12.0-3/input1
[    4.199171] Refined TSC clocksource calibration: 3727.525 MHz.
[    4.199227] Switching to clocksource tsc
[    4.211085] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    4.344514] usb 2-1: New USB device found, idVendor=0781, idProduct=5575
[    4.344568] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.344617] usb 2-1: Product: Cruzer Glide
[    4.344653] usb 2-1: Manufacturer: SanDisk
[    4.344689] usb 2-1: SerialNumber: 20043513930760538685
[    4.346992] usbcore: registered new interface driver uas
[    4.355160] Initializing USB Mass Storage driver...
[    4.355386] scsi6 : usb-storage 2-1:1.0
[    4.355804] usbcore: registered new interface driver usb-storage
[    4.355844] USB Mass Storage support registered.
[    4.573133] Btrfs loaded
[    4.577595] xor: automatically using best checksumming function:
[    4.613993]    avx       :  4508.000 MB/sec
[    4.614410] device-mapper: dm-raid45: initialized v0.2594b
[    5.353699] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Glide     1.26 PQ: 0 ANSI: 5
[    5.354445] sd 6:0:0:0: Attached scsi generic sg0 type 0
[    5.355803] sd 6:0:0:0: [sda] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[    5.356625] sd 6:0:0:0: [sda] Write Protect is off
[    5.356629] sd 6:0:0:0: [sda] Mode Sense: 43 00 00 00
[    5.357419] sd 6:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    5.363236]  sda: sda1
[    5.365964] sd 6:0:0:0: [sda] Attached SCSI removable disk
[    5.876419] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   11.783485] EXT2-fs (loop1): warning: mounting unchecked fs, running e2fsck is recommended
[   24.538726] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.572883] udevd[2122]: starting version 175
[   24.809500] Bluetooth: Core ver 2.16
[   24.809534] NET: Registered protocol family 31
[   24.809536] Bluetooth: HCI device and connection manager initialized
[   24.809537] Bluetooth: HCI socket layer initialized
[   24.809538] Bluetooth: L2CAP socket layer initialized
[   24.809542] Bluetooth: SCO socket layer initialized
[   24.823429] Bluetooth: RFCOMM TTY layer initialized
[   24.823433] Bluetooth: RFCOMM socket layer initialized
[   24.823435] Bluetooth: RFCOMM ver 1.11
[   24.823622] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.823623] Bluetooth: BNEP filters: protocol multicast
[   24.827846] lp: driver loaded but no devices found
[   24.847205] ppdev: user-space parallel port driver
[   24.857411] parport_pc 00:04: reported by Plug and Play ACPI
[   24.857438] parport0: PC-style at 0x378, irq 5 [PCSPP,EPP]
[   24.946627] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   24.953577] lp0: using parport0 (interrupt-driven).
[   24.958029] microcode: CPU0: patch_level=0x06001116
[   25.025971] device-mapper: multipath: version 1.4.0 loaded
[   25.139684] microcode: failed to load file amd-ucode/microcode_amd_fam15h.bin
[   25.139693] microcode: CPU1: patch_level=0x06001116
[   25.141277] microcode: failed to load file amd-ucode/microcode_amd_fam15h.bin
[   25.141498] microcode: CPU2: patch_level=0x06001116
[   25.142782] microcode: failed to load file amd-ucode/microcode_amd_fam15h.bin
[   25.142793] microcode: CPU3: patch_level=0x06001116
[   25.144074] microcode: failed to load file amd-ucode/microcode_amd_fam15h.bin
[   25.144176] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   25.194044] kvm: Nested Virtualization enabled
[   25.194047] kvm: Nested Paging enabled
[   25.210421] hda-intel: Force to non-snoop mode
[   25.210460] snd_hda_intel 0000:00:01.1: irq 53 for MSI/MSI-X
[   25.245670] init: failsafe main process (2390) killed by TERM signal
[   25.699047] init: alsa-restore main process (2522) terminated with status 19
[   25.749225] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input4
[   25.820134] input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input5
[   25.820204] input: HD-Audio Generic Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input6
[   25.820263] input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
[   25.820323] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   25.820381] input: HD-Audio Generic Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[   25.820439] input: HD-Audio Generic Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   25.820497] input: HD-Audio Generic Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   26.278882] r8169 0000:03:00.0: eth0: link down
[   26.279025] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.279279] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.892983] r8169 0000:03:00.0: eth0: link up
[   27.893085] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

---

### Post by oldfred on 2013-04-03
Do you have SSD connected to the asmedia ports? Many have reported that as an issue.

Some BIOS issues users have reported.

>  Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!



---

### Post by ninjalogic on 2013-05-16
What I did was went into Raid Utility and deleted the array and it finally detected it, then once the usb installed the OS, you have to go back to raid utility then select new array change it to stripe then finish it it will ask is you want to clear mbr select no then when it comes back to main screen press "B" to set as bootable, then exit weird eh personally this needs to be fixed it should have the same options as any other operating system, detect ALL drives including SSD, delete partitions, create partitions, format drives and choose what drive you want, like how windows is... because honestly probably about 75% of users are migrating from windows, why make it harder than it should be

---

### Post by oldfred on 2013-05-16
New UltraBooks are using RAID somehow, but normally RAID was only a sever configuration.

Ubuntu used to have an alternative installer for the few cases of RAID on desktops, but new versions do not have that version. They planned on adding all the RAID drivers and install to the Desktop but have not finished updates to allow for that.

If you do not have RAID it is not an issue.

Have you tried to install Windows on a system with Linux or really anything else? It does not even see Linux formatted partitions and you have to create the Windows partitions in advance for it to install into.

---

