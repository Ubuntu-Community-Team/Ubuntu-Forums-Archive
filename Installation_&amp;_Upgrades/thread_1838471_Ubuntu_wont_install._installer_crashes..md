---
title: "Ubuntu wont install. installer crashes."
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by Kyomaru on 2011-09-03
I'm trying to install Ubuntu 11.04 on my girlfriends computer, as her winxp partition got a virus and seriously started to mess up. she's fed up with it, but wanted a working computer, so i offered to install ubuntu till she can get it to the shop. As i was installing it the first time, the installer crashed. I'd had this happen before, but after i said quit, it said a desktop session would be launched so i could investigate the problem. so i tried to install from there, and it gave me this message; [HTML]ubi-partman failed with exit code 10. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.[/HTML]<br><br>&nbsp;now, i went to go check it, but it is completly unintelligable to me, so i was wondering if someone could help me out. i also have a cd for 10.10, but i wanted her to have this version, as she's used it before while my hard drive was on her computer. If installing 10.10 would fix the problem instead, then i will gladly do it. here is the syslog information for reference

<br><br><div align="left">```
Sep  3 17:11:52 ubuntu kernel: imklog 4.6.4, log source = /proc/kmsg started.
Sep  3 17:11:52 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="1195" x-info="http://www.rsyslog.com"] (re)start
Sep  3 17:11:52 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Sep  3 17:11:52 ubuntu rsyslogd: rsyslogd's userid changed to 101
Sep  3 17:11:52 ubuntu rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fd0000 (usable)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000077fd0000 - 0000000077fde000 (ACPI data)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000077fde000 - 0000000078000000 (ACPI NVS)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Sep  3 17:11:52 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Sep  3 17:11:52 ubuntu kernel: [    0.000000] DMI present.
Sep  3 17:11:52 ubuntu kernel: [    0.000000] DMI: MICRO-STAR INTERANTIONAL CO.,LTD MS-7327/MS-7327, BIOS V1.0 02/08/2007
Sep  3 17:11:52 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==&gt; (reserved)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] last_pfn = 0x77fd0 max_arch_pfn = 0x100000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Sep  3 17:11:52 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   A0000-EFFFF uncachable
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Sep  3 17:11:52 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   1 disabled
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   2 disabled
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   3 disabled
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   4 disabled
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   5 disabled
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   6 disabled
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   7 disabled
Sep  3 17:11:52 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep  3 17:11:52 ubuntu kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Sep  3 17:11:52 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Sep  3 17:11:52 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Sep  3 17:11:52 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] RAMDISK: 7730b000 - 77fd0000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 36b39000 - 377fd9b3
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007730b000 - 0000000077fcf9b2 to 36b39000 - 377fd9b2
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: RSDP 000f96d0 00014 (v00 ACPIAM)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: RSDT 77fd0000 00038 (v01 020807 RSDT1716 20070208 MSFT 00000097)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: FACP 77fd0200 00084 (v02 020807 FACP1716 20070208 MSFT 00000097)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: DSDT 77fd0430 044A0 (v01  1ADNC 1ADNCB33 00000B33 INTL 20051117)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: FACS 77fde000 00040
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: APIC 77fd0390 0005C (v01 020807 APIC1716 20070208 MSFT 00000097)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: MCFG 77fd03f0 0003C (v01 020807 OEMMCFG  20070208 MSFT 00000097)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: OEMB 77fde040 00071 (v01 020807 OEMB1716 20070208 MSFT 00000097)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: HPET 77fd48d0 00038 (v01 020807 OEMHPET  20070208 MSFT 00000097)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] 1031MB HIGHMEM available.
Sep  3 17:11:52 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Zone PFN ranges:
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   DMA      0x00000010 -&gt; 0x00001000
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   Normal   0x00001000 -&gt; 0x000377fe
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -&gt; 0x00077fd0
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Sep  3 17:11:52 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Sep  3 17:11:52 ubuntu kernel: [    0.000000]     0: 0x00000010 -&gt; 0x0000009f
Sep  3 17:11:52 ubuntu kernel: [    0.000000]     0: 0x00000100 -&gt; 0x00077fd0
Sep  3 17:11:52 ubuntu kernel: [    0.000000] On node 0 totalpages: 491359
Sep  3 17:11:52 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f5c38200
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   HighMem zone: 2064 pages used for memmap
Sep  3 17:11:52 ubuntu kernel: [    0.000000]   HighMem zone: 262082 pages, LIFO batch:31
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Using APIC driver default
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep  3 17:11:52 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  3 17:11:52 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Sep  3 17:11:52 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Sep  3 17:11:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 78000000 (gap: 78000000:87f80000)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep  3 17:11:52 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Sep  3 17:11:52 ubuntu kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u2097152
Sep  3 17:11:52 ubuntu kernel: [    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
Sep  3 17:11:52 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487519
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Sep  3 17:11:52 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Initializing CPU#0
Sep  3 17:11:52 ubuntu kernel: [    0.000000] allocated 9829120 bytes of page_cgroup
Sep  3 17:11:52 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:00077fd0)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Memory: 1917084k/1965888k available (5188k kernel code, 48352k reserved, 2540k data, 700k init, 1056584k highmem)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Sep  3 17:11:52 ubuntu kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
Sep  3 17:11:52 ubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Sep  3 17:11:52 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Sep  3 17:11:52 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Sep  3 17:11:52 ubuntu kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Sep  3 17:11:52 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Sep  3 17:11:52 ubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f4808000 soft=f480a000
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Sep  3 17:11:52 ubuntu kernel: [    0.000000] console [tty0] enabled
Sep  3 17:11:52 ubuntu kernel: [    0.000000] hpet clockevent registered
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Detected 1995.187 MHz processor.
Sep  3 17:11:52 ubuntu kernel: [    0.000000] Marking TSC unstable due to TSCs unsynchronized
Sep  3 17:11:52 ubuntu kernel: [    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.37 BogoMIPS (lpj=7980748)
Sep  3 17:11:52 ubuntu kernel: [    0.004015] pid_max: default: 32768 minimum: 301
Sep  3 17:11:52 ubuntu kernel: [    0.004050] Security Framework initialized
Sep  3 17:11:52 ubuntu kernel: [    0.004074] AppArmor: AppArmor initialized
Sep  3 17:11:52 ubuntu kernel: [    0.004077] Yama: becoming mindful.
Sep  3 17:11:52 ubuntu kernel: [    0.004156] Mount-cache hash table entries: 512
Sep  3 17:11:52 ubuntu kernel: [    0.004331] Initializing cgroup subsys ns
Sep  3 17:11:52 ubuntu kernel: [    0.004336] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Sep  3 17:11:52 ubuntu kernel: [    0.004341] Initializing cgroup subsys cpuacct
Sep  3 17:11:52 ubuntu kernel: [    0.004348] Initializing cgroup subsys memory
Sep  3 17:11:52 ubuntu kernel: [    0.004360] Initializing cgroup subsys devices
Sep  3 17:11:52 ubuntu kernel: [    0.004363] Initializing cgroup subsys freezer
Sep  3 17:11:52 ubuntu kernel: [    0.004366] Initializing cgroup subsys net_cls
Sep  3 17:11:52 ubuntu kernel: [    0.004370] Initializing cgroup subsys blkio
Sep  3 17:11:52 ubuntu kernel: [    0.004411] CPU: Physical Processor ID: 0
Sep  3 17:11:52 ubuntu kernel: [    0.004413] CPU: Processor Core ID: 0
Sep  3 17:11:52 ubuntu kernel: [    0.004418] mce: CPU supports 5 MCE banks
Sep  3 17:11:52 ubuntu kernel: [    0.004432] using C1E aware idle routine
Sep  3 17:11:52 ubuntu kernel: [    0.010079] ACPI: Core revision 20110112
Sep  3 17:11:52 ubuntu kernel: [    0.014492] ftrace: allocating 23640 entries in 47 pages
Sep  3 17:11:52 ubuntu kernel: [    0.016093] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  3 17:11:52 ubuntu kernel: [    0.016409] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  3 17:11:52 ubuntu kernel: [    0.059022] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
Sep  3 17:11:52 ubuntu kernel: [    0.060003] Performance Events: AMD PMU driver.
Sep  3 17:11:52 ubuntu kernel: [    0.060003] ... version:                0
Sep  3 17:11:52 ubuntu kernel: [    0.060003] ... bit width:              48
Sep  3 17:11:52 ubuntu kernel: [    0.060003] ... generic registers:      4
Sep  3 17:11:52 ubuntu kernel: [    0.060003] ... value mask:             0000ffffffffffff
Sep  3 17:11:52 ubuntu kernel: [    0.060003] ... max period:             00007fffffffffff
Sep  3 17:11:52 ubuntu kernel: [    0.060003] ... fixed-purpose events:   0
Sep  3 17:11:52 ubuntu kernel: [    0.060003] ... event mask:             000000000000000f
Sep  3 17:11:52 ubuntu kernel: [    0.060003] CPU 1 irqstacks, hard=f48aa000 soft=f48ac000
Sep  3 17:11:52 ubuntu kernel: [    0.060003] Booting Node   0, Processors  #1 Ok.
Sep  3 17:11:52 ubuntu kernel: [    0.008000] Initializing CPU#1
Sep  3 17:11:52 ubuntu kernel: [    0.144113] Brought up 2 CPUs
Sep  3 17:11:52 ubuntu kernel: [    0.144117] Total of 2 processors activated (7980.73 BogoMIPS).
Sep  3 17:11:52 ubuntu kernel: [    0.144328] devtmpfs: initialized
Sep  3 17:11:52 ubuntu kernel: [    0.145413] print_constraints: dummy: 
Sep  3 17:11:52 ubuntu kernel: [    0.145443] Time: 17:10:20  Date: 09/03/11
Sep  3 17:11:52 ubuntu kernel: [    0.145491] NET: Registered protocol family 16
Sep  3 17:11:52 ubuntu kernel: [    0.145533] Trying to unpack rootfs image as initramfs...
Sep  3 17:11:52 ubuntu kernel: [    0.145650] EISA bus registered
Sep  3 17:11:52 ubuntu kernel: [    0.145657] node 0 link 0: io port [1000, ffffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145661] TOM: 0000000080000000 aka 2048M
Sep  3 17:11:52 ubuntu kernel: [    0.145666] node 0 link 0: mmio [f0000000, f7feffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145670] node 0 link 0: mmio [e0000000, efffffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145673] node 0 link 0: mmio [80000000, dfffffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145677] node 0 link 0: mmio [a0000, bffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145680] node 0 link 0: mmio [f7ff0000, ffffffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145684] bus: [00, ff] on node 0 link 0
Sep  3 17:11:52 ubuntu kernel: [    0.145687] bus: 00 index 0 [io  0x0000-0xffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145690] bus: 00 index 1 [mem 0x80000000-0xffffffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145693] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
Sep  3 17:11:52 ubuntu kernel: [    0.145701] ACPI: bus type pci registered
Sep  3 17:11:52 ubuntu kernel: [    0.145791] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Sep  3 17:11:52 ubuntu kernel: [    0.145795] PCI: not using MMCONFIG
Sep  3 17:11:52 ubuntu kernel: [    0.146470] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
Sep  3 17:11:52 ubuntu kernel: [    0.146472] PCI: Using configuration type 1 for base access
Sep  3 17:11:52 ubuntu kernel: [    0.148326] bio: create slab <bio-0> at 0
Sep  3 17:11:52 ubuntu kernel: [    0.149546] ACPI: EC: Detected MSI hardware, enabling workarounds.
Sep  3 17:11:52 ubuntu kernel: [    0.149549] ACPI: EC: Look up EC in DSDT
Sep  3 17:11:52 ubuntu kernel: [    0.150823] ACPI: Executed 3 blocks of module-level executable AML code
Sep  3 17:11:52 ubuntu kernel: [    2.820597] ACPI: Interpreter enabled
Sep  3 17:11:52 ubuntu kernel: [    2.820605] ACPI: (supports S0 S1 S4 S5)
Sep  3 17:11:52 ubuntu kernel: [    2.820629] ACPI: Using IOAPIC for interrupt routing
Sep  3 17:11:52 ubuntu kernel: [    2.820654] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Sep  3 17:11:52 ubuntu kernel: [    2.821842] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Sep  3 17:11:52 ubuntu kernel: [    2.821845] PCI: Using MMCONFIG for extended config space
Sep  3 17:11:52 ubuntu kernel: [    3.460335] ACPI: No dock devices found.
Sep  3 17:11:52 ubuntu kernel: [    3.460338] HEST: Table not found.
Sep  3 17:11:52 ubuntu kernel: [    3.460343] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Sep  3 17:11:52 ubuntu kernel: [    3.460450] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Sep  3 17:11:52 ubuntu kernel: [    3.460664] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Sep  3 17:11:52 ubuntu kernel: [    3.460668] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Sep  3 17:11:52 ubuntu kernel: [    3.460671] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Sep  3 17:11:52 ubuntu kernel: [    3.460674] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
Sep  3 17:11:52 ubuntu kernel: [    3.460678] pci_root PNP0A03:00: host bridge window [mem 0x78000000-0xdfffffff] (ignored)
Sep  3 17:11:52 ubuntu kernel: [    3.460681] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
Sep  3 17:11:52 ubuntu kernel: [    3.460695] pci 0000:00:00.0: [1002:7910] type 0 class 0x000600
Sep  3 17:11:52 ubuntu kernel: [    3.460734] pci 0000:00:01.0: [1002:7912] type 1 class 0x000604
Sep  3 17:11:52 ubuntu kernel: [    3.460783] pci 0000:00:07.0: [1002:7917] type 1 class 0x000604
Sep  3 17:11:52 ubuntu kernel: [    3.460817] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Sep  3 17:11:52 ubuntu kernel: [    3.460820] pci 0000:00:07.0: PME# disabled
Sep  3 17:11:52 ubuntu kernel: [    3.460860] pci 0000:00:12.0: [1002:4380] type 0 class 0x000101
Sep  3 17:11:52 ubuntu kernel: [    3.460885] pci 0000:00:12.0: reg 10: [io  0xc000-0xc007]
Sep  3 17:11:52 ubuntu kernel: [    3.460897] pci 0000:00:12.0: reg 14: [io  0xb000-0xb003]
Sep  3 17:11:52 ubuntu kernel: [    3.460909] pci 0000:00:12.0: reg 18: [io  0xa000-0xa007]
Sep  3 17:11:52 ubuntu kernel: [    3.460921] pci 0000:00:12.0: reg 1c: [io  0x9000-0x9003]
Sep  3 17:11:52 ubuntu kernel: [    3.460934] pci 0000:00:12.0: reg 20: [io  0x8000-0x800f]
Sep  3 17:11:52 ubuntu kernel: [    3.460946] pci 0000:00:12.0: reg 24: [mem 0xfe8ff800-0xfe8ffbff]
Sep  3 17:11:52 ubuntu kernel: [    3.460972] pci 0000:00:12.0: set SATA to AHCI mode
Sep  3 17:11:52 ubuntu kernel: [    3.461015] pci 0000:00:13.0: [1002:4387] type 0 class 0x000c03
Sep  3 17:11:52 ubuntu kernel: [    3.461032] pci 0000:00:13.0: reg 10: [mem 0xfe8fe000-0xfe8fefff]
Sep  3 17:11:52 ubuntu kernel: [    3.461111] pci 0000:00:13.1: [1002:4388] type 0 class 0x000c03
Sep  3 17:11:52 ubuntu kernel: [    3.461128] pci 0000:00:13.1: reg 10: [mem 0xfe8fd000-0xfe8fdfff]
Sep  3 17:11:52 ubuntu kernel: [    3.461206] pci 0000:00:13.2: [1002:4389] type 0 class 0x000c03
Sep  3 17:11:52 ubuntu kernel: [    3.461223] pci 0000:00:13.2: reg 10: [mem 0xfe8fc000-0xfe8fcfff]
Sep  3 17:11:52 ubuntu kernel: [    3.461301] pci 0000:00:13.3: [1002:438a] type 0 class 0x000c03
Sep  3 17:11:52 ubuntu kernel: [    3.461318] pci 0000:00:13.3: reg 10: [mem 0xfe8fb000-0xfe8fbfff]
Sep  3 17:11:52 ubuntu kernel: [    3.461395] pci 0000:00:13.4: [1002:438b] type 0 class 0x000c03
Sep  3 17:11:52 ubuntu kernel: [    3.461412] pci 0000:00:13.4: reg 10: [mem 0xfe8fa000-0xfe8fafff]
Sep  3 17:11:52 ubuntu kernel: [    3.461497] pci 0000:00:13.5: [1002:4386] type 0 class 0x000c03
Sep  3 17:11:52 ubuntu kernel: [    3.461520] pci 0000:00:13.5: reg 10: [mem 0xfe8ff000-0xfe8ff0ff]
Sep  3 17:11:52 ubuntu kernel: [    3.461605] pci 0000:00:13.5: supports D1 D2
Sep  3 17:11:52 ubuntu kernel: [    3.461608] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
Sep  3 17:11:52 ubuntu kernel: [    3.461613] pci 0000:00:13.5: PME# disabled
Sep  3 17:11:52 ubuntu kernel: [    3.461916] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Sep  3 17:11:52 ubuntu kernel: [    3.462893] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
Sep  3 17:11:52 ubuntu kernel: [    3.462049] Freeing initrd memory: 13076k freed
Sep  3 17:11:52 ubuntu kernel: [    3.470418] pci 0000:00:14.1: [1002:438c] type 0 class 0x000101
Sep  3 17:11:52 ubuntu kernel: [    3.470439] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Sep  3 17:11:52 ubuntu kernel: [    3.470452] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Sep  3 17:11:52 ubuntu kernel: [    3.470464] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Sep  3 17:11:52 ubuntu kernel: [    3.470476] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Sep  3 17:11:52 ubuntu kernel: [    3.470488] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Sep  3 17:11:52 ubuntu kernel: [    3.470553] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Sep  3 17:11:52 ubuntu kernel: [    3.470584] pci 0000:00:14.2: reg 10: [mem 0xfe8f4000-0xfe8f7fff 64bit]
Sep  3 17:11:52 ubuntu kernel: [    3.470660] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Sep  3 17:11:52 ubuntu kernel: [    3.470665] pci 0000:00:14.2: PME# disabled
Sep  3 17:11:52 ubuntu kernel: [    3.470690] pci 0000:00:14.3: [1002:438d] type 0 class 0x000601
Sep  3 17:11:52 ubuntu kernel: [    3.470780] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Sep  3 17:11:52 ubuntu kernel: [    3.470838] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
Sep  3 17:11:52 ubuntu kernel: [    3.470873] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
Sep  3 17:11:52 ubuntu kernel: [    3.470902] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
Sep  3 17:11:52 ubuntu kernel: [    3.470932] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
Sep  3 17:11:52 ubuntu kernel: [    3.470975] PCI: peer root bus 00 res updated from pci conf
Sep  3 17:11:52 ubuntu kernel: [    3.471011] pci 0000:01:05.0: [1002:791e] type 0 class 0x000300
Sep  3 17:11:52 ubuntu kernel: [    3.471025] pci 0000:01:05.0: reg 10: [mem 0xf0000000-0xf7ffffff 64bit pref]
Sep  3 17:11:52 ubuntu kernel: [    3.471034] pci 0000:01:05.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
Sep  3 17:11:52 ubuntu kernel: [    3.471041] pci 0000:01:05.0: reg 20: [io  0xd000-0xd0ff]
Sep  3 17:11:52 ubuntu kernel: [    3.471048] pci 0000:01:05.0: reg 24: [mem 0xfe900000-0xfe9fffff]
Sep  3 17:11:52 ubuntu kernel: [    3.471065] pci 0000:01:05.0: supports D1 D2
Sep  3 17:11:52 ubuntu kernel: [    3.471086] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Sep  3 17:11:52 ubuntu kernel: [    3.471091] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Sep  3 17:11:52 ubuntu kernel: [    3.471095] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
Sep  3 17:11:52 ubuntu kernel: [    3.471101] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Sep  3 17:11:52 ubuntu kernel: [    3.471157] pci 0000:02:00.0: [10ec:8136] type 0 class 0x000200
Sep  3 17:11:52 ubuntu kernel: [    3.471174] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
Sep  3 17:11:52 ubuntu kernel: [    3.471203] pci 0000:02:00.0: reg 18: [mem 0xfebff000-0xfebfffff 64bit]
Sep  3 17:11:52 ubuntu kernel: [    3.471236] pci 0000:02:00.0: reg 30: [mem 0xfebc0000-0xfebdffff pref]
Sep  3 17:11:52 ubuntu kernel: [    3.471278] pci 0000:02:00.0: supports D1 D2
Sep  3 17:11:52 ubuntu kernel: [    3.471281] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
Sep  3 17:11:52 ubuntu kernel: [    3.471286] pci 0000:02:00.0: PME# disabled
Sep  3 17:11:52 ubuntu kernel: [    3.471308] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Sep  3 17:11:52 ubuntu kernel: [    3.471323] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Sep  3 17:11:52 ubuntu kernel: [    3.471327] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
Sep  3 17:11:52 ubuntu kernel: [    3.471331] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Sep  3 17:11:52 ubuntu kernel: [    3.471337] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Sep  3 17:11:52 ubuntu kernel: [    3.471409] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
Sep  3 17:11:52 ubuntu kernel: [    3.471416] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
Sep  3 17:11:52 ubuntu kernel: [    3.471422] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Sep  3 17:11:52 ubuntu kernel: [    3.471428] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Sep  3 17:11:52 ubuntu kernel: [    3.471431] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
Sep  3 17:11:52 ubuntu kernel: [    3.471434] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xffffffff] (subtractive decode)
Sep  3 17:11:52 ubuntu kernel: [    3.471438] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Sep  3 17:11:52 ubuntu kernel: [    3.471452] pci_bus 0000:00: on NUMA node 0
Sep  3 17:11:52 ubuntu kernel: [    3.471457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  3 17:11:52 ubuntu kernel: [    3.471650] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Sep  3 17:11:52 ubuntu kernel: [    3.471701] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Sep  3 17:11:52 ubuntu kernel: [    3.471752] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Sep  3 17:11:52 ubuntu kernel: [    3.471866]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Sep  3 17:11:52 ubuntu kernel: [    3.476904] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
Sep  3 17:11:52 ubuntu kernel: [    3.476952] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 10 11 12 14 15)
Sep  3 17:11:52 ubuntu kernel: [    3.476999] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
Sep  3 17:11:52 ubuntu kernel: [    3.477045] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
Sep  3 17:11:52 ubuntu kernel: [    3.477092] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Sep  3 17:11:52 ubuntu kernel: [    3.477139] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Sep  3 17:11:52 ubuntu kernel: [    3.477187] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
Sep  3 17:11:52 ubuntu kernel: [    3.477237] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Sep  3 17:11:52 ubuntu kernel: [    3.477375] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Sep  3 17:11:52 ubuntu kernel: [    3.477378] vgaarb: loaded
Sep  3 17:11:52 ubuntu kernel: [    3.477645] SCSI subsystem initialized
Sep  3 17:11:52 ubuntu kernel: [    3.477664] libata version 3.00 loaded.
Sep  3 17:11:52 ubuntu kernel: [    3.477664] usbcore: registered new interface driver usbfs
Sep  3 17:11:52 ubuntu kernel: [    3.477664] usbcore: registered new interface driver hub
Sep  3 17:11:52 ubuntu kernel: [    3.477664] usbcore: registered new device driver usb
Sep  3 17:11:52 ubuntu kernel: [    3.477664] wmi: Mapper loaded
Sep  3 17:11:52 ubuntu kernel: [    3.477664] PCI: Using ACPI for IRQ routing
Sep  3 17:11:52 ubuntu kernel: [    3.477664] PCI: pci_cache_line_size set to 64 bytes
Sep  3 17:11:52 ubuntu kernel: [    3.477664] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Sep  3 17:11:52 ubuntu kernel: [    3.477664] reserve RAM buffer: 0000000077fd0000 - 0000000077ffffff 
Sep  3 17:11:52 ubuntu kernel: [    3.477664] NetLabel: Initializing
Sep  3 17:11:52 ubuntu kernel: [    3.477664] NetLabel:  domain hash size = 128
Sep  3 17:11:52 ubuntu kernel: [    3.477664] NetLabel:  protocols = UNLABELED CIPSOv4
Sep  3 17:11:52 ubuntu kernel: [    3.477664] NetLabel:  unlabeled traffic allowed by default
Sep  3 17:11:52 ubuntu kernel: [    3.477664] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Sep  3 17:11:52 ubuntu kernel: [    3.477664] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Sep  3 17:11:52 ubuntu kernel: [    3.480336] Switching to clocksource hpet
Sep  3 17:11:52 ubuntu kernel: [    3.483694] Switched to NOHz mode on CPU #0
Sep  3 17:11:52 ubuntu kernel: [    3.483737] Switched to NOHz mode on CPU #1
Sep  3 17:11:52 ubuntu kernel: [    3.488718] AppArmor: AppArmor Filesystem Enabled
Sep  3 17:11:52 ubuntu kernel: [    3.488757] pnp: PnP ACPI init
Sep  3 17:11:52 ubuntu kernel: [    3.488779] ACPI: bus type pnp registered
Sep  3 17:11:52 ubuntu kernel: [    3.488938] pnp 00:00: [bus 00-ff]
Sep  3 17:11:52 ubuntu kernel: [    3.488942] pnp 00:00: [io  0x0cf8-0x0cff]
Sep  3 17:11:52 ubuntu kernel: [    3.488945] pnp 00:00: [io  0x0000-0x0cf7 window]
Sep  3 17:11:52 ubuntu kernel: [    3.488948] pnp 00:00: [io  0x0d00-0xffff window]
Sep  3 17:11:52 ubuntu kernel: [    3.488951] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Sep  3 17:11:52 ubuntu kernel: [    3.488954] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Sep  3 17:11:52 ubuntu kernel: [    3.488957] pnp 00:00: [mem 0x78000000-0xdfffffff window]
Sep  3 17:11:52 ubuntu kernel: [    3.488960] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Sep  3 17:11:52 ubuntu kernel: [    3.489029] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.489094] pnp 00:01: [mem 0x78000000-0x7fffffff]
Sep  3 17:11:52 ubuntu kernel: [    3.489157] system 00:01: [mem 0x78000000-0x7fffffff] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.489162] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.489205] pnp 00:02: [dma 4]
Sep  3 17:11:52 ubuntu kernel: [    3.489208] pnp 00:02: [io  0x0000-0x000f]
Sep  3 17:11:52 ubuntu kernel: [    3.489210] pnp 00:02: [io  0x0081-0x0083]
Sep  3 17:11:52 ubuntu kernel: [    3.489213] pnp 00:02: [io  0x0087]
Sep  3 17:11:52 ubuntu kernel: [    3.489216] pnp 00:02: [io  0x0089-0x008b]
Sep  3 17:11:52 ubuntu kernel: [    3.489218] pnp 00:02: [io  0x008f]
Sep  3 17:11:52 ubuntu kernel: [    3.489221] pnp 00:02: [io  0x00c0-0x00df]
Sep  3 17:11:52 ubuntu kernel: [    3.489254] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.489267] pnp 00:03: [io  0x0070-0x0071]
Sep  3 17:11:52 ubuntu kernel: [    3.489280] pnp 00:03: [irq 8]
Sep  3 17:11:52 ubuntu kernel: [    3.489317] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.489327] pnp 00:04: [io  0x0061]
Sep  3 17:11:52 ubuntu kernel: [    3.489360] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.489370] pnp 00:05: [io  0x00f0-0x00ff]
Sep  3 17:11:52 ubuntu kernel: [    3.489375] pnp 00:05: [irq 13]
Sep  3 17:11:52 ubuntu kernel: [    3.489408] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.489941] pnp 00:06: [io  0x03f0-0x03f5]
Sep  3 17:11:52 ubuntu kernel: [    3.489943] pnp 00:06: [io  0x03f7]
Sep  3 17:11:52 ubuntu kernel: [    3.489949] pnp 00:06: [irq 6]
Sep  3 17:11:52 ubuntu kernel: [    3.489952] pnp 00:06: [dma 2]
Sep  3 17:11:52 ubuntu kernel: [    3.490021] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.490345] pnp 00:07: [io  0x0378-0x037f]
Sep  3 17:11:52 ubuntu kernel: [    3.490351] pnp 00:07: [irq 7]
Sep  3 17:11:52 ubuntu kernel: [    3.490354] pnp 00:07: [dma 0 disabled]
Sep  3 17:11:52 ubuntu kernel: [    3.490490] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.490547] pnp 00:08: [mem 0xfed00000-0xfed003ff]
Sep  3 17:11:52 ubuntu kernel: [    3.490584] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.490638] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Sep  3 17:11:52 ubuntu kernel: [    3.490641] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Sep  3 17:11:52 ubuntu kernel: [    3.490697] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Sep  3 17:11:52 ubuntu kernel: [    3.490700] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.490704] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.490826] pnp 00:0a: [io  0x0010-0x001f]
Sep  3 17:11:52 ubuntu kernel: [    3.490828] pnp 00:0a: [io  0x0022-0x003f]
Sep  3 17:11:52 ubuntu kernel: [    3.490831] pnp 00:0a: [io  0x0062-0x0063]
Sep  3 17:11:52 ubuntu kernel: [    3.490834] pnp 00:0a: [io  0x0065-0x006f]
Sep  3 17:11:52 ubuntu kernel: [    3.490836] pnp 00:0a: [io  0x0072-0x007f]
Sep  3 17:11:52 ubuntu kernel: [    3.490842] pnp 00:0a: [io  0x0080]
Sep  3 17:11:52 ubuntu kernel: [    3.490844] pnp 00:0a: [io  0x0084-0x0086]
Sep  3 17:11:52 ubuntu kernel: [    3.490847] pnp 00:0a: [io  0x0088]
Sep  3 17:11:52 ubuntu kernel: [    3.490849] pnp 00:0a: [io  0x008c-0x008e]
Sep  3 17:11:52 ubuntu kernel: [    3.490852] pnp 00:0a: [io  0x0090-0x009f]
Sep  3 17:11:52 ubuntu kernel: [    3.490854] pnp 00:0a: [io  0x00a2-0x00bf]
Sep  3 17:11:52 ubuntu kernel: [    3.490856] pnp 00:0a: [io  0x00b1]
Sep  3 17:11:52 ubuntu kernel: [    3.490859] pnp 00:0a: [io  0x00e0-0x00ef]
Sep  3 17:11:52 ubuntu kernel: [    3.490861] pnp 00:0a: [io  0x04d0-0x04d1]
Sep  3 17:11:52 ubuntu kernel: [    3.490864] pnp 00:0a: [io  0x040b]
Sep  3 17:11:52 ubuntu kernel: [    3.490866] pnp 00:0a: [io  0x04d6]
Sep  3 17:11:52 ubuntu kernel: [    3.490869] pnp 00:0a: [io  0x0c00-0x0c01]
Sep  3 17:11:52 ubuntu kernel: [    3.490871] pnp 00:0a: [io  0x0c14]
Sep  3 17:11:52 ubuntu kernel: [    3.490874] pnp 00:0a: [io  0x0c50-0x0c51]
Sep  3 17:11:52 ubuntu kernel: [    3.490876] pnp 00:0a: [io  0x0c52]
Sep  3 17:11:52 ubuntu kernel: [    3.490878] pnp 00:0a: [io  0x0c6c]
Sep  3 17:11:52 ubuntu kernel: [    3.490881] pnp 00:0a: [io  0x0c6f]
Sep  3 17:11:52 ubuntu kernel: [    3.490883] pnp 00:0a: [io  0x0cd0-0x0cd1]
Sep  3 17:11:52 ubuntu kernel: [    3.490886] pnp 00:0a: [io  0x0cd2-0x0cd3]
Sep  3 17:11:52 ubuntu kernel: [    3.490888] pnp 00:0a: [io  0x0cd4-0x0cd5]
Sep  3 17:11:52 ubuntu kernel: [    3.490891] pnp 00:0a: [io  0x0cd6-0x0cd7]
Sep  3 17:11:52 ubuntu kernel: [    3.490893] pnp 00:0a: [io  0x0cd8-0x0cdf]
Sep  3 17:11:52 ubuntu kernel: [    3.490896] pnp 00:0a: [io  0x0800-0x089f]
Sep  3 17:11:52 ubuntu kernel: [    3.490898] pnp 00:0a: [io  0x0b10-0x0b1f]
Sep  3 17:11:52 ubuntu kernel: [    3.490901] pnp 00:0a: [io  0x0000-0xffffffff disabled]
Sep  3 17:11:52 ubuntu kernel: [    3.490904] pnp 00:0a: [io  0x0900-0x090f]
Sep  3 17:11:52 ubuntu kernel: [    3.490906] pnp 00:0a: [io  0x0910-0x091f]
Sep  3 17:11:52 ubuntu kernel: [    3.490909] pnp 00:0a: [io  0xfe00-0xfefe]
Sep  3 17:11:52 ubuntu kernel: [    3.490912] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Sep  3 17:11:52 ubuntu kernel: [    3.490914] pnp 00:0a: [mem 0xfff80000-0xffffffff]
Sep  3 17:11:52 ubuntu kernel: [    3.491017] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491021] system 00:0a: [io  0x040b] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491024] system 00:0a: [io  0x04d6] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491027] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491030] system 00:0a: [io  0x0c14] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491033] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491037] system 00:0a: [io  0x0c52] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491040] system 00:0a: [io  0x0c6c] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491043] system 00:0a: [io  0x0c6f] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491046] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491049] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491053] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491056] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491060] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491063] system 00:0a: [io  0x0800-0x089f] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491066] system 00:0a: [io  0x0b10-0x0b1f] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491070] system 00:0a: [io  0x0900-0x090f] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491073] system 00:0a: [io  0x0910-0x091f] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491077] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491081] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491084] system 00:0a: [mem 0xfff80000-0xffffffff] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491088] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.491222] pnp 00:0b: [io  0x0000-0xffffffff disabled]
Sep  3 17:11:52 ubuntu kernel: [    3.491225] pnp 00:0b: [io  0x0600-0x06df]
Sep  3 17:11:52 ubuntu kernel: [    3.491228] pnp 00:0b: [io  0x0ae0-0x0aef]
Sep  3 17:11:52 ubuntu kernel: [    3.491283] system 00:0b: [io  0x0600-0x06df] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491286] system 00:0b: [io  0x0ae0-0x0aef] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491290] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.491326] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Sep  3 17:11:52 ubuntu kernel: [    3.491381] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491385] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.491594] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Sep  3 17:11:52 ubuntu kernel: [    3.491597] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Sep  3 17:11:52 ubuntu kernel: [    3.491600] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Sep  3 17:11:52 ubuntu kernel: [    3.491603] pnp 00:0d: [mem 0x00100000-0x77ffffff]
Sep  3 17:11:52 ubuntu kernel: [    3.491606] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Sep  3 17:11:52 ubuntu kernel: [    3.491668] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491672] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491675] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491679] system 00:0d: [mem 0x00100000-0x77ffffff] could not be reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491683] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Sep  3 17:11:52 ubuntu kernel: [    3.491687] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Sep  3 17:11:52 ubuntu kernel: [    3.491804] pnp: PnP ACPI: found 14 devices
Sep  3 17:11:52 ubuntu kernel: [    3.491806] ACPI: ACPI bus type pnp unregistered
Sep  3 17:11:52 ubuntu kernel: [    3.491810] PnPBIOS: Disabled by ACPI PNP
Sep  3 17:11:52 ubuntu kernel: [    3.528480] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Sep  3 17:11:52 ubuntu kernel: [    3.528484] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Sep  3 17:11:52 ubuntu kernel: [    3.528489] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528493] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Sep  3 17:11:52 ubuntu kernel: [    3.528498] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Sep  3 17:11:52 ubuntu kernel: [    3.528502] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
Sep  3 17:11:52 ubuntu kernel: [    3.528506] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528510] pci 0000:00:07.0:   bridge window [mem pref disabled]
Sep  3 17:11:52 ubuntu kernel: [    3.528515] pci 0000:00:14.4: PCI bridge to [bus 03-03]
Sep  3 17:11:52 ubuntu kernel: [    3.528517] pci 0000:00:14.4:   bridge window [io  disabled]
Sep  3 17:11:52 ubuntu kernel: [    3.528524] pci 0000:00:14.4:   bridge window [mem disabled]
Sep  3 17:11:52 ubuntu kernel: [    3.528529] pci 0000:00:14.4:   bridge window [mem pref disabled]
Sep  3 17:11:52 ubuntu kernel: [    3.528545] pci 0000:00:07.0: setting latency timer to 64
Sep  3 17:11:52 ubuntu kernel: [    3.528555] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528558] pci_bus 0000:00: resource 5 [mem 0x80000000-0xffffffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528561] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528564] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
Sep  3 17:11:52 ubuntu kernel: [    3.528567] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528570] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
Sep  3 17:11:52 ubuntu kernel: [    3.528574] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
Sep  3 17:11:52 ubuntu kernel: [    3.528577] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528580] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528583] pci_bus 0000:03: resource 5 [mem 0x80000000-0xffffffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528586] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Sep  3 17:11:52 ubuntu kernel: [    3.528630] NET: Registered protocol family 2
Sep  3 17:11:52 ubuntu kernel: [    3.528705] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  3 17:11:52 ubuntu kernel: [    3.529013] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  3 17:11:52 ubuntu kernel: [    3.529763] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  3 17:11:52 ubuntu kernel: [    3.530200] TCP: Hash tables configured (established 131072 bind 65536)
Sep  3 17:11:52 ubuntu kernel: [    3.530203] TCP reno registered
Sep  3 17:11:52 ubuntu kernel: [    3.530208] UDP hash table entries: 512 (order: 2, 16384 bytes)
Sep  3 17:11:52 ubuntu kernel: [    3.530222] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Sep  3 17:11:52 ubuntu kernel: [    3.530330] NET: Registered protocol family 1
Sep  3 17:11:52 ubuntu kernel: [    3.652056] pci 0000:01:05.0: Boot video device
Sep  3 17:11:52 ubuntu kernel: [    3.652062] PCI: CLS 64 bytes, default 64
Sep  3 17:11:52 ubuntu kernel: [    3.652365] cpufreq-nforce2: No nForce2 chipset.
Sep  3 17:11:52 ubuntu kernel: [    3.652521] audit: initializing netlink socket (disabled)
Sep  3 17:11:52 ubuntu kernel: [    3.652532] type=2000 audit(1315069823.648:1): initialized
Sep  3 17:11:52 ubuntu kernel: [    3.664144] highmem bounce pool size: 64 pages
Sep  3 17:11:52 ubuntu kernel: [    3.664150] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Sep  3 17:11:52 ubuntu kernel: [    3.666214] VFS: Disk quotas dquot_6.5.2
Sep  3 17:11:52 ubuntu kernel: [    3.666283] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  3 17:11:52 ubuntu kernel: [    3.667075] fuse init (API version 7.16)
Sep  3 17:11:52 ubuntu kernel: [    3.667198] msgmni has been set to 1706
Sep  3 17:11:52 ubuntu kernel: [    3.667530] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Sep  3 17:11:52 ubuntu kernel: [    3.667571] io scheduler noop registered
Sep  3 17:11:52 ubuntu kernel: [    3.667574] io scheduler deadline registered
Sep  3 17:11:52 ubuntu kernel: [    3.667594] io scheduler cfq registered (default)
Sep  3 17:11:52 ubuntu kernel: [    3.667739] pcieport 0000:00:07.0: setting latency timer to 64
Sep  3 17:11:52 ubuntu kernel: [    3.667779] pcieport 0000:00:07.0: irq 40 for MSI/MSI-X
Sep  3 17:11:52 ubuntu kernel: [    3.667874] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  3 17:11:52 ubuntu kernel: [    3.667903] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep  3 17:11:52 ubuntu kernel: [    3.668098] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Sep  3 17:11:52 ubuntu kernel: [    3.700019] ACPI: Power Button [PWRB]
Sep  3 17:11:52 ubuntu kernel: [    3.700095] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Sep  3 17:11:52 ubuntu kernel: [    3.700101] ACPI: Power Button [PWRF]
Sep  3 17:11:52 ubuntu kernel: [    3.700296] ACPI: acpi_idle registered with cpuidle
Sep  3 17:11:52 ubuntu kernel: [    3.700321] ACPI: duty_cycle spans bit 4
Sep  3 17:11:52 ubuntu kernel: [    3.702083] ERST: Table is not found!
Sep  3 17:11:52 ubuntu kernel: [    3.702127] isapnp: Scanning for PnP cards...
Sep  3 17:11:52 ubuntu kernel: [    3.702185] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Sep  3 17:11:52 ubuntu kernel: [    4.056041] isapnp: No Plug &amp; Play device found
Sep  3 17:11:52 ubuntu kernel: [    4.188453] Linux agpgart interface v0.103
Sep  3 17:11:52 ubuntu kernel: [    4.190126] brd: module loaded
Sep  3 17:11:52 ubuntu kernel: [    4.190799] loop: module loaded
Sep  3 17:11:52 ubuntu kernel: [    4.190915] i2c-core: driver [adp5520] using legacy suspend method
Sep  3 17:11:52 ubuntu kernel: [    4.190918] i2c-core: driver [adp5520] using legacy resume method
Sep  3 17:11:52 ubuntu kernel: [    4.191089] pata_acpi 0000:00:14.1: PCI INT A -&gt; GSI 16 (level, low) -&gt; IRQ 16
Sep  3 17:11:52 ubuntu kernel: [    4.191133] pata_acpi 0000:00:14.1: setting latency timer to 64
Sep  3 17:11:52 ubuntu kernel: [    4.191581] Fixed MDIO Bus: probed
Sep  3 17:11:52 ubuntu kernel: [    4.191631] PPP generic driver version 2.4.2
Sep  3 17:11:52 ubuntu kernel: [    4.191676] tun: Universal TUN/TAP device driver, 1.6
Sep  3 17:11:52 ubuntu kernel: [    4.191679] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep  3 17:11:52 ubuntu kernel: [    4.191777] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep  3 17:11:52 ubuntu kernel: [    4.191799] ehci_hcd 0000:00:13.5: PCI INT D -&gt; GSI 19 (level, low) -&gt; IRQ 19
Sep  3 17:11:52 ubuntu kernel: [    4.191817] ehci_hcd 0000:00:13.5: EHCI Host Controller
Sep  3 17:11:52 ubuntu kernel: [    4.191859] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
Sep  3 17:11:52 ubuntu kernel: [    4.191940] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
Sep  3 17:11:52 ubuntu kernel: [    4.191957] ehci_hcd 0000:00:13.5: debug port 1
Sep  3 17:11:52 ubuntu kernel: [    4.191986] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe8ff000
Sep  3 17:11:52 ubuntu kernel: [    4.200019] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
Sep  3 17:11:52 ubuntu kernel: [    4.200172] hub 1-0:1.0: USB hub found
Sep  3 17:11:52 ubuntu kernel: [    4.200178] hub 1-0:1.0: 10 ports detected
Sep  3 17:11:52 ubuntu kernel: [    4.200298] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep  3 17:11:52 ubuntu kernel: [    4.200320] ohci_hcd 0000:00:13.0: PCI INT A -&gt; GSI 16 (level, low) -&gt; IRQ 16
Sep  3 17:11:52 ubuntu kernel: [    4.200342] ohci_hcd 0000:00:13.0: OHCI Host Controller
Sep  3 17:11:52 ubuntu kernel: [    4.200393] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
Sep  3 17:11:52 ubuntu kernel: [    4.200448] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe8fe000
Sep  3 17:11:52 ubuntu kernel: [    4.260161] hub 2-0:1.0: USB hub found
Sep  3 17:11:52 ubuntu kernel: [    4.260169] hub 2-0:1.0: 2 ports detected
Sep  3 17:11:52 ubuntu kernel: [    4.260259] ohci_hcd 0000:00:13.1: PCI INT B -&gt; GSI 17 (level, low) -&gt; IRQ 17
Sep  3 17:11:52 ubuntu kernel: [    4.260273] ohci_hcd 0000:00:13.1: OHCI Host Controller
Sep  3 17:11:52 ubuntu kernel: [    4.260315] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
Sep  3 17:11:52 ubuntu kernel: [    4.260365] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe8fd000
Sep  3 17:11:52 ubuntu kernel: [    4.320131] hub 3-0:1.0: USB hub found
Sep  3 17:11:52 ubuntu kernel: [    4.320138] hub 3-0:1.0: 2 ports detected
Sep  3 17:11:52 ubuntu kernel: [    4.320235] ohci_hcd 0000:00:13.2: PCI INT C -&gt; GSI 18 (level, low) -&gt; IRQ 18
Sep  3 17:11:52 ubuntu kernel: [    4.320248] ohci_hcd 0000:00:13.2: OHCI Host Controller
Sep  3 17:11:52 ubuntu kernel: [    4.320299] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
Sep  3 17:11:52 ubuntu kernel: [    4.324048] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe8fc000
Sep  3 17:11:52 ubuntu kernel: [    4.384138] hub 4-0:1.0: USB hub found
Sep  3 17:11:52 ubuntu kernel: [    4.384145] hub 4-0:1.0: 2 ports detected
Sep  3 17:11:52 ubuntu kernel: [    4.384222] ohci_hcd 0000:00:13.3: PCI INT B -&gt; GSI 17 (level, low) -&gt; IRQ 17
Sep  3 17:11:52 ubuntu kernel: [    4.384235] ohci_hcd 0000:00:13.3: OHCI Host Controller
Sep  3 17:11:52 ubuntu kernel: [    4.384279] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
Sep  3 17:11:52 ubuntu kernel: [    4.384318] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe8fb000
Sep  3 17:11:52 ubuntu kernel: [    4.444127] hub 5-0:1.0: USB hub found
Sep  3 17:11:52 ubuntu kernel: [    4.444134] hub 5-0:1.0: 2 ports detected
Sep  3 17:11:52 ubuntu kernel: [    4.444214] ohci_hcd 0000:00:13.4: PCI INT C -&gt; GSI 18 (level, low) -&gt; IRQ 18
Sep  3 17:11:52 ubuntu kernel: [    4.444227] ohci_hcd 0000:00:13.4: OHCI Host Controller
Sep  3 17:11:52 ubuntu kernel: [    4.444275] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
Sep  3 17:11:52 ubuntu kernel: [    4.444313] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe8fa000
Sep  3 17:11:52 ubuntu kernel: [    4.504140] hub 6-0:1.0: USB hub found
Sep  3 17:11:52 ubuntu kernel: [    4.504148] hub 6-0:1.0: 2 ports detected
Sep  3 17:11:52 ubuntu kernel: [    4.504229] uhci_hcd: USB Universal Host Controller Interface driver
Sep  3 17:11:52 ubuntu kernel: [    4.504332] i8042: PNP: No PS/2 controller found. Probing ports directly.
Sep  3 17:11:52 ubuntu kernel: [    4.506831] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  3 17:11:52 ubuntu kernel: [    4.506838] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  3 17:11:52 ubuntu kernel: [    4.506976] mousedev: PS/2 mouse device common for all mice
Sep  3 17:11:52 ubuntu kernel: [    4.507128] rtc_cmos 00:03: RTC can wake from S4
Sep  3 17:11:52 ubuntu kernel: [    4.508082] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Sep  3 17:11:52 ubuntu kernel: [    4.508112] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Sep  3 17:11:52 ubuntu kernel: [    4.508226] device-mapper: uevent: version 1.0.3
Sep  3 17:11:52 ubuntu kernel: [    4.508322] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Sep  3 17:11:52 ubuntu kernel: [    4.508444] device-mapper: multipath: version 1.2.0 loaded
Sep  3 17:11:52 ubuntu kernel: [    4.508447] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep  3 17:11:52 ubuntu kernel: [    4.508546] EISA: Probing bus 0 at eisa.0
Sep  3 17:11:52 ubuntu kernel: [    4.508549] EISA: Cannot allocate resource for mainboard
Sep  3 17:11:52 ubuntu kernel: [    4.508552] Cannot allocate resource for EISA slot 1
Sep  3 17:11:52 ubuntu kernel: [    4.508555] Cannot allocate resource for EISA slot 2
Sep  3 17:11:52 ubuntu kernel: [    4.508558] Cannot allocate resource for EISA slot 3
Sep  3 17:11:52 ubuntu kernel: [    4.508560] Cannot allocate resource for EISA slot 4
Sep  3 17:11:52 ubuntu kernel: [    4.508563] Cannot allocate resource for EISA slot 5
Sep  3 17:11:52 ubuntu kernel: [    4.508565] Cannot allocate resource for EISA slot 6
Sep  3 17:11:52 ubuntu kernel: [    4.508568] Cannot allocate resource for EISA slot 7
Sep  3 17:11:52 ubuntu kernel: [    4.508571] Cannot allocate resource for EISA slot 8
Sep  3 17:11:52 ubuntu kernel: [    4.508573] EISA: Detected 0 cards.
Sep  3 17:11:52 ubuntu kernel: [    4.508662] cpuidle: using governor ladder
Sep  3 17:11:52 ubuntu kernel: [    4.508664] cpuidle: using governor menu
Sep  3 17:11:52 ubuntu kernel: [    4.508982] TCP cubic registered
Sep  3 17:11:52 ubuntu kernel: [    4.509129] NET: Registered protocol family 10
Sep  3 17:11:52 ubuntu kernel: [    4.509752] NET: Registered protocol family 17
Sep  3 17:11:52 ubuntu kernel: [    4.509774] Registering the dns_resolver key type
Sep  3 17:11:52 ubuntu kernel: [    4.509800] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (2 cpu cores) (version 2.20.00)
Sep  3 17:11:52 ubuntu kernel: [    4.509810] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
Sep  3 17:11:52 ubuntu kernel: [    4.509812] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
Sep  3 17:11:52 ubuntu kernel: [    4.509836] Using IPI No-Shortcut mode
Sep  3 17:11:52 ubuntu kernel: [    4.509957] PM: Hibernation image not present or could not be loaded.
Sep  3 17:11:52 ubuntu kernel: [    4.509972] registered taskstats version 1
Sep  3 17:11:52 ubuntu kernel: [    4.510426]   Magic number: 11:661:187
Sep  3 17:11:52 ubuntu kernel: [    4.510531] rtc_cmos 00:03: setting system clock to 2011-09-03 17:10:24 UTC (1315069824)
Sep  3 17:11:52 ubuntu kernel: [    4.510535] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  3 17:11:52 ubuntu kernel: [    4.510537] EDD information not available.
Sep  3 17:11:52 ubuntu kernel: [    4.510657] Freeing unused kernel memory: 700k freed
Sep  3 17:11:52 ubuntu kernel: [    4.511072] Write protecting the kernel text: 5192k
Sep  3 17:11:52 ubuntu kernel: [    4.511122] Write protecting the kernel read-only data: 2148k
Sep  3 17:11:52 ubuntu kernel: [    4.545860] &lt;30&gt;udev[69]: starting version 167
Sep  3 17:11:52 ubuntu kernel: [    4.568058] usb 1-7: new high speed USB device using ehci_hcd and address 3
Sep  3 17:11:52 ubuntu kernel: [    4.647381] scsi0 : pata_atiixp
Sep  3 17:11:52 ubuntu kernel: [    4.650194] scsi1 : pata_atiixp
Sep  3 17:11:52 ubuntu kernel: [    4.650918] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Sep  3 17:11:52 ubuntu kernel: [    4.650922] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Sep  3 17:11:52 ubuntu kernel: [    4.666183] Floppy drive(s): fd0 is 1.44M
Sep  3 17:11:52 ubuntu kernel: [    4.680145] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Sep  3 17:11:52 ubuntu kernel: [    4.680173] r8169 0000:02:00.0: PCI INT A -&gt; GSI 19 (level, low) -&gt; IRQ 19
Sep  3 17:11:52 ubuntu kernel: [    4.680217] r8169 0000:02:00.0: setting latency timer to 64
Sep  3 17:11:52 ubuntu kernel: [    4.680283] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
Sep  3 17:11:52 ubuntu kernel: [    4.681355] r8169 0000:02:00.0: eth0: RTL8101e at 0xf8010000, 00:19:db:70:29:6d, XID 14000000 IRQ 41
Sep  3 17:11:52 ubuntu kernel: [    4.683867] FDC 0 is a post-1991 82077
Sep  3 17:11:52 ubuntu kernel: [    4.812556] ata1.00: ATAPI: HL-DT-STDVD-RAM GH22NP21, 1.00, max UDMA/66
Sep  3 17:11:52 ubuntu kernel: [    4.828479] ata1.00: configured for UDMA/66
Sep  3 17:11:52 ubuntu kernel: [    4.830712] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP21 1.00 PQ: 0 ANSI: 5
Sep  3 17:11:52 ubuntu kernel: [    4.832443] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep  3 17:11:52 ubuntu kernel: [    4.832446] cdrom: Uniform CD-ROM driver Revision: 3.20
Sep  3 17:11:52 ubuntu kernel: [    4.832607] sr 0:0:0:0: Attached scsi CD-ROM sr0
Sep  3 17:11:52 ubuntu kernel: [    4.832701] sr 0:0:0:0: Attached scsi generic sg0 type 5
Sep  3 17:11:52 ubuntu kernel: [    4.840154] ahci 0000:00:12.0: version 3.0
Sep  3 17:11:52 ubuntu kernel: [    4.840188] ahci 0000:00:12.0: PCI INT A -&gt; GSI 22 (level, low) -&gt; IRQ 22
Sep  3 17:11:52 ubuntu kernel: [    4.840223] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Sep  3 17:11:52 ubuntu kernel: [    4.840358] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Sep  3 17:11:52 ubuntu kernel: [    4.840363] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio ccc 
Sep  3 17:11:52 ubuntu kernel: [    4.842486] scsi2 : ahci
Sep  3 17:11:52 ubuntu kernel: [    4.845954] scsi3 : ahci
Sep  3 17:11:52 ubuntu kernel: [    4.846171] scsi4 : ahci
Sep  3 17:11:52 ubuntu kernel: [    4.846292] scsi5 : ahci
Sep  3 17:11:52 ubuntu kernel: [    4.846434] ata3: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff900 irq 22
Sep  3 17:11:52 ubuntu kernel: [    4.846438] ata4: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff980 irq 22
Sep  3 17:11:52 ubuntu kernel: [    4.846443] ata5: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa00 irq 22
Sep  3 17:11:52 ubuntu kernel: [    4.846447] ata6: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa80 irq 22
Sep  3 17:11:52 ubuntu kernel: [    4.867716] [drm] Initialized drm 1.1.0 20060810
Sep  3 17:11:52 ubuntu kernel: [    4.996027] usb 1-8: new high speed USB device using ehci_hcd and address 4
Sep  3 17:11:52 ubuntu kernel: [    5.136672] usbcore: registered new interface driver uas
Sep  3 17:11:52 ubuntu kernel: [    5.164039] ata4: SATA link down (SStatus 0 SControl 300)
Sep  3 17:11:52 ubuntu kernel: [    5.164109] ata6: SATA link down (SStatus 0 SControl 300)
Sep  3 17:11:52 ubuntu kernel: [    5.164147] ata5: SATA link down (SStatus 0 SControl 300)
Sep  3 17:11:52 ubuntu kernel: [    5.320017] usb 3-2: new low speed USB device using ohci_hcd and address 2
Sep  3 17:11:52 ubuntu kernel: [    5.336020] ata3: softreset failed (device not ready)
Sep  3 17:11:52 ubuntu kernel: [    5.336025] ata3: applying SB600 PMP SRST workaround and retrying
Sep  3 17:11:52 ubuntu kernel: [    5.508057] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  3 17:11:52 ubuntu kernel: [    5.538789] ata3.00: ATA-7: ST380811AS, 3.AAE, max UDMA/133
Sep  3 17:11:52 ubuntu kernel: [    5.538795] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Sep  3 17:11:52 ubuntu kernel: [    5.538800] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
Sep  3 17:11:52 ubuntu kernel: [    5.552124] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input2
Sep  3 17:11:52 ubuntu kernel: [    5.552250] generic-usb 0003:046E:5542.0001: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:13.1-2/input0
Sep  3 17:11:52 ubuntu kernel: [    5.572137] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.1/input/input3
Sep  3 17:11:52 ubuntu kernel: [    5.572317] generic-usb 0003:046E:5542.0002: input,hiddev0,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:13.1-2/input1
Sep  3 17:11:52 ubuntu kernel: [    5.572581] usbcore: registered new interface driver usbhid
Sep  3 17:11:52 ubuntu kernel: [    5.572584] usbhid: USB HID core driver
Sep  3 17:11:52 ubuntu kernel: [    5.597100] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
Sep  3 17:11:52 ubuntu kernel: [    5.597103] ata3.00: configured for UDMA/133
Sep  3 17:11:52 ubuntu kernel: [    5.597278] scsi 2:0:0:0: Direct-Access     ATA      ST380811AS       3.AA PQ: 0 ANSI: 5
Sep  3 17:11:52 ubuntu kernel: [    5.597495] sd 2:0:0:0: Attached scsi generic sg1 type 0
Sep  3 17:11:52 ubuntu kernel: [    5.597543] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Sep  3 17:11:52 ubuntu kernel: [    5.597625] sd 2:0:0:0: [sda] Write Protect is off
Sep  3 17:11:52 ubuntu kernel: [    5.597629] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  3 17:11:52 ubuntu kernel: [    5.597652] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  3 17:11:52 ubuntu kernel: [    5.645177]  sda: sda1
Sep  3 17:11:52 ubuntu kernel: [    5.645482] sd 2:0:0:0: [sda] Attached SCSI disk
Sep  3 17:11:52 ubuntu kernel: [    5.658578] Initializing USB Mass Storage driver...
Sep  3 17:11:52 ubuntu kernel: [    5.668475] scsi6 : usb-storage 1-8:1.0
Sep  3 17:11:52 ubuntu kernel: [    5.674986] usbcore: registered new interface driver usb-storage
Sep  3 17:11:52 ubuntu kernel: [    5.674989] USB Mass Storage support registered.
Sep  3 17:11:52 ubuntu kernel: [    5.712638] [drm] radeon defaulting to kernel modesetting.
Sep  3 17:11:52 ubuntu kernel: [    5.712642] [drm] radeon kernel modesetting enabled.
Sep  3 17:11:52 ubuntu kernel: [    5.712733] radeon 0000:01:05.0: PCI INT A -&gt; GSI 18 (level, low) -&gt; IRQ 18
Sep  3 17:11:52 ubuntu kernel: [    5.714668] [drm] initializing kernel modesetting (RS690 0x1002:0x791E).
Sep  3 17:11:52 ubuntu kernel: [    5.714696] [drm] register mmio base: 0xFEAF0000
Sep  3 17:11:52 ubuntu kernel: [    5.714698] [drm] register mmio size: 65536
Sep  3 17:11:52 ubuntu kernel: [    5.715758] ATOM BIOS: ATI
Sep  3 17:11:52 ubuntu kernel: [    5.715787] radeon 0000:01:05.0: VRAM: 128M 0x0000000078000000 - 0x000000007FFFFFFF (128M used)
Sep  3 17:11:52 ubuntu kernel: [    5.715791] radeon 0000:01:05.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
Sep  3 17:11:52 ubuntu kernel: [    5.715817] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Sep  3 17:11:52 ubuntu kernel: [    5.715819] [drm] Driver supports precise vblank timestamp query.
Sep  3 17:11:52 ubuntu kernel: [    5.715829] [drm] radeon: irq initialized.
Sep  3 17:11:52 ubuntu kernel: [    5.716109] [drm] Detected VRAM RAM=128M, BAR=128M
Sep  3 17:11:52 ubuntu kernel: [    5.716114] [drm] RAM width 128bits DDR
Sep  3 17:11:52 ubuntu kernel: [    5.716221] [TTM] Zone  kernel: Available graphics memory: 437138 kiB.
Sep  3 17:11:52 ubuntu kernel: [    5.716226] [TTM] Zone highmem: Available graphics memory: 965430 kiB.
Sep  3 17:11:52 ubuntu kernel: [    5.716228] [TTM] Initializing pool allocator.
Sep  3 17:11:52 ubuntu kernel: [    5.716254] [drm] radeon: 128M of VRAM memory ready
Sep  3 17:11:52 ubuntu kernel: [    5.716257] [drm] radeon: 512M of GTT memory ready.
Sep  3 17:11:52 ubuntu kernel: [    5.716280] [drm] GART: num cpu pages 131072, num gpu pages 131072
Sep  3 17:11:52 ubuntu kernel: [    5.725577] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
Sep  3 17:11:52 ubuntu kernel: [    5.733544] radeon 0000:01:05.0: WB enabled
Sep  3 17:11:52 ubuntu kernel: [    5.733621] [drm] Loading RS690/RS740 Microcode
Sep  3 17:11:52 ubuntu kernel: [    5.736128] [drm] radeon: ring at 0x0000000080001000
Sep  3 17:11:52 ubuntu kernel: [    5.736148] [drm] ring test succeeded in 1 usecs
Sep  3 17:11:52 ubuntu kernel: [    5.736289] [drm] radeon: ib pool ready.
Sep  3 17:11:52 ubuntu kernel: [    5.736374] [drm] ib test succeeded in 0 usecs
Sep  3 17:11:52 ubuntu kernel: [    5.736377] [drm] Enabling audio support
Sep  3 17:11:52 ubuntu kernel: [    5.736385] failed to evaluate ATIF got AE_BAD_PARAMETER
Sep  3 17:11:52 ubuntu kernel: [    5.737264] [drm] Radeon Display Connectors
Sep  3 17:11:52 ubuntu kernel: [    5.737267] [drm] Connector 0:
Sep  3 17:11:52 ubuntu kernel: [    5.737269] [drm]   VGA
Sep  3 17:11:52 ubuntu kernel: [    5.737273] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
Sep  3 17:11:52 ubuntu kernel: [    5.737275] [drm]   Encoders:
Sep  3 17:11:52 ubuntu kernel: [    5.737277] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Sep  3 17:11:52 ubuntu kernel: [    5.737279] [drm] Connector 1:
Sep  3 17:11:52 ubuntu kernel: [    5.737281] [drm]   S-video
Sep  3 17:11:52 ubuntu kernel: [    5.737283] [drm]   Encoders:
Sep  3 17:11:52 ubuntu kernel: [    5.737285] [drm]     TV1: INTERNAL_KLDSCP_DAC1
Sep  3 17:11:52 ubuntu kernel: [    5.737287] [drm] Connector 2:
Sep  3 17:11:52 ubuntu kernel: [    5.737288] [drm]   HDMI-A
Sep  3 17:11:52 ubuntu kernel: [    5.737291] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
Sep  3 17:11:52 ubuntu kernel: [    5.737293] [drm]   Encoders:
Sep  3 17:11:52 ubuntu kernel: [    5.737295] [drm]     DFP3: INTERNAL_LVTM1
Sep  3 17:11:52 ubuntu kernel: [    5.768046] usb 6-2: new low speed USB device using ohci_hcd and address 2
Sep  3 17:11:52 ubuntu kernel: [    5.932994] [drm] fb mappable at 0xF0040000
Sep  3 17:11:52 ubuntu kernel: [    5.932998] [drm] vram apper at 0xF0000000
Sep  3 17:11:52 ubuntu kernel: [    5.933000] [drm] size 5763072
Sep  3 17:11:52 ubuntu kernel: [    5.933002] [drm] fb depth is 24
Sep  3 17:11:52 ubuntu kernel: [    5.933004] [drm]    pitch is 6400
Sep  3 17:11:52 ubuntu kernel: [    5.951626] input: Microsoft Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb6/6-2/6-2:1.0/input/input4
Sep  3 17:11:52 ubuntu kernel: [    5.951781] generic-usb 0003:045E:0084.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Basic Optical Mouse] on usb-0000:00:13.4-2/input0
Sep  3 17:11:52 ubuntu kernel: [    5.952522] Console: switching to colour frame buffer device 200x56
Sep  3 17:11:52 ubuntu kernel: [    5.964535] fb0: radeondrmfb frame buffer device
Sep  3 17:11:52 ubuntu kernel: [    5.964537] drm: registered panic notifier
Sep  3 17:11:52 ubuntu kernel: [    5.964546] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
Sep  3 17:11:52 ubuntu kernel: [    6.673129] scsi 6:0:0:0: Direct-Access     Lexar    JD Secure II +   1100 PQ: 0 ANSI: 0 CCS
Sep  3 17:11:52 ubuntu kernel: [    6.673866] sd 6:0:0:0: Attached scsi generic sg2 type 0
Sep  3 17:11:52 ubuntu kernel: [    6.675613] sd 6:0:0:0: [sdb] 1966080 512-byte logical blocks: (1.00 GB/960 MiB)
Sep  3 17:11:52 ubuntu kernel: [    6.676474] sd 6:0:0:0: [sdb] Write Protect is off
Sep  3 17:11:52 ubuntu kernel: [    6.676478] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
Sep  3 17:11:52 ubuntu kernel: [    6.677848] sd 6:0:0:0: [sdb] No Caching mode page present
Sep  3 17:11:52 ubuntu kernel: [    6.677850] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep  3 17:11:52 ubuntu kernel: [    6.682849] sd 6:0:0:0: [sdb] No Caching mode page present
Sep  3 17:11:52 ubuntu kernel: [    6.682852] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep  3 17:11:52 ubuntu kernel: [    6.683531]  sdb: sdb1
Sep  3 17:11:52 ubuntu kernel: [    6.688232] sd 6:0:0:0: [sdb] No Caching mode page present
Sep  3 17:11:52 ubuntu kernel: [    6.688238] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep  3 17:11:52 ubuntu kernel: [    6.688243] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Sep  3 17:11:52 ubuntu kernel: [   10.211529] Btrfs loaded
Sep  3 17:11:52 ubuntu kernel: [   10.219801] xor: automatically using best checksumming function: pIII_sse
Sep  3 17:11:52 ubuntu kernel: [   10.236013]    pIII_sse  :  6053.000 MB/sec
Sep  3 17:11:52 ubuntu kernel: [   10.236016] xor: using function: pIII_sse (6053.000 MB/sec)
Sep  3 17:11:52 ubuntu kernel: [   10.239293] device-mapper: dm-raid45: initialized v0.2594b
Sep  3 17:11:52 ubuntu kernel: [   14.129238] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   14.129244] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   14.129248] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   14.129254] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   14.129260] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   14.129270] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   14.129275] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   14.659436] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   14.659439] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   14.659442] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   14.659447] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   14.659451] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   14.659460] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   14.659463] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   15.116652] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   15.116654] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   15.116658] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   15.116662] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   15.116667] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   15.116675] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   15.116678] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   15.573760] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   15.573762] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   15.573766] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   15.573770] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   15.573774] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   15.573783] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   15.573786] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   15.994396] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   15.994399] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   15.994402] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   15.994406] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   15.994410] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   15.994419] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   15.994422] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   16.449358] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   16.449361] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   16.449365] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   16.449369] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   16.449373] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   16.449382] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   16.449386] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   16.868801] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   16.868804] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   16.868807] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   16.868812] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   16.868816] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   16.868825] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   16.868828] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   17.532109] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   17.532112] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   17.532116] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   17.532120] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   17.532125] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   17.532133] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   17.532136] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   17.950809] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   17.950811] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   17.950815] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   17.950819] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   17.950823] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   17.950832] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   17.950835] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   18.403827] sr 0:0:0:0: [sr0] Unhandled sense code
Sep  3 17:11:52 ubuntu kernel: [   18.403829] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep  3 17:11:52 ubuntu kernel: [   18.403833] sr 0:0:0:0: [sr0]  Sense Key : Medium Error [current] 
Sep  3 17:11:52 ubuntu kernel: [   18.403837] sr 0:0:0:0: [sr0]  Add. Sense: Unrecovered read error
Sep  3 17:11:52 ubuntu kernel: [   18.403842] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5a 98 00 00 01 00
Sep  3 17:11:52 ubuntu kernel: [   18.403850] end_request: I/O error, dev sr0, sector 1403488
Sep  3 17:11:52 ubuntu kernel: [   18.403853] Buffer I/O error on device sr0, logical block 350872
Sep  3 17:11:52 ubuntu kernel: [   19.931357] ISO 9660 Extensions: Microsoft Joliet Level 3
Sep  3 17:11:52 ubuntu kernel: [   19.980857] ISO 9660 Extensions: RRIP_1991A
Sep  3 17:11:52 ubuntu kernel: [   20.253598] aufs 2.1-standalone.tree-38-rcN-20110207
Sep  3 17:11:52 ubuntu kernel: [   20.353127] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Sep  3 17:11:54 ubuntu kernel: [   94.462220] &lt;30&gt;udev[1232]: starting version 167
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Successfully dropped root privileges.
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: avahi-daemon 0.6.30 starting up.
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Successfully called chroot().
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Successfully dropped remaining capabilities.
Sep  3 17:11:54 ubuntu avahi-daemon[1245]: chroot.c: open() failed: No such file or directory
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Failed to open /etc/resolv.conf: Invalid argument
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Loading service file /services/udisks.service.
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Network interface enumeration completed.
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Registering HINFO record with values 'I686'/'LINUX'.
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2734576883.
Sep  3 17:11:54 ubuntu avahi-daemon[1242]: Service "ubuntu" (/services/udisks.service) successfully established.
Sep  3 17:11:56 ubuntu NetworkManager[1451]: <info> NetworkManager (version 0.8.3.998) is starting...
Sep  3 17:11:56 ubuntu NetworkManager[1451]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep  3 17:11:58 ubuntu NetworkManager[1451]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep  3 17:11:58 ubuntu NetworkManager[1451]: <info> trying to start the modem manager...
Sep  3 17:11:58 ubuntu modem-manager[1531]: <info>  ModemManager (version 0.4) starting...
Sep  3 17:11:59 ubuntu modem-manager[1531]: <info>  Loaded plugin AnyData
Sep  3 17:11:59 ubuntu modem-manager[1531]: <info>  Loaded plugin Generic
Sep  3 17:11:59 ubuntu modem-manager[1531]: <info>  Loaded plugin Gobi
Sep  3 17:11:59 ubuntu modem-manager[1531]: <info>  Loaded plugin Option High-Speed
Sep  3 17:11:59 ubuntu modem-manager[1531]: <info>  Loaded plugin Huawei
Sep  3 17:11:59 ubuntu modem-manager[1531]: <info>  Loaded plugin Linktop
Sep  3 17:11:59 ubuntu modem-manager[1531]: <info>  Loaded plugin Longcheer
Sep  3 17:11:59 ubuntu polkitd[1536]: started daemon version 0.101 using authority implementation `local' version `0.101'
Sep  3 17:11:59 ubuntu NetworkManager[1451]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep  3 17:11:59 ubuntu modem-manager[1531]: <info>  Loaded plugin Ericsson MBM
Sep  3 17:12:00 ubuntu kernel: [  100.105275] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  3 17:12:00 ubuntu kernel: [  100.211132] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Sep  3 17:12:00 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: init!
Sep  3 17:12:00 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: update_system_hostname
Sep  3 17:12:00 ubuntu NetworkManager[1451]:    SCPluginIfupdown: management mode: unmanaged
Sep  3 17:12:00 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0, iface: eth0)
Sep  3 17:12:00 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep  3 17:12:00 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep  3 17:12:00 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep  3 17:12:00 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: end _init.
Sep  3 17:12:00 ubuntu NetworkManager[1451]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep  3 17:12:00 ubuntu kernel: [  100.365735] cfg80211: Calling CRDA to update world regulatory domain
Sep  3 17:12:00 ubuntu kernel: [  100.442836] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMOV [io 0xb00-0xb06]
Sep  3 17:12:00 ubuntu kernel: [  100.442841] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep  3 17:12:00 ubuntu modem-manager[1531]: <info>  Loaded plugin MotoC
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep  3 17:12:01 ubuntu NetworkManager[1451]:    Ifupdown: get unmanaged devices count: 0
Sep  3 17:12:01 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: (157522976) ... get_connections.
Sep  3 17:12:01 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: (157522976) ... get_connections (managed=false): return empty list.
Sep  3 17:12:01 ubuntu NetworkManager[1451]:    Ifupdown: get unmanaged devices count: 0
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> Networking is enabled by state file
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> (eth0): carrier is OFF
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> (eth0): now managed
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> (eth0): device state change: 1 -&gt; 2 (reason 2)
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> (eth0): bringing up device.
Sep  3 17:12:01 ubuntu kernel: [  101.423813] r8169 0000:02:00.0: eth0: link down
Sep  3 17:12:01 ubuntu kernel: [  101.423825] r8169 0000:02:00.0: eth0: link down
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> (eth0): preparing device.
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> (eth0): deactivating device (reason: 2).
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0
Sep  3 17:12:01 ubuntu kernel: [  101.424454] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  3 17:12:01 ubuntu modem-manager[1531]: <info>  Loaded plugin Nokia
Sep  3 17:12:01 ubuntu modem-manager[1531]: <info>  Loaded plugin Novatel
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> modem-manager is now available
Sep  3 17:12:01 ubuntu modem-manager[1531]: <info>  Loaded plugin Option
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep  3 17:12:01 ubuntu modem-manager[1531]: <info>  Loaded plugin Sierra
Sep  3 17:12:01 ubuntu NetworkManager[1451]: <info> Trying to start the supplicant...
Sep  3 17:12:01 ubuntu modem-manager[1531]: <info>  Loaded plugin SimTech
Sep  3 17:12:01 ubuntu modem-manager[1531]: <info>  Loaded plugin X22X
Sep  3 17:12:02 ubuntu kernel: [  102.150003] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Sep  3 17:12:02 ubuntu kernel: [  102.151232] SP5100 TCO timer: mmio address 0xfec000f0 already in use
Sep  3 17:12:02 ubuntu modem-manager[1531]: <info>  Loaded plugin ZTE
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> (eth0): carrier now ON (device state 2)
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> (eth0): device state change: 2 -&gt; 3 (reason 40)
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) starting connection 'Auto eth0'
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> (eth0): device state change: 3 -&gt; 4 (reason 0)
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> (eth0): device state change: 4 -&gt; 5 (reason 0)
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep  3 17:12:02 ubuntu kernel: [  102.981282] r8169 0000:02:00.0: eth0: link up
Sep  3 17:12:02 ubuntu kernel: [  102.981541] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep  3 17:12:02 ubuntu NetworkManager[1451]: <info> (eth0): device state change: 5 -&gt; 7 (reason 0)
Sep  3 17:12:03 ubuntu NetworkManager[1451]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep  3 17:12:03 ubuntu kernel: [  103.065829] parport_pc 00:07: reported by Plug and Play ACPI
Sep  3 17:12:03 ubuntu kernel: [  103.065916] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep  3 17:12:03 ubuntu NetworkManager[1451]: <info> dhclient started with pid 1695
Sep  3 17:12:03 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep  3 17:12:03 ubuntu acpid: starting up with proc fs
Sep  3 17:12:03 ubuntu kernel: [  103.776194] ppdev: user-space parallel port driver
Sep  3 17:12:03 ubuntu cron[1681]: (CRON) INFO (pidfile fd = 3)
Sep  3 17:12:04 ubuntu kernel: [  104.291585] cfg80211: World regulatory domain updated:
Sep  3 17:12:04 ubuntu kernel: [  104.291592] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep  3 17:12:04 ubuntu kernel: [  104.291596] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.291599] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.291603] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.291606] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.291609] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu avahi-daemon[1242]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::219:dbff:fe70:296d.
Sep  3 17:12:04 ubuntu avahi-daemon[1242]: New relevant interface eth0.IPv6 for mDNS.
Sep  3 17:12:04 ubuntu avahi-daemon[1242]: Registering new address record for fe80::219:dbff:fe70:296d on eth0.*.
Sep  3 17:12:04 ubuntu cron[1730]: (CRON) STARTUP (fork ok)
Sep  3 17:12:04 ubuntu cron[1730]: (CRON) INFO (Running @reboot jobs)
Sep  3 17:12:04 ubuntu acpid: 32 rules loaded
Sep  3 17:12:04 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Sep  3 17:12:04 ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium.
Sep  3 17:12:04 ubuntu dhclient: All rights reserved.
Sep  3 17:12:04 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep  3 17:12:04 ubuntu dhclient: 
Sep  3 17:12:04 ubuntu acpid: waiting for events: event logging is off
Sep  3 17:12:04 ubuntu NetworkManager[1451]: <info> (eth0): DHCPv4 state changed nbi -&gt; preinit
Sep  3 17:12:04 ubuntu dhclient: Listening on LPF/eth0/00:19:db:70:29:6d
Sep  3 17:12:04 ubuntu dhclient: Sending on   LPF/eth0/00:19:db:70:29:6d
Sep  3 17:12:04 ubuntu dhclient: Sending on   Socket/fallback
Sep  3 17:12:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep  3 17:12:04 ubuntu kernel: [  104.802507] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802513] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802517] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802521] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802523] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802527] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802529] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802533] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802536] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802539] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802542] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802545] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802548] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802551] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802554] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802557] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802560] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802563] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802566] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802569] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802572] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802575] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802578] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802581] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802584] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802587] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu kernel: [  104.802590] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Sep  3 17:12:04 ubuntu kernel: [  104.802594] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  3 17:12:04 ubuntu dhclient: DHCPOFFER of 192.168.2.4 from 192.168.2.1
Sep  3 17:12:04 ubuntu dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Sep  3 17:12:05 ubuntu dhclient: DHCPACK of 192.168.2.4 from 192.168.2.1
Sep  3 17:12:05 ubuntu dhclient: bound to 192.168.2.4 -- renewal in 832413722 seconds.
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info> (eth0): DHCPv4 state changed preinit -&gt; bound
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info>   address 192.168.2.4
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info>   prefix 24 (255.255.255.0)
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info>   gateway 192.168.2.1
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info>   nameserver '192.168.2.1'
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info>   domain name 'Treasureboxauction'
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info> Scheduling stage 5
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info> Done scheduling stage 5
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  3 17:12:05 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep  3 17:12:05 ubuntu avahi-daemon[1242]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.4.
Sep  3 17:12:05 ubuntu avahi-daemon[1242]: New relevant interface eth0.IPv4 for mDNS.
Sep  3 17:12:05 ubuntu avahi-daemon[1242]: Registering new address record for 192.168.2.4 on eth0.IPv4.
Sep  3 17:12:05 ubuntu kernel: [  105.929932] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Sep  3 17:12:05 ubuntu kernel: [  105.930681] Registered led device: rt2500usb-phy0::radio
Sep  3 17:12:05 ubuntu kernel: [  105.930710] Registered led device: rt2500usb-phy0::quality
Sep  3 17:12:05 ubuntu kernel: [  105.931495] usbcore: registered new interface driver rt2500usb
Sep  3 17:12:06 ubuntu NetworkManager[1451]: <info> (eth0): device state change: 7 -&gt; 8 (reason 0)
Sep  3 17:12:06 ubuntu NetworkManager[1451]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  3 17:12:06 ubuntu NetworkManager[1451]: <info> Activation (eth0) successful, device activated.
Sep  3 17:12:06 ubuntu NetworkManager[1451]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  3 17:12:06 ubuntu NetworkManager[1451]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:13.5/usb1/1-7/1-7:1.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2500usb' ifindex: 3)
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): now managed
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): device state change: 1 -&gt; 2 (reason 2)
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): bringing up device.
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): preparing device.
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): deactivating device (reason: 2).
Sep  3 17:12:07 ubuntu kernel: [  107.238686] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  3 17:12:07 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-7/1-7:1.0/net/wlan0, iface: wlan0)
Sep  3 17:12:07 ubuntu NetworkManager[1451]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-7/1-7:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): supplicant interface state:  starting -&gt; ready
Sep  3 17:12:07 ubuntu NetworkManager[1451]: <info> (wlan0): device state change: 2 -&gt; 3 (reason 42)
Sep  3 17:12:07 ubuntu kernel: [  107.908001] HDA Intel 0000:00:14.2: PCI INT A -&gt; GSI 16 (level, low) -&gt; IRQ 16
Sep  3 17:12:07 ubuntu kernel: [  107.908259] HDA Intel 0000:00:14.2: irq 42 for MSI/MSI-X
Sep  3 17:12:07 ubuntu wpa_supplicant[1684]: Failed to initiate AP scan.
Sep  3 17:12:13 ubuntu kernel: [  113.456014] eth0: no IPv6 routers present
Sep  3 17:12:14 ubuntu acpid: client connected from 2187[0:0]
Sep  3 17:12:14 ubuntu acpid: 1 client rule loaded
Sep  3 17:12:15 ubuntu kernel: [  115.499895] lp0: using parport0 (interrupt-driven).
Sep  3 17:12:18 ubuntu udev-configure-printer: add /devices/pnp0/00:07/printer/lp0
Sep  3 17:12:18 ubuntu udev-configure-printer: Failed to get parent
Sep  3 17:12:18 ubuntu udev-configure-printer: add /module/lp
Sep  3 17:12:18 ubuntu udev-configure-printer: Failed to get parent
Sep  3 21:12:43 ubuntu ntpdate[2357]: step time server 91.189.94.4 offset 14413.896802 sec
Sep  3 21:12:57 ubuntu rtkit-daemon[3089]: Successfully called chroot.
Sep  3 21:12:57 ubuntu rtkit-daemon[3089]: Successfully dropped privileges.
Sep  3 21:12:57 ubuntu rtkit-daemon[3089]: Successfully limited resources.
Sep  3 21:12:57 ubuntu rtkit-daemon[3089]: Running.
Sep  3 21:12:57 ubuntu rtkit-daemon[3089]: Watchdog thread running.
Sep  3 21:12:57 ubuntu rtkit-daemon[3089]: Canary thread running.
Sep  3 21:12:58 ubuntu rtkit-daemon[3089]: Successfully made thread 3087 of process 3087 (n/a) owned by '999' high priority at nice level -11.
Sep  3 21:12:58 ubuntu rtkit-daemon[3089]: Supervising 1 threads of 1 processes of 1 users.
Sep  3 21:12:59 ubuntu ubiquity[3085]: Ubiquity 2.6.10
Sep  3 21:13:02 ubuntu rtkit-daemon[3089]: Successfully made thread 3099 of process 3087 (n/a) owned by '999' RT at priority 5.
Sep  3 21:13:02 ubuntu rtkit-daemon[3089]: Supervising 2 threads of 1 processes of 1 users.
Sep  3 21:13:03 ubuntu rtkit-daemon[3089]: Successfully made thread 3100 of process 3087 (n/a) owned by '999' RT at priority 5.
Sep  3 21:13:03 ubuntu rtkit-daemon[3089]: Supervising 3 threads of 1 processes of 1 users.
Sep  3 21:13:10 ubuntu ubiquity[3085]: log-output -t ubiquity laptop-detect
Sep  3 21:13:16 ubuntu ubiquity[3085]: switched to page language
Sep  3 21:13:19 ubuntu ubiquity[3085]: switched to page prepare
Sep  3 21:13:19 ubuntu ubiquity[3085]: switched to page language
Sep  3 21:13:24 ubuntu localechooser: info: Language = 'en'
Sep  3 21:13:24 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Sep  3 21:13:24 ubuntu localechooser: info: Set debian-installer/language = 'en'
Sep  3 21:13:24 ubuntu localechooser: info: Default country = 'US'
Sep  3 21:13:24 ubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Sep  3 21:13:24 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Sep  3 21:13:24 ubuntu localechooser: info: Set debian-installer/country = 'US'
Sep  3 21:13:24 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Sep  3 21:13:24 ubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Sep  3 21:13:26 ubuntu ubiquity[3085]: debconffilter_done: ubi-language (current: ubi-language)
Sep  3 21:13:26 ubuntu ubiquity[3085]: Step_before = stepLanguage
Sep  3 21:13:39 ubuntu kernel: [  185.696660] end_request: I/O error, dev fd0, sector 0
Sep  3 21:13:51 ubuntu kernel: [  197.857084] end_request: I/O error, dev fd0, sector 0
Sep  3 21:13:52 ubuntu ubiquity[3085]: switched to page prepare
Sep  3 21:13:52 ubuntu ubiquity[3085]: switched to page prepare
Sep  3 21:14:06 ubuntu ubiquity: Additional Drivers
Sep  3 21:14:06 ubuntu ubiquity: Searching for available drivers...
Sep  3 21:14:06 ubuntu ubiquity[3085]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Sep  3 21:14:06 ubuntu ubiquity[3085]: Step_before = stepPrepare
Sep  3 21:14:07 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Sep  3 21:14:07 ubuntu kernel: [  214.016723] JFS: nTxBlock = 8192, nTxLock = 65536
Sep  3 21:14:08 ubuntu kernel: [  214.524825] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Sep  3 21:14:08 ubuntu kernel: [  214.528255] SGI XFS Quota Management subsystem
Sep  3 21:14:20 ubuntu kernel: [  226.780712] end_request: I/O error, dev fd0, sector 0
Sep  3 21:14:32 ubuntu kernel: [  238.948621] end_request: I/O error, dev fd0, sector 0
Sep  3 21:14:34 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep  3 21:14:34 ubuntu ntfsresize: Device name        : /dev/sda1
Sep  3 21:14:34 ubuntu ntfsresize: NTFS volume version: 3.1
Sep  3 21:14:34 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep  3 21:14:34 ubuntu ntfsresize: Current volume size: 80015491584 bytes (80016 MB)
Sep  3 21:14:34 ubuntu ntfsresize: Current device size: 80015491584 bytes (80016 MB)
Sep  3 21:14:34 ubuntu ntfsresize: Checking filesystem consistency ...
Sep  3 21:14:34 ubuntu ntfsresize: Accounting clusters ...
Sep  3 21:14:34 ubuntu ntfsresize: Space in use       : 3501 MB (4.4%)
Sep  3 21:14:34 ubuntu ntfsresize: Collecting resizing constraints ...
Sep  3 21:14:34 ubuntu ntfsresize: You might resize at 3500589056 bytes or 3501 MB (freeing 76515 MB).
Sep  3 21:14:34 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep  3 21:14:34 ubuntu ntfs-3g[4894]: Version 2010.8.8 external FUSE 28
Sep  3 21:14:34 ubuntu ntfs-3g[4894]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Sep  3 21:14:34 ubuntu ntfs-3g[4894]: Cmdline options: ro
Sep  3 21:14:34 ubuntu ntfs-3g[4894]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Sep  3 21:14:34 ubuntu ntfs-3g[4894]: Ownership and permissions disabled, configuration type 1
Sep  3 21:14:34 ubuntu ntfs-3g[4894]: Unmounting /dev/sda1 ()
Sep  3 21:14:34 ubuntu ubiquity: umount: /tmp/tmp.6eJslMhMaJ: not mounted
Sep  3 21:14:35 ubuntu ntfs-3g[4952]: Version 2010.8.8 external FUSE 28
Sep  3 21:14:35 ubuntu ntfs-3g[4952]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Sep  3 21:14:35 ubuntu ntfs-3g[4952]: Cmdline options: ro
Sep  3 21:14:35 ubuntu ntfs-3g[4952]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Sep  3 21:14:35 ubuntu ntfs-3g[4952]: Ownership and permissions disabled, configuration type 1
Sep  3 21:14:35 ubuntu ntfs-3g[4952]: Unmounting /dev/sda1 ()
Sep  3 21:14:35 ubuntu ubiquity: umount: /tmp/tmp.51hWTNmwI3: not mounted
Sep  3 21:14:35 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep  3 21:14:35 ubuntu ntfsresize: Device name        : /dev/sda1
Sep  3 21:14:35 ubuntu ntfsresize: NTFS volume version: 3.1
Sep  3 21:14:35 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep  3 21:14:35 ubuntu ntfsresize: Current volume size: 80015491584 bytes (80016 MB)
Sep  3 21:14:35 ubuntu ntfsresize: Current device size: 80015491584 bytes (80016 MB)
Sep  3 21:14:35 ubuntu ntfsresize: Checking filesystem consistency ...
Sep  3 21:14:35 ubuntu ntfsresize: Accounting clusters ...
Sep  3 21:14:35 ubuntu ntfsresize: Space in use       : 3501 MB (4.4%)
Sep  3 21:14:35 ubuntu ntfsresize: Collecting resizing constraints ...
Sep  3 21:14:35 ubuntu ntfsresize: You might resize at 3500589056 bytes or 3501 MB (freeing 76515 MB).
Sep  3 21:14:35 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep  3 21:14:36 ubuntu ntfs-3g[5107]: Version 2010.8.8 external FUSE 28
Sep  3 21:14:36 ubuntu ntfs-3g[5107]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Sep  3 21:14:36 ubuntu ntfs-3g[5107]: Cmdline options: ro
Sep  3 21:14:36 ubuntu ntfs-3g[5107]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Sep  3 21:14:36 ubuntu ntfs-3g[5107]: Ownership and permissions disabled, configuration type 1
Sep  3 21:14:36 ubuntu ntfs-3g[5107]: Unmounting /dev/sda1 ()
Sep  3 21:14:36 ubuntu ubiquity: umount: /tmp/tmp.avTZCbv7Vo: not mounted
Sep  3 21:14:36 ubuntu ntfs-3g[5165]: Version 2010.8.8 external FUSE 28
Sep  3 21:14:36 ubuntu ntfs-3g[5165]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Sep  3 21:14:36 ubuntu ntfs-3g[5165]: Cmdline options: ro
Sep  3 21:14:36 ubuntu ntfs-3g[5165]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Sep  3 21:14:36 ubuntu ntfs-3g[5165]: Ownership and permissions disabled, configuration type 1
Sep  3 21:14:36 ubuntu ntfs-3g[5165]: Unmounting /dev/sda1 ()
Sep  3 21:14:36 ubuntu ubiquity: umount: /tmp/tmp.t9cMYqE9uP: not mounted
Sep  3 21:14:37 ubuntu ntfs-3g[5319]: Version 2010.8.8 external FUSE 28
Sep  3 21:14:37 ubuntu ntfs-3g[5319]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Sep  3 21:14:37 ubuntu ntfs-3g[5319]: Cmdline options: ro
Sep  3 21:14:37 ubuntu ntfs-3g[5319]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Sep  3 21:14:37 ubuntu ntfs-3g[5319]: Ownership and permissions disabled, configuration type 1
Sep  3 21:14:37 ubuntu ntfs-3g[5319]: Unmounting /dev/sda1 ()
Sep  3 21:14:37 ubuntu ubiquity: umount: /tmp/tmp.cx5ojAdVUz: not mounted
Sep  3 21:14:37 ubuntu ntfs-3g[5377]: Version 2010.8.8 external FUSE 28
Sep  3 21:14:37 ubuntu ntfs-3g[5377]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Sep  3 21:14:37 ubuntu ntfs-3g[5377]: Cmdline options: ro
Sep  3 21:14:37 ubuntu ntfs-3g[5377]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Sep  3 21:14:37 ubuntu ntfs-3g[5377]: Ownership and permissions disabled, configuration type 1
Sep  3 21:14:37 ubuntu ntfs-3g[5377]: Unmounting /dev/sda1 ()
Sep  3 21:14:37 ubuntu ubiquity: umount: /tmp/tmp.lNQGlEIcZ6: not mounted
Sep  3 21:14:38 ubuntu kernel: [  244.864883] NTFS driver 2.1.30 [Flags: R/O MODULE].
Sep  3 21:14:38 ubuntu kernel: [  245.061317] QNX4 filesystem 0.2.3 registered.
Sep  3 21:14:39 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Sep  3 21:14:39 ubuntu 50mounted-tests: debug: mounted using GRUB
Sep  3 21:14:39 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Sep  3 21:14:39 ubuntu 10freedos: debug: /dev/sda1 is a FUSE partition
Sep  3 21:14:39 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Sep  3 21:14:39 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Sep  3 21:14:39 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Sep  3 21:14:39 ubuntu macosx-prober: debug: /dev/sda1 is a FUSE partition
Sep  3 21:14:39 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Sep  3 21:14:39 ubuntu 20microsoft: debug: /dev/sda1 is a FUSE partition
Sep  3 21:14:39 ubuntu 20microsoft: result: /dev/sda1:Microsoft Windows XP Home Edition:Windows:chain
Sep  3 21:14:39 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Sep  3 21:14:39 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Sep  3 21:14:39 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb1
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: mounted using GRUB
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Sep  3 21:14:40 ubuntu 10freedos: debug: /dev/sdb1 is a FUSE partition
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Sep  3 21:14:40 ubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Sep  3 21:14:40 ubuntu macosx-prober: debug: /dev/sdb1 is a FUSE partition
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Sep  3 21:14:40 ubuntu 20microsoft: debug: /dev/sdb1 is a FUSE partition
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Sep  3 21:14:40 ubuntu 30utility: debug: /dev/sdb1 is a FUSE partition
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Sep  3 21:14:40 ubuntu 83haiku: debug: /dev/sdb1 is a FUSE partition
Sep  3 21:14:40 ubuntu 83haiku: debug: Stage 1 bootloader not found: exiting
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Sep  3 21:14:40 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Sep  3 21:14:40 ubuntu ubiquity[3085]: Device /dev/sdb1 not found in os-prober output
Sep  3 21:14:40 ubuntu ubiquity[3085]: switched to page partman
Sep  3 21:14:52 ubuntu ubiquity[3085]: switched to page partman
Sep  3 21:14:59 ubuntu kernel: [  265.257012] usb 1-8: USB disconnect, address 4
Sep  3 21:15:11 ubuntu ubiquity[3085]: debconffilter_done: ubi-partman (current: ubi-partman)
Sep  3 21:15:11 ubuntu ubiquity[3085]: Step_before = stepPartAuto
Sep  3 21:15:13 ubuntu kernel: [  279.156750] Adding 1964028k swap on /dev/sda5.  Priority:-1 extents:1 across:1964028k 
Sep  3 21:15:13 ubuntu partman: mke2fs 1.41.14 (22-Dec-2010)
Sep  3 21:15:15 ubuntu clock-setup: Sat Sep  3 21:15:15 UTC 2011
Sep  3 21:15:15 ubuntu clock-setup: rdate: adjust local clock by -0.004453 seconds
Sep  3 21:15:17 ubuntu ubiquity[3085]: switched to page timezone
Sep  3 21:15:19 ubuntu kernel: [  285.403158] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  3 21:15:20 ubuntu ubiquity[3085]: debconffilter_done: ubiquity.components.partman_commit (current: ubi-timezone)
Sep  3 21:15:20 ubuntu install.py: keeping packages due to preseeding: icedtea6-plugin openoffice.org
Sep  3 21:15:20 ubuntu install.py: keeping language packs for: en
Sep  3 21:15:22 ubuntu ubiquity: /usr/lib/python2.7/dist-packages/apt/deprecation.py:96: UserWarning: Deprecated parameter 'autoFix'
Sep  3 21:15:22 ubuntu ubiquity:   warnings.warn("Deprecated parameter %r" % key)
Sep  3 21:15:28 ubuntu localechooser: info: debian-installer/language preseeded to 'en' (seen: false)
Sep  3 21:15:28 ubuntu localechooser: info: debian-installer/country preseeded to 'US' (seen: true)
Sep  3 21:15:28 ubuntu localechooser: info: debian-installer/locale preseeded to 'en_US.UTF-8' (seen: true)
Sep  3 21:15:28 ubuntu localechooser: info: Preseeded language ignored: unknown language code
Sep  3 21:15:28 ubuntu localechooser: info: Language = 'en'
Sep  3 21:15:28 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Sep  3 21:15:28 ubuntu localechooser: info: Set debian-installer/language = 'en'
Sep  3 21:15:28 ubuntu localechooser: info: Default country = 'US'
Sep  3 21:15:28 ubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Sep  3 21:15:28 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Sep  3 21:15:28 ubuntu localechooser: info: Set debian-installer/country = 'US'
Sep  3 21:15:28 ubuntu kernel: [  294.471028] BUG: unable to handle kernel NULL pointer dereference at 00000010
Sep  3 21:15:28 ubuntu kernel: [  294.471147] IP: [<c113b876>] __d_lookup+0x86/0x140
Sep  3 21:15:28 ubuntu kernel: [  294.471224] *pde = 7484d067 
Sep  3 21:15:28 ubuntu kernel: [  294.471265] Oops: 0000 [#1] SMP 
Sep  3 21:15:28 ubuntu kernel: [  294.471310] last sysfs file: /sys/devices/system/cpu/cpu1/cache/index2/shared_cpu_map
Sep  3 21:15:28 ubuntu kernel: [  294.471414] Modules linked in: ufs qnx4 hfsplus hfs minix ntfs msdos xfs exportfs reiserfs jfs dm_crypt lp binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi arc4 snd_seq_midi_event snd_seq rt2500usb snd_timer snd_seq_device rt2x00usb ppdev rt2x00lib parport_pc mac80211 sp5100_tco snd parport soundcore psmouse i2c_piix4 cfg80211 k8temp shpchp snd_page_alloc serio_raw squashfs aufs nls_utf8 isofs nls_iso8859_1 nls_cp437 vfat fat dm_raid45 xor btrfs zlib_deflate libcrc32c radeon ttm usb_storage drm_kms_helper usbhid hid uas drm ahci r8169 i2c_algo_bit floppy ati_agp libahci pata_atiixp
Sep  3 21:15:28 ubuntu kernel: [  294.472231] 
Sep  3 21:15:28 ubuntu kernel: [  294.472251] Pid: 7919, comm: http Not tainted 2.6.38-8-generic #42-Ubuntu MICRO-STAR INTERANTIONAL CO.,LTD MS-7327/MS-7327
Sep  3 21:15:28 ubuntu kernel: [  294.472390] EIP: 0060:[<c113b876>] EFLAGS: 00210202 CPU: 1
Sep  3 21:15:28 ubuntu kernel: [  294.472460] EIP is at __d_lookup+0x86/0x140
Sep  3 21:15:28 ubuntu kernel: [  294.472516] EAX: f5be134c EBX: fffffffc ECX: 00000011 EDX: 43148d92
Sep  3 21:15:28 ubuntu kernel: [  294.472598] ESI: 00000004 EDI: 415f9172 EBP: e921bc24 ESP: e921bbec
Sep  3 21:15:28 ubuntu kernel: [  294.472679]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Sep  3 21:15:28 ubuntu kernel: [  294.472747] Process http (pid: 7919, ti=e921a000 task=f05c1940 task.ti=e921a000)
Sep  3 21:15:28 ubuntu kernel: [  294.472747] Stack:
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  f3c4ec00 00000000 00000044 29b378a0 0000000a 8fd5dbf8 f3080800 ec8a7c00
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  e921bc68 00000043 415f9172 00012ca0 f3080800 e921bc68 e921bc38 c113b963
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  00000000 f3080800 f7343230 e921bc58 c113007f c1169b50 00000000 e921bc68
Sep  3 21:15:28 ubuntu kernel: [  294.472747] Call Trace:
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c113b963>] d_lookup+0x33/0x60
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c113007f>] __lookup_hash+0x6f/0x100
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c1169b50>] ? generic_check_acl+0x0/0xb0
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c11303cb>] lookup_one_len+0x3b/0x70
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81d538e>] vfsub_lookup_one_len+0x1e/0x40 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81dbc41>] au_lkup_one+0x31/0xd0 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c1040605>] ? reweight_entity+0x125/0x130
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c10412cf>] ? enqueue_entity+0x18f/0x2c0
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81d8ac6>] au_wh_test+0x26/0xd0 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81dbe8e>] au_do_lookup+0x5e/0x1f0 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81dc189>] au_lkup_dentry+0x169/0x280 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c111ae62>] ? __kmalloc+0x152/0x1a0
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81da983>] ? au_di_alloc+0x43/0xa0 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81da983>] ? au_di_alloc+0x43/0xa0 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81da91d>] ? do_ii_read_lock+0x2d/0x30 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<f81e2f7a>] aufs_lookup+0xba/0x1e0 [aufs]
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c112ffd7>] d_alloc_and_lookup+0x37/0x70
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c1131d67>] do_lookup+0x177/0x260
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c1132a8a>] link_path_walk+0x5aa/0xb10
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c1249c93>] ? apparmor_file_alloc_security+0x23/0x50
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c1249c93>] ? apparmor_file_alloc_security+0x23/0x50
Sep  3 21:15:28 ubuntu kernel: [  294.472747]  [<c1133264>] do_path_lookup+0x44/0x120
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c11336a1>] user_path_at+0x41/0x80
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c112b197>] vfs_fstatat+0x47/0x90
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c112b230>] vfs_stat+0x20/0x30
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c112b5a6>] sys_stat64+0x16/0x30
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c113050b>] ? putname+0x2b/0x40
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c1126630>] ? do_sys_open+0xd0/0x120
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c1126a20>] ? do_sync_read+0x0/0xe0
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c11266ae>] ? sys_open+0x2e/0x40
Sep  3 21:15:28 ubuntu kernel: [  294.485886]  [<c1509bf4>] syscall_call+0x7/0xb
Sep  3 21:15:28 ubuntu kernel: [  294.485886] Code: 00 89 7d e0 eb 1f 8d b4 26 00 00 00 00 39 55 ec 74 73 8d 43 4c e8 0b 20 ef ff 90 8b 36 85 f6 0f 84 a0 00 00 00 8d 5e f8 8b 7d f0 &lt;39&gt; 7b 14 75 eb 8d 46 44 e8 3d df 3c 00 8b 7d e0 39 7b 10 75 d2 
Sep  3 21:15:28 ubuntu kernel: [  294.485886] EIP: [<c113b876>] __d_lookup+0x86/0x140 SS:ESP 0068:e921bbec
Sep  3 21:15:28 ubuntu kernel: [  294.485886] CR2: 0000000000000010
Sep  3 21:15:28 ubuntu kernel: [  294.564873] ---[ end trace ec7091686d6f3e67 ]---
Sep  3 21:15:28 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Sep  3 21:15:28 ubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Sep  3 21:15:28 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Sep  3 21:15:28 ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Sep  3 21:15:28 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Sep  3 21:15:28 ubuntu os-prober: debug: /dev/sda5: is active swap
Sep  3 21:15:28 ubuntu ubiquity[3085]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Sep  3 21:15:28 ubuntu ubiquity[3085]: Step_before = stepLocation
Sep  3 21:15:31 ubuntu ubiquity[3085]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Sep  3 21:15:31 ubuntu ubiquity[3085]: switched to page console_setup
Sep  3 21:15:41 ubuntu acpid: client 2187[0:0] has disconnected
Sep  3 21:15:41 ubuntu acpid: client connected from 2187[0:0]
Sep  3 21:15:41 ubuntu acpid: 1 client rule loaded
Sep  3 21:15:41 ubuntu kernel: [  307.988963] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Sep  3 21:15:48 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Sep  3 21:15:48 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Sep  3 21:15:48 ubuntu ubiquity[3085]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Sep  3 21:15:48 ubuntu ubiquity[3085]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Sep  3 21:15:48 ubuntu ubiquity[3085]: Step_before = stepKeyboardConf
Sep  3 21:15:48 ubuntu ubiquity[3085]: switched to page usersetup
Sep  3 21:16:58 ubuntu ubiquity[3085]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Sep  3 21:16:58 ubuntu ubiquity[3085]: Step_before = stepUserInfo
Sep  3 21:16:59 ubuntu ubiquity[3085]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Sep  3 21:16:59 ubuntu ubiquity[3085]: Step_before = stepUserInfo
Sep  3 21:17:02 ubuntu CRON[8548]: (root) CMD (   cd / &amp;&amp; run-parts --report /etc/cron.hourly)
Sep  3 21:18:45 ubuntu kernel: [  491.646419] BUG: unable to handle kernel NULL pointer dereference at 00000010
Sep  3 21:18:45 ubuntu kernel: [  491.648016] IP: [<c113b876>] __d_lookup+0x86/0x140
Sep  3 21:18:45 ubuntu kernel: [  491.648016] *pde = 730d1067 
Sep  3 21:18:45 ubuntu kernel: [  491.648016] Oops: 0000 [#2] SMP 
Sep  3 21:18:45 ubuntu kernel: [  491.648016] last sysfs file: /sys/devices/system/cpu/cpu1/cache/index2/shared_cpu_map
Sep  3 21:18:45 ubuntu kernel: [  491.648016] Modules linked in: ufs qnx4 hfsplus hfs minix ntfs msdos xfs exportfs reiserfs jfs dm_crypt lp binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi arc4 snd_seq_midi_event snd_seq rt2500usb snd_timer snd_seq_device rt2x00usb ppdev rt2x00lib parport_pc mac80211 sp5100_tco snd parport soundcore psmouse i2c_piix4 cfg80211 k8temp shpchp snd_page_alloc serio_raw squashfs aufs nls_utf8 isofs nls_iso8859_1 nls_cp437 vfat fat dm_raid45 xor btrfs zlib_deflate libcrc32c radeon ttm usb_storage drm_kms_helper usbhid hid uas drm ahci r8169 i2c_algo_bit floppy ati_agp libahci pata_atiixp
Sep  3 21:18:45 ubuntu kernel: [  491.648016] 
Sep  3 21:18:45 ubuntu kernel: [  491.648016] Pid: 7888, comm: install.py Tainted: G      D     2.6.38-8-generic #42-Ubuntu MICRO-STAR INTERANTIONAL CO.,LTD MS-7327/MS-7327
Sep  3 21:18:45 ubuntu kernel: [  491.648016] EIP: 0060:[<c113b876>] EFLAGS: 00210202 CPU: 0
Sep  3 21:18:45 ubuntu kernel: [  491.648016] EIP is at __d_lookup+0x86/0x140
Sep  3 21:18:45 ubuntu kernel: [  491.648016] EAX: f5be134c EBX: fffffffc ECX: 00000011 EDX: b81ef017
Sep  3 21:18:45 ubuntu kernel: [  491.648016] ESI: 00000004 EDI: b6758d2f EBP: e4bcbee8 ESP: e4bcbeb0
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Sep  3 21:18:45 ubuntu kernel: [  491.648016] Process install.py (pid: 7888, ti=e4bca000 task=ec94f1a0 task.ti=e4bca000)
Sep  3 21:18:45 ubuntu kernel: [  491.648016] Stack:
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  e4bcbf2c ec94f1a0 00000050 ec94f1a0 e4bcbec8 c113fd49 f46fba00 f70f703b
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  e4bcbf38 00000011 b6758d2f 00015ebe f46fba00 e4bcbf38 e4bcbefc c113b963
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  00000000 f46fba00 ece8fd08 e4bcbf1c c113007f c11e1940 e4bcbf30 e4bcbf38
Sep  3 21:18:45 ubuntu kernel: [  491.648016] Call Trace:
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  [<c113fd49>] ? vfsmount_lock_local_unlock+0x19/0x20
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  [<c113b963>] d_lookup+0x33/0x60
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  [<c113007f>] __lookup_hash+0x6f/0x100
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  [<c11e1940>] ? ext4_check_acl+0x0/0xa0
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  [<c1130125>] lookup_hash+0x15/0x20
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  [<c1133492>] do_unlinkat+0x72/0x160
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  [<c1134915>] sys_unlink+0x15/0x20
Sep  3 21:18:45 ubuntu kernel: [  491.648016]  [<c1509bf4>] syscall_call+0x7/0xb
Sep  3 21:18:45 ubuntu kernel: [  491.648016] Code: 00 89 7d e0 eb 1f 8d b4 26 00 00 00 00 39 55 ec 74 73 8d 43 4c e8 0b 20 ef ff 90 8b 36 85 f6 0f 84 a0 00 00 00 8d 5e f8 8b 7d f0 &lt;39&gt; 7b 14 75 eb 8d 46 44 e8 3d df 3c 00 8b 7d e0 39 7b 10 75 d2 
Sep  3 21:18:45 ubuntu kernel: [  491.648016] EIP: [<c113b876>] __d_lookup+0x86/0x140 SS:ESP 0068:e4bcbeb0
Sep  3 21:18:45 ubuntu kernel: [  491.648016] CR2: 0000000000000010
Sep  3 21:18:45 ubuntu kernel: [  491.798382] ---[ end trace ec7091686d6f3e68 ]---
Sep  3 21:18:57 ubuntu acpid: client 2187[0:0] has disconnected
Sep  3 21:18:57 ubuntu acpid: client connected from 2187[0:0]
Sep  3 21:18:57 ubuntu acpid: 1 client rule loaded
Sep  3 21:18:57 ubuntu kernel: [  503.365122] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Sep  3 21:19:00 ubuntu ubiquity[3085]: Reverting lockdown the desktop environment.
Sep  3 21:19:01 ubuntu ubiquity[3085]: Reverting lockdown the desktop environment.
Sep  3 21:19:17 ubuntu gdm-binary[8618]: WARNING: Unable to find users: no seat-id found
Sep  3 21:19:18 ubuntu acpid: client 2187[0:0] has disconnected
Sep  3 21:19:18 ubuntu acpid: client connected from 8630[0:0]
Sep  3 21:19:18 ubuntu acpid: 1 client rule loaded
Sep  3 21:19:21 ubuntu gdm-session-worker[8639]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep  3 21:21:16 ubuntu ubiquity[9047]: Ubiquity 2.6.10
Sep  3 21:21:16 ubuntu ubiquity: umount: /target: device is busy.
Sep  3 21:21:16 ubuntu ubiquity:         (In some cases useful info about processes that use
Sep  3 21:21:16 ubuntu ubiquity:          the device is found by lsof(8) or fuser(1))
Sep  3 21:21:16 ubuntu ubiquity[9047]: log-output -t ubiquity umount /target
Sep  3 21:21:19 ubuntu ubiquity[9047]: log-output -t ubiquity laptop-detect
Sep  3 21:21:24 ubuntu ubiquity[9047]: switched to page language
Sep  3 21:21:26 ubuntu localechooser: info: debian-installer/language preseeded to 'en' (seen: false)
Sep  3 21:21:26 ubuntu localechooser: info: debian-installer/country preseeded to 'US' (seen: false)
Sep  3 21:21:26 ubuntu localechooser: info: debian-installer/locale preseeded to 'en_US.UTF-8' (seen: false)
Sep  3 21:21:26 ubuntu localechooser: info: Preseeded language ignored: unknown language code
Sep  3 21:21:27 ubuntu ubiquity[9047]: switched to page language
Sep  3 21:21:31 ubuntu localechooser: info: Language = 'en'
Sep  3 21:21:32 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Sep  3 21:21:32 ubuntu localechooser: info: Set debian-installer/language = 'en'
Sep  3 21:21:32 ubuntu localechooser: info: Default country = 'US'
Sep  3 21:21:32 ubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Sep  3 21:21:32 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Sep  3 21:21:32 ubuntu localechooser: info: Set debian-installer/country = 'US'
Sep  3 21:21:32 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Sep  3 21:21:32 ubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Sep  3 21:21:33 ubuntu ubiquity[9047]: debconffilter_done: ubi-language (current: ubi-language)
Sep  3 21:21:34 ubuntu ubiquity[9047]: Step_before = stepLanguage
Sep  3 21:21:47 ubuntu kernel: [  673.352751] end_request: I/O error, dev fd0, sector 0
Sep  3 21:21:59 ubuntu kernel: [  685.520663] end_request: I/O error, dev fd0, sector 0
Sep  3 21:21:59 ubuntu ubiquity[9047]: switched to page prepare
Sep  3 21:22:08 ubuntu ubiquity[9047]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Sep  3 21:22:08 ubuntu ubiquity[9047]: Step_before = stepPrepare
Sep  3 21:22:09 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Sep  3 21:22:10 ubuntu ubiquity: umount: /target: device is busy.
Sep  3 21:22:10 ubuntu ubiquity:         (In some cases useful info about processes that use
Sep  3 21:22:10 ubuntu ubiquity:          the device is found by lsof(8) or fuser(1))
Sep  3 21:22:10 ubuntu ubiquity: 
Sep  3 21:22:10 ubuntu ubiquity[9047]: Traceback (most recent call last):
Sep  3 21:22:10 ubuntu ubiquity[9047]:   File "/usr/lib/ubiquity/ubiquity/misc.py", line 193, in boot_device
Sep  3 21:22:10 ubuntu ubiquity[9047]:     for disk in p.disks():
Sep  3 21:22:10 ubuntu ubiquity[9047]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 153, in disks
Sep  3 21:22:10 ubuntu ubiquity[9047]:     disks = os.listdir(devices)
Sep  3 21:22:10 ubuntu ubiquity[9047]: OSError: [Errno 2] No such file or directory: '/var/lib/partman/devices'
Sep  3 21:22:10 ubuntu ubiquity[9047]: 
Sep  3 21:22:10 ubuntu ubiquity[9047]: debconffilter_done: ubi-partman (current: ubi-partman)
Sep  3 21:22:10 ubuntu ubiquity[9047]: dbfilter_handle_status: ('ubi-partman', 10)
Sep  3 21:22:18 ubuntu ubiquity[9047]: dbfilter_handle_status: response 2
Sep  3 21:22:18 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Sep  3 21:22:19 ubuntu ubiquity: umount: /target: device is busy.
Sep  3 21:22:19 ubuntu ubiquity:         (In some cases useful info about processes that use
Sep  3 21:22:19 ubuntu ubiquity:          the device is found by lsof(8) or fuser(1))
Sep  3 21:22:19 ubuntu ubiquity[9047]: Traceback (most recent call last):
Sep  3 21:22:19 ubuntu ubiquity[9047]:   File "/usr/lib/ubiquity/ubiquity/misc.py", line 193, in boot_device
Sep  3 21:22:19 ubuntu ubiquity[9047]:     for disk in p.disks():
Sep  3 21:22:19 ubuntu ubiquity[9047]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 153, in disks
Sep  3 21:22:19 ubuntu ubiquity[9047]:     disks = os.listdir(devices)
Sep  3 21:22:19 ubuntu ubiquity[9047]: OSError: [Errno 2] No such file or directory: '/var/lib/partman/devices'
Sep  3 21:22:19 ubuntu ubiquity[9047]: 
Sep  3 21:22:19 ubuntu ubiquity[9047]: debconffilter_done: ubi-partman (current: ubi-partman)
Sep  3 21:22:19 ubuntu ubiquity[9047]: dbfilter_handle_status: ('ubi-partman', 10)
Sep  3 21:22:21 ubuntu ubiquity[9047]: dbfilter_handle_status: response 1
Sep  3 21:22:21 ubuntu ubiquity[9047]: Step_before = stepPrepare
Sep  3 21:22:25 ubuntu clock-setup: Sat Sep  3 17:22:25 EDT 2011
Sep  3 21:22:25 ubuntu clock-setup: rdate: adjust local clock by -0.014245 seconds
Sep  3 21:22:27 ubuntu ubiquity[9047]: switched to page timezone
Sep  3 21:22:39 ubuntu localechooser: info: debian-installer/language preseeded to 'en' (seen: false)
Sep  3 21:22:39 ubuntu localechooser: info: debian-installer/country preseeded to 'US' (seen: true)
Sep  3 21:22:39 ubuntu localechooser: info: debian-installer/locale preseeded to 'en_US.UTF-8' (seen: true)
Sep  3 21:22:39 ubuntu localechooser: info: Preseeded language ignored: unknown language code
Sep  3 21:22:39 ubuntu localechooser: info: Language = 'en'
Sep  3 21:22:39 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Sep  3 21:22:39 ubuntu localechooser: info: Set debian-installer/language = 'en'
Sep  3 21:22:39 ubuntu localechooser: info: Default country = 'US'
Sep  3 21:22:39 ubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Sep  3 21:22:39 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Sep  3 21:22:39 ubuntu localechooser: info: Set debian-installer/country = 'US'
Sep  3 21:22:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Sep  3 21:22:39 ubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Sep  3 21:22:40 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Sep  3 21:22:40 ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Sep  3 21:22:40 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Sep  3 21:22:40 ubuntu os-prober: debug: /dev/sda5: is active swap
Sep  3 21:22:40 ubuntu ubiquity[9047]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Sep  3 21:22:40 ubuntu ubiquity[9047]: Step_before = stepLocation
Sep  3 21:22:42 ubuntu ubiquity[9047]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Sep  3 21:22:42 ubuntu ubiquity[9047]: switched to page console_setup
Sep  3 21:22:46 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Sep  3 21:22:46 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Sep  3 21:22:46 ubuntu ubiquity[9047]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Sep  3 21:22:46 ubuntu ubiquity[9047]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Sep  3 21:22:46 ubuntu ubiquity[9047]: Step_before = stepKeyboardConf
Sep  3 21:22:46 ubuntu ubiquity[9047]: switched to page usersetup
Sep  3 21:22:56 ubuntu ubiquity[9047]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Sep  3 21:22:56 ubuntu ubiquity[9047]: Step_before = stepUserInfo
Sep  3 21:22:56 ubuntu ubiquity[9047]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Sep  3 21:22:56 ubuntu ubiquity[9047]: Step_before = stepUserInfo
Sep  3 21:23:12 ubuntu ubiquity[9047]: Reverting lockdown the desktop environment.
Sep  3 21:23:17 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep  3 21:23:17 ubuntu ubiquity[9047]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^oem-config/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep  3 21:23:17 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep  3 21:23:17 ubuntu ubiquity[9047]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^keyboard-configuration/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep  3 21:23:17 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep  3 21:23:17 ubuntu ubiquity[9047]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep  3 21:23:17 ubuntu ubiquity: umount: /target: device is busy.
Sep  3 21:23:17 ubuntu ubiquity:         (In some cases useful info about processes that use
Sep  3 21:23:17 ubuntu ubiquity:          the device is found by lsof(8) or fuser(1))
Sep  3 21:23:17 ubuntu ubiquity[9047]: log-output -t ubiquity umount /target
Sep  3 21:23:20 ubuntu ubiquity[11074]: Ubiquity 2.6.10
Sep  3 21:23:20 ubuntu ubiquity: umount: /target: device is busy.
Sep  3 21:23:20 ubuntu ubiquity:         (In some cases useful info about processes that use
Sep  3 21:23:20 ubuntu ubiquity:          the device is found by lsof(8) or fuser(1))
Sep  3 21:23:20 ubuntu ubiquity[11074]: log-output -t ubiquity umount /target
Sep  3 21:23:21 ubuntu ubiquity[11074]: log-output -t ubiquity laptop-detect
Sep  3 21:23:23 ubuntu ubiquity[11074]: switched to page language
Sep  3 21:23:25 ubuntu localechooser: info: debian-installer/language preseeded to 'en' (seen: false)
Sep  3 21:23:25 ubuntu localechooser: info: debian-installer/country preseeded to 'US' (seen: false)
Sep  3 21:23:25 ubuntu localechooser: info: debian-installer/locale preseeded to 'en_US.UTF-8' (seen: false)
Sep  3 21:23:25 ubuntu localechooser: info: Preseeded language ignored: unknown language code
Sep  3 21:23:25 ubuntu ubiquity[11074]: switched to page language
Sep  3 21:23:27 ubuntu localechooser: info: Language = 'en'
Sep  3 21:23:27 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Sep  3 21:23:27 ubuntu localechooser: info: Set debian-installer/language = 'en'
Sep  3 21:23:27 ubuntu localechooser: info: Default country = 'US'
Sep  3 21:23:27 ubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Sep  3 21:23:27 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Sep  3 21:23:27 ubuntu localechooser: info: Set debian-installer/country = 'US'
Sep  3 21:23:28 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Sep  3 21:23:28 ubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Sep  3 21:23:29 ubuntu ubiquity[11074]: debconffilter_done: ubi-language (current: ubi-language)
Sep  3 21:23:29 ubuntu ubiquity[11074]: Step_before = stepLanguage
Sep  3 21:23:42 ubuntu kernel: [  788.561427] end_request: I/O error, dev fd0, sector 0
Sep  3 21:23:54 ubuntu kernel: [  800.736757] end_request: I/O error, dev fd0, sector 0
Sep  3 21:23:54 ubuntu ubiquity[11074]: switched to page prepare
Sep  3 21:23:58 ubuntu ubiquity[11074]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Sep  3 21:23:58 ubuntu ubiquity[11074]: Step_before = stepPrepare
Sep  3 21:23:58 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Sep  3 21:23:58 ubuntu ubiquity: umount: /target: device is busy.
Sep  3 21:23:58 ubuntu ubiquity:         (In some cases useful info about processes that use
Sep  3 21:23:58 ubuntu ubiquity:          the device is found by lsof(8) or fuser(1))
Sep  3 21:23:58 ubuntu ubiquity[11074]: Traceback (most recent call last):
Sep  3 21:23:58 ubuntu ubiquity[11074]:   File "/usr/lib/ubiquity/ubiquity/misc.py", line 193, in boot_device
Sep  3 21:23:58 ubuntu ubiquity[11074]:     for disk in p.disks():
Sep  3 21:23:58 ubuntu ubiquity[11074]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 153, in disks
Sep  3 21:23:58 ubuntu ubiquity[11074]:     disks = os.listdir(devices)
Sep  3 21:23:58 ubuntu ubiquity[11074]: OSError: [Errno 2] No such file or directory: '/var/lib/partman/devices'
Sep  3 21:23:58 ubuntu ubiquity[11074]: 
Sep  3 21:23:58 ubuntu ubiquity[11074]: debconffilter_done: ubi-partman (current: ubi-partman)
Sep  3 21:23:58 ubuntu ubiquity[11074]: dbfilter_handle_status: ('ubi-partman', 10)
```</c113b876></c1509bf4></c1134915></c1133492></c1130125></c11e1940></c113007f></c113b963></c113fd49></c113b876></c113b876></c113b876></c1509bf4></c11266ae></c1126a20></c1126630></c113050b></c112b5a6></c112b230></c112b197></c11336a1></c1133264></c1249c93></c1249c93></c1132a8a></c1131d67></c112ffd7></f81e2f7a></f81da91d></f81da983></f81da983></c111ae62></f81dc189></f81dbe8e></f81d8ac6></c10412cf></c1040605></f81dbc41></f81d538e></c11303cb></c1169b50></c113007f></c113b963></c113b876></c113b876></info></info></info></info></info></info></info></info></info></info></unknown></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></warn></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></info></maxk@qualcomm.com></bio-0></div>

---

### Post by dirtclustit on 2012-12-15
What manufacturer produced the computer and hard drive? 

I had a Lenovo laptap that had several security features enabled on the original hard drive that prevented even Dban from being able to boot and nuke the hard drive. When I put in a spare hard drive it worked

I am not a guru by any means, so I have to take the low tech fix it route. Unless you have another computer to make sure it isn't the install disc or better yet a second hard drive you can put into her computer  you could try installing the temporary version where the entire Ubuntu operating system is stored in your RAM. 

Sorry this may not help much, but when a similar event  happened to me, it was some crazy security feature that I couldn't figure out how to disable it. I have had two lenovos that had this security feature that wouldn't let me install or change the masterboot record on the original hard drive

---

### Post by howefield on 2012-12-15
Old thread back to sleep.

---

