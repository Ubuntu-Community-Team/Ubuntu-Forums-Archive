---
title: "installing Ubuntu Server 12.04 on a nokia ip380 firewall"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by pierref on 2012-06-06
Hello

I am trying to install Ubuntu 12.04 (server) on a Nokia IP380 firewall. It is an embedded system with serial console access. I ever was been able to boot with a previous version of Ubuntu, but in this case, the system freezes at boot time. 

I don't see find the logs of the booting kernel something that helps be to resolve this case. 

Any help would be appreciated. Here are the logs:

```
General Software Pentium III Embedded BIOS (tm) Version 4.3
Copyright (C) 2000 General Software, Inc.
Nokia NIC Trooper BIOS Version 1.1


00000640K Low Memory Passed
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic-pae (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SM)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI not present or invalid.
[    0.000000] last_pfn = 0x10000 max_arch_pfn = 0x1000000
[    0.000000] PAT not supported by CPU.
[    0.000000] init_memory_mapping: 0000000000000000-0000000010000000
[    0.000000] RAMDISK: 0f9d6000 - 0fff0000
[    0.000000] ACPI Error: A valid RSDP was not found (20110623/tbxfroot-219)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 10000000
[    0.000000]   low ram: 0 - 10000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00010000
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00010000
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- reenabling.
[    0.000000] Found and enabled local APIC!
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 10000000:eff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @cf400000 s34240 r0 d23104 u2097152
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64911
[    0.000000] Kernel command line: nousb lapic initrd=initrd.gz console=ttyS0,9600n8 BOOT_IMAGE=vmlinuz 
[    0.000000] PID hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1048320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 241716k/262144k available (5825k kernel code, 19976k reserved, 2850k data, 740k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xd0800000 - 0xffbfe000   ( 755 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1932000   ( 740 kB)
[    0.000000]       .data : 0xc15b04bc - 0xc1878d00   (2850 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b04bc   (5825 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [ttyS0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 866.427 MHz processor.
[    0.012006] Calibrating delay loop (skipped), value calculated using timer frequency.. 1732.85 BogoMIPS (lpj=3465708)
[    0.020009] pid_max: default: 32768 minimum: 301
[    0.024075] Security Framework initialized
[    0.028066] AppArmor: AppArmor initialized
[    0.032008] Yama: becoming mindful.
[    0.036233] Mount-cache hash table entries: 512
[    0.044043] Initializing cgroup subsys cpuacct
[    0.048023] Initializing cgroup subsys memory
[    0.052033] Initializing cgroup subsys devices
[    0.056012] Initializing cgroup subsys freezer
[    0.060011] Initializing cgroup subsys blkio
[    0.064028] Initializing cgroup subsys perf_event
[    0.068089] CPU serial number disabled.
[    0.072014] mce: CPU supports 5 MCE banks
[    0.076215] SMP alternatives: switching to UP code
[    0.103439] Freeing SMP alternatives: 24k freed
[    0.104068] ftrace: allocating 26594 entries in 53 pages
[    0.112289] weird, boot CPU (#0) not listed by the BIOS.
[    0.116021] SMP motherboard not detected.
[    0.120015] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.232038] SMP disabled
[    0.236020] Performance Events: p6 PMU driver.
[    0.244026] ... version:                0
[    0.248019] ... bit width:              32
[    0.252019] ... generic registers:      2
[    0.256019] ... value mask:             00000000ffffffff
[    0.260019] ... max period:             000000007fffffff
[    0.264019] ... fixed-purpose events:   0
[    0.268020] ... event mask:             0000000000000003
[    0.272709] NMI watchdog enabled, takes one hw-pmu counter.
[    0.276251] Brought up 1 CPUs
[    0.280034] Total of 1 processors activated (1732.85 BogoMIPS).
[    0.284730] devtmpfs: initialized
[    0.288487] EVM: security.selinux
[    0.292024] EVM: security.SMACK64
[    0.296023] EVM: security.capability
[    0.308745] print_constraints: dummy: 
[    0.312100] RTC time: 23:28:51, date: 01/01/80
[    0.316163] NET: Registered protocol family 16
[    0.320440] EISA bus registered
[    0.324270] PCI: PCI BIOS revision 2.10 entry at 0xe7c3e, last bus=4
[    0.328027] PCI: Using configuration type 1 for base access
[    0.337494] bio: create slab <bio-0> at 0
[    0.340348] ACPI: Interpreter disabled.
[    0.348085] vgaarb: loaded
[    0.352436] i2c-core: driver [aat2870] using legacy suspend method
[    0.356028] i2c-core: driver [aat2870] using legacy resume method
[    0.360304] SCSI subsystem initialized
[    0.364271] usbcore: USB support disabled
[    0.368351] PCI: Probing PCI hardware
[    0.372186] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.372190] * this clock source is slow. If you are sure your timer does not have
[    0.372195] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.376095] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.376100] * this clock source is slow. If you are sure your timer does not have
[    0.376104] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.385701] PCI: Discovered peer bus 02
[    0.393016] PCI: Discovered peer bus 03
[    0.396633] PCI: Discovered peer bus 04
[    0.401606] NetLabel: Initializing
[    0.404042] NetLabel:  domain hash size = 128
[    0.408029] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.412061] NetLabel:  unlabeled traffic allowed by default
[    0.450856] AppArmor: AppArmor Filesystem Enabled
[    0.452138] pnp: PnP ACPI: disabled
[    0.456038] PnPBIOS: Scanning system for PnP BIOS support...
[    0.460220] PnPBIOS: PnP BIOS support was not detected.
[    0.474880] pci 0000:02:04.0: address space collision: [mem 0xff000000-0xff0fffff pref] conflicts with 0000:02:03.0 [mem 0xff000]
[    0.476056] pci 0000:02:05.0: address space collision: [mem 0xff000000-0xff0fffff pref] conflicts with 0000:02:03.0 [mem 0xff000]
[    0.480044] pci 0000:02:06.0: address space collision: [mem 0xff000000-0xff0fffff pref] conflicts with 0000:02:03.0 [mem 0xff000]
[    0.484044] pci 0000:03:05.0: address space collision: [mem 0xff000000-0xff03ffff pref] conflicts with 0000:02:03.0 [mem 0xff000]
[    0.488044] pci 0000:03:06.0: address space collision: [mem 0xff000000-0xff03ffff pref] conflicts with 0000:02:03.0 [mem 0xff000]
[    0.492045] pci 0000:04:05.0: address space collision: [mem 0xff000000-0xff03ffff pref] conflicts with 0000:02:03.0 [mem 0xff000]
[    0.496044] pci 0000:04:06.0: address space collision: [mem 0xff000000-0xff03ffff pref] conflicts with 0000:02:03.0 [mem 0xff000]
[    0.500092] pci 0000:00:09.0: BAR 0: assigned [mem 0x10000000-0x10000fff]
[    0.504048] pci 0000:00:09.0: BAR 0: set to [mem 0x10000000-0x10000fff] (PCI address [0x10000000-0x10000fff])
[    0.508042] pci 0000:00:09.1: BAR 0: assigned [mem 0x14000000-0x14000fff]
[    0.512044] pci 0000:00:09.1: BAR 0: set to [mem 0x14000000-0x14000fff] (PCI address [0x14000000-0x14000fff])
[    0.516044] pci 0000:00:09.1: BAR 16: assigned [mem 0x18000000-0x1bffffff]
[    0.520044] pci 0000:00:09.1: BAR 15: assigned [mem 0x1c000000-0x1fffffff pref]
[    0.524047] pci 0000:00:09.1: BAR 14: assigned [io  0x1000-0x10ff]
[    0.528044] pci 0000:00:09.1: BAR 13: assigned [io  0x1400-0x14ff]
[    0.532044] pci 0000:00:09.0: BAR 16: assigned [mem 0x20000000-0x23ffffff]
[    0.536045] pci 0000:00:09.0: BAR 15: assigned [mem 0x24000000-0x27ffffff pref]
[    0.540045] pci 0000:00:09.0: BAR 14: assigned [io  0x1800-0x18ff]
[    0.544046] pci 0000:00:09.0: BAR 13: assigned [io  0x1c00-0x1cff]
[    0.548043] pci 0000:00:09.0: CardBus bridge to [bus 01-04]
[    0.552041] pci 0000:00:09.0:   bridge window [io  0x1c00-0x1cff]
[    0.556044] pci 0000:00:09.0:   bridge window [io  0x1800-0x18ff]
[    0.560045] pci 0000:00:09.0:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.564044] pci 0000:00:09.0:   bridge window [mem 0x20000000-0x23ffffff]
[    0.568045] pci 0000:00:09.1: CardBus bridge to [bus 05-08]
[    0.572042] pci 0000:00:09.1:   bridge window [io  0x1400-0x14ff]
[    0.576045] pci 0000:00:09.1:   bridge window [io  0x1000-0x10ff]
[    0.580046] pci 0000:00:09.1:   bridge window [mem 0x1c000000-0x1fffffff pref]
[    0.584046] pci 0000:00:09.1:   bridge window [mem 0x18000000-0x1bffffff]
[    0.588056] pci 0000:02:04.0: BAR 6: assigned [mem 0x10100000-0x101fffff pref]
[    0.592048] pci 0000:02:05.0: BAR 6: assigned [mem 0x10200000-0x102fffff pref]
[    0.596048] pci 0000:02:06.0: BAR 6: assigned [mem 0x10300000-0x103fffff pref]
[    0.600052] pci 0000:03:05.0: BAR 6: assigned [mem 0x10040000-0x1007ffff pref]
[    0.604049] pci 0000:03:06.0: BAR 6: assigned [mem 0x10080000-0x100bffff pref]
[    0.608053] pci 0000:04:05.0: BAR 6: assigned [mem 0x100c0000-0x100fffff pref]
[    0.612049] pci 0000:04:06.0: BAR 6: assigned [mem 0x10400000-0x1043ffff pref]
[    0.616054] pci 0000:00:09.0: enabling device (0000 -> 0003)
[    0.620052] pci 0000:00:09.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    0.624065] pci 0000:00:09.1: enabling device (0000 -> 0003)
[    0.628049] pci 0000:00:09.1: can't find IRQ for PCI INT B; please try using pci=biosirq
[    0.632357] NET: Registered protocol family 2
[    0.640263] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.644728] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.648211] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.652220] TCP: Hash tables configured (established 8192 bind 8192)
[    0.656052] TCP reno registered
[    0.660055] UDP hash table entries: 128 (order: 0, 4096 bytes)
[    0.664075] UDP-Lite hash table entries: 128 (order: 0, 4096 bytes)
[    0.668362] NET: Registered protocol family 1
```

---

