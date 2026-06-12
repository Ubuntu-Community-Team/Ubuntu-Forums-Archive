---
title: "HTPC keeps changing default sound output after upgrading to 16.04"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by HEXYEBO on 2016-04-24
Hello, community,
I have a Gateway [SX2851] - i3@3.20GHz/8GB DDR3/500GB. The PC is connected to LCD TV screen via HDMI for both video and audio. This setup has been serving me faithfully as HTPC since 12.04, possibly longer.

I subscribe to LTS philosophy and recently upgraded to 16.04. After resolving few minor issues everything was peaches and cream, until...

Sound started changing default output. This is apparently very random, but most of the time when PC is left idle for some time.

Any help is appreciated.

.[ATTACH=CONFIG]268596[/ATTACH]

HEX

---

### Post by DuckHook on 2016-04-25
Welcome to the forums HEXYEBO.

The next time such a change occurs, please open a terminal and do:> dmesgPost the output back to this thread. Wrap output in CODE brackets because *dmesg* can be huge.

---

### Post by QLee on 2016-04-25
> **HEXYEBO said:**
> 
I subscribe to LTS philosophy and recently upgraded to 16.04. 

Of course you can do as you choose but I would suggest that the wisest LTS Philosophy is to continue using your working LTS release until the first point release of the new LTS. Give a little time for any bugs still in the latest release to be worked out. Choose stability over what may appear to be the latest and greatest.

---

### Post by DuckHook on 2016-04-25
> **QLee said:**
> ...I would suggest that the wisest LTS Philosophy is to continue using your working LTS release until the first point release of the new LTS. Give a little time for any bugs still in the latest release to be worked out. Choose stability over what may appear to be the latest and greatest.+1

---

### Post by HEXYEBO on 2016-04-25
Hello,
Thank you for getting back. Here's the output of *[COLOR=#000000][I]dmesg *[/COLOR][/I][COLOR=#000000]*command*[/COLOR][I][COLOR=#000000][I]:


