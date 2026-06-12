---
title: "Ubuntu 11.04 - Unusually long boot time (ata3: SATA link down)"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by nsudarshan on 2011-06-14
Hello,

I am trying to upgrade my sister's Acer D150 NetBook, and upgraded it to 11.04 now. The boot time of the netbook is very high now.

From the dmesg log, I see that a unusual amount of time is spent trying to mount (??) the hard disk - I see this message - [B]ata3: SATA link down (SStatus 0 SControl 300)
[/B]
The netbook used to boot fine on 10.10. I see this issue after upgrading to 11.04.
Is anyone else facing the similar issues ? Any help / suggestions is much appreciated.

I have attached the bootchart image file. Below is the full dmesg log. 

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f594000 (usable)
[    0.000000]  BIOS-e820: 000000003f594000 - 000000003f5bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f66e000 (usable)
[    0.000000]  BIOS-e820: 000000003f66e000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f6ef000 (usable)
[    0.000000]  BIOS-e820: 000000003f6ef000 - 000000003f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Acer       Aspire one      /Aspire one      , BIOS V1.11 09/04/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
[    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
[    0.000000]   2 base 000000000 mask 0E0000000 write-back
[    0.000000]   3 base 020000000 mask 0E0000000 write-back
[    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36792000 - 373c1000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 3f6f1000 06DAB (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 3f688000 00040
[    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 3f6f0000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 3f6ef000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f594
[    0.000000]     0: 0x0003f5bf -> 0x0003f66e
[    0.000000]     0: 0x0003f6bf -> 0x0003f6ef
[    0.000000]     0: 0x0003f6ff -> 0x0003f700
[    0.000000] On node 0 totalpages: 259587
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f5fa2200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32119 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257556
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=2623450a-4421-438f-a56c-4674c002554d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5196480 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f700)
[    0.000000] Memory: 1002372k/1039360k available (5188k kernel code, 35976k reserved, 2540k data, 700k init, 129496k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5408000 soft=f540a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.890 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.78 BogoMIPS (lpj=6383560)
[    0.004019] pid_max: default: 32768 minimum: 301
[    0.004077] Security Framework initialized
[    0.004115] AppArmor: AppArmor initialized
[    0.004119] Yama: becoming mindful.
[    0.004250] Mount-cache hash table entries: 512
[    0.004531] Initializing cgroup subsys ns
[    0.004541] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004549] Initializing cgroup subsys cpuacct
[    0.004561] Initializing cgroup subsys memory
[    0.004581] Initializing cgroup subsys devices
[    0.004587] Initializing cgroup subsys freezer
[    0.004593] Initializing cgroup subsys net_cls
[    0.004599] Initializing cgroup subsys blkio
[    0.004670] CPU: Physical Processor ID: 0
[    0.004675] CPU: Processor Core ID: 0
[    0.004681] mce: CPU supports 5 MCE banks
[    0.004699] CPU0: Thermal monitoring enabled (TM2)
[    0.004708] using mwait in idle threads.
[    0.010633] ACPI: Core revision 20110112
[    0.024029] ftrace: allocating 23640 entries in 47 pages
[    0.028107] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028519] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070596] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] CPU 1 irqstacks, hard=f54ca000 soft=f54cc000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.164044] Brought up 2 CPUs
[    0.164054] Total of 2 processors activated (6383.72 BogoMIPS).
[    0.164420] devtmpfs: initialized
[    0.168338] print_constraints: dummy: 
[    0.168385] Time: 18:14:39  Date: 06/14/11
[    0.168473] NET: Registered protocol family 16
[    0.168565] Trying to unpack rootfs image as initramfs...
[    0.168954] EISA bus registered
[    0.168981] ACPI: bus type pci registered
[    0.169205] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.169217] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.169224] PCI: Using MMCONFIG for extended config space
[    0.169231] PCI: Using configuration type 1 for base access
[    0.173635] bio: create slab <bio-0> at 0
[    0.179435] ACPI: EC: Look up EC in DSDT
[    0.185115] ACPI: Executed 1 blocks of module-level executable AML code
[    0.190959] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.191153] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.192393] ACPI: SSDT 3f597c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.193741] ACPI: Dynamic OEM Table Load:
[    0.193752] ACPI: SSDT   (null) 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.194212] ACPI: SSDT 3f596e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.195497] ACPI: Dynamic OEM Table Load:
[    0.195509] ACPI: SSDT   (null) 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.257009] ACPI: SSDT 3f597f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.258339] ACPI: Dynamic OEM Table Load:
[    0.258351] ACPI: SSDT   (null) 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.258764] ACPI: SSDT 3f595f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.260071] ACPI: Dynamic OEM Table Load:
[    0.260083] ACPI: SSDT   (null) 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.337164] ACPI: Interpreter enabled
[    0.337181] ACPI: (supports S0 S3 S4 S5)
[    0.337268] ACPI: Using IOAPIC for interrupt routing
[    0.522342] ACPI: Power Resource [FN00] (on)
[    0.523636] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.524191] ACPI: No dock devices found.
[    0.524202] HEST: Table not found.
[    0.524214] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.525678] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.525701] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5428a38), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.525729] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.525754] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.528301] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.528313] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xefff]
[    0.528323] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.528336] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.528375] pci 0000:00:00.0: [8086:27ac] type 0 class 0x000600
[    0.528468] pci 0000:00:02.0: [8086:27ae] type 0 class 0x000300
[    0.528494] pci 0000:00:02.0: reg 10: [mem 0x56280000-0x562fffff]
[    0.528511] pci 0000:00:02.0: reg 14: [io  0x50f0-0x50f7]
[    0.528527] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
[    0.528544] pci 0000:00:02.0: reg 1c: [mem 0x56300000-0x5633ffff]
[    0.528621] pci 0000:00:02.1: [8086:27a6] type 0 class 0x000380
[    0.528645] pci 0000:00:02.1: reg 10: [mem 0x56200000-0x5627ffff]
[    0.528801] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.528837] pci 0000:00:1b.0: reg 10: [mem 0x56340000-0x56343fff 64bit]
[    0.528950] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.528962] pci 0000:00:1b.0: PME# disabled
[    0.529012] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.529126] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.529139] pci 0000:00:1c.0: PME# disabled
[    0.529195] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.529317] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.529331] pci 0000:00:1c.1: PME# disabled
[    0.529389] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.529507] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.529519] pci 0000:00:1c.2: PME# disabled
[    0.529577] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.529654] pci 0000:00:1d.0: reg 20: [io  0x50a0-0x50bf]
[    0.529719] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.529796] pci 0000:00:1d.1: reg 20: [io  0x5080-0x509f]
[    0.529861] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.529938] pci 0000:00:1d.2: reg 20: [io  0x5060-0x507f]
[    0.530008] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.530090] pci 0000:00:1d.3: reg 20: [io  0x5040-0x505f]
[    0.530178] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.530219] pci 0000:00:1d.7: reg 10: [mem 0x56344400-0x563447ff]
[    0.530341] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.530354] pci 0000:00:1d.7: PME# disabled
[    0.530398] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.530521] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.530670] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
[    0.530682] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
[    0.530768] pci 0000:00:1f.2: [8086:27c5] type 0 class 0x000106
[    0.530805] pci 0000:00:1f.2: reg 10: [io  0x50d8-0x50df]
[    0.530826] pci 0000:00:1f.2: reg 14: [io  0x50fc-0x50ff]
[    0.530847] pci 0000:00:1f.2: reg 18: [io  0x50d0-0x50d7]
[    0.530868] pci 0000:00:1f.2: reg 1c: [io  0x50f8-0x50fb]
[    0.530889] pci 0000:00:1f.2: reg 20: [io  0x5020-0x502f]
[    0.530911] pci 0000:00:1f.2: reg 24: [mem 0x56344000-0x563443ff]
[    0.530975] pci 0000:00:1f.2: PME# supported from D3hot
[    0.530988] pci 0000:00:1f.2: PME# disabled
[    0.531031] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.531131] pci 0000:00:1f.3: reg 20: [io  0x5000-0x501f]
[    0.531312] pci 0000:01:00.0: [168c:001c] type 0 class 0x000200
[    0.531359] pci 0000:01:00.0: reg 10: [mem 0x55100000-0x5510ffff 64bit]
[    0.531546] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.531572] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.531585] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.531598] pci 0000:00:1c.0:   bridge window [mem 0x55100000-0x561fffff]
[    0.531615] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.531703] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.531716] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.531728] pci 0000:00:1c.1:   bridge window [mem 0x54100000-0x550fffff]
[    0.531745] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.531872] pci 0000:03:00.0: [1969:1026] type 0 class 0x000200
[    0.531923] pci 0000:03:00.0: reg 10: [mem 0x53000000-0x5303ffff 64bit]
[    0.531952] pci 0000:03:00.0: reg 18: [io  0x1000-0x107f]
[    0.532106] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.532121] pci 0000:03:00.0: PME# disabled
[    0.532161] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.532186] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.532198] pci 0000:00:1c.2:   bridge window [io  0x1000-0x2fff]
[    0.532211] pci 0000:00:1c.2:   bridge window [mem 0x53000000-0x540fffff]
[    0.532228] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
[    0.532353] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.532366] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.532379] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.532395] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.532406] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.532416] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xefff] (subtractive decode)
[    0.532426] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.532437] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.532478] pci_bus 0000:00: on NUMA node 0
[    0.532496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.533050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.533335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.533530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.534006] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.534031] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5428a38), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.534077]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.534293] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.534315] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5428a38), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.546576] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.546799] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.547026] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.547245] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.547459] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.547677] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.547901] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.548137] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.548537] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.548570] vgaarb: loaded
[    0.549433] SCSI subsystem initialized
[    0.549649] libata version 3.00 loaded.
[    0.549857] usbcore: registered new interface driver usbfs
[    0.549907] usbcore: registered new interface driver hub
[    0.550019] usbcore: registered new device driver usb
[    0.551846] wmi: Mapper loaded
[    0.551855] PCI: Using ACPI for IRQ routing
[    0.551864] PCI: pci_cache_line_size set to 64 bytes
[    0.552024] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.552046] reserve RAM buffer: 000000003f594000 - 000000003fffffff 
[    0.552057] reserve RAM buffer: 000000003f66e000 - 000000003fffffff 
[    0.552067] reserve RAM buffer: 000000003f6ef000 - 000000003fffffff 
[    0.552077] reserve RAM buffer: 000000003f700000 - 000000003fffffff 
[    0.552452] NetLabel: Initializing
[    0.552460] NetLabel:  domain hash size = 128
[    0.552465] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.552500] NetLabel:  unlabeled traffic allowed by default
[    0.552636] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.552651] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.552667] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.556190] Switching to clocksource hpet
[    0.559321] Switched to NOHz mode on CPU #0
[    0.559442] Switched to NOHz mode on CPU #1
[    0.579599] AppArmor: AppArmor Filesystem Enabled
[    0.579681] pnp: PnP ACPI init
[    0.579738] ACPI: bus type pnp registered
[    0.581085] pnp 00:00: [bus 00-ff]
[    0.581097] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.581106] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.581114] pnp 00:00: [io  0x0d00-0xefff window]
[    0.581123] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.581133] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.581141] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.581150] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.581159] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.581168] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.581177] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.581185] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.581194] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.581203] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.581212] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.581221] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.581229] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.581238] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.581247] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.581452] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.644644] pnp 00:01: [io  0x002e-0x002f]
[    0.644658] pnp 00:01: [io  0x004e-0x004f]
[    0.644666] pnp 00:01: [io  0x0068]
[    0.644673] pnp 00:01: [io  0x006c]
[    0.644681] pnp 00:01: [io  0x0200-0x020f]
[    0.644690] pnp 00:01: [io  0x164e-0x164f]
[    0.644698] pnp 00:01: [io  0x0061]
[    0.644706] pnp 00:01: [io  0x0070]
[    0.644714] pnp 00:01: [io  0x0080]
[    0.644722] pnp 00:01: [io  0x0092]
[    0.644730] pnp 00:01: [io  0x00b2-0x00b3]
[    0.644738] pnp 00:01: [io  0x0063]
[    0.644745] pnp 00:01: [io  0x0065]
[    0.644752] pnp 00:01: [io  0x0067]
[    0.644759] pnp 00:01: [io  0x0600-0x060f]
[    0.644767] pnp 00:01: [io  0x0610]
[    0.644774] pnp 00:01: [io  0x0800-0x080f]
[    0.644782] pnp 00:01: [io  0x0400-0x047f]
[    0.644789] pnp 00:01: [io  0x0500-0x053f]
[    0.644797] pnp 00:01: [io  0xff2c-0xff2f]
[    0.644806] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.644814] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.644822] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.644831] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.644839] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.644847] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.644856] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.644925] pnp 00:01: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.2 BAR 13 [io  0x1000-0x2fff]
[    0.645156] system 00:01: [io  0x0200-0x020f] has been reserved
[    0.645170] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.645181] system 00:01: [io  0x0610] has been reserved
[    0.645190] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.645201] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.645213] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.645224] system 00:01: [io  0xff2c-0xff2f] has been reserved
[    0.645238] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.645249] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.645261] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.645271] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.645282] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.645294] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.645305] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.645319] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.645369] pnp 00:02: [io  0x0000-0x001f]
[    0.645377] pnp 00:02: [io  0x0081-0x0091]
[    0.645392] pnp 00:02: [io  0x0093-0x009f]
[    0.645400] pnp 00:02: [io  0x00c0-0x00df]
[    0.645408] pnp 00:02: [dma 4]
[    0.645522] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.645627] pnp 00:03: [io  0x0070-0x0077]
[    0.645748] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.646006] pnp 00:04: [irq 0 disabled]
[    0.646033] pnp 00:04: [irq 8]
[    0.646042] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.646163] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.646209] pnp 00:05: [io  0x00f0]
[    0.646226] pnp 00:05: [irq 13]
[    0.646336] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.646380] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.646498] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.646612] pnp 00:07: [io  0x0060]
[    0.646622] pnp 00:07: [io  0x0064]
[    0.646640] pnp 00:07: [irq 1]
[    0.646762] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.646985] pnp 00:08: [irq 12]
[    0.647109] pnp 00:08: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
[    0.647486] pnp: PnP ACPI: found 9 devices
[    0.647494] ACPI: ACPI bus type pnp unregistered
[    0.647503] PnPBIOS: Disabled by ACPI PNP
[    0.689593] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.689608] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.689624] pci 0000:00:1c.0:   bridge window [mem 0x55100000-0x561fffff]
[    0.689637] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.689654] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.689664] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.689678] pci 0000:00:1c.1:   bridge window [mem 0x54100000-0x550fffff]
[    0.689692] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.689708] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.689718] pci 0000:00:1c.2:   bridge window [io  0x1000-0x2fff]
[    0.689732] pci 0000:00:1c.2:   bridge window [mem 0x53000000-0x540fffff]
[    0.689745] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
[    0.689761] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.689769] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.689781] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.689791] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.689849] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.689864] pci 0000:00:1c.0: setting latency timer to 64
[    0.689881] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.689905] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.689919] pci 0000:00:1c.1: setting latency timer to 64
[    0.689948] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.689961] pci 0000:00:1c.2: setting latency timer to 64
[    0.689979] pci 0000:00:1e.0: setting latency timer to 64
[    0.689991] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.690000] pci_bus 0000:00: resource 5 [io  0x0d00-0xefff]
[    0.690010] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.690019] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.690029] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.690037] pci_bus 0000:01: resource 1 [mem 0x55100000-0x561fffff]
[    0.690047] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.690057] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.690066] pci_bus 0000:02: resource 1 [mem 0x54100000-0x550fffff]
[    0.690075] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.690085] pci_bus 0000:03: resource 0 [io  0x1000-0x2fff]
[    0.690094] pci_bus 0000:03: resource 1 [mem 0x53000000-0x540fffff]
[    0.690104] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
[    0.690113] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.690122] pci_bus 0000:04: resource 5 [io  0x0d00-0xefff]
[    0.690131] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.690141] pci_bus 0000:04: resource 7 [mem 0x40000000-0xfebfffff]
[    0.690276] NET: Registered protocol family 2
[    0.690477] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.691335] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.692537] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.693089] TCP: Hash tables configured (established 131072 bind 65536)
[    0.693099] TCP reno registered
[    0.693114] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.693139] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.693451] NET: Registered protocol family 1
[    0.693517] pci 0000:00:02.0: Boot video device
[    0.693819] PCI: CLS 0 bytes, default 64
[    0.693902] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.693910] Simple Boot Flag at 0x44 set to 0x1
[    0.694584] cpufreq-nforce2: No nForce2 chipset.
[    0.695059] audit: initializing netlink socket (disabled)
[    0.695088] type=2000 audit(1308075279.688:1): initialized
[    0.719980] highmem bounce pool size: 64 pages
[    0.719998] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.727069] VFS: Disk quotas dquot_6.5.2
[    0.727287] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.729994] fuse init (API version 7.16)
[    0.730352] msgmni has been set to 1704
[    0.731220] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.731322] io scheduler noop registered
[    0.731329] io scheduler deadline registered
[    0.731396] io scheduler cfq registered (default)
[    0.731781] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.731876] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.732091] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.732175] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.732333] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.732415] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.732711] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.732814] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.732998] intel_idle: MWAIT substates: 0x20220
[    0.733016] intel_idle: v0.4 model 0x1C
[    0.733021] intel_idle: lapic_timer_reliable_states 0x2
[    0.733040] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.792597] Freeing initrd memory: 12476k freed
[    0.796277] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.860111] ACPI: AC Adapter [AC] (off-line)
[    0.860387] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.860401] ACPI: Power Button [PWRB]
[    0.860517] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.860563] ACPI: Lid Switch [LID0]
[    0.860685] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.860695] ACPI: Sleep Button [SLPB]
[    0.860833] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.860842] ACPI: Power Button [PWRF]
[    0.861018] ACPI: Fan [FAN] (on)
[    0.861386] ACPI: acpi_idle yielding to intel_idle
[    0.926591] thermal LNXTHERM:00: registered as thermal_zone0
[    0.926599] ACPI: Thermal Zone [THRM] (27 C)
[    0.926648] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.926798] ERST: Table is not found!
[    0.926962] isapnp: Scanning for PnP cards...
[    0.927015] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.281038] isapnp: No Plug & Play device found
[    1.288511] Linux agpgart interface v0.103
[    1.288677] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.288958] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.289179] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.289426] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    1.292808] brd: module loaded
[    1.294385] loop: module loaded
[    1.294653] i2c-core: driver [adp5520] using legacy suspend method
[    1.294659] i2c-core: driver [adp5520] using legacy resume method
[    1.295923] Fixed MDIO Bus: probed
[    1.296127] PPP generic driver version 2.4.2
[    1.296277] tun: Universal TUN/TAP device driver, 1.6
[    1.296282] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.296509] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.296558] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.296595] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.296603] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.296707] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.296805] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.296824] ehci_hcd 0000:00:1d.7: debug port 1
[    1.300725] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.300763] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x56344400
[    1.316034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.316364] hub 1-0:1.0: USB hub found
[    1.316376] hub 1-0:1.0: 8 ports detected
[    1.316566] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.316606] uhci_hcd: USB Universal Host Controller Interface driver
[    1.316683] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.316699] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.316706] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.316812] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.316910] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000050a0
[    1.317229] hub 2-0:1.0: USB hub found
[    1.317240] hub 2-0:1.0: 2 ports detected
[    1.317396] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.317410] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.317417] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.317520] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.317627] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00005080
[    1.317949] hub 3-0:1.0: USB hub found
[    1.317960] hub 3-0:1.0: 2 ports detected
[    1.318111] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.318126] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.318133] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.318244] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.320117] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005060
[    1.320441] hub 4-0:1.0: USB hub found
[    1.320452] hub 4-0:1.0: 2 ports detected
[    1.320627] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.320641] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.320649] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.320756] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.320864] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00005040
[    1.321192] hub 5-0:1.0: USB hub found
[    1.321203] hub 5-0:1.0: 2 ports detected
[    1.321475] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.363372] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.363388] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.363760] mousedev: PS/2 mouse device common for all mice
[    1.365732] rtc_cmos 00:03: RTC can wake from S4
[    1.372173] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.372226] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.372472] device-mapper: uevent: version 1.0.3
[    1.372707] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    1.372889] device-mapper: multipath: version 1.2.0 loaded
[    1.372898] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.373116] EISA: Probing bus 0 at eisa.0
[    1.373123] EISA: Cannot allocate resource for mainboard
[    1.373130] Cannot allocate resource for EISA slot 1
[    1.373136] Cannot allocate resource for EISA slot 2
[    1.373142] Cannot allocate resource for EISA slot 3
[    1.373147] Cannot allocate resource for EISA slot 4
[    1.373153] Cannot allocate resource for EISA slot 5
[    1.373158] Cannot allocate resource for EISA slot 6
[    1.373164] Cannot allocate resource for EISA slot 7
[    1.373170] Cannot allocate resource for EISA slot 8
[    1.373174] EISA: Detected 0 cards.
[    1.373511] cpuidle: using governor ladder
[    1.373788] cpuidle: using governor menu
[    1.374438] TCP cubic registered
[    1.374796] NET: Registered protocol family 10
[    1.376126] NET: Registered protocol family 17
[    1.376182] Registering the dns_resolver key type
[    1.377799] Using IPI No-Shortcut mode
[    1.378087] PM: Hibernation image not present or could not be loaded.
[    1.378112] registered taskstats version 1
[    1.378551]   Magic number: 15:129:241
[    1.378705] rtc_cmos 00:03: setting system clock to 2011-06-14 18:14:40 UTC (1308075280)
[    1.378714] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.378718] EDD information not available.
[    1.378985] Freeing unused kernel memory: 700k freed
[    1.379468] Write protecting the kernel text: 5192k
[    1.379559] Write protecting the kernel read-only data: 2148k
[    1.396955] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.489645] <30>udev[78]: starting version 167
[    1.596411] ACPI: Battery Slot [BAT0] (battery present)
[    1.632092] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.852976] ATL1E 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.853004] ATL1E 0000:03:00.0: setting latency timer to 64
[    1.891970] ahci 0000:00:1f.2: version 3.0
[    1.892060] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.894963] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.895055] ahci: SSS flag set, parallel bus scan disabled
[    1.895121] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.895134] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
[    1.895150] ahci 0000:00:1f.2: setting latency timer to 64
[    1.898317] scsi0 : ahci
[    1.898752] scsi1 : ahci
[    1.899069] scsi2 : ahci
[    1.899383] scsi3 : ahci
[    1.900203] ata1: SATA max UDMA/133 abar m1024@0x56344000 port 0x56344100 irq 43
[    1.900214] ata2: DUMMY
[    1.900224] ata3: SATA max UDMA/133 abar m1024@0x56344000 port 0x56344200 irq 43
[    1.900231] ata4: DUMMY
[    2.220110] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.221406] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.221848] ata1.00: ATA-8: Hitachi HTS543216L9A300, FB2OC40C, max UDMA/133
[    2.221864] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.223451] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.223837] ata1.00: configured for UDMA/133
[    2.224146] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    2.224761] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.224862] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.225150] sd 0:0:0:0: [sda] Write Protect is off
[    2.225163] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.225277] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.248385]  sda: sda1 sda2 sda3 sda4
[    2.249403] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.544102] ata3: SATA link down (SStatus 0 SControl 300)
[   17.304415] <30>udev[298]: starting version 167
[   17.366168] lp: driver loaded but no devices found
[   17.960484] acpi device:19: registered as cooling_device3
[   17.960997] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   17.961989] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[   18.067842] type=1400 audit(1308055497.182:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=415 comm="apparmor_parser"
[   18.069421] type=1400 audit(1308055497.186:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=415 comm="apparmor_parser"
[   18.070199] type=1400 audit(1308055497.186:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=415 comm="apparmor_parser"
[   18.497851] intel_rng: FWH not detected
[   18.566016] ATL1E 0000:03:00.0: irq 44 for MSI/MSI-X
[   18.566245] ATL1E 0000:03:00.0: eth0: NIC Link is Up <100 Mbps Full Duplex>
[   18.736266] leds_ss4200: no LED devices found
[   18.803296] cfg80211: Calling CRDA to update world regulatory domain
[   18.956669] [drm] Initialized drm 1.1.0 20060810
[   19.177837] Linux video capture interface: v2.00
[   19.507955] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   19.538510] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input6
[   19.538801] usbcore: registered new interface driver uvcvideo
[   19.538810] USB Video Class driver (v1.0.0)
[   19.597802] type=1400 audit(1308055498.714:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=588 comm="apparmor_parser"
[   19.598994] type=1400 audit(1308055498.714:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=588 comm="apparmor_parser"
[   19.599770] type=1400 audit(1308055498.714:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=588 comm="apparmor_parser"
[   19.721533] type=1400 audit(1308055498.838:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=587 comm="apparmor_parser"
[   19.810210] type=1400 audit(1308055498.926:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=590 comm="apparmor_parser"
[   19.838031] type=1400 audit(1308055498.954:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=590 comm="apparmor_parser"
[   19.844298] type=1400 audit(1308055498.962:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=604 comm="apparmor_parser"
[   20.395291] cfg80211: World regulatory domain updated:
[   20.395302] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.395314] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.395323] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.395333] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.395343] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.395352] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.535727] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000
[   20.653741] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   20.764220] ath5k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.764248] ath5k 0000:01:00.0: setting latency timer to 64
[   20.764383] ath5k 0000:01:00.0: registered as 'phy0'

---

