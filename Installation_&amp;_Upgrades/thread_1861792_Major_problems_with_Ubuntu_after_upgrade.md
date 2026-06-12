---
title: "Major problems with Ubuntu after upgrade"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by jorritTyb on 2011-10-16
A few days ago I upgraded from Ubuntu 10.something to ubuntu 11.something. I did it because at that point I got a message saying an update was ready. So I clicked ok. At first I got a few glitches but I got everything to work.

But occasionally I had a problem after boot. Linux would boot up and the purple ubuntu startup screen would come up. But then it would switch back to text with no real error visible. I could then switch to other text consoles and there manually type /sbin/shutdown -r now to try again. And then it usually worked.

But today I got no such luck. It fails every time to boot up correctly. I get the ubuntu startup screen and it ends up with a text console full of messages. The weird thing is that these messages are always different. Most of the time they all end with [Ok]. Sometimes there is a [Fail].

I can always switch to a text console but I don't know what to do there to correct the situation. At this moment I'm booted into windows but I'd love to go back to Linux obviously.

I don't know what kind of information you need from me so that you can help you. Also everytime I boot things are different (but still wrong). I also would like to note that I *never* had any problems with Ubuntu 10.x.

Here is the dmesg output of one of the cases where the boot failed:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=2328aa0a-fb0a-425a-8e34-31a510d1a4df ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000df7c0000 (usable)
[    0.000000]  BIOS-e820: 00000000df7c0000 - 00000000df7c3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df7c3000 - 00000000df7e0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000df7e0000 - 00000000df800000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000021f800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. H67A-USB3-B3/H67A-USB3-B3, BIOS F5 03/31/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x21f800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CCFFF write-protect
[    0.000000]   CD000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 100000000 mask F00000000 write-back
[    0.000000]   3 base 200000000 mask FE0000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 2, base: 4GB, range: 4GB, type WB
[    0.000000] reg 3, base: 8GB, range: 512MB, type WB
[    0.000000] total RAM covered: 8192M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64K 	num_reg: 5  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 512MB, type WB
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdf7c0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f5a10] f5a10
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000df7c0000
[    0.000000]  0000000000 - 00df600000 page 2M
[    0.000000]  00df600000 - 00df7c0000 page 4k
[    0.000000] kernel direct mapping tables up to df7c0000 @ df7ba000-df7c0000
[    0.000000] init_memory_mapping: 0000000100000000-000000021f800000
[    0.000000]  0100000000 - 021f800000 page 2M
[    0.000000] kernel direct mapping tables up to 21f800000 @ 21f7f6000-21f800000
[    0.000000] RAMDISK: 35950000 - 36ca0000
[    0.000000] ACPI: RSDP 00000000000f7180 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000df7c3040 0004C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000df7c3100 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000df7c31c0 047D3 (v01 GBT    GBTUACPI 00001000 MSFT 04000000)
[    0.000000] ACPI: FACS 00000000df7c0000 00040
[    0.000000] ACPI: HPET 00000000df7c7b00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000df7c7b80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: ASPT 00000000df7c7c00 00034 (v07 GBT    PerfTune 312E3042 UTBG 01010101)
[    0.000000] ACPI: SSPT 00000000df7c7c40 02350 (v01 GBT    SsptHead 312E3042 UTBG 01010101)
[    0.000000] ACPI: EUDS 00000000df7c9f90 000C0 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: MATS 00000000df7ca050 00034 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000df7ca0b0 008CA (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000df7c7a00 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 00000000df7ca980 01F4C (v01  INTEL PPM RCM  80000001 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000021f800000
[    0.000000] Initmem setup node 0 0000000000000000-000000021f800000
[    0.000000]   NODE_DATA [000000021f7fb000 - 000000021f7fffff]
[    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880216e00000-ffff88021dffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0021f800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000df7c0
[    0.000000]     0: 0x00100000 -> 0x0021f800
[    0.000000] On node 0 totalpages: 2092877
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 897016 pages, LIFO batch:31
[    0.000000]   Normal zone: 16100 pages used for memmap
[    0.000000]   Normal zone: 1161500 pages, LIFO batch:31
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
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df7c0000 - 00000000df7c3000
[    0.000000] PM: Registered nosave memory: 00000000df7c3000 - 00000000df7e0000
[    0.000000] PM: Registered nosave memory: 00000000df7e0000 - 00000000df800000
[    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at df800000 (gap: df800000:10800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021f400000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2062436
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=2328aa0a-fb0a-425a-8e34-31a510d1a4df ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8154488k/8904704k available (6104k kernel code, 533196k absent, 217020k reserved, 4880k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3092.487 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6184.97 BogoMIPS (lpj=12369948)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000021] Security Framework initialized
[    0.000031] AppArmor: AppArmor initialized
[    0.000032] Yama: becoming mindful.
[    0.000596] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001899] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002414] Mount-cache hash table entries: 256
[    0.002489] Initializing cgroup subsys cpuacct
[    0.002492] Initializing cgroup subsys memory
[    0.002497] Initializing cgroup subsys devices
[    0.002498] Initializing cgroup subsys freezer
[    0.002499] Initializing cgroup subsys net_cls
[    0.002501] Initializing cgroup subsys blkio
[    0.002504] Initializing cgroup subsys perf_event
[    0.002523] CPU: Physical Processor ID: 0
[    0.002523] CPU: Processor Core ID: 0
[    0.002527] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002527] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002530] mce: CPU supports 9 MCE banks
[    0.002540] CPU0: Thermal monitoring enabled (TM1)
[    0.002547] using mwait in idle threads.
[    0.004269] ACPI: Core revision 20110413
[    0.010352] ftrace: allocating 25651 entries in 101 pages
[    0.017390] x2apic not enabled, IRQ remapping init failed
[    0.017718] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057387] CPU0: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz stepping 07
[    0.164350] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.164354] ... version:                3
[    0.164355] ... bit width:              48
[    0.164355] ... generic registers:      8
[    0.164356] ... value mask:             0000ffffffffffff
[    0.164357] ... max period:             000000007fffffff
[    0.164358] ... fixed-purpose events:   3
[    0.164359] ... event mask:             00000007000000ff
[    0.164626] Booting Node   0, Processors  #1
[    0.164627] smpboot cpu 1: start_ip = 98000
[    0.272471]  #2
[    0.272473] smpboot cpu 2: start_ip = 98000
[    0.380415]  #3
[    0.380416] smpboot cpu 3: start_ip = 98000
[    0.488407] Brought up 4 CPUs
[    0.488409] Total of 4 processors activated (24742.68 BogoMIPS).
[    0.490272] devtmpfs: initialized
[    0.490354] PM: Registering ACPI NVS region at df7c0000 (12288 bytes)
[    0.491265] print_constraints: dummy: 
[    0.491289] Time:  7:30:38  Date: 10/16/11
[    0.491309] NET: Registered protocol family 16
[    0.491373] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.491375] ACPI: bus type pci registered
[    0.491376] Trying to unpack rootfs image as initramfs...
[    0.491412] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.491414] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.498024] PCI: Using configuration type 1 for base access
[    0.498434] bio: create slab <bio-0> at 0
[    0.498975] ACPI: EC: Look up EC in DSDT
[    0.506548] ACPI Warning: Incorrect checksum in table [TAMG] - 0xD5, should be 0xD4 (20110413/tbutils-314)
[    0.506897] ACPI: Interpreter enabled
[    0.506899] ACPI: (supports S0 S3 S4 S5)
[    0.506909] ACPI: Using IOAPIC for interrupt routing
[    0.508906] ACPI: No dock devices found.
[    0.508907] HEST: Table not found.
[    0.508909] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.508940] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.508998] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.509000] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.509001] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.509003] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.509004] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xfebfffff]
[    0.509012] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
[    0.509037] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    0.509055] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.509057] pci 0000:00:01.0: PME# disabled
[    0.509095] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.509116] pci 0000:00:16.0: reg 10: [mem 0xfbfff000-0xfbfff00f 64bit]
[    0.509173] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.509176] pci 0000:00:16.0: PME# disabled
[    0.509204] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.509223] pci 0000:00:1a.0: reg 10: [mem 0xfbffe000-0xfbffe3ff]
[    0.509290] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.509293] pci 0000:00:1a.0: PME# disabled
[    0.509313] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.509326] pci 0000:00:1b.0: reg 10: [mem 0xfbff4000-0xfbff7fff 64bit]
[    0.509376] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.509379] pci 0000:00:1b.0: PME# disabled
[    0.509395] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.509452] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.509455] pci 0000:00:1c.0: PME# disabled
[    0.509478] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    0.509535] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.509538] pci 0000:00:1c.5: PME# disabled
[    0.509559] pci 0000:00:1c.6: [8086:244e] type 1 class 0x000604
[    0.509616] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.509619] pci 0000:00:1c.6: PME# disabled
[    0.509638] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    0.509695] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.509698] pci 0000:00:1c.7: PME# disabled
[    0.509722] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.509741] pci 0000:00:1d.0: reg 10: [mem 0xfbffd000-0xfbffd3ff]
[    0.509808] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.509812] pci 0000:00:1d.0: PME# disabled
[    0.509832] pci 0000:00:1f.0: [8086:1c4a] type 0 class 0x000601
[    0.509937] pci 0000:00:1f.2: [8086:1c02] type 0 class 0x000106
[    0.509954] pci 0000:00:1f.2: reg 10: [io  0xff00-0xff07]
[    0.509960] pci 0000:00:1f.2: reg 14: [io  0xfe00-0xfe03]
[    0.509967] pci 0000:00:1f.2: reg 18: [io  0xfd00-0xfd07]
[    0.509974] pci 0000:00:1f.2: reg 1c: [io  0xfc00-0xfc03]
[    0.509980] pci 0000:00:1f.2: reg 20: [io  0xfb00-0xfb1f]
[    0.509987] pci 0000:00:1f.2: reg 24: [mem 0xfbffc000-0xfbffc7ff]
[    0.510016] pci 0000:00:1f.2: PME# supported from D3hot
[    0.510019] pci 0000:00:1f.2: PME# disabled
[    0.510032] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.510045] pci 0000:00:1f.3: reg 10: [mem 0xfbffb000-0xfbffb0ff 64bit]
[    0.510064] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
[    0.510108] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
[    0.510116] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf7ffffff]
[    0.510125] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xe7ffffff 64bit pref]
[    0.510133] pci 0000:01:00.0: reg 1c: [mem 0xec000000-0xefffffff 64bit pref]
[    0.510139] pci 0000:01:00.0: reg 24: [io  0xef00-0xef7f]
[    0.510145] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.510178] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
[    0.510186] pci 0000:01:00.1: reg 10: [mem 0xf9ffc000-0xf9ffffff]
[    0.510244] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.510246] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.510248] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf9ffffff]
[    0.510251] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.510291] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.510294] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.510298] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.510303] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.510364] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.510383] pci 0000:03:00.0: reg 10: [io  0xde00-0xdeff]
[    0.510416] pci 0000:03:00.0: reg 18: [mem 0xfbdff000-0xfbdfffff 64bit pref]
[    0.510436] pci 0000:03:00.0: reg 20: [mem 0xfbdf8000-0xfbdfbfff 64bit pref]
[    0.510494] pci 0000:03:00.0: supports D1 D2
[    0.510495] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.510500] pci 0000:03:00.0: PME# disabled
[    0.510539] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
[    0.510542] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.510545] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.510550] pci 0000:00:1c.5:   bridge window [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.510612] pci 0000:04:00.0: [1283:8892] type 1 class 0x000604
[    0.510739] pci 0000:04:00.0: supports D1 D2
[    0.510740] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.510746] pci 0000:04:00.0: PME# disabled
[    0.510768] pci 0000:00:1c.6: PCI bridge to [bus 04-05] (subtractive decode)
[    0.510772] pci 0000:00:1c.6:   bridge window [io  0xf000-0x0000] (disabled)
[    0.510775] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.510780] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.510782] pci 0000:00:1c.6:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.510783] pci 0000:00:1c.6:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.510784] pci 0000:00:1c.6:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.510786] pci 0000:00:1c.6:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.510787] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xfebfffff] (subtractive decode)
[    0.510938] pci 0000:04:00.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.510949] pci 0000:04:00.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.510955] pci 0000:04:00.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.510966] pci 0000:04:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.510968] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.510969] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.510971] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.510972] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.510974] pci 0000:04:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.510975] pci 0000:04:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.510976] pci 0000:04:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.510978] pci 0000:04:00.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.510979] pci 0000:04:00.0:   bridge window [mem 0xe0000000-0xfebfffff] (subtractive decode)
[    0.511054] pci 0000:06:00.0: [1033:0194] type 0 class 0x000c03
[    0.511079] pci 0000:06:00.0: reg 10: [mem 0xfbefe000-0xfbefffff 64bit]
[    0.511182] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.511186] pci 0000:06:00.0: PME# disabled
[    0.511225] pci 0000:00:1c.7: PCI bridge to [bus 06-06]
[    0.511229] pci 0000:00:1c.7:   bridge window [io  0xf000-0x0000] (disabled)
[    0.511232] pci 0000:00:1c.7:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.511237] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.511257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.511330] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.511347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.511366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.511382] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
[    0.511397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7._PRT]
[    0.511424]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.511425]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.511427] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.514834] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.514861] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.514887] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.514912] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.514938] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.514964] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.514991] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.515017] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.515075] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.515077] vgaarb: loaded
[    0.515078] vgaarb: bridge control possible 0000:01:00.0
[    0.515177] SCSI subsystem initialized
[    0.515213] libata version 3.00 loaded.
[    0.515236] usbcore: registered new interface driver usbfs
[    0.515241] usbcore: registered new interface driver hub
[    0.515253] usbcore: registered new device driver usb
[    0.515294] PCI: Using ACPI for IRQ routing
[    0.516688] PCI: pci_cache_line_size set to 64 bytes
[    0.516740] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.516741] reserve RAM buffer: 00000000df7c0000 - 00000000dfffffff 
[    0.516743] reserve RAM buffer: 000000021f800000 - 000000021fffffff 
[    0.516800] NetLabel: Initializing
[    0.516801] NetLabel:  domain hash size = 128
[    0.516802] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.516809] NetLabel:  unlabeled traffic allowed by default
[    0.516834] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.516837] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.518849] Switching to clocksource hpet
[    0.520275] Switched to NOHz mode on CPU #0
[    0.520337] Switched to NOHz mode on CPU #2
[    0.520369] Switched to NOHz mode on CPU #1
[    0.520405] Switched to NOHz mode on CPU #3
[    0.522293] AppArmor: AppArmor Filesystem Enabled
[    0.522309] pnp: PnP ACPI init
[    0.522318] ACPI: bus type pnp registered
[    0.522371] pnp 00:00: [bus 00-3f]
[    0.522373] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.522374] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.522376] pnp 00:00: [io  0x0d00-0xffff window]
[    0.522378] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.522379] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.522380] pnp 00:00: [mem 0xe0000000-0xfebfffff window]
[    0.522412] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.522459] pnp 00:01: [io  0x0010-0x001f]
[    0.522460] pnp 00:01: [io  0x0022-0x003f]
[    0.522461] pnp 00:01: [io  0x0044-0x005f]
[    0.522462] pnp 00:01: [io  0x0062-0x0063]
[    0.522463] pnp 00:01: [io  0x0065-0x006f]
[    0.522464] pnp 00:01: [io  0x0074-0x007f]
[    0.522465] pnp 00:01: [io  0x0091-0x0093]
[    0.522466] pnp 00:01: [io  0x00a2-0x00bf]
[    0.522467] pnp 00:01: [io  0x00e0-0x00ef]
[    0.522468] pnp 00:01: [io  0x04d0-0x04d1]
[    0.522469] pnp 00:01: [io  0x0290-0x029f]
[    0.522470] pnp 00:01: [io  0x0800-0x087f]
[    0.522471] pnp 00:01: [io  0x0290-0x0294]
[    0.522472] pnp 00:01: [io  0x0880-0x088f]
[    0.522499] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.522500] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.522502] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.522503] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.522505] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.522507] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.522513] pnp 00:02: [dma 4]
[    0.522514] pnp 00:02: [io  0x0000-0x000f]
[    0.522515] pnp 00:02: [io  0x0080-0x0090]
[    0.522516] pnp 00:02: [io  0x0094-0x009f]
[    0.522517] pnp 00:02: [io  0x00c0-0x00df]
[    0.522532] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.522560] pnp 00:03: [irq 0 disabled]
[    0.522566] pnp 00:03: [irq 8]
[    0.522567] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.522581] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.522595] pnp 00:04: [io  0x0070-0x0073]
[    0.522608] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.522613] pnp 00:05: [io  0x0061]
[    0.522626] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.522632] pnp 00:06: [io  0x00f0-0x00ff]
[    0.522635] pnp 00:06: [irq 13]
[    0.522648] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.522798] pnp 00:07: [io  0x03f8-0x03ff]
[    0.522802] pnp 00:07: [irq 4]
[    0.522835] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.522866] pnp 00:08: [io  0x0400-0x04cf]
[    0.522867] pnp 00:08: [io  0x04d2-0x04ff]
[    0.522888] system 00:08: [io  0x0400-0x04cf] has been reserved
[    0.522889] system 00:08: [io  0x04d2-0x04ff] has been reserved
[    0.522891] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.522899] pnp 00:09: [io  0x1000-0x107f]
[    0.522900] pnp 00:09: [io  0x1080-0x10ff]
[    0.522901] pnp 00:09: [io  0x1100-0x117f]
[    0.522902] pnp 00:09: [io  0x1180-0x11ff]
[    0.522923] system 00:09: [io  0x1000-0x107f] has been reserved
[    0.522924] system 00:09: [io  0x1080-0x10ff] has been reserved
[    0.522926] system 00:09: [io  0x1100-0x117f] has been reserved
[    0.522927] system 00:09: [io  0x1180-0x11ff] has been reserved
[    0.522929] system 00:09: Plug and Play ACPI device, IDs ICD0001 PNP0c02 (active)
[    0.523043] pnp 00:0a: [io  0x0454-0x0457]
[    0.523069] system 00:0a: [io  0x0454-0x0457] has been reserved
[    0.523071] system 00:0a: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.523081] pnp 00:0b: [mem 0xf0000000-0xf3ffffff]
[    0.523108] system 00:0b: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.523109] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.523212] pnp 00:0c: [mem 0x000d0a00-0x000d3fff]
[    0.523213] pnp 00:0c: [mem 0x000f0000-0x000f7fff]
[    0.523214] pnp 00:0c: [mem 0x000f8000-0x000fbfff]
[    0.523215] pnp 00:0c: [mem 0x000fc000-0x000fffff]
[    0.523216] pnp 00:0c: [mem 0xdf7c0000-0xdf7cffff]
[    0.523218] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.523219] pnp 00:0c: [mem 0x00100000-0xdf7bffff]
[    0.523220] pnp 00:0c: [mem 0xdf7d0000-0xdf7effff]
[    0.523221] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.523222] pnp 00:0c: [mem 0xfed10000-0xfed1dfff]
[    0.523223] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
[    0.523224] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.523225] pnp 00:0c: [mem 0xffb00000-0xffb7ffff]
[    0.523227] pnp 00:0c: [mem 0xfff00000-0xffffffff]
[    0.523228] pnp 00:0c: [mem 0x000e0000-0x000effff]
[    0.523229] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    0.523230] pnp 00:0c: [mem 0x40000000-0x400fffff]
[    0.523231] pnp 00:0c: [mem 0xdf800000-0xdfffffff]
[    0.523264] system 00:0c: [mem 0x000d0a00-0x000d3fff] has been reserved
[    0.523266] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.523267] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.523269] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.523270] system 00:0c: [mem 0xdf7c0000-0xdf7cffff] could not be reserved
[    0.523272] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.523273] system 00:0c: [mem 0x00100000-0xdf7bffff] could not be reserved
[    0.523275] system 00:0c: [mem 0xdf7d0000-0xdf7effff] could not be reserved
[    0.523276] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.523278] system 00:0c: [mem 0xfed10000-0xfed1dfff] has been reserved
[    0.523279] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.523281] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.523282] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.523284] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
[    0.523285] system 00:0c: [mem 0x000e0000-0x000effff] has been reserved
[    0.523287] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
[    0.523288] system 00:0c: [mem 0x40000000-0x400fffff] could not be reserved
[    0.523290] system 00:0c: [mem 0xdf800000-0xdfffffff] could not be reserved
[    0.523291] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.523302] pnp 00:0d: [mem 0xffb80000-0xffbfffff]
[    0.523320] pnp 00:0d: Plug and Play ACPI device, IDs INT0800 (active)
[    0.523324] pnp: PnP ACPI: found 14 devices
[    0.523325] ACPI: ACPI bus type pnp unregistered
[    0.528540] PCI: max bus depth: 2 pci_try_num: 3
[    0.528588] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf4000000-0xf41fffff]
[    0.528590] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.528592] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.528594] pci 0000:01:00.0: BAR 6: assigned [mem 0xe8000000-0xe807ffff pref]
[    0.528596] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.528598] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.528600] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf9ffffff]
[    0.528602] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.528605] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.528607] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.528611] pci 0000:00:1c.0:   bridge window [mem 0xf4000000-0xf41fffff]
[    0.528614] pci 0000:00:1c.0:   bridge window [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.528619] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
[    0.528621] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.528625] pci 0000:00:1c.5:   bridge window [mem disabled]
[    0.528628] pci 0000:00:1c.5:   bridge window [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.528634] pci 0000:04:00.0: PCI bridge to [bus 05-05]
[    0.528635] pci 0000:04:00.0:   bridge window [io  disabled]
[    0.528643] pci 0000:04:00.0:   bridge window [mem disabled]
[    0.528649] pci 0000:04:00.0:   bridge window [mem pref disabled]
[    0.528659] pci 0000:00:1c.6: PCI bridge to [bus 04-05]
[    0.528660] pci 0000:00:1c.6:   bridge window [io  disabled]
[    0.528664] pci 0000:00:1c.6:   bridge window [mem disabled]
[    0.528667] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.528672] pci 0000:00:1c.7: PCI bridge to [bus 06-06]
[    0.528673] pci 0000:00:1c.7:   bridge window [io  disabled]
[    0.528677] pci 0000:00:1c.7:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.528680] pci 0000:00:1c.7:   bridge window [mem pref disabled]
[    0.528693] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.528696] pci 0000:00:01.0: setting latency timer to 64
[    0.528700] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.528702] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.528706] pci 0000:00:1c.0: setting latency timer to 64
[    0.528713] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.528717] pci 0000:00:1c.5: setting latency timer to 64
[    0.528723] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.528727] pci 0000:00:1c.6: setting latency timer to 64
[    0.528735] pci 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.528743] pci 0000:04:00.0: setting latency timer to 64
[    0.528751] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.528754] pci 0000:00:1c.7: setting latency timer to 64
[    0.528757] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.528758] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.528760] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.528761] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.528762] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfebfffff]
[    0.528764] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.528765] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf9ffffff]
[    0.528767] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.528768] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.528769] pci_bus 0000:02: resource 1 [mem 0xf4000000-0xf41fffff]
[    0.528771] pci_bus 0000:02: resource 2 [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.528772] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.528773] pci_bus 0000:03: resource 2 [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.528775] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.528776] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.528777] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.528779] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000dffff]
[    0.528780] pci_bus 0000:04: resource 8 [mem 0xe0000000-0xfebfffff]
[    0.528781] pci_bus 0000:05: resource 8 [io  0x0000-0x0cf7]
[    0.528783] pci_bus 0000:05: resource 9 [io  0x0d00-0xffff]
[    0.528784] pci_bus 0000:05: resource 10 [mem 0x000a0000-0x000bffff]
[    0.528785] pci_bus 0000:05: resource 11 [mem 0x000c0000-0x000dffff]
[    0.528786] pci_bus 0000:05: resource 12 [mem 0xe0000000-0xfebfffff]
[    0.528788] pci_bus 0000:06: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.528807] NET: Registered protocol family 2
[    0.528969] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.529655] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.530649] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.530768] TCP: Hash tables configured (established 524288 bind 65536)
[    0.530770] TCP reno registered
[    0.530784] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.530810] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.530884] NET: Registered protocol family 1
[    0.562985] pci 0000:01:00.0: Boot video device
[    0.563025] PCI: CLS 4 bytes, default 64
[    0.563027] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.563028] Placing 64MB software IO TLB between ffff8800db7ba000 - ffff8800df7ba000
[    0.563030] software IO TLB at phys 0xdb7ba000 - 0xdf7ba000
[    0.563304] audit: initializing netlink socket (disabled)
[    0.563310] type=2000 audit(1318750238.404:1): initialized
[    0.584681] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.600042] VFS: Disk quotas dquot_6.5.2
[    0.600076] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.600408] fuse init (API version 7.16)
[    0.600454] msgmni has been set to 15926
[    0.600692] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.600709] io scheduler noop registered
[    0.600710] io scheduler deadline registered
[    0.600733] io scheduler cfq registered (default)
[    0.600793] pcieport 0000:00:01.0: setting latency timer to 64
[    0.600813] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.600964] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.600976] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.601001] intel_idle: MWAIT substates: 0x1120
[    0.601002] intel_idle: v0.4 model 0x2A
[    0.601003] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.601062] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.601065] ACPI: Power Button [PWRB]
[    0.601089] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.601091] ACPI: Power Button [PWRF]
[    0.601106] ACPI: acpi_idle yielding to intel_idle
[    0.603873] ERST: Table is not found!
[    0.603910] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.624307] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.752332] Freeing initrd memory: 19776k freed
[    0.919385] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.919562] Linux agpgart interface v0.103
[    0.920169] brd: module loaded
[    0.920427] loop: module loaded
[    0.920646] Fixed MDIO Bus: probed
[    0.920659] PPP generic driver version 2.4.2
[    0.920676] tun: Universal TUN/TAP device driver, 1.6
[    0.920677] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.920715] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.920728] ehci_hcd 0000:00:1a.0: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.920744] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.920746] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.920763] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.920785] ehci_hcd 0000:00:1a.0: debug port 2
[    0.924680] ehci_hcd 0000:00:1a.0: cache line size of 4 is not supported
[    0.924692] ehci_hcd 0000:00:1a.0: irq 18, io mem 0xfbffe000
[    0.938878] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.938981] hub 1-0:1.0: USB hub found
[    0.938984] hub 1-0:1.0: 2 ports detected
[    0.939023] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.939030] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.939033] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.939051] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.939069] ehci_hcd 0000:00:1d.0: debug port 2
[    0.942955] ehci_hcd 0000:00:1d.0: cache line size of 4 is not supported
[    0.942964] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbffd000
[    0.954875] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.954966] hub 2-0:1.0: USB hub found
[    0.954968] hub 2-0:1.0: 2 ports detected
[    0.955000] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.955006] uhci_hcd: USB Universal Host Controller Interface driver
[    0.955037] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.987802] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.987803] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.238899] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.238935] mousedev: PS/2 mouse device common for all mice
[    1.238985] rtc_cmos 00:04: RTC can wake from S4
[    1.239058] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.239081] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.239135] device-mapper: uevent: version 1.0.3
[    1.239172] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.239225] cpuidle: using governor ladder
[    1.239304] cpuidle: using governor menu
[    1.239305] EFI Variables Facility v0.08 2004-May-17
[    1.239425] TCP cubic registered
[    1.239489] NET: Registered protocol family 10
[    1.239728] NET: Registered protocol family 17
[    1.239735] Registering the dns_resolver key type
[    1.239786] PM: Hibernation image not present or could not be loaded.
[    1.239792] registered taskstats version 1
[    1.250839] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.251379]   Magic number: 15:444:521
[    1.251491] rtc_cmos 00:04: setting system clock to 2011-10-16 07:30:39 UTC (1318750239)
[    1.252695] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.252696] EDD information not available.
[    1.253833] Freeing unused kernel memory: 984k freed
[    1.253921] Write protecting the kernel read-only data: 10240k
[    1.254263] Freeing unused kernel memory: 20k freed
[    1.257038] Freeing unused kernel memory: 1400k freed
[    1.268043] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    1.268429] zram: num_devices not specified. Using default: 1
[    1.268430] zram: Creating 1 devices ...
[    1.270585] udevd[95]: starting version 173
[    1.283458] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.283477] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.283526] r8169 0000:03:00.0: setting latency timer to 64
[    1.283533] r8169 0000:03:00.0: (unregistered net_device): unknown MAC, using family default
[    1.283617] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
[    1.283869] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xffffc90000c6e000, 50:e5:49:35:d8:50, XID 0c900800 IRQ 41
[    1.284852] ahci 0000:00:1f.2: version 3.0
[    1.284861] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.284892] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.284915] ahci: SSS flag set, parallel bus scan disabled
[    1.286740] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.286755] xhci_hcd 0000:06:00.0: setting latency timer to 64
[    1.286759] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.287255] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 3
[    1.287421] xhci_hcd 0000:06:00.0: irq 19, io mem 0xfbefe000
[    1.287485] xhci_hcd 0000:06:00.0: irq 43 for MSI/MSI-X
[    1.287489] xhci_hcd 0000:06:00.0: irq 44 for MSI/MSI-X
[    1.287492] xhci_hcd 0000:06:00.0: irq 45 for MSI/MSI-X
[    1.287495] xhci_hcd 0000:06:00.0: irq 46 for MSI/MSI-X
[    1.287498] xhci_hcd 0000:06:00.0: irq 47 for MSI/MSI-X
[    1.287622] xHCI xhci_add_endpoint called for root hub
[    1.287623] xHCI xhci_check_bandwidth called for root hub
[    1.287640] hub 3-0:1.0: USB hub found
[    1.287646] hub 3-0:1.0: 2 ports detected
[    1.287683] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.287703] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 4
[    1.291103] xHCI xhci_add_endpoint called for root hub
[    1.291106] xHCI xhci_check_bandwidth called for root hub
[    1.291124] hub 4-0:1.0: USB hub found
[    1.291131] hub 4-0:1.0: 2 ports detected
[    1.298935] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    1.298938] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems apst 
[    1.298942] ahci 0000:00:1f.2: setting latency timer to 64
[    1.299448] Adding 4088332k swap on /dev/zram0.  Priority:100 extents:1 across:4088332k SS
[    1.339244] scsi0 : ahci
[    1.339431] scsi1 : ahci
[    1.339543] scsi2 : ahci
[    1.339657] scsi3 : ahci
[    1.339842] scsi4 : ahci
[    1.339996] scsi5 : ahci
[    1.340085] ata1: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc100 irq 42
[    1.340088] ata2: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc180 irq 42
[    1.340090] ata3: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc200 irq 42
[    1.340091] ata4: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc280 irq 42
[    1.340093] ata5: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc300 irq 42
[    1.340095] ata6: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc380 irq 42
[    1.383442] hub 1-1:1.0: USB hub found
[    1.383519] hub 1-1:1.0: 6 ports detected
[    1.494809] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.562785] Refined TSC clocksource calibration: 3092.973 MHz.
[    1.562791] Switching to clocksource tsc
[    1.627382] hub 2-1:1.0: USB hub found
[    1.627486] hub 2-1:1.0: 8 ports detected
[    1.658766] ata1: SATA link down (SStatus 0 SControl 300)
[    1.698862] usb 1-1.5: new low speed USB device number 3 using ehci_hcd
[    1.866813] usb 1-1.6: new low speed USB device number 4 using ehci_hcd
[    1.971040] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input2
[    1.971093] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.5/input0
[    1.973914] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3
[    1.973956] generic-usb 0003:046D:C313.0002: input,hidraw1: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1.6/input0
[    1.976867] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input4
[    1.976917] generic-usb 0003:046D:C313.0003: input,hidraw2: USB HID v1.10 Device [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1.6/input1
[    1.976925] usbcore: registered new interface driver usbhid
[    1.976926] usbhid: USB HID core driver
[    1.978671] ata2: SATA link down (SStatus 0 SControl 300)
[    2.470575] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.512455] ata3.00: ATA-8: ADATA SSD S599 128GB, 3.4.6, max UDMA/133
[    2.512460] ata3.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.542362] ata3.00: configured for UDMA/133
[    2.542493] scsi 2:0:0:0: Direct-Access     ATA      ADATA SSD S599 1 3.4. PQ: 0 ANSI: 5
[    2.542577] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.542642] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.542944] sd 2:0:0:0: [sda] Write Protect is off
[    2.542946] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.543021] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.543641]  sda: sda1 sda2 sda3
[    2.543954] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.034453] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.036144] ata4.00: ATAPI: Optiarc DVD RW AD-7260S, 1.03, max UDMA/100
[    3.038150] ata4.00: configured for UDMA/100
[    3.041369] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.03 PQ: 0 ANSI: 5
[    3.043567] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.043572] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.043653] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.043687] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.534340] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.540134] ata5.00: ATA-8: SAMSUNG HD103SJ, 1AJ10001, max UDMA/133
[    3.540138] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.545938] ata5.00: configured for UDMA/133
[    3.546105] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    3.546184] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.546209] sd 4:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.546261] sd 4:0:0:0: [sdb] Write Protect is off
[    3.546263] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.546278] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.551645]  sdb: sdb1 sdb2
[    3.552178] sd 4:0:0:0: [sdb] Attached SCSI disk
[    3.862280] ata6: SATA link down (SStatus 0 SControl 300)
[    4.211252] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    4.211254] vesafb: scrolling: redraw
[    4.211255] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.212877] vesafb: framebuffer at 0xed000000, mapped to 0xffffc90006880000, using 5120k, total 5120k
[    4.212946] Console: switching to colour frame buffer device 160x64
[    4.212961] fb0: VESA VGA frame buffer device
[    4.461979] Btrfs loaded
[    4.465065] xor: automatically using best checksumming function: generic_sse
[    4.482098]    generic_sse: 15114.000 MB/sec
[    4.482099] xor: using function: generic_sse (15114.000 MB/sec)
[    4.482555] device-mapper: dm-raid45: initialized v0.2594b
[    4.878548] udevd[417]: starting version 173
[    4.897961] lp: driver loaded but no devices found
[    4.919542] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    4.920058] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.920063] mei 0000:00:16.0: setting latency timer to 64
[    5.023377] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.023426] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[    5.023446] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.036715] nvidia: module license 'NVIDIA' taints kernel.
[    5.036717] Disabling lock debugging due to kernel taint
[    5.051486] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[    5.058334] type=1400 audit(1318743043.306:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=561 comm="apparmor_parser"
[    5.058575] type=1400 audit(1318743043.306:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=561 comm="apparmor_parser"
[    5.058727] type=1400 audit(1318743043.306:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=561 comm="apparmor_parser"
[    5.058972] type=1400 audit(1318743043.306:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=689 comm="apparmor_parser"
[    5.059212] type=1400 audit(1318743043.306:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=689 comm="apparmor_parser"
[    5.059363] type=1400 audit(1318743043.306:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=689 comm="apparmor_parser"
[    5.068815] hda_codec: ALC889: BIOS auto-probing.
[    5.074454] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    5.074527] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.074529] hda_intel: Disabling MSI
[    5.074569] HDA Intel 0000:01:00.1: setting latency timer to 64
[    5.185748] type=1400 audit(1318743043.430:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=979 comm="apparmor_parser"
[    5.186511] type=1400 audit(1318743043.434:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=979 comm="apparmor_parser"
[    5.186666] type=1400 audit(1318743043.434:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=979 comm="apparmor_parser"
[    5.392915] init: failsafe main process (846) killed by TERM signal
[    5.393308] init: apport pre-start process (1024) terminated with status 1
[    5.404043] init: apport post-stop process (1066) terminated with status 1
[    5.406740] init: gdm main process (1070) killed by TERM signal
[    5.438045] Bluetooth: Core ver 2.16
[    5.438059] NET: Registered protocol family 31
[    5.438060] Bluetooth: HCI device and connection manager initialized
[    5.438061] Bluetooth: HCI socket layer initialized
[    5.438062] Bluetooth: L2CAP socket layer initialized
[    5.443021] Bluetooth: SCO socket layer initialized
[    5.446556] Bluetooth: RFCOMM TTY layer initialized
[    5.446559] Bluetooth: RFCOMM socket layer initialized
[    5.446560] Bluetooth: RFCOMM ver 1.11
[    5.447130] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.447132] Bluetooth: BNEP filters: protocol multicast
[    5.486541] r8169 0000:03:00.0: eth0: link down
[    5.486546] r8169 0000:03:00.0: eth0: link down
[    5.486952] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.551710] EXT4-fs (sdb2): re-mounted. Opts: commit=0
[    5.790989] init: lightdm main process (1042) terminated with status 1
[    5.953787] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.985777] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[    6.017770] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[    6.049763] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[    6.065815] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input6
[    6.065870] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input7
[    6.065902] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[    6.065936] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[    6.066236] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.066242] nvidia 0000:01:00.0: setting latency timer to 64
[    6.066246] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    6.066390] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[    6.204535] ppdev: user-space parallel port driver
[    6.208249] audit_printk_skb: 30 callbacks suppressed
[    6.208251] type=1400 audit(1318743044.454:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1332 comm="apparmor_parser"
[    6.208548] type=1400 audit(1318743044.454:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1332 comm="apparmor_parser"
[    7.086417] r8169 0000:03:00.0: eth0: link up
[    7.086807] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.807170] eth0: no IPv6 routers present

```

The last line in the boot console was this (don't know how to copy/paste all of it here):

```

Starting the Winbind daemon winbind

```

But this message is different all the time.

What more information do you need? How can I fix my system?

Thanks in advance!

---

### Post by andho on 2011-10-16
Login to a console and type `startx`.

For me the lightdm login manager doesn't load and show the console message 'checking battery status' and just stays there. So I goto a console and startx but it's just a work around till I find a way to load lightdm.

---

### Post by jorritTyb on 2011-10-16
Ok that helps to get back into X but only as root and that's really not good. If I 'su' my user first and then do startx I get an X environment without unity. How can I then start unity?

Also this is not a really nice solution. It works so good with my previous ubuntu :-(

---

### Post by mörgæs on 2011-10-16
A lot of trouble with this upgrade. Have you thought of a fresh install?

There is a link explaining how below.

---

### Post by pamandonald on 2011-10-16
major problems after upgrade is a key fatal failure of Ubuntu 6 month cycle, so i stick on 2 years cycle Ubuntu, Long Term Support, now, i still use 10.04, and only upgrade to 12.04 after 1 year it is released and 10.04's end ofsupport. i save my time for failure system upgrade which i experienced when move from 9.04 to 9.10. 
==> or maybe i won't upgrade to 12.04 on this laptop except for new hardware, and maybe new LTS version on those laptop hehe
(many people still use 9 years old Windows XP, and they just fine)
new is not always better, for FOSS or proprietary software

---

### Post by senortroll on 2011-10-16
Actually, I'm having the same problem after a fresh install.  If I switch to a virtual console and start lightdm manually, I can then log in.

---

### Post by jorritTyb on 2011-10-21
I still haven't managed to fix this problem but I now have a clue as to what is wrong. I think that the system is trying to restore from suspend every time I boot. The kind of messages that I'm getting seem to indicate that. I remember that before things started going wrong I tried out suspend and it failed horribly. I had to forcibly power down the computer in order to get back into linux. From that point on it started to not work 100% (before it only didn't work occasionally).

Is there any way that I can convince the system (or gnome/xorg) that it doesn't have to resume from suspend after boot? I think somewhere a 'flag' is set indicating that it should resume.

Greetings,

---

### Post by manatlan on 2011-10-23
Same trouble ;-(

I think it's this bug :
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/875539](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/875539)

---

### Post by jorritTyb on 2011-10-24
Yesterday I accidently selected 'suspend' again. So I had to hard-power-down my computer again to get back into business. Strangely enough after doing that my gnome started perfectly as it should (immediatelly after boot). I was almost happy that things were fixed but unfortunatelly it didn't last. Next reboot things were back to the broken state.

Greetings,

---