[/I][/COLOR][/I]```

[    0.000000] microcode: CPU0 microcode updated early to revision 0x4, date = 2013-06-28
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-21-generic (buildd@lgw01-21) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2) ) #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 (Ubuntu 4.4.0-21.37-generic 4.4.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-21-generic root=UUID=d7aa528b-d59c-4357-b37e-5e35d82d365b ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bb77ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb780000-0x00000000bb78dfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb78e000-0x00000000bb7cffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb7d0000-0x00000000bb7dffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb7ed000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed3ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001fbffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000001fc000000-0x00000001ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000200000000-0x000000023bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Gateway SX2851/SX2851, BIOS P01-A0 11/16/2010
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x23c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-E7FFF write-through
[    0.000000]   E8000-EBFFF write-protect
[    0.000000]   EC000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 1FC000000 mask FFC000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 4, base: 8128MB, range: 64MB, type UC
[    0.000000] total RAM covered: 8064M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 6  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8128MB, range: 64MB, type UC
[    0.000000] reg 5, base: 8GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbc000000-0xffffffff] usable ==> reserved
[    0.000000] e820: update [mem 0x1fc000000-0x1ffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbb780 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] BRK [0x021fe000, 0x021fefff] PGTABLE
[    0.000000] BRK [0x021ff000, 0x021fffff] PGTABLE
[    0.000000] BRK [0x02200000, 0x02200fff] PGTABLE
[    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
[    0.000000] BRK [0x02202000, 0x02202fff] PGTABLE
[    0.000000] BRK [0x02203000, 0x02203fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33b0e000-0x35d7efff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FA6A0 000024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 0x00000000BB780100 00006C (v01 ACRSYS ACRPRDCT 20101116 MSFT 00000097)
[    0.000000] ACPI: FACP 0x00000000BB780290 0000F4 (v04 ACRSYS FACP1334 20101116 MSFT 00000097)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/64 (20150930/tbfadt-623)
[    0.000000] ACPI: DSDT 0x00000000BB7805E0 006A49 (v02 AA2A1  AA2A1002 00000002 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000BB78E000 000040
[    0.000000] ACPI: FACS 0x00000000BB78E000 000040
[    0.000000] ACPI: APIC 0x00000000BB780390 00008C (v02 ACRSYS APIC1334 20101116 MSFT 00000097)
[    0.000000] ACPI: MCFG 0x00000000BB780420 00003C (v01 ACRSYS OEMMCFG  20101116 MSFT 00000097)
[    0.000000] ACPI: SLIC 0x00000000BB780460 000176 (v01 ACRSYS ACRPRDCT 20101116 MSFT 00000097)
[    0.000000] ACPI: OEMB 0x00000000BB78E040 000072 (v01 ACRSYS OEMB1334 20101116 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000BB78A5E0 000038 (v01 ACRSYS OEMHPET  20101116 MSFT 00000097)
[    0.000000] ACPI: GSCI 0x00000000BB78E0C0 002024 (v01 ACRSYS GMCHSCI  20101116 MSFT 00000097)
[    0.000000] ACPI: AWMI 0x00000000BB7900F0 00004E (v01 ACRSYS OEMB1334 20101116 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x00000000BB791A90 000363 (v01 DpgPmm CpuPm    00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023bffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23bff6000-0x23bffafff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000023bffffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bb77ffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000001fbffffff]
[    0.000000]   node   0: [mem 0x0000000200000000-0x000000023bffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000023bffffff]
[    0.000000] On node 0 totalpages: 2045724
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11934 pages used for memmap
[    0.000000]   DMA32 zone: 763776 pages, LIFO batch:31
[    0.000000]   Normal zone: 20224 pages used for memmap
[    0.000000]   Normal zone: 1277952 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xbe000000-0xbfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 6, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb780000-0xbb78dfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb78e000-0xbb7cffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb7d0000-0xbb7dffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb7e0000-0xbb7ecfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb7ed000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfed3ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed40000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb00000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x1fc000000-0x1ffffffff]
[    0.000000] e820: [mem 0xc0000000-0xfed1ffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88023bc00000 s98008 r8192 d28968 u262144
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2013481
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-21-generic root=UUID=d7aa528b-d59c-4357-b37e-5e35d82d365b ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7930624K/8182896K available (8356K kernel code, 1278K rwdata, 3920K rodata, 1476K init, 1292K bss, 252272K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3191.981 MHz processor
[    0.000032] Calibrating delay loop (skipped), value calculated using timer frequency.. 6383.96 BogoMIPS (lpj=12767924)
[    0.000034] pid_max: default: 32768 minimum: 301
[    0.000041] ACPI: Core revision 20150930
[    0.004879] ACPI: 2 ACPI AML tables successfully acquired and loaded
[    0.004902] Security Framework initialized
[    0.004904] Yama: becoming mindful.
[    0.004921] AppArmor: AppArmor initialized
[    0.005431] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.007110] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007846] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.007857] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.008097] Initializing cgroup subsys io
[    0.008101] Initializing cgroup subsys memory
[    0.008108] Initializing cgroup subsys devices
[    0.008112] Initializing cgroup subsys freezer
[    0.008114] Initializing cgroup subsys net_cls
[    0.008117] Initializing cgroup subsys perf_event
[    0.008119] Initializing cgroup subsys net_prio
[    0.008122] Initializing cgroup subsys hugetlb
[    0.008125] Initializing cgroup subsys pids
[    0.008147] CPU: Physical Processor ID: 0
[    0.008148] CPU: Processor Core ID: 0
[    0.008153] mce: CPU supports 9 MCE banks
[    0.008164] CPU0: Thermal monitoring enabled (TM1)
[    0.008172] process: using mwait in idle threads
[    0.008176] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.008177] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.008475] Freeing SMP alternatives memory: 28K (ffffffff820b2000 - ffffffff820b9000)
[    0.010287] ftrace: allocating 31878 entries in 125 pages
[    0.024039] smpboot: Max logical packages: 4
[    0.024043] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.024433] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.170942] smpboot: CPU0: Intel(R) Core(TM) i3 CPU         550  @ 3.20GHz (family: 0x6, model: 0x25, stepping: 0x5)
[    0.170959] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.170976] core: CPUID marked event: 'bus cycles' unavailable
[    0.170979] ... version:                3
[    0.170980] ... bit width:              48
[    0.170981] ... generic registers:      4
[    0.170982] ... value mask:             0000ffffffffffff
[    0.170983] ... max period:             000000007fffffff
[    0.170983] ... fixed-purpose events:   3
[    0.170984] ... event mask:             000000070000000f
[    0.171793] x86: Booting SMP configuration:
[    0.171795] .... node  #0, CPUs:      #1
[    0.172258] microcode: CPU1 microcode updated early to revision 0x4, date = 2013-06-28
[    0.174495] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.174597]  #2 #3
[    0.179244] x86: Booted up 1 node, 4 CPUs
[    0.179248] smpboot: Total of 4 processors activated (25535.84 BogoMIPS)
[    0.181589] devtmpfs: initialized
[    0.183848] evm: security.selinux
[    0.183849] evm: security.SMACK64
[    0.183850] evm: security.SMACK64EXEC
[    0.183850] evm: security.SMACK64TRANSMUTE
[    0.183851] evm: security.SMACK64MMAP
[    0.183852] evm: security.ima
[    0.183852] evm: security.capability
[    0.183912] PM: Registering ACPI NVS region [mem 0xbb78e000-0xbb7cffff] (270336 bytes)
[    0.183983] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.184052] pinctrl core: initialized pinctrl subsystem
[    0.184158] RTC time: 20:02:32, date: 04/23/16
[    0.184255] NET: Registered protocol family 16
[    0.194951] cpuidle: using governor ladder
[    0.206948] cpuidle: using governor menu
[    0.206954] PCCT header not found.
[    0.207058] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.207060] ACPI: bus type PCI registered
[    0.207061] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.207118] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.207120] PCI: not using MMCONFIG
[    0.207121] PCI: Using configuration type 1 for base access
[    0.219299] ACPI: Added _OSI(Module Device)
[    0.219301] ACPI: Added _OSI(Processor Device)
[    0.219302] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.219303] ACPI: Added _OSI(Processor Aggregator Device)
[    0.221002] ACPI: Executed 1 blocks of module-level executable AML code
[    0.222604] ACPI: Dynamic OEM Table Load:
[    0.222612] ACPI: SSDT 0xFFFF8802330FE000 001448 (v01 DpgPmm P001Ist  00000011 INTL 20051117)
[    0.222908] ACPI: Dynamic OEM Table Load:
[    0.222912] ACPI: SSDT 0xFFFF880231D6A000 0004F4 (v01 PmRef  P001Cst  00003001 INTL 20051117)
[    0.223600] ACPI: Interpreter enabled
[    0.223605] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.223608] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.223618] ACPI: (supports S0 S3 S4 S5)
[    0.223620] ACPI: Using IOAPIC for interrupt routing
[    0.223640] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.225030] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.225043] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.231045] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.231051] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.231184] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.231309] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.231310] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.231507] PCI host bridge to bus 0000:00
[    0.231509] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.231511] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.231512] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.231514] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
[    0.231515] pci_bus 0000:00: root bus resource [mem 0xbc000000-0xdfffffff window]
[    0.231516] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfed8ffff window]
[    0.231518] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.231525] pci 0000:00:00.0: [8086:0040] type 00 class 0x060000
[    0.231544] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.231601] pci 0000:00:02.0: [8086:0042] type 00 class 0x030000
[    0.231612] pci 0000:00:02.0: reg 0x10: [mem 0xfb800000-0xfbbfffff 64bit]
[    0.231617] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.231621] pci 0000:00:02.0: reg 0x20: [io  0xdc00-0xdc07]
[    0.231705] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.231742] pci 0000:00:16.0: reg 0x10: [mem 0xfbefbc00-0xfbefbc0f 64bit]
[    0.231815] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.231883] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.231907] pci 0000:00:1a.0: reg 0x10: [mem 0xfbef8000-0xfbef83ff]
[    0.231967] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.232003] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.232035] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.232057] pci 0000:00:1b.0: reg 0x10: [mem 0xfbef4000-0xfbef7fff 64bit]
[    0.232107] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.232170] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.232223] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.232259] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.232291] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.232339] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.232374] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.232404] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.232453] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.232488] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.232518] pci 0000:00:1c.3: [8086:3b48] type 01 class 0x060400
[    0.232570] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.232608] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.232638] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.232687] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.232722] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.232753] pci 0000:00:1c.6: [8086:3b4e] type 01 class 0x060400
[    0.232802] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.232839] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.232869] pci 0000:00:1c.7: [8086:3b50] type 01 class 0x060400
[    0.232919] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.232956] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    0.232988] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.233011] pci 0000:00:1d.0: reg 0x10: [mem 0xfbef2000-0xfbef23ff]
[    0.233072] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.233106] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.233135] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.233196] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.233228] pci 0000:00:1f.0: [8086:3b08] type 00 class 0x060100
[    0.233371] pci 0000:00:1f.2: [8086:3b22] type 00 class 0x010601
[    0.233390] pci 0000:00:1f.2: reg 0x10: [io  0xd880-0xd887]
[    0.233396] pci 0000:00:1f.2: reg 0x14: [io  0xd800-0xd803]
[    0.233402] pci 0000:00:1f.2: reg 0x18: [io  0xd480-0xd487]
[    0.233408] pci 0000:00:1f.2: reg 0x1c: [io  0xd400-0xd403]
[    0.233414] pci 0000:00:1f.2: reg 0x20: [io  0xd080-0xd09f]
[    0.233420] pci 0000:00:1f.2: reg 0x24: [mem 0xfbef0000-0xfbef07ff]
[    0.233445] pci 0000:00:1f.2: PME# supported from D3hot
[    0.233505] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.233518] pci 0000:00:1f.3: reg 0x10: [mem 0xfbefb800-0xfbefb8ff 64bit]
[    0.233534] pci 0000:00:1f.3: reg 0x20: [io  0x0400-0x041f]
[    0.233641] pci 0000:01:00.0: [10ec:8168] type 00 class 0x020000
[    0.233676] pci 0000:01:00.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.233700] pci 0000:01:00.0: reg 0x18: [mem 0xfafff000-0xfaffffff 64bit pref]
[    0.233715] pci 0000:01:00.0: reg 0x20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
[    0.233776] pci 0000:01:00.0: supports D1 D2
[    0.233777] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.238966] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.238973] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.238983] pci 0000:00:1c.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.239048] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.239086] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.239135] pci 0000:04:00.0: [1814:3090] type 00 class 0x028000
[    0.239165] pci 0000:04:00.0: reg 0x10: [mem 0xfbff0000-0xfbffffff]
[    0.246962] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.246971] pci 0000:00:1c.3:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.247044] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.247081] pci 0000:00:1c.6: PCI bridge to [bus 06]
[    0.247118] pci 0000:00:1c.7: PCI bridge to [bus 07]
[    0.247179] pci 0000:00:1e.0: PCI bridge to [bus 08] (subtractive decode)
[    0.247186] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.247188] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.247189] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.247191] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff window] (subtractive decode)
[    0.247192] pci 0000:00:1e.0:   bridge window [mem 0xbc000000-0xdfffffff window] (subtractive decode)
[    0.247193] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff window] (subtractive decode)
[    0.248097] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.248138] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.248176] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.248216] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.248255] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.248294] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.248333] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.248372] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.248435] ACPI: Enabled 3 GPEs in block 00 to 3F
[    0.248520] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.248522] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.248525] vgaarb: loaded
[    0.248526] vgaarb: bridge control possible 0000:00:02.0
[    0.248706] SCSI subsystem initialized
[    0.248745] libata version 3.00 loaded.
[    0.248765] ACPI: bus type USB registered
[    0.248777] usbcore: registered new interface driver usbfs
[    0.248784] usbcore: registered new interface driver hub
[    0.248797] usbcore: registered new device driver usb
[    0.248911] PCI: Using ACPI for IRQ routing
[    0.253766] PCI: Discovered peer bus ff
[    0.253767] PCI: root bus ff: using default resources
[    0.253768] PCI: Probing PCI hardware (bus ff)
[    0.253791] ACPI: \: failed to evaluate _DSM (0x1001)
[    0.253792] PCI host bridge to bus 0000:ff
[    0.253794] pci_bus 0000:ff: root bus resource [io  0x0000-0xffff]
[    0.253795] pci_bus 0000:ff: root bus resource [mem 0x00000000-0xfffffffff]
[    0.253797] pci_bus 0000:ff: No busn resource found for root bus, will use [bus ff-ff]
[    0.253799] pci_bus 0000:ff: busn_res: can not insert [bus ff] under domain [bus 00-ff] (conflicts with (null) [bus 00-ff])
[    0.253803] pci 0000:ff:00.0: [8086:2c61] type 00 class 0x060000
[    0.253839] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.253874] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.253905] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.253938] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.253970] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.254009] pci_bus 0000:ff: busn_res: [bus ff] end is updated to ff
[    0.254011] pci_bus 0000:ff: busn_res: can not insert [bus ff] under domain [bus 00-ff] (conflicts with (null) [bus 00-ff])
[    0.254013] PCI: pci_cache_line_size set to 64 bytes
[    0.254053] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.254054] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    0.254056] e820: reserve RAM buffer [mem 0xbb780000-0xbbffffff]
[    0.254151] NetLabel: Initializing
[    0.254152] NetLabel:  domain hash size = 128
[    0.254153] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.254164] NetLabel:  unlabeled traffic allowed by default
[    0.254223] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.254227] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.256250] clocksource: Switched to clocksource hpet
[    0.261694] AppArmor: AppArmor Filesystem Enabled
[    0.261767] pnp: PnP ACPI init
[    0.261848] system 00:00: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.261850] system 00:00: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.261852] system 00:00: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.261854] system 00:00: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.261858] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.261921] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.262489] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.262539] pnp 00:03: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.262657] system 00:04: [io  0x0a00-0x0a0f] has been reserved
[    0.262659] system 00:04: [io  0x0a10-0x0a1f] has been reserved
[    0.262661] system 00:04: [io  0x0a20-0x0a2f] has been reserved
[    0.262662] system 00:04: [io  0x0a30-0x0a3f] has been reserved
[    0.262665] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.262768] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.262771] system 00:05: [io  0x0800-0x087f] could not be reserved
[    0.262772] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.262774] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.262776] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.262777] system 00:05: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.262780] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.262852] system 00:06: [mem 0xffc00000-0xffefffff] has been reserved
[    0.262855] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.262930] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.262932] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.262934] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.262977] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.262980] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.263129] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.263132] system 00:09: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.263133] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.263135] system 00:09: [mem 0x00100000-0xbbffffff] could not be reserved
[    0.263136] system 00:09: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.263139] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.263232] pnp: PnP ACPI: found 10 devices
[    0.269534] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.269550] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 400000 add_align 100000
[    0.269557] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.269559] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000 add_align 100000
[    0.269560] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000 add_align 100000
[    0.269567] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.269568] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
[    0.269570] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000 add_align 100000
[    0.269576] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    0.269578] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000 add_align 100000
[    0.269584] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 05] add_size 1000
[    0.269586] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000 add_align 100000
[    0.269587] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff] to [bus 05] add_size 200000 add_align 100000
[    0.269594] pci 0000:00:1c.6: bridge window [io  0x1000-0x0fff] to [bus 06] add_size 1000
[    0.269595] pci 0000:00:1c.6: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000 add_align 100000
[    0.269597] pci 0000:00:1c.6: bridge window [mem 0x00100000-0x000fffff] to [bus 06] add_size 200000 add_align 100000
[    0.269603] pci 0000:00:1c.7: bridge window [io  0x1000-0x0fff] to [bus 07] add_size 1000
[    0.269605] pci 0000:00:1c.7: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 07] add_size 200000 add_align 100000
[    0.269607] pci 0000:00:1c.7: bridge window [mem 0x00100000-0x000fffff] to [bus 07] add_size 200000 add_align 100000
[    0.269619] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 400000 min_align 100000
[    0.269621] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x004fffff] res_to_dev_res add_size 400000 min_align 100000
[    0.269622] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269624] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269626] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269627] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269629] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269630] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269632] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269634] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269635] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269637] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269639] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269640] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269642] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269644] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269645] pci 0000:00:1c.6: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269647] pci 0000:00:1c.6: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269648] pci 0000:00:1c.6: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269650] pci 0000:00:1c.6: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269652] pci 0000:00:1c.7: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269653] pci 0000:00:1c.7: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.269655] pci 0000:00:1c.7: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269657] pci 0000:00:1c.7: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.269658] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269660] pci 0000:00:1c.1: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269661] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269663] pci 0000:00:1c.2: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269664] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269666] pci 0000:00:1c.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269667] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269669] pci 0000:00:1c.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269670] pci 0000:00:1c.6: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269672] pci 0000:00:1c.6: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269673] pci 0000:00:1c.7: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269675] pci 0000:00:1c.7: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.269680] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc03fffff]
[    0.269682] pci 0000:00:1c.1: BAR 14: assigned [mem 0xc0400000-0xc05fffff]
[    0.269686] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.269688] pci 0000:00:1c.2: BAR 14: assigned [mem 0xc0800000-0xc09fffff]
[    0.269691] pci 0000:00:1c.2: BAR 15: assigned [mem 0xc0a00000-0xc0bfffff 64bit pref]
[    0.269695] pci 0000:00:1c.3: BAR 15: assigned [mem 0xc0c00000-0xc0dfffff 64bit pref]
[    0.269696] pci 0000:00:1c.4: BAR 14: assigned [mem 0xc0e00000-0xc0ffffff]
[    0.269700] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc1000000-0xc11fffff 64bit pref]
[    0.269701] pci 0000:00:1c.6: BAR 14: assigned [mem 0xc1200000-0xc13fffff]
[    0.269705] pci 0000:00:1c.6: BAR 15: assigned [mem 0xc1400000-0xc15fffff 64bit pref]
[    0.269706] pci 0000:00:1c.7: BAR 14: assigned [mem 0xc1600000-0xc17fffff]
[    0.269710] pci 0000:00:1c.7: BAR 15: assigned [mem 0xc1800000-0xc19fffff 64bit pref]
[    0.269712] pci 0000:00:1c.1: BAR 13: assigned [io  0x1000-0x1fff]
[    0.269713] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.269715] pci 0000:00:1c.3: BAR 13: assigned [io  0x3000-0x3fff]
[    0.269717] pci 0000:00:1c.4: BAR 13: assigned [io  0x4000-0x4fff]
[    0.269719] pci 0000:00:1c.6: BAR 13: assigned [io  0x5000-0x5fff]
[    0.269721] pci 0000:00:1c.7: BAR 13: assigned [io  0x6000-0x6fff]
[    0.269725] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.269727] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.269731] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc03fffff]
[    0.269733] pci 0000:00:1c.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.269738] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.269740] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.269743] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc05fffff]
[    0.269746] pci 0000:00:1c.1:   bridge window [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.269750] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.269752] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.269755] pci 0000:00:1c.2:   bridge window [mem 0xc0800000-0xc09fffff]
[    0.269758] pci 0000:00:1c.2:   bridge window [mem 0xc0a00000-0xc0bfffff 64bit pref]
[    0.269762] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.269764] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.269768] pci 0000:00:1c.3:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.269770] pci 0000:00:1c.3:   bridge window [mem 0xc0c00000-0xc0dfffff 64bit pref]
[    0.269775] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.269777] pci 0000:00:1c.4:   bridge window [io  0x4000-0x4fff]
[    0.269780] pci 0000:00:1c.4:   bridge window [mem 0xc0e00000-0xc0ffffff]
[    0.269783] pci 0000:00:1c.4:   bridge window [mem 0xc1000000-0xc11fffff 64bit pref]
[    0.269787] pci 0000:00:1c.6: PCI bridge to [bus 06]
[    0.269789] pci 0000:00:1c.6:   bridge window [io  0x5000-0x5fff]
[    0.269792] pci 0000:00:1c.6:   bridge window [mem 0xc1200000-0xc13fffff]
[    0.269795] pci 0000:00:1c.6:   bridge window [mem 0xc1400000-0xc15fffff 64bit pref]
[    0.269799] pci 0000:00:1c.7: PCI bridge to [bus 07]
[    0.269801] pci 0000:00:1c.7:   bridge window [io  0x6000-0x6fff]
[    0.269805] pci 0000:00:1c.7:   bridge window [mem 0xc1600000-0xc17fffff]
[    0.269807] pci 0000:00:1c.7:   bridge window [mem 0xc1800000-0xc19fffff 64bit pref]
[    0.269812] pci 0000:00:1e.0: PCI bridge to [bus 08]
[    0.269821] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.269822] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.269824] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.269825] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.269826] pci_bus 0000:00: resource 8 [mem 0xbc000000-0xdfffffff window]
[    0.269828] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff window]
[    0.269829] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.269831] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xc03fffff]
[    0.269832] pci_bus 0000:01: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.269833] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.269835] pci_bus 0000:02: resource 1 [mem 0xc0400000-0xc05fffff]
[    0.269836] pci_bus 0000:02: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.269837] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.269839] pci_bus 0000:03: resource 1 [mem 0xc0800000-0xc09fffff]
[    0.269840] pci_bus 0000:03: resource 2 [mem 0xc0a00000-0xc0bfffff 64bit pref]
[    0.269841] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.269843] pci_bus 0000:04: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.269844] pci_bus 0000:04: resource 2 [mem 0xc0c00000-0xc0dfffff 64bit pref]
[    0.269845] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
[    0.269847] pci_bus 0000:05: resource 1 [mem 0xc0e00000-0xc0ffffff]
[    0.269848] pci_bus 0000:05: resource 2 [mem 0xc1000000-0xc11fffff 64bit pref]
[    0.269849] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.269851] pci_bus 0000:06: resource 1 [mem 0xc1200000-0xc13fffff]
[    0.269852] pci_bus 0000:06: resource 2 [mem 0xc1400000-0xc15fffff 64bit pref]
[    0.269853] pci_bus 0000:07: resource 0 [io  0x6000-0x6fff]
[    0.269855] pci_bus 0000:07: resource 1 [mem 0xc1600000-0xc17fffff]
[    0.269856] pci_bus 0000:07: resource 2 [mem 0xc1800000-0xc19fffff 64bit pref]
[    0.269858] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7 window]
[    0.269859] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff window]
[    0.269860] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.269862] pci_bus 0000:08: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.269863] pci_bus 0000:08: resource 8 [mem 0xbc000000-0xdfffffff window]
[    0.269864] pci_bus 0000:08: resource 9 [mem 0xf0000000-0xfed8ffff window]
[    0.269867] pci_bus 0000:ff: resource 4 [io  0x0000-0xffff]
[    0.269868] pci_bus 0000:ff: resource 5 [mem 0x00000000-0xfffffffff]
[    0.269899] NET: Registered protocol family 2
[    0.270060] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.270194] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.270362] TCP: Hash tables configured (established 65536 bind 65536)
[    0.270398] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.270427] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.270491] NET: Registered protocol family 1
[    0.270503] pci 0000:00:02.0: Video device with shadowed ROM
[    0.320304] PCI: CLS 32 bytes, default 64
[    0.320373] Trying to unpack rootfs image as initramfs...
[    0.789564] Freeing initrd memory: 35268K (ffff880033b0e000 - ffff880035d7f000)
[    0.789603] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.789605] software IO TLB [mem 0xb7780000-0xbb780000] (64MB) mapped at [ffff8800b7780000-ffff8800bb77ffff]
[    0.789788] Scanning for low memory corruption every 60 seconds
[    0.790149] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.790187] audit: initializing netlink subsys (disabled)
[    0.790205] audit: type=2000 audit(1461441752.680:1): initialized
[    0.790512] Initialise system trusted keyring
[    0.790603] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.791810] zbud: loaded
[    0.791971] VFS: Disk quotas dquot_6.6.0
[    0.792001] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.792404] fuse init (API version 7.23)
[    0.792519] Key type big_key registered
[    0.792796] Key type asymmetric registered
[    0.792800] Asymmetric key parser 'x509' registered
[    0.792833] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.792859] io scheduler noop registered
[    0.792861] io scheduler deadline registered (default)
[    0.792886] io scheduler cfq registered
[    0.793151] pcieport 0000:00:1c.1: enabling device (0104 -> 0107)
[    0.793234] pcieport 0000:00:1c.2: enabling device (0104 -> 0107)
[    0.793316] pcieport 0000:00:1c.3: enabling device (0106 -> 0107)
[    0.793396] pcieport 0000:00:1c.4: enabling device (0104 -> 0107)
[    0.793475] pcieport 0000:00:1c.6: enabling device (0104 -> 0107)
[    0.793555] pcieport 0000:00:1c.7: enabling device (0104 -> 0107)
[    0.793596] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.793601] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.793621] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    0.793622] vesafb: scrolling: redraw
[    0.793624] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.793636] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90001000000, using 5120k, total 5120k
[    0.793724] Console: switching to colour frame buffer device 160x64
[    0.793753] fb0: VESA VGA frame buffer device
[    0.793764] intel_idle: MWAIT substates: 0x1120
[    0.793766] intel_idle: v0.4.1 model 0x25
[    0.793766] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.793944] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.793947] ACPI: Power Button [PWRB]
[    0.793977] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.793978] ACPI: Power Button [PWRF]
[    0.794268] thermal LNXTHERM:00: registered as thermal_zone0
[    0.794269] ACPI: Thermal Zone [THRM] (8 C)
[    0.794408] thermal LNXTHERM:01: registered as thermal_zone1
[    0.794409] ACPI: Thermal Zone [THRS] (38 C)
[    0.794435] GHES: HEST is not enabled!
[    0.794513] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.795795] Linux agpgart interface v0.103
[    0.795848] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    0.795863] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.796435] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.796577] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.798993] brd: module loaded
[    0.800146] loop: module loaded
[    0.800340] libphy: Fixed MDIO Bus: probed
[    0.800343] tun: Universal TUN/TAP device driver, 1.6
[    0.800344] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.800381] PPP generic driver version 2.4.2
[    0.800432] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.800436] ehci-pci: EHCI PCI platform driver
[    0.800573] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.800579] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.800590] ehci-pci 0000:00:1a.0: debug port 2
[    0.804550] ehci-pci 0000:00:1a.0: cache line size of 32 is not supported
[    0.804564] ehci-pci 0000:00:1a.0: irq 16, io mem 0xfbef8000
[    0.816342] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.816481] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.816483] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.816485] usb usb1: Product: EHCI Host Controller
[    0.816486] usb usb1: Manufacturer: Linux 4.4.0-21-generic ehci_hcd
[    0.816487] usb usb1: SerialNumber: 0000:00:1a.0
[    0.816798] hub 1-0:1.0: USB hub found
[    0.816816] hub 1-0:1.0: 2 ports detected
[    0.817013] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.817018] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.817026] ehci-pci 0000:00:1d.0: debug port 2
[    0.820966] ehci-pci 0000:00:1d.0: cache line size of 32 is not supported
[    0.820974] ehci-pci 0000:00:1d.0: irq 23, io mem 0xfbef2000
[    0.832350] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.832412] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.832416] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.832419] usb usb2: Product: EHCI Host Controller
[    0.832422] usb usb2: Manufacturer: Linux 4.4.0-21-generic ehci_hcd
[    0.832425] usb usb2: SerialNumber: 0000:00:1d.0
[    0.832718] hub 2-0:1.0: USB hub found
[    0.832733] hub 2-0:1.0: 2 ports detected
[    0.832854] ehci-platform: EHCI generic platform driver
[    0.832865] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.832869] ohci-pci: OHCI PCI platform driver
[    0.832878] ohci-platform: OHCI generic platform driver
[    0.832885] uhci_hcd: USB Universal Host Controller Interface driver
[    0.832941] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.833412] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.833422] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.833834] mousedev: PS/2 mouse device common for all mice
[    0.834482] rtc_cmos 00:01: RTC can wake from S4
[    0.834727] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.834762] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.834784] i2c /dev entries driver
[    0.834871] device-mapper: uevent: version 1.0.3
[    0.835001] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    0.835034] ledtrig-cpu: registered to indicate activity on CPUs
[    0.835665] NET: Registered protocol family 10
[    0.835823] NET: Registered protocol family 17
[    0.835834] Key type dns_resolver registered
[    0.836005] microcode: CPU0 sig=0x20655, pf=0x2, revision=0x4
[    0.836009] microcode: CPU1 sig=0x20655, pf=0x2, revision=0x4
[    0.836015] microcode: CPU2 sig=0x20655, pf=0x2, revision=0x4
[    0.836022] microcode: CPU3 sig=0x20655, pf=0x2, revision=0x4
[    0.836056] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.836189] registered taskstats version 1
[    0.836204] Loading compiled-in X.509 certificates
[    0.836986] Loaded X.509 cert 'Build time autogenerated kernel key: fc7c0e9f152f32eca50ea2d9722926e5127af244'
[    0.837004] zswap: loaded using pool lzo/zbud
[    0.838557] Key type trusted registered
[    0.840893] Key type encrypted registered
[    0.840900] AppArmor: AppArmor sha1 policy hashing enabled
[    0.840903] ima: No TPM chip found, activating TPM-bypass!
[    0.840932] evm: HMAC attrs: 0x1
[    0.841211]   Magic number: 12:798:43
[    0.841330] rtc_cmos 00:01: setting system clock to 2016-04-23 20:02:33 UTC (1461441753)
[    0.842129] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.842131] EDD information not available.
[    0.842178] PM: Hibernation image not present or could not be loaded.
[    0.843384] Freeing unused kernel memory: 1476K (ffffffff81f41000 - ffffffff820b2000)
[    0.843386] Write protecting the kernel read-only data: 14336k
[    0.843887] Freeing unused kernel memory: 1872K (ffff88000182c000 - ffff880001a00000)
[    0.844238] Freeing unused kernel memory: 176K (ffff880001dd4000 - ffff880001e00000)
[    0.855066] random: systemd-udevd urandom read with 4 bits of entropy available
[    0.878397] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    0.886271] wmi: Mapper loaded
[    0.890086] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.890097] r8169 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.890467] r8169 0000:01:00.0 eth0: RTL8168e/8111e at 0xffffc90000e96000, d0:27:88:3b:e4:32, XID 0c200000 IRQ 24
[    0.890470] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.892857] ahci 0000:00:1f.2: version 3.0
[    0.892958] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    0.892991] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.892993] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    0.895088] [drm] Initialized drm 1.1.0 20060810
[    0.932787] scsi host0: ahci
[    0.932881] scsi host1: ahci
[    0.932965] scsi host2: ahci
[    0.933042] scsi host3: ahci
[    0.933117] scsi host4: ahci
[    0.933192] scsi host5: ahci
[    0.933231] ata1: SATA max UDMA/133 abar m2048@0xfbef0000 port 0xfbef0100 irq 25
[    0.933233] ata2: SATA max UDMA/133 abar m2048@0xfbef0000 port 0xfbef0180 irq 25
[    0.933235] ata3: SATA max UDMA/133 abar m2048@0xfbef0000 port 0xfbef0200 irq 25
[    0.933237] ata4: SATA max UDMA/133 abar m2048@0xfbef0000 port 0xfbef0280 irq 25
[    0.933238] ata5: SATA max UDMA/133 abar m2048@0xfbef0000 port 0xfbef0300 irq 25
[    0.933240] ata6: SATA max UDMA/133 abar m2048@0xfbef0000 port 0xfbef0380 irq 25
[    0.933816] [drm] Memory usable by graphics device = 2048M
[    0.933821] checking generic (d0000000 500000) vs hw (d0000000 10000000)
[    0.933823] fb: switching to inteldrmfb from VESA VGA
[    0.933858] Console: switching to colour dummy device 80x25
[    0.933935] [drm] Replacing VGA console driver
[    0.940122] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.940124] [drm] Driver supports precise vblank timestamp query.
[    0.940691] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.943139] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[    1.006288] fbcon: inteldrmfb (fb0) is primary device
[    1.006411] Console: switching to colour frame buffer device 240x67
[    1.006455] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.128335] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.144339] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.252343] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.260922] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.260928] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.261312] hub 1-1:1.0: USB hub found
[    1.261362] hub 1-1:1.0: 6 ports detected
[    1.270659] ata1.00: ATA-8: WDC WD10EARS-22Y5B1, 80.00A80, max UDMA/133
[    1.270665] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.272637] ata1.00: configured for UDMA/133
[    1.272952] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EARS-22Y 0A80 PQ: 0 ANSI: 5
[    1.273424] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[    1.273427] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.273435] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.273475] sd 0:0:0:0: [sda] Write Protect is off
[    1.273477] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.273506] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.276829] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.276835] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.277215] hub 2-1:1.0: USB hub found
[    1.277390] hub 2-1:1.0: 8 ports detected
[    1.322864]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.324042] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.548324] usb 2-1.2: new full-speed USB device number 3 using ehci-pci
[    1.592343] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.594908] ata2.00: ATAPI: ATAPI   DVD A  DH16ABSH, YA12, max UDMA/100
[    1.595878] ata2.00: configured for UDMA/100
[    1.598399] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH16ABSH  YA12 PQ: 0 ANSI: 5
[    1.614965] sr 1:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.614970] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.615178] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.615242] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.644419] usb 2-1.2: New USB device found, idVendor=046d, idProduct=c52e
[    1.644425] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.644429] usb 2-1.2: Product: USB Receiver
[    1.644432] usb 2-1.2: Manufacturer: Logitech
[    1.648350] hidraw: raw HID events driver (C) Jiri Kosina
[    1.653046] usbcore: registered new interface driver usbhid
[    1.653047] usbhid: USB HID core driver
[    1.654360] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:046D:C52E.0001/input/input5
[    1.708578] hid-generic 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input0
[    1.708795] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:046D:C52E.0002/input/input6
[    1.720338] usb 2-1.5: new high-speed USB device number 4 using ehci-pci
[    1.764835] hid-generic 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input1
[    1.788341] tsc: Refined TSC clocksource calibration: 3191.999 MHz
[    1.788346] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2e02c398820, max_idle_ns: 440795273435 ns
[    1.814660] usb 2-1.5: New USB device found, idVendor=058f, idProduct=6361
[    1.814666] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.814670] usb 2-1.5: Product: Mass Storage Device
[    1.814674] usb 2-1.5: Manufacturer: Generic
[    1.814677] usb 2-1.5: SerialNumber: 058F63616476
[    1.817880] usb-storage 2-1.5:1.0: USB Mass Storage device detected
[    1.818004] scsi host6: usb-storage 2-1.5:1.0
[    1.818060] usbcore: registered new interface driver usb-storage
[    1.819192] usbcore: registered new interface driver uas
[    1.932352] ata3: SATA link down (SStatus 0 SControl 300)
[    2.252347] ata4: SATA link down (SStatus 0 SControl 300)
[    2.572349] ata5: SATA link down (SStatus 0 SControl 300)
[    2.788535] clocksource: Switched to clocksource tsc
[    2.817466] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.818212] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    2.818673] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.818912] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.834772] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.835575] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.892348] ata6: SATA link down (SStatus 0 SControl 300)
[    3.904413] floppy0: no floppy controllers found
[    3.904430] work still pending
[    4.849132] random: nonblocking pool is initialized
[    4.991144] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    6.300586] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    6.300699] systemd[1]: Detected architecture x86-64.
[    6.317062] systemd[1]: Set hostname to <bedroom-l>.
[    7.923205] systemd-sysv-generator[245]: Overwriting existing symlink /run/systemd/generator.late/vncserver-virtuald.service with real service.
[    7.923418] systemd-sysv-generator[245]: Overwriting existing symlink /run/systemd/generator.late/vncserver-x11-serviced.service with real service.
[    8.401680] systemd[1]: Reached target Encrypted Volumes.
[    8.401732] systemd[1]: Reached target User and Group Name Lookups.
[    8.401764] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    8.401872] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    8.401898] systemd[1]: Listening on fsck to fsckd communication Socket.
[    8.401951] systemd[1]: Listening on Journal Audit Socket.
[    8.401984] systemd[1]: Listening on Journal Socket (/dev/log).
[    8.402005] systemd[1]: Listening on Syslog Socket.
[    8.402023] systemd[1]: Listening on udev Kernel Socket.
[    8.402122] systemd[1]: Created slice User and Session Slice.
[    8.402156] systemd[1]: Listening on udev Control Socket.
[    8.402188] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    8.402259] systemd[1]: Created slice System Slice.
[    8.402348] systemd[1]: Created slice system-getty.slice.
[    8.402358] systemd[1]: Reached target Slices.
[    8.402431] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    8.402466] systemd[1]: Listening on Journal Socket.
[    8.476576] systemd[1]: Starting Load Kernel Modules...
[    8.477012] systemd[1]: Starting Braille Device Support...
[    8.477433] systemd[1]: Mounting Debug File System...
[    8.477803] systemd[1]: Mounting RPC Pipe File System...
[    8.478387] systemd[1]: Starting Journal Service...
[    8.478940] systemd[1]: Starting Uncomplicated firewall...
[    8.544644] systemd[1]: Started Read required files in advance.
[    8.545248] systemd[1]: Mounting Huge Pages File System...
[    8.545729] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    8.546157] systemd[1]: Mounting POSIX Message Queue File System...
[    8.667687] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    8.680575] systemd[1]: Starting Create Static Device Nodes in /dev...
[    8.706707] systemd[1]: Started Uncomplicated firewall.
[    9.050135] systemd[1]: Mounted Huge Pages File System.
[    9.050168] systemd[1]: Mounted POSIX Message Queue File System.
[    9.050181] systemd[1]: Mounted Debug File System.
[    9.075677] lp: driver loaded but no devices found
[    9.093458] ppdev: user-space parallel port driver
[    9.364697] systemd[1]: Started Load Kernel Modules.
[    9.376467] systemd[1]: Starting Apply Kernel Variables...
[    9.376976] systemd[1]: Mounting FUSE Control File System...
[    9.380840] systemd[1]: Mounted FUSE Control File System.
[    9.430643] systemd[1]: Started Journal Service.
[    9.675433] RPC: Registered named UNIX socket transport module.
[    9.675436] RPC: Registered udp transport module.
[    9.675437] RPC: Registered tcp transport module.
[    9.675437] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   13.517853] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   13.892836] systemd-journald[254]: Received request to flush runtime journal from PID 1
[   14.572388] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.695209] ACPI Warning: SystemIO range 0x0000000000000828-0x000000000000082F conflicts with OpRegion 0x0000000000000800-0x000000000000084F (\PMRG) (20150930/utaddress-254)
[   14.695216] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.695220] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000051F (\LEDC) (20150930/utaddress-254)
[   14.695223] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.695243] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.029823] gpio_ich: GPIO from 436 to 511 on gpio_ich
[   15.214346] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   15.495343] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3090, rev 3213 detected
[   15.498778] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   15.599445] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   16.009990] snd_hda_codec_realtek hdaudioC0D2: autoconfig for ALC662 rev1: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   16.009993] snd_hda_codec_realtek hdaudioC0D2:    speaker_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   16.009995] snd_hda_codec_realtek hdaudioC0D2:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.009996] snd_hda_codec_realtek hdaudioC0D2:    mono: mono_out=0x0
[   16.009998] snd_hda_codec_realtek hdaudioC0D2:    dig-out=0x1e/0x0
[   16.009999] snd_hda_codec_realtek hdaudioC0D2:    inputs:
[   16.010001] snd_hda_codec_realtek hdaudioC0D2:      Front Mic=0x19
[   16.010003] snd_hda_codec_realtek hdaudioC0D2:      Rear Mic=0x18
[   16.010004] snd_hda_codec_realtek hdaudioC0D2:      Line=0x1a
[   16.026957] input: HDA Intel MID Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.027016] input: HDA Intel MID Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.027062] input: HDA Intel MID Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.027110] input: HDA Intel MID Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.027156] input: HDA Intel MID Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.027203] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   16.444459] cfg80211: World regulatory domain updated:
[   16.444464] cfg80211:  DFS Master region: unset
[   16.444465] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   16.444467] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   16.444468] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   16.444469] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   16.444471] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   16.444473] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   16.444474] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   16.444475] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   16.444476] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   17.182627] Adding 3999740k swap on /dev/sda5.  Priority:-1 extents:1 across:3999740k FS
[   17.584535] floppy0: no floppy controllers found
[   17.584553] work still pending
[   19.928603] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   26.814439] audit: type=1400 audit(1461441779.467:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=639 comm="apparmor_parser"
[   26.960876] audit: type=1400 audit(1461441779.615:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=636 comm="apparmor_parser"
[   26.960883] audit: type=1400 audit(1461441779.615:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=636 comm="apparmor_parser"
[   26.960887] audit: type=1400 audit(1461441779.615:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=636 comm="apparmor_parser"
[   26.960891] audit: type=1400 audit(1461441779.615:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=636 comm="apparmor_parser"
[   27.083064] audit: type=1400 audit(1461441779.735:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=635 comm="apparmor_parser"
[   27.083070] audit: type=1400 audit(1461441779.735:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=635 comm="apparmor_parser"
[   27.123997] audit: type=1400 audit(1461441779.775:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=641 comm="apparmor_parser"
[   27.124004] audit: type=1400 audit(1461441779.775:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=641 comm="apparmor_parser"
[   27.124008] audit: type=1400 audit(1461441779.775:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*//pxgsettings" pid=641 comm="apparmor_parser"
[   28.120947] cgroup: new mount options do not match the existing superblock, will be ignored
[   39.109669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.112920] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.364278] r8169 0000:01:00.0 eth0: link down
[   39.364279] r8169 0000:01:00.0 eth0: link down
[   39.364319] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.003178] r8169 0000:01:00.0 eth0: link up
[   41.003194] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   69.521542] FS-Cache: Loaded
[   69.557234] FS-Cache: Netfs 'nfs' registered for caching
[   69.590484] NFS: Registering the id_resolver key type
[   69.590494] Key type id_resolver registered
[   69.590495] Key type id_legacy registered
[  159.852825] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[ 4492.091101] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[ 5341.892089] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[15392.119904] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[15887.526428] perf interrupt took too long (2513 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[17164.360715] [drm:i915_hangcheck_elapsed [i915]] *ERROR* Hangcheck timer elapsed... bsd ring idle
[21172.228258] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[24560.225063] perf interrupt took too long (5018 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[48512.455096] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[58636.895971] r8169 0000:01:00.0 eth0: link down
[58641.264265] r8169 0000:01:00.0 eth0: link up
[64758.757768] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[78763.859125] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[78837.405419] show_signal_msg: 48 callbacks suppressed
[78837.405425] metacity[1759]: segfault at 40c3362 ip 0000000000426f4d sp 00007ffe3456db78 error 4 in metacity[400000+8d000]
[82568.497761] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[105118.995995] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[138951.703382] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[151944.436756] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun

```

