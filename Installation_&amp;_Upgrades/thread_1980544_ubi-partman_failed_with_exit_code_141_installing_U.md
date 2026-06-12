---
title: "ubi-partman failed with exit code 141 installing Ubuntu 12.04 ?"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by cyb3r_sn4k3 on 2012-05-15
When I installed Ubuntu 12.04 on my laptop it worked fine. But on my desktop it gives me an error saying "ubi-partman failed with exit code 141" and I tried continuing but nothing happens no progress bar etc. I am using an iso which I downloaded recently. How can I fix this?

---

### Post by cyb3r_sn4k3 on 2012-05-15
Help.

---

### Post by cyb3r_sn4k3 on 2012-05-15
/var/log/syslog

```

May 16 08:16:50 ubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 16 08:16:50 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1416" x-info="http://www.rsyslog.com"] start
May 16 08:16:50 ubuntu rsyslogd: rsyslogd's groupid changed to 103
May 16 08:16:50 ubuntu rsyslogd: rsyslogd's userid changed to 101
May 16 08:16:50 ubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May 16 08:16:50 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
May 16 08:16:50 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
May 16 08:16:50 ubuntu kernel: [    0.000000] Linux version 3.2.0-23-generic-pae (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 (Ubuntu 3.2.0-23.36-generic-pae 3.2.14)
May 16 08:16:50 ubuntu kernel: [    0.000000] KERNEL supported cpus:
May 16 08:16:50 ubuntu kernel: [    0.000000]   Intel GenuineIntel
May 16 08:16:50 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
May 16 08:16:50 ubuntu kernel: [    0.000000]   NSC Geode by NSC
May 16 08:16:50 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
May 16 08:16:50 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
May 16 08:16:50 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
May 16 08:16:50 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
May 16 08:16:50 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
May 16 08:16:50 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fffe000 (reserved)
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 16 08:16:50 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
May 16 08:16:50 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
May 16 08:16:50 ubuntu kernel: [    0.000000] DMI present.
May 16 08:16:50 ubuntu kernel: [    0.000000] DMI: Acer ASAG3730/ASAG1730/G31T-M5, BIOS R01-A0S0 11/18/2008
May 16 08:16:50 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
May 16 08:16:50 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
May 16 08:16:50 ubuntu kernel: [    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x1000000
May 16 08:16:50 ubuntu kernel: [    0.000000] MTRR default type: uncachable
May 16 08:16:50 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
May 16 08:16:50 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
May 16 08:16:50 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
May 16 08:16:50 ubuntu kernel: [    0.000000]   C0000-CFFFF write-protect
May 16 08:16:50 ubuntu kernel: [    0.000000]   D0000-DFFFF uncachable
May 16 08:16:50 ubuntu kernel: [    0.000000]   E0000-EFFFF write-through
May 16 08:16:50 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
May 16 08:16:50 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
May 16 08:16:50 ubuntu kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
May 16 08:16:50 ubuntu kernel: [    0.000000]   1 disabled
May 16 08:16:50 ubuntu kernel: [    0.000000]   2 disabled
May 16 08:16:50 ubuntu kernel: [    0.000000]   3 disabled
May 16 08:16:50 ubuntu kernel: [    0.000000]   4 disabled
May 16 08:16:50 ubuntu kernel: [    0.000000]   5 disabled
May 16 08:16:50 ubuntu kernel: [    0.000000]   6 disabled
May 16 08:16:50 ubuntu kernel: [    0.000000]   7 disabled
May 16 08:16:50 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May 16 08:16:50 ubuntu kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
May 16 08:16:50 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 02000000
May 16 08:16:50 ubuntu kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
May 16 08:16:50 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
May 16 08:16:50 ubuntu kernel: [    0.000000]  0000000000 - 0000200000 page 4k
May 16 08:16:50 ubuntu kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
May 16 08:16:50 ubuntu kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
May 16 08:16:50 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
May 16 08:16:50 ubuntu kernel: [    0.000000] RAMDISK: 7f17f000 - 7ffaf000
May 16 08:16:50 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 36dce000 - 37bfd501
May 16 08:16:50 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007f17f000 - 000000007ffae500 to 36dce000 - 37bfd500
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: RSDP 000fa1b0 00014 (v00 ACPIAM)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: RSDT 7ffb0000 00044 (v01 ACRSYS ACRPRDCT 20081118 MSFT 00000097)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: FACP 7ffb0200 00084 (v01 111808 FACP1137 20081118 MSFT 00000097)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: DSDT 7ffb05c0 05947 (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: FACS 7ffbe000 00040
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: APIC 7ffb0390 0006C (v01 111808 APIC1137 20081118 MSFT 00000097)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: MCFG 7ffb0400 0003C (v01 111808 OEMMCFG  20081118 MSFT 00000097)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: SLIC 7ffb0440 00176 (v01 ACRSYS ACRPRDCT 20081118 MSFT 00000097)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: OEMB 7ffbe040 00071 (v01 111808 OEMB1137 20081118 MSFT 00000097)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: HPET 7ffb5f10 00038 (v01 111808 OEMHPET  20081118 MSFT 00000097)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: GSCI 7ffbe0c0 02024 (v01 111808 GMCHSCI  20081118 MSFT 00000097)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: SSDT 7ffc0a10 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 16 08:16:50 ubuntu kernel: [    0.000000] 1155MB HIGHMEM available.
May 16 08:16:50 ubuntu kernel: [    0.000000] 891MB LOWMEM available.
May 16 08:16:50 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
May 16 08:16:50 ubuntu kernel: [    0.000000]   low ram: 0 - 37bfe000
May 16 08:16:50 ubuntu kernel: [    0.000000] Zone PFN ranges:
May 16 08:16:50 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May 16 08:16:50 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
May 16 08:16:50 ubuntu kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0007ffb0
May 16 08:16:50 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
May 16 08:16:50 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
May 16 08:16:50 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
May 16 08:16:50 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007ffb0
May 16 08:16:50 ubuntu kernel: [    0.000000] On node 0 totalpages: 524095
May 16 08:16:50 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c186b480, node_mem_map f5dcd200
May 16 08:16:50 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 16 08:16:50 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May 16 08:16:50 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
May 16 08:16:50 ubuntu kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
May 16 08:16:50 ubuntu kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
May 16 08:16:50 ubuntu kernel: [    0.000000]   HighMem zone: 2312 pages used for memmap
May 16 08:16:50 ubuntu kernel: [    0.000000]   HighMem zone: 293546 pages, LIFO batch:31
May 16 08:16:50 ubuntu kernel: [    0.000000] Using APIC driver default
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May 16 08:16:50 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
May 16 08:16:50 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 16 08:16:50 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
May 16 08:16:50 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
May 16 08:16:50 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
May 16 08:16:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May 16 08:16:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May 16 08:16:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May 16 08:16:50 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 7fffe000 (gap: 7fffe000:7ee02000)
May 16 08:16:50 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May 16 08:16:50 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
May 16 08:16:50 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f5a00000 s34240 r0 d23104 u524288
May 16 08:16:50 ubuntu kernel: [    0.000000] pcpu-alloc: s34240 r0 d23104 u524288 alloc=1*2097152
May 16 08:16:50 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
May 16 08:16:50 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
May 16 08:16:50 ubuntu kernel: [    0.000000] Kernel command line: initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- BOOT_IMAGE=/casper/vmlinuz 
May 16 08:16:50 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
May 16 08:16:50 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 16 08:16:50 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 16 08:16:50 ubuntu kernel: [    0.000000] Initializing CPU#0
May 16 08:16:50 ubuntu kernel: [    0.000000] allocated 8387072 bytes of page_cgroup
May 16 08:16:50 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May 16 08:16:50 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffb0)
May 16 08:16:50 ubuntu kernel: [    0.000000] Memory: 2045824k/2096832k available (5825k kernel code, 50556k reserved, 2850k data, 740k init, 1183432k highmem)
May 16 08:16:50 ubuntu kernel: [    0.000000] virtual kernel memory layout:
May 16 08:16:50 ubuntu kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
May 16 08:16:50 ubuntu kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
May 16 08:16:50 ubuntu kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
May 16 08:16:50 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
May 16 08:16:50 ubuntu kernel: [    0.000000]       .init : 0xc1879000 - 0xc1932000   ( 740 kB)
May 16 08:16:50 ubuntu kernel: [    0.000000]       .data : 0xc15b04bc - 0xc1878d00   (2850 kB)
May 16 08:16:50 ubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc15b04bc   (5825 kB)
May 16 08:16:50 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May 16 08:16:50 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May 16 08:16:50 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
May 16 08:16:50 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
May 16 08:16:50 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712 16
May 16 08:16:50 ubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f4c0a000 soft=f4c0c000
May 16 08:16:50 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
May 16 08:16:50 ubuntu kernel: [    0.000000] console [tty0] enabled
May 16 08:16:50 ubuntu kernel: [    0.000000] hpet clockevent registered
May 16 08:16:50 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
May 16 08:16:50 ubuntu kernel: [    0.000000] Detected 2660.117 MHz processor.
May 16 08:16:50 ubuntu kernel: [    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5320.23 BogoMIPS (lpj=10640468)
May 16 08:16:50 ubuntu kernel: [    0.004006] pid_max: default: 32768 minimum: 301
May 16 08:16:50 ubuntu kernel: [    0.004025] Security Framework initialized
May 16 08:16:50 ubuntu kernel: [    0.004040] AppArmor: AppArmor initialized
May 16 08:16:50 ubuntu kernel: [    0.004041] Yama: becoming mindful.
May 16 08:16:50 ubuntu kernel: [    0.004090] Mount-cache hash table entries: 512
May 16 08:16:50 ubuntu kernel: [    0.004212] Initializing cgroup subsys cpuacct
May 16 08:16:50 ubuntu kernel: [    0.004218] Initializing cgroup subsys memory
May 16 08:16:50 ubuntu kernel: [    0.004224] Initializing cgroup subsys devices
May 16 08:16:50 ubuntu kernel: [    0.004226] Initializing cgroup subsys freezer
May 16 08:16:50 ubuntu kernel: [    0.004228] Initializing cgroup subsys blkio
May 16 08:16:50 ubuntu kernel: [    0.004234] Initializing cgroup subsys perf_event
May 16 08:16:50 ubuntu kernel: [    0.004258] CPU: Physical Processor ID: 0
May 16 08:16:50 ubuntu kernel: [    0.004259] CPU: Processor Core ID: 0
May 16 08:16:50 ubuntu kernel: [    0.004262] mce: CPU supports 6 MCE banks
May 16 08:16:50 ubuntu kernel: [    0.004270] CPU0: Thermal monitoring enabled (TM2)
May 16 08:16:50 ubuntu kernel: [    0.004273] using mwait in idle threads.
May 16 08:16:50 ubuntu kernel: [    0.009320] ACPI: Core revision 20110623
May 16 08:16:50 ubuntu kernel: [    0.016010] ftrace: allocating 26594 entries in 53 pages
May 16 08:16:50 ubuntu kernel: [    0.020043] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 16 08:16:50 ubuntu kernel: [    0.020393] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May 16 08:16:50 ubuntu kernel: [    0.061309] CPU0: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz stepping 06
May 16 08:16:50 ubuntu kernel: [    0.064003] APIC calibration not consistent with PM-Timer: 155ms instead of 100ms
May 16 08:16:50 ubuntu kernel: [    0.064003] APIC delta adjusted to PM-Timer: 1662495 (2593464)
May 16 08:16:50 ubuntu kernel: [    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
May 16 08:16:50 ubuntu kernel: [    0.064003] ... version:                2
May 16 08:16:50 ubuntu kernel: [    0.064003] ... bit width:              40
May 16 08:16:50 ubuntu kernel: [    0.064003] ... generic registers:      2
May 16 08:16:50 ubuntu kernel: [    0.064003] ... value mask:             000000ffffffffff
May 16 08:16:50 ubuntu kernel: [    0.064003] ... max period:             000000007fffffff
May 16 08:16:50 ubuntu kernel: [    0.064003] ... fixed-purpose events:   3
May 16 08:16:50 ubuntu kernel: [    0.064003] ... event mask:             0000000700000003
May 16 08:16:50 ubuntu kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
May 16 08:16:50 ubuntu kernel: [    0.064003] CPU 1 irqstacks, hard=f4d12000 soft=f4d14000
May 16 08:16:50 ubuntu kernel: [    0.064003] Booting Node   0, Processors  #1
May 16 08:16:50 ubuntu kernel: [    0.064003] smpboot cpu 1: start_ip = 9b000
May 16 08:16:50 ubuntu kernel: [    0.008000] Initializing CPU#1
May 16 08:16:50 ubuntu kernel: [    0.152036] NMI watchdog enabled, takes one hw-pmu counter.
May 16 08:16:50 ubuntu kernel: [    0.152072] Brought up 2 CPUs
May 16 08:16:50 ubuntu kernel: [    0.152074] Total of 2 processors activated (10640.19 BogoMIPS).
May 16 08:16:50 ubuntu kernel: [    0.153800] devtmpfs: initialized
May 16 08:16:50 ubuntu kernel: [    0.153800] EVM: security.selinux
May 16 08:16:50 ubuntu kernel: [    0.153800] EVM: security.SMACK64
May 16 08:16:50 ubuntu kernel: [    0.153800] EVM: security.capability
May 16 08:16:50 ubuntu kernel: [    0.153800] PM: Registering ACPI NVS region at 7ffbe000 (204800 bytes)
May 16 08:16:50 ubuntu kernel: [    0.153800] print_constraints: dummy: 
May 16 08:16:50 ubuntu kernel: [    0.153800] RTC time:  8:16:35, date: 05/16/12
May 16 08:16:50 ubuntu kernel: [    0.153800] NET: Registered protocol family 16
May 16 08:16:50 ubuntu kernel: [    0.153800] Trying to unpack rootfs image as initramfs...
May 16 08:16:50 ubuntu kernel: [    0.153800] EISA bus registered
May 16 08:16:50 ubuntu kernel: [    0.153800] ACPI: bus type pci registered
May 16 08:16:50 ubuntu kernel: [    0.153800] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
May 16 08:16:50 ubuntu kernel: [    0.153800] PCI: not using MMCONFIG
May 16 08:16:50 ubuntu kernel: [    0.153800] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
May 16 08:16:50 ubuntu kernel: [    0.153800] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
May 16 08:16:50 ubuntu kernel: [    0.153800] PCI: Using configuration type 1 for base access
May 16 08:16:50 ubuntu kernel: [    0.156420] bio: create slab <bio-0> at 0
May 16 08:16:50 ubuntu kernel: [    0.156491] ACPI: Added _OSI(Module Device)
May 16 08:16:50 ubuntu kernel: [    0.156493] ACPI: Added _OSI(Processor Device)
May 16 08:16:50 ubuntu kernel: [    0.156495] ACPI: Added _OSI(3.0 _SCP Extensions)
May 16 08:16:50 ubuntu kernel: [    0.156497] ACPI: Added _OSI(Processor Aggregator Device)
May 16 08:16:50 ubuntu kernel: [    0.157519] ACPI: EC: Look up EC in DSDT
May 16 08:16:50 ubuntu kernel: [    0.159313] ACPI: Executed 1 blocks of module-level executable AML code
May 16 08:16:50 ubuntu kernel: [    0.161422] ACPI: SSDT 7ffc00f0 002B9 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
May 16 08:16:50 ubuntu kernel: [    0.161676] ACPI: Dynamic OEM Table Load:
May 16 08:16:50 ubuntu kernel: [    0.161679] ACPI: SSDT   (null) 002B9 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
May 16 08:16:50 ubuntu kernel: [    0.161949] ACPI: SSDT 7ffc0580 002B9 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
May 16 08:16:50 ubuntu kernel: [    0.162204] ACPI: Dynamic OEM Table Load:
May 16 08:16:50 ubuntu kernel: [    0.162206] ACPI: SSDT   (null) 002B9 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
May 16 08:16:50 ubuntu kernel: [    0.163019] ACPI: Interpreter enabled
May 16 08:16:50 ubuntu kernel: [    0.163024] ACPI: (supports S0 S3 S4 S5)
May 16 08:16:50 ubuntu kernel: [    0.163041] ACPI: Using IOAPIC for interrupt routing
May 16 08:16:50 ubuntu kernel: [    0.163059] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
May 16 08:16:50 ubuntu kernel: [    0.165347] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
May 16 08:16:50 ubuntu kernel: [    0.165349] PCI: Using MMCONFIG for extended config space
May 16 08:16:50 ubuntu kernel: [    0.172451] ACPI: No dock devices found.
May 16 08:16:50 ubuntu kernel: [    0.172454] HEST: Table not found.
May 16 08:16:50 ubuntu kernel: [    0.172457] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
May 16 08:16:50 ubuntu kernel: [    0.172606] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
May 16 08:16:50 ubuntu kernel: [    0.172761] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
May 16 08:16:50 ubuntu kernel: [    0.172764] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
May 16 08:16:50 ubuntu kernel: [    0.172766] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
May 16 08:16:50 ubuntu kernel: [    0.172768] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
May 16 08:16:50 ubuntu kernel: [    0.172770] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
May 16 08:16:50 ubuntu kernel: [    0.172773] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
May 16 08:16:50 ubuntu kernel: [    0.172785] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
May 16 08:16:50 ubuntu kernel: [    0.172824] pci 0000:00:01.0: [8086:29c1] type 1 class 0x000604
May 16 08:16:50 ubuntu kernel: [    0.172861] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
May 16 08:16:50 ubuntu kernel: [    0.172864] pci 0000:00:01.0: PME# disabled
May 16 08:16:50 ubuntu kernel: [    0.172902] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
May 16 08:16:50 ubuntu kernel: [    0.172916] pci 0000:00:1b.0: reg 10: [mem 0xf9ffc000-0xf9ffffff 64bit]
May 16 08:16:50 ubuntu kernel: [    0.172977] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May 16 08:16:50 ubuntu kernel: [    0.172980] pci 0000:00:1b.0: PME# disabled
May 16 08:16:50 ubuntu kernel: [    0.172998] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
May 16 08:16:50 ubuntu kernel: [    0.173060] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
May 16 08:16:50 ubuntu kernel: [    0.173063] pci 0000:00:1c.0: PME# disabled
May 16 08:16:50 ubuntu kernel: [    0.173082] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
May 16 08:16:50 ubuntu kernel: [    0.173144] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
May 16 08:16:50 ubuntu kernel: [    0.173148] pci 0000:00:1c.1: PME# disabled
May 16 08:16:50 ubuntu kernel: [    0.173168] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
May 16 08:16:50 ubuntu kernel: [    0.173204] pci 0000:00:1d.0: reg 20: [io  0xcc00-0xcc1f]
May 16 08:16:50 ubuntu kernel: [    0.173232] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
May 16 08:16:50 ubuntu kernel: [    0.173267] pci 0000:00:1d.1: reg 20: [io  0xc880-0xc89f]
May 16 08:16:50 ubuntu kernel: [    0.173295] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
May 16 08:16:50 ubuntu kernel: [    0.173330] pci 0000:00:1d.2: reg 20: [io  0xc800-0xc81f]
May 16 08:16:50 ubuntu kernel: [    0.173358] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
May 16 08:16:50 ubuntu kernel: [    0.173394] pci 0000:00:1d.3: reg 20: [io  0xc480-0xc49f]
May 16 08:16:50 ubuntu kernel: [    0.173429] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
May 16 08:16:50 ubuntu kernel: [    0.173446] pci 0000:00:1d.7: reg 10: [mem 0xf9ffbc00-0xf9ffbfff]
May 16 08:16:50 ubuntu kernel: [    0.173521] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
May 16 08:16:50 ubuntu kernel: [    0.173524] pci 0000:00:1d.7: PME# disabled
May 16 08:16:50 ubuntu kernel: [    0.173539] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
May 16 08:16:50 ubuntu kernel: [    0.173595] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
May 16 08:16:50 ubuntu kernel: [    0.173670] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
May 16 08:16:50 ubuntu kernel: [    0.173712] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
May 16 08:16:50 ubuntu kernel: [    0.173724] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
May 16 08:16:50 ubuntu kernel: [    0.173731] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
May 16 08:16:50 ubuntu kernel: [    0.173739] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
May 16 08:16:50 ubuntu kernel: [    0.173746] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
May 16 08:16:50 ubuntu kernel: [    0.173753] pci 0000:00:1f.2: reg 20: [io  0xffa0-0xffaf]
May 16 08:16:50 ubuntu kernel: [    0.173784] pci 0000:00:1f.2: PME# supported from D3hot
May 16 08:16:50 ubuntu kernel: [    0.173787] pci 0000:00:1f.2: PME# disabled
May 16 08:16:50 ubuntu kernel: [    0.173799] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
May 16 08:16:50 ubuntu kernel: [    0.173845] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
May 16 08:16:50 ubuntu kernel: [    0.173909] pci 0000:01:00.0: [10de:0641] type 0 class 0x000300
May 16 08:16:50 ubuntu kernel: [    0.173918] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
May 16 08:16:50 ubuntu kernel: [    0.173928] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    0.173938] pci 0000:01:00.0: reg 1c: [mem 0xfa000000-0xfbffffff 64bit]
May 16 08:16:50 ubuntu kernel: [    0.173944] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
May 16 08:16:50 ubuntu kernel: [    0.173951] pci 0000:01:00.0: reg 30: [mem 0xfea80000-0xfeafffff pref]
May 16 08:16:50 ubuntu kernel: [    0.174003] pci 0000:00:01.0: PCI bridge to [bus 01-01]
May 16 08:16:50 ubuntu kernel: [    0.174006] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
May 16 08:16:50 ubuntu kernel: [    0.174009] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
May 16 08:16:50 ubuntu kernel: [    0.174013] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    0.174048] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
May 16 08:16:50 ubuntu kernel: [    0.174111] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
May 16 08:16:50 ubuntu kernel: [    0.174128] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
May 16 08:16:50 ubuntu kernel: [    0.174158] pci 0000:03:00.0: reg 18: [mem 0xfebff000-0xfebfffff 64bit]
May 16 08:16:50 ubuntu kernel: [    0.174192] pci 0000:03:00.0: reg 30: [mem 0xfebc0000-0xfebdffff pref]
May 16 08:16:50 ubuntu kernel: [    0.174268] pci 0000:03:00.0: supports D1 D2
May 16 08:16:50 ubuntu kernel: [    0.174270] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
May 16 08:16:50 ubuntu kernel: [    0.174274] pci 0000:03:00.0: PME# disabled
May 16 08:16:50 ubuntu kernel: [    0.174296] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
May 16 08:16:50 ubuntu kernel: [    0.174305] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
May 16 08:16:50 ubuntu kernel: [    0.174309] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
May 16 08:16:50 ubuntu kernel: [    0.174312] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
May 16 08:16:50 ubuntu kernel: [    0.174371] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
May 16 08:16:50 ubuntu kernel: [    0.174380] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
May 16 08:16:50 ubuntu kernel: [    0.174382] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May 16 08:16:50 ubuntu kernel: [    0.174384] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May 16 08:16:50 ubuntu kernel: [    0.174386] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
May 16 08:16:50 ubuntu kernel: [    0.174389] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
May 16 08:16:50 ubuntu kernel: [    0.174391] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
May 16 08:16:50 ubuntu kernel: [    0.174406] pci_bus 0000:00: on NUMA node 0
May 16 08:16:50 ubuntu kernel: [    0.174408] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 16 08:16:50 ubuntu kernel: [    0.174495] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
May 16 08:16:50 ubuntu kernel: [    0.174552] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
May 16 08:16:50 ubuntu kernel: [    0.174581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
May 16 08:16:50 ubuntu kernel: [    0.174705]  pci0000:00: Requesting ACPI _OSC control (0x1d)
May 16 08:16:50 ubuntu kernel: [    0.174842]  pci0000:00: ACPI _OSC control (0x1d) granted
May 16 08:16:50 ubuntu kernel: [    0.179788] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
May 16 08:16:50 ubuntu kernel: [    0.179832] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
May 16 08:16:50 ubuntu kernel: [    0.179875] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
May 16 08:16:50 ubuntu kernel: [    0.179918] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
May 16 08:16:50 ubuntu kernel: [    0.179960] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
May 16 08:16:50 ubuntu kernel: [    0.180018] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
May 16 08:16:50 ubuntu kernel: [    0.180062] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
May 16 08:16:50 ubuntu kernel: [    0.180106] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
May 16 08:16:50 ubuntu kernel: [    0.180209] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
May 16 08:16:50 ubuntu kernel: [    0.180212] vgaarb: loaded
May 16 08:16:50 ubuntu kernel: [    0.180213] vgaarb: bridge control possible 0000:01:00.0
May 16 08:16:50 ubuntu kernel: [    0.180317] i2c-core: driver [aat2870] using legacy suspend method
May 16 08:16:50 ubuntu kernel: [    0.180319] i2c-core: driver [aat2870] using legacy resume method
May 16 08:16:50 ubuntu kernel: [    0.180383] SCSI subsystem initialized
May 16 08:16:50 ubuntu kernel: [    0.180421] libata version 3.00 loaded.
May 16 08:16:50 ubuntu kernel: [    0.180459] usbcore: registered new interface driver usbfs
May 16 08:16:50 ubuntu kernel: [    0.180469] usbcore: registered new interface driver hub
May 16 08:16:50 ubuntu kernel: [    1.152116] usbcore: registered new device driver usb
May 16 08:16:50 ubuntu kernel: [    1.152241] PCI: Using ACPI for IRQ routing
May 16 08:16:50 ubuntu kernel: [    1.152246] PCI: pci_cache_line_size set to 64 bytes
May 16 08:16:50 ubuntu kernel: [    1.152307] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
May 16 08:16:50 ubuntu kernel: [    1.152309] reserve RAM buffer: 000000007ffb0000 - 000000007fffffff 
May 16 08:16:50 ubuntu kernel: [    1.152411] NetLabel: Initializing
May 16 08:16:50 ubuntu kernel: [    1.152413] NetLabel:  domain hash size = 128
May 16 08:16:50 ubuntu kernel: [    1.152414] NetLabel:  protocols = UNLABELED CIPSOv4
May 16 08:16:50 ubuntu kernel: [    1.152425] NetLabel:  unlabeled traffic allowed by default
May 16 08:16:50 ubuntu kernel: [    1.152479] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May 16 08:16:50 ubuntu kernel: [    1.152483] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
May 16 08:16:50 ubuntu kernel: [    1.152487] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
May 16 08:16:50 ubuntu kernel: [    1.972199] Switching to clocksource hpet
May 16 08:16:50 ubuntu kernel: [    1.980762] AppArmor: AppArmor Filesystem Enabled
May 16 08:16:50 ubuntu kernel: [    1.980810] pnp: PnP ACPI init
May 16 08:16:50 ubuntu kernel: [    1.980832] ACPI: bus type pnp registered
May 16 08:16:50 ubuntu kernel: [    1.980974] pnp 00:00: [bus 00-ff]
May 16 08:16:50 ubuntu kernel: [    1.980977] pnp 00:00: [io  0x0cf8-0x0cff]
May 16 08:16:50 ubuntu kernel: [    1.980979] pnp 00:00: [io  0x0000-0x0cf7 window]
May 16 08:16:50 ubuntu kernel: [    1.980982] pnp 00:00: [io  0x0d00-0xffff window]
May 16 08:16:50 ubuntu kernel: [    1.980984] pnp 00:00: [mem 0x000a0000-0x000bffff window]
May 16 08:16:50 ubuntu kernel: [    1.980987] pnp 00:00: [mem 0x000d0000-0x000dffff window]
May 16 08:16:50 ubuntu kernel: [    1.980989] pnp 00:00: [mem 0x80000000-0xdfffffff window]
May 16 08:16:50 ubuntu kernel: [    1.980991] pnp 00:00: [mem 0xf0000000-0xffffffff window]
May 16 08:16:50 ubuntu kernel: [    1.981063] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
May 16 08:16:50 ubuntu kernel: [    1.981073] pnp 00:01: [mem 0xfed14000-0xfed19fff]
May 16 08:16:50 ubuntu kernel: [    1.981136] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.981140] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
May 16 08:16:50 ubuntu kernel: [    1.981173] pnp 00:02: [dma 4]
May 16 08:16:50 ubuntu kernel: [    1.981175] pnp 00:02: [io  0x0000-0x000f]
May 16 08:16:50 ubuntu kernel: [    1.981177] pnp 00:02: [io  0x0081-0x0083]
May 16 08:16:50 ubuntu kernel: [    1.981179] pnp 00:02: [io  0x0087]
May 16 08:16:50 ubuntu kernel: [    1.981180] pnp 00:02: [io  0x0089-0x008b]
May 16 08:16:50 ubuntu kernel: [    1.981182] pnp 00:02: [io  0x008f]
May 16 08:16:50 ubuntu kernel: [    1.981184] pnp 00:02: [io  0x00c0-0x00df]
May 16 08:16:50 ubuntu kernel: [    1.981209] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
May 16 08:16:50 ubuntu kernel: [    1.981219] pnp 00:03: [io  0x0070-0x0071]
May 16 08:16:50 ubuntu kernel: [    1.981236] pnp 00:03: [irq 8]
May 16 08:16:50 ubuntu kernel: [    1.981261] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
May 16 08:16:50 ubuntu kernel: [    1.981269] pnp 00:04: [io  0x0061]
May 16 08:16:50 ubuntu kernel: [    1.981297] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
May 16 08:16:50 ubuntu kernel: [    1.981306] pnp 00:05: [io  0x00f0-0x00ff]
May 16 08:16:50 ubuntu kernel: [    1.981311] pnp 00:05: [irq 13]
May 16 08:16:50 ubuntu kernel: [    1.981337] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
May 16 08:16:50 ubuntu kernel: [    1.981869] pnp 00:06: [io  0x03f8-0x03ff]
May 16 08:16:50 ubuntu kernel: [    1.981876] pnp 00:06: [irq 4]
May 16 08:16:50 ubuntu kernel: [    1.981879] pnp 00:06: [dma 0 disabled]
May 16 08:16:50 ubuntu kernel: [    1.981980] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
May 16 08:16:50 ubuntu kernel: [    1.982499] pnp 00:07: [io  0x02f8-0x02ff]
May 16 08:16:50 ubuntu kernel: [    1.982507] pnp 00:07: [irq 3]
May 16 08:16:50 ubuntu kernel: [    1.982509] pnp 00:07: [dma 0 disabled]
May 16 08:16:50 ubuntu kernel: [    1.982602] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
May 16 08:16:50 ubuntu kernel: [    1.983837] pnp 00:08: [io  0x0378-0x037f]
May 16 08:16:50 ubuntu kernel: [    1.983839] pnp 00:08: [io  0x0778-0x077f]
May 16 08:16:50 ubuntu kernel: [    1.983850] pnp 00:08: [irq 7]
May 16 08:16:50 ubuntu kernel: [    1.983852] pnp 00:08: [dma 3]
May 16 08:16:50 ubuntu kernel: [    1.984198] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (active)
May 16 08:16:50 ubuntu kernel: [    1.984228] pnp 00:09: [io  0x0060]
May 16 08:16:50 ubuntu kernel: [    1.984230] pnp 00:09: [io  0x0064]
May 16 08:16:50 ubuntu kernel: [    1.984236] pnp 00:09: [irq 1]
May 16 08:16:50 ubuntu kernel: [    1.984274] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
May 16 08:16:50 ubuntu kernel: [    1.984314] pnp 00:0a: [irq 12]
May 16 08:16:50 ubuntu kernel: [    1.984350] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
May 16 08:16:50 ubuntu kernel: [    1.984472] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
May 16 08:16:50 ubuntu kernel: [    1.984474] pnp 00:0b: [io  0x0a00-0x0a0f]
May 16 08:16:50 ubuntu kernel: [    1.984476] pnp 00:0b: [io  0x0a10-0x0a1f]
May 16 08:16:50 ubuntu kernel: [    1.984478] pnp 00:0b: [io  0x0a20-0x0a2f]
May 16 08:16:50 ubuntu kernel: [    1.984480] pnp 00:0b: [io  0x0a30-0x0a3f]
May 16 08:16:50 ubuntu kernel: [    1.984545] system 00:0b: [io  0x0a00-0x0a0f] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984548] system 00:0b: [io  0x0a10-0x0a1f] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984553] system 00:0b: [io  0x0a20-0x0a2f] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984555] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984558] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
May 16 08:16:50 ubuntu kernel: [    1.984624] pnp 00:0c: [io  0x0010-0x001f]
May 16 08:16:50 ubuntu kernel: [    1.984626] pnp 00:0c: [io  0x0022-0x003f]
May 16 08:16:50 ubuntu kernel: [    1.984628] pnp 00:0c: [io  0x0044-0x005f]
May 16 08:16:50 ubuntu kernel: [    1.984629] pnp 00:0c: [io  0x0062-0x0063]
May 16 08:16:50 ubuntu kernel: [    1.984631] pnp 00:0c: [io  0x0065-0x006f]
May 16 08:16:50 ubuntu kernel: [    1.984633] pnp 00:0c: [io  0x0072-0x007f]
May 16 08:16:50 ubuntu kernel: [    1.984635] pnp 00:0c: [io  0x0080]
May 16 08:16:50 ubuntu kernel: [    1.984636] pnp 00:0c: [io  0x0084-0x0086]
May 16 08:16:50 ubuntu kernel: [    1.984638] pnp 00:0c: [io  0x0088]
May 16 08:16:50 ubuntu kernel: [    1.984640] pnp 00:0c: [io  0x008c-0x008e]
May 16 08:16:50 ubuntu kernel: [    1.984641] pnp 00:0c: [io  0x0090-0x009f]
May 16 08:16:50 ubuntu kernel: [    1.984643] pnp 00:0c: [io  0x00a2-0x00bf]
May 16 08:16:50 ubuntu kernel: [    1.984645] pnp 00:0c: [io  0x00e0-0x00ef]
May 16 08:16:50 ubuntu kernel: [    1.984646] pnp 00:0c: [io  0x04d0-0x04d1]
May 16 08:16:50 ubuntu kernel: [    1.984648] pnp 00:0c: [io  0x0800-0x087f]
May 16 08:16:50 ubuntu kernel: [    1.984650] pnp 00:0c: [io  0x0000-0xffffffffffffffff disabled]
May 16 08:16:50 ubuntu kernel: [    1.984652] pnp 00:0c: [io  0x0480-0x04bf]
May 16 08:16:50 ubuntu kernel: [    1.984654] pnp 00:0c: [mem 0xfed1c000-0xfed1ffff]
May 16 08:16:50 ubuntu kernel: [    1.984656] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
May 16 08:16:50 ubuntu kernel: [    1.984710] system 00:0c: [io  0x04d0-0x04d1] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984712] system 00:0c: [io  0x0800-0x087f] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984715] system 00:0c: [io  0x0480-0x04bf] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984719] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984721] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984724] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
May 16 08:16:50 ubuntu kernel: [    1.984775] pnp 00:0d: [mem 0xfed00000-0xfed003ff]
May 16 08:16:50 ubuntu kernel: [    1.984804] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
May 16 08:16:50 ubuntu kernel: [    1.984849] pnp 00:0e: [mem 0xffb80000-0xffbfffff]
May 16 08:16:50 ubuntu kernel: [    1.984851] pnp 00:0e: [mem 0xfff80000-0xffffffff]
May 16 08:16:50 ubuntu kernel: [    1.984882] pnp 00:0e: Plug and Play ACPI device, IDs INT0800 (active)
May 16 08:16:50 ubuntu kernel: [    1.984918] pnp 00:0f: [mem 0xffc00000-0xfff7ffff]
May 16 08:16:50 ubuntu kernel: [    1.984959] system 00:0f: [mem 0xffc00000-0xfff7ffff] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.984962] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
May 16 08:16:50 ubuntu kernel: [    1.985032] pnp 00:10: [mem 0xfec00000-0xfec00fff]
May 16 08:16:50 ubuntu kernel: [    1.985034] pnp 00:10: [mem 0xfee00000-0xfee00fff]
May 16 08:16:50 ubuntu kernel: [    1.985081] system 00:10: [mem 0xfec00000-0xfec00fff] could not be reserved
May 16 08:16:50 ubuntu kernel: [    1.985084] system 00:10: [mem 0xfee00000-0xfee00fff] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.985087] system 00:10: Plug and Play ACPI device, IDs PNP0c02 (active)
May 16 08:16:50 ubuntu kernel: [    1.985116] pnp 00:11: [mem 0xe0000000-0xefffffff]
May 16 08:16:50 ubuntu kernel: [    1.985157] system 00:11: [mem 0xe0000000-0xefffffff] has been reserved
May 16 08:16:50 ubuntu kernel: [    1.985160] system 00:11: Plug and Play ACPI device, IDs PNP0c02 (active)
May 16 08:16:50 ubuntu kernel: [    1.985309] pnp 00:12: [mem 0x00000000-0x0009ffff]
May 16 08:16:50 ubuntu kernel: [    1.985311] pnp 00:12: [mem 0x000c0000-0x000cffff]
May 16 08:16:50 ubuntu kernel: [    1.985313] pnp 00:12: [mem 0x000e0000-0x000fffff]
May 16 08:16:50 ubuntu kernel: [    1.985315] pnp 00:12: [mem 0x00100000-0x7fffffff]
May 16 08:16:50 ubuntu kernel: [    1.985317] pnp 00:12: [mem 0x00000000-0xffffffffffffffff disabled]
May 16 08:16:50 ubuntu kernel: [    1.985371] system 00:12: [mem 0x00000000-0x0009ffff] could not be reserved
May 16 08:16:50 ubuntu kernel: [    1.985373] system 00:12: [mem 0x000c0000-0x000cffff] could not be reserved
May 16 08:16:50 ubuntu kernel: [    1.985376] system 00:12: [mem 0x000e0000-0x000fffff] could not be reserved
May 16 08:16:50 ubuntu kernel: [    1.985379] system 00:12: [mem 0x00100000-0x7fffffff] could not be reserved
May 16 08:16:50 ubuntu kernel: [    1.985382] system 00:12: Plug and Play ACPI device, IDs PNP0c01 (active)
May 16 08:16:50 ubuntu kernel: [    1.985503] pnp: PnP ACPI: found 19 devices
May 16 08:16:50 ubuntu kernel: [    1.985505] ACPI: ACPI bus type pnp unregistered
May 16 08:16:50 ubuntu kernel: [    1.985509] PnPBIOS: Disabled by ACPI PNP
May 16 08:16:50 ubuntu kernel: [    2.022255] PCI: max bus depth: 1 pci_try_num: 2
May 16 08:16:50 ubuntu kernel: [    2.022291] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    2.022295] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80200000-0x803fffff]
May 16 08:16:50 ubuntu kernel: [    2.022298] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    2.022302] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
May 16 08:16:50 ubuntu kernel: [    2.022305] pci 0000:00:01.0: PCI bridge to [bus 01-01]
May 16 08:16:50 ubuntu kernel: [    2.022307] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
May 16 08:16:50 ubuntu kernel: [    2.022310] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
May 16 08:16:50 ubuntu kernel: [    2.022314] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    2.022318] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
May 16 08:16:50 ubuntu kernel: [    2.022320] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
May 16 08:16:50 ubuntu kernel: [    2.022325] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff]
May 16 08:16:50 ubuntu kernel: [    2.022328] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    2.022334] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
May 16 08:16:50 ubuntu kernel: [    2.022336] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
May 16 08:16:50 ubuntu kernel: [    2.022341] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
May 16 08:16:50 ubuntu kernel: [    2.022344] pci 0000:00:1c.1:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    2.022350] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
May 16 08:16:50 ubuntu kernel: [    2.022377] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 16 08:16:50 ubuntu kernel: [    2.022381] pci 0000:00:01.0: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    2.022386] pci 0000:00:1c.0: enabling device (0104 -> 0107)
May 16 08:16:50 ubuntu kernel: [    2.022389] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 16 08:16:50 ubuntu kernel: [    2.022393] pci 0000:00:1c.0: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    2.022402] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May 16 08:16:50 ubuntu kernel: [    2.022405] pci 0000:00:1c.1: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    2.022411] pci 0000:00:1e.0: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    2.022414] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
May 16 08:16:50 ubuntu kernel: [    2.022417] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
May 16 08:16:50 ubuntu kernel: [    2.022419] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
May 16 08:16:50 ubuntu kernel: [    2.022421] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
May 16 08:16:50 ubuntu kernel: [    2.022423] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
May 16 08:16:50 ubuntu kernel: [    2.022425] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff]
May 16 08:16:50 ubuntu kernel: [    2.022427] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
May 16 08:16:50 ubuntu kernel: [    2.022429] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfeafffff]
May 16 08:16:50 ubuntu kernel: [    2.022431] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    2.022434] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
May 16 08:16:50 ubuntu kernel: [    2.022436] pci_bus 0000:02: resource 1 [mem 0x80200000-0x803fffff]
May 16 08:16:50 ubuntu kernel: [    2.022438] pci_bus 0000:02: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    2.022440] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
May 16 08:16:50 ubuntu kernel: [    2.022442] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
May 16 08:16:50 ubuntu kernel: [    2.022444] pci_bus 0000:03: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
May 16 08:16:50 ubuntu kernel: [    2.022447] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
May 16 08:16:50 ubuntu kernel: [    2.022449] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
May 16 08:16:50 ubuntu kernel: [    2.022451] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
May 16 08:16:50 ubuntu kernel: [    2.022453] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
May 16 08:16:50 ubuntu kernel: [    2.022455] pci_bus 0000:04: resource 8 [mem 0x80000000-0xdfffffff]
May 16 08:16:50 ubuntu kernel: [    2.022457] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xffffffff]
May 16 08:16:50 ubuntu kernel: [    2.022499] NET: Registered protocol family 2
May 16 08:16:50 ubuntu kernel: [    2.022567] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May 16 08:16:50 ubuntu kernel: [    2.022768] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 16 08:16:50 ubuntu kernel: [    2.023075] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May 16 08:16:50 ubuntu kernel: [    2.023228] TCP: Hash tables configured (established 131072 bind 65536)
May 16 08:16:50 ubuntu kernel: [    2.023230] TCP reno registered
May 16 08:16:50 ubuntu kernel: [    2.023232] UDP hash table entries: 512 (order: 2, 16384 bytes)
May 16 08:16:50 ubuntu kernel: [    2.023239] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
May 16 08:16:50 ubuntu kernel: [    2.023293] NET: Registered protocol family 1
May 16 08:16:50 ubuntu kernel: [    2.023322] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 16 08:16:50 ubuntu kernel: [    2.023338] pci 0000:00:1d.0: PCI INT A disabled
May 16 08:16:50 ubuntu kernel: [    2.023347] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 16 08:16:50 ubuntu kernel: [    2.023361] pci 0000:00:1d.1: PCI INT B disabled
May 16 08:16:50 ubuntu kernel: [    2.023370] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 16 08:16:50 ubuntu kernel: [    2.023385] pci 0000:00:1d.2: PCI INT C disabled
May 16 08:16:50 ubuntu kernel: [    2.023391] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
May 16 08:16:50 ubuntu kernel: [    2.023407] pci 0000:00:1d.3: PCI INT D disabled
May 16 08:16:50 ubuntu kernel: [    2.023414] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 16 08:16:50 ubuntu kernel: [    2.023437] pci 0000:00:1d.7: PCI INT A disabled
May 16 08:16:50 ubuntu kernel: [    2.023458] pci 0000:01:00.0: Boot video device
May 16 08:16:50 ubuntu kernel: [    2.023463] PCI: CLS 32 bytes, default 64
May 16 08:16:50 ubuntu kernel: [    2.728114] Freeing initrd memory: 14528k freed
May 16 08:16:50 ubuntu kernel: [    2.733407] audit: initializing netlink socket (disabled)
May 16 08:16:50 ubuntu kernel: [    2.733422] type=2000 audit(1337156197.728:1): initialized
May 16 08:16:50 ubuntu kernel: [    2.755899] highmem bounce pool size: 64 pages
May 16 08:16:50 ubuntu kernel: [    2.755904] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May 16 08:16:50 ubuntu kernel: [    2.763754] VFS: Disk quotas dquot_6.5.2
May 16 08:16:50 ubuntu kernel: [    2.763820] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 16 08:16:50 ubuntu kernel: [    2.764455] fuse init (API version 7.17)
May 16 08:16:50 ubuntu kernel: [    2.764545] msgmni has been set to 1712
May 16 08:16:50 ubuntu kernel: [    2.764843] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May 16 08:16:50 ubuntu kernel: [    2.764865] io scheduler noop registered
May 16 08:16:50 ubuntu kernel: [    2.764867] io scheduler deadline registered
May 16 08:16:50 ubuntu kernel: [    2.764874] io scheduler cfq registered (default)
May 16 08:16:50 ubuntu kernel: [    2.764970] pcieport 0000:00:01.0: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    2.764998] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
May 16 08:16:50 ubuntu kernel: [    2.765059] pcieport 0000:00:1c.0: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    2.765091] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
May 16 08:16:50 ubuntu kernel: [    2.765174] pcieport 0000:00:1c.1: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    2.765206] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
May 16 08:16:50 ubuntu kernel: [    2.765307] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
May 16 08:16:50 ubuntu kernel: [    2.765309] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
May 16 08:16:50 ubuntu kernel: [    2.765312] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
May 16 08:16:50 ubuntu kernel: [    2.765328] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
May 16 08:16:50 ubuntu kernel: [    2.765332] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
May 16 08:16:50 ubuntu kernel: [    2.765348] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
May 16 08:16:50 ubuntu kernel: [    2.765350] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
May 16 08:16:50 ubuntu kernel: [    2.765353] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
May 16 08:16:50 ubuntu kernel: [    2.765369] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 16 08:16:50 ubuntu kernel: [    2.765406] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 27d0 ss_vid 1019 ss_did 2672
May 16 08:16:50 ubuntu kernel: [    2.765424] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
May 16 08:16:50 ubuntu kernel: [    2.765433] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 27d2 ss_vid 1019 ss_did 2672
May 16 08:16:50 ubuntu kernel: [    2.765452] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
May 16 08:16:50 ubuntu kernel: [    2.765458] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 16 08:16:50 ubuntu kernel: [    2.765533] intel_idle: MWAIT substates: 0x22220
May 16 08:16:50 ubuntu kernel: [    2.765535] intel_idle: does not run on family 6 model 23
May 16 08:16:50 ubuntu kernel: [    2.765608] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
May 16 08:16:50 ubuntu kernel: [    2.765614] ACPI: Power Button [PWRB]
May 16 08:16:50 ubuntu kernel: [    2.765654] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May 16 08:16:50 ubuntu kernel: [    2.765657] ACPI: Power Button [PWRF]
May 16 08:16:50 ubuntu kernel: [    2.768549] ERST: Table is not found!
May 16 08:16:50 ubuntu kernel: [    2.768551] GHES: HEST is not enabled!
May 16 08:16:50 ubuntu kernel: [    2.768575] isapnp: Scanning for PnP cards...
May 16 08:16:50 ubuntu kernel: [    2.768614] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May 16 08:16:50 ubuntu kernel: [    2.788938] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 16 08:16:50 ubuntu kernel: [    2.888299] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 16 08:16:50 ubuntu kernel: [    3.034491] Refined TSC clocksource calibration: 2659.999 MHz.
May 16 08:16:50 ubuntu kernel: [    3.034495] Switching to clocksource tsc
May 16 08:16:50 ubuntu kernel: [    3.121383] isapnp: No Plug & Play device found
May 16 08:16:50 ubuntu kernel: [    3.180497] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 16 08:16:50 ubuntu kernel: [    3.216363] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 16 08:16:50 ubuntu kernel: [    3.232281] Linux agpgart interface v0.103
May 16 08:16:50 ubuntu kernel: [    3.233698] brd: module loaded
May 16 08:16:50 ubuntu kernel: [    3.234376] loop: module loaded
May 16 08:16:50 ubuntu kernel: [    3.234521] ata_piix 0000:00:1f.2: version 2.13
May 16 08:16:50 ubuntu kernel: [    3.234531] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 16 08:16:50 ubuntu kernel: [    3.234536] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
May 16 08:16:50 ubuntu kernel: [    3.234562] ata_piix 0000:00:1f.2: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    3.234816] scsi0 : ata_piix
May 16 08:16:50 ubuntu kernel: [    3.234881] scsi1 : ata_piix
May 16 08:16:50 ubuntu kernel: [    3.236072] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
May 16 08:16:50 ubuntu kernel: [    3.236074] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
May 16 08:16:50 ubuntu kernel: [    3.236395] Fixed MDIO Bus: probed
May 16 08:16:50 ubuntu kernel: [    3.236416] tun: Universal TUN/TAP device driver, 1.6
May 16 08:16:50 ubuntu kernel: [    3.236418] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May 16 08:16:50 ubuntu kernel: [    3.236458] PPP generic driver version 2.4.2
May 16 08:16:50 ubuntu kernel: [    3.236543] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May 16 08:16:50 ubuntu kernel: [    3.236558] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 16 08:16:50 ubuntu kernel: [    3.236568] ehci_hcd 0000:00:1d.7: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    3.236571] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May 16 08:16:50 ubuntu kernel: [    3.236608] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
May 16 08:16:50 ubuntu kernel: [    3.236622] ehci_hcd 0000:00:1d.7: using broken periodic workaround
May 16 08:16:50 ubuntu kernel: [    3.236631] ehci_hcd 0000:00:1d.7: debug port 1
May 16 08:16:50 ubuntu kernel: [    3.240501] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
May 16 08:16:50 ubuntu kernel: [    3.240517] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9ffbc00
May 16 08:16:50 ubuntu kernel: [    3.256012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
May 16 08:16:50 ubuntu kernel: [    3.256154] hub 1-0:1.0: USB hub found
May 16 08:16:50 ubuntu kernel: [    3.256158] hub 1-0:1.0: 8 ports detected
May 16 08:16:50 ubuntu kernel: [    3.256227] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May 16 08:16:50 ubuntu kernel: [    3.256238] uhci_hcd: USB Universal Host Controller Interface driver
May 16 08:16:50 ubuntu kernel: [    3.256252] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 16 08:16:50 ubuntu kernel: [    3.256258] uhci_hcd 0000:00:1d.0: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    3.256260] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May 16 08:16:50 ubuntu kernel: [    3.256299] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
May 16 08:16:50 ubuntu kernel: [    3.256319] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cc00
May 16 08:16:50 ubuntu kernel: [    3.256426] hub 2-0:1.0: USB hub found
May 16 08:16:50 ubuntu kernel: [    3.256430] hub 2-0:1.0: 2 ports detected
May 16 08:16:50 ubuntu kernel: [    3.256489] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 16 08:16:50 ubuntu kernel: [    3.256495] uhci_hcd 0000:00:1d.1: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    3.256498] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May 16 08:16:50 ubuntu kernel: [    3.256532] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
May 16 08:16:50 ubuntu kernel: [    3.256560] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c880
May 16 08:16:50 ubuntu kernel: [    3.256662] hub 3-0:1.0: USB hub found
May 16 08:16:50 ubuntu kernel: [    3.256666] hub 3-0:1.0: 2 ports detected
May 16 08:16:50 ubuntu kernel: [    3.256718] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 16 08:16:50 ubuntu kernel: [    3.256724] uhci_hcd 0000:00:1d.2: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    3.256727] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May 16 08:16:50 ubuntu kernel: [    3.256764] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
May 16 08:16:50 ubuntu kernel: [    3.256791] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
May 16 08:16:50 ubuntu kernel: [    3.256892] hub 4-0:1.0: USB hub found
May 16 08:16:50 ubuntu kernel: [    3.256895] hub 4-0:1.0: 2 ports detected
May 16 08:16:50 ubuntu kernel: [    3.256948] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
May 16 08:16:50 ubuntu kernel: [    3.256954] uhci_hcd 0000:00:1d.3: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    3.256957] uhci_hcd 0000:00:1d.3: UHCI Host Controller
May 16 08:16:50 ubuntu kernel: [    3.256992] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
May 16 08:16:50 ubuntu kernel: [    3.257020] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c480
May 16 08:16:50 ubuntu kernel: [    3.257122] hub 5-0:1.0: USB hub found
May 16 08:16:50 ubuntu kernel: [    3.257126] hub 5-0:1.0: 2 ports detected
May 16 08:16:50 ubuntu kernel: [    3.257216] usbcore: registered new interface driver libusual
May 16 08:16:50 ubuntu kernel: [    3.257274] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
May 16 08:16:50 ubuntu kernel: [    3.257602] serio: i8042 KBD port at 0x60,0x64 irq 1
May 16 08:16:50 ubuntu kernel: [    3.257608] serio: i8042 AUX port at 0x60,0x64 irq 12
May 16 08:16:50 ubuntu kernel: [    3.257715] mousedev: PS/2 mouse device common for all mice
May 16 08:16:50 ubuntu kernel: [    3.257831] rtc_cmos 00:03: RTC can wake from S4
May 16 08:16:50 ubuntu kernel: [    3.257917] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 16 08:16:50 ubuntu kernel: [    3.257938] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 16 08:16:50 ubuntu kernel: [    3.257989] device-mapper: uevent: version 1.0.3
May 16 08:16:50 ubuntu kernel: [    3.258049] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
May 16 08:16:50 ubuntu kernel: [    3.258076] EISA: Probing bus 0 at eisa.0
May 16 08:16:50 ubuntu kernel: [    3.258078] EISA: Cannot allocate resource for mainboard
May 16 08:16:50 ubuntu kernel: [    3.258080] Cannot allocate resource for EISA slot 1
May 16 08:16:50 ubuntu kernel: [    3.258082] Cannot allocate resource for EISA slot 2
May 16 08:16:50 ubuntu kernel: [    3.258084] Cannot allocate resource for EISA slot 3
May 16 08:16:50 ubuntu kernel: [    3.258085] Cannot allocate resource for EISA slot 4
May 16 08:16:50 ubuntu kernel: [    3.258087] Cannot allocate resource for EISA slot 5
May 16 08:16:50 ubuntu kernel: [    3.258089] Cannot allocate resource for EISA slot 6
May 16 08:16:50 ubuntu kernel: [    3.258090] Cannot allocate resource for EISA slot 7
May 16 08:16:50 ubuntu kernel: [    3.258092] Cannot allocate resource for EISA slot 8
May 16 08:16:50 ubuntu kernel: [    3.258093] EISA: Detected 0 cards.
May 16 08:16:50 ubuntu kernel: [    3.258099] cpufreq-nforce2: No nForce2 chipset.
May 16 08:16:50 ubuntu kernel: [    3.258101] cpuidle: using governor ladder
May 16 08:16:50 ubuntu kernel: [    3.258103] cpuidle: using governor menu
May 16 08:16:50 ubuntu kernel: [    3.258105] EFI Variables Facility v0.08 2004-May-17
May 16 08:16:50 ubuntu kernel: [    3.258332] TCP cubic registered
May 16 08:16:50 ubuntu kernel: [    3.258441] NET: Registered protocol family 10
May 16 08:16:50 ubuntu kernel: [    3.258930] NET: Registered protocol family 17
May 16 08:16:50 ubuntu kernel: [    3.258942] Registering the dns_resolver key type
May 16 08:16:50 ubuntu kernel: [    3.258959] Using IPI No-Shortcut mode
May 16 08:16:50 ubuntu kernel: [    3.259042] PM: Hibernation image not present or could not be loaded.
May 16 08:16:50 ubuntu kernel: [    3.259052] registered taskstats version 1
May 16 08:16:50 ubuntu kernel: [    3.267365]   Magic number: 12:760:270
May 16 08:16:50 ubuntu kernel: [    3.267442] rtc_cmos 00:03: setting system clock to 2012-05-16 08:16:39 UTC (1337156199)
May 16 08:16:50 ubuntu kernel: [    3.267867] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 16 08:16:50 ubuntu kernel: [    3.267869] EDD information not available.
May 16 08:16:50 ubuntu kernel: [    3.408319] ata1.01: ATA-8: ST31000528AS, CC38, max UDMA/133
May 16 08:16:50 ubuntu kernel: [    3.408324] ata1.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
May 16 08:16:50 ubuntu kernel: [    3.424345] ata2.00: ATA-8: Hitachi HDP725032GLA380, GM3OA52A, max UDMA/133
May 16 08:16:50 ubuntu kernel: [    3.424350] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
May 16 08:16:50 ubuntu kernel: [    3.424357] ata2.01: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
May 16 08:16:50 ubuntu kernel: [    3.424436] ata1.01: configured for UDMA/133
May 16 08:16:50 ubuntu kernel: [    3.424542] scsi 0:0:1:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
May 16 08:16:50 ubuntu kernel: [    3.424647] sd 0:0:1:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
May 16 08:16:50 ubuntu kernel: [    3.424683] sd 0:0:1:0: Attached scsi generic sg0 type 0
May 16 08:16:50 ubuntu kernel: [    3.424689] sd 0:0:1:0: [sda] Write Protect is off
May 16 08:16:50 ubuntu kernel: [    3.424692] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
May 16 08:16:50 ubuntu kernel: [    3.424711] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 16 08:16:50 ubuntu kernel: [    3.440279] ata2.00: configured for UDMA/133
May 16 08:16:50 ubuntu kernel: [    3.456119] ata2.01: configured for UDMA/100
May 16 08:16:50 ubuntu kernel: [    3.458497] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDP72503 GM3O PQ: 0 ANSI: 5
May 16 08:16:50 ubuntu kernel: [    3.458589] sd 1:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
May 16 08:16:50 ubuntu kernel: [    3.458612] sd 1:0:0:0: Attached scsi generic sg1 type 0
May 16 08:16:50 ubuntu kernel: [    3.458631] sd 1:0:0:0: [sdb] Write Protect is off
May 16 08:16:50 ubuntu kernel: [    3.458633] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May 16 08:16:50 ubuntu kernel: [    3.458652] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 16 08:16:50 ubuntu kernel: [    3.462219] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
May 16 08:16:50 ubuntu kernel: [    3.471170]  sda: sda2 sda3
May 16 08:16:50 ubuntu kernel: [    3.471406] sd 0:0:1:0: [sda] Attached SCSI disk
May 16 08:16:50 ubuntu kernel: [    3.492531]  sdb: sdb1 sdb2 sdb3
May 16 08:16:50 ubuntu kernel: [    3.494897] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
May 16 08:16:50 ubuntu kernel: [    3.494901] cdrom: Uniform CD-ROM driver Revision: 3.20
May 16 08:16:50 ubuntu kernel: [    3.494982] sd 1:0:0:0: [sdb] Attached SCSI disk
May 16 08:16:50 ubuntu kernel: [    3.495004] sr 1:0:1:0: Attached scsi CD-ROM sr0
May 16 08:16:50 ubuntu kernel: [    3.495108] sr 1:0:1:0: Attached scsi generic sg2 type 5
May 16 08:16:50 ubuntu kernel: [    3.495195] Freeing unused kernel memory: 740k freed
May 16 08:16:50 ubuntu kernel: [    3.495407] Write protecting the kernel text: 5828k
May 16 08:16:50 ubuntu kernel: [    3.495422] Write protecting the kernel read-only data: 2376k
May 16 08:16:50 ubuntu kernel: [    3.495423] NX-protecting the kernel data: 4412k
May 16 08:16:50 ubuntu kernel: [    3.567014] wmi: Mapper loaded
May 16 08:16:50 ubuntu kernel: [    3.568058] usb 1-1: new high-speed USB device number 2 using ehci_hcd
May 16 08:16:50 ubuntu kernel: [    3.574969] [drm] Initialized drm 1.1.0 20060810
May 16 08:16:50 ubuntu kernel: [    3.592715] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May 16 08:16:50 ubuntu kernel: [    3.592741] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May 16 08:16:50 ubuntu kernel: [    3.592773] r8169 0000:03:00.0: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    3.592841] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
May 16 08:16:50 ubuntu kernel: [    3.593297] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xf840e000, 00:21:97:3e:6b:56, XID 18000000 IRQ 43
May 16 08:16:50 ubuntu kernel: [    3.593300] r8169 0000:03:00.0: eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
May 16 08:16:50 ubuntu kernel: [    3.600554] VGA switcheroo: detected Optimus DSM method \ handle
May 16 08:16:50 ubuntu kernel: [    3.600581] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 16 08:16:50 ubuntu kernel: [    3.600586] nouveau 0000:01:00.0: setting latency timer to 64
May 16 08:16:50 ubuntu kernel: [    3.601610] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x096080a1)
May 16 08:16:50 ubuntu kernel: [    3.604596] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
May 16 08:16:50 ubuntu kernel: [    3.650526] [drm] nouveau 0000:01:00.0: ... appears to be valid
May 16 08:16:50 ubuntu kernel: [    3.650530] [drm] nouveau 0000:01:00.0: BIT BIOS found
May 16 08:16:50 ubuntu kernel: [    3.650533] [drm] nouveau 0000:01:00.0: Bios version 62.94.4b.00
May 16 08:16:50 ubuntu kernel: [    3.650536] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
May 16 08:16:50 ubuntu kernel: [    3.650538] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
May 16 08:16:50 ubuntu kernel: [    3.650541] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028
May 16 08:16:50 ubuntu kernel: [    3.650544] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00020030
May 16 08:16:50 ubuntu kernel: [    3.650546] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
May 16 08:16:50 ubuntu kernel: [    3.650548] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02022332 00020010
May 16 08:16:50 ubuntu kernel: [    3.650550] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 0000000e 00000000
May 16 08:16:50 ubuntu kernel: [    3.650552] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
May 16 08:16:50 ubuntu kernel: [    3.650555] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
May 16 08:16:50 ubuntu kernel: [    3.650558] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
May 16 08:16:50 ubuntu kernel: [    3.650560] [drm] nouveau 0000:01:00.0:   2: 0x00002261: type 0x61 idx 2 tag 0x08
May 16 08:16:50 ubuntu kernel: [    3.650564] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD20A
May 16 08:16:50 ubuntu kernel: [    3.675642] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD657
May 16 08:16:50 ubuntu kernel: [    3.678640] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE6A7
May 16 08:16:50 ubuntu kernel: [    3.678646] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE7F0
May 16 08:16:50 ubuntu kernel: [    3.679706] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEA5C
May 16 08:16:50 ubuntu kernel: [    3.679708] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xEAC1
May 16 08:16:50 ubuntu kernel: [    3.699602] [drm] nouveau 0000:01:00.0: 0xEAC1: Condition still not met after 20ms, skipping following opcodes
May 16 08:16:50 ubuntu kernel: [    3.718149] [drm] nouveau 0000:01:00.0: 1 available performance level(s)
May 16 08:16:50 ubuntu kernel: [    3.718153] [drm] nouveau 0000:01:00.0: 3: core 550MHz shader 1400MHz memory 400MHz fanspeed 100%
May 16 08:16:50 ubuntu kernel: [    3.718167] [drm] nouveau 0000:01:00.0: c: core 400MHz shader 800MHz memory 399MHz
May 16 08:16:50 ubuntu kernel: [    3.721201] [TTM] Zone  kernel: Available graphics memory: 438830 kiB.
May 16 08:16:50 ubuntu kernel: [    3.721203] [TTM] Zone highmem: Available graphics memory: 1030546 kiB.
May 16 08:16:50 ubuntu kernel: [    3.721205] [TTM] Initializing pool allocator.
May 16 08:16:50 ubuntu kernel: [    3.721213] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
May 16 08:16:50 ubuntu kernel: [    3.722606] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
May 16 08:16:50 ubuntu kernel: [    3.747554] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
May 16 08:16:50 ubuntu kernel: [    3.747557] [drm] No driver support for vblank timestamp query.
May 16 08:16:50 ubuntu kernel: [    3.909283] [drm] nouveau 0000:01:00.0: allocated 1366x768 fb: 0x330000, bo f464da00
May 16 08:16:50 ubuntu kernel: [    3.909340] fbcon: nouveaufb (fb0) is primary device
May 16 08:16:50 ubuntu kernel: [    3.944056] Console: switching to colour frame buffer device 170x48
May 16 08:16:50 ubuntu kernel: [    3.945369] fb0: nouveaufb frame buffer device
May 16 08:16:50 ubuntu kernel: [    3.945370] drm: registered panic notifier
May 16 08:16:50 ubuntu kernel: [    3.945376] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
May 16 08:16:50 ubuntu kernel: [    3.964030] usb 1-5: new high-speed USB device number 4 using ehci_hcd
May 16 08:16:50 ubuntu kernel: [    4.102541] Initializing USB Mass Storage driver...
May 16 08:16:50 ubuntu kernel: [    4.102613] usb-storage 1-5:1.0: Quirks match for vid 13fe pid 3600: 4000
May 16 08:16:50 ubuntu kernel: [    4.102628] scsi2 : usb-storage 1-5:1.0
May 16 08:16:50 ubuntu kernel: [    4.102692] usbcore: registered new interface driver usb-storage
May 16 08:16:50 ubuntu kernel: [    4.102694] USB Mass Storage support registered.
May 16 08:16:50 ubuntu kernel: [    4.153876] Btrfs loaded
May 16 08:16:50 ubuntu kernel: [    4.158370] xor: automatically using best checksumming function: pIII_sse
May 16 08:16:50 ubuntu kernel: [    4.176002]    pIII_sse  :  9903.000 MB/sec
May 16 08:16:50 ubuntu kernel: [    4.176004] xor: using function: pIII_sse (9903.000 MB/sec)
May 16 08:16:50 ubuntu kernel: [    4.176507] device-mapper: dm-raid45: initialized v0.2594b
May 16 08:16:50 ubuntu kernel: [    4.212025] usb 1-7: new high-speed USB device number 5 using ehci_hcd
May 16 08:16:50 ubuntu kernel: [    4.346921] scsi3 : usb-storage 1-7:1.0
May 16 08:16:50 ubuntu kernel: [    4.696022] usb 2-2: new full-speed USB device number 2 using uhci_hcd
May 16 08:16:50 ubuntu kernel: [    4.877409] hub 2-2:1.0: USB hub found
May 16 08:16:50 ubuntu kernel: [    4.879354] hub 2-2:1.0: 4 ports detected
May 16 08:16:50 ubuntu kernel: [    5.100971] scsi 2:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
May 16 08:16:50 ubuntu kernel: [    5.101520] sd 2:0:0:0: Attached scsi generic sg3 type 0
May 16 08:16:50 ubuntu kernel: [    5.102460] sd 2:0:0:0: [sdc] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
May 16 08:16:50 ubuntu kernel: [    5.103826] sd 2:0:0:0: [sdc] Write Protect is off
May 16 08:16:50 ubuntu kernel: [    5.103830] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
May 16 08:16:50 ubuntu kernel: [    5.105205] sd 2:0:0:0: [sdc] No Caching mode page present
May 16 08:16:50 ubuntu kernel: [    5.105207] sd 2:0:0:0: [sdc] Assuming drive cache: write through
May 16 08:16:50 ubuntu kernel: [    5.110327] sd 2:0:0:0: [sdc] No Caching mode page present
May 16 08:16:50 ubuntu kernel: [    5.110331] sd 2:0:0:0: [sdc] Assuming drive cache: write through
May 16 08:16:50 ubuntu kernel: [    5.111522]  sdc: sdc1
May 16 08:16:50 ubuntu kernel: [    5.115965] sd 2:0:0:0: [sdc] No Caching mode page present
May 16 08:16:50 ubuntu kernel: [    5.115969] sd 2:0:0:0: [sdc] Assuming drive cache: write through
May 16 08:16:50 ubuntu kernel: [    5.115978] sd 2:0:0:0: [sdc] Attached SCSI removable disk
May 16 08:16:50 ubuntu kernel: [    5.124029] usb 5-2: new full-speed USB device number 2 using uhci_hcd
May 16 08:16:50 ubuntu kernel: [    5.134285] EXT4-fs (sdb2): bad geometry: block count 5376000 exceeds size of device (5375744 blocks)
May 16 08:16:50 ubuntu kernel: [    5.316456] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input2
May 16 08:16:50 ubuntu kernel: [    5.316532] generic-usb 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-2/input0
May 16 08:16:50 ubuntu kernel: [    5.320105] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/input/input3
May 16 08:16:50 ubuntu kernel: [    5.320310] generic-usb 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2/input1
May 16 08:16:50 ubuntu kernel: [    5.320323] usbcore: registered new interface driver usbhid
May 16 08:16:50 ubuntu kernel: [    5.320324] usbhid: USB HID core driver
May 16 08:16:50 ubuntu kernel: [    5.344724] scsi 3:0:0:0: Direct-Access     JetFlash TS4GJFV60        8.07 PQ: 0 ANSI: 2
May 16 08:16:50 ubuntu kernel: [    5.345253] sd 3:0:0:0: Attached scsi generic sg4 type 0
May 16 08:16:50 ubuntu kernel: [    5.346706] sd 3:0:0:0: [sdd] 7852032 512-byte logical blocks: (4.02 GB/3.74 GiB)
May 16 08:16:50 ubuntu kernel: [    5.347200] sd 3:0:0:0: [sdd] Write Protect is off
May 16 08:16:50 ubuntu kernel: [    5.347204] sd 3:0:0:0: [sdd] Mode Sense: 03 00 00 00
May 16 08:16:50 ubuntu kernel: [    5.347700] sd 3:0:0:0: [sdd] No Caching mode page present
May 16 08:16:50 ubuntu kernel: [    5.347703] sd 3:0:0:0: [sdd] Assuming drive cache: write through
May 16 08:16:50 ubuntu kernel: [    5.350325] sd 3:0:0:0: [sdd] No Caching mode page present
May 16 08:16:50 ubuntu kernel: [    5.350329] sd 3:0:0:0: [sdd] Assuming drive cache: write through
May 16 08:16:50 ubuntu kernel: [    5.881401]  sdd: sdd1
May 16 08:16:50 ubuntu kernel: [    5.884078] sd 3:0:0:0: [sdd] No Caching mode page present
May 16 08:16:50 ubuntu kernel: [    5.884080] sd 3:0:0:0: [sdd] Assuming drive cache: write through
May 16 08:16:50 ubuntu kernel: [    5.884083] sd 3:0:0:0: [sdd] Attached SCSI removable disk
May 16 08:16:50 ubuntu kernel: [    6.619504] EXT4-fs (sdb2): bad geometry: block count 5376000 exceeds size of device (5375744 blocks)
May 16 08:16:50 ubuntu kernel: [    7.184738] squashfs: version 4.0 (2009/01/31) Phillip Lougher
May 16 08:16:50 ubuntu kernel: [   14.093873] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  ModemManager (version 0.5.2.0) starting...
May 16 08:16:50 ubuntu bluetoothd[1454]: Bluetooth daemon 4.98
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin AnyData
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Generic
May 16 08:16:50 ubuntu bluetoothd[1454]: Starting SDP server
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Gobi
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Option High-Speed
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Huawei
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Linktop
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Longcheer
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Ericsson MBM
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin MotoC
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Nokia
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Novatel
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Option
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Samsung
May 16 08:16:50 ubuntu avahi-daemon[1591]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
May 16 08:16:50 ubuntu avahi-daemon[1591]: Successfully dropped root privileges.
May 16 08:16:50 ubuntu avahi-daemon[1591]: avahi-daemon 0.6.30 starting up.
May 16 08:16:50 ubuntu avahi-daemon[1591]: Successfully called chroot().
May 16 08:16:50 ubuntu avahi-daemon[1591]: Successfully dropped remaining capabilities.
May 16 08:16:50 ubuntu avahi-daemon[1591]: Loading service file /services/udisks.service.
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Sierra
May 16 08:16:50 ubuntu avahi-daemon[1591]: Network interface enumeration completed.
May 16 08:16:50 ubuntu avahi-daemon[1591]: Registering HINFO record with values 'I686'/'LINUX'.
May 16 08:16:50 ubuntu avahi-daemon[1591]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1699100057.
May 16 08:16:50 ubuntu avahi-daemon[1591]: Service "ubuntu" (/services/udisks.service) successfully established.
May 16 08:16:50 ubuntu NetworkManager[1617]: <info> NetworkManager (version 0.9.4.0) is starting...
May 16 08:16:50 ubuntu NetworkManager[1617]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
May 16 08:16:50 ubuntu kernel: [   14.473699] Bluetooth: Core ver 2.16
May 16 08:16:50 ubuntu kernel: [   14.473718] NET: Registered protocol family 31
May 16 08:16:50 ubuntu kernel: [   14.473719] Bluetooth: HCI device and connection manager initialized
May 16 08:16:50 ubuntu kernel: [   14.473722] Bluetooth: HCI socket layer initialized
May 16 08:16:50 ubuntu kernel: [   14.473723] Bluetooth: L2CAP socket layer initialized
May 16 08:16:50 ubuntu kernel: [   14.473762] Bluetooth: SCO socket layer initialized
May 16 08:16:50 ubuntu bluetoothd[1454]: Failed to init alert plugin
May 16 08:16:50 ubuntu bluetoothd[1454]: Failed to init time plugin
May 16 08:16:50 ubuntu bluetoothd[1454]: Failed to init proximity plugin
May 16 08:16:50 ubuntu kernel: [   14.498478] intel_rng: FWH not detected
May 16 08:16:50 ubuntu mtp-probe: checking bus 5, device 2: "/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2"
May 16 08:16:50 ubuntu mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7"
May 16 08:16:50 ubuntu mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5"
May 16 08:16:50 ubuntu mtp-probe: bus: 1, device: 4 was not an MTP device
May 16 08:16:50 ubuntu mtp-probe: bus: 1, device: 5 was not an MTP device
May 16 08:16:50 ubuntu mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1"
May 16 08:16:50 ubuntu kernel: [   14.509843] leds_ss4200: no LED devices found
May 16 08:16:50 ubuntu mtp-probe: bus: 1, device: 2 was not an MTP device
May 16 08:16:50 ubuntu mtp-probe: bus: 5, device: 2 was not an MTP device
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin SimTech
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin Wavecom
May 16 08:16:50 ubuntu kernel: [   14.534179] lp: driver loaded but no devices found
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin X22X
May 16 08:16:50 ubuntu kernel: [   14.579083] device-mapper: multipath: version 1.3.0 loaded
May 16 08:16:50 ubuntu modem-manager[1449]: <info>  Loaded plugin ZTE
May 16 08:16:50 ubuntu kernel: [   14.619874] ppdev: user-space parallel port driver
May 16 08:16:50 ubuntu kernel: [   14.633330] Bluetooth: RFCOMM TTY layer initialized
May 16 08:16:50 ubuntu kernel: [   14.633335] Bluetooth: RFCOMM socket layer initialized
May 16 08:16:50 ubuntu kernel: [   14.633336] Bluetooth: RFCOMM ver 1.11
May 16 08:16:50 ubuntu kernel: [   14.635813] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 16 08:16:50 ubuntu kernel: [   14.635816] Bluetooth: BNEP filters: protocol multicast
May 16 08:16:50 ubuntu NetworkManager[1617]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
May 16 08:16:50 ubuntu NetworkManager[1617]: <info> DNS: loaded plugin dnsmasq
May 16 08:16:50 ubuntu bluetoothd[1454]: Failed to init gatt_example plugin
May 16 08:16:50 ubuntu failsafe: Failsafe of 120 seconds reached.
May 16 08:16:50 ubuntu kernel: [   14.669447] parport_pc 00:08: reported by Plug and Play ACPI
May 16 08:16:50 ubuntu kernel: [   14.669523] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May 16 08:16:50 ubuntu kernel: [   14.685592] Linux video capture interface: v2.00
May 16 08:16:50 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
May 16 08:16:50 ubuntu kernel: [   14.705888] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:6340)
May 16 08:16:50 ubuntu kernel: [   14.719854] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input4
May 16 08:16:50 ubuntu kernel: [   14.719966] usbcore: registered new interface driver uvcvideo
May 16 08:16:50 ubuntu kernel: [   14.719968] USB Video Class driver (1.1.1)
May 16 08:16:51 ubuntu kernel: [   14.765248] lp0: using parport0 (interrupt-driven).
May 16 08:16:51 ubuntu kernel: [   14.809948] init: failsafe main process (1679) killed by TERM signal
May 16 08:16:51 ubuntu polkitd[1698]: started daemon version 0.104 using authority implementation `local' version `0.104'
May 16 08:16:51 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: init!
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: update_system_hostname
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPluginIfupdown: management mode: unmanaged
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: end _init.
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May 16 08:16:51 ubuntu NetworkManager[1617]:    Ifupdown: get unmanaged devices count: 0
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: (167955536) ... get_connections.
May 16 08:16:51 ubuntu NetworkManager[1617]:    SCPlugin-Ifupdown: (167955536) ... get_connections (managed=false): return empty list.
May 16 08:16:51 ubuntu NetworkManager[1617]:    Ifupdown: get unmanaged devices count: 0
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> modem-manager is now available
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> WiFi enabled by radio killswitch; enabled by state file
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> WWAN enabled by radio killswitch; enabled by state file
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> WiMAX enabled by radio killswitch; enabled by state file
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> Networking is enabled by state file
May 16 08:16:51 ubuntu NetworkManager[1617]: <warn> failed to allocate link cache: (-10) Operation not supported
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> (eth0): carrier is OFF
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> (eth0): now managed
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> (eth0): bringing up device.
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> (eth0): preparing device.
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> (eth0): deactivating device (reason 'managed') [2]
May 16 08:16:51 ubuntu NetworkManager[1617]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
May 16 08:16:51 ubuntu kernel: [   14.874085] r8169 0000:03:00.0: eth0: link down
May 16 08:16:51 ubuntu kernel: [   14.874091] r8169 0000:03:00.0: eth0: link down
May 16 08:16:51 ubuntu kernel: [   14.874262] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 16 08:16:51 ubuntu kernel: [   14.874595] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 16 08:16:51 ubuntu cron[1899]: (CRON) INFO (pidfile fd = 3)
May 16 08:16:51 ubuntu acpid: starting up with proc fs
May 16 08:16:51 ubuntu acpid: 35 rules loaded
May 16 08:16:51 ubuntu acpid: waiting for events: event logging is off
May 16 08:16:51 ubuntu cron[2035]: (CRON) STARTUP (fork ok)
May 16 08:16:51 ubuntu cron[2035]: (CRON) INFO (Running @reboot jobs)
May 16 08:16:51 ubuntu udev-configure-printer: add /module/lp
May 16 08:16:51 ubuntu udev-configure-printer: Failed to get parent
May 16 08:16:51 ubuntu kernel: [   15.318956] 2:3:1: cannot get freq at ep 0x84
May 16 08:16:51 ubuntu kernel: [   15.329380] usbcore: registered new interface driver snd-usb-audio
May 16 08:16:51 ubuntu udev-configure-printer: add /devices/pnp0/00:08/printer/lp0
May 16 08:16:51 ubuntu udev-configure-printer: Failed to get parent
May 16 08:16:51 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
May 16 08:16:51 ubuntu kernel: [   15.379404] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 16 08:16:51 ubuntu kernel: [   15.379469] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
May 16 08:16:51 ubuntu kernel: [   15.379496] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
May 16 08:16:51 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
May 16 08:16:51 ubuntu kernel: [   15.513477] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
May 16 08:16:51 ubuntu kernel: [   15.513786] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
May 16 08:16:51 ubuntu kernel: [   15.514078] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
May 16 08:16:51 ubuntu kernel: [   15.514374] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
May 16 08:16:51 ubuntu kernel: [   15.514742] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
May 16 08:16:51 ubuntu acpid: client connected from 2232[0:0]
May 16 08:16:51 ubuntu acpid: 1 client rule loaded
May 16 08:16:52 ubuntu udev-configure-printer: add /devices/pnp0/00:08/printer/lp0
May 16 08:16:52 ubuntu udev-configure-printer: Failed to get parent
May 16 08:16:52 ubuntu udev-configure-printer: add /module/lp
May 16 08:16:52 ubuntu udev-configure-printer: Failed to get parent
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> (eth0): carrier now ON (device state 20)
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Auto-activating connection 'Wired connection 1'.
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) starting connection 'Wired connection 1'
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 16 08:16:52 ubuntu kernel: [   16.540443] r8169 0000:03:00.0: eth0: link up
May 16 08:16:52 ubuntu kernel: [   16.540575] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> dhclient started with pid 2847
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Beginning IP6 addrconf.
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 16 08:16:52 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 16 08:16:52 ubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 16 08:16:52 ubuntu dhclient: All rights reserved.
May 16 08:16:52 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 16 08:16:52 ubuntu dhclient: 
May 16 08:16:52 ubuntu NetworkManager[1617]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 16 08:16:52 ubuntu dhclient: Listening on LPF/eth0/00:21:97:3e:6b:56
May 16 08:16:52 ubuntu dhclient: Sending on   LPF/eth0/00:21:97:3e:6b:56
May 16 08:16:52 ubuntu dhclient: Sending on   Socket/fallback
May 16 08:16:52 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 16 08:16:53 ubuntu kernel: [   17.524398] init: plymouth-upstart-bridge main process (1439) killed by TERM signal
May 16 08:16:53 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
May 16 08:16:53 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.Accounts'
May 16 08:16:53 ubuntu accounts-daemon[3201]: started daemon version 0.6.15
May 16 08:16:54 ubuntu avahi-daemon[1591]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::221:97ff:fe3e:6b56.
May 16 08:16:54 ubuntu avahi-daemon[1591]: New relevant interface eth0.IPv6 for mDNS.
May 16 08:16:54 ubuntu avahi-daemon[1591]: Registering new address record for fe80::221:97ff:fe3e:6b56 on eth0.*.
May 16 08:16:54 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
May 16 08:16:54 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.UPower'
May 16 08:16:55 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 16 08:16:55 ubuntu dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
May 16 08:16:55 ubuntu dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
May 16 08:16:55 ubuntu dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
May 16 08:16:55 ubuntu dhclient: bound to 192.168.1.2 -- renewal in 36648 seconds.
May 16 08:16:55 ubuntu NetworkManager[1617]: <info> (eth0): DHCPv4 state changed preinit -> bound
May 16 08:16:55 ubuntu NetworkManager[1617]: <info>   address 192.168.1.2
May 16 08:16:55 ubuntu NetworkManager[1617]: <info>   prefix 24 (255.255.255.0)
May 16 08:16:55 ubuntu NetworkManager[1617]: <info>   gateway 192.168.1.1
May 16 08:16:55 ubuntu NetworkManager[1617]: <info>   nameserver '192.168.1.1'
May 16 08:16:55 ubuntu NetworkManager[1617]: nm_ip4_config_add_nameserver: assertion `nameserver != s' failed
May 16 08:16:55 ubuntu NetworkManager[1617]: <info>   nameserver '192.168.1.1'
May 16 08:16:55 ubuntu NetworkManager[1617]: <info>   domain name 'Home'
May 16 08:16:55 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 16 08:16:55 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May 16 08:16:55 ubuntu avahi-daemon[1591]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
May 16 08:16:55 ubuntu avahi-daemon[1591]: New relevant interface eth0.IPv4 for mDNS.
May 16 08:16:55 ubuntu avahi-daemon[1591]: Registering new address record for 192.168.1.2 on eth0.IPv4.
May 16 08:16:56 ubuntu NetworkManager[1617]: <info> DNS: starting dnsmasq...
May 16 08:16:56 ubuntu NetworkManager[1617]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
May 16 08:16:56 ubuntu dnsmasq[3446]: started, version 2.59 cache disabled
May 16 08:16:56 ubuntu dnsmasq[3446]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 16 08:16:56 ubuntu dnsmasq[3446]: using nameserver 192.168.1.1#53
May 16 08:16:56 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
May 16 08:16:56 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.ColorManager'
May 16 08:16:56 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
May 16 08:16:56 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Successfully called chroot.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Successfully dropped privileges.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Successfully limited resources.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Running.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Canary thread running.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Watchdog thread running.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Successfully made thread 3495 of process 3495 (n/a) owned by '999' high priority at nice level -11.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Supervising 1 threads of 1 processes of 1 users.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Successfully made thread 3500 of process 3495 (n/a) owned by '999' RT at priority 5.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Supervising 2 threads of 1 processes of 1 users.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Successfully made thread 3502 of process 3495 (n/a) owned by '999' RT at priority 5.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Supervising 3 threads of 1 processes of 1 users.
May 16 08:16:56 ubuntu kernel: [   20.480080] 2:3:1: cannot get freq at ep 0x84
May 16 08:16:56 ubuntu kernel: [   20.516022] 2:3:1: cannot get freq at ep 0x84
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Successfully made thread 3509 of process 3495 (n/a) owned by '999' RT at priority 5.
May 16 08:16:56 ubuntu rtkit-daemon[3497]: Supervising 4 threads of 1 processes of 1 users.
May 16 08:16:57 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
May 16 08:16:57 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.UDisks'
May 16 08:17:01 ubuntu CRON[3661]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 16 08:17:02 ubuntu NetworkManager[1617]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 16 08:17:02 ubuntu NetworkManager[1617]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May 16 08:17:02 ubuntu NetworkManager[1617]: <info> Activation (eth0) successful, device activated.
May 16 08:17:02 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May 16 08:17:02 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 16 08:17:02 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 16 08:17:03 ubuntu kernel: [   26.848011] eth0: no IPv6 routers present
May 16 08:17:11 ubuntu goa[3724]: goa-daemon version 3.4.0 starting [main.c:112, main()]
May 16 08:17:13 ubuntu NetworkManager[1617]: <info> (eth0): IP6 addrconf timed out or failed.
May 16 08:17:13 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 16 08:17:13 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 16 08:17:13 ubuntu NetworkManager[1617]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 16 02:47:16 ubuntu ntpdate[3709]: step time server 91.189.94.4 offset -19802.764455 sec
May 16 02:47:54 ubuntu dbus[1422]: [system] Activating service name='com.ubuntu.DeviceDriver' (using servicehelper)
May 16 02:47:54 ubuntu dbus[1422]: [system] Successfully activated service 'com.ubuntu.DeviceDriver'
May 16 02:47:58 ubuntu dbus[1422]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
May 16 02:47:58 ubuntu AptDaemon: INFO: Initializing daemon
May 16 02:47:58 ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May 16 02:47:58 ubuntu dbus[1422]: [system] Successfully activated service 'org.freedesktop.PackageKit'
May 16 02:47:58 ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
May 16 02:47:58 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/ed3451661c4940899304e3b6cd716687
May 16 02:47:58 ubuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/ed3451661c4940899304e3b6cd716687
May 16 02:47:58 ubuntu AptDaemon.PackageKit: INFO: Get updates()
May 16 02:47:59 ubuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/ed3451661c4940899304e3b6cd716687
May 16 02:48:55 ubuntu ubiquity[4169]: Ubiquity 2.10.16
May 16 02:48:56 ubuntu ubiquity[4169]: log-output -t ubiquity laptop-detect
May 16 02:48:59 ubuntu ubiquity[4169]: switched to page language
May 16 02:49:00 ubuntu ubiquity[4169]: switched to page language
May 16 02:49:06 ubuntu localechooser: info: Language = 'en'
May 16 02:49:06 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
May 16 02:49:06 ubuntu localechooser: info: Set debian-installer/language = 'en'
May 16 02:49:06 ubuntu localechooser: info: Default country = 'US'
May 16 02:49:06 ubuntu localechooser: info: Default locale = 'en_US.UTF-8'
May 16 02:49:06 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
May 16 02:49:06 ubuntu localechooser: info: Set debian-installer/country = 'US'
May 16 02:49:06 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May 16 02:49:06 ubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
May 16 02:49:07 ubuntu ubiquity[4169]: debconffilter_done: ubi-language (current: ubi-language)
May 16 02:49:07 ubuntu ubiquity[4169]: Step_before = stepLanguage
May 16 02:49:08 ubuntu ubiquity[4169]: switched to page prepare
May 16 02:49:11 ubuntu dbus[1422]: [system] Activating service name='com.ubuntu.DeviceDriver' (using servicehelper)
May 16 02:49:11 ubuntu dbus[1422]: [system] Successfully activated service 'com.ubuntu.DeviceDriver'
May 16 02:49:15 ubuntu ubiquity: Additional Drivers
May 16 02:49:15 ubuntu ubiquity: Searching for available drivers...
May 16 02:49:15 ubuntu ubiquity[4169]: debconffilter_done: ubi-prepare (current: ubi-prepare)
May 16 02:49:15 ubuntu ubiquity[4169]: Step_before = stepPrepare
May 16 02:49:15 ubuntu ubiquity[4169]: Step_before = stepPrepare
May 16 02:49:16 ubuntu activate-dmraid: No Serial ATA RAID disks detected
May 16 02:49:16 ubuntu kernel: [  162.681810] JFS: nTxBlock = 8192, nTxLock = 65536
May 16 02:49:16 ubuntu kernel: [  162.769614] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
May 16 02:49:16 ubuntu kernel: [  162.771164] SGI XFS Quota Management subsystem
May 16 02:49:24 ubuntu ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 16 02:49:24 ubuntu ntfsresize: Device name        : /dev/sda2
May 16 02:49:24 ubuntu ntfsresize: NTFS volume version: 3.1
May 16 02:49:24 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 16 02:49:24 ubuntu ntfsresize: Current volume size: 104857596416 bytes (104858 MB)
May 16 02:49:24 ubuntu ntfsresize: Current device size: 104857600000 bytes (104858 MB)
May 16 02:49:24 ubuntu ntfsresize: Checking filesystem consistency ...
May 16 02:49:24 ubuntu ntfsresize: Accounting clusters ...
May 16 02:49:24 ubuntu ntfsresize: Space in use       : 13371 MB (12.8%)
May 16 02:49:24 ubuntu ntfsresize: Collecting resizing constraints ...
May 16 02:49:24 ubuntu ntfsresize: You might resize at 13370212352 bytes or 13371 MB (freeing 91487 MB).
May 16 02:49:24 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 16 02:49:26 ubuntu kernel: [  172.627776] usb 1-5: USB disconnect, device number 4
May 16 02:49:28 ubuntu ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 16 02:49:28 ubuntu ntfsresize: Device name        : /dev/sda3
May 16 02:49:28 ubuntu ntfsresize: NTFS volume version: 3.1
May 16 02:49:28 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 16 02:49:28 ubuntu ntfsresize: Current volume size: 895210222080 bytes (895211 MB)
May 16 02:49:28 ubuntu ntfsresize: Current device size: 895210225664 bytes (895211 MB)
May 16 02:49:28 ubuntu ntfsresize: Checking filesystem consistency ...
May 16 02:49:28 ubuntu ntfsresize: Accounting clusters ...
May 16 02:49:28 ubuntu ntfsresize: Space in use       : 544852 MB (60.9%)
May 16 02:49:28 ubuntu ntfsresize: Collecting resizing constraints ...
May 16 02:49:28 ubuntu ntfsresize: You might resize at 544851234816 bytes or 544852 MB (freeing 350359 MB).
May 16 02:49:28 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 16 02:49:29 ubuntu ntfsresize: ntfsresize v2012.1.15AR.1 (libntfs-3g)
May 16 02:49:29 ubuntu ntfsresize: Device name        : /dev/sdb1
May 16 02:49:29 ubuntu ntfsresize: NTFS volume version: 3.1
May 16 02:49:29 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 16 02:49:29 ubuntu ntfsresize: Current volume size: 110356328960 bytes (110357 MB)
May 16 02:49:29 ubuntu ntfsresize: Current device size: 110356332544 bytes (110357 MB)
May 16 02:49:29 ubuntu ntfsresize: Checking filesystem consistency ...
May 16 02:49:29 ubuntu ntfsresize: Accounting clusters ...
May 16 02:49:29 ubuntu ntfsresize: Space in use       : 27055 MB (24.5%)
May 16 02:49:29 ubuntu ntfsresize: Collecting resizing constraints ...
May 16 02:49:29 ubuntu ntfsresize: You might resize at 27054809088 bytes or 27055 MB (freeing 83302 MB).
May 16 02:49:29 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 16 02:49:29 ubuntu ntfs-3g[6493]: Version 2012.1.15AR.1 external FUSE 28
May 16 02:49:29 ubuntu ntfs-3g[6493]: Mounted /dev/sda2 (Read-Only, label "WinStor", NTFS 3.1)
May 16 02:49:29 ubuntu ntfs-3g[6493]: Cmdline options: ro
May 16 02:49:29 ubuntu ntfs-3g[6493]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
May 16 02:49:29 ubuntu ntfs-3g[6493]: Ownership and permissions disabled, configuration type 7
May 16 02:49:29 ubuntu ntfs-3g[6493]: Unmounting /dev/sda2 (WinStor)
May 16 02:49:30 ubuntu ntfs-3g[6502]: Version 2012.1.15AR.1 external FUSE 28
May 16 02:49:30 ubuntu ntfs-3g[6502]: Mounted /dev/sda3 (Read-Only, label "Storage", NTFS 3.1)
May 16 02:49:30 ubuntu ntfs-3g[6502]: Cmdline options: ro
May 16 02:49:30 ubuntu ntfs-3g[6502]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda3,blkdev,blksize=4096
May 16 02:49:30 ubuntu ntfs-3g[6502]: Ownership and permissions disabled, configuration type 7
May 16 02:49:30 ubuntu ntfs-3g[6502]: Unmounting /dev/sda3 (Storage)
May 16 02:49:30 ubuntu ntfs-3g[6513]: Version 2012.1.15AR.1 external FUSE 28
May 16 02:49:30 ubuntu ntfs-3g[6513]: Mounted /dev/sdb1 (Read-Only, label "", NTFS 3.1)
May 16 02:49:30 ubuntu ntfs-3g[6513]: Cmdline options: ro
May 16 02:49:30 ubuntu ntfs-3g[6513]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
May 16 02:49:30 ubuntu ntfs-3g[6513]: Ownership and permissions disabled, configuration type 7
May 16 02:49:30 ubuntu ntfs-3g[6513]: Unmounting /dev/sdb1 ()
May 16 02:49:30 ubuntu kernel: [  177.037381] EXT4-fs (sdb2): bad geometry: block count 5376000 exceeds size of device (5375744 blocks)
May 16 02:49:30 ubuntu ubiquity: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
May 16 02:49:30 ubuntu ubiquity:        missing codepage or helper program, or other error
May 16 02:49:30 ubuntu ubiquity:        In some cases useful info is found in syslog - try
May 16 02:49:30 ubuntu ubiquity:        dmesg | tail  or so
May 16 02:49:30 ubuntu ubiquity: 
May 16 02:49:30 ubuntu ubiquity: umount: /tmp/tmp.QvmegMeLjU: not mounted
May 16 02:49:30 ubuntu ntfs-3g[6587]: Version 2012.1.15AR.1 external FUSE 28
May 16 02:49:30 ubuntu ntfs-3g[6587]: Mounted /dev/sda2 (Read-Only, label "WinStor", NTFS 3.1)
May 16 02:49:30 ubuntu ntfs-3g[6587]: Cmdline options: ro
May 16 02:49:30 ubuntu ntfs-3g[6587]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
May 16 02:49:30 ubuntu ntfs-3g[6587]: Ownership and permissions disabled, configuration type 7
May 16 02:49:30 ubuntu ntfs-3g[6587]: Unmounting /dev/sda2 (WinStor)
May 16 02:49:31 ubuntu ntfs-3g[6596]: Version 2012.1.15AR.1 external FUSE 28
May 16 02:49:31 ubuntu ntfs-3g[6596]: Mounted /dev/sda3 (Read-Only, label "Storage", NTFS 3.1)
May 16 02:49:31 ubuntu ntfs-3g[6596]: Cmdline options: ro
May 16 02:49:31 ubuntu ntfs-3g[6596]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sda3,blkdev,blksize=4096
May 16 02:49:31 ubuntu ntfs-3g[6596]: Ownership and permissions disabled, configuration type 7
May 16 02:49:31 ubuntu ntfs-3g[6596]: Unmounting /dev/sda3 (Storage)
May 16 02:49:31 ubuntu ntfs-3g[6607]: Version 2012.1.15AR.1 external FUSE 28
May 16 02:49:31 ubuntu ntfs-3g[6607]: Mounted /dev/sdb1 (Read-Only, label "", NTFS 3.1)
May 16 02:49:31 ubuntu ntfs-3g[6607]: Cmdline options: ro
May 16 02:49:31 ubuntu ntfs-3g[6607]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
May 16 02:49:31 ubuntu ntfs-3g[6607]: Ownership and permissions disabled, configuration type 7
May 16 02:49:31 ubuntu ntfs-3g[6607]: Unmounting /dev/sdb1 ()
May 16 02:49:31 ubuntu kernel: [  177.842722] EXT4-fs (sdb2): bad geometry: block count 5376000 exceeds size of device (5375744 blocks)
May 16 02:49:31 ubuntu ubiquity: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
May 16 02:49:31 ubuntu ubiquity:        missing codepage or helper program, or other error
May 16 02:49:31 ubuntu ubiquity:        In some cases useful info is found in syslog - try
May 16 02:49:31 ubuntu ubiquity:        dmesg | tail  or so
May 16 02:49:31 ubuntu ubiquity: 
May 16 02:49:31 ubuntu ubiquity: umount: /tmp/tmp.bj45xZYXU8: not mounted
May 16 02:49:31 ubuntu ubiquity[4169]: Traceback (most recent call last):
May 16 02:49:31 ubuntu ubiquity[4169]:   File "/usr/lib/ubiquity/ubiquity/misc.py", line 203, in boot_device
May 16 02:49:31 ubuntu ubiquity[4169]:     for part in p.partitions():
May 16 02:49:31 ubuntu ubiquity[4169]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 206, in partitions
May 16 02:49:31 ubuntu ubiquity[4169]:     self.open_dialog('PARTITIONS')
May 16 02:49:31 ubuntu ubiquity[4169]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 135, in open_dialog
May 16 02:49:31 ubuntu ubiquity[4169]:     self.outf = open(outfifo, 'r')
May 16 02:49:31 ubuntu ubiquity[4169]: IOError: [Errno 2] No such file or directory: '/var/lib/partman/outfifo'
May 16 02:49:31 ubuntu ubiquity[4169]: 
May 16 02:49:31 ubuntu ubiquity[4169]: Traceback (most recent call last):
May 16 02:49:31 ubuntu ubiquity[4169]:   File "/usr/lib/ubiquity/ubiquity/misc.py", line 203, in boot_device
May 16 02:49:31 ubuntu ubiquity[4169]:     for part in p.partitions():
May 16 02:49:31 ubuntu ubiquity[4169]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 206, in partitions
May 16 02:49:31 ubuntu ubiquity[4169]:     self.open_dialog('PARTITIONS')
May 16 02:49:31 ubuntu ubiquity[4169]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 137, in open_dialog
May 16 02:49:31 ubuntu ubiquity[4169]:     self.error_handler()
May 16 02:49:31 ubuntu ubiquity[4169]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 126, in error_handler
May 16 02:49:31 ubuntu ubiquity[4169]:     raise PartedServerError(exception_type, message, options)
May 16 02:49:31 ubuntu ubiquity[4169]: PartedServerError: ('', '', [])
May 16 02:49:31 ubuntu ubiquity[4169]: 
May 16 02:49:31 ubuntu ubiquity[4169]: debconffilter_done: ubi-partman (current: ubi-partman)
May 16 02:49:31 ubuntu ubiquity[4169]: dbfilter_handle_status: ('ubi-partman', 141)
May 16 02:49:38 ubuntu ubiquity[4169]: dbfilter_handle_status: response -7
May 16 02:49:39 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May 16 02:49:39 ubuntu ubiquity[4169]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^oem-config/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
May 16 02:49:39 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May 16 02:49:39 ubuntu ubiquity[4169]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^keyboard-configuration/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
May 16 02:49:39 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May 16 02:49:39 ubuntu ubiquity[4169]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
May 16 02:50:53 ubuntu kernel: [  260.116025] usb 1-5: new high-speed USB device number 7 using ehci_hcd
May 16 02:50:53 ubuntu mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5"
May 16 02:50:53 ubuntu kernel: [  260.253194] usb-storage 1-5:1.0: Quirks match for vid 13fe pid 3600: 4000
May 16 02:50:53 ubuntu kernel: [  260.253226] scsi4 : usb-storage 1-5:1.0
May 16 02:50:53 ubuntu mtp-probe: bus: 1, device: 7 was not an MTP device
May 16 02:50:54 ubuntu kernel: [  261.275558] scsi 4:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
May 16 02:50:54 ubuntu kernel: [  261.276600] sd 4:0:0:0: Attached scsi generic sg3 type 0
May 16 02:50:55 ubuntu kernel: [  261.745795] sd 4:0:0:0: [sdc] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
May 16 02:50:55 ubuntu kernel: [  261.747158] sd 4:0:0:0: [sdc] Write Protect is off
May 16 02:50:55 ubuntu kernel: [  261.747163] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
May 16 02:50:55 ubuntu kernel: [  261.748535] sd 4:0:0:0: [sdc] No Caching mode page present
May 16 02:50:55 ubuntu kernel: [  261.748539] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May 16 02:50:55 ubuntu kernel: [  261.753781] sd 4:0:0:0: [sdc] No Caching mode page present
May 16 02:50:55 ubuntu kernel: [  261.753785] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May 16 02:50:55 ubuntu kernel: [  261.771359]  sdc: sdc1
May 16 02:50:55 ubuntu kernel: [  261.775656] sd 4:0:0:0: [sdc] No Caching mode page present
May 16 02:50:55 ubuntu kernel: [  261.775661] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May 16 02:50:55 ubuntu kernel: [  261.775666] sd 4:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by forpeterssake on 2012-05-17
I get the same error trying to install Lubuntu 12.04 to my netbook, an Asus EeePC 900. I see people have experienced this or similar errors since Oneiric or earlier. From previous threads, I suspect it may be related to the fact that this particular netbook has two internal drives (a 4GB for the OS and a 16GB for data), but I don't know for sure. Anyone more experienced users have any ideas?

---

### Post by cyb3r_sn4k3 on 2012-05-17
> **forpeterssake said:**
> I get the same error trying to install Lubuntu 12.04 to my netbook, an Asus EeePC 900. I see people have experienced this or similar errors since Oneiric or earlier. From previous threads, I suspect it may be related to the fact that this particular netbook has two internal drives (a 4GB for the OS and a 16GB for data), but I don't know for sure. Anyone more experienced users have any ideas?

Same here. Haven't had any problems like this in past Ubuntu installs. And even I have 2 HDD. Maybe thats why ? And I also got an error during windows 7 install also, and when I tried removing one HDD it worked. So I will try using 1 HDD and install and will post results. :)

---

### Post by cyb3r_sn4k3 on 2012-05-17
Yes! It worked. I removed the HDD which I wasn't gonna install to, and installation works without any problems! I had the the same problem with Windows 7 install. Is this a problem with my computer ?

---

### Post by forpeterssake on 2012-05-17
> **cyb3r_sn4k3 said:**
> Yes! It worked. I removed the HDD which I wasn't gonna install to, and installation works without any problems! I had the the same problem with Windows 7 install. Is this a problem with my computer ?

Sounds like I should give that a try. I'm not exactly sure how to do it on this netbook, but I'll take a look tonight. What a weird bug.

---

