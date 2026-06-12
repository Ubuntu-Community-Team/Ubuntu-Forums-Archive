---
title: "nautilus stops responding after upgrade 11.10 to 12.04"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by rocketscove on 2012-04-29
I had 11.10 working with no problems on netbook (samsung n145). I used update manager to go to 12.04. Nautilus now hangs the computer to the point of ctl-alt-del must be used to shutdown/reboot.

Can I delete any files in ~/gnome or nautilus that will be rebuilt on reboot?

 LXDE appears to work (an internal fail of 12.04 did occur in lxde).

---

### Post by rocketscove on 2012-04-29
I tried reinstall of Nautilus,gnome, nautilus-open-terminal (synaptic--don't see this option in ubuntu software center).
Am still seeing strange behavior...eg: rt clk at any nautilus location and select open in terminal gives >>>>

user@name:~/desktop$
ls does list the desktop files

I don't understand this. Please give me some direction. Is nautilus broken, what do I repair???

---

### Post by rocketscove on 2012-04-29
Desperately need help (advice).....I cannot concisely define the problem...
1-one click in rox terminal and complete freeze.
2- sometimes just clicking the task bar will freeze it.
3- I don't think it has froze with firefox open.
4- terminal and  nautilus have been open when it freezes.

Freeze means: no response to touchscreen, touch pad, ctl-alt-del, alt-f4, hud, etc.
 I can open tty (ctl-alt-f2-6) and reboot or power off.
Here is my dmesg after a freeze...:>>

```
    
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-24-generic (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 (Ubuntu 3.2.0-24.37-generic 3.2.14)
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
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5b0000 (usable)
[    0.000000]  BIOS-e820: 000000007f5b0000 - 000000007f5c0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5c0000 - 000000007f5c3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5c3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: SAMSUNG ELECTRONICS CO., LTD. N250P                      /N250P                      , BIOS 01HG.M011.20101209.RHU 12/09/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f5b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F600000 mask 0FFE00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2038M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00f7d30] f7d30
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36504000 - 3727a000
[    0.000000] ACPI: RSDP 000f7d00 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f5b82ef 0007C (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f5bfc92 000F4 (v03 INTEL           06040000 PTL  00000002)
[    0.000000] ACPI: DSDT 7f5b9e9e 05D00 (v01  INTEL BEARG31A 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 7f5c2fc0 00040
[    0.000000] ACPI: MCFG 7f5bfd86 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 7f5bfdc2 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 7f5bfdfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f5bfe62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7f5bfe8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7f5b8f29 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8e83 000A6 (v01  PmRef  Cpu3Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8ddd 000A6 (v01  PmRef  Cpu2Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b8d37 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5b836b 009CC (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1149MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f5b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007f5b0
[    0.000000] On node 0 totalpages: 521533
[    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map f5514200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292022 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s31616 r0 d21632 u2097152
[    0.000000] pcpu-alloc: s31616 r0 d21632 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517457
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=120a448e-24a7-4fd4-9635-95314dc627ab ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8346112 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f5b0)
[    0.000000] Memory: 2036892k/2086592k available (5627k kernel code, 49240k reserved, 2764k data, 712k init, 1177288k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
[    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.461 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.92 BogoMIPS (lpj=6649844)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004066] Security Framework initialized
[    0.004105] AppArmor: AppArmor initialized
[    0.004110] Yama: becoming mindful.
[    0.004229] Mount-cache hash table entries: 512
[    0.004496] Initializing cgroup subsys cpuacct
[    0.004511] Initializing cgroup subsys memory
[    0.004529] Initializing cgroup subsys devices
[    0.004535] Initializing cgroup subsys freezer
[    0.004541] Initializing cgroup subsys blkio
[    0.004557] Initializing cgroup subsys perf_event
[    0.004606] CPU: Physical Processor ID: 0
[    0.004611] CPU: Processor Core ID: 0
[    0.004617] mce: CPU supports 5 MCE banks
[    0.004630] CPU0: Thermal monitoring handled by SMI
[    0.004637] using mwait in idle threads.
[    0.009938] ACPI: Core revision 20110623
[    0.020028] ftrace: allocating 25954 entries in 51 pages
[    0.024095] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024589] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066708] CPU0: Intel(R) Atom(TM) CPU N455   @ 1.66GHz stepping 0a
[    0.068003] APIC calibration not consistent with PM-Timer: 1691ms instead of 100ms
[    0.068003] APIC delta adjusted to PM-Timer: 1039050 (17580540)
[    0.068003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.068003] ... version:                3
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f44ea000 soft=f44ec000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.008000] CPU0: Thermal monitoring enabled (TM1)
[    0.156065] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156151] Brought up 2 CPUs
[    0.156159] Total of 2 processors activated (6649.91 BogoMIPS).
[    0.156731] devtmpfs: initialized
[    0.156731] EVM: security.selinux
[    0.156731] EVM: security.SMACK64
[    0.156731] EVM: security.capability
[    0.156731] PM: Registering ACPI NVS region at 7f5c0000 (12288 bytes)
[    0.160488] print_constraints: dummy: 
[    0.160541] RTC time: 18:04:06, date: 04/29/12
[    0.160629] NET: Registered protocol family 16
[    0.160839] Trying to unpack rootfs image as initramfs...
[    0.161054] EISA bus registered
[    0.161146] ACPI: bus type pci registered
[    0.161335] PCI: MMCONFIG for domain 0000 [bus 00-10] at [mem 0xe0000000-0xe10fffff] (base 0xe0000000)
[    0.161347] PCI: MMCONFIG at [mem 0xe0000000-0xe10fffff] reserved in E820
[    0.161354] PCI: Using MMCONFIG for extended config space
[    0.161360] PCI: Using configuration type 1 for base access
[    0.176273] bio: create slab <bio-0> at 0
[    0.176570] ACPI: Added _OSI(Module Device)
[    0.176579] ACPI: Added _OSI(Processor Device)
[    0.176587] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.176595] ACPI: Added _OSI(Processor Aggregator Device)
[    0.180090] ACPI: EC: Look up EC in DSDT
[    0.193512] ACPI: SSDT 7f5b9a1f 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.194395] ACPI: Dynamic OEM Table Load:
[    0.194406] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.195043] ACPI: SSDT 7f5b9188 00708 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.195867] ACPI: Dynamic OEM Table Load:
[    0.195879] ACPI: SSDT   (null) 00708 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.196835] ACPI: SSDT 7f5b9c22 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.197694] ACPI: Dynamic OEM Table Load:
[    0.197706] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.198144] ACPI: SSDT 7f5b9890 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.198973] ACPI: Dynamic OEM Table Load:
[    0.198984] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.200832] ACPI: Interpreter enabled
[    0.200832] ACPI: (supports S0 S3 S4 S5)
[    0.200832] ACPI: Using IOAPIC for interrupt routing
[    0.216164] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.216661] ACPI: No dock devices found.
[    0.216668] HEST: Table not found.
[    0.216683] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.219014] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.219040] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4420e88), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.219067] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.219090] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.223402] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.223415] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.223426] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.223435] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.223444] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.223454] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.223464] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf7ffffff]
[    0.223474] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xfdff]
[    0.223512] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.223595] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.223617] pci 0000:00:02.0: reg 10: [mem 0xf0300000-0xf037ffff]
[    0.223632] pci 0000:00:02.0: reg 14: [io  0x18d0-0x18d7]
[    0.223646] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.223661] pci 0000:00:02.0: reg 1c: [mem 0xf0000000-0xf00fffff]
[    0.223729] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.223748] pci 0000:00:02.1: reg 10: [mem 0xf0380000-0xf03fffff]
[    0.223903] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.223940] pci 0000:00:1b.0: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.224103] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.224118] pci 0000:00:1b.0: PME# disabled
[    0.224172] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.224324] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.224336] pci 0000:00:1c.0: PME# disabled
[    0.224388] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.224537] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.224549] pci 0000:00:1c.1: PME# disabled
[    0.224600] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.224748] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.224760] pci 0000:00:1c.2: PME# disabled
[    0.224812] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.224961] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.224973] pci 0000:00:1c.3: PME# disabled
[    0.225026] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.225110] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.225180] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.225259] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.225326] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.225405] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.225472] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.225551] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.225634] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.225675] pci 0000:00:1d.7: reg 10: [mem 0xf0604000-0xf06043ff]
[    0.225823] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.225836] pci 0000:00:1d.7: PME# disabled
[    0.225884] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.226021] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.226142] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.226227] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.226270] pci 0000:00:1f.2: reg 10: [io  0x18e8-0x18ef]
[    0.226292] pci 0000:00:1f.2: reg 14: [io  0x18dc-0x18df]
[    0.226313] pci 0000:00:1f.2: reg 18: [io  0x18e0-0x18e7]
[    0.226334] pci 0000:00:1f.2: reg 1c: [io  0x18d8-0x18db]
[    0.226355] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.226377] pci 0000:00:1f.2: reg 24: [mem 0xf0604400-0xf06047ff]
[    0.226459] pci 0000:00:1f.2: PME# supported from D3hot
[    0.226471] pci 0000:00:1f.2: PME# disabled
[    0.226506] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.226588] pci 0000:00:1f.3: reg 20: [io  0x18a0-0x18bf]
[    0.226766] pci 0000:05:00.0: [168c:002b] type 0 class 0x000280
[    0.226812] pci 0000:05:00.0: reg 10: [mem 0xf0100000-0xf010ffff 64bit]
[    0.227000] pci 0000:05:00.0: supports D1
[    0.227009] pci 0000:05:00.0: PME# supported from D0 D1 D3hot
[    0.227022] pci 0000:05:00.0: PME# disabled
[    0.232073] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.232095] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.232199] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.232477] pci 0000:09:00.0: [11ab:4354] type 0 class 0x000200
[    0.232691] pci 0000:09:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    0.232800] pci 0000:09:00.0: reg 18: [io  0x2000-0x20ff]
[    0.233633] pci 0000:09:00.0: supports D1 D2
[    0.233643] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233678] pci 0000:09:00.0: PME# disabled
[    0.234002] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.234016] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.234029] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.234128] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.234261] pci 0000:00:1e.0: PCI bridge to [bus 11-11] (subtractive decode)
[    0.234287] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.234297] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.234308] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.234318] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.234329] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.234339] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.234349] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.234360] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.234410] pci_bus 0000:00: on NUMA node 0
[    0.234426] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.234702] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.234851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.234988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.235136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.235270] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.235703] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.235727] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4420e88), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.235766]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.235964] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.235986] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4420e88), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.236044]  pci0000:00: ACPI _OSC request failed (AE_ALREADY_EXISTS), returned control mask: 0x1d
[    0.236052] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.249492] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.249678] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.249842] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.250005] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.250178] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.250364] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.250552] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.250728] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.251105] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.251136] vgaarb: loaded
[    0.251142] vgaarb: bridge control possible 0000:00:02.0
[    0.251546] i2c-core: driver [aat2870] using legacy suspend method
[    0.251554] i2c-core: driver [aat2870] using legacy resume method
[    0.251815] SCSI subsystem initialized
[    0.252015] libata version 3.00 loaded.
[    0.252167] usbcore: registered new interface driver usbfs
[    0.252207] usbcore: registered new interface driver hub
[    0.252304] usbcore: registered new device driver usb
[    0.252635] PCI: Using ACPI for IRQ routing
[    0.253180] PCI: pci_cache_line_size set to 64 bytes
[    0.253372] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.253382] reserve RAM buffer: 000000007f5b0000 - 000000007fffffff 
[    0.253698] NetLabel: Initializing
[    0.253705] NetLabel:  domain hash size = 128
[    0.253711] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.253740] NetLabel:  unlabeled traffic allowed by default
[    0.253916] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.253931] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.253946] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.264192] Switching to clocksource hpet
[    0.288072] AppArmor: AppArmor Filesystem Enabled
[    0.288146] pnp: PnP ACPI init
[    0.288201] ACPI: bus type pnp registered
[    0.290439] pnp 00:00: [bus 00-3f]
[    0.290451] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.290460] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.290469] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.290478] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.290486] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.290496] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.290505] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.290514] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.290523] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.290533] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.290542] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.290552] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.290561] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.290571] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.290580] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.290593] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.290602] pnp 00:00: [mem 0x80000000-0xf7ffffff window]
[    0.290611] pnp 00:00: [io  0x0d00-0xfdff window]
[    0.290619] pnp 00:00: [mem 0x00000000 window]
[    0.290627] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.290809] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.291527] pnp 00:01: [io  0x0010-0x001f]
[    0.291537] pnp 00:01: [io  0x0024-0x0025]
[    0.291545] pnp 00:01: [io  0x0028-0x0029]
[    0.291552] pnp 00:01: [io  0x002c-0x002d]
[    0.291559] pnp 00:01: [io  0x0030-0x0031]
[    0.291567] pnp 00:01: [io  0x0034-0x0035]
[    0.291574] pnp 00:01: [io  0x0038-0x0039]
[    0.291582] pnp 00:01: [io  0x003c-0x003d]
[    0.291589] pnp 00:01: [io  0x0072-0x0077]
[    0.291596] pnp 00:01: [io  0x0080]
[    0.291603] pnp 00:01: [io  0x0090-0x009f]
[    0.291611] pnp 00:01: [io  0x00a4-0x00a5]
[    0.291618] pnp 00:01: [io  0x00a8-0x00a9]
[    0.291626] pnp 00:01: [io  0x00ac-0x00ad]
[    0.291633] pnp 00:01: [io  0x00b0-0x00b5]
[    0.291640] pnp 00:01: [io  0x00b8-0x00b9]
[    0.291648] pnp 00:01: [io  0x00bc-0x00bd]
[    0.291655] pnp 00:01: [io  0x0800-0x080f]
[    0.291663] pnp 00:01: [io  0x1000-0x107f]
[    0.291670] pnp 00:01: [io  0x1180-0x11bf]
[    0.291678] pnp 00:01: [io  0x002e-0x002f]
[    0.291685] pnp 00:01: [io  0x04d0-0x04d1]
[    0.291693] pnp 00:01: [io  0xfe00]
[    0.291700] pnp 00:01: [io  0x164e-0x174c]
[    0.291708] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.291716] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.291724] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.291732] pnp 00:01: [mem 0xfef00000-0xfeffffff]
[    0.291965] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.291976] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.291986] system 00:01: [io  0x1180-0x11bf] has been reserved
[    0.291996] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.292043] system 00:01: [io  0xfe00] has been reserved
[    0.292053] system 00:01: [io  0x164e-0x174c] has been reserved
[    0.292064] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.292075] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.292085] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.292096] system 00:01: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.292109] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.292152] pnp 00:02: [io  0x0000-0x000f]
[    0.292160] pnp 00:02: [io  0x0081-0x008f]
[    0.292168] pnp 00:02: [io  0x00c0-0x00df]
[    0.292176] pnp 00:02: [dma 4]
[    0.292296] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.292335] pnp 00:03: [io  0x00f0-0x00fe]
[    0.292359] pnp 00:03: [irq 13]
[    0.292463] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.292582] pnp 00:04: [io  0x0070-0x0071]
[    0.292600] pnp 00:04: [irq 8]
[    0.292708] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.292742] pnp 00:05: [io  0x0061]
[    0.292850] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.292932] pnp 00:06: [io  0x0060]
[    0.292940] pnp 00:06: [io  0x0064]
[    0.292956] pnp 00:06: [irq 1]
[    0.293072] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.293195] pnp 00:07: [irq 12]
[    0.293320] pnp 00:07: Plug and Play ACPI device, IDs ETD0b00 SYN0002 PNP0f13 (active)
[    0.293740] pnp 00:08: [mem 0xff800000-0xffffffff]
[    0.293859] pnp 00:08: Plug and Play ACPI device, IDs INT0800 (active)
[    0.294374] pnp: PnP ACPI: found 9 devices
[    0.294382] ACPI: ACPI bus type pnp unregistered
[    0.294391] PnPBIOS: Disabled by ACPI PNP
[    0.335989] PCI: max bus depth: 1 pci_try_num: 2
[    0.336139] pci 0000:00:1c.3: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.336155] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.336170] pci 0000:00:1c.3: BAR 13: assigned [io  0x3000-0x3fff]
[    0.336183] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.336196] pci 0000:00:1c.1: BAR 14: assigned [mem 0x80600000-0x807fffff]
[    0.336210] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80800000-0x809fffff 64bit pref]
[    0.336223] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.336236] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.336249] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.336260] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.336270] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.336284] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.336297] pci 0000:00:1c.0:   bridge window [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.336313] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.336323] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.336337] pci 0000:00:1c.1:   bridge window [mem 0x80600000-0x807fffff]
[    0.336350] pci 0000:00:1c.1:   bridge window [mem 0x80800000-0x809fffff 64bit pref]
[    0.336367] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.336376] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.336391] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.336403] pci 0000:00:1c.2:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.336419] pci 0000:00:1c.3: PCI bridge to [bus 0b-0b]
[    0.336429] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.336443] pci 0000:00:1c.3:   bridge window [mem 0x80000000-0x801fffff]
[    0.336456] pci 0000:00:1c.3:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.336473] pci 0000:00:1e.0: PCI bridge to [bus 11-11]
[    0.336546] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.336561] pci 0000:00:1c.0: setting latency timer to 64
[    0.336578] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.336603] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.336617] pci 0000:00:1c.1: setting latency timer to 64
[    0.336647] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.336659] pci 0000:00:1c.2: setting latency timer to 64
[    0.336676] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.336698] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.336713] pci 0000:00:1c.3: setting latency timer to 64
[    0.336731] pci 0000:00:1e.0: setting latency timer to 64
[    0.336743] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.336752] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.336761] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.336770] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.336779] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.336788] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.336797] pci_bus 0000:00: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.336806] pci_bus 0000:00: resource 11 [io  0x0d00-0xfdff]
[    0.336815] pci_bus 0000:05: resource 0 [io  0x5000-0x5fff]
[    0.336824] pci_bus 0000:05: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.336833] pci_bus 0000:05: resource 2 [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.336843] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.336851] pci_bus 0000:07: resource 1 [mem 0x80600000-0x807fffff]
[    0.336861] pci_bus 0000:07: resource 2 [mem 0x80800000-0x809fffff 64bit pref]
[    0.336870] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.336879] pci_bus 0000:09: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.336888] pci_bus 0000:09: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.336897] pci_bus 0000:0b: resource 0 [io  0x3000-0x3fff]
[    0.336906] pci_bus 0000:0b: resource 1 [mem 0x80000000-0x801fffff]
[    0.336915] pci_bus 0000:0b: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.336925] pci_bus 0000:11: resource 4 [io  0x0000-0x0cf7]
[    0.336934] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[    0.336943] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.336953] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.336962] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.336972] pci_bus 0000:11: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.336982] pci_bus 0000:11: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.336992] pci_bus 0000:11: resource 11 [io  0x0d00-0xfdff]
[    0.337104] NET: Registered protocol family 2
[    0.337294] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.337972] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.339104] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.339623] TCP: Hash tables configured (established 131072 bind 65536)
[    0.339633] TCP reno registered
[    0.339648] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.339672] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.339905] NET: Registered protocol family 1
[    0.339951] pci 0000:00:02.0: Boot video device
[    0.340087] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.340118] pci 0000:00:1d.0: PCI INT A disabled
[    0.340141] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.340169] pci 0000:00:1d.1: PCI INT B disabled
[    0.340189] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.340218] pci 0000:00:1d.2: PCI INT C disabled
[    0.340239] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.340268] pci 0000:00:1d.3: PCI INT D disabled
[    0.340295] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.340344] pci 0000:00:1d.7: PCI INT A disabled
[    0.340403] PCI: CLS 32 bytes, default 64
[    0.340415] Simple Boot Flag at 0x36 set to 0x1
[    0.341509] audit: initializing netlink socket (disabled)
[    0.341534] type=2000 audit(1335722644.336:1): initialized
[    0.404284] highmem bounce pool size: 64 pages
[    0.404301] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.420444] VFS: Disk quotas dquot_6.5.2
[    0.420648] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.422576] fuse init (API version 7.17)
[    0.422918] msgmni has been set to 1678
[    0.424105] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.424209] io scheduler noop registered
[    0.424216] io scheduler deadline registered
[    0.424242] io scheduler cfq registered (default)
[    0.424601] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.424695] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.424853] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.424937] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.425090] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.425174] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.425326] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.425410] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.425659] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.425742] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.425955] intel_idle: MWAIT substates: 0x20220
[    0.425973] intel_idle: v0.4 model 0x1C
[    0.425979] intel_idle: lapic_timer_reliable_states 0x2
[    0.425987] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.426444] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.427448] ACPI: AC Adapter [ADP1] (on-line)
[    0.427947] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.428162] ACPI: Lid Switch [LID0]
[    0.428328] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.428343] ACPI: Power Button [PWRB]
[    0.428492] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.428505] ACPI: Sleep Button [SLPB]
[    0.428655] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.428668] ACPI: Power Button [PWRF]
[    0.440122] thermal LNXTHERM:00: registered as thermal_zone0
[    0.440132] ACPI: Thermal Zone [TZ00] (59 C)
[    0.440219] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.440255] ACPI: Battery Slot [BAT1] (battery present)
[    0.440347] ERST: Table is not found!
[    0.440353] GHES: HEST is not enabled!
[    0.440587] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.441822] isapnp: Scanning for PnP cards...
[    0.472320] ACPI: Battery Slot [BAT1] (battery present)
[    0.796526] isapnp: No Plug & Play device found
[    0.931836] Freeing initrd memory: 13784k freed
[    0.984867] Linux agpgart interface v0.103
[    0.985041] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    0.985243] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.985517] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.985780] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.989866] brd: module loaded
[    0.992086] loop: module loaded
[    0.992353] ahci 0000:00:1f.2: version 3.0
[    0.992381] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.992472] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    0.992595] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.992604] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    0.992614] ahci 0000:00:1f.2: setting latency timer to 64
[    0.993996] scsi0 : ahci
[    0.994249] scsi1 : ahci
[    0.994456] scsi2 : ahci
[    0.994657] scsi3 : ahci
[    0.994976] ata1: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604500 irq 44
[    0.994985] ata2: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604580 irq 44
[    0.994993] ata3: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604600 irq 44
[    0.995000] ata4: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604680 irq 44
[    0.996201] Fixed MDIO Bus: probed
[    0.996255] tun: Universal TUN/TAP device driver, 1.6
[    0.996260] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.996420] PPP generic driver version 2.4.2
[    0.996675] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.996723] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.996759] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.996767] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.996895] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.996929] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.996947] ehci_hcd 0000:00:1d.7: debug port 1
[    1.000853] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.000895] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0604000
[    1.016068] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.016411] hub 1-0:1.0: USB hub found
[    1.016423] hub 1-0:1.0: 8 ports detected
[    1.016602] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.016637] uhci_hcd: USB Universal Host Controller Interface driver
[    1.016685] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.016702] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.016709] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.016843] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.016884] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.017205] hub 2-0:1.0: USB hub found
[    1.017217] hub 2-0:1.0: 2 ports detected
[    1.017365] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.017381] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.017388] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.017511] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.017569] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.017895] hub 3-0:1.0: USB hub found
[    1.017907] hub 3-0:1.0: 2 ports detected
[    1.018048] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.018068] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.018075] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.018196] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.018252] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.018587] hub 4-0:1.0: USB hub found
[    1.018598] hub 4-0:1.0: 2 ports detected
[    1.018741] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.018756] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.018764] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.018901] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.018958] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.019289] hub 5-0:1.0: USB hub found
[    1.019301] hub 5-0:1.0: 2 ports detected
[    1.019574] usbcore: registered new interface driver libusual
[    1.019671] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE1] at 0x60,0x64 irq 1,12
[    1.022171] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.022190] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.022565] mousedev: PS/2 mouse device common for all mice
[    1.023345] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.023397] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.023559] device-mapper: uevent: version 1.0.3
[    1.023761] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.023848] EISA: Probing bus 0 at eisa.0
[    1.023853] EISA: Cannot allocate resource for mainboard
[    1.023859] Cannot allocate resource for EISA slot 1
[    1.023863] Cannot allocate resource for EISA slot 2
[    1.023868] Cannot allocate resource for EISA slot 3
[    1.023872] Cannot allocate resource for EISA slot 4
[    1.023877] Cannot allocate resource for EISA slot 5
[    1.023881] Cannot allocate resource for EISA slot 6
[    1.023886] Cannot allocate resource for EISA slot 7
[    1.023890] Cannot allocate resource for EISA slot 8
[    1.023895] EISA: Detected 0 cards.
[    1.023911] cpufreq-nforce2: No nForce2 chipset.
[    1.024095] cpuidle: using governor ladder
[    1.024330] cpuidle: using governor menu
[    1.024335] EFI Variables Facility v0.08 2004-May-17
[    1.024928] TCP cubic registered
[    1.025213] NET: Registered protocol family 10
[    1.026662] NET: Registered protocol family 17
[    1.026705] Registering the dns_resolver key type
[    1.026750] Using IPI No-Shortcut mode
[    1.027115] PM: Hibernation image not present or could not be loaded.
[    1.027140] registered taskstats version 1
[    1.047935]   Magic number: 8:589:90
[    1.048162] rtc_cmos 00:04: setting system clock to 2012-04-29 18:04:07 UTC (1335722647)
[    1.048955] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.048961] EDD information not available.
[    1.055703] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.312119] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.312158] ata2: SATA link down (SStatus 0 SControl 300)
[    1.312196] ata4: SATA link down (SStatus 0 SControl 300)
[    1.312234] ata3: SATA link down (SStatus 0 SControl 300)
[    1.312623] ata1.00: ATA-7: Kingston SSDNow V Series 64GB, B090522a, max UDMA/133
[    1.312637] ata1.00: 125045424 sectors, multi 1: LBA 
[    1.313222] ata1.00: configured for UDMA/133
[    1.313549] scsi 0:0:0:0: Direct-Access     ATA      Kingston SSDNow  B090 PQ: 0 ANSI: 5
[    1.313902] sd 0:0:0:0: [sda] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
[    1.314046] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.314157] sd 0:0:0:0: [sda] Write Protect is off
[    1.314168] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.314278] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.315984]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    1.317401] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.317468] Freeing unused kernel memory: 712k freed
[    1.317983] Write protecting the kernel text: 5628k
[    1.318074] Write protecting the kernel read-only data: 2324k
[    1.328084] usb 1-3: new high-speed USB device number 2 using ehci_hcd
[    1.358820] udevd[92]: starting version 175
[    1.462358] hub 1-3:1.0: USB hub found
[    1.462723] hub 1-3:1.0: 4 ports detected
[    1.576144] usb 1-8: new high-speed USB device number 3 using ehci_hcd
[    1.628593] sky2: driver version 1.30
[    1.628820] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.628976] sky2 0000:09:00.0: setting latency timer to 64
[    1.629238] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    1.630356] sky2 0000:09:00.0: irq 45 for MSI/MSI-X
[    1.633843] sky2 0000:09:00.0: eth0: addr e8:11:32:16:17:e7
[    1.784362] usb 1-3.1: new low-speed USB device number 4 using ehci_hcd
[    1.894974] input: eGalax Inc. Touch as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input5
[    1.895395] input: eGalax Inc. Touch as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input6
[    1.895773] generic-usb 0003:0EEF:0001.0001: input,hidraw0: USB HID v1.12 Pointer [eGalax Inc. Touch] on usb-0000:00:1d.7-3.1/input0
[    1.895833] usbcore: registered new interface driver usbhid
[    1.895841] usbhid: USB HID core driver
[    6.683093] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    7.327113] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.356986] udevd[302]: starting version 175
[    7.377452] Adding 2134012k swap on /dev/sda7.  Priority:-1 extents:1 across:2134012k SS
[    7.444113] lp: driver loaded but no devices found
[    7.515809] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    7.820491] cfg80211: Calling CRDA to update world regulatory domain
[    7.952277] [drm] Initialized drm 1.1.0 20060810
[    8.299006] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.299022] i915 0000:00:02.0: setting latency timer to 64
[    8.422022] ath9k 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.422046] ath9k 0000:05:00.0: setting latency timer to 64
[    8.475896] type=1400 audit(1335740654.921:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=524 comm="apparmor_parser"
[    8.481511] type=1400 audit(1335740654.929:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=524 comm="apparmor_parser"
[    8.482400] type=1400 audit(1335740654.929:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=524 comm="apparmor_parser"
[    8.490191] ppdev: user-space parallel port driver
[    8.516853] Bluetooth: Core ver 2.16
[    8.516934] NET: Registered protocol family 31
[    8.516942] Bluetooth: HCI device and connection manager initialized
[    8.516951] Bluetooth: HCI socket layer initialized
[    8.516958] Bluetooth: L2CAP socket layer initialized
[    8.516976] Bluetooth: SCO socket layer initialized
[    8.519913] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    8.519931] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.519938] [drm] Driver supports precise vblank timestamp query.
[    8.530783] ath: EEPROM regdomain: 0x65
[    8.530792] ath: EEPROM indicates we should expect a direct regpair map
[    8.530803] ath: Country alpha2 being used: 00
[    8.530810] ath: Regpair used: 0x65
[    8.530820] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    8.530831] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530839] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    8.530849] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530858] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    8.530868] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530876] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    8.530887] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530895] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    8.530906] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530914] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    8.530925] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530934] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    8.530945] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530953] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    8.530964] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530972] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    8.530983] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.530991] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    8.531002] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.531011] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    8.531022] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.531030] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    8.531041] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.531049] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    8.531060] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    8.531068] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    8.553355] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    8.561839] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.561849] Bluetooth: BNEP filters: protocol multicast
[    8.585136] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    8.648518] type=1400 audit(1335740655.097:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=560 comm="apparmor_parser"
[    8.664706] type=1400 audit(1335740655.113:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=560 comm="apparmor_parser"
[    8.697734] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    8.718654] Bluetooth: RFCOMM TTY layer initialized
[    8.718671] Bluetooth: RFCOMM socket layer initialized
[    8.718678] Bluetooth: RFCOMM ver 1.11
[    8.719715] Registered led device: ath9k-phy0
[    8.719736] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8360000, irq=16
[    9.034143] Linux video capture interface: v2.00
[    9.158464] psmouse serio1: hgpk: ID: 10 00 64
[    9.187006] uvcvideo: Found UVC 1.00 device WebCam SCB-0355N (2232:1006)
[    9.187583] [drm] initialized overlay support
[    9.193363] input: WebCam SCB-0355N as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input7
[    9.193988] usbcore: registered new interface driver uvcvideo
[    9.193997] USB Video Class driver (1.1.1)
[    9.257196] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x040216)
[    9.294147] psmouse serio1: elantech: Synaptics capabilities query result 0x09, 0x14, 0x0b.
[    9.297413] fbcon: inteldrmfb (fb0) is primary device
[    9.300339] Console: switching to colour frame buffer device 128x37
[    9.300421] fb0: inteldrmfb frame buffer device
[    9.300427] drm: registered panic notifier
[    9.325994] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[    9.333570] acpi device:04: registered as cooling_device2
[    9.333884] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    9.346938] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[    9.351865] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.351994] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.353391] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    9.353466] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    9.428790] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.433416] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.446866] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input9
[    9.464479] sky2 0000:09:00.0: eth0: enabling interface
[    9.468872] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.476410] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.521901] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    9.529240] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    9.635097] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.635116] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.850568] type=1400 audit(1335740656.297:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=713 comm="apparmor_parser"
[    9.855611] type=1400 audit(1335740656.301:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=714 comm="apparmor_parser"
[    9.896604] type=1400 audit(1335740656.345:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=715 comm="apparmor_parser"
[    9.909346] type=1400 audit(1335740656.357:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=715 comm="apparmor_parser"
[    9.910268] type=1400 audit(1335740656.357:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=715 comm="apparmor_parser"
[   11.054285] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   11.054297] cfg80211: World regulatory domain updated:
[   11.054310] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.054321] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.054330] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.054339] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.054348] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.054357] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.196699] init: lxdm main process (890) killed by TERM signal
[   11.205004] init: gdm main process (907) killed by TERM signal
[   12.560446] init: plymouth-stop pre-start process (1138) terminated with status 1
[   12.569269] wlan0: authenticate with 00:06:25:fe:e6:a3 (try 1)
[   12.571525] wlan0: authenticated
[   12.572363] wlan0: associate with 00:06:25:fe:e6:a3 (try 1)
[   12.580062] wlan0: RX AssocResp from 00:06:25:fe:e6:a3 (capab=0x411 status=0 aid=1)
[   12.580073] wlan0: associated
[   12.580875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.426251] input: EETI virtual device as /devices/virtual/input/input12
[   13.428913] input: EETI virtual device as /devices/virtual/input/input13
[   16.143109] Easy slow down manager: checking for SABI support.
[   16.143322] Easy slow down manager: SABI is supported (f50d9)
[   23.528036] wlan0: no IPv6 routers present
[  130.199895] audit_printk_skb: 45 callbacks suppressed
[  130.199905] type=1400 audit(1335740776.644:27): apparmor="STATUS" operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" pid=2030 comm="apparmor_parser"
[  130.199938] type=1400 audit(1335740776.644:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=2031 comm="apparmor_parser"
[  130.210123] type=1400 audit(1335740776.656:29): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=2032 comm="apparmor_parser"
[  130.211559] type=1400 audit(1335740776.656:30): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2032 comm="apparmor_parser"
[  130.212432] type=1400 audit(1335740776.660:31): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=2032 comm="apparmor_parser"
[  130.231237] type=1400 audit(1335740776.676:32): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/mission-control-5" pid=2035 comm="apparmor_parser"
[  130.233347] type=1400 audit(1335740776.680:33): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-*" pid=2035 comm="apparmor_parser"
[  130.248477] type=1400 audit(1335740776.696:34): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=2036 comm="apparmor_parser"
[  130.250464] type=1400 audit(1335740776.696:35): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=2036 comm="apparmor_parser"
[  130.251524] type=1400 audit(1335740776.696:36): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=2033 comm="apparmor_parser"
[  130.832660] init: plymouth-stop pre-start process (2178) terminated with status 1       
``` Could someone recommend which log to review or a configuration command to test it?????
Remember it was working with "no problems" in 11.10....can I revert?? how???

---

### Post by exactiv on 2012-04-30
I'm having the same problem. Everything was working great in 11.10, now Nautilus crashes for no reason. I could be in FireFox, terminal, Libre... anything, it just randomly hangs.

Can I revert? As the OP asked, which logs should I look at?

Thanks!

---

### Post by exactiv on 2012-05-01
Anyone? Help!

---

### Post by yurx cherio on 2012-05-01
Same here. It is very bizarre. Nautilus scripts stop working as there seems to be a problem with highlighting and selecting items (files & folders). Those triangle icons before the folder names are changing sizes from medium to small and back. File names become un-readble (seems like the font color becomes the same as text background color).

Altogether seems to be quite unstable.

P.S. I uploaded a screenshot. It shows the bizarre triangles and a file highlighting issue.

---

### Post by kylea on 2012-05-03
My Nautilus also crashes - however I you create a new user it works fine. So there is something in the hidden files (I guess) that is up setting Nautilus).

I'll do some experimenting and see what is going on.

---

### Post by kylea on 2012-05-03
I copied over a few . files from a new account (did a chown) and got my account working - partially - but there are still indicators crashing - weather, Ubuntu One and others - I'll try moving the key data files to another account and then see if that account works.

This might need some re-installs of some components

---

### Post by rocketscove on 2012-05-04
Update:
I have been updating with update manager, each and every change coming in...There appears to be some improvement, but I still periodically get bug report on nautilus when I use lxde. My problem seems to be related to the touchscreen and touchpad, and I do not know how to troubleshoot this....

I have recalibrated the egalax touchscreen using the egalaxu calibrator, forced loading of the eGTouchD daemon via startup applications, and deleted the eGTouchD commands from /etc/gdm/init and rc.local.

It is marginally usable...Now the touchscreen cursor position drops down and to the right about 1/3 of the screen when the touchpad is used, and right click with the touchscreen stylus comes up displaced from the cursor.

Looks like a simple calibration/sync problem....please someone guide me to trouble shoot or correct...

thanks, dan

---

