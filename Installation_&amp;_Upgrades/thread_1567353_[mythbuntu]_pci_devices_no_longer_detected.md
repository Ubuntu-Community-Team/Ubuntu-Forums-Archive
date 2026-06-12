---
title: "[mythbuntu] pci devices no longer detected"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by galorin on 2010-09-03
Ok, I have checked, and can't seem to find anything.  I have a PC which had seen a dist-upgrade from 9.04 to 9.10 to 10.04 when 10.04 was first released.  A few things started to go wrong, and I made a few mistakes and screwed up the system so I decided to do a clean install of 10.04.  Now here is where my problems came in.

I have a broadcom bc43xx wireless PCI card, and a Hauppage Nova-t tuner card.  Both were visible and worked superbly under 9.10 and the dist-upgrade to 10.04.

On the clean install, neither show up under lspci -v, which I have posted below

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
	Subsystem: Elitegroup Computer Systems Device 0131
	Flags: bus master, medium devsel, latency 32
	Memory at f0000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-febfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
	Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
	Subsystem: Elitegroup Computer Systems Device 0131
	Flags: bus master, medium devsel, latency 128, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_sis

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: Elitegroup Computer Systems Device 1880
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at d800 [size=256]
	I/O ports at d400 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 0131
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 0131
	Flags: bus master, medium devsel, latency 64, IRQ 3
	Memory at f9ffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 0131
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f9ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 0131
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f9ffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Ethernet Adapter
	Subsystem: Silicon Integrated Systems [SiS] Device 0191
	Flags: bus master, medium devsel, latency 0, IRQ 5
	Memory at f9ffbc00 (32-bit, non-prefetchable) [size=128]
	I/O ports at d000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: sis190
	Kernel modules: sis190

00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel modules: shpchp

00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel modules: shpchp

00:08.0 IDE interface: Silicon Integrated Systems [SiS] Device 0183 (rev 01) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Device 0131
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at c800 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c000 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at b400 [size=16]
	I/O ports at <unassigned>
	Capabilities: <access denied>
	Kernel driver in use: sata_sis
	Kernel modules: sata_sis

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
	Subsystem: CardExpert Technology Device 0401
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at e800 [size=128]
	[virtual] Expansion ROM at febe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