---

### Post by DuckHook on 2016-04-25
The last part of your dmesg output indicates a bug in the intel video driver. This seems to be a difficult alligator for the developers to wrestle with as also indicated in [this]("http://askubuntu.com/questions/507302/updated-intel-display-driver-causing-errors-when-booting") post, from askubuntu. They've been wrestling with this since the introduction of 14.04. This bug is also presumably what is causing the segfault in metacity (I've highlighted it in red).```
[  159.852825] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[ 4492.091101] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[ 5341.892089] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[15392.119904] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[15887.526428] perf interrupt took too long (2513 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[17164.360715] [drm:i915_hangcheck_elapsed [i915]] *ERROR* Hangcheck timer elapsed... bsd ring idle
[21172.228258] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[24560.225063] perf interrupt took too long (5018 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[48512.455096] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[58636.895971] r8169 0000:01:00.0 eth0: link down
[58641.264265] r8169 0000:01:00.0 eth0: link up
[64758.757768] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[78763.859125] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[78837.405419] show_signal_msg: 48 callbacks suppressed
[COLOR="#FF0000"][78837.405425] metacity[1759]: segfault at 40c3362 ip 0000000000426f4d sp 00007ffe3456db78 error 4 in metacity[400000+8d000][/COLOR]
[82568.497761] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[105118.995995] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[138951.703382] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[151944.436756] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
```Frankly, I'm surprised you are even getting reliable video.

