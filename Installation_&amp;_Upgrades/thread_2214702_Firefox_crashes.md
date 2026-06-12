---
title: "Firefox crashes"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by xxx6 on 2014-04-02
Hi!

as title says...firefox with 10 tabs open...what a CRASH! about 10 min tty1 tty2 tty3 no response!! I had to turn off button!!!!
[B]
dmesg[/B]

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-18-generic (buildd@akateko) (gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu6) ) #38-Ubuntu SMP Mon Mar 17 21:40:06 UTC 2014 (Ubuntu 3.13.0-18.38-generic 3.13.6)
[    0.000000] Command line: BOOT_IMAGE=/@/boot/vmlinuz-3.13.0-18-generic root=UUID=8e77dc19-dd54-4193-83f9-598030b0dc28 ro rootflags=subvol=@ quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040200000-0x0000000075abefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000075abf000-0x0000000075ebefff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000075ebf000-0x0000000075fbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000075fbf000-0x0000000075ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000075fff000-0x0000000075ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000076000000-0x000000007e9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001005fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Acer Aspire E1-431/EA40_HC, BIOS V1.17 04/25/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x100600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 076000000 mask FFE000000 uncachable
[    0.000000]   2 base 078000000 mask FF8000000 uncachable
[    0.000000]   3 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   4 base 100000000 mask FFF800000 write-back
[    0.000000]   5 base 100600000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x76000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100400000-0x1005fffff]
[    0.000000]  [mem 0x100400000-0x1005fffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1003fffff]
[    0.000000]  [mem 0x100000000-0x1003fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x3fffffff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x40200000-0x75abefff]
[    0.000000]  [mem 0x40200000-0x759fffff] page 2M
[    0.000000]  [mem 0x75a00000-0x75abefff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x75fff000-0x75ffffff]
[    0.000000]  [mem 0x75fff000-0x75ffffff] page 4k
[    0.000000] RAMDISK: [mem 0x35b86000-0x36dbafff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 0000000075ffe210 00009C (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 0000000075ffb000 00010C (v05 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: DSDT 0000000075fed000 00ADB8 (v01 ACRSYS ACRPRDCT 00000000 1025 00040000)
[    0.000000] ACPI: FACS 0000000075fbb000 000040
[    0.000000] ACPI: UEFI 0000000075ffd000 000236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASF! 0000000075ffc000 0000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: HPET 0000000075ffa000 000038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: APIC 0000000075ff9000 00008C (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MCFG 0000000075ff8000 00003C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SLIC 0000000075fec000 000176 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: WDAT 0000000075feb000 000224 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 0000000075fe9000 001068 (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
[    0.000000] ACPI: BOOT 0000000075fe7000 000028 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASPT 0000000075fe2000 000034 (v07 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MSDM 0000000075fe1000 000055 (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: FPDT 0000000075fdf000 000044 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 0000000075fde000 00081E (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 0000000075fdd000 000A92 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000001005fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x1005fffff]
[    0.000000]   NODE_DATA [mem 0x1005fa000-0x1005fefff]
[    0.000000]  [ffffea0000000000-ffffea00041fffff] PMD -> [ffff880073600000-ffff8800755fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x1005fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x3fffffff]
[    0.000000]   node   0: [mem 0x40200000-0x75abefff]
[    0.000000]   node   0: [mem 0x75fff000-0x75ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x1005fffff]
[    0.000000] On node 0 totalpages: 482396
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 156 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7451 pages used for memmap
[    0.000000]   DMA32 zone: 476864 pages, LIFO batch:31
[    0.000000]   Normal zone: 24 pages used for memmap
[    0.000000]   Normal zone: 1536 pages, LIFO batch:0
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40000000-0x401fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x75abf000-0x75ebefff]
[    0.000000] PM: Registered nosave memory: [mem 0x75ebf000-0x75fbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x75fbf000-0x75ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x76000000-0x7e9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ea00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
[    0.000000] e820: [mem 0x7ea00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880100200000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 474701
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/@/boot/vmlinuz-3.13.0-18-generic root=UUID=8e77dc19-dd54-4193-83f9-598030b0dc28 ro rootflags=subvol=@ quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1794024K/1929584K available (7320K kernel code, 1138K rwdata, 3384K rodata, 1336K init, 1440K bss, 135560K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1696.139 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3392.27 BogoMIPS (lpj=6784556)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000059] AppArmor: AppArmor initialized
[    0.000060] Yama: becoming mindful.
[    0.000337] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000975] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.001235] Mount-cache hash table entries: 256
[    0.001466] Initializing cgroup subsys memory
[    0.001473] Initializing cgroup subsys devices
[    0.001475] Initializing cgroup subsys freezer
[    0.001478] Initializing cgroup subsys blkio
[    0.001479] Initializing cgroup subsys perf_event
[    0.001482] Initializing cgroup subsys hugetlb
[    0.001509] CPU: Physical Processor ID: 0
[    0.001510] CPU: Processor Core ID: 0
[    0.001516] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.001516] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.001520] mce: CPU supports 7 MCE banks
[    0.001534] CPU0: Thermal monitoring enabled (TM1)
[    0.001547] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.001547] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.001547] tlb_flushall_shift: 5
[    0.001705] Freeing SMP alternatives memory: 28K (ffffffff81e6c000 - ffffffff81e73000)
[    0.003728] ACPI: Core revision 20131115
[    0.010609] ACPI: All ACPI Tables successfully acquired
[    0.021805] ftrace: allocating 28370 entries in 111 pages
[    0.041971] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081677] smpboot: CPU0: Intel(R) Celeron(R) CPU B820 @ 1.70GHz (fam: 06, model: 2a, stepping: 07)
[    0.081687] TSC deadline timer enabled
[    0.084822] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.084832] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.084835] ... version:                3
[    0.084837] ... bit width:              48
[    0.084838] ... generic registers:      8
[    0.084840] ... value mask:             0000ffffffffffff
[    0.084841] ... max period:             0000ffffffffffff
[    0.084843] ... fixed-purpose events:   3
[    0.084844] ... event mask:             00000007000000ff
[    0.087034] x86: Booting SMP configuration:
[    0.087038] .... node  #0, CPUs:      #1
[    0.100212] x86: Booted up 1 node, 2 CPUs
[    0.100216] smpboot: Total of 2 processors activated (6784.55 BogoMIPS)
[    0.100345] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.101969] devtmpfs: initialized
[    0.105120] EVM: security.selinux
[    0.105122] EVM: security.SMACK64
[    0.105124] EVM: security.ima
[    0.105125] EVM: security.capability
[    0.105201] PM: Registering ACPI NVS region [mem 0x75ebf000-0x75fbefff] (1048576 bytes)
[    0.106341] pinctrl core: initialized pinctrl subsystem
[    0.106426] regulator-dummy: no parameters
[    0.106461] RTC time: 14:01:30, date: 04/02/14
[    0.106508] NET: Registered protocol family 16
[    0.106646] cpuidle: using governor ladder
[    0.106648] cpuidle: using governor menu
[    0.106706] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.106708] ACPI: bus type PCI registered
[    0.106710] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.106786] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.106789] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.138626] PCI: Using configuration type 1 for base access
[    0.138759] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.138760] mtrr: probably your BIOS does not setup all CPUs.
[    0.138762] mtrr: corrected configuration.
[    0.139712] bio: create slab <bio-0> at 0
[    0.139905] ACPI: Added _OSI(Module Device)
[    0.139908] ACPI: Added _OSI(Processor Device)
[    0.139910] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.139912] ACPI: Added _OSI(Processor Aggregator Device)
[    0.144341] ACPI: Executed 1 blocks of module-level executable AML code
[    0.149870] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.150693] ACPI: SSDT 0000000075e29018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.151265] ACPI: Dynamic OEM Table Load:
[    0.151268] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.154151] ACPI: SSDT 0000000075e2aa98 000303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.154758] ACPI: Dynamic OEM Table Load:
[    0.154761] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.157978] ACPI: SSDT 0000000075e28d98 000119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    0.158539] ACPI: Dynamic OEM Table Load:
[    0.158542] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    0.166015] ACPI: Interpreter enabled
[    0.166024] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.166030] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.166049] ACPI: (supports S0 S3 S4 S5)
[    0.166051] ACPI: Using IOAPIC for interrupt routing
[    0.166086] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.166277] ACPI: No dock devices found.
[    0.173329] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.173336] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.173424] \_SB_.PCI0:_OSC invalid UUID
[    0.173426] _OSC request data:1 1f 0 
[    0.173431] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.174311] PCI host bridge to bus 0000:00
[    0.174315] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.174319] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.174321] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.174324] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.174326] pci_bus 0000:00: root bus resource [mem 0x7ea00000-0xfeafffff]
[    0.174337] pci 0000:00:00.0: [8086:0104] type 00 class 0x060000
[    0.174449] pci 0000:00:02.0: [8086:0106] type 00 class 0x030000
[    0.174465] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x903fffff 64bit]
[    0.174473] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.174480] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    0.174630] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.174666] pci 0000:00:16.0: reg 0x10: [mem 0x90704000-0x9070400f 64bit]
[    0.174784] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.174904] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.175181] pci 0000:00:1a.0: reg 0x10: [mem 0x90709000-0x907093ff]
[    0.176719] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.176804] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.176857] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.176885] pci 0000:00:1b.0: reg 0x10: [mem 0x90700000-0x90703fff 64bit]
[    0.177011] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.177079] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.177122] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.177262] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.177332] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.177377] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    0.177516] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.177588] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.177638] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
[    0.177781] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.177859] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    0.177907] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.178175] pci 0000:00:1d.0: reg 0x10: [mem 0x90708000-0x907083ff]
[    0.179710] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.179791] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.179836] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.180088] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.180126] pci 0000:00:1f.2: reg 0x10: [io  0x3088-0x308f]
[    0.180141] pci 0000:00:1f.2: reg 0x14: [io  0x3094-0x3097]
[    0.180156] pci 0000:00:1f.2: reg 0x18: [io  0x3080-0x3087]
[    0.180170] pci 0000:00:1f.2: reg 0x1c: [io  0x3090-0x3093]
[    0.180185] pci 0000:00:1f.2: reg 0x20: [io  0x3060-0x307f]
[    0.180199] pci 0000:00:1f.2: reg 0x24: [mem 0x90707000-0x907077ff]
[    0.180296] pci 0000:00:1f.2: PME# supported from D3hot
[    0.180394] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.180422] pci 0000:00:1f.3: reg 0x10: [mem 0x90705000-0x907050ff 64bit]
[    0.180460] pci 0000:00:1f.3: reg 0x20: [io  0x3040-0x305f]
[    0.180669] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.180812] pci 0000:04:00.0: [10ec:5289] type 00 class 0xff0000
[    0.180840] pci 0000:04:00.0: reg 0x10: [mem 0x90600000-0x9060ffff]
[    0.181050] pci 0000:04:00.0: supports D1 D2
[    0.181053] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.181104] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.181163] pci 0000:04:00.2: [10ec:8168] type 00 class 0x020000
[    0.181190] pci 0000:04:00.2: reg 0x10: [io  0x2000-0x20ff]
[    0.181236] pci 0000:04:00.2: reg 0x18: [mem 0x90404000-0x90404fff 64bit pref]
[    0.181265] pci 0000:04:00.2: reg 0x20: [mem 0x90400000-0x90403fff 64bit pref]
[    0.181392] pci 0000:04:00.2: supports D1 D2
[    0.181394] pci 0000:04:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185886] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.185897] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.185907] pci 0000:00:1c.2:   bridge window [mem 0x90600000-0x906fffff]
[    0.185922] pci 0000:00:1c.2:   bridge window [mem 0x90400000-0x904fffff 64bit pref]
[    0.186124] pci 0000:09:00.0: [14e4:4727] type 00 class 0x028000
[    0.186163] pci 0000:09:00.0: reg 0x10: [mem 0x90500000-0x90503fff 64bit]
[    0.186366] pci 0000:09:00.0: supports D1 D2
[    0.186368] pci 0000:09:00.0: PME# supported from D0 D3hot D3cold
[    0.186420] pci 0000:09:00.0: System wakeup disabled by ACPI
[    0.193918] pci 0000:00:1c.7: PCI bridge to [bus 09]
[    0.193934] pci 0000:00:1c.7:   bridge window [mem 0x90500000-0x905fffff]
[    0.194624] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.194698] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.194767] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.194836] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.194904] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.194973] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.195042] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.195109] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.195515] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.195524] ACPI: \_SB_.PCI0: notify handler is installed
[    0.195597] Found 1 acpi root devices
[    0.195662] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.195786] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.195791] vgaarb: loaded
[    0.195792] vgaarb: bridge control possible 0000:00:02.0
[    0.195989] SCSI subsystem initialized
[    0.196053] libata version 3.00 loaded.
[    0.196080] ACPI: bus type USB registered
[    0.196102] usbcore: registered new interface driver usbfs
[    0.196113] usbcore: registered new interface driver hub
[    0.196146] usbcore: registered new device driver usb
[    0.196268] PCI: Using ACPI for IRQ routing
[    0.204265] PCI: pci_cache_line_size set to 64 bytes
[    0.204364] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.204366] e820: reserve RAM buffer [mem 0x75abf000-0x77ffffff]
[    0.204369] e820: reserve RAM buffer [mem 0x76000000-0x77ffffff]
[    0.204371] e820: reserve RAM buffer [mem 0x100600000-0x103ffffff]
[    0.204467] NetLabel: Initializing
[    0.204469] NetLabel:  domain hash size = 128
[    0.204470] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204486] NetLabel:  unlabeled traffic allowed by default
[    0.204572] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.204580] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.206621] Switched to clocksource hpet
[    0.212916] AppArmor: AppArmor Filesystem Enabled
[    0.212952] pnp: PnP ACPI init
[    0.212967] ACPI: bus type PNP registered
[    0.213017] pnp 00:00: [dma 4]
[    0.213043] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.213068] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.213193] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.213230] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.213286] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.213290] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.213292] system 00:04: [io  0xffff] has been reserved
[    0.213295] system 00:04: [io  0xffff] has been reserved
[    0.213298] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.213301] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.213304] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.213306] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.213310] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.213339] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.213398] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.213401] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.213431] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.213462] pnp 00:08: Plug and Play ACPI device, IDs AUI2010 PNP0f13 (active)
[    0.213623] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.213626] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.213629] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.213632] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.213635] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.213637] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.213640] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.213643] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.213646] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.213649] system 00:09: [mem 0x7ea00000-0x7ea00fff] has been reserved
[    0.213652] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.213963] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    0.213966] system 00:0a: [mem 0x40000000-0x401fffff] has been reserved
[    0.213970] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.214014] pnp: PnP ACPI: found 11 devices
[    0.214016] ACPI: bus type PNP unregistered
[    0.220721] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.220743] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.220748] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.220756] pci 0000:00:1c.2:   bridge window [mem 0x90600000-0x906fffff]
[    0.220763] pci 0000:00:1c.2:   bridge window [mem 0x90400000-0x904fffff 64bit pref]
[    0.220773] pci 0000:00:1c.7: PCI bridge to [bus 09]
[    0.220781] pci 0000:00:1c.7:   bridge window [mem 0x90500000-0x905fffff]
[    0.220796] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.220799] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.220801] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.220804] pci_bus 0000:00: resource 7 [mem 0x7ea00000-0xfeafffff]
[    0.220807] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.220809] pci_bus 0000:04: resource 1 [mem 0x90600000-0x906fffff]
[    0.220812] pci_bus 0000:04: resource 2 [mem 0x90400000-0x904fffff 64bit pref]
[    0.220814] pci_bus 0000:09: resource 1 [mem 0x90500000-0x905fffff]
[    0.220851] NET: Registered protocol family 2
[    0.221035] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.221095] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.221146] TCP: Hash tables configured (established 16384 bind 16384)
[    0.221170] TCP: reno registered
[    0.221178] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.221190] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.221260] NET: Registered protocol family 1
[    0.221274] pci 0000:00:02.0: Boot video device
[    0.250891] PCI: CLS 64 bytes, default 64
[    0.250958] Trying to unpack rootfs image as initramfs...
[    0.668168] Freeing initrd memory: 18644K (ffff880035b86000 - ffff880036dbb000)
[    0.668175] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.668179] software IO TLB [mem 0x6f600000-0x73600000] (64MB) mapped at [ffff88006f600000-ffff8800735fffff]
[    0.668263] Simple Boot Flag at 0x44 set to 0x1
[    0.668438] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x26
[    0.668448] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x26
[    0.668507] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.668509] Scanning for low memory corruption every 60 seconds
[    0.668848] Initialise system trusted keyring
[    0.668914] audit: initializing netlink socket (disabled)
[    0.668927] type=2000 audit(1396447290.652:1): initialized
[    0.705038] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.706268] zbud: loaded
[    0.706448] VFS: Disk quotas dquot_6.5.2
[    0.706500] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.707024] fuse init (API version 7.22)
[    0.707115] msgmni has been set to 3540
[    0.707186] Key type big_key registered
[    0.707584] Key type asymmetric registered
[    0.707587] Asymmetric key parser 'x509' registered
[    0.707622] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.707658] io scheduler noop registered
[    0.707661] io scheduler deadline registered (default)
[    0.707687] io scheduler cfq registered
[    0.708229] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.708248] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.708289] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.708291] vesafb: scrolling: redraw
[    0.708293] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.708837] vesafb: framebuffer at 0x80000000, mapped to 0xffffc90010400000, using 4160k, total 4160k
[    0.807310] Console: switching to colour frame buffer device 170x48
[    0.905431] fb0: VESA VGA frame buffer device
[    0.905464] intel_idle: MWAIT substates: 0x120
[    0.905467] intel_idle: v0.4 model 0x2A
[    0.905468] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.905531] ipmi message handler version 39.2
[    0.905729] ACPI: AC Adapter [ACAD] (on-line)
[    0.905916] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.905921] ACPI: Power Button [PWRB]
[    0.905958] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.905961] ACPI: Sleep Button [SLPB]
[    0.906004] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.906023] ACPI: Lid Switch [LID]
[    0.906061] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.906065] ACPI: Power Button [PWRF]
[    0.906448] thermal LNXTHERM:00: registered as thermal_zone0
[    0.906450] ACPI: Thermal Zone [THRM] (56 C)
[    0.906476] GHES: HEST is not enabled!
[    0.906559] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.907271] ACPI: Battery Slot [BAT1] (battery present)
[    0.907939] Linux agpgart interface v0.103
[    0.909388] brd: module loaded
[    0.910168] loop: module loaded
[    0.910547] libphy: Fixed MDIO Bus: probed
[    0.910644] tun: Universal TUN/TAP device driver, 1.6
[    0.910646] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.910690] PPP generic driver version 2.4.2
[    0.910733] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.910737] ehci-pci: EHCI PCI platform driver
[    0.910895] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.910902] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.910921] ehci-pci 0000:00:1a.0: debug port 2
[    0.914848] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.914869] ehci-pci 0000:00:1a.0: irq 16, io mem 0x90709000
[    0.922965] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.923025] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.923028] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.923030] usb usb1: Product: EHCI Host Controller
[    0.923033] usb usb1: Manufacturer: Linux 3.13.0-18-generic ehci_hcd
[    0.923035] usb usb1: SerialNumber: 0000:00:1a.0
[    0.923200] hub 1-0:1.0: USB hub found
[    0.923211] hub 1-0:1.0: 2 ports detected
[    0.923439] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.923445] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.923463] ehci-pci 0000:00:1d.0: debug port 2
[    0.927366] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.927385] ehci-pci 0000:00:1d.0: irq 23, io mem 0x90708000
[    0.938991] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.939091] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.939097] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.939102] usb usb2: Product: EHCI Host Controller
[    0.939115] usb usb2: Manufacturer: Linux 3.13.0-18-generic ehci_hcd
[    0.939117] usb usb2: SerialNumber: 0000:00:1d.0
[    0.939238] hub 2-0:1.0: USB hub found
[    0.939248] hub 2-0:1.0: 2 ports detected
[    0.939343] ehci-platform: EHCI generic platform driver
[    0.939352] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.939354] ohci-pci: OHCI PCI platform driver
[    0.939363] ohci-platform: OHCI generic platform driver
[    0.939371] uhci_hcd: USB Universal Host Controller Interface driver
[    0.939434] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.940800] i8042: Detected active multiplexing controller, rev 1.1
[    0.941460] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.941467] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.941494] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.941513] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.941534] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.941719] mousedev: PS/2 mouse device common for all mice
[    0.942074] rtc_cmos 00:05: RTC can wake from S4
[    0.942207] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.942239] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.942305] device-mapper: uevent: version 1.0.3
[    0.942368] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.942377] ledtrig-cpu: registered to indicate activity on CPUs
[    0.942494] TCP: cubic registered
[    0.942596] NET: Registered protocol family 10
[    0.942798] NET: Registered protocol family 17
[    0.942808] Key type dns_resolver registered
[    0.943076] Loading compiled-in X.509 certificates
[    0.944377] Loaded X.509 cert 'Magrathea: Glacier signing key: 50a51f016878d62c084f13ed047626639f5a1089'
[    0.944392] registered taskstats version 1
[    0.947321] Key type trusted registered
[    0.949943] Key type encrypted registered
[    0.952528] AppArmor: AppArmor sha1 policy hashing enabled
[    0.952533] IMA: No TPM chip found, activating TPM-bypass!
[    0.953009]   Magic number: 10:581:29
[    0.953106] rtc_cmos 00:05: setting system clock to 2014-04-02 14:01:31 UTC (1396447291)
[    0.953556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.953559] EDD information not available.
[    0.953611] PM: Hibernation image not present or could not be loaded.
[    0.955437] Freeing unused kernel memory: 1336K (ffffffff81d1e000 - ffffffff81e6c000)
[    0.955440] Write protecting the kernel read-only data: 12288k
[    0.958034] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.958280] Freeing unused kernel memory: 860K (ffff880001729000 - ffff880001800000)
[    0.960488] Freeing unused kernel memory: 712K (ffff880001b4e000 - ffff880001c00000)
[    0.977204] systemd-udevd[110]: starting version 204
[    1.006668] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.006681] r8169 0000:04:00.2: can't disable ASPM; OS doesn't have ASPM control
[    1.006954] r8169 0000:04:00.2: irq 40 for MSI/MSI-X
[    1.012457] r8169 0000:04:00.2 eth0: RTL8411 at 0xffffc9000031c000, 04:7d:7b:cf:41:c8, XID 08800800 IRQ 40
[    1.012462] r8169 0000:04:00.2 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.012632] rtsx_pci 0000:04:00.0: irq 41 for MSI/MSI-X
[    1.012650] rtsx_pci 0000:04:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 41
[    1.029773] ahci 0000:00:1f.2: version 3.0
[    1.030280] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.043051] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x21 impl SATA mode
[    1.043057] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.051878] scsi0 : ahci
[    1.054002] scsi1 : ahci
[    1.054118] scsi2 : ahci
[    1.055892] scsi3 : ahci
[    1.056068] scsi4 : ahci
[    1.057807] scsi5 : ahci
[    1.057860] ata1: SATA max UDMA/133 abar m2048@0x90707000 port 0x90707100 irq 42
[    1.057862] ata2: DUMMY
[    1.057864] ata3: DUMMY
[    1.057866] ata4: DUMMY
[    1.057867] ata5: DUMMY
[    1.057871] ata6: SATA max UDMA/133 abar m2048@0x90707000 port 0x90707380 irq 42
[    1.235257] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.367875] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.367879] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.368183] hub 1-1:1.0: USB hub found
[    1.368260] hub 1-1:1.0: 6 ports detected
[    1.375208] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.383205] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.384750] ata6.00: ATAPI: MATSHITADVD-RAM UJ8C0, 1.00, max UDMA/133
[    1.386000] ata6.00: configured for UDMA/133
[    1.414359] ata1.00: ATA-8: TOSHIBA MK3259GSXP, GN003J, max UDMA/100
[    1.414365] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.415241] ata1.00: configured for UDMA/100
[    1.415517] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3259GS GN00 PQ: 0 ANSI: 5
[    1.415683] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.415819] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.415822] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.415871] sd 0:0:0:0: [sda] Write Protect is off
[    1.415875] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.415895] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.418188] scsi 5:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8C0    1.00 PQ: 0 ANSI: 5
[    1.422460] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.422463] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.422584] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.422698] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    1.479276] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.497116]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.497564] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.611965] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.611971] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.612296] hub 2-1:1.0: USB hub found
[    1.612365] hub 2-1:1.0: 8 ports detected
[    1.667335] tsc: Refined TSC clocksource calibration: 1696.146 MHz
[    1.683502] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    1.842281] usb 1-1.1: New USB device found, idVendor=1bcf, idProduct=2c18
[    1.842287] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.842290] usb 1-1.1: Product: HD Webcam
[    1.842292] usb 1-1.1: Manufacturer: NC.21411.00221908ACDLM0007
[    2.135517] raid6: sse2x1    4592 MB/s
[    2.203546] raid6: sse2x2    5686 MB/s
[    2.271579] raid6: sse2x4    6555 MB/s
[    2.271581] raid6: using algorithm sse2x4 (6555 MB/s)
[    2.271583] raid6: using ssse3x2 recovery algorithm
[    2.273265] xor: measuring software checksum speed
[    2.311596]    prefetch64-sse:  9490.000 MB/sec
[    2.351613]    generic_sse:  8692.000 MB/sec
[    2.351615] xor: using function: prefetch64-sse (9490.000 MB/sec)
[    2.370750] bio: create slab <bio-1> at 1
[    2.371445] Btrfs loaded
[    2.667863] Switched to clocksource tsc
[    2.780337] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2202 /dev/sda6
[    2.788085] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2202 /dev/disk/by-uuid/8e77dc19-dd54-4193-83f9-598030b0dc28
[    2.788624] btrfs: disk space caching is enabled
[    3.494152] random: init urandom read with 120 bits of entropy available
[    3.779189] random: nonblocking pool is initialized
[   16.509173] Adding 2110460k swap on /dev/sda5.  Priority:-1 extents:1 across:2110460k FS
[   16.660224] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.734763] btrfs: disk space caching is enabled
[   16.776888] BTRFS debug (device sda6): unlinked 2 orphans
[   16.779931] systemd-udevd[319]: starting version 204
[   16.841184] lp: driver loaded but no devices found
[   16.870787] [drm] Initialized drm 1.1.0 20060810
[   16.884218] wmi: Mapper loaded
[   16.918358] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2202 /dev/sda6
[   16.927660] [drm] Memory usable by graphics device = 2048M
[   16.927667] checking generic (80000000 410000) vs hw (80000000 10000000)
[   16.927669] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   16.927692] Console: switching to colour dummy device 80x25
[   16.978490] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   16.978525] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   16.978552] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   16.978605] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   16.992051] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   16.992064] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   16.992066] [drm] Driver supports precise vblank timestamp query.
[   16.992140] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.000564] type=1400 audit(1396468907.534:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=381 comm="apparmor_parser"
[   17.000573] type=1400 audit(1396468907.534:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=381 comm="apparmor_parser"
[   17.000579] type=1400 audit(1396468907.534:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=381 comm="apparmor_parser"
[   17.001183] type=1400 audit(1396468907.534:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=381 comm="apparmor_parser"
[   17.001190] type=1400 audit(1396468907.534:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=381 comm="apparmor_parser"
[   17.001486] type=1400 audit(1396468907.534:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=381 comm="apparmor_parser"
[   17.027785] [drm] Wrong MCH_SSKPD value: 0x16040307
[   17.027790] [drm] This can cause pipe underruns and display issues.
[   17.027791] [drm] Please upgrade your BIOS to fix this.
[   17.030270] bcma: bus0: Bus registered
[   17.044657] fbcon: inteldrmfb (fb0) is primary device
[   17.275027] Linux video capture interface: v2.00
[   17.283552] uvcvideo: Found UVC 1.00 device HD Webcam (1bcf:2c18)
[   17.292791] input: HD Webcam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input11
[   17.292944] usbcore: registered new interface driver uvcvideo
[   17.292945] USB Video Class driver (1.1.1)
[   17.295984] BTRFS debug (device sda6): unlinked 9 orphans
[   17.438728] psmouse serio2: alps: Unknown ALPS touchpad: E7=73 03 50, EC=73 02 02
[   17.885695] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2202 /dev/sda6
[   17.907118] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2202 /dev/sda6
[   17.942106] cfg80211: Calling CRDA to update world regulatory domain
[   17.966490] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   17.966495] b43: probe of bcma0:0 failed with error -524
[   17.966522] Broadcom 43xx driver loaded [ Features: PNL ]
[   17.980498] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 19
[   17.988136] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   17.988471] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   18.014910] Console: switching to colour frame buffer device 170x48
[   18.018421] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   18.018423] i915 0000:00:02.0: registered panic notifier
[   18.042449] cfg80211: World regulatory domain updated:
[   18.042454] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.042457] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.042460] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.042462] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.042464] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.042466] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.048789] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.049056] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input12
[   18.049328] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.049611] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   18.056993] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   18.057003] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.057008] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   18.057012] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.057014] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   18.057018] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.057020] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   18.057475] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   18.081195] SKU: Nid=0x1d sku_cfg=0x40189e2d
[   18.081199] SKU: port_connectivity=0x1
[   18.081200] SKU: enable_pcbeep=0x1
[   18.081202] SKU: check_sum=0x00000008
[   18.081203] SKU: customization=0x0000009e
[   18.081205] SKU: external_amp=0x5
[   18.081206] SKU: platform_type=0x1
[   18.081208] SKU: swap=0x0
[   18.081209] SKU: override=0x1
[   18.081795] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   18.081797]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.081799]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   18.081801]    mono: mono_out=0x0
[   18.081802]    inputs:
[   18.081804]      Internal Mic=0x19
[   18.081806]      Mic=0x18
[   18.081808] realtek: No valid SSID, checking pincfg 0x40189e2d for NID 0x1d
[   18.081810] realtek: Enabling init ASM_ID=0x9e2d CODEC_ID=10ec0269
[   18.107936] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   18.111847] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   18.112064] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   18.182441] input: PS/2 Generic Mouse as /devices/platform/i8042/serio2/input/input10
[   18.839617] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   19.324298] init: failsafe main process (621) killed by TERM signal
[   19.498075] Bluetooth: Core ver 2.17
[   19.498098] NET: Registered protocol family 31
[   19.498100] Bluetooth: HCI device and connection manager initialized
[   19.498108] Bluetooth: HCI socket layer initialized
[   19.498111] Bluetooth: L2CAP socket layer initialized
[   19.498116] Bluetooth: SCO socket layer initialized
[   19.522523] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.522528] Bluetooth: BNEP filters: protocol multicast
[   19.522536] Bluetooth: BNEP socket layer initialized
[   19.532563] type=1400 audit(1396468910.066:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=724 comm="apparmor_parser"
[   19.532573] type=1400 audit(1396468910.066:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=724 comm="apparmor_parser"
[   19.533179] type=1400 audit(1396468910.066:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=724 comm="apparmor_parser"
[   19.535165] Bluetooth: RFCOMM TTY layer initialized
[   19.535178] Bluetooth: RFCOMM socket layer initialized
[   19.535184] Bluetooth: RFCOMM ver 1.11
[   19.856222] init: cups main process (726) killed by HUP signal
[   19.856239] init: cups main process ended, respawning
[   20.130660] type=1400 audit(1396468910.662:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=798 comm="apparmor_parser"
[   20.230820] r8169 0000:04:00.2 eth0: link down
[   20.230876] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.231306] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.423143] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   20.423156] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   20.423778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.424195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```



**dmesg****.0**

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-18-generic (buildd@akateko) (gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu6) ) #38-Ubuntu SMP Mon Mar 17 21:40:06 UTC 2014 (Ubuntu 3.13.0-18.38-generic 3.13.6)
[    0.000000] Command line: BOOT_IMAGE=/@/boot/vmlinuz-3.13.0-18-generic root=UUID=8e77dc19-dd54-4193-83f9-598030b0dc28 ro rootflags=subvol=@ quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040200000-0x0000000075abefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000075abf000-0x0000000075ebefff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000075ebf000-0x0000000075fbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000075fbf000-0x0000000075ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000075fff000-0x0000000075ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000076000000-0x000000007e9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001005fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Acer Aspire E1-431/EA40_HC, BIOS V1.17 04/25/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x100600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 076000000 mask FFE000000 uncachable
[    0.000000]   2 base 078000000 mask FF8000000 uncachable
[    0.000000]   3 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   4 base 100000000 mask FFF800000 write-back
[    0.000000]   5 base 100600000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x76000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100400000-0x1005fffff]
[    0.000000]  [mem 0x100400000-0x1005fffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1003fffff]
[    0.000000]  [mem 0x100000000-0x1003fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x3fffffff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x40200000-0x75abefff]
[    0.000000]  [mem 0x40200000-0x759fffff] page 2M
[    0.000000]  [mem 0x75a00000-0x75abefff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x75fff000-0x75ffffff]
[    0.000000]  [mem 0x75fff000-0x75ffffff] page 4k
[    0.000000] RAMDISK: [mem 0x35b86000-0x36dbafff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 0000000075ffe210 00009C (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 0000000075ffb000 00010C (v05 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: DSDT 0000000075fed000 00ADB8 (v01 ACRSYS ACRPRDCT 00000000 1025 00040000)
[    0.000000] ACPI: FACS 0000000075fbb000 000040
[    0.000000] ACPI: UEFI 0000000075ffd000 000236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASF! 0000000075ffc000 0000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: HPET 0000000075ffa000 000038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: APIC 0000000075ff9000 00008C (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MCFG 0000000075ff8000 00003C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SLIC 0000000075fec000 000176 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: WDAT 0000000075feb000 000224 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 0000000075fe9000 001068 (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
[    0.000000] ACPI: BOOT 0000000075fe7000 000028 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASPT 0000000075fe2000 000034 (v07 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MSDM 0000000075fe1000 000055 (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: FPDT 0000000075fdf000 000044 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 0000000075fde000 00081E (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 0000000075fdd000 000A92 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000001005fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x1005fffff]
[    0.000000]   NODE_DATA [mem 0x1005fa000-0x1005fefff]
[    0.000000]  [ffffea0000000000-ffffea00041fffff] PMD -> [ffff880073600000-ffff8800755fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x1005fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x3fffffff]
[    0.000000]   node   0: [mem 0x40200000-0x75abefff]
[    0.000000]   node   0: [mem 0x75fff000-0x75ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x1005fffff]
[    0.000000] On node 0 totalpages: 482396
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 156 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7451 pages used for memmap
[    0.000000]   DMA32 zone: 476864 pages, LIFO batch:31
[    0.000000]   Normal zone: 24 pages used for memmap
[    0.000000]   Normal zone: 1536 pages, LIFO batch:0
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40000000-0x401fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x75abf000-0x75ebefff]
[    0.000000] PM: Registered nosave memory: [mem 0x75ebf000-0x75fbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x75fbf000-0x75ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x76000000-0x7e9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ea00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
[    0.000000] e820: [mem 0x7ea00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880100200000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 474701
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/@/boot/vmlinuz-3.13.0-18-generic root=UUID=8e77dc19-dd54-4193-83f9-598030b0dc28 ro rootflags=subvol=@ quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1794024K/1929584K available (7320K kernel code, 1138K rwdata, 3384K rodata, 1336K init, 1440K bss, 135560K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1696.206 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3392.41 BogoMIPS (lpj=6784824)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000036] Security Framework initialized
[    0.000059] AppArmor: AppArmor initialized
[    0.000061] Yama: becoming mindful.
[    0.000337] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000973] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.001234] Mount-cache hash table entries: 256
[    0.001467] Initializing cgroup subsys memory
[    0.001475] Initializing cgroup subsys devices
[    0.001477] Initializing cgroup subsys freezer
[    0.001479] Initializing cgroup subsys blkio
[    0.001480] Initializing cgroup subsys perf_event
[    0.001483] Initializing cgroup subsys hugetlb
[    0.001510] CPU: Physical Processor ID: 0
[    0.001511] CPU: Processor Core ID: 0
[    0.001517] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.001517] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.001521] mce: CPU supports 7 MCE banks
[    0.001535] CPU0: Thermal monitoring enabled (TM1)
[    0.001548] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.001548] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.001548] tlb_flushall_shift: 5
[    0.001707] Freeing SMP alternatives memory: 28K (ffffffff81e6c000 - ffffffff81e73000)
[    0.003731] ACPI: Core revision 20131115
[    0.010613] ACPI: All ACPI Tables successfully acquired
[    0.021713] ftrace: allocating 28370 entries in 111 pages
[    0.041888] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081596] smpboot: CPU0: Intel(R) Celeron(R) CPU B820 @ 1.70GHz (fam: 06, model: 2a, stepping: 07)
[    0.081606] TSC deadline timer enabled
[    0.084742] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.084752] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.084755] ... version:                3
[    0.084757] ... bit width:              48
[    0.084758] ... generic registers:      8
[    0.084760] ... value mask:             0000ffffffffffff
[    0.084761] ... max period:             0000ffffffffffff
[    0.084763] ... fixed-purpose events:   3
[    0.084764] ... event mask:             00000007000000ff
[    0.086953] x86: Booting SMP configuration:
[    0.086957] .... node  #0, CPUs:      #1
[    0.100134] x86: Booted up 1 node, 2 CPUs
[    0.100139] smpboot: Total of 2 processors activated (6784.82 BogoMIPS)
[    0.100269] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.101896] devtmpfs: initialized
[    0.105046] EVM: security.selinux
[    0.105049] EVM: security.SMACK64
[    0.105050] EVM: security.ima
[    0.105052] EVM: security.capability
[    0.105126] PM: Registering ACPI NVS region [mem 0x75ebf000-0x75fbefff] (1048576 bytes)
[    0.106269] pinctrl core: initialized pinctrl subsystem
[    0.106354] regulator-dummy: no parameters
[    0.106389] RTC time: 13:20:12, date: 04/02/14
[    0.106436] NET: Registered protocol family 16
[    0.106574] cpuidle: using governor ladder
[    0.106576] cpuidle: using governor menu
[    0.106633] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.106636] ACPI: bus type PCI registered
[    0.106638] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.106713] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.106717] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.138598] PCI: Using configuration type 1 for base access
[    0.138731] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.138733] mtrr: probably your BIOS does not setup all CPUs.
[    0.138734] mtrr: corrected configuration.
[    0.139687] bio: create slab <bio-0> at 0
[    0.139880] ACPI: Added _OSI(Module Device)
[    0.139882] ACPI: Added _OSI(Processor Device)
[    0.139884] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.139886] ACPI: Added _OSI(Processor Aggregator Device)
[    0.144311] ACPI: Executed 1 blocks of module-level executable AML code
[    0.149794] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.150613] ACPI: SSDT 0000000075e29018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.151186] ACPI: Dynamic OEM Table Load:
[    0.151189] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.154072] ACPI: SSDT 0000000075e2aa98 000303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.154679] ACPI: Dynamic OEM Table Load:
[    0.154681] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.157900] ACPI: SSDT 0000000075e28d98 000119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    0.158461] ACPI: Dynamic OEM Table Load:
[    0.158464] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    0.165936] ACPI: Interpreter enabled
[    0.165945] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.165952] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.165970] ACPI: (supports S0 S3 S4 S5)
[    0.165973] ACPI: Using IOAPIC for interrupt routing
[    0.166008] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.166198] ACPI: No dock devices found.
[    0.173247] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.173254] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.173342] \_SB_.PCI0:_OSC invalid UUID
[    0.173344] _OSC request data:1 1f 0 
[    0.173349] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.174231] PCI host bridge to bus 0000:00
[    0.174236] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.174238] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.174241] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.174244] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.174246] pci_bus 0000:00: root bus resource [mem 0x7ea00000-0xfeafffff]
[    0.174257] pci 0000:00:00.0: [8086:0104] type 00 class 0x060000
[    0.174370] pci 0000:00:02.0: [8086:0106] type 00 class 0x030000
[    0.174385] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x903fffff 64bit]
[    0.174394] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.174400] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    0.174552] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.174588] pci 0000:00:16.0: reg 0x10: [mem 0x90704000-0x9070400f 64bit]
[    0.174704] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.174826] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.175101] pci 0000:00:1a.0: reg 0x10: [mem 0x90709000-0x907093ff]
[    0.176636] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.176722] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.176774] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.176804] pci 0000:00:1b.0: reg 0x10: [mem 0x90700000-0x90703fff 64bit]
[    0.176937] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.177005] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.177048] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.177189] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.177257] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.177301] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    0.177439] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.177508] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.177558] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
[    0.177701] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.177778] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    0.177824] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.178091] pci 0000:00:1d.0: reg 0x10: [mem 0x90708000-0x907083ff]
[    0.179626] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.179709] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.179753] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.180004] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.180041] pci 0000:00:1f.2: reg 0x10: [io  0x3088-0x308f]
[    0.180055] pci 0000:00:1f.2: reg 0x14: [io  0x3094-0x3097]
[    0.180069] pci 0000:00:1f.2: reg 0x18: [io  0x3080-0x3087]
[    0.180084] pci 0000:00:1f.2: reg 0x1c: [io  0x3090-0x3093]
[    0.180097] pci 0000:00:1f.2: reg 0x20: [io  0x3060-0x307f]
[    0.180113] pci 0000:00:1f.2: reg 0x24: [mem 0x90707000-0x907077ff]
[    0.180207] pci 0000:00:1f.2: PME# supported from D3hot
[    0.180305] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.180335] pci 0000:00:1f.3: reg 0x10: [mem 0x90705000-0x907050ff 64bit]
[    0.180373] pci 0000:00:1f.3: reg 0x20: [io  0x3040-0x305f]
[    0.180582] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.180727] pci 0000:04:00.0: [10ec:5289] type 00 class 0xff0000
[    0.180755] pci 0000:04:00.0: reg 0x10: [mem 0x90600000-0x9060ffff]
[    0.180967] pci 0000:04:00.0: supports D1 D2
[    0.180970] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.181021] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.181080] pci 0000:04:00.2: [10ec:8168] type 00 class 0x020000
[    0.181107] pci 0000:04:00.2: reg 0x10: [io  0x2000-0x20ff]
[    0.181155] pci 0000:04:00.2: reg 0x18: [mem 0x90404000-0x90404fff 64bit pref]
[    0.181185] pci 0000:04:00.2: reg 0x20: [mem 0x90400000-0x90403fff 64bit pref]
[    0.181313] pci 0000:04:00.2: supports D1 D2
[    0.181316] pci 0000:04:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185811] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.185822] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.185832] pci 0000:00:1c.2:   bridge window [mem 0x90600000-0x906fffff]
[    0.185846] pci 0000:00:1c.2:   bridge window [mem 0x90400000-0x904fffff 64bit pref]
[    0.186045] pci 0000:09:00.0: [14e4:4727] type 00 class 0x028000
[    0.186083] pci 0000:09:00.0: reg 0x10: [mem 0x90500000-0x90503fff 64bit]
[    0.186287] pci 0000:09:00.0: supports D1 D2
[    0.186289] pci 0000:09:00.0: PME# supported from D0 D3hot D3cold
[    0.186341] pci 0000:09:00.0: System wakeup disabled by ACPI
[    0.193842] pci 0000:00:1c.7: PCI bridge to [bus 09]
[    0.193857] pci 0000:00:1c.7:   bridge window [mem 0x90500000-0x905fffff]
[    0.194549] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.194622] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.194692] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.194761] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.194829] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.194899] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.194967] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.195036] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.195442] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.195452] ACPI: \_SB_.PCI0: notify handler is installed
[    0.195525] Found 1 acpi root devices
[    0.195590] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.195714] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.195719] vgaarb: loaded
[    0.195720] vgaarb: bridge control possible 0000:00:02.0
[    0.195916] SCSI subsystem initialized
[    0.195980] libata version 3.00 loaded.
[    0.196007] ACPI: bus type USB registered
[    0.196029] usbcore: registered new interface driver usbfs
[    0.196040] usbcore: registered new interface driver hub
[    0.196073] usbcore: registered new device driver usb
[    0.196193] PCI: Using ACPI for IRQ routing
[    0.204192] PCI: pci_cache_line_size set to 64 bytes
[    0.204291] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.204293] e820: reserve RAM buffer [mem 0x75abf000-0x77ffffff]
[    0.204296] e820: reserve RAM buffer [mem 0x76000000-0x77ffffff]
[    0.204298] e820: reserve RAM buffer [mem 0x100600000-0x103ffffff]
[    0.204394] NetLabel: Initializing
[    0.204396] NetLabel:  domain hash size = 128
[    0.204397] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204413] NetLabel:  unlabeled traffic allowed by default
[    0.204499] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.204507] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.206548] Switched to clocksource hpet
[    0.212843] AppArmor: AppArmor Filesystem Enabled
[    0.212877] pnp: PnP ACPI init
[    0.212892] ACPI: bus type PNP registered
[    0.212943] pnp 00:00: [dma 4]
[    0.212970] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.212994] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.213118] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.213155] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.213211] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.213215] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.213218] system 00:04: [io  0xffff] has been reserved
[    0.213220] system 00:04: [io  0xffff] has been reserved
[    0.213223] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.213226] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.213229] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.213231] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.213235] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.213265] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.213324] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.213327] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.213357] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.213388] pnp 00:08: Plug and Play ACPI device, IDs AUI2010 PNP0f13 (active)
[    0.213550] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.213554] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.213556] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.213559] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.213562] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.213565] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.213567] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.213570] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.213573] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.213576] system 00:09: [mem 0x7ea00000-0x7ea00fff] has been reserved
[    0.213579] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.213894] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    0.213897] system 00:0a: [mem 0x40000000-0x401fffff] has been reserved
[    0.213900] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.213944] pnp: PnP ACPI: found 11 devices
[    0.213946] ACPI: bus type PNP unregistered
[    0.220649] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.220670] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.220675] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.220684] pci 0000:00:1c.2:   bridge window [mem 0x90600000-0x906fffff]
[    0.220690] pci 0000:00:1c.2:   bridge window [mem 0x90400000-0x904fffff 64bit pref]
[    0.220700] pci 0000:00:1c.7: PCI bridge to [bus 09]
[    0.220709] pci 0000:00:1c.7:   bridge window [mem 0x90500000-0x905fffff]
[    0.220724] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.220727] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.220729] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.220732] pci_bus 0000:00: resource 7 [mem 0x7ea00000-0xfeafffff]
[    0.220735] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.220737] pci_bus 0000:04: resource 1 [mem 0x90600000-0x906fffff]
[    0.220740] pci_bus 0000:04: resource 2 [mem 0x90400000-0x904fffff 64bit pref]
[    0.220742] pci_bus 0000:09: resource 1 [mem 0x90500000-0x905fffff]
[    0.220778] NET: Registered protocol family 2
[    0.220960] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.221020] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.221072] TCP: Hash tables configured (established 16384 bind 16384)
[    0.221096] TCP: reno registered
[    0.221104] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.221117] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.221188] NET: Registered protocol family 1
[    0.221202] pci 0000:00:02.0: Boot video device
[    0.250817] PCI: CLS 64 bytes, default 64
[    0.250884] Trying to unpack rootfs image as initramfs...
[    0.668087] Freeing initrd memory: 18644K (ffff880035b86000 - ffff880036dbb000)
[    0.668094] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.668097] software IO TLB [mem 0x6f600000-0x73600000] (64MB) mapped at [ffff88006f600000-ffff8800735fffff]
[    0.668181] Simple Boot Flag at 0x44 set to 0x1
[    0.668355] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x26
[    0.668365] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x26
[    0.668424] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.668426] Scanning for low memory corruption every 60 seconds
[    0.668765] Initialise system trusted keyring
[    0.668823] audit: initializing netlink socket (disabled)
[    0.668836] type=2000 audit(1396444812.652:1): initialized
[    0.705210] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.706440] zbud: loaded
[    0.706621] VFS: Disk quotas dquot_6.5.2
[    0.706673] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.707199] fuse init (API version 7.22)
[    0.707290] msgmni has been set to 3540
[    0.707359] Key type big_key registered
[    0.707753] Key type asymmetric registered
[    0.707756] Asymmetric key parser 'x509' registered
[    0.707791] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.707826] io scheduler noop registered
[    0.707828] io scheduler deadline registered (default)
[    0.707854] io scheduler cfq registered
[    0.708393] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.708409] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.708453] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.708454] vesafb: scrolling: redraw
[    0.708457] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.709001] vesafb: framebuffer at 0x80000000, mapped to 0xffffc90010400000, using 4160k, total 4160k
[    0.807476] Console: switching to colour frame buffer device 170x48
[    0.905594] fb0: VESA VGA frame buffer device
[    0.905627] intel_idle: MWAIT substates: 0x120
[    0.905630] intel_idle: v0.4 model 0x2A
[    0.905632] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.905695] ipmi message handler version 39.2
[    0.905894] ACPI: AC Adapter [ACAD] (on-line)
[    0.905965] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.905970] ACPI: Power Button [PWRB]
[    0.906007] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.906010] ACPI: Sleep Button [SLPB]
[    0.906053] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.906074] ACPI: Lid Switch [LID]
[    0.906112] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.906115] ACPI: Power Button [PWRF]
[    0.906574] thermal LNXTHERM:00: registered as thermal_zone0
[    0.906577] ACPI: Thermal Zone [THRM] (47 C)
[    0.906605] GHES: HEST is not enabled!
[    0.906692] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.907446] ACPI: Battery Slot [BAT1] (battery present)
[    0.908912] Linux agpgart interface v0.103
[    0.910346] brd: module loaded
[    0.911199] loop: module loaded
[    0.911584] libphy: Fixed MDIO Bus: probed
[    0.911682] tun: Universal TUN/TAP device driver, 1.6
[    0.911684] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.911744] PPP generic driver version 2.4.2
[    0.911812] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.911816] ehci-pci: EHCI PCI platform driver
[    0.911973] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.911980] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.911999] ehci-pci 0000:00:1a.0: debug port 2
[    0.915908] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.915936] ehci-pci 0000:00:1a.0: irq 16, io mem 0x90709000
[    0.926907] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.927034] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.927037] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.927039] usb usb1: Product: EHCI Host Controller
[    0.927042] usb usb1: Manufacturer: Linux 3.13.0-18-generic ehci_hcd
[    0.927044] usb usb1: SerialNumber: 0000:00:1a.0
[    0.927200] hub 1-0:1.0: USB hub found
[    0.927210] hub 1-0:1.0: 2 ports detected
[    0.927435] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.927440] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.927458] ehci-pci 0000:00:1d.0: debug port 2
[    0.931356] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.931383] ehci-pci 0000:00:1d.0: irq 23, io mem 0x90708000
[    0.942926] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.943039] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.943042] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.943045] usb usb2: Product: EHCI Host Controller
[    0.943047] usb usb2: Manufacturer: Linux 3.13.0-18-generic ehci_hcd
[    0.943049] usb usb2: SerialNumber: 0000:00:1d.0
[    0.943191] hub 2-0:1.0: USB hub found
[    0.943201] hub 2-0:1.0: 2 ports detected
[    0.943293] ehci-platform: EHCI generic platform driver
[    0.943302] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.943304] ohci-pci: OHCI PCI platform driver
[    0.943313] ohci-platform: OHCI generic platform driver
[    0.943319] uhci_hcd: USB Universal Host Controller Interface driver
[    0.943385] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.944709] i8042: Detected active multiplexing controller, rev 1.1
[    0.945738] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.945744] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.945769] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.945792] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.945815] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.945985] mousedev: PS/2 mouse device common for all mice
[    0.946280] rtc_cmos 00:05: RTC can wake from S4
[    0.946415] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.946446] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.946512] device-mapper: uevent: version 1.0.3
[    0.946576] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.946587] ledtrig-cpu: registered to indicate activity on CPUs
[    0.946703] TCP: cubic registered
[    0.946802] NET: Registered protocol family 10
[    0.947029] NET: Registered protocol family 17
[    0.947046] Key type dns_resolver registered
[    0.947346] Loading compiled-in X.509 certificates
[    0.948659] Loaded X.509 cert 'Magrathea: Glacier signing key: 50a51f016878d62c084f13ed047626639f5a1089'
[    0.948673] registered taskstats version 1
[    0.951645] Key type trusted registered
[    0.954219] Key type encrypted registered
[    0.956767] AppArmor: AppArmor sha1 policy hashing enabled
[    0.956771] IMA: No TPM chip found, activating TPM-bypass!
[    0.957245]   Magic number: 10:784:330
[    0.957271] tty tty51: hash matches
[    0.957342] rtc_cmos 00:05: setting system clock to 2014-04-02 13:20:13 UTC (1396444813)
[    0.957785] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.957787] EDD information not available.
[    0.957839] PM: Hibernation image not present or could not be loaded.
[    0.959653] Freeing unused kernel memory: 1336K (ffffffff81d1e000 - ffffffff81e6c000)
[    0.959656] Write protecting the kernel read-only data: 12288k
[    0.962164] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.962569] Freeing unused kernel memory: 860K (ffff880001729000 - ffff880001800000)
[    0.964779] Freeing unused kernel memory: 712K (ffff880001b4e000 - ffff880001c00000)
[    0.981660] systemd-udevd[110]: starting version 204
[    1.023511] rtsx_pci 0000:04:00.0: irq 40 for MSI/MSI-X
[    1.023531] rtsx_pci 0000:04:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 40
[    1.027674] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.027687] r8169 0000:04:00.2: can't disable ASPM; OS doesn't have ASPM control
[    1.028315] r8169 0000:04:00.2: irq 41 for MSI/MSI-X
[    1.028633] r8169 0000:04:00.2 eth0: RTL8411 at 0xffffc9000031c000, 04:7d:7b:cf:41:c8, XID 08800800 IRQ 41
[    1.028637] r8169 0000:04:00.2 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.034191] ahci 0000:00:1f.2: version 3.0
[    1.034371] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.047760] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x21 impl SATA mode
[    1.047766] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.057886] scsi0 : ahci
[    1.060067] scsi1 : ahci
[    1.060150] scsi2 : ahci
[    1.060211] scsi3 : ahci
[    1.060274] scsi4 : ahci
[    1.060334] scsi5 : ahci
[    1.060376] ata1: SATA max UDMA/133 abar m2048@0x90707000 port 0x90707100 irq 42
[    1.060378] ata2: DUMMY
[    1.060380] ata3: DUMMY
[    1.060381] ata4: DUMMY
[    1.060383] ata5: DUMMY
[    1.060386] ata6: SATA max UDMA/133 abar m2048@0x90707000 port 0x90707380 irq 42
[    1.239189] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.371855] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.371858] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.372119] hub 1-1:1.0: USB hub found
[    1.372205] hub 1-1:1.0: 6 ports detected
[    1.379140] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.379177] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.380718] ata6.00: ATAPI: MATSHITADVD-RAM UJ8C0, 1.00, max UDMA/133
[    1.381928] ata6.00: configured for UDMA/133
[    1.433284] ata1.00: ATA-8: TOSHIBA MK3259GSXP, GN003J, max UDMA/100
[    1.433291] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.434164] ata1.00: configured for UDMA/100
[    1.434459] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3259GS GN00 PQ: 0 ANSI: 5
[    1.434609] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.434612] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.434621] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.434720] sd 0:0:0:0: [sda] Write Protect is off
[    1.434724] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.434754] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.437282] scsi 5:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8C0    1.00 PQ: 0 ANSI: 5
[    1.441409] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.441411] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.441512] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.441567] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    1.483161] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.516027]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.516678] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.615948] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.615954] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.616276] hub 2-1:1.0: USB hub found
[    1.616515] hub 2-1:1.0: 8 ports detected
[    1.667256] tsc: Refined TSC clocksource calibration: 1696.146 MHz
[    1.687461] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    1.846471] usb 1-1.1: New USB device found, idVendor=1bcf, idProduct=2c18
[    1.846477] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.846479] usb 1-1.1: Product: HD Webcam
[    1.846482] usb 1-1.1: Manufacturer: NC.21411.00221908ACDLM0007
[    2.155453] raid6: sse2x1    4593 MB/s
[    2.223482] raid6: sse2x2    5685 MB/s
[    2.291517] raid6: sse2x4    6553 MB/s
[    2.291519] raid6: using algorithm sse2x4 (6553 MB/s)
[    2.291521] raid6: using ssse3x2 recovery algorithm
[    2.293197] xor: measuring software checksum speed
[    2.331532]    prefetch64-sse:  9378.000 MB/sec
[    2.371550]    generic_sse:  8626.000 MB/sec
[    2.371552] xor: using function: prefetch64-sse (9378.000 MB/sec)
[    2.390707] bio: create slab <bio-1> at 1
[    2.391368] Btrfs loaded
[    2.667952] Switched to clocksource tsc
[    2.810396] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2142 /dev/sda6
[    2.818113] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2142 /dev/disk/by-uuid/8e77dc19-dd54-4193-83f9-598030b0dc28
[    2.818601] btrfs: disk space caching is enabled
[    3.435397] random: init urandom read with 123 bits of entropy available
[    3.634485] random: nonblocking pool is initialized
[   16.901548] Adding 2110460k swap on /dev/sda5.  Priority:-1 extents:1 across:2110460k FS
[   16.909205] btrfs: disk space caching is enabled
[   17.067464] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.121981] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2142 /dev/sda6
[   17.135168] systemd-udevd[335]: starting version 204
[   17.218045] lp: driver loaded but no devices found
[   17.221456] wmi: Mapper loaded
[   17.296599] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   17.296609] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.296614] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   17.296618] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.296620] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   17.296624] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.296626] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.297559] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   17.297593] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   17.297621] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   17.297674] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   17.305405] type=1400 audit(1396466429.833:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=384 comm="apparmor_parser"
[   17.305414] type=1400 audit(1396466429.833:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=384 comm="apparmor_parser"
[   17.305420] type=1400 audit(1396466429.833:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=384 comm="apparmor_parser"
[   17.306020] type=1400 audit(1396466429.833:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=384 comm="apparmor_parser"
[   17.306028] type=1400 audit(1396466429.833:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=384 comm="apparmor_parser"
[   17.306344] type=1400 audit(1396466429.833:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=384 comm="apparmor_parser"
[   17.309008] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[   17.320588] bcma: bus0: Bus registered
[   17.334681] [drm] Initialized drm 1.1.0 20060810
[   17.398642] [drm] Memory usable by graphics device = 2048M
[   17.398648] checking generic (80000000 410000) vs hw (80000000 10000000)
[   17.398651] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   17.398671] Console: switching to colour dummy device 80x25
[   17.474720] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   17.474742] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   17.474744] [drm] Driver supports precise vblank timestamp query.
[   17.474818] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.507835] [drm] Wrong MCH_SSKPD value: 0x16040307
[   17.507840] [drm] This can cause pipe underruns and display issues.
[   17.507841] [drm] Please upgrade your BIOS to fix this.
[   17.531876] fbcon: inteldrmfb (fb0) is primary device
[   17.583222] Linux video capture interface: v2.00
[   17.592531] uvcvideo: Found UVC 1.00 device HD Webcam (1bcf:2c18)
[   17.601293] input: HD Webcam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input11
[   17.601449] usbcore: registered new interface driver uvcvideo
[   17.601450] USB Video Class driver (1.1.1)
[   17.614424] cfg80211: Calling CRDA to update world regulatory domain
[   17.649363] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   17.649367] b43: probe of bcma0:0 failed with error -524
[   17.649395] Broadcom 43xx driver loaded [ Features: PNL ]
[   17.663641] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 19
[   17.673025] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   17.673360] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   17.678732] cfg80211: World regulatory domain updated:
[   17.678733] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.678735] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.678737] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.678738] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.678739] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.678740] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.779106] psmouse serio2: alps: Unknown ALPS touchpad: E7=73 03 50, EC=73 02 02
[   18.526903] input: PS/2 Generic Mouse as /devices/platform/i8042/serio2/input/input10
[   18.539122] Console: switching to colour frame buffer device 170x48
[   18.542677] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   18.542678] i915 0000:00:02.0: registered panic notifier
[   18.573614] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.581305] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input14
[   18.583538] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.586100] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   18.587433] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2142 /dev/sda6
[   18.626161] SKU: Nid=0x1d sku_cfg=0x40189e2d
[   18.626166] SKU: port_connectivity=0x1
[   18.626167] SKU: enable_pcbeep=0x1
[   18.626169] SKU: check_sum=0x00000008
[   18.626170] SKU: customization=0x0000009e
[   18.626172] SKU: external_amp=0x5
[   18.626173] SKU: platform_type=0x1
[   18.626175] SKU: swap=0x0
[   18.626176] SKU: override=0x1
[   18.626766] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   18.626768]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.626770]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   18.626772]    mono: mono_out=0x0
[   18.626773]    inputs:
[   18.626775]      Internal Mic=0x19
[   18.626777]      Mic=0x18
[   18.626779] realtek: No valid SSID, checking pincfg 0x40189e2d for NID 0x1d
[   18.626782] realtek: Enabling init ASM_ID=0x9e2d CODEC_ID=10ec0269
[   18.639291] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   18.639508] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   18.639666] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   18.706828] init: failsafe main process (568) killed by TERM signal
[   18.815305] btrfs: device fsid 8e77dc19-dd54-4193-83f9-598030b0dc28 devid 1 transid 2142 /dev/sda6
[   18.839522] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   18.978649] type=1400 audit(1396466431.505:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=660 comm="apparmor_parser"
[   18.978660] type=1400 audit(1396466431.505:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=660 comm="apparmor_parser"
[   18.979671] type=1400 audit(1396466431.509:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=660 comm="apparmor_parser"
[   19.212750] init: cups main process (662) killed by HUP signal
[   19.212767] init: cups main process ended, respawning
[   19.235383] Bluetooth: Core ver 2.17
[   19.235434] NET: Registered protocol family 31
[   19.235437] Bluetooth: HCI device and connection manager initialized
[   19.235686] Bluetooth: HCI socket layer initialized
[   19.235690] Bluetooth: L2CAP socket layer initialized
[   19.235696] Bluetooth: SCO socket layer initialized
[   19.244430] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.244434] Bluetooth: BNEP filters: protocol multicast
[   19.244444] Bluetooth: BNEP socket layer initialized
[   19.251954] Bluetooth: RFCOMM TTY layer initialized
[   19.251965] Bluetooth: RFCOMM socket layer initialized
[   19.251972] Bluetooth: RFCOMM ver 1.11
[   20.138723] r8169 0000:04:00.2 eth0: link down
[   20.138779] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.139205] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.194293] type=1400 audit(1396466432.721:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=803 comm="apparmor_parser"
[   20.374547] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   20.374560] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   20.375179] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.375537] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

tia!

:x

---

### Post by xxx6 on 2014-04-02
found the culprit: microsoft word pdf!

---

### Post by xxx6 on 2014-04-02
...?...

---

### Post by QIII on 2014-04-02
Please wait 24 hours before bumping.  The Ubuntu Forums community lives around the world in every timezone and we are all here voluntarily as we have time.

This sort of impatience is more likely to be off-putting than to get you an answer.

---

### Post by xxx6 on 2014-04-03
What could have happened?

---

### Post by xxx6 on 2014-04-05
who changed the title???

---

### Post by tgalati4 on 2014-04-05
Run *firefox* in a terminal.  Keep the terminal on top so you can see it if it freezes.  Take accurate notes on the error messages and post them.  You might need to clear your cache or start with a new firefox profile.

---

### Post by mörgæs on 2014-04-06
> **xxx6 said:**
> who changed the title???

I did, trying to make it more informative and precise.

---

### Post by xxx6 on 2014-04-07
> **tgalati4 said:**
> Run *firefox* in a terminal.  Keep the terminal on top so you can see it if it freezes.  Take accurate notes on the error messages and post them.  You might need to clear your cache or start with a new firefox profile

no man! the lag was when I opened a PDF automatically from the net!

---