```

Here is my dmesg output, which I don't know if it is relevant or not.

```

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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Malformed early option 'apic'
[    0.000000] Malformed early option 'apic'
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3ffc0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  modified: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  modified: 000000003ffce000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  modified: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f876000 - 3000f0dc
[    0.000000] ACPI: RSDP 000f9530 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3ffc0000 00034 (v01 A M I  OEMRSDT  08000713 MSFT 00000097)
[    0.000000] ACPI: FACP 3ffc0200 00084 (v02 A M I  OEMFACP  08000713 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ffc0430 0477C (v01   A32G A32GV11C 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 3ffce000 00040
[    0.000000] ACPI: APIC 3ffc0390 0005C (v01 A M I  OEMAPIC  08000713 MSFT 00000097)
[    0.000000] ACPI: MCFG 3ffc03f0 0003C (v01 A M I  OEMMCFG  08000713 MSFT 00000097)
[    0.000000] ACPI: OEMB 3ffce040 00047 (v01 A M I  AMI_OEM  08000713 MSFT 00000097)
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [002f876000 - 003000f0dc]          RAMDISK ==> [002f876000 - 003000f0dc]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008de000 - 00008e1101]              BRK ==> [00008de000 - 00008e1101]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ffc0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ffc0
[    0.000000] On node 0 totalpages: 261967
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34482 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: SiS     
[    0.000000] MPTABLE: Product ID: 756/965     
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] I/O APIC #1 Version 20 at 0xFEC00000.
[    0.000000] Processors: 1
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf780000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259919
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=cf303a90-0e14-4350-a949-bb375b1f3829 ro quiet splash apic = off noapic nolapic
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5241280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ffc0)
[    0.000000] Memory: 1017220k/1048320k available (4679k kernel code, 30064k reserved, 2124k data, 660k init, 139016k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2200.246 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.49 BogoMIPS (lpj=8800984)
[    0.004024] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004060] Mount-cache hash table entries: 512
[    0.004194] Initializing cgroup subsys ns
[    0.004197] Initializing cgroup subsys cpuacct
[    0.004201] Initializing cgroup subsys memory
[    0.004210] Initializing cgroup subsys devices
[    0.004213] Initializing cgroup subsys freezer
[    0.004215] Initializing cgroup subsys net_cls
[    0.004235] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004238] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004242] mce: CPU supports 5 MCE banks
[    0.004259] Performance Events: AMD PMU driver.
[    0.004266] ... version:                0
[    0.004268] ... bit width:              48
[    0.004270] ... generic registers:      4
[    0.004271] ... value mask:             0000ffffffffffff
[    0.004273] ... max period:             00007fffffffffff
[    0.004275] ... fixed-purpose events:   0
[    0.004277] ... event mask:             000000000000000f
[    0.004281] Checking 'hlt' instruction... OK.
[    0.020666] SMP alternatives: switching to UP code
[    0.026199] Freeing SMP alternatives: 19k freed
[    0.026220] ACPI: Core revision 20090903
[    0.032221] ACPI: setting ELCR to 0200 (from 0c28)
[    0.032412] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032419] ftrace: allocating 21780 entries in 43 pages
[    0.036101] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036105] SMP disabled
[    0.036299] Brought up 1 CPUs
[    0.036302] Total of 1 processors activated (4400.49 BogoMIPS).
[    0.036602] CPU0 attaching NULL sched-domain.
[    0.036753] devtmpfs: initialized
[    0.037055] regulator: core version 0.5
[    0.037078] Time: 20:04:34  Date: 09/03/10
[    0.037116] NET: Registered protocol family 16
[    0.037219] EISA bus registered
[    0.037226] ACPI: bus type pci registered
[    0.037289] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.037292] PCI: Not using MMCONFIG.
[    0.038028] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.038030] PCI: Using configuration type 1 for base access
[    0.040719] bio: create slab <bio-0> at 0
[    0.041142] ACPI: EC: Look up EC in DSDT
[    0.044914] ACPI: Executed 3 blocks of module-level executable AML code
[    0.049141] ACPI: Interpreter enabled
[    0.049147] ACPI: (supports S0 S1 S4 S5)
[    0.049165] ACPI: Using PIC for interrupt routing
[    0.049204] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.056584] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.056586] PCI: Using MMCONFIG for extended config space
[    0.063546] ACPI Warning: Incorrect checksum in table [OEMB] - E6, should be D9 (20090903/tbutils-314)
[    0.063620] ACPI: No dock devices found.
[    0.063721] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.063767] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf3ffffff]
[    0.063847] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.063851] pci 0000:00:01.0: PME# disabled
[    0.063909] pci 0000:00:02.5: reg 10 io port: [0x1f0-0x1f7]
[    0.063914] pci 0000:00:02.5: reg 14 io port: [0x3f4-0x3f7]
[    0.063918] pci 0000:00:02.5: reg 18 io port: [0x170-0x177]
[    0.063923] pci 0000:00:02.5: reg 1c io port: [0x374-0x377]
[    0.063928] pci 0000:00:02.5: reg 20 io port: [0xffa0-0xffaf]
[    0.063946] pci 0000:00:02.5: PME# supported from D3cold
[    0.063949] pci 0000:00:02.5: PME# disabled
[    0.063972] pci 0000:00:02.7: reg 10 io port: [0xd800-0xd8ff]
[    0.063977] pci 0000:00:02.7: reg 14 io port: [0xd400-0xd47f]
[    0.064012] pci 0000:00:02.7: supports D1 D2
[    0.064014] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.064017] pci 0000:00:02.7: PME# disabled
[    0.064033] pci 0000:00:03.0: reg 10 32bit mmio: [0xf9fff000-0xf9ffffff]
[    0.064067] pci 0000:00:03.1: reg 10 32bit mmio: [0xf9ffe000-0xf9ffefff]
[    0.064099] pci 0000:00:03.2: reg 10 32bit mmio: [0xf9ffd000-0xf9ffdfff]
[    0.064136] pci 0000:00:03.3: reg 10 32bit mmio: [0xf9ffc000-0xf9ffcfff]
[    0.064163] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.064166] pci 0000:00:03.3: PME# disabled
[    0.064190] pci 0000:00:04.0: reg 10 32bit mmio: [0xf9ffbc00-0xf9ffbc7f]
[    0.064195] pci 0000:00:04.0: reg 14 io port: [0xd000-0xd07f]
[    0.064219] pci 0000:00:04.0: supports D1 D2
[    0.064221] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.064225] pci 0000:00:04.0: PME# disabled
[    0.064278] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.064282] pci 0000:00:06.0: PME# disabled
[    0.064339] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.064342] pci 0000:00:07.0: PME# disabled
[    0.064368] pci 0000:00:08.0: reg 10 io port: [0xc800-0xc807]
[    0.064373] pci 0000:00:08.0: reg 14 io port: [0xc400-0xc403]
[    0.064378] pci 0000:00:08.0: reg 18 io port: [0xc000-0xc007]
[    0.064382] pci 0000:00:08.0: reg 1c io port: [0xb800-0xb803]
[    0.064387] pci 0000:00:08.0: reg 20 io port: [0xb400-0xb40f]
[    0.064405] pci 0000:00:08.0: PME# supported from D3cold
[    0.064408] pci 0000:00:08.0: PME# disabled
[    0.064511] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.064519] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.064527] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.064532] pci 0000:01:00.0: reg 24 io port: [0xe800-0xe87f]
[    0.064537] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfebe0000-0xfebfffff]
[    0.064577] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.064581] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfebfffff]
[    0.064586] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.064669] pci_bus 0000:00: on NUMA node 0
[    0.064673] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.064940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.064987] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.072062] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.072152] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.072240] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.072328] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.072415] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.072503] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.072591] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.072679] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.072776] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.072779] vgaarb: loaded
[    0.072891] SCSI subsystem initialized
[    0.072962] libata version 3.00 loaded.
[    0.073033] usbcore: registered new interface driver usbfs
[    0.073044] usbcore: registered new interface driver hub
[    0.073067] usbcore: registered new device driver usb
[    0.073174] ACPI: WMI: Mapper loaded
[    0.073176] PCI: Using ACPI for IRQ routing
[    0.073304] NetLabel: Initializing
[    0.073306] NetLabel:  domain hash size = 128
[    0.073307] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.073320] NetLabel:  unlabeled traffic allowed by default
[    0.073362] Switching to clocksource tsc
[    0.075095] AppArmor: AppArmor Filesystem Enabled
[    0.075121] pnp: PnP ACPI init
[    0.075140] ACPI: bus type pnp registered
[    0.079496] pnp: PnP ACPI: found 13 devices
[    0.079498] ACPI: ACPI bus type pnp unregistered
[    0.079501] PnPBIOS: Disabled by ACPI PNP
[    0.079516] system 00:08: ioport range 0xa00-0xa0f has been reserved
[    0.079519] system 00:08: ioport range 0xa10-0xa1f has been reserved
[    0.079522] system 00:08: ioport range 0xa20-0xa2f has been reserved
[    0.079525] system 00:08: ioport range 0xa30-0xa3f has been reserved
[    0.079530] system 00:09: ioport range 0x290-0x297 has been reserved
[    0.079533] system 00:09: ioport range 0xc00-0xc05 has been reserved
[    0.079536] system 00:09: ioport range 0xd00-0xd05 has been reserved
[    0.079539] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.079542] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.079544] system 00:09: ioport range 0x800-0x8cf has been reserved
[    0.079547] system 00:09: ioport range 0x8d0-0x8ff has been reserved
[    0.079552] system 00:09: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.079555] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.079558] system 00:09: iomem range 0xffee0000-0xffefffff has been reserved
[    0.079563] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.079566] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.079571] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.079577] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.079580] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.079583] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.079586] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
[    0.114255] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.114258] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.114262] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfebfffff
[    0.114266] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.114272] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.114274] pci 0000:00:06.0:   IO window: disabled
[    0.114278] pci 0000:00:06.0:   MEM window: disabled
[    0.114281] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.114285] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.114287] pci 0000:00:07.0:   IO window: disabled
[    0.114291] pci 0000:00:07.0:   MEM window: disabled
[    0.114294] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.114307] pci 0000:00:01.0: setting latency timer to 64
[    0.114314] pci 0000:00:06.0: setting latency timer to 64
[    0.114321] pci 0000:00:07.0: setting latency timer to 64
[    0.114326] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.114328] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.114331] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.114334] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfebfffff]
[    0.114336] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.114374] NET: Registered protocol family 2
[    0.114463] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.114836] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.115758] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.116257] TCP: Hash tables configured (established 131072 bind 65536)
[    0.116260] TCP reno registered
[    0.116360] NET: Registered protocol family 1
[    0.116436] pci 0000:01:00.0: Boot video device
[    0.116646] cpufreq-nforce2: No nForce2 chipset.
[    0.116667] Scanning for low memory corruption every 60 seconds
[    0.116768] audit: initializing netlink socket (disabled)
[    0.116783] type=2000 audit(1283544274.114:1): initialized
[    0.126006] Trying to unpack rootfs image as initramfs...
[    0.138939] highmem bounce pool size: 64 pages
[    0.138946] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.140282] VFS: Disk quotas dquot_6.5.2
[    0.140342] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.140872] fuse init (API version 7.13)
[    0.140948] msgmni has been set to 1716
[    0.146967] alg: No test for stdrng (krng)
[    0.147064] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.147067] io scheduler noop registered
[    0.147069] io scheduler anticipatory registered
[    0.147070] io scheduler deadline registered
[    0.147105] io scheduler cfq registered (default)
[    0.147263]   alloc irq_desc for 24 on node -1
[    0.147265]   alloc kstat_irqs on node -1
[    0.147326] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.147345] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.147442] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.147446] ACPI: Power Button [PWRB]
[    0.147489] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.147491] ACPI: Power Button [PWRF]
[    0.147704] processor LNXCPU:00: registered as cooling_device0
[    0.159113] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.159215] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.159484] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.160469] brd: module loaded
[    0.160908] loop: module loaded
[    0.160989] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.161102] pata_sis 0000:00:02.5: version 0.5.2
[    0.161279] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    0.161281] PCI: setting IRQ 10 as level-triggered
[    0.161285] pata_sis 0000:00:02.5: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    0.161437] isapnp: Scanning for PnP cards...
[    0.166958] scsi0 : pata_sis
[    0.167026] scsi1 : pata_sis
[    0.167605] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.167608] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.167753] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    0.167755] PCI: setting IRQ 5 as level-triggered
[    0.167759] pata_acpi 0000:00:08.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.167804] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.168068] Fixed MDIO Bus: probed
[    0.168098] PPP generic driver version 2.4.2
[    0.168149] tun: Universal TUN/TAP device driver, 1.6
[    0.168151] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.168228] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.168342] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[    0.168346] ehci_hcd 0000:00:03.3: PCI INT D -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
[    0.168363] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.168397] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.168428] ehci_hcd 0000:00:03.3: cache line size of 64 is not supported
[    0.168436] ehci_hcd 0000:00:03.3: irq 5, io mem 0xf9ffc000
[    0.214348] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.214476] usb usb1: configuration #1 chosen from 1 choice
[    0.214503] hub 1-0:1.0: USB hub found
[    0.214513] hub 1-0:1.0: 8 ports detected
[    0.214577] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.214766] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[    0.214770] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 5 (level, low) -> IRQ 5
[    0.214788] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.214824] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.214842] ohci_hcd 0000:00:03.0: irq 5, io mem 0xf9fff000
[    0.304426] usb usb2: configuration #1 chosen from 1 choice
[    0.304456] hub 2-0:1.0: USB hub found
[    0.304469] hub 2-0:1.0: 3 ports detected
[    0.304683] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 3
[    0.304686] PCI: setting IRQ 3 as level-triggered
[    0.304690] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 3 (level, low) -> IRQ 3
[    0.304710] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.304750] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    0.304771] ohci_hcd 0000:00:03.1: irq 3, io mem 0xf9ffe000
[    0.340135] ata1.00: ATA-7: WDC WD1600AVBB-63SYA0, 00.07H00, max UDMA/100
[    0.340139] ata1.00: 312581808 sectors, multi 16: LBA48 
[    0.348104] ata1.00: configured for UDMA/100
[    0.393756] usb usb3: configuration #1 chosen from 1 choice
[    0.393784] hub 3-0:1.0: USB hub found
[    0.393800] hub 3-0:1.0: 3 ports detected
[    0.394027] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
[    0.394031] ohci_hcd 0000:00:03.2: PCI INT C -> Link[LNKG] -> GSI 5 (level, low) -> IRQ 5
[    0.394052] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    0.394088] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    0.394108] ohci_hcd 0000:00:03.2: irq 5, io mem 0xf9ffd000
[    0.484395] usb usb4: configuration #1 chosen from 1 choice
[    0.484426] hub 4-0:1.0: USB hub found
[    0.484439] hub 4-0:1.0: 2 ports detected
[    0.484500] uhci_hcd: USB Universal Host Controller Interface driver
[    0.484596] PNP: No PS/2 controller found. Probing ports directly.
[    0.484882] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.484889] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.490953] mice: PS/2 mouse device common for all mice
[    0.491072] rtc_cmos 00:02: RTC can wake from S4
[    0.491119] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.491139] rtc0: alarms up to one year, 114 bytes nvram
[    0.491265] device-mapper: uevent: version 1.0.3
[    0.491376] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.491425] device-mapper: multipath: version 1.1.0 loaded
[    0.491428] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.491542] EISA: Probing bus 0 at eisa.0
[    0.491574] EISA: Detected 0 cards.
[    0.494783] cpuidle: using governor ladder
[    0.494787] cpuidle: using governor menu
[    0.495227] TCP cubic registered
[    0.495370] NET: Registered protocol family 10
[    0.495816] lo: Disabled Privacy Extensions
[    0.496133] NET: Registered protocol family 17
[    0.496167] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[    0.496214] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[    0.496217] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[    0.496219] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[    0.496221] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    0.496260] Using IPI No-Shortcut mode
[    0.496353] PM: Resume from disk failed.
[    0.496368] registered taskstats version 1
[    0.496579]   Magic number: 10:876:92
[    0.496674] rtc_cmos 00:02: setting system clock to 2010-09-03 20:04:35 UTC (1283544275)
[    0.496677] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.496678] EDD information not available.
[    0.576373] Freeing initrd memory: 7780k freed
[    0.714486] isapnp: No Plug & Play device found
[    0.714675] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AVBB-6 00.0 PQ: 0 ANSI: 5
[    0.714840] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.715020] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.715063] sd 0:0:0:0: [sda] Write Protect is off
[    0.715065] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.715087] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.715230]  sda: sda1
[    0.721816] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.878917] ata2.01: ATAPI: DVD DC 16X8X5, 103, max UDMA/66
[    0.878936] ata2.01: limited to UDMA/33 due to 40-wire cable
[    0.886598] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    0.894934] ata2.01: configured for UDMA/33
[    0.896986] scsi 1:0:1:0: CD-ROM            ATAPI    DVD DC 16X8X5    103  PQ: 0 ANSI: 5
[    0.904351] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.904353] Uniform CD-ROM driver Revision: 3.20
[    0.904426] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    0.904468] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    0.904508] Freeing unused kernel memory: 660k freed
[    0.905057] Write protecting the kernel text: 4680k
[    0.905085] Write protecting the kernel read-only data: 1844k
[    0.923350] udev: starting version 151
[    1.100170] sata_sis 0000:00:08.0: version 1.0
[    1.100189] sata_sis 0000:00:08.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    1.100194] sata_sis 0000:00:08.0: Detected SiS 182/965L chipset
[    1.100692] usb 3-1: configuration #1 chosen from 1 choice
[    1.117350] Floppy drive(s): fd0 is 1.44M
[    1.124404] scsi2 : sata_sis
[    1.133797] scsi3 : sata_sis
[    1.134303] ata3: SATA max UDMA/133 cmd 0xc800 ctl 0xc400 bmdma 0xb400 irq 5
[    1.134307] ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xb800 bmdma 0xb408 irq 5
[    1.139104] FDC 0 is a post-1991 82077
[    1.404030] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    1.452056] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.460339] ata3.00: ATA-7: SAMSUNG HD103SI, 1AG01118, max UDMA7
[    1.460342] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.468350] ata3.00: configured for UDMA/133
[    1.468462] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
[    1.468625] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.468837] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.468877] sd 2:0:0:0: [sdb] Write Protect is off
[    1.468880] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.468900] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.469019]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    1.508764] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.618289] usb 2-2: configuration #1 chosen from 1 choice
[    1.798578] ata4: SATA link down (SStatus 0 SControl 300)
[    1.798603] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    1.805329] usbcore: registered new interface driver hiddev
[    1.811671] input: Darfon USB Optical Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input3
[    1.811857] generic-usb 0003:0D62:A100.0001: input,hidraw0: USB HID v1.10 Mouse [Darfon USB Optical Mouse] on usb-0000:00:03.0-2/input0
[    1.811883] usbcore: registered new interface driver usbhid
[    1.811973] usbhid: v2.6:USB HID core driver
[    2.013280] usb 4-1: configuration #1 chosen from 1 choice
[    2.015998] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    2.016033] EXT4-fs (sdb1): write access will be enabled during recovery
[    2.027648] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1:1.0/input/input4
[    2.027804] logitech 0003:046D:C517.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:03.2-1/input0
[    2.037161] logitech 0003:046D:C517.0003: fixing up Logitech keyboard report descriptor
[    2.038309] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1:1.1/input/input5
[    2.038832] logitech 0003:046D:C517.0003: input,hiddev96,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:03.2-1/input1
[    2.097993] EXT4-fs (sdb1): recovery complete
[    2.098323] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    9.337909] udev: starting version 151
[    9.403731] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.410112] lp: driver loaded but no devices found
[    9.435044] Adding 3903752k swap on /dev/sdb5.  Priority:-1 extents:1 across:3903752k 
[    9.499650] vga16fb: initializing
[    9.499655] vga16fb: mapped to 0xc00a0000
[    9.499725] fb0: VGA16 VGA frame buffer device
[    9.692802] Linux agpgart interface v0.103
[    9.825178] sis190 Gigabit Ethernet driver 1.3 loaded.
[    9.825363] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[    9.825368] sis190 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
[    9.825379] sis190 0000:00:04.0: setting latency timer to 64
[    9.825395] 0000:00:04.0: Read MAC address from EEPROM
[    9.825398] 0000:00:04.0: Error EEPROM read 0.
[    9.825400] 0000:00:04.0: Read MAC address from APC.
[    9.982514] type=1505 audit(1283544284.983:2):  operation="profile_load" pid=595 name="/sbin/dhclient3"
[    9.982777] type=1505 audit(1283544284.983:3):  operation="profile_load" pid=595 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.982921] type=1505 audit(1283544284.983:4):  operation="profile_load" pid=595 name="/usr/lib/connman/scripts/dhclient-script"
[    9.993721] type=1505 audit(1283544284.995:5):  operation="profile_load" pid=608 name="/usr/sbin/ntpd"
[   10.046834] nvidia: module license 'NVIDIA' taints kernel.
[   10.046838] Disabling lock debugging due to kernel taint
[   11.375095] EXT4-fs (sdb7): mounted filesystem with ordered data mode
[   11.377903] Bluetooth: Core ver 2.15
[   11.378370] NET: Registered protocol family 31
[   11.378372] Bluetooth: HCI device and connection manager initialized
[   11.378376] Bluetooth: HCI socket layer initialized
[   11.386478] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.386800] usbcore: registered new interface driver btusb
[   11.396236] parport_pc 00:07: reported by Plug and Play ACPI
[   11.396305] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   11.541952] ppdev: user-space parallel port driver
[   11.568299] lp0: using parport0 (interrupt-driven).
[   11.672890] Console: switching to colour frame buffer device 80x30
[   11.764058] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 31.
[   11.780042] 0000:00:04.0: Using transceiver at address 31 as default.
[   11.812713] 0000:00:04.0: SiS 190 PCI Fast Ethernet adapter at f80d0c00 (IRQ: 5), 00:1b:b9:d1:5b:4b
[   11.812717] eth0: GMII mode.
[   11.812722] eth0: Enabling Auto-negotiation.
[   11.844399] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   11.844404] PCI: setting IRQ 11 as level-triggered
[   11.844409] Intel ICH 0000:00:02.7: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   11.885952] type=1505 audit(1283544286.887:6):  operation="profile_replace" pid=756 name="/sbin/dhclient3"
[   11.886232] type=1505 audit(1283544286.887:7):  operation="profile_replace" pid=756 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.886387] type=1505 audit(1283544286.887:8):  operation="profile_replace" pid=756 name="/usr/lib/connman/scripts/dhclient-script"
[   11.924404] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[   11.924415] nvidia 0000:01:00.0: setting latency timer to 64
[   11.924421] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.925593] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   11.931420] type=1505 audit(1283544286.931:9):  operation="profile_load" pid=759 name="/usr/bin/evince"
[   11.951667] type=1505 audit(1283544286.951:10):  operation="profile_load" pid=759 name="/usr/bin/evince-previewer"
[   11.965593] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.967733] type=1505 audit(1283544286.967:11):  operation="profile_load" pid=759 name="/usr/bin/evince-thumbnailer"
[   12.284070] intel8x0_measure_ac97_clock: measured 52189 usecs (2511 samples)
[   12.284074] intel8x0: clocking to 48000
[   12.477868] Bluetooth: L2CAP ver 2.14
[   12.477872] Bluetooth: L2CAP socket layer initialized
[   12.497471] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.497475] Bluetooth: BNEP filters: protocol multicast
[   12.536974] Bridge firewalling registered
[   12.560837] Bluetooth: SCO (Voice Link) ver 0.6
[   12.560840] Bluetooth: SCO socket layer initialized
[   17.656286] hci_cmd_task: hci0 command tx timeout
[   17.721761] Bluetooth: RFCOMM TTY layer initialized
[   17.721769] Bluetooth: RFCOMM socket layer initialized
[   17.721771] Bluetooth: RFCOMM ver 1.11
[   21.996020] eth0: mii ext = 0000.
[   22.020020] eth0: mii lpa=41e1 adv=01e1 exp=0001.
[   22.020024] eth0: link on 100 Mbps Full Duplex mode.
[   22.020222] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.964013] eth0: no IPv6 routers present
[   73.184138] Marking TSC unstable due to cpufreq changes
[   73.188143] Switching to clocksource acpi_pm

```

---

