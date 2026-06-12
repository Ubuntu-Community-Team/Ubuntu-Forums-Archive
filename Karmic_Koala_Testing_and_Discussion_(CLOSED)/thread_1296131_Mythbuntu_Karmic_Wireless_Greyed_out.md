---
title: "Mythbuntu Karmic Wireless Greyed out"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by molder on 2009-10-20
I can not get my Broadcom 4303 wireless card to work.  It make be time to upgrade to n but it work flawless in my jaunty setup.  I installed the fwcutter tool through jockey, the wireless is disabled in network manager.  As you can see from my iwconfig and dmesg output, the wireless adaptor is working.  Guess the next step is wicd


iwconfig output
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```lspci output
```
andrew@MythTV-Zeus:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
04:03.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:03.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
04:03.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
04:04.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CDFFF write-protect
[    0.000000]   CE000-EFFFF uncachable
[    0.000000]   F0000-F7FFF write-through
[    0.000000]   F8000-F8FFF uncachable
[    0.000000]   F9000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0D8000000 mask FF8000000 write-combining
[    0.000000]   2 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 378a6000 - 37fefc2d
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff6c2d
[    0.000000] Move RAMDISK from 00000000378a6000 - 0000000037fefc2c to 008ad000 - 00ff6c2c
[    0.000000] ACPI: RSDP 000f7f50 00014 (v00 P4M900)
[    0.000000] ACPI: RSDT 7fee3000 00034 (v01 P4M900 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 7fee3080 00074 (v01 P4M900 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 7fee3100 062D0 (v01 P4M900 AWRDACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 7fee0000 00040
[    0.000000] ACPI: HPET 7fee94c0 00038 (v01 P4M900 AWRDACPI 42302E31 AWRD 00000098)
[    0.000000] ACPI: MCFG 7fee9500 0003C (v01 P4M900 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 7fee9400 00090 (v01 P4M900 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac0d2]              BRK ==> [00008a9000 - 00008ac0d2]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0000ff6c2d]      NEW RAMDISK ==> [00008ad000 - 0000ff6c2d]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f3d60] f3d60
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523887
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294356 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 5, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfe800000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 48
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:60100000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c200a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=d16d96da-8947-4154-a30d-57278a58a099 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
[    0.000000] Memory: 2051668k/2096000k available (4565k kernel code, 43020k reserved, 2143k data, 540k init, 1186696k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:848
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3098.832 MHz processor.
[    0.002368] Console: colour VGA+ 80x25
[    0.002373] console [tty0] enabled
[    0.002500] hpet clockevent registered
[    0.002505] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002512] Calibrating delay loop (skipped), value calculated using timer frequency.. 6197.66 BogoMIPS (lpj=12395328)
[    0.002534] Security Framework initialized
[    0.002556] AppArmor: AppArmor initialized
[    0.002566] Mount-cache hash table entries: 512
[    0.002719] Initializing cgroup subsys ns
[    0.002726] Initializing cgroup subsys cpuacct
[    0.002732] Initializing cgroup subsys memory
[    0.002741] Initializing cgroup subsys freezer
[    0.002745] Initializing cgroup subsys net_cls
[    0.002763] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.002768] CPU: L2 cache: 512K
[    0.002772] CPU: Physical Processor ID: 0
[    0.002775] CPU: Processor Core ID: 0
[    0.002780] mce: CPU supports 4 MCE banks
[    0.002791] CPU0: Thermal monitoring enabled (TM1)
[    0.002802] Performance Counters: no PMU driver, software counters only.
[    0.002810] Checking 'hlt' instruction... OK.
[    0.018794] ACPI: Core revision 20090521
[    0.036402] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076101] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6197.06 BogoMIPS (lpj=12394134)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 4 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.164779] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[    0.164802] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168032] Brought up 2 CPUs
[    0.168038] Total of 2 processors activated (12394.73 BogoMIPS).
[    0.168107] CPU0 attaching sched-domain:
[    0.168112]  domain 0: span 0-1 level SIBLING
[    0.168116]   groups: 0 1
[    0.168126] CPU1 attaching sched-domain:
[    0.168129]  domain 0: span 0-1 level SIBLING
[    0.168134]   groups: 1 0
[    0.168229] Booting paravirtualized kernel on bare hardware
[    0.168265] regulator: core version 0.5
[    0.168265] Time: 13:31:49  Date: 10/20/09
[    0.168265] NET: Registered protocol family 16
[    0.168290] EISA bus registered
[    0.168303] ACPI: bus type pci registered
[    0.168392] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168396] PCI: MCFG area at e0000000 reserved in E820
[    0.168399] PCI: Using MMCONFIG for extended config space
[    0.168403] PCI: Using configuration type 1 for base access
[    0.169929] bio: create slab <bio-0> at 0
[    0.173237] ACPI: EC: Look up EC in DSDT
[    0.186474] ACPI: Interpreter enabled
[    0.186482] ACPI: (supports S0 S1 S4 S5)
[    0.186519] ACPI: Using IOAPIC for interrupt routing
[    0.196803] ACPI: No dock devices found.
[    0.197554] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.197622] pci 0000:00:00.0: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.198187] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.198193] pci 0000:00:02.0: PME# disabled
[    0.198275] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.198281] pci 0000:00:03.0: PME# disabled
[    0.198361] pci 0000:00:0f.0: reg 10 io port: [0xfc00-0xfc07]
[    0.198370] pci 0000:00:0f.0: reg 14 io port: [0xf800-0xf803]
[    0.198379] pci 0000:00:0f.0: reg 18 io port: [0xf400-0xf407]
[    0.198388] pci 0000:00:0f.0: reg 1c io port: [0xf000-0xf003]
[    0.198397] pci 0000:00:0f.0: reg 20 io port: [0xec00-0xec0f]
[    0.198406] pci 0000:00:0f.0: reg 24 io port: [0xe800-0xe8ff]
[    0.198490] pci 0000:00:0f.1: reg 20 io port: [0xe400-0xe40f]
[    0.198587] pci 0000:00:10.0: reg 20 io port: [0xe000-0xe01f]
[    0.198618] pci 0000:00:10.0: supports D1 D2
[    0.198622] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198628] pci 0000:00:10.0: PME# disabled
[    0.198688] pci 0000:00:10.1: reg 20 io port: [0xdc00-0xdc1f]
[    0.198719] pci 0000:00:10.1: supports D1 D2
[    0.198722] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198728] pci 0000:00:10.1: PME# disabled
[    0.198786] pci 0000:00:10.2: reg 20 io port: [0xd800-0xd81f]
[    0.198817] pci 0000:00:10.2: supports D1 D2
[    0.198820] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198826] pci 0000:00:10.2: PME# disabled
[    0.198883] pci 0000:00:10.3: reg 20 io port: [0xd400-0xd41f]
[    0.198914] pci 0000:00:10.3: supports D1 D2
[    0.198918] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198924] pci 0000:00:10.3: PME# disabled
[    0.198962] pci 0000:00:10.4: reg 10 32bit mmio: [0xfdfff000-0xfdfff0ff]
[    0.199012] pci 0000:00:10.4: supports D1 D2
[    0.199016] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199022] pci 0000:00:10.4: PME# disabled
[    0.199222] pci 0000:00:12.0: reg 10 io port: [0xd000-0xd0ff]
[    0.199231] pci 0000:00:12.0: reg 14 32bit mmio: [0xfdffe000-0xfdffe0ff]
[    0.199277] pci 0000:00:12.0: supports D1 D2
[    0.199281] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199286] pci 0000:00:12.0: PME# disabled
[    0.199504] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.199510] pci 0000:00:01.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.199517] pci 0000:00:01.0: bridge 32bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.199561] pci 0000:02:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
[    0.199575] pci 0000:02:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.199589] pci 0000:02:00.0: reg 1c 64bit mmio: [0xf4000000-0xf5ffffff]
[    0.199598] pci 0000:02:00.0: reg 24 io port: [0xbc00-0xbc7f]
[    0.199607] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.199703] pci 0000:00:02.0: bridge io port: [0xb000-0xbfff]
[    0.199708] pci 0000:00:02.0: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.199717] pci 0000:00:02.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.199775] pci 0000:00:03.0: bridge io port: [0xa000-0xafff]
[    0.199781] pci 0000:00:03.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.199790] pci 0000:00:03.0: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.199844] pci 0000:04:03.0: reg 10 32bit mmio: [0xf9000000-0xf9ffffff]
[    0.199933] pci 0000:04:03.1: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.200029] pci 0000:04:03.2: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.200119] pci 0000:04:04.0: reg 10 32bit mmio: [0xfcffe000-0xfcffffff]
[    0.200168] pci 0000:04:04.0: supports D1 D2
[    0.200172] pci 0000:04:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.200178] pci 0000:04:04.0: PME# disabled
[    0.200224] pci 0000:00:13.1: transparent bridge
[    0.200229] pci 0000:00:13.1: bridge io port: [0x9000-0x9fff]
[    0.200235] pci 0000:00:13.1: bridge 32bit mmio: [0xf9000000-0xfcffffff]
[    0.200244] pci 0000:00:13.1: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
[    0.200268] pci_bus 0000:00: on NUMA node 0
[    0.200275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.200700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
[    0.200889] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.201074] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
[    0.267455] ACPI: PCI Root Bridge [PCI1] (0000:80)
[    0.267530] pci 0000:80:01.0: reg 10 64bit mmio: [0xbfffc000-0xbfffffff]
[    0.267581] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
[    0.267586] pci 0000:80:01.0: PME# disabled
[    0.267642] pci_bus 0000:80: on NUMA node 0
[    0.267649] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.268425] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.268639] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.268859] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
[    0.269075] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
[    0.269263] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.269444] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.269624] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.269823] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
[    0.270074] SCSI subsystem initialized
[    0.270129] libata version 3.00 loaded.
[    0.270129] usbcore: registered new interface driver usbfs
[    0.270129] usbcore: registered new interface driver hub
[    0.270129] usbcore: registered new device driver usb
[    0.270129] ACPI: WMI: Mapper loaded
[    0.270129] PCI: Using ACPI for IRQ routing
[    0.280012] Bluetooth: Core ver 2.15
[    0.280039] NET: Registered protocol family 31
[    0.280039] Bluetooth: HCI device and connection manager initialized
[    0.280039] Bluetooth: HCI socket layer initialized
[    0.280039] NetLabel: Initializing
[    0.280039] NetLabel:  domain hash size = 128
[    0.280039] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.280052] NetLabel:  unlabeled traffic allowed by default
[    0.280096] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
[    0.280106] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.296016] pnp: PnP ACPI init
[    0.296041] ACPI: bus type pnp registered
[    0.301983] pnp: PnP ACPI: found 18 devices
[    0.301988] ACPI: ACPI bus type pnp unregistered
[    0.301993] PnPBIOS: Disabled by ACPI PNP
[    0.302009] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.302013] system 00:01: ioport range 0x500-0x50f has been reserved
[    0.302023] system 00:02: iomem range 0xf0001000-0xf0001fff has been reserved
[    0.302035] system 00:03: iomem range 0xf0002000-0xf0002fff has been reserved
[    0.302044] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.302048] system 00:04: ioport range 0x800-0x805 has been reserved
[    0.302053] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.302057] system 00:04: ioport range 0x880-0x88f has been reserved
[    0.302070] system 00:0e: iomem range 0xf0000000-0xf0000fff has been reserved
[    0.302079] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.302089] system 00:11: iomem range 0xf0000-0xfffff could not be reserved
[    0.302093] system 00:11: iomem range 0xfe800000-0xfe8000ff has been reserved
[    0.302098] system 00:11: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.302103] system 00:11: iomem range 0xffff0000-0xffffffff has been reserved
[    0.302107] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.302112] system 00:11: iomem range 0x100000-0x7fedffff could not be reserved
[    0.302117] system 00:11: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.302122] system 00:11: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.302126] system 00:11: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.336849] AppArmor: AppArmor Filesystem Enabled
[    0.336917] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.336922] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.336929] pci 0000:00:01.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.336935] pci 0000:00:01.0:   PREFETCH window: 0xfdb00000-0xfdbfffff
[    0.336944] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.336949] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
[    0.336956] pci 0000:00:02.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.336962] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.336971] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.336976] pci 0000:00:03.0:   IO window: 0xa000-0xafff
[    0.336983] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
[    0.336990] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.337000] pci 0000:00:13.1: PCI bridge, secondary bus 0000:04
[    0.337005] pci 0000:00:13.1:   IO window: 0x9000-0x9fff
[    0.337012] pci 0000:00:13.1:   MEM window: 0xf9000000-0xfcffffff
[    0.337018] pci 0000:00:13.1:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.337035] pci 0000:00:01.0: setting latency timer to 64
[    0.337048]   alloc irq_desc for 27 on node -1
[    0.337052]   alloc kstat_irqs on node -1
[    0.337060] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.337066] pci 0000:00:02.0: setting latency timer to 64
[    0.337076]   alloc irq_desc for 31 on node -1
[    0.337080]   alloc kstat_irqs on node -1
[    0.337085] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.337091] pci 0000:00:03.0: setting latency timer to 64
[    0.337101] pci 0000:00:13.1: setting latency timer to 64
[    0.337108] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.337112] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.337116] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.337121] pci_bus 0000:01: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.337125] pci_bus 0000:01: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.337129] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.337133] pci_bus 0000:02: resource 1 mem: [0xf4000000-0xf7ffffff]
[    0.337138] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.337142] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]
[    0.337146] pci_bus 0000:03: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.337150] pci_bus 0000:03: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.337155] pci_bus 0000:04: resource 0 io:  [0x9000-0x9fff]
[    0.337159] pci_bus 0000:04: resource 1 mem: [0xf9000000-0xfcffffff]
[    0.337163] pci_bus 0000:04: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.337167] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.337171] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.337176] pci_bus 0000:80: resource 0 io:  [0x00-0xffff]
[    0.337180] pci_bus 0000:80: resource 1 mem: [0x000000-0xffffffff]
[    0.337227] NET: Registered protocol family 2
[    0.337358] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.337783] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.338309] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.338628] TCP: Hash tables configured (established 131072 bind 65536)
[    0.338634] TCP reno registered
[    0.338773] NET: Registered protocol family 1
[    0.338861] Trying to unpack rootfs image as initramfs...
[    0.500821] Switched to high resolution mode on CPU 1
[    0.503989] Switched to high resolution mode on CPU 0
[    0.549480] Freeing initrd memory: 7463k freed
[    0.554950] cpufreq-nforce2: No nForce2 chipset.
[    0.554995] Scanning for low memory corruption every 60 seconds
[    0.555123] audit: initializing netlink socket (disabled)
[    0.555142] type=2000 audit(1256045508.552:1): initialized
[    0.562808] highmem bounce pool size: 64 pages
[    0.562816] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.564737] VFS: Disk quotas dquot_6.5.2
[    0.564821] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.565545] fuse init (API version 7.12)
[    0.565653] msgmni has been set to 1705
[    0.565961] alg: No test for stdrng (krng)
[    0.565982] io scheduler noop registered
[    0.565986] io scheduler anticipatory registered
[    0.565989] io scheduler deadline registered
[    0.566052] io scheduler cfq registered (default)
[    0.566064] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.566083] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.566193] pci 0000:02:00.0: Boot video device
[    0.566400] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.566561] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.567051] aer 0000:00:02.0:pcie02: service driver aer loaded
[    0.567098] aer 0000:00:03.0:pcie02: service driver aer loaded
[    0.567111] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.567560] pciehp 0000:00:02.0:pcie04: HPC vendor_id 1106 device_id a364 ss_vid 0 ss_did 0
[    0.567599] pciehp 0000:00:02.0:pcie04: service driver pciehp loaded
[    0.567626] pciehp 0000:00:03.0:pcie04: HPC vendor_id 1106 device_id c364 ss_vid 0 ss_did 0
[    0.567659] pciehp 0000:00:03.0:pcie04: service driver pciehp loaded
[    0.567671] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.567857] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.567862] ACPI: Power Button [PWRF]
[    0.567923] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.567927] ACPI: Power Button [PWRB]
[    0.567985] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.567992] ACPI: Sleep Button [SLPB]
[    0.568099] fan PNP0C0B:00: registered as cooling_device0
[    0.568108] ACPI: Fan [FAN] (on)
[    0.569255] processor LNXCPU:00: registered as cooling_device1
[    0.569312] processor LNXCPU:01: registered as cooling_device2
[    0.574723] thermal LNXTHERM:01: registered as thermal_zone0
[    0.574739] ACPI: Thermal Zone [THRM] (24 C)
[    0.574837] isapnp: Scanning for PnP cards...
[    0.928729] isapnp: No Plug & Play device found
[    0.930444] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.930549] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.930975] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.932386] brd: module loaded
[    0.933006] loop: module loaded
[    0.933116] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.934119] pata_via 0000:00:0f.1: version 0.3.4
[    0.934347] scsi0 : pata_via
[    0.934467] scsi1 : pata_via
[    0.936644] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    0.936648] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    0.936816]   alloc irq_desc for 21 on node -1
[    0.936819]   alloc kstat_irqs on node -1
[    0.936828] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.936877] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.937322] Fixed MDIO Bus: probed
[    0.937372] PPP generic driver version 2.4.2
[    0.937513] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.937541] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.937559] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.937626] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.937682] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdfff000
[    0.948512] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.948626] usb usb1: configuration #1 chosen from 1 choice
[    0.948666] hub 1-0:1.0: USB hub found
[    0.948677] hub 1-0:1.0: 8 ports detected
[    0.948776] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.948808] uhci_hcd: USB Universal Host Controller Interface driver
[    0.948862]   alloc irq_desc for 20 on node -1
[    0.948866]   alloc kstat_irqs on node -1
[    0.948874] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.948884] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.948936] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.948972] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e000
[    0.949068] usb usb2: configuration #1 chosen from 1 choice
[    0.949107] hub 2-0:1.0: USB hub found
[    0.949116] hub 2-0:1.0: 2 ports detected
[    0.949180]   alloc irq_desc for 22 on node -1
[    0.949184]   alloc kstat_irqs on node -1
[    0.949190] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.949198] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.949248] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.949281] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000dc00
[    0.949374] usb usb3: configuration #1 chosen from 1 choice
[    0.949412] hub 3-0:1.0: USB hub found
[    0.949421] hub 3-0:1.0: 2 ports detected
[    0.949484] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.949491] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.949535] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.949558] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    0.949658] usb usb4: configuration #1 chosen from 1 choice
[    0.949695] hub 4-0:1.0: USB hub found
[    0.949704] hub 4-0:1.0: 2 ports detected
[    0.949767]   alloc irq_desc for 23 on node -1
[    0.949770]   alloc kstat_irqs on node -1
[    0.949777] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.949785] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.949831] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.949864] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d400
[    0.949962] usb usb5: configuration #1 chosen from 1 choice
[    0.949998] hub 5-0:1.0: USB hub found
[    0.950007] hub 5-0:1.0: 2 ports detected
[    0.950139] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.950142] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.950247] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.950334] mice: PS/2 mouse device common for all mice
[    0.950470] rtc_cmos 00:07: RTC can wake from S4
[    0.950517] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.950554] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.950699] device-mapper: uevent: version 1.0.3
[    0.950858] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.950977] device-mapper: multipath: version 1.1.0 loaded
[    0.950982] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.951156] EISA: Probing bus 0 at eisa.0
[    0.951196] EISA: Detected 0 cards.
[    0.951326] cpuidle: using governor ladder
[    0.951329] cpuidle: using governor menu
[    0.952055] TCP cubic registered
[    0.952220] NET: Registered protocol family 10
[    0.952878] lo: Disabled Privacy Extensions
[    0.953354] NET: Registered protocol family 17
[    0.953381] Bluetooth: L2CAP ver 2.13
[    0.953384] Bluetooth: L2CAP socket layer initialized
[    0.953388] Bluetooth: SCO (Voice Link) ver 0.6
[    0.953391] Bluetooth: SCO socket layer initialized
[    0.953446] Bluetooth: RFCOMM TTY layer initialized
[    0.953452] Bluetooth: RFCOMM socket layer initialized
[    0.953457] Bluetooth: RFCOMM ver 1.11
[    0.953504] Using IPI No-Shortcut mode
[    0.953606] PM: Resume from disk failed.
[    0.953623] registered taskstats version 1
[    0.953833]   Magic number: 13:383:534
[    0.953851] bdi 1:12: hash matches
[    0.953946] rtc_cmos 00:07: setting system clock to 2009-10-20 13:31:50 UTC (1256045510)
[    0.953951] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.953954] EDD information not available.
[    1.108457] ata1.00: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
[    1.108500] ata1.01: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-106S 0122, E1.22, max UDMA/66
[    1.108544] ata1.01: limited to UDMA/33 due to 40-wire cable
[    1.124352] ata1.00: configured for UDMA/33
[    1.140270] ata1.01: configured for UDMA/33
[    1.143168] scsi 0:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
[    1.146646] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.146651] Uniform CD-ROM driver Revision: 3.20
[    1.146769] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.146844] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.148086] scsi 0:0:1:0: CD-ROM            PIONEER  DVD-ROM DVD-106  1.22 PQ: 0 ANSI: 5
[    1.150976] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[    1.151092] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    1.151155] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.312477] ata2.00: ATA-7: Maxtor 2F040L0, VAM51JJ0, max UDMA/133
[    1.312482] ata2.00: 80293248 sectors, multi 16: LBA 
[    1.312519] ata2.00: limited to UDMA/33 due to 40-wire cable
[    1.328364] ata2.00: configured for UDMA/33
[    1.328482] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 2F040L0   VAM5 PQ: 0 ANSI: 5
[    1.328656] sd 1:0:0:0: [sda] 80293248 512-byte logical blocks: (41.1 GB/38.2 GiB)
[    1.328674] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    1.328749] sd 1:0:0:0: [sda] Write Protect is off
[    1.328753] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.328786] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.328960]  sda:
[    1.372021] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    1.506811] usb 1-4: configuration #1 chosen from 1 choice
[    1.744012] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.923982] usb 2-1: configuration #1 chosen from 1 choice
[    2.164011] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    2.339949] usb 2-2: configuration #1 chosen from 1 choice
[    2.796862]  sda1 sda2 < sda5 >
[    2.831196] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.831229] Freeing unused kernel memory: 540k freed
[    2.831722] Write protecting the kernel text: 4568k
[    2.831789] Write protecting the kernel read-only data: 1836k
[    3.003375] Linux agpgart interface v0.103
[    3.007706] agpgart: Detected VIA P4M900 chipset
[    3.021775] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.021787] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    3.046228] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[    3.047051] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.051877] eth0: VIA Rhine II at 0xfdffe000, 00:e0:4d:ab:08:f4, IRQ 23.
[    3.052561] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[    3.058694] sata_via 0000:00:0f.0: version 2.4
[    3.058716] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.058777] sata_via 0000:00:0f.0: routed to hard irq line 11
[    3.058915] scsi2 : sata_via
[    3.059070] scsi3 : sata_via
[    3.062168] ata3: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 21
[    3.062176] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 21
[    3.103497] FDC 0 is a post-1991 82077
[    3.180920]   alloc irq_desc for 17 on node -1
[    3.180926]   alloc kstat_irqs on node -1
[    3.180937] b43-pci-bridge 0000:04:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.184125] ssb: Sonics Silicon Backplane found on PCI device 0000:04:04.0
[    3.191337] usbcore: registered new interface driver hiddev
[    3.218277] Initializing USB Mass Storage driver...
[    3.219484] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.219696] usbcore: registered new interface driver usb-storage
[    3.219705] USB Mass Storage support registered.
[    3.219726] usb-storage: device found at 4
[    3.219731] usb-storage: waiting for device to settle before scanning
[    3.230252] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input4
[    3.230347] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:10.0-1/input0
[    3.244097] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input5
[    3.244218] generic-usb 0003:046D:C018.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:10.0-2/input0
[    3.244244] usbcore: registered new interface driver usbhid
[    3.244249] usbhid: v2.6:USB HID core driver
[    3.300018] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.512016] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.533451] b44.c:v2.0
[    3.533471] b44: Invalid MAC address found in EEPROM
[    3.533477] b44 ssb0:1: Problem fetching invariants of chip, aborting.
[    3.533490] b44: probe of ssb0:1 failed with error -22
[    4.796892] PM: Starting manual resume from disk
[    4.796898] PM: Resume from partition 8:5
[    4.796901] PM: Checking hibernation image.
[    4.797221] PM: Resume from disk failed.
[    4.801769] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    4.801776] EXT4-fs (sda1): write access will be enabled during recovery
[    4.829041] EXT4-fs (sda1): barriers enabled
[    5.247664] kjournald2 starting: pid 387, dev sda1:8, commit interval 5 seconds
[    5.247688] EXT4-fs (sda1): delayed allocation enabled
[    5.247694] EXT4-fs: file extents enabled
[    5.252106] EXT4-fs: mballoc enabled
[    5.252126] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.252139] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 511
[    5.252268] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1457
[    5.252303] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1180
[    5.252330] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1176
[    5.252359] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1171
[    5.252386] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1167
[    5.252414] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1163
[    5.252440] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1161
[    5.252468] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1150
[    5.252540] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 477
[    5.252569] EXT4-fs (sda1): 10 orphan inodes deleted
[    5.252575] EXT4-fs (sda1): recovery complete
[    5.799498] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.815580] type=1505 audit(1256045516.359:2): operation="profile_load" pid=410 name=/sbin/dhclient3
[    6.816117] type=1505 audit(1256045516.359:3): operation="profile_load" pid=410 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.816411] type=1505 audit(1256045516.359:4): operation="profile_load" pid=410 name=/usr/lib/connman/scripts/dhclient-script
[    6.878132] type=1505 audit(1256045516.422:5): operation="profile_load" pid=411 name=/usr/bin/evince
[    6.886536] type=1505 audit(1256045516.430:6): operation="profile_load" pid=411 name=/usr/bin/evince-previewer
[    6.891500] type=1505 audit(1256045516.434:7): operation="profile_load" pid=411 name=/usr/bin/evince-thumbnailer
[    6.927136] type=1505 audit(1256045516.470:8): operation="profile_load" pid=413 name=/usr/sbin/mysqld
[    6.946264] type=1505 audit(1256045516.490:9): operation="profile_load" pid=414 name=/usr/sbin/ntpd
[    6.964924] type=1505 audit(1256045516.510:10): operation="profile_load" pid=415 name=/usr/sbin/tcpdump
[    8.016657] Adding 1694816k swap on /dev/sda5.  Priority:-1 extents:1 across:1694816k 
[    8.220206] usb-storage: device scan complete
[    8.221183] scsi 4:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[    8.221735] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    8.222669] sd 4:0:0:0: [sdb] 3948543 512-byte logical blocks: (2.02 GB/1.88 GiB)
[    8.223415] sd 4:0:0:0: [sdb] Write Protect is off
[    8.223420] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[    8.223423] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    8.226291] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    8.226296]  sdb: sdb1
[    8.328421] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    8.328428] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    8.508325] EXT4-fs (sda1): internal journal on sda1:8
[   10.444281] udev: starting version 147
[   12.671973] type=1505 audit(1256045522.214:11): operation="profile_replace" pid=784 name=/sbin/dhclient3
[   12.672656] type=1505 audit(1256045522.218:12): operation="profile_replace" pid=784 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.672951] type=1505 audit(1256045522.218:13): operation="profile_replace" pid=784 name=/usr/lib/connman/scripts/dhclient-script
[   12.678966] type=1505 audit(1256045522.222:14): operation="profile_replace" pid=785 name=/usr/bin/evince
[   12.687563] type=1505 audit(1256045522.230:15): operation="profile_replace" pid=785 name=/usr/bin/evince-previewer
[   12.692789] type=1505 audit(1256045522.238:16): operation="profile_replace" pid=785 name=/usr/bin/evince-thumbnailer
[   12.703032] type=1505 audit(1256045522.246:17): operation="profile_replace" pid=789 name=/usr/sbin/mysqld
[   12.706458] type=1505 audit(1256045522.250:18): operation="profile_replace" pid=790 name=/usr/sbin/ntpd
[   12.709471] type=1505 audit(1256045522.254:19): operation="profile_replace" pid=791 name=/usr/sbin/tcpdump
[   13.612672] lp: driver loaded but no devices found
[   13.761045] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.908450] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.924046] parport_pc 00:0c: reported by Plug and Play ACPI
[   13.924095] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   14.020735] lp0: using parport0 (interrupt-driven).
[   14.030136] cfg80211: Calling CRDA to update world regulatory domain
[   15.023565] cfg80211: World regulatory domain updated:
[   15.023571]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.023575]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.023579]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.023583]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.023587]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.023591]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.963550] nvidia: module license 'NVIDIA' taints kernel.
[   15.963556] Disabling lock debugging due to kernel taint
[   15.985034] ppdev: user-space parallel port driver
[   16.219163]   alloc irq_desc for 24 on node -1
[   16.219168]   alloc kstat_irqs on node -1
[   16.219178] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   16.219188] nvidia 0000:02:00.0: setting latency timer to 64
[   16.219428] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   16.293059] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   16.673815] b43legacy-phy0: Broadcom 4301 WLAN found
[   16.696519] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   16.696542] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   16.720523] b43legacy-phy0 debug: Radio initialized
[   16.961778] Linux video capture interface: v2.00
[   17.633237] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   17.633824] cx88[0]: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34,autodetected], frontend(s): 1
[   17.633830] cx88[0]: TV tuner type 68, Radio tuner type -1
[   17.640607] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   17.827314] phy0: Selected rate control algorithm 'minstrel'
[   17.828978] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
[   17.852038] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[   17.880061] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   17.948048] cx2388x alsa driver version 0.0.7 loaded
[   18.320008] tuner-simple 1-0061: creating new instance
[   18.320016] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   18.322379] cx88[0]/2: cx2388x 8802 Driver Manager
[   18.322398]   alloc irq_desc for 16 on node -1
[   18.322402]   alloc kstat_irqs on node -1
[   18.322412] cx88-mpeg driver manager 0000:04:03.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.322423] cx88[0]/2: found at 0000:04:03.2, rev: 5, irq: 16, latency: 32, mmio: 0xfa000000
[   18.322434] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   18.322501] cx8800 0000:04:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.322516] cx88[0]/0: found at 0000:04:03.0, rev: 5, irq: 16, latency: 32, mmio: 0xf9000000
[   18.322530] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   18.322630] cx88[0]/0: registered device video0 [v4l2]
[   18.322681] cx88[0]/0: registered device vbi0
[   18.334989] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.335052] HDA Intel 0000:80:01.0: setting latency timer to 64
[   18.335060] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[   18.335622] cx88_audio 0000:04:03.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.335639] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   18.335683] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   18.391202] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   18.469245] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   18.751043] input: HDA Digital PCBeep as /devices/pci0000:80/0000:80:01.0/input/input6
[   18.868024] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   18.894021] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   18.894026] cx88/2: registering cx8802 driver, type: dvb access: shared
[   18.894031] cx88[0]/2: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34]
[   18.894035] cx88[0]/2: cx2388x based DVB/ATSC card
[   18.894038] cx8802_alloc_frontends() allocating 1 frontend(s)
[   18.921230] b43legacy-phy0 debug: Chip initialized
[   18.921407] b43legacy-phy0 debug: 30-bit DMA initialized
[   18.921712] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2B
[   18.921720] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x78
[   18.921727] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2E
[   18.921733] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x19
[   18.921767] b43legacy-phy0 debug: Wireless interface started
[   18.921778] b43legacy-phy0 debug: Adding Interface type 2
[   18.956688] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.015605] nxt200x: NXT2004 Detected
[   19.016149] tuner-simple 1-0061: attaching existing instance
[   19.016157] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   19.016167] DVB: registering new adapter (cx88[0])
[   19.016174] DVB: registering adapter 0 frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   19.027683] b43legacy-phy0: Radio hardware status changed to DISABLED
[   19.027694] b43legacy-phy0 debug: Radio initialized
[   19.069348] b43legacy-phy0 debug: Removing Interface type 2
[   19.084709] b43legacy-phy0 debug: Wireless interface stopped
[   19.084854] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   19.084915] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[   19.084976] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   19.092534] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   19.100521] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   19.108516] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   19.116515] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   19.124514] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   19.132514] b43legacy-phy0 debug: Radio initialized
[   19.132526] b43legacy-phy0 debug: Radio initialized
[   23.939727] type=1503 audit(1256045533.484:20): operation="open" pid=1471 parent=1470 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   24.813983] type=1503 audit(1256045534.358:21): operation="open" pid=1555 parent=1554 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   25.717335] type=1503 audit(1256045535.262:22): operation="open" pid=1705 parent=1562 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.200183] type=1503 audit(1256045535.746:23): operation="open" pid=1719 parent=1718 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.548513] eth0: no IPv6 routers present
[   27.223252] type=1503 audit(1256045536.766:24): operation="open" pid=1733 parent=1732 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   28.251180] type=1503 audit(1256045537.794:25): operation="open" pid=1748 parent=1747 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.303278] type=1503 audit(1256045538.846:26): operation="open" pid=1764 parent=1763 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.501183] type=1503 audit(1256045539.046:27): operation="open" pid=1775 parent=1774 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   42.738614] CPU0 attaching NULL sched-domain.
[   42.738623] CPU1 attaching NULL sched-domain.
[   42.748576] CPU0 attaching sched-domain:
[   42.748582]  domain 0: span 0-1 level SIBLING
[   42.748587]   groups: 0 1
[   42.748595]   domain 1: span 0-1 level MC
[   42.748600]    groups: 0-1 (__cpu_power = 2048)
[   42.748610] CPU1 attaching sched-domain:
[   42.748614]  domain 0: span 0-1 level SIBLING
[   42.748618]   groups: 1 0
[   42.748626]   domain 1: span 0-1 level MC
[   42.748630]    groups: 0-1 (__cpu_power = 2048)
[   44.473052] sd 4:0:0:0: [sdb] 3948543 512-byte logical blocks: (2.02 GB/1.88 GiB)
[   44.473899] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   44.475630] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   44.475643]  sdb: sdb1
[   44.491349] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   44.491359]  sdb: sdb1
[   51.053380] CPU0 attaching NULL sched-domain.
[   51.053392] CPU1 attaching NULL sched-domain.
[   51.068579] CPU0 attaching sched-domain:
[   51.068585]  domain 0: span 0-1 level SIBLING
[   51.068590]   groups: 0 1
[   51.068600] CPU1 attaching sched-domain:
[   51.068604]  domain 0: span 0-1 level SIBLING
[   51.068608]   groups: 1 0
[   51.463828] sd 4:0:0:0: [sdb] 3948543 512-byte logical blocks: (2.02 GB/1.88 GiB)
[   51.464311] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   51.469041] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   51.469053]  sdb: sdb1
[   52.437102] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive
```

---

### Post by molder on 2009-10-20
Tried installing wicd with no success.  It did ask me to join the group netdev?

---

