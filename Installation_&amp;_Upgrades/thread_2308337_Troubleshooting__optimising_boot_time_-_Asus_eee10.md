---
title: "Troubleshooting / optimising boot time - Asus eee1000h"
date: 2016-01-02
forum: Installation &amp; Upgrades
---

### Post by steve234 on 2016-01-02
Hi there,

I have just moved my Lubuntu 14.04 LTS install from one atom-based netbook to another. The "new" machine is an Asus 1000h. It has twice the ram of the old machine (2gb) and an SSD rather than a HDD (the eee1000h supports SATA2 speed).

Ubuntu runs nice on the new machine but the boot-up time is longer than (1) a fresh Lubuntu install on the same machine; and (2) the boot up time of the old macine. I was not expecting this.

The dmesg log seems to say it was a 20 second boot, but I timed it from a stopwatch at 40 seconds.

It took 10 seconds from pressing the power button to the bios splash screen disappearing. I have fast boot and silent boot enabled in my bios. Perhaps the other 10 seconds that don't show in the log were taken up by grub (no grub screen shows).

I am a nOOb and don't really know where to begin troubleshooting the boot process. I have read around this forum, and know I need to check my boot log - which is below. Is there a log for grub too?

I am concerned that my /home partition (sda5) seems to be mounted twice - see 9.8 seconds. There are a bunch of warnings at 11 and 13 seconds, and 2 seconds are taken up killing a process just before 18s.

Grateful if anyone can point me in the right direction.

