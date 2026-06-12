---
title: "[SOLVED] Cannot boot Intrepid Beta on a Vostro 1400 (Nvidia problem?)"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by muadnu on 2008-10-10
I decided to give Intrepid Beta a try today, so I installed it on a separate partition on my laptop (a Dell Vostro 1400). Everything went fine, I logged in, checked a couple of things, and then run the upgrades. After rebooting, and right at the beginning of the booting process, my laptop started beeping very loudly, and then went to a blank screen from which I couldn't get it out from. I'm not sure what went wrong, but I think it has to do with the Nvidia drivers that were installed (I have an Nvidia 8400GS card). My guess is based in the following: when I tried the Alpha 3 release, the same thing happened, it logged in fine, but got this awful beeps after running the upgrades. 

Here is the output of /etc/var/dmesg in case it helps.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 10 03:55:01 UTC 2008 (Ubuntu 2.6.27-7.10-generic)
[    0.000000] Command line: root=UUID=f57a656b-f0eb-4d15-85cd-7b9fd553dbfa ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe6d800 (usable)
[    0.000000]  BIOS-e820: 000000007fe6d800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7fe6d max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fe6d000 page 4k
[    0.000000] kernel direct mapping tables up to 7fe6d000 @ 8000-c000
[    0.000000] last_map_addr: 7fe6d000 end: 7fe6d000
[    0.000000] RAMDISK: 377bf000 - 37fefb64
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7FE6F200, 005C (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: FACP 7FE6F09C, 00F4 (r4 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: DSDT 7FE6F800, 5676 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7FE7E000, 0040
[    0.000000] ACPI: HPET 7FE6F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7FE6F400, 0068 (r1 DELL    M08     27D80203 ASL        47)
[    0.000000] ACPI: MCFG 7FE6F3C0, 003E (r16 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: SLIC 7FE6F49C, 0176 (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: BOOT 7FE6EFC0, 0028 (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: SSDT 7FE6D9BC, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fe6d000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fe6d000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000a000 -  0000000000019fcf] pages 10
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fe6d000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008bbf9c]    TEXT DATA BSS ==> [0000200000 - 00008bbf9c]
[    0.000000]   #3 [00377bf000 - 0037fefb64]          RAMDISK ==> [00377bf000 - 0037fefb64]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]  [ffffe20000000000-ffffe20001ffffff] PMD -> [ffff880001200000-ffff8800031fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fe6d
[    0.000000] On node 0 totalpages: 523788
[    0.000000]   DMA zone: 2110 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 511667 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:74000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 513777
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=f57a656b-f0eb-4d15-85cd-7b9fd553dbfa ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1994.984 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2046800k/2095540k available (3118k kernel code, 48352k reserved, 1574k data, 540k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.96 BogoMIPS (lpj=7979936)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] CPU0: Thermal monitoring enabled (TM2)
[    0.004000] using mwait in idle threads.
[    0.004016] ACPI: Core revision 20080609
[    0.005972] ACPI: Checking initramfs for custom DSDT
[    0.392302] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.432000] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[    0.432005] Using local APIC timer interrupts.
[    0.432028] APIC timer calibration result 12468666
[    0.432030] Detected 12.468 MHz APIC timer.
[    0.432168] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.00 BogoMIPS (lpj=7980000)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.520670] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[    0.520696] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.524066] Brought up 2 CPUs
[    0.524069] Total of 2 processors activated (7979.96 BogoMIPS).
[    0.524123] CPU0 attaching sched-domain:
[    0.524126]  domain 0: span 0-1 level MC
[    0.524129]   groups: 0 1
[    0.524133]   domain 1: span 0-1 level NODE
[    0.524136]    groups: 0-1
[    0.524141] CPU1 attaching sched-domain:
[    0.524143]  domain 0: span 0-1 level MC
[    0.524145]   groups: 1 0
[    0.524149]   domain 1: span 0-1 level NODE
[    0.524152]    groups: 0-1
[    0.524243] net_namespace: 1552 bytes
[    0.524243] Booting paravirtualized kernel on bare hardware
[    0.524312] Time: 18:54:25  Date: 10/10/08
[    0.524312] NET: Registered protocol family 16
[    0.524312] ACPI: bus type pci registered
[    0.524312] PCI: MCFG configuration 0: base f4000000 segment 0 buses 0 - 63
[    0.524312] PCI: MCFG area at f4000000 reserved in E820
[    0.531168] PCI: Using MMCONFIG at f4000000 - f7ffffff
[    0.531173] PCI: Using configuration type 1 for base access
[    0.534170] ACPI: EC: Look up EC in DSDT
[    0.591399] ACPI: Interpreter enabled
[    0.591404] ACPI: (supports S0 S3 S4 S5)
[    0.595253] ACPI: Using IOAPIC for interrupt routing
[    0.700410] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.700410] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.700410] pci 0000:00:01.0: PME# disabled
[    0.700410] PCI: 0000:00:1a.0 reg 20 io port: [6f20, 6f3f]
[    0.700410] PCI: 0000:00:1a.1 reg 20 io port: [6f00, 6f1f]
[    0.700423] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fed1c400, fed1c7ff]
[    0.700492] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.700501] pci 0000:00:1a.7: PME# disabled
[    0.700558] PCI: 0000:00:1b.0 reg 10 64bit mmio: [febfc000, febfffff]
[    0.700623] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.700631] pci 0000:00:1b.0: PME# disabled
[    0.700716] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.700724] pci 0000:00:1c.0: PME# disabled
[    0.700809] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.700817] pci 0000:00:1c.1: PME# disabled
[    0.700904] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.700912] pci 0000:00:1c.3: PME# disabled
[    0.700999] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.701007] pci 0000:00:1c.5: PME# disabled
[    0.701065] PCI: 0000:00:1d.0 reg 20 io port: [6f80, 6f9f]
[    0.701141] PCI: 0000:00:1d.1 reg 20 io port: [6f60, 6f7f]
[    0.701217] PCI: 0000:00:1d.2 reg 20 io port: [6f40, 6f5f]
[    0.701301] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fed1c000, fed1c3ff]
[    0.701370] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.701379] pci 0000:00:1d.7: PME# disabled
[    0.701567] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.701575] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.701615] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
[    0.701626] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
[    0.701637] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
[    0.701648] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
[    0.701659] PCI: 0000:00:1f.1 reg 20 io port: [6fa0, 6faf]
[    0.701747] PCI: 0000:00:1f.2 reg 10 io port: [6eb0, 6eb7]
[    0.701758] PCI: 0000:00:1f.2 reg 14 io port: [6eb8, 6ebb]
[    0.701769] PCI: 0000:00:1f.2 reg 18 io port: [6ec0, 6ec7]
[    0.701780] PCI: 0000:00:1f.2 reg 1c io port: [6ec8, 6ecb]
[    0.701791] PCI: 0000:00:1f.2 reg 20 io port: [6ee0, 6eff]
[    0.701802] PCI: 0000:00:1f.2 reg 24 32bit mmio: [febfb800, febfbfff]
[    0.701843] pci 0000:00:1f.2: PME# supported from D3hot
[    0.701851] pci 0000:00:1f.2: PME# disabled
[    0.701877] PCI: 0000:00:1f.3 reg 10 32bit mmio: [febfb700, febfb7ff]
[    0.701910] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
[    0.702002] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.702015] PCI: 0000:01:00.0 reg 14 32bit mmio: [e0000000, efffffff]
[    0.702043] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.702056] PCI: 0000:01:00.0 reg 24 io port: [ef00, ef7f]
[    0.702067] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.702163] PCI: bridge 0000:00:01.0 io port: [e000, efff]
[    0.702169] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, feafffff]
[    0.702177] PCI: bridge 0000:00:01.0 64bit mmio pref: [e0000000, efffffff]
[    0.702458] PCI: 0000:0c:00.0 reg 10 32bit mmio: [f9fff000, f9ffffff]
[    0.702679] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.702694] pci 0000:0c:00.0: PME# disabled
[    0.702765] PCI: bridge 0000:00:1c.1 32bit mmio: [f9f00000, f9ffffff]
[    0.702851] PCI: bridge 0000:00:1c.3 io port: [d000, dfff]
[    0.702859] PCI: bridge 0000:00:1c.3 32bit mmio: [f9c00000, f9efffff]
[    0.702870] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f0000000, f01fffff]
[    0.704209] PCI: 0000:09:00.0 reg 10 64bit mmio: [f9bf0000, f9bfffff]
[    0.704374] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.704388] pci 0000:09:00.0: PME# disabled
[    0.704459] PCI: bridge 0000:00:1c.5 32bit mmio: [f9b00000, f9bfffff]
[    0.704524] PCI: 0000:03:01.0 reg 10 32bit mmio: [f9aff800, f9afffff]
[    0.704592] pci 0000:03:01.0: supports D1
[    0.704595] pci 0000:03:01.0: supports D2
[    0.704599] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.704607] pci 0000:03:01.0: PME# disabled
[    0.704652] PCI: 0000:03:01.1 reg 10 32bit mmio: [f9aff500, f9aff5ff]
[    0.704719] pci 0000:03:01.1: supports D1
[    0.704723] pci 0000:03:01.1: supports D2
[    0.704726] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.704734] pci 0000:03:01.1: PME# disabled
[    0.704780] PCI: 0000:03:01.2 reg 10 32bit mmio: [f9aff600, f9aff6ff]
[    0.704848] pci 0000:03:01.2: supports D1
[    0.704851] pci 0000:03:01.2: supports D2
[    0.704855] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.704863] pci 0000:03:01.2: PME# disabled
[    0.704907] PCI: 0000:03:01.3 reg 10 32bit mmio: [f9aff700, f9aff7ff]
[    0.704975] pci 0000:03:01.3: supports D1
[    0.704979] pci 0000:03:01.3: supports D2
[    0.704982] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.704990] pci 0000:03:01.3: PME# disabled
[    0.705071] pci 0000:00:1e.0: transparent bridge
[    0.705081] PCI: bridge 0000:00:1e.0 32bit mmio: [f9a00000, f9afffff]
[    0.705143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.706646] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.707149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.707493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.707912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.708348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.708766] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.748412] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.748844] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.749269] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.749694] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.750122] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.750557] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.750990] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.751374] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.751575] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.752064] pnp: PnP ACPI init
[    0.752078] ACPI: bus type pnp registered
[    0.821173] pnp 00:09: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.821180] pnp 00:09: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.821266] pnp 00:0a: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.821266] pnp 00:0a: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.821266] pnp 00:0a: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.821266] pnp 00:0a: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.910136] pnp: PnP ACPI: found 12 devices
[    0.910136] ACPI: ACPI bus type pnp unregistered
[    0.910136] PCI: Using ACPI for IRQ routing
[    0.940046] NET: Registered protocol family 8
[    0.940050] NET: Registered protocol family 20
[    0.940075] NetLabel: Initializing
[    0.940075] NetLabel:  domain hash size = 128
[    0.940075] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.940093] NetLabel:  unlabeled traffic allowed by default
[    0.940138] PCI-GART: No AMD northbridge found.
[    0.940147] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.940157] hpet0: 3 64-bit timers, 14318180 Hz
[    0.944049] Switched to high resolution mode on CPU 0
[    0.944725] Switched to high resolution mode on CPU 1
[    0.944907] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.944912]    actual entries 65586
[    0.945064] AppArmor: AppArmor Filesystem Enabled
[    0.945098] ACPI: RTC can wake from S4
[    0.960037] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    0.960054] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.960067] system 00:09: ioport range 0x900-0x97f has been reserved
[    0.960073] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.960085] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    0.960091] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    0.960096] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    0.960102] system 00:0a: ioport range 0x809-0x809 has been reserved
[    0.960115] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    0.960121] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    0.960126] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.960132] system 00:0b: iomem range 0xe0000-0xfffff has been reserved
[    0.960138] system 00:0b: iomem range 0x100000-0x7fe6d7ff could not be reserved
[    0.960144] system 00:0b: iomem range 0x7fe6d800-0x7fefffff could not be reserved
[    0.960151] system 00:0b: iomem range 0x7ff00000-0x7fffffff could not be reserved
[    0.960157] system 00:0b: iomem range 0x7ff00000-0x806fffff could not be reserved
[    0.960163] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.960170] system 00:0b: iomem range 0xffa00000-0xffafffff has been reserved
[    0.960176] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.960182] system 00:0b: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.960189] system 00:0b: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.960195] system 00:0b: iomem range 0xfeda0000-0xfeda3fff could not be reserved
[    0.960201] system 00:0b: iomem range 0xfeda4000-0xfeda4fff could not be reserved
[    0.960208] system 00:0b: iomem range 0xfeda5000-0xfeda5fff could not be reserved
[    0.960214] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.960220] system 00:0b: iomem range 0xfed18000-0xfed1bfff could not be reserved
[    0.960227] system 00:0b: iomem range 0xf4000000-0xf7ffffff could not be reserved
[    0.965775] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.965782] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.965789] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfeafffff
[    0.965796] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.965805] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.965810] pci 0000:00:1c.0:   IO window: disabled
[    0.965819] pci 0000:00:1c.0:   MEM window: disabled
[    0.965826] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.965837] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.965841] pci 0000:00:1c.1:   IO window: disabled
[    0.965851] pci 0000:00:1c.1:   MEM window: 0xf9f00000-0xf9ffffff
[    0.965859] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.965870] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.965876] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.965885] pci 0000:00:1c.3:   MEM window: 0xf9c00000-0xf9efffff
[    0.965893] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.965906] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.965910] pci 0000:00:1c.5:   IO window: disabled
[    0.965919] pci 0000:00:1c.5:   MEM window: 0xf9b00000-0xf9bfffff
[    0.965927] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.965938] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.965943] pci 0000:00:1e.0:   IO window: disabled
[    0.965952] pci 0000:00:1e.0:   MEM window: 0xf9a00000-0xf9afffff
[    0.965959] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.965984] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.965992] pci 0000:00:01.0: setting latency timer to 64
[    0.966005] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.966014] pci 0000:00:1c.0: setting latency timer to 64
[    0.966029] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.966038] pci 0000:00:1c.1: setting latency timer to 64
[    0.966053] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.966062] pci 0000:00:1c.3: setting latency timer to 64
[    0.966075] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.966084] pci 0000:00:1c.5: setting latency timer to 64
[    0.966097] pci 0000:00:1e.0: setting latency timer to 64
[    0.966103] bus: 00 index 0 io port: [0, ffff]
[    0.966107] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.966112] bus: 01 index 0 io port: [e000, efff]
[    0.966116] bus: 01 index 1 mmio: [fa000000, feafffff]
[    0.966120] bus: 01 index 2 mmio: [e0000000, efffffff]
[    0.966123] bus: 01 index 3 mmio: [0, 0]
[    0.966127] bus: 0b index 0 mmio: [0, 0]
[    0.966130] bus: 0b index 1 mmio: [0, 0]
[    0.966134] bus: 0b index 2 mmio: [0, 0]
[    0.966137] bus: 0b index 3 mmio: [0, 0]
[    0.966141] bus: 0c index 0 mmio: [0, 0]
[    0.966144] bus: 0c index 1 mmio: [f9f00000, f9ffffff]
[    0.966148] bus: 0c index 2 mmio: [0, 0]
[    0.966151] bus: 0c index 3 mmio: [0, 0]
[    0.966155] bus: 0d index 0 io port: [d000, dfff]
[    0.966159] bus: 0d index 1 mmio: [f9c00000, f9efffff]
[    0.966163] bus: 0d index 2 mmio: [f0000000, f01fffff]
[    0.966166] bus: 0d index 3 mmio: [0, 0]
[    0.966170] bus: 09 index 0 mmio: [0, 0]
[    0.966173] bus: 09 index 1 mmio: [f9b00000, f9bfffff]
[    0.966177] bus: 09 index 2 mmio: [0, 0]
[    0.966181] bus: 09 index 3 mmio: [0, 0]
[    0.966184] bus: 03 index 0 mmio: [0, 0]
[    0.966188] bus: 03 index 1 mmio: [f9a00000, f9afffff]
[    0.966192] bus: 03 index 2 mmio: [0, 0]
[    0.966195] bus: 03 index 3 io port: [0, ffff]
[    0.966199] bus: 03 index 4 mmio: [0, ffffffffffffffff]
[    0.966214] NET: Registered protocol family 2
[    1.004231] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    1.005863] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    1.007689] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.008246] TCP: Hash tables configured (established 262144 bind 65536)
[    1.008253] TCP reno registered
[    1.020152] NET: Registered protocol family 1
[    1.020339] checking if image is initramfs... it is
[    1.825545] Freeing initrd memory: 8386k freed
[    1.830929] Simple Boot Flag at 0x79 set to 0x1
[    1.831865] audit: initializing netlink socket (disabled)
[    1.831889] type=2000 audit(1223664865.828:1): initialized
[    1.838013] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.840316] VFS: Disk quotas dquot_6.5.1
[    1.840394] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.840487] msgmni has been set to 4014
[    1.840605] io scheduler noop registered
[    1.840608] io scheduler anticipatory registered
[    1.840610] io scheduler deadline registered
[    1.840724] io scheduler cfq registered (default)
[    1.840900] pci 0000:01:00.0: Boot video device
[    1.841020] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.841054] pcieport-driver 0000:00:01.0: found MSI capability
[    1.841086] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.841126] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.841160] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.841246] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.841294] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.841341] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.841380] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.841416] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.841520] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.841568] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.841616] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.841651] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.841686] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.841794] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.841842] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.841889] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.841924] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.841959] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.842067] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.842115] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.842162] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.842199] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.842237] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.872228] hpet_resources: 0xfed00000 is busy
[    1.872329] Linux agpgart interface v0.103
[    1.872334] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.874298] brd: module loaded
[    1.874370] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.874477] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.877875] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.877881] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.900107] mice: PS/2 mouse device common for all mice
[    1.900220] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.900255] rtc0: alarms up to one month, y3k, hpet irqs
[    1.900293] cpuidle: using governor ladder
[    1.900295] cpuidle: using governor menu
[    1.900829] registered taskstats version 1
[    1.900982]   Magic number: 12:575:948
[    1.900997] tty ttya3: hash matches
[    1.901067] tty tty5: hash matches
[    1.901130] rtc_cmos 00:03: setting system clock to 2008-10-10 18:54:27 UTC (1223664867)
[    1.901133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.901135] EDD information not available.
[    1.901177] Freeing unused kernel memory: 540k freed
[    1.901408] Write protecting the kernel read-only data: 1252k
[    1.903782] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.036037] fuse init (API version 7.9)
[    2.044580] uvesafb: failed to execute /sbin/v86d
[    2.044649] uvesafb: make sure that the v86d helper is installed and executable
[    2.044726] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
[    2.044796] uvesafb: vbe_init() failed with -22
[    2.044880] uvesafb: probe of uvesafb.0 failed with error -22
[    2.164485] ACPI: SSDT 7FE6E4F2, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.164945] ACPI: SSDT 7FE6DE88, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.165302] Monitor-Mwait will be used to enter C-1 state
[    2.165305] Monitor-Mwait will be used to enter C-2 state
[    2.165307] Monitor-Mwait will be used to enter C-3 state
[    2.165479] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.165531] processor ACPI0007:00: registered as cooling_device0
[    2.165540] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.165878] ACPI: SSDT 7FE6E778, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.166198] ACPI: SSDT 7FE6E46D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.168026] Marking TSC unstable due to TSC halts in idle
[    2.176227] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.176280] processor ACPI0007:01: registered as cooling_device1
[    2.176284] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.183853] thermal LNXTHERM:01: registered as thermal_zone0
[    2.187485] ACPI: Thermal Zone [THM] (58 C)
[    2.354164] usbcore: registered new interface driver usbfs
[    2.354188] usbcore: registered new interface driver hub
[    2.360650] usbcore: registered new device driver usb
[    2.365216] USB Universal Host Controller Interface driver v3.0
[    2.365264] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.365275] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.365280] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.365322] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.365375] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    2.365527] usb usb1: configuration #1 chosen from 1 choice
[    2.365555] hub 1-0:1.0: USB hub found
[    2.365562] hub 1-0:1.0: 2 ports detected
[    2.576239] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.576250] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.576254] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.576280] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.576320] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    2.576410] usb usb2: configuration #1 chosen from 1 choice
[    2.576438] hub 2-0:1.0: USB hub found
[    2.576445] hub 2-0:1.0: 2 ports detected
[    2.655551] No dock devices found.
[    2.680296] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.680311] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.680315] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.680339] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.684267] ehci_hcd 0000:00:1a.7: debug port 1
[    2.684274] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.684290] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.688185] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    2.700028] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.700147] usb usb3: configuration #1 chosen from 1 choice
[    2.700174] hub 3-0:1.0: USB hub found
[    2.700182] hub 3-0:1.0: 4 ports detected
[    2.756246] hub 1-0:1.0: unable to enumerate USB device on port 2
[    2.764740] SCSI subsystem initialized
[    2.816907] libata version 3.00 loaded.
[    2.916382] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.916395] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.916400] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.916428] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.916473] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    2.916565] usb usb4: configuration #1 chosen from 1 choice
[    2.916589] hub 4-0:1.0: USB hub found
[    2.916595] hub 4-0:1.0: 2 ports detected
[    3.020462] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.020474] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.020479] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.020501] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    3.020543] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    3.020632] usb usb5: configuration #1 chosen from 1 choice
[    3.020655] hub 5-0:1.0: USB hub found
[    3.020661] hub 5-0:1.0: 2 ports detected
[    3.124347] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.124359] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.124363] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.124385] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    3.124428] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    3.124517] usb usb6: configuration #1 chosen from 1 choice
[    3.124540] hub 6-0:1.0: USB hub found
[    3.124546] hub 6-0:1.0: 2 ports detected
[    3.332457] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.332473] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.332478] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.332501] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.336421] ehci_hcd 0000:00:1d.7: debug port 1
[    3.336432] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.336438] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    3.372059] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    3.384059] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.384128] usb usb7: configuration #1 chosen from 1 choice
[    3.384152] hub 7-0:1.0: USB hub found
[    3.384158] hub 7-0:1.0: 6 ports detected
[    3.562955] usb 1-2: configuration #1 chosen from 1 choice
[    3.565927] hub 1-2:1.0: USB hub found
[    3.567450] hub 1-2:1.0: 3 ports detected
[    3.595030] tg3.c:v3.94 (August 14, 2008)
[    3.595057] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.595077] tg3 0000:09:00.0: setting latency timer to 64
[    3.595420] ahci 0000:00:1f.2: version 3.0
[    3.595434] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.595605] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    3.595609] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    3.595616] ahci 0000:00:1f.2: setting latency timer to 64
[    3.596380] scsi0 : ahci
[    3.596503] scsi1 : ahci
[    3.596584] scsi2 : ahci
[    3.596856] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 2298
[    3.596858] ata2: DUMMY
[    3.596861] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 2298
[    3.873567] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1a:a0:fd:64:0b
[    3.873571] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[    3.873573] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.028066] usb 7-6: new high speed USB device using ehci_hcd and address 2
[    4.084085] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.166050] usb 7-6: configuration #1 chosen from 1 choice
[    4.258465] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
[    4.393324] usb 1-2.1: configuration #1 chosen from 1 choice
[    4.416389] ata1.00: ATA-7: TOSHIBA MK1237GSX, DL140D, max UDMA/100
[    4.416393] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    4.417252] ata1.00: configured for UDMA/100
[    4.474462] usb 1-2.2: new full speed USB device using uhci_hcd and address 5
[    4.619541] usb 1-2.2: configuration #1 chosen from 1 choice
[    4.705452] usb 1-2.3: new full speed USB device using uhci_hcd and address 6
[    4.764083] ata3: SATA link down (SStatus 0 SControl 300)
[    4.780214] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL14 PQ: 0 ANSI: 5
[    4.780325] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.831045] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f9aff800-f9afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.841107] ata_piix 0000:00:1f.1: version 2.12
[    4.841119] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.841158] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.844265] scsi3 : ata_piix
[    4.844405] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.852778] scsi4 : ata_piix
[    4.853537] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    4.853540] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    4.856251] Driver 'sd' needs updating - please use bus_type methods
[    4.856355] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.856379] sd 0:0:0:0: [sda] Write Protect is off
[    4.856381] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.856419] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.856507] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.856528] sd 0:0:0:0: [sda] Write Protect is off
[    4.856531] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.856569] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.856573]  sda:<6>usb 1-2.3: configuration #1 chosen from 1 choice
[    4.896578] usbcore: registered new interface driver hiddev
[    4.899745] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
[    4.908113] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2
[    4.911825] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.3/1-2.3:1.0/input/input3
[    4.917876]  sda1 sda2 <<6>input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3
[    4.932144] usbcore: registered new interface driver usbhid
[    4.932147] usbhid: v2.6:USB HID core driver
[    4.935310]  sda5 sda6 sda7 >
[    4.957317] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.033521] ata4.00: ATAPI: PIONEER DVD+/-RW DR-K17Y, 0.95, max UDMA/33
[    5.065440] ata4.00: configured for UDMA/33
[    5.065488] ata5: port disabled. ignoring.
[    5.065524] isa bounce pool size: 16 pages
[    5.075619] scsi 3:0:0:0: CD-ROM            PIONEER  DVD+-RW DR-K17Y  0.95 PQ: 0 ANSI: 5
[    5.075740] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    5.106069] Driver 'sr' needs updating - please use bus_type methods
[    5.147442] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.147446] Uniform CD-ROM driver Revision: 3.20
[    5.147529] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    5.495031] PM: Starting manual resume from disk
[    5.495033] PM: Resume from partition 8:5
[    5.495035] PM: Checking hibernation image.
[    5.495349] PM: Resume from disk failed.
[    5.535295] kjournald starting.  Commit interval 5 seconds
[    5.535308] EXT3-fs: mounted filesystem with ordered data mode.
[    6.108216] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc0000bd1b581]
[   14.011807] udevd version 124 started
[   14.418163] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.455189] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.541209] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   14.541716] ACPI: Lid Switch [LID]
[   14.541765] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   14.569031] ACPI: Power Button (CM) [PBTN]
[   14.569135] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   14.601035] ACPI: Sleep Button (CM) [SBTN]
[   14.601239] ACPI: AC Adapter [AC] (on-line)
[   14.658880] ACPI: Battery Slot [BAT0] (battery present)
[   14.668260] ACPI: WMI: Mapper loaded
[   14.982486] acpi device:32: registered as cooling_device2
[   14.983652] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input7
[   15.009021] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   15.018948] acpi device:37: registered as cooling_device3
[   15.019740] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:34/input/input8
[   15.045021] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   15.045179] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:39/input/input9
[   15.077037] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   15.657363] nvidia: module license 'NVIDIA' taints kernel.
[   15.957957] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.957966] nvidia 0000:01:00.0: setting latency timer to 64
[   15.958089] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   15.966008] Bluetooth: Core ver 2.13
[   15.967862] NET: Registered protocol family 31
[   15.967864] Bluetooth: HCI device and connection manager initialized
[   15.967870] Bluetooth: HCI socket layer initialized
[   16.018935] iTCO_vendor_support: vendor-support=0
[   16.039657] input: PC Speaker as /devices/platform/pcspkr/input/input10
[   16.084539] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   16.084677] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   16.085213] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.153185] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   16.157123] usbcore: registered new interface driver btusb
[   16.232199] sdhci: Secure Digital Host Controller Interface driver
[   16.232202] sdhci: Copyright(c) Pierre Ossman
[   16.263131] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   16.263151] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   16.266490] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   16.385284] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.385306] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.411318] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   16.411321] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   16.428607] Linux video capture interface: v2.00
[   16.445590] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
[   16.481765] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   16.482138] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   16.494616] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input12
[   16.532232] usbcore: registered new interface driver uvcvideo
[   16.532236] USB Video Class driver (v0.1.0)
[   16.535613] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input13
[   16.592330] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.861407] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.861423] iwl3945 0000:0c:00.0: setting latency timer to 64
[   16.861446] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   17.051069] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   17.066854] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.197522] iwl3945 0000:0c:00.0: PCI INT A disabled
[   18.075170] lp: driver loaded but no devices found
[   18.281889] Adding 4096532k swap on /dev/sda5.  Priority:-1 extents:1 across:4096532k
[   18.935549] EXT3 FS on sda7, internal journal
[   19.960058] type=1505 audit(1223664885.089:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4539
[   20.089936] type=1505 audit(1223664885.221:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4546
[   20.090094] type=1505 audit(1223664885.221:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4546
[   20.196838] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by muadnu on 2008-10-10
I just found this (after posting) which I guess might be the problem [http://ubuntuforums.org/showthread.php?t=943229](http://ubuntuforums.org/showthread.php?t=943229), though no one here talks about loud beeps :(.

---

### Post by FuturePilot on 2008-10-10
Most likely not a Nvidia problem.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187")

---

### Post by muadnu on 2008-10-11
I solved it, and I still think the problem was with Nvidia. The problem actually must have been that the upgrades installed a new kernel, different from the one for which the drivers were installed. I logged in in recover mode (or however it is called), regenerated the xorg.conf file so that I would log in using the Vesa drivers, and then when I logged back in it offered me to activate the Nvidia driver, after which I could log in with Nvidia.

---

### Post by hdhrnova on 2008-10-11
> **muadnu said:**
> I just found this (after posting) which I guess might be the problem [http://ubuntuforums.org/showthread.php?t=943229](http://ubuntuforums.org/showthread.php?t=943229), though no one here talks about loud beeps :(.

well I get the load beep at power up every once in a while. Its very annoying.   8200M GS.   Compaq Presario CQ50-115NR

using 8.10 with latest 2.6.27-7 kernel. 177.80 nvideo drivers.

---

