---
title: "Intrepid Upgrade Slow Boot"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by castles on 2008-11-12
I upgraded to intrepid on the weekend and since then my media center has taken ages and ages to boot up. Once it boots it seems to perform fine. Any tips or suggestions would be greatly appreciated.

Attached is my bootchart.

Dmesg:
[HTML][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff80000 (usable)
[    0.000000]  BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7ff80 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37821000 - 37feffcb
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000FBCC0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FF80000, 003C (r1 A_M_I_ OEMRSDT   7000703 MSFT       97)
[    0.000000] ACPI: FACP 7FF80200, 0084 (r2 A_M_I_ OEMFACP   7000703 MSFT       97)
[    0.000000] ACPI: DSDT 7FF805C0, 8C16 (r1  A0753 A0753001        1 INTL 20060113)
[    0.000000] ACPI: FACS 7FF8E000, 0040
[    0.000000] ACPI: APIC 7FF80390, 006C (r1 A_M_I_ OEMAPIC   7000703 MSFT       97)
[    0.000000] ACPI: MCFG 7FF80400, 003C (r1 A_M_I_ OEMMCFG   7000703 MSFT       97)
[    0.000000] ACPI: OEMB 7FF8E040, 0081 (r1 A_M_I_ AMI_OEM   7000703 MSFT       97)
[    0.000000] ACPI: HPET 7FF891E0, 0038 (r1 A_M_I_ OEMHPET   7000703 MSFT       97)
[    0.000000] ACPI: OSFR 7FF89220, 00B0 (r1 A_M_I_ OEMOSFR   7000703 MSFT       97)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037821000 - 0037feffcb]          RAMDISK ==> [0037821000 - 0037feffcb]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007ff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ff80
[    0.000000] On node 0 totalpages: 524063
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292193 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519456
[    0.000000] Kernel command line: root=UUID=6a8755fa-97a1-4a97-8de0-07add93b78e6 ro quiet splash acpi=force
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2405.442 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2063176k/2096640k available (2572k kernel code, 32344k reserved, 1160k data, 424k init, 1179136k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4810.88 BogoMIPS (lpj=9621768)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017582] ACPI: Core revision 20080609
[    0.020338] ACPI: Checking initramfs for custom DSDT
[    0.304192] ENABLING IO-APIC IRQs
[    0.304359] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.345611] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.348021] APIC calibration not consistent with PM Timer: 115ms instead of 100ms
[    0.348021] APIC delta adjusted to PM-Timer: 1670453 (1937700)
[    0.348021] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4810.95 BogoMIPS (lpj=9621913)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.432562] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.432576] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.436112] Booting processor 2/2 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4810.98 BogoMIPS (lpj=9621960)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.524618] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.524631] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.528104] Booting processor 3/3 ip 6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4810.98 BogoMIPS (lpj=9621961)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.616563] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.616578] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.620038] Brought up 4 CPUs
[    0.620041] Total of 4 processors activated (19243.80 BogoMIPS).
[    0.620065] CPU0 attaching sched-domain:
[    0.620067]  domain 0: span 0-1 level MC
[    0.620069]   groups: 0 1
[    0.620077]   domain 1: span 0-3 level CPU
[    0.620079]    groups: 0-1 2-3
[    0.620084] CPU1 attaching sched-domain:
[    0.620086]  domain 0: span 0-1 level MC
[    0.620088]   groups: 1 0
[    0.620091]   domain 1: span 0-3 level CPU
[    0.620093]    groups: 0-1 2-3
[    0.620097] CPU2 attaching sched-domain:
[    0.620098]  domain 0: span 2-3 level MC
[    0.620100]   groups: 2 3
[    0.620103]   domain 1: span 0-3 level CPU
[    0.620105]    groups: 2-3 0-1
[    0.620109] CPU3 attaching sched-domain:
[    0.620110]  domain 0: span 2-3 level MC
[    0.620112]   groups: 3 2
[    0.620115]   domain 1: span 0-3 level CPU
[    0.620117]    groups: 2-3 0-1
[    0.620223] net_namespace: 840 bytes
[    0.620223] Booting paravirtualized kernel on bare hardware
[    0.620242] Time: 20:53:52  Date: 11/10/08
[    0.620263] NET: Registered protocol family 16
[    0.620279] EISA bus registered
[    0.620279] ACPI: bus type pci registered
[    0.620279] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.620279] PCI: Not using MMCONFIG.
[    0.620279] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.620279] PCI: Using configuration type 1 for base access
[    0.624266] ACPI: EC: Look up EC in DSDT
[    0.634439] ACPI: Interpreter enabled
[    0.634447] ACPI: (supports S0 S1 S3 S4 S5)
[    0.634461] ACPI: Using IOAPIC for interrupt routing
[    0.634513] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.636917] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.636919] PCI: Using MMCONFIG for extended config space
[    0.645160] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.645160] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.645160] pci 0000:00:01.0: PME# disabled
[    0.645160] PCI: 0000:00:1a.0 reg 20 io port: [b800, b81f]
[    0.645160] PCI: 0000:00:1a.1 reg 20 io port: [b880, b89f]
[    0.645160] PCI: 0000:00:1a.2 reg 20 io port: [bc00, bc1f]
[    0.645160] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f9fffc00, f9ffffff]
[    0.645160] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.645160] pci 0000:00:1a.7: PME# disabled
[    0.645160] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f9ff8000, f9ffbfff]
[    0.645160] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.645160] pci 0000:00:1b.0: PME# disabled
[    0.645160] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.645160] pci 0000:00:1c.0: PME# disabled
[    0.645160] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.645160] pci 0000:00:1c.4: PME# disabled
[    0.645160] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.645160] pci 0000:00:1c.5: PME# disabled
[    0.645160] PCI: 0000:00:1d.0 reg 20 io port: [b080, b09f]
[    0.645160] PCI: 0000:00:1d.1 reg 20 io port: [b400, b41f]
[    0.645160] PCI: 0000:00:1d.2 reg 20 io port: [b480, b49f]
[    0.645160] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f9fff800, f9fffbff]
[    0.645160] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.645160] pci 0000:00:1d.7: PME# disabled
[    0.645160] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.645160] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.645160] PCI: 0000:00:1f.2 reg 10 io port: [a000, a007]
[    0.645160] PCI: 0000:00:1f.2 reg 14 io port: [9c00, 9c03]
[    0.645160] PCI: 0000:00:1f.2 reg 18 io port: [9880, 9887]
[    0.645160] PCI: 0000:00:1f.2 reg 1c io port: [9800, 9803]
[    0.645160] PCI: 0000:00:1f.2 reg 20 io port: [9480, 948f]
[    0.645160] PCI: 0000:00:1f.2 reg 24 io port: [9400, 940f]
[    0.645160] PCI: 0000:00:1f.3 reg 10 64bit mmio: [f9fff400, f9fff4ff]
[    0.645160] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.645160] PCI: 0000:00:1f.5 reg 10 io port: [b000, b007]
[    0.645160] PCI: 0000:00:1f.5 reg 14 io port: [ac00, ac03]
[    0.645160] PCI: 0000:00:1f.5 reg 18 io port: [a880, a887]
[    0.645160] PCI: 0000:00:1f.5 reg 1c io port: [a800, a803]
[    0.645160] PCI: 0000:00:1f.5 reg 20 io port: [a480, a48f]
[    0.645160] PCI: 0000:00:1f.5 reg 24 io port: [a400, a40f]
[    0.645160] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.645160] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, dfffffff]
[    0.645169] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.645174] PCI: 0000:01:00.0 reg 24 io port: [cc00, cc7f]
[    0.645179] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe8e0000, fe8fffff]
[    0.645220] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.645223] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, fe8fffff]
[    0.645227] PCI: bridge 0000:00:01.0 64bit mmio pref: [c0000000, dfffffff]
[    0.645266] PCI: bridge 0000:00:1c.0 64bit mmio pref: [f8f00000, f8ffffff]
[    0.648113] PCI: 0000:03:00.0 reg 24 32bit mmio: [feafe000, feafffff]
[    0.648121] PCI: 0000:03:00.0 reg 30 32bit mmio: [feae0000, feaeffff]
[    0.648143] pci 0000:03:00.0: PME# supported from D3hot
[    0.648148] pci 0000:03:00.0: PME# disabled
[    0.648185] PCI: 0000:03:00.1 reg 10 io port: [dc00, dc07]
[    0.648194] PCI: 0000:03:00.1 reg 14 io port: [d880, d883]
[    0.648202] PCI: 0000:03:00.1 reg 18 io port: [d800, d807]
[    0.648210] PCI: 0000:03:00.1 reg 1c io port: [d480, d483]
[    0.648218] PCI: 0000:03:00.1 reg 20 io port: [d400, d40f]
[    0.648289] PCI: bridge 0000:00:1c.4 io port: [d000, dfff]
[    0.648293] PCI: bridge 0000:00:1c.4 32bit mmio: [fea00000, feafffff]
[    0.648344] PCI: 0000:02:00.0 reg 10 64bit mmio: [fe9c0000, fe9fffff]
[    0.648375] PCI: 0000:02:00.0 reg 30 32bit mmio: [fe9a0000, fe9bffff]
[    0.648397] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.648401] pci 0000:02:00.0: PME# disabled
[    0.648432] PCI: bridge 0000:00:1c.5 32bit mmio: [fe900000, fe9fffff]
[    0.648467] PCI: 0000:05:01.0 reg 10 32bit mmio: [febf8000, febfffff]
[    0.648548] PCI: 0000:05:02.0 reg 20 io port: [e880, e89f]
[    0.648569] pci 0000:05:02.0: supports D1
[    0.648570] pci 0000:05:02.0: supports D2
[    0.648572] pci 0000:05:02.0: PME# supported from D0 D1 D2 D3hot
[    0.648576] pci 0000:05:02.0: PME# disabled
[    0.648618] PCI: 0000:05:02.1 reg 20 io port: [ec00, ec1f]
[    0.648640] pci 0000:05:02.1: supports D1
[    0.648641] pci 0000:05:02.1: supports D2
[    0.648643] pci 0000:05:02.1: PME# supported from D0 D1 D2 D3hot
[    0.648646] pci 0000:05:02.1: PME# disabled
[    0.648671] PCI: 0000:05:02.2 reg 10 32bit mmio: [febf7c00, febf7cff]
[    0.648710] pci 0000:05:02.2: supports D1
[    0.648712] pci 0000:05:02.2: supports D2
[    0.648713] pci 0000:05:02.2: PME# supported from D0 D1 D2 D3hot
[    0.648717] pci 0000:05:02.2: PME# disabled
[    0.648749] PCI: 0000:05:03.0 reg 10 32bit mmio: [febf7000, febf77ff]
[    0.648755] PCI: 0000:05:03.0 reg 14 io port: [e800, e87f]
[    0.648792] pci 0000:05:03.0: supports D2
[    0.648793] pci 0000:05:03.0: PME# supported from D2 D3hot D3cold
[    0.648797] pci 0000:05:03.0: PME# disabled
[    0.648831] pci 0000:00:1e.0: transparent bridge
[    0.648834] PCI: bridge 0000:00:1e.0 io port: [e000, efff]
[    0.648837] PCI: bridge 0000:00:1e.0 32bit mmio: [feb00000, febfffff]
[    0.648859] bus 00 -> node 0
[    0.648865] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.649105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.649211] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.649392] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.649501] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.649620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.668148] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.668281] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.668409] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.668537] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.668665] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.668793] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.668920] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.669048] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.669107] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - DD, should be D4 [20080609]
[    0.669107] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.669107] pnp: PnP ACPI init
[    0.669107] ACPI: bus type pnp registered
[    0.672654] pnp: PnP ACPI: found 15 devices
[    0.672654] ACPI: ACPI bus type pnp unregistered
[    0.672654] PnPBIOS: Disabled by ACPI PNP
[    0.672654] PCI: Using ACPI for IRQ routing
[    0.684044] NET: Registered protocol family 8
[    0.684047] NET: Registered protocol family 20
[    0.684067] NetLabel: Initializing
[    0.684067] NetLabel:  domain hash size = 128
[    0.684067] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.684067] NetLabel:  unlabeled traffic allowed by default
[    0.684067] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.684067] hpet0: 4 64-bit timers, 14318180 Hz
[    0.685829] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.685831]    actual entries 65620
[    0.685895] AppArmor: AppArmor Filesystem Enabled
[    0.685912] ACPI: RTC can wake from S4
[    0.688039] Switched to high resolution mode on CPU 0
[    0.688606] Switched to high resolution mode on CPU 1
[    0.689176] Switched to high resolution mode on CPU 3
[    0.689249] Switched to high resolution mode on CPU 2
[    0.692046] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.692058] system 00:07: ioport range 0x290-0x297 has been reserved
[    0.692066] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.692070] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.692074] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.692078] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.692082] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.692089] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.692093] system 00:08: iomem range 0xffa00000-0xffafffff has been reserved
[    0.692096] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.692100] system 00:08: iomem range 0xffe00000-0xffefffff has been reserved
[    0.692104] system 00:08: iomem range 0xfff00000-0xfffffffe could not be reserved
[    0.692113] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.692117] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.692124] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.692132] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.692136] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.692139] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.692143] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.727425] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.727427] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.727431] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe8fffff
[    0.727434] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000dfffffff
[    0.727438] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.727440] pci 0000:00:1c.0:   IO window: disabled
[    0.727444] pci 0000:00:1c.0:   MEM window: disabled
[    0.727447] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.727453] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.727456] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.727460] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    0.727463] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.727468] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.727470] pci 0000:00:1c.5:   IO window: disabled
[    0.727474] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    0.727477] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.727483] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.727485] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.727490] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.727493] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.727503] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.727507] pci 0000:00:01.0: setting latency timer to 64
[    0.727513] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.727517] pci 0000:00:1c.0: setting latency timer to 64
[    0.727523] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.727526] pci 0000:00:1c.4: setting latency timer to 64
[    0.727532] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.727536] pci 0000:00:1c.5: setting latency timer to 64
[    0.727541] pci 0000:00:1e.0: setting latency timer to 64
[    0.727544] bus: 00 index 0 io port: [0, ffff]
[    0.727546] bus: 00 index 1 mmio: [0, ffffffff]
[    0.727548] bus: 01 index 0 io port: [c000, cfff]
[    0.727550] bus: 01 index 1 mmio: [fa000000, fe8fffff]
[    0.727551] bus: 01 index 2 mmio: [c0000000, dfffffff]
[    0.727553] bus: 01 index 3 mmio: [0, 0]
[    0.727555] bus: 04 index 0 mmio: [0, 0]
[    0.727556] bus: 04 index 1 mmio: [0, 0]
[    0.727558] bus: 04 index 2 mmio: [f8f00000, f8ffffff]
[    0.727559] bus: 04 index 3 mmio: [0, 0]
[    0.727561] bus: 03 index 0 io port: [d000, dfff]
[    0.727563] bus: 03 index 1 mmio: [fea00000, feafffff]
[    0.727565] bus: 03 index 2 mmio: [0, 0]
[    0.727566] bus: 03 index 3 mmio: [0, 0]
[    0.727568] bus: 02 index 0 mmio: [0, 0]
[    0.727569] bus: 02 index 1 mmio: [fe900000, fe9fffff]
[    0.727571] bus: 02 index 2 mmio: [0, 0]
[    0.727572] bus: 02 index 3 mmio: [0, 0]
[    0.727574] bus: 05 index 0 io port: [e000, efff]
[    0.727576] bus: 05 index 1 mmio: [feb00000, febfffff]
[    0.727577] bus: 05 index 2 mmio: [0, 0]
[    0.727579] bus: 05 index 3 io port: [0, ffff]
[    0.727581] bus: 05 index 4 mmio: [0, ffffffff]
[    0.727587] NET: Registered protocol family 2
[    0.740069] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.740275] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.740522] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.740644] TCP: Hash tables configured (established 131072 bind 65536)
[    0.740647] TCP reno registered
[    0.744087] NET: Registered protocol family 1
[    0.744199] checking if image is initramfs... it is
[    1.312862] Freeing initrd memory: 7995k freed
[    1.314664] audit: initializing netlink socket (disabled)
[    1.314682] type=2000 audit(1226350432.312:1): initialized
[    1.319636] highmem bounce pool size: 64 pages
[    1.319641] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.322527] VFS: Disk quotas dquot_6.5.1
[    1.322632] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.322752] msgmni has been set to 1743
[    1.322895] io scheduler noop registered
[    1.322899] io scheduler anticipatory registered
[    1.322902] io scheduler deadline registered
[    1.322916] io scheduler cfq registered (default)
[    1.323068] pci 0000:01:00.0: Boot video device
[    1.323245] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.323291] pcieport-driver 0000:00:01.0: found MSI capability
[    1.323315] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.323364] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.323463] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.323491] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.323519] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.323568] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.323624] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.323732] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.323773] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.323801] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.323850] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.323908] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.324009] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.324044] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.324079] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.324133] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.324192] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.324599] isapnp: Scanning for PnP cards...
[    1.677431] isapnp: No Plug & Play device found
[    1.720369] hpet_resources: 0xfed00000 is busy
[    1.720466] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.720594] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.721386] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.723969] brd: module loaded
[    1.724062] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.724234] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.724236] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.724713] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.729749] mice: PS/2 mouse device common for all mice
[    1.729902] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.729925] rtc0: alarms up to one month, y3k, hpet irqs
[    1.730123] EISA: Probing bus 0 at eisa.0
[    1.730151] EISA: Detected 0 cards.
[    1.730153] cpuidle: using governor ladder
[    1.730155] cpuidle: using governor menu
[    1.730691] TCP cubic registered
[    1.730711] Using IPI No-Shortcut mode
[    1.730942] registered taskstats version 1
[    1.731113]   Magic number: 0:244:902
[    1.731132] tty ptyvf: hash matches
[    1.731178] rtc_cmos 00:03: setting system clock to 2008-11-10 20:53:53 UTC (1226350433)
[    1.731181] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.731182] EDD information not available.
[    1.731316] Freeing unused kernel memory: 424k freed
[    1.731356] Write protecting the kernel text: 2576k
[    1.731380] Write protecting the kernel read-only data: 936k
[    1.823195] fuse init (API version 7.9)
[    1.843810] ACPI: SSDT 7FF8E0D0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[    1.844157] processor ACPI0007:00: registered as cooling_device0
[    1.844390] ACPI: SSDT 7FF8E2B0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[    1.844713] processor ACPI0007:01: registered as cooling_device1
[    1.844944] ACPI: SSDT 7FF8E400, 0143 (r1    AMI   CPU3PM        1 INTL 20060113)
[    1.845265] processor ACPI0007:02: registered as cooling_device2
[    1.845497] ACPI: SSDT 7FF8E550, 0143 (r1    AMI   CPU4PM        1 INTL 20060113)
[    1.845823] processor ACPI0007:03: registered as cooling_device3
[    1.985460] usbcore: registered new interface driver usbfs
[    1.985482] usbcore: registered new interface driver hub
[    1.985983] usbcore: registered new device driver usb
[    1.987747] USB Universal Host Controller Interface driver v3.0
[    1.987780] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.987787] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.987790] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.987822] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.987849] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    1.987949] usb usb1: configuration #1 chosen from 1 choice
[    1.987970] hub 1-0:1.0: USB hub found
[    1.987976] hub 1-0:1.0: 2 ports detected
[    2.082848] No dock devices found.
[    2.089708] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.089716] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.089720] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.089739] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.089772] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    2.089841] usb usb2: configuration #1 chosen from 1 choice
[    2.089864] hub 2-0:1.0: USB hub found
[    2.089869] hub 2-0:1.0: 2 ports detected
[    2.095505] SCSI subsystem initialized
[    2.108939] libata version 3.00 loaded.
[    2.194000] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.194010] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.194014] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.194036] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.194072] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[    2.194150] usb usb3: configuration #1 chosen from 1 choice
[    2.194171] hub 3-0:1.0: USB hub found
[    2.194176] hub 3-0:1.0: 2 ports detected
[    2.297778] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.297792] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.297796] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.297817] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.301729] ehci_hcd 0000:00:1a.7: debug port 1
[    2.301737] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.301743] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    2.317508] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.317574] usb usb4: configuration #1 chosen from 1 choice
[    2.317597] hub 4-0:1.0: USB hub found
[    2.317607] hub 4-0:1.0: 6 ports detected
[    2.420303] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.420310] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.420313] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.420334] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.420364] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[    2.420431] usb usb5: configuration #1 chosen from 1 choice
[    2.420455] hub 5-0:1.0: USB hub found
[    2.420460] hub 5-0:1.0: 2 ports detected
[    2.628248] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.628255] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.628263] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.628282] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.628307] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    2.628379] usb usb6: configuration #1 chosen from 1 choice
[    2.628400] hub 6-0:1.0: USB hub found
[    2.628405] hub 6-0:1.0: 2 ports detected
[    2.732212] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.732218] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.732225] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.732247] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.732268] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[    2.732336] usb usb7: configuration #1 chosen from 1 choice
[    2.732357] hub 7-0:1.0: USB hub found
[    2.732361] hub 7-0:1.0: 2 ports detected
[    2.740023] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    2.929719] usb 5-1: configuration #1 chosen from 1 choice
[    2.941813] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.941824] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.941827] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.941851] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.945742] ehci_hcd 0000:00:1d.7: debug port 1
[    2.945747] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.945752] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    3.048043] usb 5-2: new full speed USB device using uhci_hcd and address 3
[    3.060034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.060128] usb usb8: configuration #1 chosen from 1 choice
[    3.060162] hub 8-0:1.0: USB hub found
[    3.060175] hub 8-0:1.0: 6 ports detected
[    3.116055] hub 5-0:1.0: unable to enumerate USB device on port 2
[    3.268332] uhci_hcd 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.268339] uhci_hcd 0000:05:02.0: UHCI Host Controller
[    3.268360] uhci_hcd 0000:05:02.0: new USB bus registered, assigned bus number 9
[    3.268384] uhci_hcd 0000:05:02.0: irq 18, io base 0x0000e880
[    3.268455] usb usb9: configuration #1 chosen from 1 choice
[    3.268480] hub 9-0:1.0: USB hub found
[    3.268485] hub 9-0:1.0: 2 ports detected
[    3.268563] ata_piix 0000:00:1f.2: version 2.12
[    3.268579] ata_piix 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.268583] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    3.268622] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.269564] scsi0 : ata_piix
[    3.269664] scsi1 : ata_piix
[    3.270968] ata1: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 22
[    3.270972] ata2: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 22
[    3.372030] usb 5-1: USB disconnect, address 2
[    3.476204] uhci_hcd 0000:05:02.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.476212] uhci_hcd 0000:05:02.1: UHCI Host Controller
[    3.476231] uhci_hcd 0000:05:02.1: new USB bus registered, assigned bus number 10
[    3.476252] uhci_hcd 0000:05:02.1: irq 19, io base 0x0000ec00
[    3.476321] usb usb10: configuration #1 chosen from 1 choice
[    3.476343] hub 10-0:1.0: USB hub found
[    3.476348] hub 10-0:1.0: 2 ports detected
[    3.729039] usb 8-2: new high speed USB device using ehci_hcd and address 3
[    3.744061] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.752592] ata1.00: ATA-7: ST3500320AS, SD04, max UDMA/133
[    3.752596] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.768562] ata1.00: configured for UDMA/133
[    3.950557] usb 8-2: configuration #1 chosen from 1 choice
[    4.232533] usb 9-1: new full speed USB device using uhci_hcd and address 2
[    4.360067] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.375411] usb 9-1: not running at top speed; connect to a high speed hub
[    4.376189] ata2.00: HPA unlocked: 390719855 -> 390721968, native 390721968
[    4.376193] ata2.00: ATA-6: ST3200822AS, 3.01, max UDMA/133
[    4.376195] ata2.00: 390721968 sectors, multi 16: LBA48
[    4.392384] ata2.00: configured for UDMA/133
[    4.392501] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD04 PQ: 0 ANSI: 5
[    4.392631] scsi 1:0:0:0: Direct-Access     ATA      ST3200822AS      3.01 PQ: 0 ANSI: 5
[    4.392749] ehci_hcd 0000:05:02.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    4.392755] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.392763] ehci_hcd 0000:05:02.2: EHCI Host Controller
[    4.392766] atl1 0000:02:00.0: setting latency timer to 64
[    4.392784] atl1 0000:02:00.0: version 2.1.3
[    4.392794] ehci_hcd 0000:05:02.2: new USB bus registered, assigned bus number 11
[    4.392829] ehci_hcd 0000:05:02.2: irq 16, io mem 0xfebf7c00
[    4.393512] ata_piix 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.393516] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    4.393551] ata_piix 0000:00:1f.5: setting latency timer to 64
[    4.393610] scsi2 : ata_piix
[    4.393921] scsi3 : ata_piix
[    4.395219] ata3: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 22
[    4.395223] ata4: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 22
[    4.405543] ehci_hcd 0000:05:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.405635] usb usb11: configuration #1 chosen from 1 choice
[    4.405658] hub 11-0:1.0: USB hub found
[    4.405664] hub 11-0:1.0: 4 ports detected
[    4.409759] usb 9-1: configuration #1 chosen from 1 choice
[    4.413415] usb 9-1: can't set config #1, error -71
[    4.652027] usb 5-1: new full speed USB device using uhci_hcd and address 4
[    4.841707] usb 5-1: configuration #1 chosen from 1 choice
[    4.872058] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.880359] ata3.00: ATA-7: Maxtor 6Y120M0, YAR51HW0, max UDMA/133
[    4.880363] ata3.00: 240121728 sectors, multi 0: LBA
[    4.896894] ata3.00: configured for UDMA/133
[    5.088017] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    5.682599] usb 7-1: configuration #1 chosen from 1 choice
[    5.924594] usb 7-2: new low speed USB device using uhci_hcd and address 3
[    5.932091] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.968189] ata4.00: HPA unlocked: 240119615 -> 240121728, native 240121728
[    5.968194] ata4.00: ATA-7: Maxtor 6Y120M0, YAR51EW0, max UDMA/133
[    5.968196] ata4.00: 240121728 sectors, multi 0: LBA
[    5.984407] ata4.00: configured for UDMA/133
[    5.984523] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y120M0   YAR5 PQ: 0 ANSI: 5
[    5.984657] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6Y120M0   YAR5 PQ: 0 ANSI: 5
[    5.984782] ahci 0000:03:00.0: version 3.0
[    5.984801] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.000066] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    6.000071] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part
[    6.000078] ahci 0000:03:00.0: setting latency timer to 64
[    6.000226] scsi4 : ahci
[    6.000318] scsi5 : ahci
[    6.000387] ata5: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe100 irq 16
[    6.000390] ata6: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe180 irq 16
[    6.098421] usb 7-2: configuration #1 chosen from 1 choice
[    6.101537] usb 9-1: USB disconnect, address 2
[    6.320038] ata5: SATA link down (SStatus 0 SControl 300)
[    6.340536] usb 11-1: new high speed USB device using ehci_hcd and address 2
[    6.473316] usb 11-1: configuration #1 chosen from 1 choice
[    6.474898] usbcore: registered new interface driver hiddev
[    6.474905] usbcore: registered new interface driver libusual
[    6.479850] Initializing USB Mass Storage driver...
[    6.479957] scsi6 : SCSI emulation for USB Mass Storage devices
[    6.480030] usb-storage: device found at 3
[    6.480032] usb-storage: waiting for device to settle before scanning
[    6.485269] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.485299] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    6.485328] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    6.485361] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[    6.492639] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input1
[    6.496160] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.2-2
[    6.496199] usbcore: registered new interface driver usbhid
[    6.496202] usbhid: v2.6:USB HID core driver
[    6.496214] usbcore: registered new interface driver usb-storage
[    6.496217] USB Mass Storage support registered.
[    6.656080] ata6: SATA link down (SStatus 0 SControl 300)
[    6.673115] ohci1394 0000:05:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.674424] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    6.674432] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.674460] pata_acpi 0000:03:00.1: setting latency timer to 64
[    6.674473] pata_acpi 0000:03:00.1: PCI INT B disabled
[    6.725834] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[febf7000-febf77ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.733266] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.733298] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    6.733359] scsi7 : pata_jmicron
[    6.733573] scsi8 : pata_jmicron
[    6.734285] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[    6.734288] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[    6.745084] Driver 'sd' needs updating - please use bus_type methods
[    6.745170] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    6.745185] sd 0:0:0:0: [sda] Write Protect is off
[    6.745187] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.745211] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.745268] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    6.745281] sd 0:0:0:0: [sda] Write Protect is off
[    6.745284] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.745308] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.745311]  sda: sda1 sda2 sda3
[    6.758075] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.758143] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[    6.758159] sd 1:0:0:0: [sdb] Write Protect is off
[    6.758161] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.758187] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.758236] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[    6.758251] sd 1:0:0:0: [sdb] Write Protect is off
[    6.758254] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.758280] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.758284]  sdb: sdb1
[    6.762898] sd 1:0:0:0: [sdb] Attached SCSI disk
[    6.762978] sd 2:0:0:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[    6.762994] sd 2:0:0:0: [sdc] Write Protect is off
[    6.762996] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.763022] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.763072] sd 2:0:0:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[    6.763086] sd 2:0:0:0: [sdc] Write Protect is off
[    6.763089] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.763115] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.763119]  sdc: sdc1
[    6.785071] sd 2:0:0:0: [sdc] Attached SCSI disk
[    6.785132] sd 3:0:0:0: [sdd] 240121728 512-byte hardware sectors (122942 MB)
[    6.785147] sd 3:0:0:0: [sdd] Write Protect is off
[    6.785149] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    6.785175] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.785230] sd 3:0:0:0: [sdd] 240121728 512-byte hardware sectors (122942 MB)
[    6.785245] sd 3:0:0:0: [sdd] Write Protect is off
[    6.785247] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    6.785274] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.785277]  sdd: sdd1
[    6.802563] sd 3:0:0:0: [sdd] Attached SCSI disk
[    7.080518] ata7.01: ATAPI: LITE-ON DVDRW SHW-1635S, YS0J, max UDMA/66
[    7.113526] ata7.01: configured for UDMA/66
[    7.281348] scsi 7:0:1:0: CD-ROM            LITE-ON  DVDRW SHW-1635S  YS0J PQ: 0 ANSI: 5
[    7.281519] scsi 7:0:1:0: Attached scsi generic sg4 type 5
[    7.306673] Driver 'sr' needs updating - please use bus_type methods
[    7.310359] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    7.310364] Uniform CD-ROM driver Revision: 3.20
[    7.310469] sr 7:0:1:0: Attached scsi CD-ROM sr0
[    7.530058] PM: Starting manual resume from disk
[    7.530061] PM: Resume from partition 8:2
[    7.530062] PM: Checking hibernation image.
[    7.530395] PM: Resume from disk failed.
[    7.551774] kjournald starting.  Commit interval 5 seconds
[    7.551780] EXT3-fs: mounted filesystem with ordered data mode.
[    8.000687] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800017c8ce7]
[   11.477268] usb-storage: device scan complete
[   11.507773] scsi 6:0:0:0: Direct-Access     Generic  2.0 Reader-CF    1.00 PQ: 0 ANSI: 0 CCS
[   11.538257] scsi 6:0:0:1: Direct-Access     Generic  2.0 Reader-SM/xD 1.00 PQ: 0 ANSI: 0 CCS
[   11.568773] scsi 6:0:0:2: Direct-Access     Generic  2.0 Reader-SD    1.00 PQ: 0 ANSI: 0 CCS
[   11.599270] scsi 6:0:0:3: Direct-Access     Generic  2.0 Reader-MS    1.00 PQ: 0 ANSI: 0 CCS
[   11.600558] sd 6:0:0:0: [sde] Attached SCSI removable disk
[   11.600643] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   11.601689] sd 6:0:0:1: [sdf] Attached SCSI removable disk
[   11.601754] sd 6:0:0:1: Attached scsi generic sg6 type 0
[   11.602798] sd 6:0:0:2: [sdg] Attached SCSI removable disk
[   11.602838] sd 6:0:0:2: Attached scsi generic sg7 type 0
[   11.603927] sd 6:0:0:3: [sdh] Attached SCSI removable disk
[   11.603986] sd 6:0:0:3: Attached scsi generic sg8 type 0
[   14.138315] udevd version 124 started
[   14.524376] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   14.540523] ACPI: Power Button (FF) [PWRF]
[   14.540622] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   14.572515] ACPI: Power Button (CM) [PWRB]
[   14.584566] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.610516] Linux agpgart interface v0.103
[   14.614822] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.623231] iTCO_vendor_support: vendor-support=0
[   14.720886] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.720950] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0860)
[   14.721030] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.786364] Bluetooth: Core ver 2.13
[   14.786418] NET: Registered protocol family 31
[   14.786420] Bluetooth: HCI device and connection manager initialized
[   14.786423] Bluetooth: HCI socket layer initialized
[   14.832657] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.971704] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   15.041256] ndiswrapper: driver rt61 (Linksys, A Division of Cisco Systems, Inc.,10/18/2005, 1.00.03.0000) loaded
[   15.041517] ndiswrapper 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.051122] ndiswrapper: using IRQ 17
[   15.414285] wlan0: ethernet device 00:18:f8:a7:4b:86 using serialized NDIS driver: rt61, version: 0x0, NDIS version: 0x500, vendor: 'Linksys Wireless-G PCI Adapter', 1814:0301.5.conf
[   15.414306] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   15.414364] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.414371] nvidia 0000:01:00.0: setting latency timer to 64
[   15.414452] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   15.416155] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   15.420179] usbcore: registered new interface driver ndiswrapper
[   15.420209] usbcore: registered new interface driver btusb
[   15.428276] usbcore: registered new interface driver lmpcm_usb
[   15.428290] lmpcm_usb: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   15.468893] usbcore: registered new interface driver usbserial
[   15.468906] usbserial: USB Serial support registered for generic
[   15.468946] usbcore: registered new interface driver usbserial_generic
[   15.468947] usbserial: USB Serial Driver core
[   15.508386] usbserial: USB Serial support registered for FTDI USB Serial Device
[   15.508573] ftdi_sio 5-1:1.0: FTDI USB Serial Device converter detected
[   15.508607] ftdi_sio: Detected FT232BM
[   15.508711] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB0
[   15.508733] usbcore: registered new interface driver ftdi_sio
[   15.508735] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[   15.748237] dib0700: loaded with support for 7 different device-types
[   15.748413] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   15.748449] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.748613] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   15.866686] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   15.920686] MT2060: successfully identified (IF1 = 1220)
[   16.003043] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.003059] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.039007] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   16.427383] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.427556] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   16.433505] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   16.438252] MT2060: successfully identified (IF1 = 1220)
[   16.993668] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:05:02.2/usb11/11-1/input/input5
[   17.004221] dvb-usb: schedule remote query interval to 150 msecs.
[   17.004224] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   17.004474] usbcore: registered new interface driver dvb_usb_dib0700
[   17.883242] end_request: I/O error, dev sr0, sector 15955200
[   17.883249] Buffer I/O error on device sr0, logical block 1994400
[   18.671481] end_request: I/O error, dev sr0, sector 15955200
[   18.671486] Buffer I/O error on device sr0, logical block 1994400
[   19.571244] end_request: I/O error, dev sr0, sector 15955136
[   19.571250] Buffer I/O error on device sr0, logical block 1994392
[   19.733032] end_request: I/O error, dev sr0, sector 15955136
[   19.733038] Buffer I/O error on device sr0, logical block 1994392
[   20.034988] lp: driver loaded but no devices found
[   20.145651] Adding 2000084k swap on /dev/sda2.  Priority:-1 extents:1 across:2000084k
[   20.690656] EXT3 FS on sda1, internal journal
[   21.506877] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   21.508390] SGI XFS Quota Management subsystem
[   21.545454] XFS mounting filesystem sda3
[   21.639241] Ending clean XFS mount for filesystem: sda3
[   21.664562] XFS mounting filesystem sdb1
[   21.734316] Ending clean XFS mount for filesystem: sdb1
[   21.876848] XFS mounting filesystem sdd1
[   22.118703] Ending clean XFS mount for filesystem: sdd1
[   22.167535] XFS mounting filesystem sdc1
[   22.353068] Ending clean XFS mount for filesystem: sdc1
[   22.719081] type=1505 audit(1226350454.790:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5834
[   22.719218] type=1505 audit(1226350454.790:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5834
[   22.751725] type=1505 audit(1226350454.820:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=5847
[   22.854203] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.100769] NET: Registered protocol family 17
[   95.442365] NET: Registered protocol family 10
[   95.442965] lo: Disabled Privacy Extensions
[   95.443659] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   95.546315] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  135.668561] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
[  168.625956] RPC: Registered udp transport module.
[  168.625959] RPC: Registered tcp transport module.
[  169.297699] ACPI: WMI: Mapper loaded
[  171.683391] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  171.683397] apm: disabled - APM is not SMP safe.
[  171.817155] ppdev: user-space parallel port driver
[  206.849022] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[  207.149068] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  207.163488] NFSD: starting 90-second grace period
[  213.839416] Bluetooth: L2CAP ver 2.11
[  213.839421] Bluetooth: L2CAP socket layer initialized
[  213.869501] Bluetooth: RFCOMM socket layer initialized
[  213.869512] Bluetooth: RFCOMM TTY layer initialized
[  213.869514] Bluetooth: RFCOMM ver 1.10
[  213.878798] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  213.878803] Bluetooth: BNEP filters: protocol multicast
[  213.905842] Bridge firewalling registered
[  213.905992] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  213.925304] Bluetooth: SCO (Voice Link) ver 0.6
[  213.925309] Bluetooth: SCO socket layer initialized
[  215.578021] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  216.377857] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  216.739708] NET: Registered protocol family 5
[  227.236026] wlan0: no IPv6 routers present
[  229.326449] end_request: I/O error, dev sr0, sector 15954364
[  229.421052] UDF-fs: Partition marked readonly; forcing readonly mount
[  229.457569] UDF-fs INFO UDF: Mounting volume 'PC FINALLY DISK 2', timestamp 2036/02/07 12:58 (1294)
[  298.789677] type=1503 audit(1226350730.861:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/17614/net/" pid=17614 profile="/usr/sbin/cupsd"
[  299.982248] type=1503 audit(1226350732.053:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/17618/net/" pid=17618 profile="/usr/sbin/cupsd"
[  299.982279] type=1503 audit(1226350732.053:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=17618 profile="/usr/sbin/cupsd"
[  299.982284] type=1503 audit(1226350732.053:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=17618 profile="/usr/sbin/cupsd"
[  299.982289] type=1503 audit(1226350732.053:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=17618 profile="/usr/sbin/cupsd"
[  299.982303] type=1503 audit(1226350732.053:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=17618 profile="/usr/sbin/cupsd"
[  299.982308] type=1503 audit(1226350732.053:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=17618 profile="/usr/sbin/cupsd"
[  299.982313] type=1503 audit(1226350732.053:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=17618 profile="/usr/sbin/cupsd"
[  299.982317] type=1503 audit(1226350732.053:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=17618 profile="/usr/sbin/cupsd"
[  299.982333] type=1503 audit(1226350732.053:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=17618 profile="/usr/sbin/cupsd"
[ 1064.454886] __set_isoc_interface: hci0 setting interface failed (71)
[ 1064.584045] usb 7-1: USB disconnect, address 2
[ 1064.584877] btusb_intr_complete: hci0 urb f55c8780 failed to resubmit (19)
[ 1064.584890] btusb_bulk_complete: hci0 urb f5040300 failed to resubmit (19)
[ 1064.584897] btusb_bulk_complete: hci0 urb f5040180 failed to resubmit (19)
[ 1064.587691] btusb_send_frame: hci0 urb f5040c80 submission failed
[ 1064.587700] __set_isoc_interface: hci0 setting interface failed (19)
[ 1066.560023] usb 7-1: new full speed USB device using uhci_hcd and address 4
[ 1067.404025] usb 7-1: configuration #1 chosen from 1 choice
[ 1071.175561] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 1071.176226] input: mythtv_keyboard as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/bluetooth/hci0/hci0:41/input6
[ 1478.023065] __ratelimit: 3 callbacks suppressed
[ 1478.023070] type=1503 audit(1226351910.094:16): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/19712/net/" pid=19712 profile="/usr/sbin/cupsd"
[ 1479.032767] type=1503 audit(1226351911.102:17): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/19716/net/" pid=19716 profile="/usr/sbin/cupsd"
[ 1479.032797] type=1503 audit(1226351911.102:18): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=19716 profile="/usr/sbin/cupsd"
[ 1479.032802] type=1503 audit(1226351911.102:19): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=19716 profile="/usr/sbin/cupsd"
[ 1479.032807] type=1503 audit(1226351911.102:20): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=19716 profile="/usr/sbin/cupsd"
[ 1479.032823] type=1503 audit(1226351911.102:21): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=19716 profile="/usr/sbin/cupsd"
[ 1479.032828] type=1503 audit(1226351911.102:22): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=19716 profile="/usr/sbin/cupsd"
[ 1479.032833] type=1503 audit(1226351911.102:23): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=19716 profile="/usr/sbin/cupsd"
[ 1479.032838] type=1503 audit(1226351911.102:24): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=19716 profile="/usr/sbin/cupsd"
[ 1479.032854] type=1503 audit(1226351911.102:25): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=19716 profile="/usr/sbin/cupsd"[/HTML]

---

### Post by null_pointer_us on 2008-11-14
Some users have reported slow boot times in Ubuntu 8.10 unless their optical drives were empty.

It's probably related to this line:

```
[  229.326449] end_request: I/O error, dev sr0, sector 15954364
```

A forum search for **end_request sr0** will turn up some related threads.

EDIT: Here's one:
[http://ubuntuforums.org/showthread.php?t=975668&highlight=end_request+sr0](http://ubuntuforums.org/showthread.php?t=975668&highlight=end_request+sr0)

---

### Post by tgpraveen on 2008-11-14
good and effective reply

---