As I see it, you have two choices:

1. If your system is otherwise stable, and you can live with the wonky audio, then you can keep your system current by installing updates as they are issued and hope that one of them fixes your problem, or

2. Do as QLee suggests above (excellent suggestion, QLee) and go back to a known working release in 14.04. Then wait for the first point release of 16.04 before upgrading. Even then, run a Live/USB session and look in dmesg for what I've just pointed out before installing. 14.04 is good until 2019, so it is better to have a stable reliable system than the latest shiny pony.

What follows is a big ask, but I will float it out there anyway. It is very valuable to the developers when people like you can report these bugs to Launchpad. This is admittedly a somewhat intimidating process for new users, but since you have been using Ubuntu from 12.04, I am assuming that you may feel comfortable enough doing so. This is the way bugs are squashed and keeps Ubuntu/Linux constantly improving for all of us. I'll leave that decision up to you.

---

### Post by HEXYEBO on 2016-04-25
,
Thanks again for getting back. I reviewed the link you provided.
Interestingly, I've never had any HDMI video issues with this PC. Since the issue is pointing to the driver, I purged and reinstalled it:
```

sudo ubuntu-drivers list
intel-microcode
...
sudo apt-get purge intel-microcode iucode-tool
...
sudo reboot


```
After reboot:
```

sudo ubuntu-drivers autoinstall && sudo reboot

```