```

$ cat /var/log/dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-42-generic (buildd@lgw01-35) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #48~14.04.1-Ubuntu SMP Fri Dec 18 10:25:23 UTC 2015 (Ubuntu 3.19.0-42.48~14.04.1-generic 3.19.8-ckt10)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007f79ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f7a0000-0x000000007f7adfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007f7ae000-0x000000007f7effff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007f7f0000-0x000000007f7fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff80000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: ASUSTeK Computer INC. 1000H/1000H, BIOS 1103    09/16/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7f7a0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2040M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 4k
[    0.000000] BRK [0x01c2e000, 0x01c2efff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x20000000-0x377fffff]
[    0.000000]  [mem 0x20000000-0x377fffff] page 4k
[    0.000000] BRK [0x01c2f000, 0x01c2ffff] PGTABLE
[    0.000000] BRK [0x01c30000, 0x01c30fff] PGTABLE
[    0.000000] BRK [0x01c31000, 0x01c31fff] PGTABLE
[    0.000000] BRK [0x01c32000, 0x01c32fff] PGTABLE
[    0.000000] BRK [0x01c33000, 0x01c33fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x1fffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] RAMDISK: [mem 0x35af4000-0x36d71fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000FB9F0 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 0x7F7A0000 00003C (v01 A_M_I_ OEMRSDT  09000816 MSFT 00000097)
[    0.000000] ACPI: FACP 0x7F7A0200 000084 (v02 A_M_I_ OEMFACP  09000816 MSFT 00000097)
[    0.000000] ACPI: DSDT 0x7F7A05B0 0050FC (v01 A1028  A1028000 00000000 INTL 20080701)
[    0.000000] ACPI: FACS 0x7F7AE000 000040
[    0.000000] ACPI: APIC 0x7F7A0390 00005C (v01 A_M_I_ OEMAPIC  09000816 MSFT 00000097)
[    0.000000] ACPI: MCFG 0x7F7A03F0 00003C (v01 A_M_I_ OEMMCFG  09000816 MSFT 00000097)
[    0.000000] ACPI: OEMB 0x7F7AE040 000061 (v01 A_M_I_ AMI_OEM  09000816 MSFT 00000097)
[    0.000000] ACPI: HPET 0x7F7A56C0 000038 (v01 A_M_I_ OEMHPET  09000816 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x7F7AEB80 0004F0 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1147MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7f79ffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7f79ffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x7f79ffff]
[    0.000000] On node 0 totalpages: 522046
[    0.000000]   DMA zone: 40 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 2190 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 293794 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Reserving Intel graphics stolen memory at 0x7f800000-0x7fffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e1fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e2000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xfedfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 17 pages/cpu @f7bb4000 s39360 r0 d30272 u69632
[    0.000000] pcpu-alloc: s39360 r0 d30272 u69632 alloc=17*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519816
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-42-generic root=UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007f7a0)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 2033424K/2088184K available (6953K kernel code, 670K rwdata, 3004K rodata, 940K init, 788K bss, 54760K reserved, 0K cma-reserved, 1175176K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1a64000 - 0xc1b4f000   ( 940 kB)
[    0.000000]       .data : 0xc16ca910 - 0xc1a62bc0   (3680 kB)
[    0.000000]       .text : 0xc1000000 - 0xc16ca910   (6954 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
[    0.000000] NR_IRQS:2304 nr_irqs:440 16
[    0.000000] CPU 0 irqstacks, hard=f4c36000 soft=f4c38000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1595.996 MHz processor
[    0.004019] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.99 BogoMIPS (lpj=6383984)
[    0.004029] pid_max: default: 32768 minimum: 301
[    0.004050] ACPI: Core revision 20141107
[    0.019362] ACPI: All ACPI Tables successfully acquired
[    0.019415] Security Framework initialized
[    0.019448] AppArmor: AppArmor initialized
[    0.019453] Yama: becoming mindful.
[    0.019565] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.019573] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.020111] Initializing cgroup subsys memory
[    0.020130] Initializing cgroup subsys devices
[    0.020140] Initializing cgroup subsys freezer
[    0.020149] Initializing cgroup subsys net_cls
[    0.020158] Initializing cgroup subsys blkio
[    0.020167] Initializing cgroup subsys perf_event
[    0.020176] Initializing cgroup subsys net_prio
[    0.020184] Initializing cgroup subsys hugetlb
[    0.020229] Atom PSE erratum detected, BIOS microcode update recommended
[    0.020234] Disabled fast string operations
[    0.020240] CPU: Physical Processor ID: 0
[    0.020244] CPU: Processor Core ID: 0
[    0.020253] mce: CPU supports 5 MCE banks
[    0.020266] CPU0: Thermal monitoring enabled (TM2)
[    0.020274] process: using mwait in idle threads
[    0.020289] Last level iTLB entries: 4KB 32, 2MB 0, 4MB 0
[    0.020289] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 8, 1GB 0
[    0.020934] Freeing SMP alternatives memory: 32K (c1b4f000 - c1b57000)
[    0.024028] ftrace: allocating 29339 entries in 58 pages
[    0.048198] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052247] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.091954] smpboot: CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz (fam: 06, model: 1c, stepping: 02)
[    0.092000] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
[    0.092000] ... version:                3
[    0.092000] ... bit width:              40
[    0.092000] ... generic registers:      2
[    0.092000] ... value mask:             000000ffffffffff
[    0.092000] ... max period:             000000007fffffff
[    0.092000] ... fixed-purpose events:   3
[    0.092000] ... event mask:             0000000700000003
[    0.092000] CPU 1 irqstacks, hard=f4d5a000 soft=f4d5c000
[    0.092000] x86: Booting SMP configuration:
[    0.092000] .... node  #0, CPUs:      #1
[    0.008000] Initializing CPU#1
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.008000] Disabled fast string operations
[    0.103637] x86: Booted up 1 node, 2 CPUs
[    0.103653] smpboot: Total of 2 processors activated (6383.98 BogoMIPS)
[    0.103780] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.104227] devtmpfs: initialized
[    0.105015] evm: security.selinux
[    0.105021] evm: security.SMACK64
[    0.105024] evm: security.SMACK64EXEC
[    0.105028] evm: security.SMACK64TRANSMUTE
[    0.105031] evm: security.SMACK64MMAP
[    0.105034] evm: security.ima
[    0.105038] evm: security.capability
[    0.105277] PM: Registering ACPI NVS region [mem 0x7f7ae000-0x7f7effff] (270336 bytes)
[    0.105682] pinctrl core: initialized pinctrl subsystem
[    0.105682] RTC time:  9:30:20, date: 01/02/16
[    0.105682] NET: Registered protocol family 16
[    0.105682] EISA bus registered
[    0.116024] cpuidle: using governor ladder
[    0.128021] cpuidle: using governor menu
[    0.128246] ACPI: bus type PCI registered
[    0.128255] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.128521] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.128529] PCI: not using MMCONFIG
[    0.128754] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
[    0.128868] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.128872] PCI: Using configuration type 1 for base access
[    0.148438] ACPI: Added _OSI(Module Device)
[    0.148446] ACPI: Added _OSI(Processor Device)
[    0.148451] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.148456] ACPI: Added _OSI(Processor Aggregator Device)
[    0.154208] ACPI: Executed 1 blocks of module-level executable AML code
[    0.160738] ACPI: Dynamic OEM Table Load:
[    0.160756] ACPI: SSDT 0xF4DD1400 00023C (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.161794] ACPI: Dynamic OEM Table Load:
[    0.161813] ACPI: SSDT 0xF4C11800 000724 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.164260] ACPI: Dynamic OEM Table Load:
[    0.164273] ACPI: SSDT 0xF4C9EF00 0000CC (v01 PmRef  Cpu1Ist  00003000 INTL 20051117)
[    0.165106] ACPI: Dynamic OEM Table Load:
[    0.165118] ACPI: SSDT 0xF4D3FB40 000085 (v01 PmRef  Cpu1Cst  00003000 INTL 20051117)
[    0.166429] ACPI: Interpreter enabled
[    0.166459] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.166470] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.166508] ACPI: (supports S0 S3 S4 S5)
[    0.166513] ACPI: Using IOAPIC for interrupt routing
[    0.166579] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.167774] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    0.167780] PCI: Using MMCONFIG for extended config space
[    0.167842] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.182054] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.182073] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.182090] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.182401] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.182881] PCI host bridge to bus 0000:00
[    0.182891] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.182898] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.182905] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.182912] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.182918] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.182925] pci_bus 0000:00: root bus resource [mem 0x7f800000-0xffffffff]
[    0.182948] pci 0000:00:00.0: [8086:27ac] type 00 class 0x060000
[    0.183233] pci 0000:00:02.0: [8086:27ae] type 00 class 0x030000
[    0.183256] pci 0000:00:02.0: reg 0x10: [mem 0xf7f00000-0xf7f7ffff]
[    0.183268] pci 0000:00:02.0: reg 0x14: [io  0xdc00-0xdc07]
[    0.183280] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff pref]
[    0.183292] pci 0000:00:02.0: reg 0x1c: [mem 0xf7ec0000-0xf7efffff]
[    0.183579] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
[    0.183605] pci 0000:00:02.1: reg 0x10: [mem 0xf7f80000-0xf7ffffff]
[    0.183948] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.183986] pci 0000:00:1b.0: reg 0x10: [mem 0xf7eb8000-0xf7ebbfff 64bit]
[    0.184149] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.184283] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.184455] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.184607] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.184740] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.184910] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.185069] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.185201] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.185374] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
[    0.185532] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.185669] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.185841] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.185915] pci 0000:00:1d.0: reg 0x20: [io  0xd400-0xd41f]
[    0.186192] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.186266] pci 0000:00:1d.1: reg 0x20: [io  0xd480-0xd49f]
[    0.186545] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.186618] pci 0000:00:1d.2: reg 0x20: [io  0xd800-0xd81f]
[    0.186895] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.186969] pci 0000:00:1d.3: reg 0x20: [io  0xd880-0xd89f]
[    0.187262] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.187298] pci 0000:00:1d.7: reg 0x10: [mem 0xf7eb7c00-0xf7eb7fff]
[    0.187436] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.187735] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.187940] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.188127] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
[    0.188261] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0800-0x087f]: address conflict with ACPI CPU throttle [io  0x0810-0x0815]
[    0.188273] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.188282] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0380 (mask 0003)
[    0.188290] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
[    0.188298] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0003)
[    0.188585] pci 0000:00:1f.2: [8086:27c4] type 00 class 0x010180
[    0.188616] pci 0000:00:1f.2: reg 0x10: [io  0x0000-0x0007]
[    0.188634] pci 0000:00:1f.2: reg 0x14: [io  0x0000-0x0003]
[    0.188652] pci 0000:00:1f.2: reg 0x18: [io  0x0000-0x0007]
[    0.188670] pci 0000:00:1f.2: reg 0x1c: [io  0x0000-0x0003]
[    0.188688] pci 0000:00:1f.2: reg 0x20: [io  0xffa0-0xffaf]
[    0.188721] pci 0000:00:1f.2: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.188727] pci 0000:00:1f.2: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.188734] pci 0000:00:1f.2: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.188739] pci 0000:00:1f.2: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.188790] pci 0000:00:1f.2: PME# supported from D3hot
[    0.189207] pci 0000:00:1c.0: PCI bridge to [bus 04]
[    0.189411] pci 0000:03:00.0: [1969:1026] type 00 class 0x020000
[    0.189459] pci 0000:03:00.0: reg 0x10: [mem 0xfbfc0000-0xfbffffff 64bit]
[    0.189482] pci 0000:03:00.0: reg 0x18: [io  0xec00-0xec7f]
[    0.189667] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.189854] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.189875] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.189885] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.189895] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.190090] pci 0000:01:00.0: [1814:0781] type 00 class 0x028000
[    0.190126] pci 0000:01:00.0: reg 0x10: [mem 0xfbef0000-0xfbefffff]
[    0.190321] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.196047] pci 0000:00:1c.3: PCI bridge to [bus 01-02]
[    0.196062] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.196076] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.196253] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)
[    0.196274] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.196281] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.196287] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.196294] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.196301] pci 0000:00:1e.0:   bridge window [mem 0x7f800000-0xffffffff] (subtractive decode)
[    0.196351] pci_bus 0000:00: on NUMA node 0
[    0.198230] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.198410] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.198577] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.198742] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.198907] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.199074] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.199241] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.199408] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.199768] ACPI : EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.200103] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.200103] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.200103] vgaarb: loaded
[    0.200103] vgaarb: bridge control possible 0000:00:02.0
[    0.201086] SCSI subsystem initialized
[    0.201202] libata version 3.00 loaded.
[    0.201202] ACPI: bus type USB registered
[    0.201202] usbcore: registered new interface driver usbfs
[    0.201202] usbcore: registered new interface driver hub
[    0.201202] usbcore: registered new device driver usb
[    0.201202] PCI: Using ACPI for IRQ routing
[    0.201202] PCI: pci_cache_line_size set to 64 bytes
[    0.201202] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.201202] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.201202] e820: reserve RAM buffer [mem 0x7f7a0000-0x7fffffff]
[    0.201202] NetLabel: Initializing
[    0.201202] NetLabel:  domain hash size = 128
[    0.201202] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.201202] NetLabel:  unlabeled traffic allowed by default
[    0.201202] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.201202] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.201202] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.205049] Switched to clocksource hpet
[    0.224537] AppArmor: AppArmor Filesystem Enabled
[    0.224780] pnp: PnP ACPI init
[    0.225029] system 00:00: [mem 0xfed13000-0xfed19fff] has been reserved
[    0.225041] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.225197] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.225396] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.225572] pnp 00:03: Plug and Play ACPI device, IDs SYN0a04 SYN0a00 SYN0002 PNP0f13 (active)
[    0.226048] system 00:04: [io  0x025c-0x025f] has been reserved
[    0.226057] system 00:04: [io  0x0380-0x0383] has been reserved
[    0.226065] system 00:04: [io  0x0400-0x041f] has been reserved
[    0.226073] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.226081] system 00:04: [io  0x0800-0x087f] could not be reserved
[    0.226088] system 00:04: [io  0x0480-0x04bf] has been reserved
[    0.226097] system 00:04: [mem 0x8c000000-0x8c01ffff] has been reserved
[    0.226105] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.226113] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.226120] system 00:04: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.226128] system 00:04: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.226136] system 00:04: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.226145] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.226473] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.226482] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.226492] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.226697] system 00:06: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.226708] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.227260] system 00:07: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.227269] system 00:07: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.227277] system 00:07: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.227285] system 00:07: [mem 0x00100000-0x7f7fffff] could not be reserved
[    0.227294] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.227669] pnp: PnP ACPI: found 8 devices
[    0.227686] PnPBIOS: Disabled by ACPI PNP
[    0.271303] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    0.271317] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
[    0.271326] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 04] add_size 200000
[    0.271345] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.271364] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 01-02] add_size 1000
[    0.271393] pci 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
[    0.271402] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.271410] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.271417] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.271425] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.271432] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.271448] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.271468] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.271485] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.271496] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.271506] pci 0000:00:1c.3: BAR 13: assigned [io  0x2000-0x2fff]
[    0.271514] pci 0000:00:1c.0: PCI bridge to [bus 04]
[    0.271523] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.271535] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.271545] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.271558] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.271566] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.271577] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.271587] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.271600] pci 0000:00:1c.3: PCI bridge to [bus 01-02]
[    0.271608] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.271619] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.271629] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.271642] pci 0000:00:1e.0: PCI bridge to [bus 05]
[    0.271664] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.271671] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.271677] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.271684] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.271690] pci_bus 0000:00: resource 8 [mem 0x7f800000-0xffffffff]
[    0.271697] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.271703] pci_bus 0000:04: resource 1 [mem 0x80000000-0x801fffff]
[    0.271710] pci_bus 0000:04: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.271717] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.271723] pci_bus 0000:03: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.271730] pci_bus 0000:03: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.271737] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.271743] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbefffff]
[    0.271750] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.271757] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.271763] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.271769] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.271775] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.271782] pci_bus 0000:05: resource 8 [mem 0x7f800000-0xffffffff]
[    0.271856] NET: Registered protocol family 2
[    0.272395] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.272442] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.272501] TCP: Hash tables configured (established 8192 bind 8192)
[    0.272554] TCP: reno registered
[    0.272562] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.272580] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.272718] NET: Registered protocol family 1
[    0.272770] pci 0000:00:02.0: Video device with shadowed ROM
[    0.274167] PCI: CLS 32 bytes, default 64
[    0.274345] Trying to unpack rootfs image as initramfs...
[    1.149416] Freeing initrd memory: 18936K (f5af4000 - f6d72000)
[    1.150164] microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x208
[    1.150186] microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x208
[    1.150378] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.150481] Scanning for low memory corruption every 60 seconds
[    1.151481] futex hash table entries: 512 (order: 3, 32768 bytes)
[    1.151516] Initialise system trusted keyring
[    1.151583] audit: initializing netlink subsys (disabled)
[    1.151633] audit: type=2000 audit(1451727020.148:1): initialized
[    1.152632] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.160160] zpool: loaded
[    1.160168] zbud: loaded
[    1.160444] VFS: Disk quotas dquot_6.5.2
[    1.160601] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.162605] fuse init (API version 7.23)
[    1.163199] Key type big_key registered
[    1.164328] Key type asymmetric registered
[    1.164341] Asymmetric key parser 'x509' registered
[    1.164392] bounce: pool size: 64 pages
[    1.164556] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.164677] io scheduler noop registered
[    1.164688] io scheduler deadline registered (default)
[    1.164827] io scheduler cfq registered
[    1.165175] pcieport 0000:00:1c.0: enabling device (0104 -> 0107)
[    1.165903] pcieport 0000:00:1c.3: enabling device (0106 -> 0107)
[    1.166311] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.166385] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.166515] vesafb: mode is 800x600x32, linelength=3200, pages=0
[    1.166520] vesafb: scrolling: redraw
[    1.166526] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.166820] vesafb: framebuffer at 0xd0000000, mapped to 0xf8480000, using 1920k, total 1920k
[    1.167186] Console: switching to colour frame buffer device 100x37
[    1.167231] fb0: VESA VGA frame buffer device
[    1.167323] intel_idle: MWAIT substates: 0x20220
[    1.167345] intel_idle: v0.4 model 0x1C
[    1.167350] intel_idle: lapic_timer_reliable_states 0x2
[    1.167365] tsc: Marking TSC unstable due to TSC halts in idle states deeper than C2
[    1.167898] ACPI: AC Adapter [AC0] (off-line)
[    1.168315] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.173479] ACPI: Lid Switch [LID]
[    1.173660] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.173671] ACPI: Sleep Button [SLPB]
[    1.173848] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    1.173857] ACPI: Power Button [PWRB]
[    1.174035] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.174043] ACPI: Power Button [PWRF]
[    1.193107] thermal LNXTHERM:00: registered as thermal_zone0
[    1.193117] ACPI: Thermal Zone [TZ00] (46 C)
[    1.193287] GHES: HEST is not enabled!
[    1.193870] isapnp: Scanning for PnP cards...
[    1.193943] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.203292] Linux agpgart interface v0.103
[    1.203544] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.203579] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.203678] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.203969] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.212261] brd: module loaded
[    1.216320] loop: module loaded
[    1.217139] ata_piix 0000:00:1f.2: version 2.13
[    1.217364] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.221842] scsi host0: ata_piix
[    1.222266] scsi host1: ata_piix
[    1.222536] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.222544] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.223122] libphy: Fixed MDIO Bus: probed
[    1.223134] tun: Universal TUN/TAP device driver, 1.6
[    1.223139] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.223386] PPP generic driver version 2.4.2
[    1.223846] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.223867] ehci-pci: EHCI PCI platform driver
[    1.224237] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.224265] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.224297] ehci-pci 0000:00:1d.7: debug port 1
[    1.228271] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
[    1.228399] ehci-pci 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    1.240061] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.240311] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.240321] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.240329] usb usb1: Product: EHCI Host Controller
[    1.240337] usb usb1: Manufacturer: Linux 3.19.0-42-generic ehci_hcd
[    1.240344] usb usb1: SerialNumber: 0000:00:1d.7
[    1.241056] hub 1-0:1.0: USB hub found
[    1.241092] hub 1-0:1.0: 8 ports detected
[    1.242232] ehci-platform: EHCI generic platform driver
[    1.242310] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.242333] ohci-pci: OHCI PCI platform driver
[    1.242402] ohci-platform: OHCI generic platform driver
[    1.242453] uhci_hcd: USB Universal Host Controller Interface driver
[    1.242731] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.242757] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.242776] uhci_hcd 0000:00:1d.0: detected 2 ports
[    1.242819] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    1.243039] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.243048] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.243056] usb usb2: Product: UHCI Host Controller
[    1.243064] usb usb2: Manufacturer: Linux 3.19.0-42-generic uhci_hcd
[    1.243071] usb usb2: SerialNumber: 0000:00:1d.0
[    1.243647] hub 2-0:1.0: USB hub found
[    1.243677] hub 2-0:1.0: 2 ports detected
[    1.244736] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.244767] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.244786] uhci_hcd 0000:00:1d.1: detected 2 ports
[    1.244860] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    1.245080] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.245089] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.245097] usb usb3: Product: UHCI Host Controller
[    1.245105] usb usb3: Manufacturer: Linux 3.19.0-42-generic uhci_hcd
[    1.245112] usb usb3: SerialNumber: 0000:00:1d.1
[    1.245683] hub 3-0:1.0: USB hub found
[    1.245713] hub 3-0:1.0: 2 ports detected
[    1.246490] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.246516] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.246534] uhci_hcd 0000:00:1d.2: detected 2 ports
[    1.246604] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.246822] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.246831] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.246839] usb usb4: Product: UHCI Host Controller
[    1.246847] usb usb4: Manufacturer: Linux 3.19.0-42-generic uhci_hcd
[    1.246854] usb usb4: SerialNumber: 0000:00:1d.2
[    1.247504] hub 4-0:1.0: USB hub found
[    1.247534] hub 4-0:1.0: 2 ports detected
[    1.248272] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.248297] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.248321] uhci_hcd 0000:00:1d.3: detected 2 ports
[    1.248399] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    1.248616] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.248625] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.248633] usb usb5: Product: UHCI Host Controller
[    1.248640] usb usb5: Manufacturer: Linux 3.19.0-42-generic uhci_hcd
[    1.248648] usb usb5: SerialNumber: 0000:00:1d.3
[    1.249227] hub 5-0:1.0: USB hub found
[    1.249257] hub 5-0:1.0: 2 ports detected
[    1.250116] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.282428] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.282459] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.283151] mousedev: PS/2 mouse device common for all mice
[    1.284126] rtc_cmos 00:01: RTC can wake from S4
[    1.284497] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.284560] rtc_cmos 00:01: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.284612] i2c /dev entries driver
[    1.284863] device-mapper: uevent: version 1.0.3
[    1.285237] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    1.285373] platform eisa.0: Probing EISA bus 0
[    1.285385] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.285395] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.285405] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.285414] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.285423] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.285433] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.285442] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.285452] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.285461] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.285469] platform eisa.0: EISA: Detected 0 cards
[    1.285523] cpufreq-nforce2: No nForce2 chipset.
[    1.285550] ledtrig-cpu: registered to indicate activity on CPUs
[    1.285583] PCCT header not found.
[    1.285587] ACPI PCC probe failed.
[    1.285974] TCP: cubic registered
[    1.286672] NET: Registered protocol family 10
[    1.287618] NET: Registered protocol family 17
[    1.287682] Key type dns_resolver registered
[    1.288684] Using IPI No-Shortcut mode
[    1.289342] Loading compiled-in X.509 certificates
[    1.303193] Loaded X.509 cert 'Magrathea: Glacier signing key: d8cc8c1d9ba963cc2cd39e24021f3aac39a4c5a3'
[    1.303256] registered taskstats version 1
[    1.311251] Key type trusted registered
[    1.326744] Key type encrypted registered
[    1.326770] AppArmor: AppArmor sha1 policy hashing enabled
[    1.326783] ima: No TPM chip found, activating TPM-bypass!
[    1.326855] evm: HMAC attrs: 0x1
[    1.327723]   Magic number: 0:548:524
[    1.327912] rtc_cmos 00:01: setting system clock to 2016-01-02 09:30:21 UTC (1451727021)
[    1.329019] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.329026] EDD information not available.
[    1.329401] PM: Hibernation image not present or could not be loaded.
[    1.347312] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.393121] ata1.00: ATA-9: SanDisk SDSSDA240G, Z22000RL, max UDMA/133
[    1.393132] ata1.00: 468862128 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    1.418059] ata1.00: configured for UDMA/133
[    1.482764] ACPI: Battery Slot [BAT0] (battery present)
[    1.505063] isapnp: No Plug & Play device found
[    1.505380] scsi 0:0:0:0: Direct-Access     ATA      SanDisk SDSSDA24 00RL PQ: 0 ANSI: 5
[    1.506090] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
[    1.506325] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.506413] sd 0:0:0:0: [sda] Write Protect is off
[    1.506424] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.506526] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.508824]  sda: sda1 sda2 < sda5 sda6 >
[    1.510310] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.511146] Freeing unused kernel memory: 940K (c1a64000 - c1b4f000)
[    1.511563] Write protecting the kernel text: 6956k
[    1.511746] Write protecting the kernel read-only data: 3008k
[    1.511752] NX-protecting the kernel data: 5332k
[    1.550548] systemd-udevd[104]: starting version 204
[    1.744080] usb 5-1: new full-speed USB device number 2 using uhci_hcd
[    1.856116] usb 1-8: new high-speed USB device number 3 using ehci-pci
[    1.926278] usb 5-1: New USB device found, idVendor=0b05, idProduct=b700
[    1.926291] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.926300] usb 5-1: Product: BT-253
[    1.926308] usb 5-1: Manufacturer: Broadcom Corp
[    1.926316] usb 5-1: SerialNumber: 0015AFF49526
[    2.035865] usb 1-8: New USB device found, idVendor=04f2, idProduct=b071
[    2.035875] usb 1-8: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.035882] usb 1-8: Product: CNF7129
[    2.035888] usb 1-8: Manufacturer: Chicony Electronics Co., Ltd.
[    2.035893] usb 1-8: SerialNumber: SN0001
[    2.886598] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020030)
[    2.960010] psmouse serio1: elantech: Synaptics capabilities query result 0x00, 0x02, 0x64.
[    3.172158] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input6
[    6.948750] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    7.156300] random: init urandom read with 21 bits of entropy available
[    7.241504] init: plymouth-upstart-bridge main process (156) terminated with status 1
[    7.241552] init: plymouth-upstart-bridge main process ended, respawning
[    7.274510] init: plymouth-upstart-bridge main process (166) terminated with status 1
[    7.274557] init: plymouth-upstart-bridge main process ended, respawning
[    7.302736] init: plymouth-upstart-bridge main process (169) terminated with status 1
[    7.302801] init: plymouth-upstart-bridge main process ended, respawning
[    7.943273] Adding 3905532k swap on /dev/sda1.  Priority:-1 extents:1 across:3905532k SSFS
[    8.862118] systemd-udevd[291]: starting version 204
[    9.252733] eeepc_laptop: Eee PC Hotkey Driver
[    9.252759] eeepc_laptop: Hotkey init flags 0x41
[    9.265466] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[    9.271561] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[    9.271579] eeepc_laptop: Get control methods supported: 0x6101713
[    9.275291] input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input7
[    9.282514] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.282759] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    9.401951] lp: driver loaded but no devices found
[    9.470091] ppdev: user-space parallel port driver
[    9.857474] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.873882] EXT4-fs (sda5): re-mounted. Opts: (null)
[    9.907071] [drm] Initialized drm 1.1.0 20060810
[   10.139087] ATL1E 0000:03:00.0 eth1: renamed from eth0
[   10.193479] systemd-udevd[308]: renamed network interface eth0 to eth1
[   10.461686] [drm] Memory usable by graphics device = 256M
[   10.461699] checking generic (d0000000 1e0000) vs hw (d0000000 10000000)
[   10.461706] fb: switching to inteldrmfb from VESA VGA
[   10.461782] Console: switching to colour dummy device 80x25
[   10.464405] [drm] Replacing VGA console driver
[   10.481390] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   10.481400] [drm] Driver supports precise vblank timestamp query.
[   10.482080] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.568773] intel_rng: FWH not detected
[   10.660462] audit: type=1400 audit(1451727030.830:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=371 comm="apparmor_parser"
[   10.660488] audit: type=1400 audit(1451727030.830:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   10.660509] audit: type=1400 audit(1451727030.830:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   10.663156] audit: type=1400 audit(1451727030.830:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   10.663184] audit: type=1400 audit(1451727030.830:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   10.664314] audit: type=1400 audit(1451727030.834:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   10.676864] audit: type=1400 audit(1451727030.846:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=378 comm="apparmor_parser"
[   10.761818] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.883515] media: Linux media interface: v0.10
[   10.884163] Bluetooth: Core ver 2.20
[   10.884419] NET: Registered protocol family 31
[   10.884427] Bluetooth: HCI device and connection manager initialized
[   10.884447] Bluetooth: HCI socket layer initialized
[   10.885565] Bluetooth: L2CAP socket layer initialized
[   10.885602] Bluetooth: SCO socket layer initialized
[   10.900232] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   10.907403] cfg80211: Calling CRDA to update world regulatory domain
[   11.019140] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   11.199502] [drm] initialized overlay support
[   11.209223] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[   11.209724] ACPI Warning: SystemIO range 0x00000828-0x0000082f conflicts with OpRegion 0x00000800-0x0000087f (\PMIO) (20141107/utaddress-258)
[   11.209749] ACPI Warning: SystemIO range 0x00000828-0x0000082f conflicts with OpRegion 0x00000800-0x0000087f (\_SB_.PCI0.SBRG.PMS0) (20141107/utaddress-258)
[   11.209766] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.209778] ACPI Warning: SystemIO range 0x000004b0-0x000004bf conflicts with OpRegion 0x00000480-0x000004bf (\_SB_.PCI0.SBRG.GPBX) (20141107/utaddress-258)
[   11.209794] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.209802] ACPI Warning: SystemIO range 0x00000480-0x000004af conflicts with OpRegion 0x00000480-0x000004bf (\_SB_.PCI0.SBRG.GPBX) (20141107/utaddress-258)
[   11.209818] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.209824] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.300793] leds_ss4200: no LED devices found
[   11.370315] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   11.371870] Linux video capture interface: v2.00
[   11.412755] fbcon: inteldrmfb (fb0) is primary device
[   11.412838] Console: switching to colour frame buffer device 128x37
[   11.412926] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   11.412934] i915 0000:00:02.0: registered panic notifier
[   11.442692] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   11.442715] lpc_ich 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
[   11.442730] pci 0000:00:1e.0: PCI bridge to [bus 05]
[   11.553538] usbcore: registered new interface driver btusb
[   11.553805] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   11.553826] lpc_ich 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
[   11.553840] pci 0000:00:1e.0: PCI bridge to [bus 05]
[   11.579365] eeepc_laptop: Unable to find port
[   12.007784] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   12.161489] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input9
[   12.171984] usbcore: registered new interface driver uvcvideo
[   12.171994] USB Video Class driver (1.1.1)
[   12.206031] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 2872, rev 0200 detected
[   12.228740] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0003 detected
[   13.049886] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.090300] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.090310] Bluetooth: BNEP filters: protocol multicast
[   13.090330] Bluetooth: BNEP socket layer initialized
[   13.285723] Bluetooth: RFCOMM TTY layer initialized
[   13.285750] Bluetooth: RFCOMM socket layer initialized
[   13.285780] Bluetooth: RFCOMM ver 1.11
[   13.541172] audit: type=1400 audit(1451727033.710:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=613 comm="apparmor_parser"
[   13.541206] audit: type=1400 audit(1451727033.710:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=613 comm="apparmor_parser"
[   13.556730] audit: type=1400 audit(1451727033.726:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=613 comm="apparmor_parser"
[   13.563534] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   13.563550] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.563560] sound hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   13.563568] sound hdaudioC0D0:    mono: mono_out=0x0
[   13.563574] sound hdaudioC0D0:    inputs:
[   13.563585] sound hdaudioC0D0:      Mic=0x18
[   13.563594] sound hdaudioC0D0:      Internal Mic=0x12
[   13.577794] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.579551] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.960392] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   13.960416] lpc_ich 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
[   13.960431] pci 0000:00:1e.0: PCI bridge to [bus 05]
[   14.066583] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   14.066607] lpc_ich 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
[   14.066621] pci 0000:00:1e.0: PCI bridge to [bus 05]
[   14.350483] cfg80211: World regulatory domain updated:
[   14.350496] cfg80211:  DFS Master region: unset
[   14.350502] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   14.350512] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.350520] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.350528] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.350538] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.350546] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.446604] rt2800pci 0000:01:00.0 wlan1: renamed from wlan0
[   14.497812] systemd-udevd[308]: renamed network interface wlan0 to wlan1
[   15.524528] init: samba-ad-dc main process (698) terminated with status 1
[   16.809555] init: failsafe main process (662) killed by TERM signal
[   18.215190] audit: type=1400 audit(1451727038.382:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=936 comm="apparmor_parser"
[   18.215228] audit: type=1400 audit(1451727038.382:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=936 comm="apparmor_parser"
[   18.215255] audit: type=1400 audit(1451727038.382:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=936 comm="apparmor_parser"
[   18.227467] audit: type=1400 audit(1451727038.394:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=935 comm="apparmor_parser"
[   18.227498] audit: type=1400 audit(1451727038.394:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=935 comm="apparmor_parser"
[   18.238238] audit: type=1400 audit(1451727038.406:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=935 comm="apparmor_parser"
[   18.244263] audit: type=1400 audit(1451727038.414:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=936 comm="apparmor_parser"
[   18.244298] audit: type=1400 audit(1451727038.414:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=936 comm="apparmor_parser"
[   18.245409] audit: type=1400 audit(1451727038.414:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=936 comm="apparmor_parser"
[   18.368128] audit: type=1400 audit(1451727038.538:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=939 comm="apparmor_parser"
[   20.014729] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   20.046334] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   20.052651] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   20.097614] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.609166] zram: Created 2 device(s) ...

```

---

### Post by tokyobadger on 2016-01-02
Can you share your /etc/fstab

---

### Post by steve234 on 2016-01-02
thanks for helping @tokyobadger

I think I got my partitions the wrong way round in the above post /dev/sda5 is mounted at / and /dev/sda6 os my /home directory.

my fstab is:

```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=468bfcd7-cb38-449f-9e63-6d40a484f648 /               ext4    defaults  0       1
# /home was on /dev/sda6 during installation
UUID=119017f8-4da1-4475-9bc7-284fe2ac5048 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=42825c74-ab1d-44e3-9a63-5c1617021dea none            swap    sw              0       0

```

---

