---
title: "[SOLVED] My Laptop Takes Over Four Minutes To Shut Down (Literally)"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-10-25
I already reported this bug, but as of yet it's not been fixed. I have a Gateway M-7315u laptop with 64-bit Intrepid installed. When I go to shut it down, the shutdown usplash appears as normal, then fails to a black screen with a blinking white cursor. There it sits for 3-4 minutes until my laptop finally agrees to turn off.

I attached my dmesg output, but I don't know if that will help. I'm hoping that this is just something I screwed up and can be fixed, rather than a bug in the final release. Any help is much appreciated. :)

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=826631f1-1619-435e-b54c-ec75035ac135 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bb6b1000 (usable)
[    0.000000]  BIOS-e820: 00000000bb6b1000 - 00000000bb6b7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb6b7000 - 00000000bb7c5000 (usable)
[    0.000000]  BIOS-e820: 00000000bb7c5000 - 00000000bb80f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb80f000 - 00000000bb909000 (usable)
[    0.000000]  BIOS-e820: 00000000bb909000 - 00000000bbb0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bbb0f000 - 00000000bbb18000 (usable)
[    0.000000]  BIOS-e820: 00000000bbb18000 - 00000000bbb1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bbb1f000 - 00000000bbb65000 (usable)
[    0.000000]  BIOS-e820: 00000000bbb65000 - 00000000bbb9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbb9f000 - 00000000bbbe3000 (usable)
[    0.000000]  BIOS-e820: 00000000bbbe3000 - 00000000bbbfd000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bbbfd000 - 00000000bbc00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xbbc00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00bbc00000 page 2M
[    0.000000] kernel direct mapping tables up to bbc00000 @ 8000-c000
[    0.000000] last_map_addr: bbc00000 end: bbc00000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ a000-10000
[    0.000000] last_map_addr: 140000000 end: 140000000
[    0.000000] RAMDISK: 377b1000 - 37fef55b
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP 000F72A0, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BBBF582D, 006C (r1 GATEWA SYSTEM   20080723  LTP        0)
[    0.000000] ACPI: FACP BBBE7000, 00F4 (r3 GATEWA SYSTEM   20080723 ALAN        1)
[    0.000000] ACPI: DSDT BBBE8000, 735D (r2 GATEWA SYSTEM   20080723 INTL 20050624)
[    0.000000] ACPI: FACS BBB9EFC0, 0040
[    0.000000] ACPI: HPET BBBFCD86, 0038 (r1 GATEWA SYSTEM   20080723 LOHR       5A)
[    0.000000] ACPI: MCFG BBBFCDBE, 003C (r1 GATEWA SYSTEM   20080723 LOHR       5A)
[    0.000000] ACPI: SLIC BBBFCDFA, 0176 (r1 GATEWA SYSTEM   20080723  LTP        0)
[    0.000000] ACPI: APIC BBBFCF70, 0068 (r1 GATEWA SYSTEM   20080723  LTP        0)
[    0.000000] ACPI: BOOT BBBFCFD8, 0028 (r1 GATEWA SYSTEM   20080723  LTP        1)
[    0.000000] ACPI: SSDT BBBE6000, 0655 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BBBE5000, 0259 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BBBE4000, 020F (r1  PmRef    ApTst     3000 INTL 20050624)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000b000 -  0000000000032fff] pages 28
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b1000 - 0037fef55b]          RAMDISK ==> [00377b1000 - 0037fef55b]
[    0.000000]   #4 [000009d400 - 0000100000]    BIOS reserved ==> [000009d400 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #6 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000f7370] 000f7370
[    0.000000]  [ffffe20000000000-ffffe20004ffffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bb6b1
[    0.000000]     0: 0x000bb6b7 -> 0x000bb7c5
[    0.000000]     0: 0x000bb80f -> 0x000bb909
[    0.000000]     0: 0x000bbb0f -> 0x000bbb18
[    0.000000]     0: 0x000bbb1f -> 0x000bbb65
[    0.000000]     0: 0x000bbb9f -> 0x000bbbe3
[    0.000000]     0: 0x000bbbfd -> 0x000bbc00
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1030380
[    0.000000]   DMA zone: 2107 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 747919 pages, LIFO batch:31
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bb6b1000 - 00000000bb6b7000
[    0.000000] PM: Registered nosave memory: 00000000bb7c5000 - 00000000bb80f000
[    0.000000] PM: Registered nosave memory: 00000000bb909000 - 00000000bbb0f000
[    0.000000] PM: Registered nosave memory: 00000000bbb18000 - 00000000bbb1f000
[    0.000000] PM: Registered nosave memory: 00000000bbb65000 - 00000000bbb9f000
[    0.000000] PM: Registered nosave memory: 00000000bbbe3000 - 00000000bbbfd000
[    0.000000] PM: Registered nosave memory: 00000000bbc00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bbc00000:44400000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1008074
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=826631f1-1619-435e-b54c-ec75035ac135 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1995.200 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3974324k/5242880k available (3112k kernel code, 147196k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.40 BogoMIPS (lpj=7980800)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004560] Mount-cache hash table entries: 256
[    0.004767] Initializing cgroup subsys ns
[    0.004774] Initializing cgroup subsys cpuacct
[    0.004776] Initializing cgroup subsys memory
[    0.004794] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004796] CPU: L2 cache: 1024K
[    0.004799] CPU 0/0 -> Node 0
[    0.004801] CPU: Physical Processor ID: 0
[    0.004802] CPU: Processor Core ID: 0
[    0.004810] CPU0: Thermal monitoring enabled (TM2)
[    0.004812] using mwait in idle threads.
[    0.007067] ACPI: Core revision 20080609
[    0.009715] ACPI: Checking initramfs for custom DSDT
[    0.396471] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.436629] CPU0: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
[    0.436634] Using local APIC timer interrupts.
[    0.440028] APIC timer calibration result 10391729
[    0.440030] Detected 10.391 MHz APIC timer.
[    0.440176] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.40 BogoMIPS (lpj=7980814)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.528360] CPU1: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
[    0.528384] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.532068] Brought up 2 CPUs
[    0.532070] Total of 2 processors activated (7980.80 BogoMIPS).
[    0.532118] CPU0 attaching sched-domain:
[    0.532121]  domain 0: span 0-1 level MC
[    0.532123]   groups: 0 1
[    0.532127]   domain 1: span 0-1 level NODE
[    0.532129]    groups: 0-1
[    0.532134] CPU1 attaching sched-domain:
[    0.532135]  domain 0: span 0-1 level MC
[    0.532137]   groups: 1 0
[    0.532140]   domain 1: span 0-1 level NODE
[    0.532142]    groups: 0-1
[    0.532235] net_namespace: 1552 bytes
[    0.532235] Booting paravirtualized kernel on bare hardware
[    0.532306] Time:  2:49:42  Date: 10/25/08
[    0.532338] NET: Registered protocol family 16
[    0.532359] ACPI: bus type pci registered
[    0.532359] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.532359] PCI: Not using MMCONFIG.
[    0.532359] PCI: Using configuration type 1 for base access
[    0.533157] ACPI: EC: Look up EC in DSDT
[    0.539763] ACPI: BIOS _OSI(Linux) query ignored
[    0.539766] ACPI: DMI System Vendor: Gateway                         
[    0.539768] ACPI: DMI Product Name: M-7315U                         
[    0.539769] ACPI: DMI Product Version: Rev 1                   
[    0.539771] ACPI: DMI Board Name:         
[    0.539772] ACPI: DMI BIOS Vendor: Phoenix Technologies LTD
[    0.539774] ACPI: DMI BIOS Date: 07/23/2008
[    0.539775] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[    0.539777] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[    0.540861] ACPI: Interpreter enabled
[    0.540864] ACPI: (supports S0 S3 S4 S5)
[    0.540874] ACPI: Using IOAPIC for interrupt routing
[    0.540874] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.540874] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.554358] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.554388] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.580210] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.580210] ACPI: EC: driver started in interrupt mode
[    0.580230] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.580230] PCI: 0000:00:02.0 reg 10 64bit mmio: [f0000000, f03fffff]
[    0.580230] PCI: 0000:00:02.0 reg 18 32bit mmio: [d0000000, dfffffff]
[    0.580230] PCI: 0000:00:02.0 reg 20 io port: [1800, 1807]
[    0.580230] PCI: 0000:00:02.1 reg 10 64bit mmio: [f0400000, f04fffff]
[    0.580284] PCI: 0000:00:1a.0 reg 20 io port: [1820, 183f]
[    0.580365] PCI: 0000:00:1a.1 reg 20 io port: [1840, 185f]
[    0.580446] PCI: 0000:00:1a.2 reg 20 io port: [1860, 187f]
[    0.580527] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f0b04800, f0b04bff]
[    0.580583] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.580588] pci 0000:00:1a.7: PME# disabled
[    0.580631] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f0900000, f0903fff]
[    0.580681] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.580686] pci 0000:00:1b.0: PME# disabled
[    0.580751] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.580755] pci 0000:00:1c.0: PME# disabled
[    0.580822] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.580826] pci 0000:00:1c.2: PME# disabled
[    0.580893] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.580897] pci 0000:00:1c.5: PME# disabled
[    0.580958] PCI: 0000:00:1d.0 reg 20 io port: [1880, 189f]
[    0.581040] PCI: 0000:00:1d.1 reg 20 io port: [18a0, 18bf]
[    0.581121] PCI: 0000:00:1d.2 reg 20 io port: [18c0, 18df]
[    0.581205] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f0b04c00, f0b04fff]
[    0.581265] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.581270] pci 0000:00:1d.7: PME# disabled
[    0.581471] PCI: 0000:00:1f.2 reg 10 io port: [1818, 181f]
[    0.581478] PCI: 0000:00:1f.2 reg 14 io port: [180c, 180f]
[    0.581485] PCI: 0000:00:1f.2 reg 18 io port: [1810, 1817]
[    0.581492] PCI: 0000:00:1f.2 reg 1c io port: [1808, 180b]
[    0.581499] PCI: 0000:00:1f.2 reg 20 io port: [18e0, 18ff]
[    0.581506] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f0b04000, f0b047ff]
[    0.581538] pci 0000:00:1f.2: PME# supported from D3hot
[    0.581542] pci 0000:00:1f.2: PME# disabled
[    0.581567] PCI: 0000:00:1f.3 reg 10 64bit mmio: [0, ff]
[    0.581585] PCI: 0000:00:1f.3 reg 20 io port: [1c00, 1c1f]
[    0.581680] PCI: 0000:02:00.0 reg 10 64bit mmio: [f0500000, f050ffff]
[    0.581755] pci 0000:02:00.0: supports D1
[    0.581757] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.581763] pci 0000:02:00.0: PME# disabled
[    0.581811] PCI: bridge 0000:00:1c.0 io port: [2000, 2fff]
[    0.581815] PCI: bridge 0000:00:1c.0 32bit mmio: [f0500000, f05fffff]
[    0.581822] PCI: bridge 0000:00:1c.0 64bit mmio pref: [f0c00000, f0cfffff]
[    0.581879] PCI: bridge 0000:00:1c.2 io port: [3000, 3fff]
[    0.581883] PCI: bridge 0000:00:1c.2 32bit mmio: [f0600000, f06fffff]
[    0.581890] PCI: bridge 0000:00:1c.2 64bit mmio pref: [f0d00000, f0dfffff]
[    0.582306] PCI: 0000:06:00.0 reg 10 64bit mmio: [f0700000, f0703fff]
[    0.582359] PCI: 0000:06:00.0 reg 18 io port: [4000, 40ff]
[    0.584388] pci 0000:06:00.0: supports D1
[    0.584389] pci 0000:06:00.0: supports D2
[    0.584391] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.584413] pci 0000:06:00.0: PME# disabled
[    0.584460] PCI: bridge 0000:00:1c.5 io port: [4000, 4fff]
[    0.584465] PCI: bridge 0000:00:1c.5 32bit mmio: [f0700000, f07fffff]
[    0.584525] PCI: 0000:07:09.0 reg 10 32bit mmio: [f0800000, f0800fff]
[    0.584577] pci 0000:07:09.0: supports D1
[    0.584578] pci 0000:07:09.0: supports D2
[    0.584580] pci 0000:07:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.584585] pci 0000:07:09.0: PME# disabled
[    0.584621] PCI: 0000:07:09.2 reg 10 32bit mmio: [f0801000, f08010ff]
[    0.584674] pci 0000:07:09.2: supports D1
[    0.584675] pci 0000:07:09.2: supports D2
[    0.584677] pci 0000:07:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.584681] pci 0000:07:09.2: PME# disabled
[    0.584723] pci 0000:00:1e.0: transparent bridge
[    0.584731] PCI: bridge 0000:00:1e.0 32bit mmio: [f0800000, f08fffff]
[    0.584769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.585112] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.585274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.585430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.585581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.600778] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.600778] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.600778] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.600778] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.600778] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.600900] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.601045] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.601190] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.601265] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.601265] pnp: PnP ACPI init
[    0.601265] ACPI: bus type pnp registered
[    0.604541] pnp: PnP ACPI: found 10 devices
[    0.604541] ACPI: ACPI bus type pnp unregistered
[    0.604804] PCI: Using ACPI for IRQ routing
[    0.632060] NET: Registered protocol family 8
[    0.632062] NET: Registered protocol family 20
[    0.632091] NetLabel: Initializing
[    0.632091] NetLabel:  domain hash size = 128
[    0.632091] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.632091] NetLabel:  unlabeled traffic allowed by default
[    0.632091] PCI-GART: No AMD northbridge found.
[    0.632091] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.632091] hpet0: 4 64-bit timers, 14318180 Hz
[    0.634420] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.634422]    actual entries 65586
[    0.634539] AppArmor: AppArmor Filesystem Enabled
[    0.634565] ACPI: RTC can wake from S4
[    0.636044] Switched to high resolution mode on CPU 0
[    0.636413] Switched to high resolution mode on CPU 1
[    0.649030] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.649040] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.649042] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.649045] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.649048] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.649050] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.649052] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.649054] system 00:05: ioport range 0x164e-0x164f has been reserved
[    0.649057] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.649066] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.649069] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.649071] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.649074] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.649076] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.649078] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.649081] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.649083] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.654207] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.654210] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.654216] pci 0000:00:1c.0:   MEM window: 0xf0500000-0xf05fffff
[    0.654221] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0c00000-0x000000f0cfffff
[    0.654228] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.654231] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
[    0.654237] pci 0000:00:1c.2:   MEM window: 0xf0600000-0xf06fffff
[    0.654241] pci 0000:00:1c.2:   PREFETCH window: 0x000000f0d00000-0x000000f0dfffff
[    0.654248] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
[    0.654251] pci 0000:00:1c.5:   IO window: 0x4000-0x4fff
[    0.654256] pci 0000:00:1c.5:   MEM window: 0xf0700000-0xf07fffff
[    0.654261] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.654268] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.654270] pci 0000:00:1e.0:   IO window: disabled
[    0.654275] pci 0000:00:1e.0:   MEM window: 0xf0800000-0xf08fffff
[    0.654280] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.654303] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.654308] pci 0000:00:1c.0: setting latency timer to 64
[    0.654317] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.654322] pci 0000:00:1c.2: setting latency timer to 64
[    0.654330] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.654335] pci 0000:00:1c.5: setting latency timer to 64
[    0.654343] pci 0000:00:1e.0: setting latency timer to 64
[    0.654346] bus: 00 index 0 io port: [0, ffff]
[    0.654348] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.654350] bus: 02 index 0 io port: [2000, 2fff]
[    0.654352] bus: 02 index 1 mmio: [f0500000, f05fffff]
[    0.654353] bus: 02 index 2 mmio: [f0c00000, f0cfffff]
[    0.654355] bus: 02 index 3 mmio: [0, 0]
[    0.654357] bus: 04 index 0 io port: [3000, 3fff]
[    0.654358] bus: 04 index 1 mmio: [f0600000, f06fffff]
[    0.654360] bus: 04 index 2 mmio: [f0d00000, f0dfffff]
[    0.654362] bus: 04 index 3 mmio: [0, 0]
[    0.654363] bus: 06 index 0 io port: [4000, 4fff]
[    0.654365] bus: 06 index 1 mmio: [f0700000, f07fffff]
[    0.654366] bus: 06 index 2 mmio: [0, 0]
[    0.654368] bus: 06 index 3 mmio: [0, 0]
[    0.654369] bus: 07 index 0 mmio: [0, 0]
[    0.654371] bus: 07 index 1 mmio: [f0800000, f08fffff]
[    0.654373] bus: 07 index 2 mmio: [0, 0]
[    0.654374] bus: 07 index 3 io port: [0, ffff]
[    0.654376] bus: 07 index 4 mmio: [0, ffffffffffffffff]
[    0.654389] NET: Registered protocol family 2
[    0.693172] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.694717] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.699800] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.700415] TCP: Hash tables configured (established 524288 bind 65536)
[    0.700418] TCP reno registered
[    0.709127] NET: Registered protocol family 1
[    0.709252] checking if image is initramfs... it is
[    1.485996] Freeing initrd memory: 8441k freed
[    1.491101] Simple Boot Flag at 0x36 set to 0x1
[    1.492105] audit: initializing netlink socket (disabled)
[    1.492120] type=2000 audit(1224902982.492:1): initialized
[    1.498247] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.500664] VFS: Disk quotas dquot_6.5.1
[    1.500753] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.500857] msgmni has been set to 7778
[    1.500981] io scheduler noop registered
[    1.500983] io scheduler anticipatory registered
[    1.500985] io scheduler deadline registered
[    1.501114] io scheduler cfq registered (default)
[    1.501128] pci 0000:00:02.0: Boot video device
[    1.501395] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.501439] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.501488] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.501532] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.501571] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.501674] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.501717] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.501760] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.501808] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.501851] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.501957] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.502000] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.502043] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.502082] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.502120] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.537155] hpet_resources: 0xfed00000 is busy
[    1.537245] Linux agpgart interface v0.103
[    1.537250] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.539476] brd: module loaded
[    1.539550] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.539678] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.542533] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.545212] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.545218] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.545220] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.545222] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.545224] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.565172] mice: PS/2 mouse device common for all mice
[    1.565320] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.565350] rtc0: alarms up to one month, y3k, hpet irqs
[    1.565387] cpuidle: using governor ladder
[    1.565389] cpuidle: using governor menu
[    1.565751] TCP cubic registered
[    1.565987] registered taskstats version 1
[    1.566110]   Magic number: 12:898:814
[    1.566188] tty ptys8: hash matches
[    1.566196] tty ptypb: hash matches
[    1.566216] pci 0000:00:1a.1: hash matches
[    1.566265] rtc_cmos 00:06: setting system clock to 2008-10-25 02:49:43 UTC (1224902983)
[    1.566267] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.566269] EDD information not available.
[    1.566337] Freeing unused kernel memory: 536k freed
[    1.566531] Write protecting the kernel read-only data: 4348k
[    1.603045] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.696104] fuse init (API version 7.9)
[    1.760746] ACPI: SSDT BBB1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.761278] ACPI: SSDT BBB18620, 0549 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.764061] Monitor-Mwait will be used to enter C-1 state
[    1.764065] Monitor-Mwait will be used to enter C-2 state
[    1.768101] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.768164] processor ACPI0007:00: registered as cooling_device0
[    1.768169] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.768723] ACPI: SSDT BBB19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.769202] ACPI: SSDT BBB19F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.776004] Marking TSC unstable due to TSC halts in idle
[    1.920265] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.920331] processor ACPI0007:01: registered as cooling_device1
[    1.920335] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.928170] thermal LNXTHERM:01: registered as thermal_zone0
[    1.936139] ACPI: Thermal Zone [TZ00] (58 C)
[    2.188132] usbcore: registered new interface driver usbfs
[    2.188161] usbcore: registered new interface driver hub
[    2.192154] usbcore: registered new device driver usb
[    2.198095] USB Universal Host Controller Interface driver v3.0
[    2.198146] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.198155] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.198159] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.198212] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.198252] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    2.198397] usb usb1: configuration #1 chosen from 1 choice
[    2.198427] hub 1-0:1.0: USB hub found
[    2.198434] hub 1-0:1.0: 2 ports detected
[    2.270262] No dock devices found.
[    2.288091] SCSI subsystem initialized
[    2.300857] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.300870] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.300875] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.300925] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.300973] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    2.301133] usb usb2: configuration #1 chosen from 1 choice
[    2.301167] hub 2-0:1.0: USB hub found
[    2.301177] hub 2-0:1.0: 2 ports detected
[    2.306845] libata version 3.00 loaded.
[    2.508302] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.508313] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.508317] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.508351] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.508391] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    2.508498] usb usb3: configuration #1 chosen from 1 choice
[    2.508526] hub 3-0:1.0: USB hub found
[    2.508534] hub 3-0:1.0: 2 ports detected
[    2.612392] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.612414] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.612418] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.612457] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.616384] ehci_hcd 0000:00:1a.7: debug port 1
[    2.616392] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.616402] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf0b04800
[    2.633028] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.633219] usb usb4: configuration #1 chosen from 1 choice
[    2.633249] hub 4-0:1.0: USB hub found
[    2.633259] hub 4-0:1.0: 6 ports detected
[    2.840351] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.840362] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.840366] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.840399] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.840442] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    2.840557] usb usb5: configuration #1 chosen from 1 choice
[    2.840588] hub 5-0:1.0: USB hub found
[    2.840597] hub 5-0:1.0: 2 ports detected
[    2.952053] usb 4-3: new high speed USB device using ehci_hcd and address 2
[    3.000042] Clocksource tsc unstable (delta = -157117702 ns)
[    3.048295] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.048304] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.048308] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.048336] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.048370] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    3.048472] usb usb6: configuration #1 chosen from 1 choice
[    3.048501] hub 6-0:1.0: USB hub found
[    3.048508] hub 6-0:1.0: 2 ports detected
[    3.097680] usb 4-3: configuration #1 chosen from 1 choice
[    3.153277] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.153288] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.153292] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.153330] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.153370] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    3.153497] usb usb7: configuration #1 chosen from 1 choice
[    3.153524] hub 7-0:1.0: USB hub found
[    3.153532] hub 7-0:1.0: 2 ports detected
[    3.257457] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.257476] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.257479] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.257522] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.261442] ehci_hcd 0000:00:1d.7: debug port 1
[    3.261448] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.261456] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0b04c00
[    3.277032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.277167] usb usb8: configuration #1 chosen from 1 choice
[    3.277195] hub 8-0:1.0: USB hub found
[    3.277205] hub 8-0:1.0: 6 ports detected
[    3.486850] sky2 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.486886] sky2 0000:06:00.0: setting latency timer to 64
[    3.486973] sky2 0000:06:00.0: v1.22 addr 0xf0700000 irq 17 Yukon-2 FE+ rev 0
[    3.487789] ahci 0000:00:1f.2: version 3.0
[    3.487803] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.487938] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    3.487941] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pmp pio slum part 
[    3.487947] ahci 0000:00:1f.2: setting latency timer to 64
[    3.488631] sky2 eth0: addr 00:e0:b8:fc:b4:7d
[    3.488963] scsi0 : ahci
[    3.489758] scsi1 : ahci
[    3.489862] scsi2 : ahci
[    3.489944] scsi3 : ahci
[    3.490019] scsi4 : ahci
[    3.490101] scsi5 : ahci
[    3.490273] ata1: SATA max UDMA/133 abar m2048@0xf0b04000 port 0xf0b04100 irq 2299
[    3.490277] ata2: SATA max UDMA/133 abar m2048@0xf0b04000 port 0xf0b04180 irq 2299
[    3.490279] ata3: DUMMY
[    3.490280] ata4: DUMMY
[    3.490283] ata5: SATA max UDMA/133 abar m2048@0xf0b04000 port 0xf0b04300 irq 2299
[    3.490286] ata6: SATA max UDMA/133 abar m2048@0xf0b04000 port 0xf0b04380 irq 2299
[    3.864055] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    3.972047] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.973085] ata1.00: _GTF unexpected object type 0x1
[    3.973263] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC31P, max UDMA/133
[    3.973265] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.974484] ata1.00: _GTF unexpected object type 0x1
[    3.974654] ata1.00: configured for UDMA/133
[    4.045247] usb 5-2: configuration #1 chosen from 1 choice
[    4.059886] usbcore: registered new interface driver hiddev
[    4.111401] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input2
[    4.120237] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:1d.0-2
[    4.120260] usbcore: registered new interface driver usbhid
[    4.120263] usbhid: v2.6:USB HID core driver
[    4.456072] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.469289] ata2.00: _GTF unexpected object type 0x1
[    4.469894] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SX07, max UDMA/100, ATAPI AN
[    4.483711] ata2.00: _GTF unexpected object type 0x1
[    4.484320] ata2.00: configured for UDMA/100
[    4.501318] ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0
[    4.501322] ata2: irq_stat 0x40000008
[    4.804074] ata5: SATA link down (SStatus 0 SControl 300)
[    5.125080] ata6: SATA link down (SStatus 0 SControl 300)
[    5.125216] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[    5.127083] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SX07 PQ: 0 ANSI: 5
[    5.141596] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.141647] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.154951] Driver 'sr' needs updating - please use bus_type methods
[    5.160511] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.160517] Uniform CD-ROM driver Revision: 3.20
[    5.160625] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.162814] Driver 'sd' needs updating - please use bus_type methods
[    5.165677] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.165756] sd 0:0:0:0: [sda] Write Protect is off
[    5.165759] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.165809] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.165910] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.165926] sd 0:0:0:0: [sda] Write Protect is off
[    5.165929] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.165959] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.165963]  sda: sda1 sda2 sda3 sda4
[    5.207562] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.597343] PM: Starting manual resume from disk
[    5.597346] PM: Resume from partition 8:4
[    5.597348] PM: Checking hibernation image.
[    5.597545] PM: Resume from disk failed.
[    5.655739] kjournald starting.  Commit interval 5 seconds
[    5.655778] EXT3-fs: mounted filesystem with ordered data mode.
[   14.195776] udevd version 124 started
[   14.659554] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.674619] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.801211] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   14.821060] ACPI: Power Button (FF) [PWRF]
[   14.821249] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   14.822425] ACPI: Lid Switch [LID]
[   14.822586] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   14.844041] ACPI: Power Button (CM) [PWRB]
[   14.844175] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   14.863900] agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset
[   14.864275] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[   14.875876] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.880036] ACPI: Sleep Button (CM) [SLPB]
[   14.903041] ACPI: AC Adapter [ACAD] (on-line)
[   15.033306] ACPI: Battery Slot [BAT1] (battery present)
[   15.033481] ACPI: WMI: Mapper loaded
[   15.172677] acpi device:06: registered as cooling_device2
[   15.173214] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input7
[   15.204041] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.463860] sdhci: Secure Digital Host Controller Interface driver
[   15.463863] sdhci: Copyright(c) Pierre Ossman
[   15.505542] sdhci-pci 0000:07:09.2: SDHCI controller found [1217:7120] (rev 2)
[   15.505561] sdhci-pci 0000:07:09.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.505585] mmc0: Unknown controller version (2). You may experience problems.
[   15.505657] mmc0: SDHCI controller on PCI [0000:07:09.2] using DMA
[   15.704041] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   15.889597] ath9k: 0.1
[   15.890307] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.890325] ath9k 0000:02:00.0: setting latency timer to 64
[   16.322986] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.353751] Linux video capture interface: v2.00
[   16.554219] uvcvideo: Found UVC 1.00 device Gateway USB 2.0 Webcam (04f2:b027)
[   16.556592] input: Gateway USB 2.0 Webcam as /devices/pci0000:00/0000:00:1a.7/usb4/4-3/4-3:1.0/input/input9
[   16.583370] usbcore: registered new interface driver uvcvideo
[   16.583374] USB Video Class driver (v0.1.0)
[   16.625186] phy0: Atheros 9280: mem=0xffffc200110a0000, irq=16
[   16.973886] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   16.973902] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.973939] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.089747] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04711/0x0
[   17.136705] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   19.185150] lp: driver loaded but no devices found
[   19.374738] Adding 4859652k swap on /dev/sda4.  Priority:-1 extents:1 across:4859652k
[  375.537725] EXT3 FS on sda3, internal journal
[  376.409272] type=1505 audit(1224917758.409:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=32377
[  376.561390] type=1505 audit(1224917758.561:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=32389
[  376.561617] type=1505 audit(1224917758.561:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=32389
[  376.658700] ip_tables: (C) 2000-2006 Netfilter Core Team
[  378.072632] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  378.158040] ppdev: user-space parallel port driver
[  379.322042] NET: Registered protocol family 10
[  379.322895] lo: Disabled Privacy Extensions
[  380.331412] Bluetooth: Core ver 2.13
[  380.333481] NET: Registered protocol family 31
[  380.333490] Bluetooth: HCI device and connection manager initialized
[  380.333496] Bluetooth: HCI socket layer initialized
[  380.352541] Bluetooth: L2CAP ver 2.11
[  380.352550] Bluetooth: L2CAP socket layer initialized
[  380.371314] Bluetooth: SCO (Voice Link) ver 0.6
[  380.371323] Bluetooth: SCO socket layer initialized
[  380.396534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  380.396544] Bluetooth: BNEP filters: protocol multicast
[  380.442832] Bridge firewalling registered
[  380.443182] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  380.578648] Bluetooth: RFCOMM socket layer initialized
[  380.578674] Bluetooth: RFCOMM TTY layer initialized
[  380.578678] Bluetooth: RFCOMM ver 1.10
[  384.060887] [drm] Initialized drm 1.1.0 20060810
[  384.088820] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  384.088836] pci 0000:00:02.0: setting latency timer to 64
[  384.092768] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  384.195290] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[  384.764527] sky2 eth0: enabling interface
[  384.770594] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  384.815282] ForceXPAon: 0
[  384.843026] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  385.069023] ForceXPAon: 0
[  385.070781] NET: Registered protocol family 17
[  385.164900] set status page addr 0x03fff000
[  385.255099] ForceXPAon: 0
[  385.443161] ForceXPAon: 0
[  385.691074] ForceXPAon: 0
[  405.247109] ForceXPAon: 0
[  405.491085] ForceXPAon: 0
[  405.675111] ForceXPAon: 0
[  405.919093] ForceXPAon: 0
[  408.431507] canberra-gtk-pl[4028]: segfault at 101c43690 ip 00007fea8f85a6ec sp 0000000040a75bd0 error 6 in libc-2.8.90.so[7fea8f7de000+169000]
[  411.515038] ForceXPAon: 0
[  411.908888] ForceXPAon: 0
[  411.921012] CPU0 attaching NULL sched-domain.
[  411.921025] CPU1 attaching NULL sched-domain.
[  411.952091] CPU0 attaching sched-domain:
[  411.952098]  domain 0: span 0-1 level MC
[  411.952101]   groups: 0 1
[  411.952105]   domain 1: span 0-1 level NODE
[  411.952107]    groups: 0-1
[  411.952111] CPU1 attaching sched-domain:
[  411.952113]  domain 0: span 0-1 level MC
[  411.952114]   groups: 1 0
[  411.952117]   domain 1: span 0-1 level NODE
[  411.952119]    groups: 0-1
[  412.184861] ForceXPAon: 0
[  412.196116] ForceXPAon: 0
[  412.383075] ForceXPAon: 0
[  412.631069] ForceXPAon: 0
[  412.639998] ForceXPAon: 0
[  412.642311] wlan0: authenticate with AP 00:18:4d:96:91:32
[  412.840069] wlan0: authenticate with AP 00:18:4d:96:91:32
[  413.044055] wlan0: authenticate with AP 00:18:4d:96:91:32
[  413.244063] wlan0: authentication with AP 00:18:4d:96:91:32 timed out
[  422.887957] ForceXPAon: 0
[  422.899195] ForceXPAon: 0
[  423.150085] ForceXPAon: 0
[  423.342085] ForceXPAon: 0
[  423.590091] ForceXPAon: 0
[  423.599088] ForceXPAon: 0
[  423.733530] ForceXPAon: 0
[  423.735139] wlan0: authenticate with AP 00:18:4d:96:91:32
[  423.735295] wlan0: authenticate with AP 00:18:4d:96:91:32
[  423.737695] wlan0: authenticated
[  423.737703] wlan0: associate with AP 00:18:4d:96:91:32
[  423.740316] wlan0: deauthenticated
[  424.740061] wlan0: authenticate with AP 00:18:4d:96:91:32
[  424.743473] wlan0: authenticated
[  424.743495] wlan0: associate with AP 00:18:4d:96:91:32
[  424.746555] wlan0: RX AssocResp from 00:18:4d:96:91:32 (capab=0x431 status=0 aid=1)
[  424.746572] wlan0: associated
[  424.895705] ForceXPAon: 0
[  424.897989] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  435.255060] ForceXPAon: 0
[  435.499082] ForceXPAon: 0
[  435.687097] ForceXPAon: 0
[  435.816039] wlan0: no IPv6 routers present
[  435.931123] ForceXPAon: 0
[  475.259085] ForceXPAon: 0
[  475.511065] ForceXPAon: 0
[  475.703107] ForceXPAon: 0
[  475.960066] ForceXPAon: 0
[  478.052076] type=1503 audit(1224917860.053:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/13538/net/" pid=13538 profile="/usr/sbin/cupsd"
[  479.265147] type=1503 audit(1224917861.265:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/13705/net/" pid=13705 profile="/usr/sbin/cupsd"
[  479.268629] type=1503 audit(1224917861.269:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=13705 profile="/usr/sbin/cupsd"
[  479.271361] type=1503 audit(1224917861.269:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=13705 profile="/usr/sbin/cupsd"
[  479.274288] type=1503 audit(1224917861.273:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=13705 profile="/usr/sbin/cupsd"
[  479.277173] type=1503 audit(1224917861.277:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=13705 profile="/usr/sbin/cupsd"
[  479.279934] type=1503 audit(1224917861.277:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=13705 profile="/usr/sbin/cupsd"
[  479.282750] type=1503 audit(1224917861.281:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=13705 profile="/usr/sbin/cupsd"
[  479.285582] type=1503 audit(1224917861.285:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=13705 profile="/usr/sbin/cupsd"
[  535.262053] ForceXPAon: 0
[  535.506126] ForceXPAon: 0
[  535.690083] ForceXPAon: 0
[  535.934164] ForceXPAon: 0
[  615.270057] ForceXPAon: 0
[  615.514084] ForceXPAon: 0
[  615.702098] ForceXPAon: 0
[  615.946148] ForceXPAon: 0
```

---

### Post by jlacroix on 2008-10-25
I installed Intrepid on a flash drive, and I did not have this problem. It must be something specific to my install. Does anyone know what may be wrong on my set up to cause this? It seems that acpi is to blame but I can't be certain.

---

### Post by jongkind on 2008-10-25
These problems are probably related to problems with the network manager, see:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995")

The solution that worked for me was written by:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/27]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/27")

(in that solution wlan0 can be substituted by e.g. eth0, depending on your network interface)

---

### Post by jlacroix on 2008-10-26
Thank you!!! That fixed the problem for me. You're my hero!!!

---

### Post by hikaricore on 2008-10-26
> **jongkind said:**
> These problems are probably related to problems with the network manager, see:
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/274995]("https://bugs.launchpad.net/ubuntu/+s...er/+bug/274995")

The solution that worked for me was written by:
[https://bugs.launchpad.net/ubuntu/+s...95/comments/33]("https://bugs.launchpad.net/ubuntu/+s...95/comments/33")

(in that solution wlan0 can be substituted by e.g. eth0, depending on your network interface)

You may want to fix your links as they are truncated in bother the url and the text fields. :p

I believe these were the links you meant to post?
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/33](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/33)

---

### Post by jongkind on 2008-10-26
> **hikaricore said:**
> You may want to fix your links as they are truncated in bother the url and the text fields. :p

I believe these were the links you meant to post?
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/33](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/33)

Thanks, you're right.

---

### Post by Jim March on 2008-10-26
A reminder: if Network Manager is giving you fits, swap in Wicd - version 1.5.3 is working fine under Intrepid.

Wicd doesn't have as much "potential" as NM7 once the latter has the bugs worked out - Wicd has no cellmodem support even attempted, and isn't near as advanced in the network sharing department.  But it does have a good user interface with scripts that can fire up on contact with a given network (wired or wireless).

Cellmodem support under Wicd means using WVdial scripts.

---