The system seems stable now, after a couple of hours. No more segfaults in the *[COLOR=#000000][I]dmesg command output.*[/COLOR][/I]
But like I mentioned before, this has been happening very sporadically. Will wait and see. Worst case, I will have to live with this.

HEX.

---

### Post by DuckHook on 2016-04-25
Glad it looks more stable so far. If this fix works and holds, please mark thread "solved" to help others searching for solutions to similar problems. If the problem recurs, you may wish to consider QLee's suggestion. It's good advice.

I have both 16.04 and 14.04 installed on separate partitions. I play with the newer but do my real work on the older, so it's a form of QLee's approach.

Good luck!

---

### Post by HEXYEBO on 2016-04-25
The behavior is back after few hours. I have found an article [here]("http://askubuntu.com/questions/69820/how-do-i-set-a-pulseaudio-card-profile-persistently-across-reboots") that deals with a similar problem.

Apparently I can change the output device from CLI:

```

...
pacmd set-card-profile 0 output:hdmi-stereo
...
pacmd set-default-sink alsa_output.pci-0000_00_1b.0.hdmi-stereo
...

```

After that the issue is fixed. And if it does not stay fixed, I should be able to script a solution.

---

### Post by sailingboyLLB on 2016-05-30
were you able to actually solve the problem or just script a work around?

i think i'm having a similar problem.
[http://ubuntuforums.org/showthread.php?t=2322018](http://ubuntuforums.org/showthread.php?t=2322018)

---

