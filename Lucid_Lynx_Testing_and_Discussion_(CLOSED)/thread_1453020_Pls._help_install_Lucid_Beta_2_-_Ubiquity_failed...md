---
title: "Pls. help install Lucid Beta 2 - Ubiquity failed..."
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2010-04-12
Hello,

I am installing Ubuntu 10.04 Beta2 onto my desktop PC which has Windows 7, openSUSE 11.2 and Fedora Core 12. Media check was OK. Near the end of the installation the machine reboots to a Ubuntu desktop with an Examples folder and an Install Ubuntu 10.04 folder, and the monitor shows the following message:

"Ubiquity.components.partman failed - Exit code 10. Further info in /var/log/syslog"

Hit "Install Ubuntu 10.04" folder to re-install Ubuntu 10.04: same problem.

Tried again with Ubuntu 9.10 with same problem!

How can I view and read /var/log/syslog if Ubuntu fails to be installed and therefore I cannot access this log?

I would appreciate your help and practical solutions.

:confused:

---

### Post by iClouseau88 on 2010-04-12
Hi,

I cleaned the DVD drive and checked SHA1 of Lucid install CD: OK. Still got rebooted into Ubuntu screen at the end of installation process.  Here's the content of /var/log/syslog from the terminal:

Apr 12 20:30:32 ubuntu kernel: imklog 4.2.0, log source ```
= /proc/kmsg started.
Apr 12 20:30:32 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1065" x-info="http://www.rsyslog.com"] (re)start
Apr 12 20:30:32 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Apr 12 20:30:32 ubuntu rsyslogd: rsyslogd's userid changed to 101
Apr 12 20:30:32 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Linux version 2.6.32-19-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 (Ubuntu 2.6.32-19.28-generic 2.6.32.10+drm33.1)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Apr 12 20:30:32 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff30000 (usable)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ff30000 - 000000007ff40000 (ACPI data)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] DMI 2.3 present.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] last_pfn = 0x7ff30 max_arch_pfn = 0x100000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   A0000-DFFFF uncachable
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   E0000-EFFFF write-through
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   1 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   2 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   3 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   4 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   5 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   6 base 0E0000000 mask FFC000000 write-combining
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   7 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Apr 12 20:30:32 ubuntu kernel: [    0.000000] modified physical RAM map:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000007ff30000 (usable)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 000000007ff30000 - 000000007ff40000 (ACPI data)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 00000000ff7c0000 - 0000000100000000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Apr 12 20:30:32 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] RAMDISK: 7f62c000 - 7feff7be
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008dc000 - 011af7be
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007f62c000 - 000000007feff7bd to 008dc000 - 011af7bd
Apr 12 20:30:32 ubuntu kernel: [    0.000000] 1159MB HIGHMEM available.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Apr 12 20:30:32 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008d7e98]    TEXT DATA BSS ==> [0000100000 - 00008d7e98]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #5 [00008d8000 - 00008db1a4]              BRK ==> [00008d8000 - 00008db1a4]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #7 [00008dc000 - 00011af7be]      NEW RAMDISK ==> [00008dc000 - 00011af7be]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Zone PFN ranges:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007ff30
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Apr 12 20:30:32 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007ff30
Apr 12 20:30:32 ubuntu kernel: [    0.000000] On node 0 totalpages: 523967
Apr 12 20:30:32 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c0796720, node_mem_map c11b1200
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   HighMem zone: 2319 pages used for memmap
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   HighMem zone: 294435 pages, LIFO batch:31
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Using APIC driver default
Apr 12 20:30:32 ubuntu kernel: [    0.000000] SFI: Simple Firmware Interface v0.7 [http://simplefirmware.org](http://simplefirmware.org)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     Virtual Wire compatibility mode.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MPTABLE: OEM ID: TEMPLATE
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MPTABLE: Product ID: 
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MPTABLE: APIC at: 0xFEE00000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] I/O APIC #13 Version 3 at 0xFEC00000.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MPTABLE: no processors registered!
Apr 12 20:30:32 ubuntu kernel: [    0.000000] BIOS bug, MP table errors detected!...
Apr 12 20:30:32 ubuntu kernel: [    0.000000] ... disabling SMP support. (tell your hw vendor)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Apr 12 20:30:32 ubuntu kernel: [    0.000000] APIC: disable apic facility
Apr 12 20:30:32 ubuntu kernel: [    0.000000] nr_irqs_gsi: 16
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7f7c0000)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr 12 20:30:32 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s35992 r0 d21352 u4194304
Apr 12 20:30:32 ubuntu kernel: [    0.000000] pcpu-alloc: s35992 r0 d21352 u4194304 alloc=1*4194304
Apr 12 20:30:32 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519872
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz  splash --  acpi=off noapic nolapic nomodeset
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Initializing CPU#0
Apr 12 20:30:32 ubuntu kernel: [    0.000000] allocated 10481280 bytes of page_cgroup
Apr 12 20:30:32 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007ff30)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Memory: 2050220k/2096320k available (4671k kernel code, 44632k reserved, 2116k data, 656k init, 1187016k highmem)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]       .init : 0xc07a1000 - 0xc0845000   ( 656 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]       .data : 0xc058fd43 - 0xc07a0e48   (2116 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc058fd43   (4671 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Apr 12 20:30:32 ubuntu kernel: [    0.000000] console [tty0] enabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Detected 2520.068 MHz processor.
Apr 12 20:30:32 ubuntu kernel: [    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5040.13 BogoMIPS (lpj=10080272)
Apr 12 20:30:32 ubuntu kernel: [    0.004154] Security Framework initialized
Apr 12 20:30:32 ubuntu kernel: [    0.004252] AppArmor: AppArmor initialized
Apr 12 20:30:32 ubuntu kernel: [    0.004323] Mount-cache hash table entries: 512
Apr 12 20:30:32 ubuntu kernel: [    0.004581] Initializing cgroup subsys ns
Apr 12 20:30:32 ubuntu kernel: [    0.004649] Initializing cgroup subsys cpuacct
Apr 12 20:30:32 ubuntu kernel: [    0.004715] Initializing cgroup subsys memory
Apr 12 20:30:32 ubuntu kernel: [    0.004788] Initializing cgroup subsys devices
Apr 12 20:30:32 ubuntu kernel: [    0.004851] Initializing cgroup subsys freezer
Apr 12 20:30:32 ubuntu kernel: [    0.004914] Initializing cgroup subsys net_cls
Apr 12 20:30:32 ubuntu kernel: [    0.005009] CPU: Trace cache: 12K uops, L1 D cache: 8K
Apr 12 20:30:32 ubuntu kernel: [    0.005121] CPU: L2 cache: 512K
Apr 12 20:30:32 ubuntu kernel: [    0.005183] CPU: Hyper-Threading is disabled
Apr 12 20:30:32 ubuntu kernel: [    0.005248] mce: CPU supports 4 MCE banks
Apr 12 20:30:32 ubuntu kernel: [    0.005330] Performance Events: no PMU driver, software events only.
Apr 12 20:30:32 ubuntu kernel: [    0.005449] Checking 'hlt' instruction... OK.
Apr 12 20:30:32 ubuntu kernel: [    0.021134] SMP alternatives: switching to UP code
Apr 12 20:30:32 ubuntu kernel: [    0.033821] Freeing SMP alternatives: 19k freed
Apr 12 20:30:32 ubuntu kernel: [    0.033915] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr 12 20:30:32 ubuntu kernel: [    0.033987] ftrace: allocating 21765 entries in 43 pages
Apr 12 20:30:32 ubuntu kernel: [    0.036114] weird, boot CPU (#0) not listed by the BIOS.
Apr 12 20:30:32 ubuntu kernel: [    0.036185] SMP motherboard not detected.
Apr 12 20:30:32 ubuntu kernel: [    0.036246] Apic disabled
Apr 12 20:30:32 ubuntu kernel: [    0.036304] Local APIC not detected. Using dummy APIC emulation.
Apr 12 20:30:32 ubuntu kernel: [    0.036367] SMP disabled
Apr 12 20:30:32 ubuntu kernel: [    0.036651] Brought up 1 CPUs
Apr 12 20:30:32 ubuntu kernel: [    0.036714] Total of 1 processors activated (5040.13 BogoMIPS).
Apr 12 20:30:32 ubuntu kernel: [    0.040058] CPU0 attaching NULL sched-domain.
Apr 12 20:30:32 ubuntu kernel: [    0.040228] devtmpfs: initialized
Apr 12 20:30:32 ubuntu kernel: [    0.040787] regulator: core version 0.5
Apr 12 20:30:32 ubuntu kernel: [    0.040890] Time: 20:29:42  Date: 04/12/10
Apr 12 20:30:32 ubuntu kernel: [    0.041010] NET: Registered protocol family 16
Apr 12 20:30:32 ubuntu kernel: [    0.041227] EISA bus registered
Apr 12 20:30:32 ubuntu kernel: [    0.041449] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Apr 12 20:30:32 ubuntu kernel: [    0.041512] PCI: Using configuration type 1 for base access
Apr 12 20:30:32 ubuntu kernel: [    0.042867] bio: create slab <bio-0> at 0
Apr 12 20:30:32 ubuntu kernel: [    0.042990] ACPI: Interpreter disabled.
Apr 12 20:30:32 ubuntu kernel: [    0.043129] vgaarb: loaded
Apr 12 20:30:32 ubuntu kernel: [    0.043340] SCSI subsystem initialized
Apr 12 20:30:32 ubuntu kernel: [    0.043453] libata version 3.00 loaded.
Apr 12 20:30:32 ubuntu kernel: [    0.043544] usbcore: registered new interface driver usbfs
Apr 12 20:30:32 ubuntu kernel: [    0.043621] usbcore: registered new interface driver hub
Apr 12 20:30:32 ubuntu kernel: [    0.043720] usbcore: registered new device driver usb
Apr 12 20:30:32 ubuntu kernel: [    0.044163] PCI: Probing PCI hardware
Apr 12 20:30:32 ubuntu kernel: [    0.044226] PCI: Probing PCI hardware (bus 00)
Apr 12 20:30:32 ubuntu kernel: [    0.044282] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
Apr 12 20:30:32 ubuntu kernel: [    0.044384] pci 0000:00:01.0: supports D1
Apr 12 20:30:32 ubuntu kernel: [    0.044428] pci 0000:00:0a.0: reg 10 io port: [0xeea0-0xeebf]
Apr 12 20:30:32 ubuntu kernel: [    0.044473] pci 0000:00:0a.0: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.044509] pci 0000:00:0d.0: reg 10 io port: [0xe000-0xe0ff]
Apr 12 20:30:32 ubuntu kernel: [    0.044517] pci 0000:00:0d.0: reg 14 32bit mmio: [0xdfd00000-0xdfd000ff]
Apr 12 20:30:32 ubuntu kernel: [    0.044542] pci 0000:00:0d.0: reg 30 32bit mmio pref: [0xdfc00000-0xdfc1ffff]
Apr 12 20:30:32 ubuntu kernel: [    0.044562] pci 0000:00:0d.0: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.044565] pci 0000:00:0d.0: PME# supported from D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.044631] pci 0000:00:0d.0: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.044725] pci 0000:00:0f.0: reg 10 io port: [0xefe0-0xefe7]
Apr 12 20:30:32 ubuntu kernel: [    0.044734] pci 0000:00:0f.0: reg 14 io port: [0xefac-0xefaf]
Apr 12 20:30:32 ubuntu kernel: [    0.044742] pci 0000:00:0f.0: reg 18 io port: [0xefa0-0xefa7]
Apr 12 20:30:32 ubuntu kernel: [    0.044750] pci 0000:00:0f.0: reg 1c io port: [0xefa8-0xefab]
Apr 12 20:30:32 ubuntu kernel: [    0.044757] pci 0000:00:0f.0: reg 20 io port: [0xef90-0xef9f]
Apr 12 20:30:32 ubuntu kernel: [    0.044765] pci 0000:00:0f.0: reg 24 io port: [0xe800-0xe8ff]
Apr 12 20:30:32 ubuntu kernel: [    0.044840] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
Apr 12 20:30:32 ubuntu kernel: [    0.044928] pci 0000:00:10.0: reg 20 io port: [0xeec0-0xeedf]
Apr 12 20:30:32 ubuntu kernel: [    0.044955] pci 0000:00:10.0: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.044958] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045024] pci 0000:00:10.0: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045133] pci 0000:00:10.1: reg 20 io port: [0xef00-0xef1f]
Apr 12 20:30:32 ubuntu kernel: [    0.045161] pci 0000:00:10.1: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.045165] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045230] pci 0000:00:10.1: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045340] pci 0000:00:10.2: reg 20 io port: [0xef20-0xef3f]
Apr 12 20:30:32 ubuntu kernel: [    0.045368] pci 0000:00:10.2: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.045372] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045437] pci 0000:00:10.2: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045547] pci 0000:00:10.3: reg 20 io port: [0xef40-0xef5f]
Apr 12 20:30:32 ubuntu kernel: [    0.045575] pci 0000:00:10.3: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.045578] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045644] pci 0000:00:10.3: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045737] pci 0000:00:10.4: reg 10 32bit mmio: [0xdfe00000-0xdfe000ff]
Apr 12 20:30:32 ubuntu kernel: [    0.045782] pci 0000:00:10.4: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.045785] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045851] pci 0000:00:10.4: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045976] HPET not enabled in BIOS. You might try hpet=force boot option
Apr 12 20:30:32 ubuntu kernel: [    0.046043] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
Apr 12 20:30:32 ubuntu kernel: [    0.046161] pci 0000:00:11.5: reg 10 io port: [0x1000-0x10ff]
Apr 12 20:30:32 ubuntu kernel: [    0.046208] pci 0000:00:11.5: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.046245] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
Apr 12 20:30:32 ubuntu kernel: [    0.046326] pci 0000:00:12.0: reg 10 io port: [0xe400-0xe4ff]
Apr 12 20:30:32 ubuntu kernel: [    0.046334] pci 0000:00:12.0: reg 14 32bit mmio: [0xdff00000-0xdff000ff]
Apr 12 20:30:32 ubuntu kernel: [    0.046375] pci 0000:00:12.0: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.046378] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.046443] pci 0000:00:12.0: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.046563] pci 0000:01:00.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
Apr 12 20:30:32 ubuntu kernel: [    0.046571] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xc0000000-0xcfffffff]
Apr 12 20:30:32 ubuntu kernel: [    0.046592] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xdf600000-0xdf61ffff]
Apr 12 20:30:32 ubuntu kernel: [    0.046653] pci 0000:00:01.0: bridge 32bit mmio: [0xdd500000-0xdf6fffff]
Apr 12 20:30:32 ubuntu kernel: [    0.046658] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbd400000-0xdd3fffff]
Apr 12 20:30:32 ubuntu kernel: [    0.047088] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr 12 20:30:32 ubuntu kernel: [    0.047224] pci 0000:00:11.0: VIA IRQ router [1106:3227]
Apr 12 20:30:32 ubuntu kernel: [    0.047309] PCI: setting IRQ 11 as level-triggered
Apr 12 20:30:32 ubuntu kernel: [    0.047314] pci 0000:00:0f.1: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    0.047388] pci 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    0.047453] pci 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    0.047527] pci 0000:00:0f.1: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    0.047605] PCI: setting IRQ 5 as level-triggered
Apr 12 20:30:32 ubuntu kernel: [    0.047610] pci 0000:00:11.5: found PCI INT C -> IRQ 5
Apr 12 20:30:32 ubuntu kernel: [    0.048023] pci 0000:00:11.5: sharing IRQ 5 with 0000:00:0a.0
Apr 12 20:30:32 ubuntu kernel: [    0.048100] pci 0000:00:11.5: sharing IRQ 5 with 0000:00:10.4
Apr 12 20:30:32 ubuntu kernel: [    0.048168] pci 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
Apr 12 20:30:32 ubuntu kernel: [    0.048408] NetLabel: Initializing
Apr 12 20:30:32 ubuntu kernel: [    0.048470] NetLabel:  domain hash size = 128
Apr 12 20:30:32 ubuntu kernel: [    0.048530] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 12 20:30:32 ubuntu kernel: [    0.048606] NetLabel:  unlabeled traffic allowed by default
Apr 12 20:30:32 ubuntu kernel: [    0.048717] Switching to clocksource tsc
Apr 12 20:30:32 ubuntu kernel: [    0.051432] AppArmor: AppArmor Filesystem Enabled
Apr 12 20:30:32 ubuntu kernel: [    0.051505] pnp: PnP ACPI: disabled
Apr 12 20:30:32 ubuntu kernel: [    0.051568] PnPBIOS: Scanning system for PnP BIOS support...
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5b70
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x675a, dseg 0xf0000
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PNPBIOS fault.. attempting recovery.
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: Check with your vendor for an updated BIOS
Apr 12 20:30:32 ubuntu kernel: [    0.051654] PnPBIOS: get_dev_node: unexpected status 0x3a
Apr 12 20:30:32 ubuntu kernel: [    0.051717] PnPBIOS: 10 nodes reported by PnP BIOS; 10 recorded by driver
Apr 12 20:30:32 ubuntu kernel: [    0.051794] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.051860] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.051925] system 00:00: iomem range 0xe4000-0xfffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.051990] system 00:00: iomem range 0x100000-0x7ff2ffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052063] system 00:00: iomem range 0x7ff30000-0x7ff3ffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052136] system 00:00: iomem range 0x7ff40000-0x7ffeffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052209] system 00:00: iomem range 0x7fff0000-0x7fffffff has been reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052274] system 00:00: iomem range 0xff7c0000-0xffffffff has been reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052609] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Apr 12 20:30:32 ubuntu kernel: [    0.052673] pci 0000:00:01.0:   IO window: disabled
Apr 12 20:30:32 ubuntu kernel: [    0.052738] pci 0000:00:01.0:   MEM window: 0xdd500000-0xdf6fffff
Apr 12 20:30:32 ubuntu kernel: [    0.052803] pci 0000:00:01.0:   PREFETCH window: 0xbd400000-0xdd3fffff
Apr 12 20:30:32 ubuntu kernel: [    0.052882] pci 0000:00:01.0: setting latency timer to 64
Apr 12 20:30:32 ubuntu kernel: [    0.052888] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Apr 12 20:30:32 ubuntu kernel: [    0.052891] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Apr 12 20:30:32 ubuntu kernel: [    0.052895] pci_bus 0000:01: resource 1 mem: [0xdd500000-0xdf6fffff]
Apr 12 20:30:32 ubuntu kernel: [    0.052898] pci_bus 0000:01: resource 2 pref mem [0xbd400000-0xdd3fffff]
Apr 12 20:30:32 ubuntu kernel: [    0.052948] NET: Registered protocol family 2
Apr 12 20:30:32 ubuntu kernel: [    0.053135] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.053697] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.054722] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.055421] TCP: Hash tables configured (established 131072 bind 65536)
Apr 12 20:30:32 ubuntu kernel: [    0.055494] TCP reno registered
Apr 12 20:30:32 ubuntu kernel: [    0.055731] NET: Registered protocol family 1
Apr 12 20:30:32 ubuntu kernel: [    0.055820] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Apr 12 20:30:32 ubuntu kernel: [    1.654779] pci 0000:00:10.4: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Apr 12 20:30:32 ubuntu kernel: [    1.654955] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
Apr 12 20:30:32 ubuntu kernel: [    1.655034] pci 0000:01:00.0: Boot video device
Apr 12 20:30:32 ubuntu kernel: [    1.655246] cpufreq-nforce2: No nForce2 chipset.
Apr 12 20:30:32 ubuntu kernel: [    1.655351] Scanning for low memory corruption every 60 seconds
Apr 12 20:30:32 ubuntu kernel: [    1.655553] audit: initializing netlink socket (disabled)
Apr 12 20:30:32 ubuntu kernel: [    1.655629] type=2000 audit(1271104183.654:1): initialized
Apr 12 20:30:32 ubuntu kernel: [    1.664427] Trying to unpack rootfs image as initramfs...
Apr 12 20:30:32 ubuntu kernel: [    4.879412] highmem bounce pool size: 64 pages
Apr 12 20:30:32 ubuntu kernel: [    4.879488] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 12 20:30:32 ubuntu kernel: [    4.881417] VFS: Disk quotas dquot_6.5.2
Apr 12 20:30:32 ubuntu kernel: [    4.881553] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 12 20:30:32 ubuntu kernel: [    4.882422] fuse init (API version 7.13)
Apr 12 20:30:32 ubuntu kernel: [    4.882598] msgmni has been set to 1687
Apr 12 20:30:32 ubuntu kernel: [    4.882977] alg: No test for stdrng (krng)
Apr 12 20:30:32 ubuntu kernel: [    4.883127] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr 12 20:30:32 ubuntu kernel: [    4.883201] io scheduler noop registered
Apr 12 20:30:32 ubuntu kernel: [    4.883262] io scheduler anticipatory registered
Apr 12 20:30:32 ubuntu kernel: [    4.883323] io scheduler deadline registered
Apr 12 20:30:32 ubuntu kernel: [    4.883432] io scheduler cfq registered (default)
Apr 12 20:30:32 ubuntu kernel: [    4.883639] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 12 20:30:32 ubuntu kernel: [    4.883733] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 12 20:30:32 ubuntu kernel: [    4.885800] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr 12 20:30:32 ubuntu kernel: [    4.885977] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 12 20:30:32 ubuntu kernel: [    4.886474] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 12 20:30:32 ubuntu kernel: [    4.887902] brd: module loaded
Apr 12 20:30:32 ubuntu kernel: [    4.888578] loop: module loaded
Apr 12 20:30:32 ubuntu kernel: [    4.888772] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 12 20:30:32 ubuntu kernel: [    4.889052] pata_acpi 0000:00:0f.1: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    4.889129] pata_acpi 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    4.889196] pata_acpi 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    4.889272] pata_acpi 0000:00:0f.1: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    4.889340] pata_acpi 0000:00:0f.1: VIA VLink IRQ fixup, from 255 to 11
Apr 12 20:30:32 ubuntu kernel: [    4.889912] Fixed MDIO Bus: probed
Apr 12 20:30:32 ubuntu kernel: [    4.890021] PPP generic driver version 2.4.2
Apr 12 20:30:32 ubuntu kernel: [    4.890143] tun: Universal TUN/TAP device driver, 1.6
Apr 12 20:30:32 ubuntu kernel: [    4.890205] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr 12 20:30:32 ubuntu kernel: [    4.890383] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 12 20:30:32 ubuntu kernel: [    4.890470] ehci_hcd 0000:00:10.4: found PCI INT C -> IRQ 5
Apr 12 20:30:32 ubuntu kernel: [    4.890538] ehci_hcd 0000:00:10.4: sharing IRQ 5 with 0000:00:0a.0
Apr 12 20:30:32 ubuntu kernel: [    4.890618] ehci_hcd 0000:00:10.4: sharing IRQ 5 with 0000:00:11.5
Apr 12 20:30:32 ubuntu kernel: [    4.890683] ehci_hcd 0000:00:10.4: sharing IRQ 5 with 0000:00:11.6
Apr 12 20:30:32 ubuntu kernel: [    4.890834] isapnp: Scanning for PnP cards...
Apr 12 20:30:32 ubuntu kernel: [    4.896429] ehci_hcd 0000:00:10.4: EHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.896545] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
Apr 12 20:30:32 ubuntu kernel: [    4.896669] ehci_hcd 0000:00:10.4: irq 5, io mem 0xdfe00000
Apr 12 20:30:32 ubuntu kernel: [    4.940327] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
Apr 12 20:30:32 ubuntu kernel: [    4.940511] usb usb1: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.940616] hub 1-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.940687] hub 1-0:1.0: 8 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.940820] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 12 20:30:32 ubuntu kernel: [    4.940901] uhci_hcd: USB Universal Host Controller Interface driver
Apr 12 20:30:32 ubuntu kernel: [    4.941017] uhci_hcd 0000:00:10.0: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    4.941091] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:0f.1
Apr 12 20:30:32 ubuntu kernel: [    4.941158] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    4.941233] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    4.941305] uhci_hcd 0000:00:10.0: UHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.941410] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Apr 12 20:30:32 ubuntu kernel: [    4.941508] uhci_hcd 0000:00:10.0: irq 11, io base 0x0000eec0
Apr 12 20:30:32 ubuntu kernel: [    4.941689] usb usb2: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.941786] hub 2-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.941858] hub 2-0:1.0: 2 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.941979] uhci_hcd 0000:00:10.1: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    4.942054] uhci_hcd 0000:00:10.1: sharing IRQ 11 with 0000:00:0f.1
Apr 12 20:30:32 ubuntu kernel: [    4.942120] uhci_hcd 0000:00:10.1: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    4.942197] uhci_hcd 0000:00:10.1: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    4.942267] uhci_hcd 0000:00:10.1: UHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.942371] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Apr 12 20:30:32 ubuntu kernel: [    4.942465] uhci_hcd 0000:00:10.1: irq 11, io base 0x0000ef00
Apr 12 20:30:32 ubuntu kernel: [    4.942639] usb usb3: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.942735] hub 3-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.942845] hub 3-0:1.0: 2 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.942960] PCI: setting IRQ 10 as level-triggered
Apr 12 20:30:32 ubuntu kernel: [    4.942966] uhci_hcd 0000:00:10.2: found PCI INT B -> IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    4.943036] uhci_hcd 0000:00:10.2: sharing IRQ 10 with 0000:00:0d.0
Apr 12 20:30:32 ubuntu kernel: [    4.943101] uhci_hcd 0000:00:10.2: sharing IRQ 10 with 0000:00:0f.0
Apr 12 20:30:32 ubuntu kernel: [    4.943173] uhci_hcd 0000:00:10.2: sharing IRQ 10 with 0000:00:10.3
Apr 12 20:30:32 ubuntu kernel: [    4.943253] uhci_hcd 0000:00:10.2: UHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.943359] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Apr 12 20:30:32 ubuntu kernel: [    4.943455] uhci_hcd 0000:00:10.2: irq 10, io base 0x0000ef20
Apr 12 20:30:32 ubuntu kernel: [    4.943639] usb usb4: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.943735] hub 4-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.943805] hub 4-0:1.0: 2 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.943921] uhci_hcd 0000:00:10.3: found PCI INT B -> IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    4.943992] uhci_hcd 0000:00:10.3: sharing IRQ 10 with 0000:00:0d.0
Apr 12 20:30:32 ubuntu kernel: [    4.944057] uhci_hcd 0000:00:10.3: sharing IRQ 10 with 0000:00:0f.0
Apr 12 20:30:32 ubuntu kernel: [    4.944127] uhci_hcd 0000:00:10.3: sharing IRQ 10 with 0000:00:10.2
Apr 12 20:30:32 ubuntu kernel: [    4.944208] uhci_hcd 0000:00:10.3: UHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.944327] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
Apr 12 20:30:32 ubuntu kernel: [    4.944421] uhci_hcd 0000:00:10.3: irq 10, io base 0x0000ef40
Apr 12 20:30:32 ubuntu kernel: [    4.944590] usb usb5: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.944686] hub 5-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.944756] hub 5-0:1.0: 2 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.944940] PNP: No PS/2 controller found. Probing ports directly.
Apr 12 20:30:32 ubuntu kernel: [    4.991368] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 12 20:30:32 ubuntu kernel: [    4.991436] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 12 20:30:32 ubuntu kernel: [    4.991666] mice: PS/2 mouse device common for all mice
Apr 12 20:30:32 ubuntu kernel: [    4.991880] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Apr 12 20:30:32 ubuntu kernel: [    4.991973] rtc0: alarms up to one day, 114 bytes nvram
Apr 12 20:30:32 ubuntu kernel: [    4.992185] device-mapper: uevent: version 1.0.3
Apr 12 20:30:32 ubuntu kernel: [    4.992396] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Apr 12 20:30:32 ubuntu kernel: [    4.992538] device-mapper: multipath: version 1.1.0 loaded
Apr 12 20:30:32 ubuntu kernel: [    4.992602] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 12 20:30:32 ubuntu kernel: [    4.992812] EISA: Probing bus 0 at eisa.0
Apr 12 20:30:32 ubuntu kernel: [    4.992881] Cannot allocate resource for EISA slot 1
Apr 12 20:30:32 ubuntu kernel: [    4.992969] EISA: Detected 0 cards.
Apr 12 20:30:32 ubuntu kernel: [    4.993089] cpuidle: using governor ladder
Apr 12 20:30:32 ubuntu kernel: [    4.993151] cpuidle: using governor menu
Apr 12 20:30:32 ubuntu kernel: [    4.993772] TCP cubic registered
Apr 12 20:30:32 ubuntu kernel: [    4.993995] NET: Registered protocol family 10
Apr 12 20:30:32 ubuntu kernel: [    4.994619] lo: Disabled Privacy Extensions
Apr 12 20:30:32 ubuntu kernel: [    4.995104] NET: Registered protocol family 17
Apr 12 20:30:32 ubuntu kernel: [    4.995218] Using IPI No-Shortcut mode
Apr 12 20:30:32 ubuntu kernel: [    4.995400] PM: Resume from disk failed.
Apr 12 20:30:32 ubuntu kernel: [    4.995418] registered taskstats version 1
Apr 12 20:30:32 ubuntu kernel: [    4.995798]   Magic number: 6:935:497
Apr 12 20:30:32 ubuntu kernel: [    4.995954] rtc_cmos 00:04: setting system clock to 2010-04-12 20:29:47 UTC (1271104187)
Apr 12 20:30:32 ubuntu kernel: [    4.996029] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 12 20:30:32 ubuntu kernel: [    4.996091] EDD information not available.
Apr 12 20:30:32 ubuntu kernel: [    5.257573] isapnp: No Plug & Play device found
Apr 12 20:30:32 ubuntu kernel: [    5.341094] Freeing initrd memory: 9037k freed
Apr 12 20:30:32 ubuntu kernel: [    5.352797] Freeing unused kernel memory: 656k freed
Apr 12 20:30:32 ubuntu kernel: [    5.353799] Write protecting the kernel text: 4672k
Apr 12 20:30:32 ubuntu kernel: [    5.353891] Write protecting the kernel read-only data: 1836k
Apr 12 20:30:32 ubuntu kernel: [    5.394464] udev: starting version 151
Apr 12 20:30:32 ubuntu kernel: [    5.558798] pata_via 0000:00:0f.1: version 0.3.4
Apr 12 20:30:32 ubuntu kernel: [    5.558816] pata_via 0000:00:0f.1: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    5.558899] pata_via 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    5.558965] pata_via 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    5.559661] pata_via 0000:00:0f.1: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    5.559729] pata_via 0000:00:0f.1: VIA VLink IRQ fixup, from 255 to 11
Apr 12 20:30:32 ubuntu kernel: [    5.577055] scsi0 : pata_via
Apr 12 20:30:32 ubuntu kernel: [    5.584016] scsi1 : pata_via
Apr 12 20:30:32 ubuntu kernel: [    5.584239] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Apr 12 20:30:32 ubuntu kernel: [    5.584305] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Apr 12 20:30:32 ubuntu kernel: [    5.584423] sata_via 0000:00:0f.0: version 2.4
Apr 12 20:30:32 ubuntu kernel: [    5.584444] sata_via 0000:00:0f.0: found PCI INT B -> IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    5.584517] sata_via 0000:00:0f.0: sharing IRQ 10 with 0000:00:0d.0
Apr 12 20:30:32 ubuntu kernel: [    5.584590] sata_via 0000:00:0f.0: sharing IRQ 10 with 0000:00:10.2
Apr 12 20:30:32 ubuntu kernel: [    5.584655] sata_via 0000:00:0f.0: sharing IRQ 10 with 0000:00:10.3
Apr 12 20:30:32 ubuntu kernel: [    5.584774] sata_via 0000:00:0f.0: routed to hard irq line 10
Apr 12 20:30:32 ubuntu kernel: [    5.590029] scsi2 : sata_via
Apr 12 20:30:32 ubuntu kernel: [    5.595211] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Apr 12 20:30:32 ubuntu kernel: [    5.595462] Linux agpgart interface v0.103
Apr 12 20:30:32 ubuntu kernel: [    5.595544] scsi3 : sata_via
Apr 12 20:30:32 ubuntu kernel: [    5.595680] ata3: SATA max UDMA/133 cmd 0xefe0 ctl 0xefac bmdma 0xef90 irq 10
Apr 12 20:30:32 ubuntu kernel: [    5.595746] ata4: SATA max UDMA/133 cmd 0xefa0 ctl 0xefa8 bmdma 0xef98 irq 10
Apr 12 20:30:32 ubuntu kernel: [    5.595978] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Apr 12 20:30:32 ubuntu kernel: [    5.596062] r8169 0000:00:0d.0: found PCI INT A -> IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    5.596135] r8169 0000:00:0d.0: sharing IRQ 10 with 0000:00:0f.0
Apr 12 20:30:32 ubuntu kernel: [    5.596206] r8169 0000:00:0d.0: sharing IRQ 10 with 0000:00:10.2
Apr 12 20:30:32 ubuntu kernel: [    5.596270] r8169 0000:00:0d.0: sharing IRQ 10 with 0000:00:10.3
Apr 12 20:30:32 ubuntu kernel: [    5.596372] r8169 0000:00:0d.0: no PCI Express capability
Apr 12 20:30:32 ubuntu kernel: [    5.597224] eth0: RTL8110s at 0xf8088000, 00:1e:2a:49:72:40, XID 04000000 IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    5.600574] via-rhine 0000:00:12.0: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    5.600653] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:0f.1
Apr 12 20:30:32 ubuntu kernel: [    5.600718] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    5.600784] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    5.601789] eth1: VIA Rhine II at 0xdff00000, 00:0e:a6:bd:8d:ae, IRQ 11.
Apr 12 20:30:32 ubuntu kernel: [    5.602529] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
Apr 12 20:30:32 ubuntu kernel: [    5.606817] usb 2-1: new low speed USB device using uhci_hcd and address 2
Apr 12 20:30:32 ubuntu kernel: [    5.725656] [drm] Initialized drm 1.1.0 20060810
Apr 12 20:30:32 ubuntu kernel: [    5.786734] usb 2-1: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    5.808774] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Apr 12 20:30:32 ubuntu kernel: [    5.820208] usbcore: registered new interface driver hiddev
Apr 12 20:30:32 ubuntu kernel: [    5.836096] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input1
Apr 12 20:30:32 ubuntu kernel: [    5.836420] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:10.0-1/input0
Apr 12 20:30:32 ubuntu kernel: [    5.877771] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/input/input2
Apr 12 20:30:32 ubuntu kernel: [    5.878357] generic-usb 0003:046D:C312.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:10.0-1/input1
Apr 12 20:30:32 ubuntu kernel: [    5.878478] usbcore: registered new interface driver usbhid
Apr 12 20:30:32 ubuntu kernel: [    5.878665] usbhid: v2.6:USB HID core driver
Apr 12 20:30:32 ubuntu kernel: [    5.935091] ata1.00: HPA unlocked: 312579695 -> 312581808, native 312581808
Apr 12 20:30:32 ubuntu kernel: [    5.935161] ata1.00: ATA-7: ST3160812A, 3.AAD, max UDMA/100
Apr 12 20:30:32 ubuntu kernel: [    5.935225] ata1.00: 312581808 sectors, multi 16: LBA48 
Apr 12 20:30:32 ubuntu kernel: [    5.977652] ata1.00: configured for UDMA/100
Apr 12 20:30:32 ubuntu kernel: [    5.977870] scsi 0:0:0:0: Direct-Access     ATA      ST3160812A       3.AA PQ: 0 ANSI: 5
Apr 12 20:30:32 ubuntu kernel: [    5.978169] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 12 20:30:32 ubuntu kernel: [    5.978818] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Apr 12 20:30:32 ubuntu kernel: [    5.978959] sd 0:0:0:0: [sda] Write Protect is off
Apr 12 20:30:32 ubuntu kernel: [    5.979022] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 12 20:30:32 ubuntu kernel: [    5.979056] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 20:30:32 ubuntu kernel: [    5.979340]  sda: sda1 sda2 sda3 <
Apr 12 20:30:32 ubuntu kernel: [    6.034778] usb 3-1: new low speed USB device using uhci_hcd and address 2
Apr 12 20:30:32 ubuntu kernel: [    6.041006]  sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
Apr 12 20:30:32 ubuntu kernel: [    6.115397]  sda2: <bsd:bad subpartition - ignored
Apr 12 20:30:32 ubuntu kernel: [    6.115508] bad subpartition - ignored
Apr 12 20:30:32 ubuntu kernel: [    6.115567] bad subpartition - ignored
Apr 12 20:30:32 ubuntu kernel: [    6.115627] bad subpartition - ignored
Apr 12 20:30:32 ubuntu kernel: [    6.115687]  >
Apr 12 20:30:32 ubuntu kernel: [    6.117073] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 12 20:30:32 ubuntu kernel: [    6.139113] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A106, max UDMA/33
Apr 12 20:30:32 ubuntu kernel: [    6.155009] ata2.01: configured for UDMA/33
Apr 12 20:30:32 ubuntu kernel: [    6.160544] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A106 PQ: 0 ANSI: 5
Apr 12 20:30:32 ubuntu kernel: [    6.166349] sr0: scsi3-mmc drive: 78x/78x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 12 20:30:32 ubuntu kernel: [    6.166428] Uniform CD-ROM driver Revision: 3.20
Apr 12 20:30:32 ubuntu kernel: [    6.166882] sr 1:0:1:0: Attached scsi CD-ROM sr0
Apr 12 20:30:32 ubuntu kernel: [    6.167076] sr 1:0:1:0: Attached scsi generic sg1 type 5
Apr 12 20:30:32 ubuntu kernel: [    6.233663] usb 3-1: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    6.370774] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Apr 12 20:30:32 ubuntu kernel: [    6.397122] agpgart: Detected VIA PT800 chipset
Apr 12 20:30:32 ubuntu kernel: [    6.426149] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
Apr 12 20:30:32 ubuntu kernel: [    6.464702] [drm] nouveau 0000:01:00.0: Detected an NV30 generation card (0x034600b1)
Apr 12 20:30:32 ubuntu kernel: [    6.464811] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
Apr 12 20:30:32 ubuntu kernel: [    6.468742] vga16fb: initializing
Apr 12 20:30:32 ubuntu kernel: [    6.468750] vga16fb: mapped to 0xc00a0000
Apr 12 20:30:32 ubuntu kernel: [    6.468998] fb0: VGA16 VGA frame buffer device
Apr 12 20:30:32 ubuntu kernel: [    6.613029] Console: switching to colour frame buffer device 80x30
Apr 12 20:30:32 ubuntu kernel: [    6.640701] generic-usb 0003:051D:0002.0003: hiddev97,hidraw2: USB HID v1.10 Device [APC Back-UPS ES 500 FW:2.e2.D USB FW:e2] on usb-0000:00:10.1-1/input0
Apr 12 20:30:32 ubuntu kernel: [    6.878787] usb 3-2: new low speed USB device using uhci_hcd and address 3
Apr 12 20:30:32 ubuntu kernel: [    7.054679] usb 3-2: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    7.070901] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input3
Apr 12 20:30:32 ubuntu kernel: [    7.081755] generic-usb 0003:046D:C018.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:10.1-2/input0
Apr 12 20:30:32 ubuntu kernel: [    7.670865] xor: automatically using best checksumming function: pIII_sse
Apr 12 20:30:32 ubuntu kernel: [    7.690763]    pIII_sse  :  3205.000 MB/sec
Apr 12 20:30:32 ubuntu kernel: [    7.690767] xor: using function: pIII_sse (3205.000 MB/sec)
Apr 12 20:30:32 ubuntu kernel: [    7.719150] device-mapper: dm-raid45: initialized v0.2594b
Apr 12 20:30:32 ubuntu kernel: [    8.304799] EXT4-fs (sda10): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    8.441571] EXT4-fs (sda11): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    8.673517] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    8.807663] EXT4-fs (sda7): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    8.970423] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    9.106669] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [   10.635451] ISO 9660 Extensions: Microsoft Joliet Level 3
Apr 12 20:30:32 ubuntu kernel: [   10.673322] ISO 9660 Extensions: RRIP_1991A
Apr 12 20:30:32 ubuntu kernel: [   10.853746] aufs 2-standalone.tree-20091207
Apr 12 20:30:32 ubuntu kernel: [   11.030823] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Apr 12 20:30:32 ubuntu kernel: [   49.094316] Adding 514040k swap on /dev/sda5.  Priority:-1 extents:1 across:514040k 
Apr 12 20:30:32 ubuntu kernel: [   50.485993] udev: starting version 151
Apr 12 20:30:35 ubuntu kernel: [   53.007269] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Successfully dropped root privileges.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: avahi-daemon 0.6.25 starting up.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Successfully called chroot().
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Successfully dropped remaining capabilities.
Apr 12 20:30:36 ubuntu avahi-daemon[1341]: chroot.c: open() failed: No such file or directory
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Failed to open /etc/resolv.conf: Invalid argument
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: No service file found in /etc/avahi/services.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Network interface enumeration completed.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2162424758.
Apr 12 20:30:36 ubuntu NetworkManager: <info>  starting...
Apr 12 20:30:36 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Apr 12 20:30:38 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0d.0/net/eth0, iface: eth0)
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0d.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth1, iface: eth1)
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Apr 12 20:30:38 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 12 20:30:39 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 12 20:30:39 ubuntu NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Apr 12 20:30:39 ubuntu NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Apr 12 20:30:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: (138292560) ... get_connections.
Apr 12 20:30:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: (138292560) ... get_connections (managed=false): return empty list.
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin AnyData
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Generic
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Gobi
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Option High-Speed
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Huawei
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Longcheer
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Ericsson MBM
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin MotoC
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Nokia
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Novatel
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Option
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Sierra
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin ZTE
Apr 12 20:30:39 ubuntu kernel: [   57.427684] CA0106 0000:00:0a.0: found PCI INT A -> IRQ 5
Apr 12 20:30:39 ubuntu kernel: [   57.427713] CA0106 0000:00:0a.0: sharing IRQ 5 with 0000:00:10.4
Apr 12 20:30:39 ubuntu kernel: [   57.427721] CA0106 0000:00:0a.0: sharing IRQ 5 with 0000:00:11.5
Apr 12 20:30:39 ubuntu kernel: [   57.427726] CA0106 0000:00:0a.0: sharing IRQ 5 with 0000:00:11.6
Apr 12 20:30:39 ubuntu kernel: [   57.427758] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
Apr 12 20:30:39 ubuntu kernel: [   57.491946] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
Apr 12 20:30:39 ubuntu kernel: [   57.491959] VIA 82xx Modem 0000:00:11.6: found PCI INT C -> IRQ 5
Apr 12 20:30:39 ubuntu kernel: [   57.491971] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:0a.0
Apr 12 20:30:39 ubuntu kernel: [   57.491988] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:10.4
Apr 12 20:30:39 ubuntu kernel: [   57.491996] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:11.5
Apr 12 20:30:39 ubuntu kernel: [   57.492008] VIA 82xx Modem 0000:00:11.6: VIA VLink IRQ fixup, from 0 to 5
Apr 12 20:30:40 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): now managed
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): preparing device.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 12 20:30:40 ubuntu kernel: [   57.609724] r8169: eth0: link down
Apr 12 20:30:40 ubuntu kernel: [   57.609932] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 12 20:30:40 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:0d.0/net/eth0
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): carrier is OFF
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'via-rhine')
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): now managed
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): bringing up device.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): preparing device.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Apr 12 20:30:40 ubuntu kernel: [   57.617768] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 12 20:30:40 ubuntu NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:12.0/net/eth1
Apr 12 20:30:40 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth1, iface: eth1)
Apr 12 20:30:40 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): carrier now ON (device state 2)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  modem-manager is now available
Apr 12 20:30:40 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  dhclient started with pid 1480
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 12 20:30:40 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 12 20:30:40 ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 12 20:30:40 ubuntu dhclient: All rights reserved.
Apr 12 20:30:40 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 12 20:30:40 ubuntu dhclient: 
Apr 12 20:30:40 ubuntu kernel: [   58.242657] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
Apr 12 20:30:41 ubuntu kernel: [   58.746876] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
Apr 12 20:30:41 ubuntu kernel: [   58.747133] VIA 82xx Audio 0000:00:11.5: enabling device (0000 -> 0001)
Apr 12 20:30:41 ubuntu kernel: [   58.747145] VIA 82xx Audio 0000:00:11.5: found PCI INT C -> IRQ 5
Apr 12 20:30:41 ubuntu kernel: [   58.747156] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:0a.0
Apr 12 20:30:41 ubuntu kernel: [   58.747176] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:10.4
Apr 12 20:30:41 ubuntu kernel: [   58.747184] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
Apr 12 20:30:41 ubuntu kernel: [   58.747194] VIA 82xx Audio 0000:00:11.5: VIA VLink IRQ fixup, from 0 to 5
Apr 12 20:30:41 ubuntu kernel: [   58.747342] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
Apr 12 20:30:41 ubuntu NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
Apr 12 20:30:41 ubuntu dhclient: Listening on LPF/eth1/00:0e:a6:bd:8d:ae
Apr 12 20:30:41 ubuntu dhclient: Sending on   LPF/eth1/00:0e:a6:bd:8d:ae
Apr 12 20:30:41 ubuntu dhclient: Sending on   Socket/fallback
Apr 12 20:30:41 ubuntu avahi-daemon[1335]: Registering new address record for fe80::20e:a6ff:febd:8dae on eth1.*.
Apr 12 20:30:41 ubuntu kernel: [   59.261873] codec_read: codec 0 is not valid [0x107e5370]
Apr 12 20:30:41 ubuntu kernel: [   59.268896] codec_read: codec 0 is not valid [0x107e5370]
Apr 12 20:30:41 ubuntu kernel: [   59.276143] codec_read: codec 0 is not valid [0x107e5370]
Apr 12 20:30:41 ubuntu kernel: [   59.283568] codec_read: codec 0 is not valid [0x107e5370]
Apr 12 20:30:45 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 12 20:30:45 ubuntu dhclient: DHCPOFFER of 192.168.1.112 from 192.168.1.1
Apr 12 20:30:45 ubuntu dhclient: DHCPREQUEST of 192.168.1.112 on eth1 to 255.255.255.255 port 67
Apr 12 20:30:45 ubuntu dhclient: DHCPACK of 192.168.1.112 from 192.168.1.1
Apr 12 20:30:45 ubuntu NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Apr 12 20:30:45 ubuntu NetworkManager: <info>    address 192.168.1.112
Apr 12 20:30:45 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Apr 12 20:30:45 ubuntu NetworkManager: <info>    gateway 192.168.1.1
Apr 12 20:30:45 ubuntu NetworkManager: <info>    hostname 'ubuntu'
Apr 12 20:30:45 ubuntu NetworkManager: <info>    nameserver '192.168.1.1'
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Apr 12 20:30:45 ubuntu avahi-daemon[1335]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.112.
Apr 12 20:30:45 ubuntu dhclient: bound to 192.168.1.112 -- renewal in 35826 seconds.
Apr 12 20:30:45 ubuntu avahi-daemon[1335]: New relevant interface eth1.IPv4 for mDNS.
Apr 12 20:30:45 ubuntu avahi-daemon[1335]: Registering new address record for 192.168.1.112 on eth1.IPv4.
Apr 12 20:30:46 ubuntu cron[1687]: (CRON) INFO (pidfile fd = 3)
Apr 12 20:30:46 ubuntu acpid: starting up with netlink and the input layer
Apr 12 20:30:46 ubuntu cron[1722]: (CRON) STARTUP (fork ok)
Apr 12 20:30:46 ubuntu NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Apr 12 20:30:46 ubuntu NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
Apr 12 20:30:46 ubuntu NetworkManager: <info>  Activation (eth1) successful, device activated.
Apr 12 20:30:46 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Apr 12 20:30:46 ubuntu cron[1722]: (CRON) INFO (Running @reboot jobs)
Apr 12 20:30:46 ubuntu acpid: 39 rules loaded
Apr 12 20:30:46 ubuntu acpid: waiting for events: event logging is off
Apr 12 20:30:46 ubuntu acpid: client connected from 1497[0:0]
Apr 12 20:30:46 ubuntu acpid: 1 client rule loaded
Apr 12 20:30:48 ubuntu kernel: [   65.612273] [TTM] Zone  kernel: Available graphics memory: 436968 kiB.
Apr 12 20:30:48 ubuntu kernel: [   65.612279] [TTM] Zone highmem: Available graphics memory: 1030476 kiB.
Apr 12 20:30:48 ubuntu kernel: [   65.612302] [drm] nouveau 0000:01:00.0: 256 MiB VRAM
Apr 12 20:30:48 ubuntu kernel: [   65.612391] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Apr 12 20:30:48 ubuntu kernel: [   65.612409] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Apr 12 20:30:48 ubuntu kernel: [   65.612418] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 12 20:30:48 ubuntu kernel: [   65.612498] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 12 20:30:48 ubuntu kernel: [   65.612502] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
Apr 12 20:30:48 ubuntu kernel: [   65.612777] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
Apr 12 20:30:48 ubuntu kernel: [   65.613572] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
Apr 12 20:30:48 ubuntu kernel: [   65.613789] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 0
Apr 12 20:30:48 ubuntu kernel: [   65.614505] [TTM] Zone  kernel: Used memory at exit: 0 kiB.
Apr 12 20:30:48 ubuntu kernel: [   65.614513] [TTM] Zone highmem: Used memory at exit: 0 kiB.
Apr 12 20:30:48 ubuntu kernel: [   66.164839] lp: driver loaded but no devices found
Apr 12 20:30:48 ubuntu kernel: [   66.340891] ppdev: user-space parallel port driver
Apr 12 20:30:50 ubuntu udev-configure-printer: add /module/lp
Apr 12 20:30:50 ubuntu udev-configure-printer: Failed to get parent
Apr 12 20:30:50 ubuntu kernel: [   68.202618] eth1: no IPv6 routers present
Apr 13 00:30:53 ubuntu ntpdate[2182]: step time server 91.189.94.4 offset 14399.109129 sec
Apr 13 00:30:53 ubuntu console-kit-daemon[2184]: WARNING: The program /usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck didn't exit within 15 seconds; killing it
Apr 13 00:30:57 ubuntu console-kit-daemon[2184]: last message repeated 3 times
Apr 13 00:30:57 ubuntu init: plymouth-stop pre-start process (2511) terminated with status 1
Apr 13 00:31:04 ubuntu ubiquity[2608]: Ubiquity 2.2.15
Apr 13 00:31:11 ubuntu ubiquity[2608]: log-output -t ubiquity laptop-detect
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Sucessfully called chroot.
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Sucessfully dropped privileges.
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Sucessfully limited resources.
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Running.
Apr 13 00:31:21 ubuntu ubiquity[2608]: log-output -t ubiquity laptop-detect
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Watchdog thread running.
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Canary thread running.
Apr 13 00:31:22 ubuntu polkitd[2642]: started daemon version 0.96 using authority implementation `local' version `0.96'
Apr 13 00:31:28 ubuntu ubiquity[2608]: switched to page language
Apr 13 00:31:32 ubuntu ubiquity[2608]: switched to page language
Apr 13 00:31:39 ubuntu localechooser: info: Language = 'en'
Apr 13 00:31:39 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/language = 'en'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Apr 13 00:31:39 ubuntu localechooser: info: Default country = 'US'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/country = 'US'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 13 00:31:39 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Apr 13 00:31:42 ubuntu ubiquity[2608]: debconffilter_done: ubi-language (current: ubi-language)
Apr 13 00:31:42 ubuntu ubiquity[2608]: Step_before = stepLanguage
Apr 13 00:31:46 ubuntu clock-setup: Tue Apr 13 00:31:46 UTC 2010
Apr 13 00:31:46 ubuntu clock-setup: rdate: adjust local clock by 0.001576 seconds
Apr 13 00:31:47 ubuntu ubiquity[2608]: switched to page timezone
Apr 13 00:32:19 ubuntu localechooser: info: Locale has been preseeded to en_CA.UTF-8
Apr 13 00:32:19 ubuntu localechooser: info: Set localechooser/languagelist = 'en'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/country = 'CA'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/locale = 'en_CA.UTF-8'
Apr 13 00:32:19 ubuntu localechooser: info: Language = 'en'
Apr 13 00:32:19 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/language = 'en'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Apr 13 00:32:19 ubuntu localechooser: info: Default country = 'US'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/country = 'CA'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/locale = 'en_CA.UTF-8'
Apr 13 00:32:19 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_CA.UTF-8'
Apr 13 00:32:20 ubuntu kernel: [  158.975008] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Apr 13 00:32:20 ubuntu kernel: [  158.982938] SGI XFS Quota Management subsystem
Apr 13 00:32:20 ubuntu kernel: [  159.063605] JFS: nTxBlock = 8192, nTxLock = 65536
Apr 13 00:32:20 ubuntu kernel: [  159.175518] NTFS driver 2.1.29 [Flags: R/O MODULE].
Apr 13 00:32:20 ubuntu kernel: [  159.378952] QNX4 filesystem 0.2.3 registered.
Apr 13 00:32:21 ubuntu kernel: [  159.752969] Btrfs loaded
Apr 13 00:32:21 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Version 2010.3.6 external FUSE 28
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Cmdline options: ro
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Mount options: ro,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Ownership and permissions disabled, configuration type 1
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: mounted as ntfs-3g filesystem
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:21 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:21 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:21 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:21 ubuntu 20microsoft: debug: /dev/sda1 is a NTFS partition
Apr 13 00:32:22 ubuntu 20microsoft: result: /dev/sda1:Windows 7 (loader):Windows:chain
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:22 ubuntu ntfs-3g[3737]: Unmounting /dev/sda1 ()
Apr 13 00:32:22 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda10
Apr 13 00:32:22 ubuntu kernel: [  160.616538] EXT4-fs (sda10): mounted filesystem with ordered data mode
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:22 ubuntu 10freedos: debug: /dev/sda10 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:22 ubuntu 10qnx: debug: /dev/sda10 is not a QNX4 partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:22 ubuntu macosx-prober: debug: /dev/sda10 is not an HFS+ partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:22 ubuntu 20microsoft: debug: /dev/sda10 is not a MS partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:22 ubuntu 30utility: debug: /dev/sda10 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda11
Apr 13 00:32:22 ubuntu kernel: [  160.828507] EXT4-fs (sda11): mounted filesystem with ordered data mode
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:22 ubuntu 10freedos: debug: /dev/sda11 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:22 ubuntu 10qnx: debug: /dev/sda11 is not a QNX4 partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:22 ubuntu macosx-prober: debug: /dev/sda11 is not an HFS+ partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:22 ubuntu 20microsoft: debug: /dev/sda11 is not a MS partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:22 ubuntu 30utility: debug: /dev/sda11 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Apr 13 00:32:22 ubuntu kernel: [  161.032952] You didn't specify the type of your ufs filesystem
Apr 13 00:32:22 ubuntu kernel: [  161.032955] 
Apr 13 00:32:22 ubuntu kernel: [  161.032956] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Apr 13 00:32:22 ubuntu kernel: [  161.032959] 
Apr 13 00:32:22 ubuntu kernel: [  161.032960] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Apr 13 00:32:22 ubuntu kernel: [  161.033281] ufs_read_super: bad magic number
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
Apr 13 00:32:22 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Apr 13 00:32:22 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Apr 13 00:32:22 ubuntu kernel: [  161.226776] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:22 ubuntu 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:22 ubuntu 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:22 ubuntu macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:22 ubuntu 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:22 ubuntu 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu 90linux-distro: result: /dev/sda6:openSUSE 11.2 (i586):SuSE:linux
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:23 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda7
Apr 13 00:32:23 ubuntu kernel: [  161.527216] EXT4-fs (sda7): mounted filesystem with ordered data mode
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:23 ubuntu 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:23 ubuntu 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:23 ubuntu macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:23 ubuntu 20microsoft: debug: /dev/sda7 is not a MS partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:23 ubuntu 30utility: debug: /dev/sda7 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:32:23 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda8
Apr 13 00:32:23 ubuntu kernel: [  161.731596] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:23 ubuntu 10freedos: debug: /dev/sda8 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:23 ubuntu 10qnx: debug: /dev/sda8 is not a QNX4 partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:23 ubuntu macosx-prober: debug: /dev/sda8 is not an HFS+ partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:23 ubuntu 20microsoft: debug: /dev/sda8 is not a MS partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:23 ubuntu 30utility: debug: /dev/sda8 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu 90linux-distro: result: /dev/sda8:Fedora release 12 (Constantine):Fedora:linux
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:23 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda9
Apr 13 00:32:23 ubuntu kernel: [  162.042443] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:23 ubuntu 10freedos: debug: /dev/sda9 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:23 ubuntu 10qnx: debug: /dev/sda9 is not a QNX4 partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:23 ubuntu macosx-prober: debug: /dev/sda9 is not an HFS+ partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:23 ubuntu 20microsoft: debug: /dev/sda9 is not a MS partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:23 ubuntu 30utility: debug: /dev/sda9 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:32:23 ubuntu ubiquity[2608]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Apr 13 00:32:23 ubuntu ubiquity[2608]: Step_before = stepLocation
Apr 13 00:32:24 ubuntu ubiquity[2608]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Apr 13 00:32:24 ubuntu ubiquity[2608]: switched to page console_setup
Apr 13 00:32:48 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Apr 13 00:32:48 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Apr 13 00:32:48 ubuntu ubiquity[2608]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Apr 13 00:32:48 ubuntu ubiquity[2608]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Apr 13 00:32:48 ubuntu ubiquity[2608]: Step_before = stepKeyboardConf
Apr 13 00:32:48 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: switched to page partman
Apr 13 00:33:04 ubuntu ubiquity[2608]: switched to page partman
Apr 13 00:33:09 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Apr 13 00:33:09 ubuntu ntfsresize: Device name        : /dev/sda1
Apr 13 00:33:09 ubuntu ntfsresize: NTFS volume version: 3.1
Apr 13 00:33:09 ubuntu ntfsresize: Cluster size       : 4096 bytes
Apr 13 00:33:09 ubuntu ntfsresize: Current volume size: 35031433728 bytes (35032 MB)
Apr 13 00:33:09 ubuntu ntfsresize: Current device size: 35031435264 bytes (35032 MB)
Apr 13 00:33:09 ubuntu ntfsresize: Checking filesystem consistency ...
Apr 13 00:33:09 ubuntu ntfsresize: Accounting clusters ...
Apr 13 00:33:09 ubuntu ntfsresize: Space in use       : 11357 MB (32.4%)
Apr 13 00:33:09 ubuntu ntfsresize: Collecting resizing constraints ...
Apr 13 00:33:09 ubuntu ntfsresize: You might resize at 11356598272 bytes or 11357 MB (freeing 23675 MB).
Apr 13 00:33:09 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Apr 13 00:33:10 ubuntu ubiquity[2608]: switched to page partman
Apr 13 00:33:46 ubuntu ubiquity[2608]: last message repeated 3 times
Apr 13 00:33:46 ubuntu ubiquity[2608]: switched to page partman
Apr 13 00:34:25 ubuntu ubiquity[2608]: debconffilter_done: ubi-partman (current: ubi-partman)
Apr 13 00:34:25 ubuntu ubiquity[2608]: Step_before = stepPartAdvanced
Apr 13 00:34:25 ubuntu ubiquity[2608]: switched to page usersetup
Apr 13 00:34:57 ubuntu ubiquity[2608]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Apr 13 00:34:57 ubuntu ubiquity[2608]: Step_before = stepUserInfo
Apr 13 00:34:57 ubuntu ubiquity[2608]: filtering out /dev/sda5 as it is to be formatted.
Apr 13 00:34:57 ubuntu ubiquity[2608]: filtering out /dev/sda10 as it is to be formatted.
Apr 13 00:34:57 ubuntu ubiquity[2608]: filtering out /dev/sda11 as it is to be formatted.
Apr 13 00:34:57 ubuntu migration-assistant: info: setting ostype from: '/dev/sda1:Windows 7 (loader):Windows:chain'
Apr 13 00:34:57 ubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Version 2010.3.6 external FUSE 28
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Mounted /dev/sda1 (Read-Write, label "", NTFS 3.1)
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Cmdline options: rw,umask=0022,nls=utf8
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096,default_permissions
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Global ownership and permissions enforced, configuration type 1
profilesdir: /mnt/migrationassistant/Users
profilesdir: /mnt/migrationassistant/Users
Apr 13 00:34:59 ubuntu ntfs-3g[9599]: Unmounting /dev/sda1 ()
Apr 13 00:34:59 ubuntu migration-assistant: info: setting ostype from: '/dev/sda6:openSUSE 11.2 (i586):SuSE:linux'
Apr 13 00:34:59 ubuntu migration-assistant: info: got ostype of: 'linux', mountpoint is: '/mnt/migrationassistant'
Apr 13 00:34:59 ubuntu kernel: [  317.572043] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 13 00:34:59 ubuntu kernel: [  317.788885] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:34:59 ubuntu migration-assistant: info: setting ostype from: '/dev/sda8:Fedora release 12 (Constantine):Fedora:linux'
Apr 13 00:34:59 ubuntu migration-assistant: info: got ostype of: 'linux', mountpoint is: '/mnt/migrationassistant'
Apr 13 00:34:59 ubuntu kernel: [  318.284626] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 13 00:35:00 ubuntu kernel: [  318.454185] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:35:00 ubuntu ubiquity[2608]: switched to page migrationassistant
Apr 13 00:35:34 ubuntu ubiquity[2608]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Apr 13 00:35:34 ubuntu ubiquity[2608]: Step_before = stepMigrationAssistant
Apr 13 00:35:35 ubuntu ubiquity[2608]: switched to page summary
Apr 13 00:36:12 ubuntu ubiquity[2608]: debconffilter_done: ubi-summary (current: ubi-summary)
Apr 13 00:36:12 ubuntu ubiquity[2608]: Step_before = stepReady
Apr 13 00:36:12 ubuntu ubiquity[2608]: progress_loop()
Apr 13 00:36:20 ubuntu partman: mke2fs 1.41.11 (14-Mar-2010)
Apr 13 00:36:26 ubuntu partman: mke2fs 1.41.11 (14-Mar-2010)
Apr 13 00:36:32 ubuntu kernel: [  410.597422] EXT4-fs (sda10): mounted filesystem with ordered data mode
Apr 13 00:36:32 ubuntu kernel: [  410.676365] EXT4-fs (sda11): mounted filesystem with ordered data mode
Apr 13 00:36:33 ubuntu ubiquity[2608]: debconffilter_done: ubiquity.components.partman_commit (current: None)
Apr 13 00:36:33 ubuntu python: keeping packages due to preseeding: icedtea6-plugin openoffice.org
Apr 13 00:36:33 ubuntu python: keeping language packs for: en
Apr 13 00:42:49 ubuntu ubiquity: umount: /target/cdrom: not found
Apr 13 00:42:49 ubuntu ubiquity: 
Apr 13 00:42:49 ubuntu python: log-output -t ubiquity umount /target/cdrom
Apr 13 00:42:49 ubuntu python: log-output -t ubiquity mount --bind /cdrom /target/cdrom
Apr 13 00:42:53 ubuntu ubiquity: /usr/lib/ubiquity/apt-setup/generators/01setup: 7: 
Apr 13 00:42:53 ubuntu ubiquity: cannot open /target/etc/apt/sources.list: No such file
Apr 13 00:42:53 ubuntu ubiquity: 
Apr 13 00:42:56 ubuntu in-target: Reading package lists...
Apr 13 00:42:56 ubuntu in-target: 
Apr 13 00:42:57 ubuntu apt-setup: Using CD-ROM mount point /cdrom/
Apr 13 00:42:57 ubuntu apt-setup: Identifying.. 
Apr 13 00:42:57 ubuntu apt-setup: [23edb90d1038bf5e9143793ff3e4a7d0-2]
Apr 13 00:42:57 ubuntu apt-setup: Scanning disc for index files..
Apr 13 00:42:57 ubuntu apt-setup: Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Apr 13 00:42:57 ubuntu apt-setup: Found label 'Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)'
Apr 13 00:42:57 ubuntu apt-setup: This disc is called: 
Apr 13 00:42:57 ubuntu apt-setup: 'Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)'
Apr 13 00:42:57 ubuntu apt-setup: Copying package lists...
Apr 13 00:42:57 ubuntu apt-setup: gpgv: 
Apr 13 00:42:57 ubuntu apt-setup: Signature made Tue 06 Apr 2010 08:23:09 PM UTC using DSA key ID FBB75451
Apr 13 00:42:57 ubuntu apt-setup: gpgv: 
Apr 13 00:42:57 ubuntu apt-setup: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Apr 13 00:42:57 ubuntu apt-setup: 
Apr 13 00:42:57 ubuntu apt-setup: #015Reading Package Indexes... 0%#015#015Reading Package Indexes... 2%#015
Apr 13 00:42:57 ubuntu apt-setup: #015Reading Package Indexes... Done#015
Apr 13 00:42:57 ubuntu apt-setup: Writing new source list
Apr 13 00:42:57 ubuntu apt-setup: Source list entries for this disc are:
Apr 13 00:42:57 ubuntu apt-setup: deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)]/ lucid main restricted
Apr 13 00:42:57 ubuntu apt-setup: Repeat this process for the rest of the CDs in your set.
Apr 13 00:42:57 ubuntu apt-setup: W: Skipping nonexistent file /cdrom/dists/lucid/main/binary-i386/Packages
Apr 13 00:42:57 ubuntu apt-setup: W: Skipping nonexistent file /cdrom/dists/lucid/restricted/binary-i386/Packages
Apr 13 00:42:59 ubuntu in-target: Ign cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)/ lucid/main Translation-en_CA
Apr 13 00:42:59 ubuntu in-target: Ign cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)/ lucid/restricted Translation-en_CA
Apr 13 00:42:59 ubuntu in-target: Reading package lists...
Apr 13 00:42:59 ubuntu in-target: 
Apr 13 00:43:00 ubuntu choose-mirror[11264]: INFO: base system installable from CD; skipping mirror check
Apr 13 00:43:00 ubuntu choose-mirror[11264]: INFO: falling back to codename lucid
Apr 13 00:43:02 ubuntu in-target: Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg [189B]
Apr 13 00:43:02 ubuntu in-target: Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA [10.3kB]
Apr 13 00:43:02 ubuntu in-target: Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA [425B]
Apr 13 00:43:02 ubuntu in-target: Get:4 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA [663B]
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release [57.2kB]
Apr 13 00:43:02 ubuntu in-target: Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release
Apr 13 00:43:03 ubuntu in-target: Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages [1,379kB]
Apr 13 00:43:06 ubuntu in-target: Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages [6,211B]
Apr 13 00:43:06 ubuntu in-target: Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources [652kB]
Apr 13 00:43:07 ubuntu in-target: Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources [3,774B]
Apr 13 00:43:07 ubuntu in-target: Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages [5,477kB]
Apr 13 00:43:18 ubuntu in-target: Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources [3,178kB]
Apr 13 00:43:24 ubuntu in-target: Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages [179kB]
Apr 13 00:43:24 ubuntu in-target: Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources [117kB]
Apr 13 00:43:25 ubuntu in-target: Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages [14B]
Apr 13 00:43:25 ubuntu in-target: Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages [14B]
Apr 13 00:43:25 ubuntu in-target: Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources [14B]
Apr 13 00:43:25 ubuntu in-target: Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources [14B]
Apr 13 00:43:25 ubuntu in-target: Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages [14B]
Apr 13 00:43:25 ubuntu in-target: Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources [14B]
Apr 13 00:43:25 ubuntu in-target: Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages [14B]
Apr 13 00:43:25 ubuntu in-target: Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources [14B]
Apr 13 00:43:29 ubuntu in-target: Fetched 11.1MB in 28s (395kB/s)
Apr 13 00:43:29 ubuntu in-target: Reading package lists...
Apr 13 00:43:33 ubuntu in-target: 
Apr 13 00:43:34 ubuntu in-target: Reading package lists...
Apr 13 00:43:34 ubuntu in-target: 
Apr 13 00:43:36 ubuntu in-target: Reading package lists...
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Apr 13 00:43:38 ubuntu in-target: Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Apr 13 00:43:38 ubuntu in-target: Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Apr 13 00:43:38 ubuntu in-target: Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Apr 13 00:43:38 ubuntu in-target: Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Apr 13 00:43:38 ubuntu in-target: Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [14B]
Apr 13 00:43:38 ubuntu in-target: Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [14B]
Apr 13 00:43:38 ubuntu in-target: Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [14B]
Apr 13 00:43:38 ubuntu in-target: Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [14B]
Apr 13 00:43:38 ubuntu in-target: Fetched 56B in 0s (68B/s)
Apr 13 00:43:38 ubuntu in-target: Reading package lists...
Apr 13 00:43:39 ubuntu in-target: 
Apr 13 00:43:39 ubuntu localechooser: Generating locales...
Apr 13 00:43:39 ubuntu localechooser:   en_CA.UTF-8... 
Apr 13 00:43:42 ubuntu localechooser: done
Apr 13 00:43:42 ubuntu localechooser: Generation complete.
Apr 13 00:43:42 ubuntu localechooser: Generating locales...
Apr 13 00:43:42 ubuntu localechooser:   en_US.UTF-8... 
Apr 13 00:43:45 ubuntu localechooser: done
Apr 13 00:43:45 ubuntu localechooser: Generation complete.
Apr 13 00:43:46 ubuntu python: log-output -t ubiquity chroot /target fontconfig-voodoo --auto --force --quiet
Apr 13 00:43:47 ubuntu clock-setup: hwclock from util-linux-ng 2.17.2
Apr 13 00:43:47 ubuntu clock-setup: Using /dev interface to clock.
Apr 13 00:43:47 ubuntu clock-setup: Assuming hardware clock is kept in local time.
Apr 13 00:43:47 ubuntu clock-setup: Time elapsed since reference time has been 0.685476 seconds.
Apr 13 00:43:47 ubuntu clock-setup: Delaying further to reach the new time.
Apr 13 00:43:47 ubuntu clock-setup: Setting Hardware Clock to 20:43:47 = 1271119427 seconds since 1969
Apr 13 00:43:47 ubuntu clock-setup: ioctl(RTC_SET_TIME) was successful.
Apr 13 00:43:52 ubuntu user-setup: Shadow passwords are now on.
Apr 13 00:43:52 ubuntu user-setup: Adding user `tt888' ...
Apr 13 00:43:52 ubuntu user-setup: Adding new group `tt888' (1000) ...
Apr 13 00:43:52 ubuntu user-setup: Adding new user `tt888' (1000) with group `tt888' ...
Apr 13 00:43:53 ubuntu user-setup: Creating home directory `/home/tt888' ...
Apr 13 00:43:53 ubuntu user-setup: Copying files from `/etc/skel' ...
Apr 13 00:43:54 ubuntu user-setup: addgroup: 
Apr 13 00:43:54 ubuntu user-setup: The group `lpadmin' already exists as a system group. Exiting.
Apr 13 00:43:54 ubuntu user-setup: Adding group `sambashare' (GID 122) ...
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:54 ubuntu user-setup: Adding user `tt888' to group `adm' ...
Apr 13 00:43:54 ubuntu user-setup: Adding user tt888 to group adm
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:54 ubuntu user-setup: Adding user `tt888' to group `cdrom' ...
Apr 13 00:43:54 ubuntu user-setup: Adding user tt888 to group cdrom
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:54 ubuntu user-setup: Adding user `tt888' to group `dialout' ...
Apr 13 00:43:54 ubuntu user-setup: Adding user tt888 to group dialout
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:54 ubuntu user-setup: Adding user `tt888' to group `lpadmin' ...
Apr 13 00:43:54 ubuntu user-setup: Adding user tt888 to group lpadmin
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:55 ubuntu user-setup: Adding user `tt888' to group `plugdev' ...
Apr 13 00:43:55 ubuntu user-setup: Adding user tt888 to group plugdev
Apr 13 00:43:55 ubuntu user-setup: Done.
Apr 13 00:43:55 ubuntu user-setup: Adding user `tt888' to group `sambashare' ...
Apr 13 00:43:55 ubuntu user-setup: Adding user tt888 to group sambashare
Apr 13 00:43:55 ubuntu user-setup: Done.
Apr 13 00:43:55 ubuntu user-setup: addgroup: 
Apr 13 00:43:55 ubuntu user-setup: The group `admin' already exists as a system group. Exiting.
Apr 13 00:43:55 ubuntu user-setup: Adding user `tt888' to group `admin' ...
Apr 13 00:43:55 ubuntu user-setup: Adding user tt888 to group admin
Apr 13 00:43:55 ubuntu user-setup: Done.
Apr 13 00:43:57 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Version 2010.3.6 external FUSE 28
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Cmdline options: ro
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Mount options: ro,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Ownership and permissions disabled, configuration type 1
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: mounted as ntfs-3g filesystem
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:58 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:58 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:58 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:58 ubuntu 20microsoft: debug: /dev/sda1 is a NTFS partition
Apr 13 00:43:58 ubuntu 20microsoft: result: /dev/sda1:Windows 7 (loader):Windows:chain
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Unmounting /dev/sda1 ()
Apr 13 00:43:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda11
Apr 13 00:43:58 ubuntu 10freedos: debug: /dev/sda11 is not a FAT partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda11
Apr 13 00:43:58 ubuntu 10qnx: debug: /dev/sda11 is not a QNX4 partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda11
Apr 13 00:43:58 ubuntu macosx-prober: debug: /dev/sda11 is not an HFS+ partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda11
Apr 13 00:43:58 ubuntu 20microsoft: debug: /dev/sda11 is not a MS partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda11
Apr 13 00:43:58 ubuntu 30utility: debug: /dev/sda11 is not a FAT partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Apr 13 00:43:58 ubuntu kernel: [  857.227777] You didn't specify the type of your ufs filesystem
Apr 13 00:43:58 ubuntu kernel: [  857.227780] 
Apr 13 00:43:58 ubuntu kernel: [  857.227781] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Apr 13 00:43:58 ubuntu kernel: [  857.227783] 
Apr 13 00:43:58 ubuntu kernel: [  857.227784] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Apr 13 00:43:58 ubuntu kernel: [  857.228126] ufs_read_super: bad magic number
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
Apr 13 00:43:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Apr 13 00:43:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Apr 13 00:43:58 ubuntu kernel: [  857.347926] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:58 ubuntu 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:58 ubuntu 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:59 ubuntu macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:59 ubuntu 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:43:59 ubuntu 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu 90linux-distro: result: /dev/sda6:openSUSE 11.2 (i586):SuSE:linux
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:59 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda7
Apr 13 00:43:59 ubuntu kernel: [  857.598473] EXT4-fs (sda7): mounted filesystem with ordered data mode
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:59 ubuntu 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:59 ubuntu 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:59 ubuntu macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:59 ubuntu 20microsoft: debug: /dev/sda7 is not a MS partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:43:59 ubuntu 30utility: debug: /dev/sda7 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:43:59 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda8
Apr 13 00:43:59 ubuntu kernel: [  857.786193] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:59 ubuntu 10freedos: debug: /dev/sda8 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:59 ubuntu 10qnx: debug: /dev/sda8 is not a QNX4 partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:59 ubuntu macosx-prober: debug: /dev/sda8 is not an HFS+ partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:59 ubuntu 20microsoft: debug: /dev/sda8 is not a MS partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:43:59 ubuntu 30utility: debug: /dev/sda8 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu 90linux-distro: result: /dev/sda8:Fedora release 12 (Constantine):Fedora:linux
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:59 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda9
Apr 13 00:43:59 ubuntu kernel: [  858.080425] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:59 ubuntu 10freedos: debug: /dev/sda9 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:59 ubuntu 10qnx: debug: /dev/sda9 is not a QNX4 partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:59 ubuntu macosx-prober: debug: /dev/sda9 is not an HFS+ partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:59 ubuntu 20microsoft: debug: /dev/sda9 is not a MS partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:43:59 ubuntu 30utility: debug: /dev/sda9 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:43:59 ubuntu kernel: [  858.354390] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 13 00:44:00 ubuntu kernel: [  858.504685] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:44:00 ubuntu kernel: [  858.626247] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 13 00:44:00 ubuntu ubiquity: /usr/bin/casper-reconfigure: package 'gnome-power-manager' is not installed
Apr 13 00:44:02 ubuntu python: log-output -t ubiquity chroot /target mount -t proc proc /proc
Apr 13 00:44:02 ubuntu python: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Apr 13 00:44:02 ubuntu python: log-output -t ubiquity mount --bind /dev /target/dev
Apr 13 00:44:03 ubuntu hw-detect:  * No PCMCIA bridge module specified
Apr 13 00:44:05 ubuntu check-missing-firmware: no missing firmware in /tmp/missing-firmware
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity chroot /target umount /sys
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity chroot /target umount /proc
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity umount /target/dev
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity /usr/lib/ubiquity/debian-installer-utils/register-module.post-base-installer
Apr 13 00:44:06 ubuntu ubiquity: chroot: 
Apr 13 00:44:06 ubuntu ubiquity: cannot run command `debconf-communicate': No such file or directory
Apr 13 00:44:06 ubuntu ubiquity: umount: /target/cdrom: not found
Apr 13 00:44:06 ubuntu ubiquity: 
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity umount /target/cdrom
Apr 13 00:44:06 ubuntu ubiquity: grep: 
Apr 13 00:44:06 ubuntu ubiquity: /target/etc/apt/sources.list
Apr 13 00:44:06 ubuntu ubiquity: : No such file or directory
Apr 13 00:44:06 ubuntu ubiquity: 
Apr 13 00:44:06 ubuntu python: Exception during installation:
Apr 13 00:44:06 ubuntu python: Traceback (most recent call last):
Apr 13 00:44:06 ubuntu python:   File "/usr/share/ubiquity/install.py", line 2497, in <module>
Apr 13 00:44:06 ubuntu python:     install.run()
Apr 13 00:44:06 ubuntu python:   File "/usr/share/ubiquity/install.py", line 391, in run
Apr 13 00:44:06 ubuntu python:     self.configure_hardware()
Apr 13 00:44:06 ubuntu python:   File "/usr/share/ubiquity/install.py", line 1403, in configure_hardware
Apr 13 00:44:06 ubuntu python:     install_misc.set_debconf(self.target, 'popularity-contest/participate', participate, self.db)
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 70, in set_debconf
Apr 13 00:44:06 ubuntu python:     dc = debconf.Debconf(read=dccomm.stdout, write=dccomm.stdin)
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 53, in __init__
Apr 13 00:44:06 ubuntu python:     self.setUp(title)
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 56, in setUp
Apr 13 00:44:06 ubuntu python:     self.version = self.version(2)
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 65, in <lambda>
Apr 13 00:44:06 ubuntu python:     lambda *args, **kw: self.command(command, *args, **kw))
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 86, in command
Apr 13 00:44:06 ubuntu python:     status = int(status)
Apr 13 00:44:06 ubuntu python: ValueError: invalid literal for int() with base 10: ''
Apr 13 00:44:06 ubuntu python: 
Apr 13 00:44:06 ubuntu ubiquity[2608]: debconffilter_done: ubiquity.components.install (current: None)
Apr 13 00:44:06 ubuntu ubiquity[2608]: Exception in GTK frontend (invoking crash handler):
Apr 13 00:44:06 ubuntu ubiquity[2608]: Traceback (most recent call last):
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/bin/ubiquity", line 524, in <module>
Apr 13 00:44:06 ubuntu ubiquity[2608]:     main(oem_config)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/bin/ubiquity", line 511, in main
Apr 13 00:44:06 ubuntu ubiquity[2608]:     install(query=options.query)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/bin/ubiquity", line 242, in install
Apr 13 00:44:06 ubuntu ubiquity[2608]:     ret = wizard.run()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 508, in run
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.process_step()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1160, in process_step
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.progress_loop()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1043, in progress_loop
Apr 13 00:44:06 ubuntu ubiquity[2608]:     (ret, realtb))
Apr 13 00:44:06 ubuntu ubiquity[2608]: RuntimeError: Install failed with exit code 1
Apr 13 00:44:06 ubuntu ubiquity[2608]: Traceback (most recent call last):
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/share/ubiquity/install.py", line 2497, in <module>
Apr 13 00:44:06 ubuntu ubiquity[2608]:     install.run()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/share/ubiquity/install.py", line 391, in run
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.configure_hardware()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/share/ubiquity/install.py", line 1403, in configure_hardware
Apr 13 00:44:06 ubuntu ubiquity[2608]:     install_misc.set_debconf(self.target, 'popularity-contest/participate', participate, self.db)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 70, in set_debconf
Apr 13 00:44:06 ubuntu ubiquity[2608]:     dc = debconf.Debconf(read=dccomm.stdout, write=dccomm.stdin)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 53, in __init__
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.setUp(title)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 56, in setUp
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.version = self.version(2)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 65, in <lambda>
Apr 13 00:44:06 ubuntu ubiquity[2608]:     lambda *args, **kw: self.command(command, *args, **kw))
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 86, in command
Apr 13 00:44:06 ubuntu ubiquity[2608]:     status = int(status)
Apr 13 00:44:06 ubuntu ubiquity[2608]: ValueError: invalid literal for int() with base 10: ''
Apr 13 00:44:06 ubuntu ubiquity[2608]: 
Apr 13 00:44:11 ubuntu ubiquity[2608]: last message repeated 2 times
Apr 13 00:44:11 ubuntu gdm-binary[13702]: WARNING: Unable to find users: no seat-id found
Apr 13 00:44:12 ubuntu acpid: client 1497[0:0] has disconnected
Apr 13 00:44:12 ubuntu acpid: client connected from 13708[0:0]
Apr 13 00:44:12 ubuntu acpid: 1 client rule loaded
Apr 13 00:44:13 ubuntu kernel: [  871.538751] [TTM] Zone  kernel: Available graphics memory: 436968 kiB.
Apr 13 00:44:13 ubuntu kernel: [  871.538756] [TTM] Zone highmem: Available graphics memory: 1030476 kiB.
Apr 13 00:44:13 ubuntu kernel: [  871.538772] [drm] nouveau 0000:01:00.0: 256 MiB VRAM
Apr 13 00:44:13 ubuntu kernel: [  871.538853] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Apr 13 00:44:13 ubuntu kernel: [  871.538870] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Apr 13 00:44:13 ubuntu kernel: [  871.538879] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 13 00:44:13 ubuntu kernel: [  871.538959] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 13 00:44:13 ubuntu kernel: [  871.538963] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
Apr 13 00:44:13 ubuntu kernel: [  871.539183] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
Apr 13 00:44:13 ubuntu kernel: [  871.539853] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
Apr 13 00:44:13 ubuntu kernel: [  871.540072] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 0
Apr 13 00:44:13 ubuntu kernel: [  871.540592] [TTM] Zone  kernel: Used memory at exit: 0 kiB.
Apr 13 00:44:13 ubuntu kernel: [  871.540601] [TTM] Zone highmem: Used memory at exit: 0 kiB.
Apr 13 00:44:14 ubuntu gdm-session-worker[13712]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 13 00:44:16 ubuntu pulseaudio[2631]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Apr 13 00:45:25 ubuntu pulseaudio[2631]: last message repeated 3 times
Apr 13 00:45:25 ubuntu AptDaemon: INFO: Initializing daemon
```

I would appreciate your suggestions and please help me install Lucid.  Thank you very much!

---

### Post by iClouseau88 on 2010-04-12
Hi,

I cleaned the DVD drive and checked SHA1 of Lucid install CD: OK. Still got rebooted into Ubuntu screen at the end of installation process.  Here's the content of /var/log/syslog from the terminal:

```
Apr 12 20:30:32 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr 12 20:30:32 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1065" x-info="http://www.rsyslog.com"] (re)start
Apr 12 20:30:32 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Apr 12 20:30:32 ubuntu rsyslogd: rsyslogd's userid changed to 101
Apr 12 20:30:32 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Linux version 2.6.32-19-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 (Ubuntu 2.6.32-19.28-generic 2.6.32.10+drm33.1)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Apr 12 20:30:32 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff30000 (usable)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ff30000 - 000000007ff40000 (ACPI data)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] DMI 2.3 present.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] last_pfn = 0x7ff30 max_arch_pfn = 0x100000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   A0000-DFFFF uncachable
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   E0000-EFFFF write-through
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   1 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   2 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   3 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   4 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   5 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   6 base 0E0000000 mask FFC000000 write-combining
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   7 disabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Apr 12 20:30:32 ubuntu kernel: [    0.000000] modified physical RAM map:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000007ff30000 (usable)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 000000007ff30000 - 000000007ff40000 (ACPI data)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  modified: 00000000ff7c0000 - 0000000100000000 (reserved)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Apr 12 20:30:32 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Apr 12 20:30:32 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] RAMDISK: 7f62c000 - 7feff7be
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008dc000 - 011af7be
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007f62c000 - 000000007feff7bd to 008dc000 - 011af7bd
Apr 12 20:30:32 ubuntu kernel: [    0.000000] 1159MB HIGHMEM available.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Apr 12 20:30:32 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008d7e98]    TEXT DATA BSS ==> [0000100000 - 00008d7e98]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #5 [00008d8000 - 00008db1a4]              BRK ==> [00008d8000 - 00008db1a4]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #7 [00008dc000 - 00011af7be]      NEW RAMDISK ==> [00008dc000 - 00011af7be]
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Apr 12 20:30:32 ubuntu kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Zone PFN ranges:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007ff30
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Apr 12 20:30:32 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007ff30
Apr 12 20:30:32 ubuntu kernel: [    0.000000] On node 0 totalpages: 523967
Apr 12 20:30:32 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c0796720, node_mem_map c11b1200
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   HighMem zone: 2319 pages used for memmap
Apr 12 20:30:32 ubuntu kernel: [    0.000000]   HighMem zone: 294435 pages, LIFO batch:31
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Using APIC driver default
Apr 12 20:30:32 ubuntu kernel: [    0.000000] SFI: Simple Firmware Interface v0.7 [http://simplefirmware.org](http://simplefirmware.org)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     Virtual Wire compatibility mode.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MPTABLE: OEM ID: TEMPLATE
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MPTABLE: Product ID: 
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MPTABLE: APIC at: 0xFEE00000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] I/O APIC #13 Version 3 at 0xFEC00000.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 12 20:30:32 ubuntu kernel: [    0.000000] MPTABLE: no processors registered!
Apr 12 20:30:32 ubuntu kernel: [    0.000000] BIOS bug, MP table errors detected!...
Apr 12 20:30:32 ubuntu kernel: [    0.000000] ... disabling SMP support. (tell your hw vendor)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Apr 12 20:30:32 ubuntu kernel: [    0.000000] APIC: disable apic facility
Apr 12 20:30:32 ubuntu kernel: [    0.000000] nr_irqs_gsi: 16
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7f7c0000)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr 12 20:30:32 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s35992 r0 d21352 u4194304
Apr 12 20:30:32 ubuntu kernel: [    0.000000] pcpu-alloc: s35992 r0 d21352 u4194304 alloc=1*4194304
Apr 12 20:30:32 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519872
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz  splash --  acpi=off noapic nolapic nomodeset
Apr 12 20:30:32 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Initializing CPU#0
Apr 12 20:30:32 ubuntu kernel: [    0.000000] allocated 10481280 bytes of page_cgroup
Apr 12 20:30:32 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007ff30)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Memory: 2050220k/2096320k available (4671k kernel code, 44632k reserved, 2116k data, 656k init, 1187016k highmem)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]       .init : 0xc07a1000 - 0xc0845000   ( 656 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]       .data : 0xc058fd43 - 0xc07a0e48   (2116 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc058fd43   (4671 kB)
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Apr 12 20:30:32 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Apr 12 20:30:32 ubuntu kernel: [    0.000000] console [tty0] enabled
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Apr 12 20:30:32 ubuntu kernel: [    0.000000] Detected 2520.068 MHz processor.
Apr 12 20:30:32 ubuntu kernel: [    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5040.13 BogoMIPS (lpj=10080272)
Apr 12 20:30:32 ubuntu kernel: [    0.004154] Security Framework initialized
Apr 12 20:30:32 ubuntu kernel: [    0.004252] AppArmor: AppArmor initialized
Apr 12 20:30:32 ubuntu kernel: [    0.004323] Mount-cache hash table entries: 512
Apr 12 20:30:32 ubuntu kernel: [    0.004581] Initializing cgroup subsys ns
Apr 12 20:30:32 ubuntu kernel: [    0.004649] Initializing cgroup subsys cpuacct
Apr 12 20:30:32 ubuntu kernel: [    0.004715] Initializing cgroup subsys memory
Apr 12 20:30:32 ubuntu kernel: [    0.004788] Initializing cgroup subsys devices
Apr 12 20:30:32 ubuntu kernel: [    0.004851] Initializing cgroup subsys freezer
Apr 12 20:30:32 ubuntu kernel: [    0.004914] Initializing cgroup subsys net_cls
Apr 12 20:30:32 ubuntu kernel: [    0.005009] CPU: Trace cache: 12K uops, L1 D cache: 8K
Apr 12 20:30:32 ubuntu kernel: [    0.005121] CPU: L2 cache: 512K
Apr 12 20:30:32 ubuntu kernel: [    0.005183] CPU: Hyper-Threading is disabled
Apr 12 20:30:32 ubuntu kernel: [    0.005248] mce: CPU supports 4 MCE banks
Apr 12 20:30:32 ubuntu kernel: [    0.005330] Performance Events: no PMU driver, software events only.
Apr 12 20:30:32 ubuntu kernel: [    0.005449] Checking 'hlt' instruction... OK.
Apr 12 20:30:32 ubuntu kernel: [    0.021134] SMP alternatives: switching to UP code
Apr 12 20:30:32 ubuntu kernel: [    0.033821] Freeing SMP alternatives: 19k freed
Apr 12 20:30:32 ubuntu kernel: [    0.033915] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr 12 20:30:32 ubuntu kernel: [    0.033987] ftrace: allocating 21765 entries in 43 pages
Apr 12 20:30:32 ubuntu kernel: [    0.036114] weird, boot CPU (#0) not listed by the BIOS.
Apr 12 20:30:32 ubuntu kernel: [    0.036185] SMP motherboard not detected.
Apr 12 20:30:32 ubuntu kernel: [    0.036246] Apic disabled
Apr 12 20:30:32 ubuntu kernel: [    0.036304] Local APIC not detected. Using dummy APIC emulation.
Apr 12 20:30:32 ubuntu kernel: [    0.036367] SMP disabled
Apr 12 20:30:32 ubuntu kernel: [    0.036651] Brought up 1 CPUs
Apr 12 20:30:32 ubuntu kernel: [    0.036714] Total of 1 processors activated (5040.13 BogoMIPS).
Apr 12 20:30:32 ubuntu kernel: [    0.040058] CPU0 attaching NULL sched-domain.
Apr 12 20:30:32 ubuntu kernel: [    0.040228] devtmpfs: initialized
Apr 12 20:30:32 ubuntu kernel: [    0.040787] regulator: core version 0.5
Apr 12 20:30:32 ubuntu kernel: [    0.040890] Time: 20:29:42  Date: 04/12/10
Apr 12 20:30:32 ubuntu kernel: [    0.041010] NET: Registered protocol family 16
Apr 12 20:30:32 ubuntu kernel: [    0.041227] EISA bus registered
Apr 12 20:30:32 ubuntu kernel: [    0.041449] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Apr 12 20:30:32 ubuntu kernel: [    0.041512] PCI: Using configuration type 1 for base access
Apr 12 20:30:32 ubuntu kernel: [    0.042867] bio: create slab <bio-0> at 0
Apr 12 20:30:32 ubuntu kernel: [    0.042990] ACPI: Interpreter disabled.
Apr 12 20:30:32 ubuntu kernel: [    0.043129] vgaarb: loaded
Apr 12 20:30:32 ubuntu kernel: [    0.043340] SCSI subsystem initialized
Apr 12 20:30:32 ubuntu kernel: [    0.043453] libata version 3.00 loaded.
Apr 12 20:30:32 ubuntu kernel: [    0.043544] usbcore: registered new interface driver usbfs
Apr 12 20:30:32 ubuntu kernel: [    0.043621] usbcore: registered new interface driver hub
Apr 12 20:30:32 ubuntu kernel: [    0.043720] usbcore: registered new device driver usb
Apr 12 20:30:32 ubuntu kernel: [    0.044163] PCI: Probing PCI hardware
Apr 12 20:30:32 ubuntu kernel: [    0.044226] PCI: Probing PCI hardware (bus 00)
Apr 12 20:30:32 ubuntu kernel: [    0.044282] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
Apr 12 20:30:32 ubuntu kernel: [    0.044384] pci 0000:00:01.0: supports D1
Apr 12 20:30:32 ubuntu kernel: [    0.044428] pci 0000:00:0a.0: reg 10 io port: [0xeea0-0xeebf]
Apr 12 20:30:32 ubuntu kernel: [    0.044473] pci 0000:00:0a.0: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.044509] pci 0000:00:0d.0: reg 10 io port: [0xe000-0xe0ff]
Apr 12 20:30:32 ubuntu kernel: [    0.044517] pci 0000:00:0d.0: reg 14 32bit mmio: [0xdfd00000-0xdfd000ff]
Apr 12 20:30:32 ubuntu kernel: [    0.044542] pci 0000:00:0d.0: reg 30 32bit mmio pref: [0xdfc00000-0xdfc1ffff]
Apr 12 20:30:32 ubuntu kernel: [    0.044562] pci 0000:00:0d.0: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.044565] pci 0000:00:0d.0: PME# supported from D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.044631] pci 0000:00:0d.0: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.044725] pci 0000:00:0f.0: reg 10 io port: [0xefe0-0xefe7]
Apr 12 20:30:32 ubuntu kernel: [    0.044734] pci 0000:00:0f.0: reg 14 io port: [0xefac-0xefaf]
Apr 12 20:30:32 ubuntu kernel: [    0.044742] pci 0000:00:0f.0: reg 18 io port: [0xefa0-0xefa7]
Apr 12 20:30:32 ubuntu kernel: [    0.044750] pci 0000:00:0f.0: reg 1c io port: [0xefa8-0xefab]
Apr 12 20:30:32 ubuntu kernel: [    0.044757] pci 0000:00:0f.0: reg 20 io port: [0xef90-0xef9f]
Apr 12 20:30:32 ubuntu kernel: [    0.044765] pci 0000:00:0f.0: reg 24 io port: [0xe800-0xe8ff]
Apr 12 20:30:32 ubuntu kernel: [    0.044840] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
Apr 12 20:30:32 ubuntu kernel: [    0.044928] pci 0000:00:10.0: reg 20 io port: [0xeec0-0xeedf]
Apr 12 20:30:32 ubuntu kernel: [    0.044955] pci 0000:00:10.0: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.044958] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045024] pci 0000:00:10.0: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045133] pci 0000:00:10.1: reg 20 io port: [0xef00-0xef1f]
Apr 12 20:30:32 ubuntu kernel: [    0.045161] pci 0000:00:10.1: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.045165] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045230] pci 0000:00:10.1: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045340] pci 0000:00:10.2: reg 20 io port: [0xef20-0xef3f]
Apr 12 20:30:32 ubuntu kernel: [    0.045368] pci 0000:00:10.2: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.045372] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045437] pci 0000:00:10.2: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045547] pci 0000:00:10.3: reg 20 io port: [0xef40-0xef5f]
Apr 12 20:30:32 ubuntu kernel: [    0.045575] pci 0000:00:10.3: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.045578] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045644] pci 0000:00:10.3: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045737] pci 0000:00:10.4: reg 10 32bit mmio: [0xdfe00000-0xdfe000ff]
Apr 12 20:30:32 ubuntu kernel: [    0.045782] pci 0000:00:10.4: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.045785] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.045851] pci 0000:00:10.4: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.045976] HPET not enabled in BIOS. You might try hpet=force boot option
Apr 12 20:30:32 ubuntu kernel: [    0.046043] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
Apr 12 20:30:32 ubuntu kernel: [    0.046161] pci 0000:00:11.5: reg 10 io port: [0x1000-0x10ff]
Apr 12 20:30:32 ubuntu kernel: [    0.046208] pci 0000:00:11.5: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.046245] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
Apr 12 20:30:32 ubuntu kernel: [    0.046326] pci 0000:00:12.0: reg 10 io port: [0xe400-0xe4ff]
Apr 12 20:30:32 ubuntu kernel: [    0.046334] pci 0000:00:12.0: reg 14 32bit mmio: [0xdff00000-0xdff000ff]
Apr 12 20:30:32 ubuntu kernel: [    0.046375] pci 0000:00:12.0: supports D1 D2
Apr 12 20:30:32 ubuntu kernel: [    0.046378] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 12 20:30:32 ubuntu kernel: [    0.046443] pci 0000:00:12.0: PME# disabled
Apr 12 20:30:32 ubuntu kernel: [    0.046563] pci 0000:01:00.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
Apr 12 20:30:32 ubuntu kernel: [    0.046571] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xc0000000-0xcfffffff]
Apr 12 20:30:32 ubuntu kernel: [    0.046592] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xdf600000-0xdf61ffff]
Apr 12 20:30:32 ubuntu kernel: [    0.046653] pci 0000:00:01.0: bridge 32bit mmio: [0xdd500000-0xdf6fffff]
Apr 12 20:30:32 ubuntu kernel: [    0.046658] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbd400000-0xdd3fffff]
Apr 12 20:30:32 ubuntu kernel: [    0.047088] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr 12 20:30:32 ubuntu kernel: [    0.047224] pci 0000:00:11.0: VIA IRQ router [1106:3227]
Apr 12 20:30:32 ubuntu kernel: [    0.047309] PCI: setting IRQ 11 as level-triggered
Apr 12 20:30:32 ubuntu kernel: [    0.047314] pci 0000:00:0f.1: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    0.047388] pci 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    0.047453] pci 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    0.047527] pci 0000:00:0f.1: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    0.047605] PCI: setting IRQ 5 as level-triggered
Apr 12 20:30:32 ubuntu kernel: [    0.047610] pci 0000:00:11.5: found PCI INT C -> IRQ 5
Apr 12 20:30:32 ubuntu kernel: [    0.048023] pci 0000:00:11.5: sharing IRQ 5 with 0000:00:0a.0
Apr 12 20:30:32 ubuntu kernel: [    0.048100] pci 0000:00:11.5: sharing IRQ 5 with 0000:00:10.4
Apr 12 20:30:32 ubuntu kernel: [    0.048168] pci 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
Apr 12 20:30:32 ubuntu kernel: [    0.048408] NetLabel: Initializing
Apr 12 20:30:32 ubuntu kernel: [    0.048470] NetLabel:  domain hash size = 128
Apr 12 20:30:32 ubuntu kernel: [    0.048530] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 12 20:30:32 ubuntu kernel: [    0.048606] NetLabel:  unlabeled traffic allowed by default
Apr 12 20:30:32 ubuntu kernel: [    0.048717] Switching to clocksource tsc
Apr 12 20:30:32 ubuntu kernel: [    0.051432] AppArmor: AppArmor Filesystem Enabled
Apr 12 20:30:32 ubuntu kernel: [    0.051505] pnp: PnP ACPI: disabled
Apr 12 20:30:32 ubuntu kernel: [    0.051568] PnPBIOS: Scanning system for PnP BIOS support...
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5b70
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x675a, dseg 0xf0000
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PNPBIOS fault.. attempting recovery.
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
Apr 12 20:30:32 ubuntu kernel: [    0.051651] PnPBIOS: Check with your vendor for an updated BIOS
Apr 12 20:30:32 ubuntu kernel: [    0.051654] PnPBIOS: get_dev_node: unexpected status 0x3a
Apr 12 20:30:32 ubuntu kernel: [    0.051717] PnPBIOS: 10 nodes reported by PnP BIOS; 10 recorded by driver
Apr 12 20:30:32 ubuntu kernel: [    0.051794] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.051860] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.051925] system 00:00: iomem range 0xe4000-0xfffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.051990] system 00:00: iomem range 0x100000-0x7ff2ffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052063] system 00:00: iomem range 0x7ff30000-0x7ff3ffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052136] system 00:00: iomem range 0x7ff40000-0x7ffeffff could not be reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052209] system 00:00: iomem range 0x7fff0000-0x7fffffff has been reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052274] system 00:00: iomem range 0xff7c0000-0xffffffff has been reserved
Apr 12 20:30:32 ubuntu kernel: [    0.052609] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Apr 12 20:30:32 ubuntu kernel: [    0.052673] pci 0000:00:01.0:   IO window: disabled
Apr 12 20:30:32 ubuntu kernel: [    0.052738] pci 0000:00:01.0:   MEM window: 0xdd500000-0xdf6fffff
Apr 12 20:30:32 ubuntu kernel: [    0.052803] pci 0000:00:01.0:   PREFETCH window: 0xbd400000-0xdd3fffff
Apr 12 20:30:32 ubuntu kernel: [    0.052882] pci 0000:00:01.0: setting latency timer to 64
Apr 12 20:30:32 ubuntu kernel: [    0.052888] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Apr 12 20:30:32 ubuntu kernel: [    0.052891] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Apr 12 20:30:32 ubuntu kernel: [    0.052895] pci_bus 0000:01: resource 1 mem: [0xdd500000-0xdf6fffff]
Apr 12 20:30:32 ubuntu kernel: [    0.052898] pci_bus 0000:01: resource 2 pref mem [0xbd400000-0xdd3fffff]
Apr 12 20:30:32 ubuntu kernel: [    0.052948] NET: Registered protocol family 2
Apr 12 20:30:32 ubuntu kernel: [    0.053135] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.053697] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.054722] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 12 20:30:32 ubuntu kernel: [    0.055421] TCP: Hash tables configured (established 131072 bind 65536)
Apr 12 20:30:32 ubuntu kernel: [    0.055494] TCP reno registered
Apr 12 20:30:32 ubuntu kernel: [    0.055731] NET: Registered protocol family 1
Apr 12 20:30:32 ubuntu kernel: [    0.055820] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Apr 12 20:30:32 ubuntu kernel: [    1.654779] pci 0000:00:10.4: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Apr 12 20:30:32 ubuntu kernel: [    1.654955] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
Apr 12 20:30:32 ubuntu kernel: [    1.655034] pci 0000:01:00.0: Boot video device
Apr 12 20:30:32 ubuntu kernel: [    1.655246] cpufreq-nforce2: No nForce2 chipset.
Apr 12 20:30:32 ubuntu kernel: [    1.655351] Scanning for low memory corruption every 60 seconds
Apr 12 20:30:32 ubuntu kernel: [    1.655553] audit: initializing netlink socket (disabled)
Apr 12 20:30:32 ubuntu kernel: [    1.655629] type=2000 audit(1271104183.654:1): initialized
Apr 12 20:30:32 ubuntu kernel: [    1.664427] Trying to unpack rootfs image as initramfs...
Apr 12 20:30:32 ubuntu kernel: [    4.879412] highmem bounce pool size: 64 pages
Apr 12 20:30:32 ubuntu kernel: [    4.879488] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 12 20:30:32 ubuntu kernel: [    4.881417] VFS: Disk quotas dquot_6.5.2
Apr 12 20:30:32 ubuntu kernel: [    4.881553] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 12 20:30:32 ubuntu kernel: [    4.882422] fuse init (API version 7.13)
Apr 12 20:30:32 ubuntu kernel: [    4.882598] msgmni has been set to 1687
Apr 12 20:30:32 ubuntu kernel: [    4.882977] alg: No test for stdrng (krng)
Apr 12 20:30:32 ubuntu kernel: [    4.883127] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr 12 20:30:32 ubuntu kernel: [    4.883201] io scheduler noop registered
Apr 12 20:30:32 ubuntu kernel: [    4.883262] io scheduler anticipatory registered
Apr 12 20:30:32 ubuntu kernel: [    4.883323] io scheduler deadline registered
Apr 12 20:30:32 ubuntu kernel: [    4.883432] io scheduler cfq registered (default)
Apr 12 20:30:32 ubuntu kernel: [    4.883639] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 12 20:30:32 ubuntu kernel: [    4.883733] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 12 20:30:32 ubuntu kernel: [    4.885800] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr 12 20:30:32 ubuntu kernel: [    4.885977] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 12 20:30:32 ubuntu kernel: [    4.886474] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 12 20:30:32 ubuntu kernel: [    4.887902] brd: module loaded
Apr 12 20:30:32 ubuntu kernel: [    4.888578] loop: module loaded
Apr 12 20:30:32 ubuntu kernel: [    4.888772] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 12 20:30:32 ubuntu kernel: [    4.889052] pata_acpi 0000:00:0f.1: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    4.889129] pata_acpi 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    4.889196] pata_acpi 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    4.889272] pata_acpi 0000:00:0f.1: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    4.889340] pata_acpi 0000:00:0f.1: VIA VLink IRQ fixup, from 255 to 11
Apr 12 20:30:32 ubuntu kernel: [    4.889912] Fixed MDIO Bus: probed
Apr 12 20:30:32 ubuntu kernel: [    4.890021] PPP generic driver version 2.4.2
Apr 12 20:30:32 ubuntu kernel: [    4.890143] tun: Universal TUN/TAP device driver, 1.6
Apr 12 20:30:32 ubuntu kernel: [    4.890205] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr 12 20:30:32 ubuntu kernel: [    4.890383] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 12 20:30:32 ubuntu kernel: [    4.890470] ehci_hcd 0000:00:10.4: found PCI INT C -> IRQ 5
Apr 12 20:30:32 ubuntu kernel: [    4.890538] ehci_hcd 0000:00:10.4: sharing IRQ 5 with 0000:00:0a.0
Apr 12 20:30:32 ubuntu kernel: [    4.890618] ehci_hcd 0000:00:10.4: sharing IRQ 5 with 0000:00:11.5
Apr 12 20:30:32 ubuntu kernel: [    4.890683] ehci_hcd 0000:00:10.4: sharing IRQ 5 with 0000:00:11.6
Apr 12 20:30:32 ubuntu kernel: [    4.890834] isapnp: Scanning for PnP cards...
Apr 12 20:30:32 ubuntu kernel: [    4.896429] ehci_hcd 0000:00:10.4: EHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.896545] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
Apr 12 20:30:32 ubuntu kernel: [    4.896669] ehci_hcd 0000:00:10.4: irq 5, io mem 0xdfe00000
Apr 12 20:30:32 ubuntu kernel: [    4.940327] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
Apr 12 20:30:32 ubuntu kernel: [    4.940511] usb usb1: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.940616] hub 1-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.940687] hub 1-0:1.0: 8 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.940820] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 12 20:30:32 ubuntu kernel: [    4.940901] uhci_hcd: USB Universal Host Controller Interface driver
Apr 12 20:30:32 ubuntu kernel: [    4.941017] uhci_hcd 0000:00:10.0: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    4.941091] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:0f.1
Apr 12 20:30:32 ubuntu kernel: [    4.941158] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    4.941233] uhci_hcd 0000:00:10.0: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    4.941305] uhci_hcd 0000:00:10.0: UHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.941410] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Apr 12 20:30:32 ubuntu kernel: [    4.941508] uhci_hcd 0000:00:10.0: irq 11, io base 0x0000eec0
Apr 12 20:30:32 ubuntu kernel: [    4.941689] usb usb2: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.941786] hub 2-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.941858] hub 2-0:1.0: 2 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.941979] uhci_hcd 0000:00:10.1: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    4.942054] uhci_hcd 0000:00:10.1: sharing IRQ 11 with 0000:00:0f.1
Apr 12 20:30:32 ubuntu kernel: [    4.942120] uhci_hcd 0000:00:10.1: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    4.942197] uhci_hcd 0000:00:10.1: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    4.942267] uhci_hcd 0000:00:10.1: UHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.942371] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Apr 12 20:30:32 ubuntu kernel: [    4.942465] uhci_hcd 0000:00:10.1: irq 11, io base 0x0000ef00
Apr 12 20:30:32 ubuntu kernel: [    4.942639] usb usb3: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.942735] hub 3-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.942845] hub 3-0:1.0: 2 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.942960] PCI: setting IRQ 10 as level-triggered
Apr 12 20:30:32 ubuntu kernel: [    4.942966] uhci_hcd 0000:00:10.2: found PCI INT B -> IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    4.943036] uhci_hcd 0000:00:10.2: sharing IRQ 10 with 0000:00:0d.0
Apr 12 20:30:32 ubuntu kernel: [    4.943101] uhci_hcd 0000:00:10.2: sharing IRQ 10 with 0000:00:0f.0
Apr 12 20:30:32 ubuntu kernel: [    4.943173] uhci_hcd 0000:00:10.2: sharing IRQ 10 with 0000:00:10.3
Apr 12 20:30:32 ubuntu kernel: [    4.943253] uhci_hcd 0000:00:10.2: UHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.943359] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Apr 12 20:30:32 ubuntu kernel: [    4.943455] uhci_hcd 0000:00:10.2: irq 10, io base 0x0000ef20
Apr 12 20:30:32 ubuntu kernel: [    4.943639] usb usb4: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.943735] hub 4-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.943805] hub 4-0:1.0: 2 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.943921] uhci_hcd 0000:00:10.3: found PCI INT B -> IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    4.943992] uhci_hcd 0000:00:10.3: sharing IRQ 10 with 0000:00:0d.0
Apr 12 20:30:32 ubuntu kernel: [    4.944057] uhci_hcd 0000:00:10.3: sharing IRQ 10 with 0000:00:0f.0
Apr 12 20:30:32 ubuntu kernel: [    4.944127] uhci_hcd 0000:00:10.3: sharing IRQ 10 with 0000:00:10.2
Apr 12 20:30:32 ubuntu kernel: [    4.944208] uhci_hcd 0000:00:10.3: UHCI Host Controller
Apr 12 20:30:32 ubuntu kernel: [    4.944327] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
Apr 12 20:30:32 ubuntu kernel: [    4.944421] uhci_hcd 0000:00:10.3: irq 10, io base 0x0000ef40
Apr 12 20:30:32 ubuntu kernel: [    4.944590] usb usb5: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    4.944686] hub 5-0:1.0: USB hub found
Apr 12 20:30:32 ubuntu kernel: [    4.944756] hub 5-0:1.0: 2 ports detected
Apr 12 20:30:32 ubuntu kernel: [    4.944940] PNP: No PS/2 controller found. Probing ports directly.
Apr 12 20:30:32 ubuntu kernel: [    4.991368] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 12 20:30:32 ubuntu kernel: [    4.991436] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 12 20:30:32 ubuntu kernel: [    4.991666] mice: PS/2 mouse device common for all mice
Apr 12 20:30:32 ubuntu kernel: [    4.991880] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Apr 12 20:30:32 ubuntu kernel: [    4.991973] rtc0: alarms up to one day, 114 bytes nvram
Apr 12 20:30:32 ubuntu kernel: [    4.992185] device-mapper: uevent: version 1.0.3
Apr 12 20:30:32 ubuntu kernel: [    4.992396] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Apr 12 20:30:32 ubuntu kernel: [    4.992538] device-mapper: multipath: version 1.1.0 loaded
Apr 12 20:30:32 ubuntu kernel: [    4.992602] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 12 20:30:32 ubuntu kernel: [    4.992812] EISA: Probing bus 0 at eisa.0
Apr 12 20:30:32 ubuntu kernel: [    4.992881] Cannot allocate resource for EISA slot 1
Apr 12 20:30:32 ubuntu kernel: [    4.992969] EISA: Detected 0 cards.
Apr 12 20:30:32 ubuntu kernel: [    4.993089] cpuidle: using governor ladder
Apr 12 20:30:32 ubuntu kernel: [    4.993151] cpuidle: using governor menu
Apr 12 20:30:32 ubuntu kernel: [    4.993772] TCP cubic registered
Apr 12 20:30:32 ubuntu kernel: [    4.993995] NET: Registered protocol family 10
Apr 12 20:30:32 ubuntu kernel: [    4.994619] lo: Disabled Privacy Extensions
Apr 12 20:30:32 ubuntu kernel: [    4.995104] NET: Registered protocol family 17
Apr 12 20:30:32 ubuntu kernel: [    4.995218] Using IPI No-Shortcut mode
Apr 12 20:30:32 ubuntu kernel: [    4.995400] PM: Resume from disk failed.
Apr 12 20:30:32 ubuntu kernel: [    4.995418] registered taskstats version 1
Apr 12 20:30:32 ubuntu kernel: [    4.995798]   Magic number: 6:935:497
Apr 12 20:30:32 ubuntu kernel: [    4.995954] rtc_cmos 00:04: setting system clock to 2010-04-12 20:29:47 UTC (1271104187)
Apr 12 20:30:32 ubuntu kernel: [    4.996029] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 12 20:30:32 ubuntu kernel: [    4.996091] EDD information not available.
Apr 12 20:30:32 ubuntu kernel: [    5.257573] isapnp: No Plug & Play device found
Apr 12 20:30:32 ubuntu kernel: [    5.341094] Freeing initrd memory: 9037k freed
Apr 12 20:30:32 ubuntu kernel: [    5.352797] Freeing unused kernel memory: 656k freed
Apr 12 20:30:32 ubuntu kernel: [    5.353799] Write protecting the kernel text: 4672k
Apr 12 20:30:32 ubuntu kernel: [    5.353891] Write protecting the kernel read-only data: 1836k
Apr 12 20:30:32 ubuntu kernel: [    5.394464] udev: starting version 151
Apr 12 20:30:32 ubuntu kernel: [    5.558798] pata_via 0000:00:0f.1: version 0.3.4
Apr 12 20:30:32 ubuntu kernel: [    5.558816] pata_via 0000:00:0f.1: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    5.558899] pata_via 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    5.558965] pata_via 0000:00:0f.1: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    5.559661] pata_via 0000:00:0f.1: sharing IRQ 11 with 0000:00:12.0
Apr 12 20:30:32 ubuntu kernel: [    5.559729] pata_via 0000:00:0f.1: VIA VLink IRQ fixup, from 255 to 11
Apr 12 20:30:32 ubuntu kernel: [    5.577055] scsi0 : pata_via
Apr 12 20:30:32 ubuntu kernel: [    5.584016] scsi1 : pata_via
Apr 12 20:30:32 ubuntu kernel: [    5.584239] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Apr 12 20:30:32 ubuntu kernel: [    5.584305] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Apr 12 20:30:32 ubuntu kernel: [    5.584423] sata_via 0000:00:0f.0: version 2.4
Apr 12 20:30:32 ubuntu kernel: [    5.584444] sata_via 0000:00:0f.0: found PCI INT B -> IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    5.584517] sata_via 0000:00:0f.0: sharing IRQ 10 with 0000:00:0d.0
Apr 12 20:30:32 ubuntu kernel: [    5.584590] sata_via 0000:00:0f.0: sharing IRQ 10 with 0000:00:10.2
Apr 12 20:30:32 ubuntu kernel: [    5.584655] sata_via 0000:00:0f.0: sharing IRQ 10 with 0000:00:10.3
Apr 12 20:30:32 ubuntu kernel: [    5.584774] sata_via 0000:00:0f.0: routed to hard irq line 10
Apr 12 20:30:32 ubuntu kernel: [    5.590029] scsi2 : sata_via
Apr 12 20:30:32 ubuntu kernel: [    5.595211] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Apr 12 20:30:32 ubuntu kernel: [    5.595462] Linux agpgart interface v0.103
Apr 12 20:30:32 ubuntu kernel: [    5.595544] scsi3 : sata_via
Apr 12 20:30:32 ubuntu kernel: [    5.595680] ata3: SATA max UDMA/133 cmd 0xefe0 ctl 0xefac bmdma 0xef90 irq 10
Apr 12 20:30:32 ubuntu kernel: [    5.595746] ata4: SATA max UDMA/133 cmd 0xefa0 ctl 0xefa8 bmdma 0xef98 irq 10
Apr 12 20:30:32 ubuntu kernel: [    5.595978] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Apr 12 20:30:32 ubuntu kernel: [    5.596062] r8169 0000:00:0d.0: found PCI INT A -> IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    5.596135] r8169 0000:00:0d.0: sharing IRQ 10 with 0000:00:0f.0
Apr 12 20:30:32 ubuntu kernel: [    5.596206] r8169 0000:00:0d.0: sharing IRQ 10 with 0000:00:10.2
Apr 12 20:30:32 ubuntu kernel: [    5.596270] r8169 0000:00:0d.0: sharing IRQ 10 with 0000:00:10.3
Apr 12 20:30:32 ubuntu kernel: [    5.596372] r8169 0000:00:0d.0: no PCI Express capability
Apr 12 20:30:32 ubuntu kernel: [    5.597224] eth0: RTL8110s at 0xf8088000, 00:1e:2a:49:72:40, XID 04000000 IRQ 10
Apr 12 20:30:32 ubuntu kernel: [    5.600574] via-rhine 0000:00:12.0: found PCI INT A -> IRQ 11
Apr 12 20:30:32 ubuntu kernel: [    5.600653] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:0f.1
Apr 12 20:30:32 ubuntu kernel: [    5.600718] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.0
Apr 12 20:30:32 ubuntu kernel: [    5.600784] via-rhine 0000:00:12.0: sharing IRQ 11 with 0000:00:10.1
Apr 12 20:30:32 ubuntu kernel: [    5.601789] eth1: VIA Rhine II at 0xdff00000, 00:0e:a6:bd:8d:ae, IRQ 11.
Apr 12 20:30:32 ubuntu kernel: [    5.602529] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
Apr 12 20:30:32 ubuntu kernel: [    5.606817] usb 2-1: new low speed USB device using uhci_hcd and address 2
Apr 12 20:30:32 ubuntu kernel: [    5.725656] [drm] Initialized drm 1.1.0 20060810
Apr 12 20:30:32 ubuntu kernel: [    5.786734] usb 2-1: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    5.808774] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Apr 12 20:30:32 ubuntu kernel: [    5.820208] usbcore: registered new interface driver hiddev
Apr 12 20:30:32 ubuntu kernel: [    5.836096] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input1
Apr 12 20:30:32 ubuntu kernel: [    5.836420] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:10.0-1/input0
Apr 12 20:30:32 ubuntu kernel: [    5.877771] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/input/input2
Apr 12 20:30:32 ubuntu kernel: [    5.878357] generic-usb 0003:046D:C312.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:10.0-1/input1
Apr 12 20:30:32 ubuntu kernel: [    5.878478] usbcore: registered new interface driver usbhid
Apr 12 20:30:32 ubuntu kernel: [    5.878665] usbhid: v2.6:USB HID core driver
Apr 12 20:30:32 ubuntu kernel: [    5.935091] ata1.00: HPA unlocked: 312579695 -> 312581808, native 312581808
Apr 12 20:30:32 ubuntu kernel: [    5.935161] ata1.00: ATA-7: ST3160812A, 3.AAD, max UDMA/100
Apr 12 20:30:32 ubuntu kernel: [    5.935225] ata1.00: 312581808 sectors, multi 16: LBA48 
Apr 12 20:30:32 ubuntu kernel: [    5.977652] ata1.00: configured for UDMA/100
Apr 12 20:30:32 ubuntu kernel: [    5.977870] scsi 0:0:0:0: Direct-Access     ATA      ST3160812A       3.AA PQ: 0 ANSI: 5
Apr 12 20:30:32 ubuntu kernel: [    5.978169] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 12 20:30:32 ubuntu kernel: [    5.978818] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Apr 12 20:30:32 ubuntu kernel: [    5.978959] sd 0:0:0:0: [sda] Write Protect is off
Apr 12 20:30:32 ubuntu kernel: [    5.979022] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 12 20:30:32 ubuntu kernel: [    5.979056] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 20:30:32 ubuntu kernel: [    5.979340]  sda: sda1 sda2 sda3 <
Apr 12 20:30:32 ubuntu kernel: [    6.034778] usb 3-1: new low speed USB device using uhci_hcd and address 2
Apr 12 20:30:32 ubuntu kernel: [    6.041006]  sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
Apr 12 20:30:32 ubuntu kernel: [    6.115397]  sda2: <bsd:bad subpartition - ignored
Apr 12 20:30:32 ubuntu kernel: [    6.115508] bad subpartition - ignored
Apr 12 20:30:32 ubuntu kernel: [    6.115567] bad subpartition - ignored
Apr 12 20:30:32 ubuntu kernel: [    6.115627] bad subpartition - ignored
Apr 12 20:30:32 ubuntu kernel: [    6.115687]  >
Apr 12 20:30:32 ubuntu kernel: [    6.117073] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 12 20:30:32 ubuntu kernel: [    6.139113] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A106, max UDMA/33
Apr 12 20:30:32 ubuntu kernel: [    6.155009] ata2.01: configured for UDMA/33
Apr 12 20:30:32 ubuntu kernel: [    6.160544] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A106 PQ: 0 ANSI: 5
Apr 12 20:30:32 ubuntu kernel: [    6.166349] sr0: scsi3-mmc drive: 78x/78x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 12 20:30:32 ubuntu kernel: [    6.166428] Uniform CD-ROM driver Revision: 3.20
Apr 12 20:30:32 ubuntu kernel: [    6.166882] sr 1:0:1:0: Attached scsi CD-ROM sr0
Apr 12 20:30:32 ubuntu kernel: [    6.167076] sr 1:0:1:0: Attached scsi generic sg1 type 5
Apr 12 20:30:32 ubuntu kernel: [    6.233663] usb 3-1: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    6.370774] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Apr 12 20:30:32 ubuntu kernel: [    6.397122] agpgart: Detected VIA PT800 chipset
Apr 12 20:30:32 ubuntu kernel: [    6.426149] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
Apr 12 20:30:32 ubuntu kernel: [    6.464702] [drm] nouveau 0000:01:00.0: Detected an NV30 generation card (0x034600b1)
Apr 12 20:30:32 ubuntu kernel: [    6.464811] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
Apr 12 20:30:32 ubuntu kernel: [    6.468742] vga16fb: initializing
Apr 12 20:30:32 ubuntu kernel: [    6.468750] vga16fb: mapped to 0xc00a0000
Apr 12 20:30:32 ubuntu kernel: [    6.468998] fb0: VGA16 VGA frame buffer device
Apr 12 20:30:32 ubuntu kernel: [    6.613029] Console: switching to colour frame buffer device 80x30
Apr 12 20:30:32 ubuntu kernel: [    6.640701] generic-usb 0003:051D:0002.0003: hiddev97,hidraw2: USB HID v1.10 Device [APC Back-UPS ES 500 FW:2.e2.D USB FW:e2] on usb-0000:00:10.1-1/input0
Apr 12 20:30:32 ubuntu kernel: [    6.878787] usb 3-2: new low speed USB device using uhci_hcd and address 3
Apr 12 20:30:32 ubuntu kernel: [    7.054679] usb 3-2: configuration #1 chosen from 1 choice
Apr 12 20:30:32 ubuntu kernel: [    7.070901] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input3
Apr 12 20:30:32 ubuntu kernel: [    7.081755] generic-usb 0003:046D:C018.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:10.1-2/input0
Apr 12 20:30:32 ubuntu kernel: [    7.670865] xor: automatically using best checksumming function: pIII_sse
Apr 12 20:30:32 ubuntu kernel: [    7.690763]    pIII_sse  :  3205.000 MB/sec
Apr 12 20:30:32 ubuntu kernel: [    7.690767] xor: using function: pIII_sse (3205.000 MB/sec)
Apr 12 20:30:32 ubuntu kernel: [    7.719150] device-mapper: dm-raid45: initialized v0.2594b
Apr 12 20:30:32 ubuntu kernel: [    8.304799] EXT4-fs (sda10): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    8.441571] EXT4-fs (sda11): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    8.673517] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    8.807663] EXT4-fs (sda7): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    8.970423] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [    9.106669] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 12 20:30:32 ubuntu kernel: [   10.635451] ISO 9660 Extensions: Microsoft Joliet Level 3
Apr 12 20:30:32 ubuntu kernel: [   10.673322] ISO 9660 Extensions: RRIP_1991A
Apr 12 20:30:32 ubuntu kernel: [   10.853746] aufs 2-standalone.tree-20091207
Apr 12 20:30:32 ubuntu kernel: [   11.030823] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Apr 12 20:30:32 ubuntu kernel: [   49.094316] Adding 514040k swap on /dev/sda5.  Priority:-1 extents:1 across:514040k 
Apr 12 20:30:32 ubuntu kernel: [   50.485993] udev: starting version 151
Apr 12 20:30:35 ubuntu kernel: [   53.007269] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Successfully dropped root privileges.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: avahi-daemon 0.6.25 starting up.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Successfully called chroot().
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Successfully dropped remaining capabilities.
Apr 12 20:30:36 ubuntu avahi-daemon[1341]: chroot.c: open() failed: No such file or directory
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Failed to open /etc/resolv.conf: Invalid argument
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: No service file found in /etc/avahi/services.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Network interface enumeration completed.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 12 20:30:36 ubuntu avahi-daemon[1335]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2162424758.
Apr 12 20:30:36 ubuntu NetworkManager: <info>  starting...
Apr 12 20:30:36 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Apr 12 20:30:38 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0d.0/net/eth0, iface: eth0)
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0d.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth1, iface: eth1)
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 12 20:30:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Apr 12 20:30:38 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 12 20:30:39 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 12 20:30:39 ubuntu NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Apr 12 20:30:39 ubuntu NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Apr 12 20:30:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: (138292560) ... get_connections.
Apr 12 20:30:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: (138292560) ... get_connections (managed=false): return empty list.
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin AnyData
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Generic
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Gobi
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Option High-Speed
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Huawei
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Longcheer
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Ericsson MBM
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin MotoC
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Nokia
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Novatel
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Option
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin Sierra
Apr 12 20:30:39 ubuntu modem-manager: Loaded plugin ZTE
Apr 12 20:30:39 ubuntu kernel: [   57.427684] CA0106 0000:00:0a.0: found PCI INT A -> IRQ 5
Apr 12 20:30:39 ubuntu kernel: [   57.427713] CA0106 0000:00:0a.0: sharing IRQ 5 with 0000:00:10.4
Apr 12 20:30:39 ubuntu kernel: [   57.427721] CA0106 0000:00:0a.0: sharing IRQ 5 with 0000:00:11.5
Apr 12 20:30:39 ubuntu kernel: [   57.427726] CA0106 0000:00:0a.0: sharing IRQ 5 with 0000:00:11.6
Apr 12 20:30:39 ubuntu kernel: [   57.427758] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
Apr 12 20:30:39 ubuntu kernel: [   57.491946] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
Apr 12 20:30:39 ubuntu kernel: [   57.491959] VIA 82xx Modem 0000:00:11.6: found PCI INT C -> IRQ 5
Apr 12 20:30:39 ubuntu kernel: [   57.491971] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:0a.0
Apr 12 20:30:39 ubuntu kernel: [   57.491988] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:10.4
Apr 12 20:30:39 ubuntu kernel: [   57.491996] VIA 82xx Modem 0000:00:11.6: sharing IRQ 5 with 0000:00:11.5
Apr 12 20:30:39 ubuntu kernel: [   57.492008] VIA 82xx Modem 0000:00:11.6: VIA VLink IRQ fixup, from 0 to 5
Apr 12 20:30:40 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): now managed
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): preparing device.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 12 20:30:40 ubuntu kernel: [   57.609724] r8169: eth0: link down
Apr 12 20:30:40 ubuntu kernel: [   57.609932] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 12 20:30:40 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:0d.0/net/eth0
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): carrier is OFF
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'via-rhine')
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): now managed
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): bringing up device.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): preparing device.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Apr 12 20:30:40 ubuntu kernel: [   57.617768] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 12 20:30:40 ubuntu NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:12.0/net/eth1
Apr 12 20:30:40 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth1, iface: eth1)
Apr 12 20:30:40 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): carrier now ON (device state 2)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  modem-manager is now available
Apr 12 20:30:40 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Apr 12 20:30:40 ubuntu NetworkManager: <info>  dhclient started with pid 1480
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Apr 12 20:30:40 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 12 20:30:40 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 12 20:30:40 ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 12 20:30:40 ubuntu dhclient: All rights reserved.
Apr 12 20:30:40 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 12 20:30:40 ubuntu dhclient: 
Apr 12 20:30:40 ubuntu kernel: [   58.242657] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
Apr 12 20:30:41 ubuntu kernel: [   58.746876] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
Apr 12 20:30:41 ubuntu kernel: [   58.747133] VIA 82xx Audio 0000:00:11.5: enabling device (0000 -> 0001)
Apr 12 20:30:41 ubuntu kernel: [   58.747145] VIA 82xx Audio 0000:00:11.5: found PCI INT C -> IRQ 5
Apr 12 20:30:41 ubuntu kernel: [   58.747156] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:0a.0
Apr 12 20:30:41 ubuntu kernel: [   58.747176] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:10.4
Apr 12 20:30:41 ubuntu kernel: [   58.747184] VIA 82xx Audio 0000:00:11.5: sharing IRQ 5 with 0000:00:11.6
Apr 12 20:30:41 ubuntu kernel: [   58.747194] VIA 82xx Audio 0000:00:11.5: VIA VLink IRQ fixup, from 0 to 5
Apr 12 20:30:41 ubuntu kernel: [   58.747342] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
Apr 12 20:30:41 ubuntu NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
Apr 12 20:30:41 ubuntu dhclient: Listening on LPF/eth1/00:0e:a6:bd:8d:ae
Apr 12 20:30:41 ubuntu dhclient: Sending on   LPF/eth1/00:0e:a6:bd:8d:ae
Apr 12 20:30:41 ubuntu dhclient: Sending on   Socket/fallback
Apr 12 20:30:41 ubuntu avahi-daemon[1335]: Registering new address record for fe80::20e:a6ff:febd:8dae on eth1.*.
Apr 12 20:30:41 ubuntu kernel: [   59.261873] codec_read: codec 0 is not valid [0x107e5370]
Apr 12 20:30:41 ubuntu kernel: [   59.268896] codec_read: codec 0 is not valid [0x107e5370]
Apr 12 20:30:41 ubuntu kernel: [   59.276143] codec_read: codec 0 is not valid [0x107e5370]
Apr 12 20:30:41 ubuntu kernel: [   59.283568] codec_read: codec 0 is not valid [0x107e5370]
Apr 12 20:30:45 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 12 20:30:45 ubuntu dhclient: DHCPOFFER of 192.168.1.112 from 192.168.1.1
Apr 12 20:30:45 ubuntu dhclient: DHCPREQUEST of 192.168.1.112 on eth1 to 255.255.255.255 port 67
Apr 12 20:30:45 ubuntu dhclient: DHCPACK of 192.168.1.112 from 192.168.1.1
Apr 12 20:30:45 ubuntu NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Apr 12 20:30:45 ubuntu NetworkManager: <info>    address 192.168.1.112
Apr 12 20:30:45 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Apr 12 20:30:45 ubuntu NetworkManager: <info>    gateway 192.168.1.1
Apr 12 20:30:45 ubuntu NetworkManager: <info>    hostname 'ubuntu'
Apr 12 20:30:45 ubuntu NetworkManager: <info>    nameserver '192.168.1.1'
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 12 20:30:45 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Apr 12 20:30:45 ubuntu avahi-daemon[1335]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.112.
Apr 12 20:30:45 ubuntu dhclient: bound to 192.168.1.112 -- renewal in 35826 seconds.
Apr 12 20:30:45 ubuntu avahi-daemon[1335]: New relevant interface eth1.IPv4 for mDNS.
Apr 12 20:30:45 ubuntu avahi-daemon[1335]: Registering new address record for 192.168.1.112 on eth1.IPv4.
Apr 12 20:30:46 ubuntu cron[1687]: (CRON) INFO (pidfile fd = 3)
Apr 12 20:30:46 ubuntu acpid: starting up with netlink and the input layer
Apr 12 20:30:46 ubuntu cron[1722]: (CRON) STARTUP (fork ok)
Apr 12 20:30:46 ubuntu NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Apr 12 20:30:46 ubuntu NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
Apr 12 20:30:46 ubuntu NetworkManager: <info>  Activation (eth1) successful, device activated.
Apr 12 20:30:46 ubuntu NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Apr 12 20:30:46 ubuntu cron[1722]: (CRON) INFO (Running @reboot jobs)
Apr 12 20:30:46 ubuntu acpid: 39 rules loaded
Apr 12 20:30:46 ubuntu acpid: waiting for events: event logging is off
Apr 12 20:30:46 ubuntu acpid: client connected from 1497[0:0]
Apr 12 20:30:46 ubuntu acpid: 1 client rule loaded
Apr 12 20:30:48 ubuntu kernel: [   65.612273] [TTM] Zone  kernel: Available graphics memory: 436968 kiB.
Apr 12 20:30:48 ubuntu kernel: [   65.612279] [TTM] Zone highmem: Available graphics memory: 1030476 kiB.
Apr 12 20:30:48 ubuntu kernel: [   65.612302] [drm] nouveau 0000:01:00.0: 256 MiB VRAM
Apr 12 20:30:48 ubuntu kernel: [   65.612391] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Apr 12 20:30:48 ubuntu kernel: [   65.612409] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Apr 12 20:30:48 ubuntu kernel: [   65.612418] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 12 20:30:48 ubuntu kernel: [   65.612498] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 12 20:30:48 ubuntu kernel: [   65.612502] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
Apr 12 20:30:48 ubuntu kernel: [   65.612777] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
Apr 12 20:30:48 ubuntu kernel: [   65.613572] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
Apr 12 20:30:48 ubuntu kernel: [   65.613789] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 0
Apr 12 20:30:48 ubuntu kernel: [   65.614505] [TTM] Zone  kernel: Used memory at exit: 0 kiB.
Apr 12 20:30:48 ubuntu kernel: [   65.614513] [TTM] Zone highmem: Used memory at exit: 0 kiB.
Apr 12 20:30:48 ubuntu kernel: [   66.164839] lp: driver loaded but no devices found
Apr 12 20:30:48 ubuntu kernel: [   66.340891] ppdev: user-space parallel port driver
Apr 12 20:30:50 ubuntu udev-configure-printer: add /module/lp
Apr 12 20:30:50 ubuntu udev-configure-printer: Failed to get parent
Apr 12 20:30:50 ubuntu kernel: [   68.202618] eth1: no IPv6 routers present
Apr 13 00:30:53 ubuntu ntpdate[2182]: step time server 91.189.94.4 offset 14399.109129 sec
Apr 13 00:30:53 ubuntu console-kit-daemon[2184]: WARNING: The program /usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck didn't exit within 15 seconds; killing it
Apr 13 00:30:57 ubuntu console-kit-daemon[2184]: last message repeated 3 times
Apr 13 00:30:57 ubuntu init: plymouth-stop pre-start process (2511) terminated with status 1
Apr 13 00:31:04 ubuntu ubiquity[2608]: Ubiquity 2.2.15
Apr 13 00:31:11 ubuntu ubiquity[2608]: log-output -t ubiquity laptop-detect
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Sucessfully called chroot.
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Sucessfully dropped privileges.
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Sucessfully limited resources.
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Running.
Apr 13 00:31:21 ubuntu ubiquity[2608]: log-output -t ubiquity laptop-detect
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Watchdog thread running.
Apr 13 00:31:21 ubuntu rtkit-daemon[2633]: Canary thread running.
Apr 13 00:31:22 ubuntu polkitd[2642]: started daemon version 0.96 using authority implementation `local' version `0.96'
Apr 13 00:31:28 ubuntu ubiquity[2608]: switched to page language
Apr 13 00:31:32 ubuntu ubiquity[2608]: switched to page language
Apr 13 00:31:39 ubuntu localechooser: info: Language = 'en'
Apr 13 00:31:39 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/language = 'en'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Apr 13 00:31:39 ubuntu localechooser: info: Default country = 'US'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/country = 'US'
Apr 13 00:31:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 13 00:31:39 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Apr 13 00:31:42 ubuntu ubiquity[2608]: debconffilter_done: ubi-language (current: ubi-language)
Apr 13 00:31:42 ubuntu ubiquity[2608]: Step_before = stepLanguage
Apr 13 00:31:46 ubuntu clock-setup: Tue Apr 13 00:31:46 UTC 2010
Apr 13 00:31:46 ubuntu clock-setup: rdate: adjust local clock by 0.001576 seconds
Apr 13 00:31:47 ubuntu ubiquity[2608]: switched to page timezone
Apr 13 00:32:19 ubuntu localechooser: info: Locale has been preseeded to en_CA.UTF-8
Apr 13 00:32:19 ubuntu localechooser: info: Set localechooser/languagelist = 'en'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/country = 'CA'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/locale = 'en_CA.UTF-8'
Apr 13 00:32:19 ubuntu localechooser: info: Language = 'en'
Apr 13 00:32:19 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/language = 'en'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Apr 13 00:32:19 ubuntu localechooser: info: Default country = 'US'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/country = 'CA'
Apr 13 00:32:19 ubuntu localechooser: info: Set debian-installer/locale = 'en_CA.UTF-8'
Apr 13 00:32:19 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_CA.UTF-8'
Apr 13 00:32:20 ubuntu kernel: [  158.975008] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Apr 13 00:32:20 ubuntu kernel: [  158.982938] SGI XFS Quota Management subsystem
Apr 13 00:32:20 ubuntu kernel: [  159.063605] JFS: nTxBlock = 8192, nTxLock = 65536
Apr 13 00:32:20 ubuntu kernel: [  159.175518] NTFS driver 2.1.29 [Flags: R/O MODULE].
Apr 13 00:32:20 ubuntu kernel: [  159.378952] QNX4 filesystem 0.2.3 registered.
Apr 13 00:32:21 ubuntu kernel: [  159.752969] Btrfs loaded
Apr 13 00:32:21 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Version 2010.3.6 external FUSE 28
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Cmdline options: ro
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Mount options: ro,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Apr 13 00:32:21 ubuntu ntfs-3g[3737]: Ownership and permissions disabled, configuration type 1
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: mounted as ntfs-3g filesystem
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:21 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:21 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:21 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Apr 13 00:32:21 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:21 ubuntu 20microsoft: debug: /dev/sda1 is a NTFS partition
Apr 13 00:32:22 ubuntu 20microsoft: result: /dev/sda1:Windows 7 (loader):Windows:chain
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:22 ubuntu ntfs-3g[3737]: Unmounting /dev/sda1 ()
Apr 13 00:32:22 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda10
Apr 13 00:32:22 ubuntu kernel: [  160.616538] EXT4-fs (sda10): mounted filesystem with ordered data mode
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:22 ubuntu 10freedos: debug: /dev/sda10 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:22 ubuntu 10qnx: debug: /dev/sda10 is not a QNX4 partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:22 ubuntu macosx-prober: debug: /dev/sda10 is not an HFS+ partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:22 ubuntu 20microsoft: debug: /dev/sda10 is not a MS partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:22 ubuntu 30utility: debug: /dev/sda10 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda11
Apr 13 00:32:22 ubuntu kernel: [  160.828507] EXT4-fs (sda11): mounted filesystem with ordered data mode
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:22 ubuntu 10freedos: debug: /dev/sda11 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:22 ubuntu 10qnx: debug: /dev/sda11 is not a QNX4 partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:22 ubuntu macosx-prober: debug: /dev/sda11 is not an HFS+ partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:22 ubuntu 20microsoft: debug: /dev/sda11 is not a MS partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:22 ubuntu 30utility: debug: /dev/sda11 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Apr 13 00:32:22 ubuntu kernel: [  161.032952] You didn't specify the type of your ufs filesystem
Apr 13 00:32:22 ubuntu kernel: [  161.032955] 
Apr 13 00:32:22 ubuntu kernel: [  161.032956] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Apr 13 00:32:22 ubuntu kernel: [  161.032959] 
Apr 13 00:32:22 ubuntu kernel: [  161.032960] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Apr 13 00:32:22 ubuntu kernel: [  161.033281] ufs_read_super: bad magic number
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
Apr 13 00:32:22 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Apr 13 00:32:22 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:22 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Apr 13 00:32:22 ubuntu kernel: [  161.226776] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:22 ubuntu 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:22 ubuntu 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:22 ubuntu macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:22 ubuntu 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:22 ubuntu 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:22 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu 90linux-distro: result: /dev/sda6:openSUSE 11.2 (i586):SuSE:linux
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:23 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda7
Apr 13 00:32:23 ubuntu kernel: [  161.527216] EXT4-fs (sda7): mounted filesystem with ordered data mode
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:23 ubuntu 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:23 ubuntu 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:23 ubuntu macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:23 ubuntu 20microsoft: debug: /dev/sda7 is not a MS partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:23 ubuntu 30utility: debug: /dev/sda7 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:32:23 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda8
Apr 13 00:32:23 ubuntu kernel: [  161.731596] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:23 ubuntu 10freedos: debug: /dev/sda8 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:23 ubuntu 10qnx: debug: /dev/sda8 is not a QNX4 partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:23 ubuntu macosx-prober: debug: /dev/sda8 is not an HFS+ partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:23 ubuntu 20microsoft: debug: /dev/sda8 is not a MS partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:23 ubuntu 30utility: debug: /dev/sda8 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu 90linux-distro: result: /dev/sda8:Fedora release 12 (Constantine):Fedora:linux
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:32:23 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda9
Apr 13 00:32:23 ubuntu kernel: [  162.042443] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:32:23 ubuntu 10freedos: debug: /dev/sda9 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:32:23 ubuntu 10qnx: debug: /dev/sda9 is not a QNX4 partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:32:23 ubuntu macosx-prober: debug: /dev/sda9 is not an HFS+ partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:32:23 ubuntu 20microsoft: debug: /dev/sda9 is not a MS partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:32:23 ubuntu 30utility: debug: /dev/sda9 is not a FAT partition: exiting
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:32:23 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:32:23 ubuntu ubiquity[2608]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Apr 13 00:32:23 ubuntu ubiquity[2608]: Step_before = stepLocation
Apr 13 00:32:24 ubuntu ubiquity[2608]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Apr 13 00:32:24 ubuntu ubiquity[2608]: switched to page console_setup
Apr 13 00:32:48 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Apr 13 00:32:48 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Apr 13 00:32:48 ubuntu ubiquity[2608]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Apr 13 00:32:48 ubuntu ubiquity[2608]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Apr 13 00:32:48 ubuntu ubiquity[2608]: Step_before = stepKeyboardConf
Apr 13 00:32:48 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda2 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda10 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda11 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda7 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: Device /dev/sda9 not found in os-prober output
Apr 13 00:32:53 ubuntu ubiquity[2608]: switched to page partman
Apr 13 00:33:04 ubuntu ubiquity[2608]: switched to page partman
Apr 13 00:33:09 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Apr 13 00:33:09 ubuntu ntfsresize: Device name        : /dev/sda1
Apr 13 00:33:09 ubuntu ntfsresize: NTFS volume version: 3.1
Apr 13 00:33:09 ubuntu ntfsresize: Cluster size       : 4096 bytes
Apr 13 00:33:09 ubuntu ntfsresize: Current volume size: 35031433728 bytes (35032 MB)
Apr 13 00:33:09 ubuntu ntfsresize: Current device size: 35031435264 bytes (35032 MB)
Apr 13 00:33:09 ubuntu ntfsresize: Checking filesystem consistency ...
Apr 13 00:33:09 ubuntu ntfsresize: Accounting clusters ...
Apr 13 00:33:09 ubuntu ntfsresize: Space in use       : 11357 MB (32.4%)
Apr 13 00:33:09 ubuntu ntfsresize: Collecting resizing constraints ...
Apr 13 00:33:09 ubuntu ntfsresize: You might resize at 11356598272 bytes or 11357 MB (freeing 23675 MB).
Apr 13 00:33:09 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Apr 13 00:33:10 ubuntu ubiquity[2608]: switched to page partman
Apr 13 00:33:46 ubuntu ubiquity[2608]: last message repeated 3 times
Apr 13 00:33:46 ubuntu ubiquity[2608]: switched to page partman
Apr 13 00:34:25 ubuntu ubiquity[2608]: debconffilter_done: ubi-partman (current: ubi-partman)
Apr 13 00:34:25 ubuntu ubiquity[2608]: Step_before = stepPartAdvanced
Apr 13 00:34:25 ubuntu ubiquity[2608]: switched to page usersetup
Apr 13 00:34:57 ubuntu ubiquity[2608]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Apr 13 00:34:57 ubuntu ubiquity[2608]: Step_before = stepUserInfo
Apr 13 00:34:57 ubuntu ubiquity[2608]: filtering out /dev/sda5 as it is to be formatted.
Apr 13 00:34:57 ubuntu ubiquity[2608]: filtering out /dev/sda10 as it is to be formatted.
Apr 13 00:34:57 ubuntu ubiquity[2608]: filtering out /dev/sda11 as it is to be formatted.
Apr 13 00:34:57 ubuntu migration-assistant: info: setting ostype from: '/dev/sda1:Windows 7 (loader):Windows:chain'
Apr 13 00:34:57 ubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Version 2010.3.6 external FUSE 28
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Mounted /dev/sda1 (Read-Write, label "", NTFS 3.1)
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Cmdline options: rw,umask=0022,nls=utf8
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096,default_permissions
Apr 13 00:34:57 ubuntu ntfs-3g[9599]: Global ownership and permissions enforced, configuration type 1
profilesdir: /mnt/migrationassistant/Users
profilesdir: /mnt/migrationassistant/Users
Apr 13 00:34:59 ubuntu ntfs-3g[9599]: Unmounting /dev/sda1 ()
Apr 13 00:34:59 ubuntu migration-assistant: info: setting ostype from: '/dev/sda6:openSUSE 11.2 (i586):SuSE:linux'
Apr 13 00:34:59 ubuntu migration-assistant: info: got ostype of: 'linux', mountpoint is: '/mnt/migrationassistant'
Apr 13 00:34:59 ubuntu kernel: [  317.572043] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 13 00:34:59 ubuntu kernel: [  317.788885] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:34:59 ubuntu migration-assistant: info: setting ostype from: '/dev/sda8:Fedora release 12 (Constantine):Fedora:linux'
Apr 13 00:34:59 ubuntu migration-assistant: info: got ostype of: 'linux', mountpoint is: '/mnt/migrationassistant'
Apr 13 00:34:59 ubuntu kernel: [  318.284626] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 13 00:35:00 ubuntu kernel: [  318.454185] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:35:00 ubuntu ubiquity[2608]: switched to page migrationassistant
Apr 13 00:35:34 ubuntu ubiquity[2608]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Apr 13 00:35:34 ubuntu ubiquity[2608]: Step_before = stepMigrationAssistant
Apr 13 00:35:35 ubuntu ubiquity[2608]: switched to page summary
Apr 13 00:36:12 ubuntu ubiquity[2608]: debconffilter_done: ubi-summary (current: ubi-summary)
Apr 13 00:36:12 ubuntu ubiquity[2608]: Step_before = stepReady
Apr 13 00:36:12 ubuntu ubiquity[2608]: progress_loop()
Apr 13 00:36:20 ubuntu partman: mke2fs 1.41.11 (14-Mar-2010)
Apr 13 00:36:26 ubuntu partman: mke2fs 1.41.11 (14-Mar-2010)
Apr 13 00:36:32 ubuntu kernel: [  410.597422] EXT4-fs (sda10): mounted filesystem with ordered data mode
Apr 13 00:36:32 ubuntu kernel: [  410.676365] EXT4-fs (sda11): mounted filesystem with ordered data mode
Apr 13 00:36:33 ubuntu ubiquity[2608]: debconffilter_done: ubiquity.components.partman_commit (current: None)
Apr 13 00:36:33 ubuntu python: keeping packages due to preseeding: icedtea6-plugin openoffice.org
Apr 13 00:36:33 ubuntu python: keeping language packs for: en
Apr 13 00:42:49 ubuntu ubiquity: umount: /target/cdrom: not found
Apr 13 00:42:49 ubuntu ubiquity: 
Apr 13 00:42:49 ubuntu python: log-output -t ubiquity umount /target/cdrom
Apr 13 00:42:49 ubuntu python: log-output -t ubiquity mount --bind /cdrom /target/cdrom
Apr 13 00:42:53 ubuntu ubiquity: /usr/lib/ubiquity/apt-setup/generators/01setup: 7: 
Apr 13 00:42:53 ubuntu ubiquity: cannot open /target/etc/apt/sources.list: No such file
Apr 13 00:42:53 ubuntu ubiquity: 
Apr 13 00:42:56 ubuntu in-target: Reading package lists...
Apr 13 00:42:56 ubuntu in-target: 
Apr 13 00:42:57 ubuntu apt-setup: Using CD-ROM mount point /cdrom/
Apr 13 00:42:57 ubuntu apt-setup: Identifying.. 
Apr 13 00:42:57 ubuntu apt-setup: [23edb90d1038bf5e9143793ff3e4a7d0-2]
Apr 13 00:42:57 ubuntu apt-setup: Scanning disc for index files..
Apr 13 00:42:57 ubuntu apt-setup: Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Apr 13 00:42:57 ubuntu apt-setup: Found label 'Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)'
Apr 13 00:42:57 ubuntu apt-setup: This disc is called: 
Apr 13 00:42:57 ubuntu apt-setup: 'Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)'
Apr 13 00:42:57 ubuntu apt-setup: Copying package lists...
Apr 13 00:42:57 ubuntu apt-setup: gpgv: 
Apr 13 00:42:57 ubuntu apt-setup: Signature made Tue 06 Apr 2010 08:23:09 PM UTC using DSA key ID FBB75451
Apr 13 00:42:57 ubuntu apt-setup: gpgv: 
Apr 13 00:42:57 ubuntu apt-setup: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Apr 13 00:42:57 ubuntu apt-setup: 
Apr 13 00:42:57 ubuntu apt-setup: #015Reading Package Indexes... 0%#015#015Reading Package Indexes... 2%#015
Apr 13 00:42:57 ubuntu apt-setup: #015Reading Package Indexes... Done#015
Apr 13 00:42:57 ubuntu apt-setup: Writing new source list
Apr 13 00:42:57 ubuntu apt-setup: Source list entries for this disc are:
Apr 13 00:42:57 ubuntu apt-setup: deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)]/ lucid main restricted
Apr 13 00:42:57 ubuntu apt-setup: Repeat this process for the rest of the CDs in your set.
Apr 13 00:42:57 ubuntu apt-setup: W: Skipping nonexistent file /cdrom/dists/lucid/main/binary-i386/Packages
Apr 13 00:42:57 ubuntu apt-setup: W: Skipping nonexistent file /cdrom/dists/lucid/restricted/binary-i386/Packages
Apr 13 00:42:59 ubuntu in-target: Ign cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)/ lucid/main Translation-en_CA
Apr 13 00:42:59 ubuntu in-target: Ign cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)/ lucid/restricted Translation-en_CA
Apr 13 00:42:59 ubuntu in-target: Reading package lists...
Apr 13 00:42:59 ubuntu in-target: 
Apr 13 00:43:00 ubuntu choose-mirror[11264]: INFO: base system installable from CD; skipping mirror check
Apr 13 00:43:00 ubuntu choose-mirror[11264]: INFO: falling back to codename lucid
Apr 13 00:43:02 ubuntu in-target: Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg [189B]
Apr 13 00:43:02 ubuntu in-target: Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA [10.3kB]
Apr 13 00:43:02 ubuntu in-target: Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA [425B]
Apr 13 00:43:02 ubuntu in-target: Get:4 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA [663B]
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Apr 13 00:43:02 ubuntu in-target: Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release [57.2kB]
Apr 13 00:43:02 ubuntu in-target: Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release
Apr 13 00:43:03 ubuntu in-target: Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages [1,379kB]
Apr 13 00:43:06 ubuntu in-target: Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages [6,211B]
Apr 13 00:43:06 ubuntu in-target: Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources [652kB]
Apr 13 00:43:07 ubuntu in-target: Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources [3,774B]
Apr 13 00:43:07 ubuntu in-target: Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages [5,477kB]
Apr 13 00:43:18 ubuntu in-target: Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources [3,178kB]
Apr 13 00:43:24 ubuntu in-target: Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages [179kB]
Apr 13 00:43:24 ubuntu in-target: Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources [117kB]
Apr 13 00:43:25 ubuntu in-target: Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages [14B]
Apr 13 00:43:25 ubuntu in-target: Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages [14B]
Apr 13 00:43:25 ubuntu in-target: Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources [14B]
Apr 13 00:43:25 ubuntu in-target: Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources [14B]
Apr 13 00:43:25 ubuntu in-target: Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages [14B]
Apr 13 00:43:25 ubuntu in-target: Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources [14B]
Apr 13 00:43:25 ubuntu in-target: Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages [14B]
Apr 13 00:43:25 ubuntu in-target: Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources [14B]
Apr 13 00:43:29 ubuntu in-target: Fetched 11.1MB in 28s (395kB/s)
Apr 13 00:43:29 ubuntu in-target: Reading package lists...
Apr 13 00:43:33 ubuntu in-target: 
Apr 13 00:43:34 ubuntu in-target: Reading package lists...
Apr 13 00:43:34 ubuntu in-target: 
Apr 13 00:43:36 ubuntu in-target: Reading package lists...
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Apr 13 00:43:38 ubuntu in-target: Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Apr 13 00:43:38 ubuntu in-target: Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Apr 13 00:43:38 ubuntu in-target: Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Apr 13 00:43:38 ubuntu in-target: Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Apr 13 00:43:38 ubuntu in-target: Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Apr 13 00:43:38 ubuntu in-target: Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [14B]
Apr 13 00:43:38 ubuntu in-target: Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [14B]
Apr 13 00:43:38 ubuntu in-target: Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [14B]
Apr 13 00:43:38 ubuntu in-target: Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [14B]
Apr 13 00:43:38 ubuntu in-target: Fetched 56B in 0s (68B/s)
Apr 13 00:43:38 ubuntu in-target: Reading package lists...
Apr 13 00:43:39 ubuntu in-target: 
Apr 13 00:43:39 ubuntu localechooser: Generating locales...
Apr 13 00:43:39 ubuntu localechooser:   en_CA.UTF-8... 
Apr 13 00:43:42 ubuntu localechooser: done
Apr 13 00:43:42 ubuntu localechooser: Generation complete.
Apr 13 00:43:42 ubuntu localechooser: Generating locales...
Apr 13 00:43:42 ubuntu localechooser:   en_US.UTF-8... 
Apr 13 00:43:45 ubuntu localechooser: done
Apr 13 00:43:45 ubuntu localechooser: Generation complete.
Apr 13 00:43:46 ubuntu python: log-output -t ubiquity chroot /target fontconfig-voodoo --auto --force --quiet
Apr 13 00:43:47 ubuntu clock-setup: hwclock from util-linux-ng 2.17.2
Apr 13 00:43:47 ubuntu clock-setup: Using /dev interface to clock.
Apr 13 00:43:47 ubuntu clock-setup: Assuming hardware clock is kept in local time.
Apr 13 00:43:47 ubuntu clock-setup: Time elapsed since reference time has been 0.685476 seconds.
Apr 13 00:43:47 ubuntu clock-setup: Delaying further to reach the new time.
Apr 13 00:43:47 ubuntu clock-setup: Setting Hardware Clock to 20:43:47 = 1271119427 seconds since 1969
Apr 13 00:43:47 ubuntu clock-setup: ioctl(RTC_SET_TIME) was successful.
Apr 13 00:43:52 ubuntu user-setup: Shadow passwords are now on.
Apr 13 00:43:52 ubuntu user-setup: Adding user `tt888' ...
Apr 13 00:43:52 ubuntu user-setup: Adding new group `tt888' (1000) ...
Apr 13 00:43:52 ubuntu user-setup: Adding new user `tt888' (1000) with group `tt888' ...
Apr 13 00:43:53 ubuntu user-setup: Creating home directory `/home/tt888' ...
Apr 13 00:43:53 ubuntu user-setup: Copying files from `/etc/skel' ...
Apr 13 00:43:54 ubuntu user-setup: addgroup: 
Apr 13 00:43:54 ubuntu user-setup: The group `lpadmin' already exists as a system group. Exiting.
Apr 13 00:43:54 ubuntu user-setup: Adding group `sambashare' (GID 122) ...
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:54 ubuntu user-setup: Adding user `tt888' to group `adm' ...
Apr 13 00:43:54 ubuntu user-setup: Adding user tt888 to group adm
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:54 ubuntu user-setup: Adding user `tt888' to group `cdrom' ...
Apr 13 00:43:54 ubuntu user-setup: Adding user tt888 to group cdrom
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:54 ubuntu user-setup: Adding user `tt888' to group `dialout' ...
Apr 13 00:43:54 ubuntu user-setup: Adding user tt888 to group dialout
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:54 ubuntu user-setup: Adding user `tt888' to group `lpadmin' ...
Apr 13 00:43:54 ubuntu user-setup: Adding user tt888 to group lpadmin
Apr 13 00:43:54 ubuntu user-setup: Done.
Apr 13 00:43:55 ubuntu user-setup: Adding user `tt888' to group `plugdev' ...
Apr 13 00:43:55 ubuntu user-setup: Adding user tt888 to group plugdev
Apr 13 00:43:55 ubuntu user-setup: Done.
Apr 13 00:43:55 ubuntu user-setup: Adding user `tt888' to group `sambashare' ...
Apr 13 00:43:55 ubuntu user-setup: Adding user tt888 to group sambashare
Apr 13 00:43:55 ubuntu user-setup: Done.
Apr 13 00:43:55 ubuntu user-setup: addgroup: 
Apr 13 00:43:55 ubuntu user-setup: The group `admin' already exists as a system group. Exiting.
Apr 13 00:43:55 ubuntu user-setup: Adding user `tt888' to group `admin' ...
Apr 13 00:43:55 ubuntu user-setup: Adding user tt888 to group admin
Apr 13 00:43:55 ubuntu user-setup: Done.
Apr 13 00:43:57 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Version 2010.3.6 external FUSE 28
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Mounted /dev/sda1 (Read-Only, label "", NTFS 3.1)
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Cmdline options: ro
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Mount options: ro,silent,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Ownership and permissions disabled, configuration type 1
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: mounted as ntfs-3g filesystem
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:58 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:58 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:58 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:58 ubuntu 20microsoft: debug: /dev/sda1 is a NTFS partition
Apr 13 00:43:58 ubuntu 20microsoft: result: /dev/sda1:Windows 7 (loader):Windows:chain
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:58 ubuntu ntfs-3g[12421]: Unmounting /dev/sda1 ()
Apr 13 00:43:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda11
Apr 13 00:43:58 ubuntu 10freedos: debug: /dev/sda11 is not a FAT partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda11
Apr 13 00:43:58 ubuntu 10qnx: debug: /dev/sda11 is not a QNX4 partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda11
Apr 13 00:43:58 ubuntu macosx-prober: debug: /dev/sda11 is not an HFS+ partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda11
Apr 13 00:43:58 ubuntu 20microsoft: debug: /dev/sda11 is not a MS partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda11
Apr 13 00:43:58 ubuntu 30utility: debug: /dev/sda11 is not a FAT partition: exiting
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda11
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Apr 13 00:43:58 ubuntu kernel: [  857.227777] You didn't specify the type of your ufs filesystem
Apr 13 00:43:58 ubuntu kernel: [  857.227780] 
Apr 13 00:43:58 ubuntu kernel: [  857.227781] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Apr 13 00:43:58 ubuntu kernel: [  857.227783] 
Apr 13 00:43:58 ubuntu kernel: [  857.227784] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Apr 13 00:43:58 ubuntu kernel: [  857.228126] ufs_read_super: bad magic number
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
Apr 13 00:43:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Apr 13 00:43:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Apr 13 00:43:58 ubuntu kernel: [  857.347926] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:58 ubuntu 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:58 ubuntu 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Apr 13 00:43:58 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:59 ubuntu macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:59 ubuntu 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:43:59 ubuntu 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu 90linux-distro: result: /dev/sda6:openSUSE 11.2 (i586):SuSE:linux
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:59 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda7
Apr 13 00:43:59 ubuntu kernel: [  857.598473] EXT4-fs (sda7): mounted filesystem with ordered data mode
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:59 ubuntu 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:59 ubuntu 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:59 ubuntu macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:59 ubuntu 20microsoft: debug: /dev/sda7 is not a MS partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:43:59 ubuntu 30utility: debug: /dev/sda7 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:43:59 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda8
Apr 13 00:43:59 ubuntu kernel: [  857.786193] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:59 ubuntu 10freedos: debug: /dev/sda8 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:59 ubuntu 10qnx: debug: /dev/sda8 is not a QNX4 partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:59 ubuntu macosx-prober: debug: /dev/sda8 is not an HFS+ partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:59 ubuntu 20microsoft: debug: /dev/sda8 is not a MS partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:43:59 ubuntu 30utility: debug: /dev/sda8 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu 90linux-distro: result: /dev/sda8:Fedora release 12 (Constantine):Fedora:linux
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 13 00:43:59 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda9
Apr 13 00:43:59 ubuntu kernel: [  858.080425] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: mounted as ext4 filesystem
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Apr 13 00:43:59 ubuntu 10freedos: debug: /dev/sda9 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Apr 13 00:43:59 ubuntu 10qnx: debug: /dev/sda9 is not a QNX4 partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Apr 13 00:43:59 ubuntu macosx-prober: debug: /dev/sda9 is not an HFS+ partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Apr 13 00:43:59 ubuntu 20microsoft: debug: /dev/sda9 is not a MS partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Apr 13 00:43:59 ubuntu 30utility: debug: /dev/sda9 is not a FAT partition: exiting
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 13 00:43:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 13 00:43:59 ubuntu kernel: [  858.354390] EXT4-fs (sda6): mounted filesystem with ordered data mode
Apr 13 00:44:00 ubuntu kernel: [  858.504685] EXT4-fs (sda9): mounted filesystem with ordered data mode
Apr 13 00:44:00 ubuntu kernel: [  858.626247] EXT4-fs (sda8): mounted filesystem with ordered data mode
Apr 13 00:44:00 ubuntu ubiquity: /usr/bin/casper-reconfigure: package 'gnome-power-manager' is not installed
Apr 13 00:44:02 ubuntu python: log-output -t ubiquity chroot /target mount -t proc proc /proc
Apr 13 00:44:02 ubuntu python: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Apr 13 00:44:02 ubuntu python: log-output -t ubiquity mount --bind /dev /target/dev
Apr 13 00:44:03 ubuntu hw-detect:  * No PCMCIA bridge module specified
Apr 13 00:44:05 ubuntu check-missing-firmware: no missing firmware in /tmp/missing-firmware
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity chroot /target umount /sys
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity chroot /target umount /proc
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity umount /target/dev
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity /usr/lib/ubiquity/debian-installer-utils/register-module.post-base-installer
Apr 13 00:44:06 ubuntu ubiquity: chroot: 
Apr 13 00:44:06 ubuntu ubiquity: cannot run command `debconf-communicate': No such file or directory
Apr 13 00:44:06 ubuntu ubiquity: umount: /target/cdrom: not found
Apr 13 00:44:06 ubuntu ubiquity: 
Apr 13 00:44:06 ubuntu python: log-output -t ubiquity umount /target/cdrom
Apr 13 00:44:06 ubuntu ubiquity: grep: 
Apr 13 00:44:06 ubuntu ubiquity: /target/etc/apt/sources.list
Apr 13 00:44:06 ubuntu ubiquity: : No such file or directory
Apr 13 00:44:06 ubuntu ubiquity: 
Apr 13 00:44:06 ubuntu python: Exception during installation:
Apr 13 00:44:06 ubuntu python: Traceback (most recent call last):
Apr 13 00:44:06 ubuntu python:   File "/usr/share/ubiquity/install.py", line 2497, in <module>
Apr 13 00:44:06 ubuntu python:     install.run()
Apr 13 00:44:06 ubuntu python:   File "/usr/share/ubiquity/install.py", line 391, in run
Apr 13 00:44:06 ubuntu python:     self.configure_hardware()
Apr 13 00:44:06 ubuntu python:   File "/usr/share/ubiquity/install.py", line 1403, in configure_hardware
Apr 13 00:44:06 ubuntu python:     install_misc.set_debconf(self.target, 'popularity-contest/participate', participate, self.db)
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 70, in set_debconf
Apr 13 00:44:06 ubuntu python:     dc = debconf.Debconf(read=dccomm.stdout, write=dccomm.stdin)
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 53, in __init__
Apr 13 00:44:06 ubuntu python:     self.setUp(title)
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 56, in setUp
Apr 13 00:44:06 ubuntu python:     self.version = self.version(2)
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 65, in <lambda>
Apr 13 00:44:06 ubuntu python:     lambda *args, **kw: self.command(command, *args, **kw))
Apr 13 00:44:06 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 86, in command
Apr 13 00:44:06 ubuntu python:     status = int(status)
Apr 13 00:44:06 ubuntu python: ValueError: invalid literal for int() with base 10: ''
Apr 13 00:44:06 ubuntu python: 
Apr 13 00:44:06 ubuntu ubiquity[2608]: debconffilter_done: ubiquity.components.install (current: None)
Apr 13 00:44:06 ubuntu ubiquity[2608]: Exception in GTK frontend (invoking crash handler):
Apr 13 00:44:06 ubuntu ubiquity[2608]: Traceback (most recent call last):
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/bin/ubiquity", line 524, in <module>
Apr 13 00:44:06 ubuntu ubiquity[2608]:     main(oem_config)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/bin/ubiquity", line 511, in main
Apr 13 00:44:06 ubuntu ubiquity[2608]:     install(query=options.query)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/bin/ubiquity", line 242, in install
Apr 13 00:44:06 ubuntu ubiquity[2608]:     ret = wizard.run()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 508, in run
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.process_step()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1160, in process_step
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.progress_loop()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1043, in progress_loop
Apr 13 00:44:06 ubuntu ubiquity[2608]:     (ret, realtb))
Apr 13 00:44:06 ubuntu ubiquity[2608]: RuntimeError: Install failed with exit code 1
Apr 13 00:44:06 ubuntu ubiquity[2608]: Traceback (most recent call last):
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/share/ubiquity/install.py", line 2497, in <module>
Apr 13 00:44:06 ubuntu ubiquity[2608]:     install.run()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/share/ubiquity/install.py", line 391, in run
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.configure_hardware()
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/share/ubiquity/install.py", line 1403, in configure_hardware
Apr 13 00:44:06 ubuntu ubiquity[2608]:     install_misc.set_debconf(self.target, 'popularity-contest/participate', participate, self.db)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 70, in set_debconf
Apr 13 00:44:06 ubuntu ubiquity[2608]:     dc = debconf.Debconf(read=dccomm.stdout, write=dccomm.stdin)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 53, in __init__
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.setUp(title)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 56, in setUp
Apr 13 00:44:06 ubuntu ubiquity[2608]:     self.version = self.version(2)
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 65, in <lambda>
Apr 13 00:44:06 ubuntu ubiquity[2608]:     lambda *args, **kw: self.command(command, *args, **kw))
Apr 13 00:44:06 ubuntu ubiquity[2608]:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 86, in command
Apr 13 00:44:06 ubuntu ubiquity[2608]:     status = int(status)
Apr 13 00:44:06 ubuntu ubiquity[2608]: ValueError: invalid literal for int() with base 10: ''
Apr 13 00:44:06 ubuntu ubiquity[2608]: 
Apr 13 00:44:11 ubuntu ubiquity[2608]: last message repeated 2 times
Apr 13 00:44:11 ubuntu gdm-binary[13702]: WARNING: Unable to find users: no seat-id found
Apr 13 00:44:12 ubuntu acpid: client 1497[0:0] has disconnected
Apr 13 00:44:12 ubuntu acpid: client connected from 13708[0:0]
Apr 13 00:44:12 ubuntu acpid: 1 client rule loaded
Apr 13 00:44:13 ubuntu kernel: [  871.538751] [TTM] Zone  kernel: Available graphics memory: 436968 kiB.
Apr 13 00:44:13 ubuntu kernel: [  871.538756] [TTM] Zone highmem: Available graphics memory: 1030476 kiB.
Apr 13 00:44:13 ubuntu kernel: [  871.538772] [drm] nouveau 0000:01:00.0: 256 MiB VRAM
Apr 13 00:44:13 ubuntu kernel: [  871.538853] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Apr 13 00:44:13 ubuntu kernel: [  871.538870] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Apr 13 00:44:13 ubuntu kernel: [  871.538879] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 13 00:44:13 ubuntu kernel: [  871.538959] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 13 00:44:13 ubuntu kernel: [  871.538963] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
Apr 13 00:44:13 ubuntu kernel: [  871.539183] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
Apr 13 00:44:13 ubuntu kernel: [  871.539853] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
Apr 13 00:44:13 ubuntu kernel: [  871.540072] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 0
Apr 13 00:44:13 ubuntu kernel: [  871.540592] [TTM] Zone  kernel: Used memory at exit: 0 kiB.
Apr 13 00:44:13 ubuntu kernel: [  871.540601] [TTM] Zone highmem: Used memory at exit: 0 kiB.
Apr 13 00:44:14 ubuntu gdm-session-worker[13712]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 13 00:44:16 ubuntu pulseaudio[2631]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Apr 13 00:45:25 ubuntu pulseaudio[2631]: last message repeated 3 times
Apr 13 00:45:25 ubuntu AptDaemon: INFO: Initializing daemon
```

I would appreciate your suggestions and please help me install Lucid.  Thank you very much!

---

### Post by VMC on 2010-04-12
Just scanning through the syslog I found this regarding you PNP:
```
Apr 12 20:30:32 ubuntu kernel: [ 0.051568] PnPBIOS: Scanning system for PnP BIOS support...
Apr 12 20:30:32 ubuntu kernel: [ 0.051651] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5b70
Apr 12 20:30:32 ubuntu kernel: [ 0.051651] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x675a, dseg 0xf0000
Apr 12 20:30:32 ubuntu kernel: [ 0.051651] PNPBIOS fault.. attempting recovery.
Apr 12 20:30:32 ubuntu kernel: [ 0.051651] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
Apr 12 20:30:32 ubuntu kernel: [ 0.051651] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
Apr 12 20:30:32 ubuntu kernel: [ 0.051651] PnPBIOS: Check with your vendor for an updated BIOS
Apr 12 20:30:32 ubuntu kernel: [ 0.051654] PnPBIOS: get_dev_node: unexpected status 0x3a
Apr 12 20:30:32 ubuntu kernel: [ 0.051717] PnPBIOS: 10 nodes reported by PnP BIOS; 10 recorded by driver

```

Also further down it references some trouble with the file system.

You can cat out '**/var/log/installer/partman**' , using sudo, and see if any other helfull info.

---

### Post by iClouseau88 on 2010-04-12
Hello VMC,

Thanks for your reply. I just re-tried the installation using "pnpbios=off" in addition to "acpi=off, noapic, nolapic and nomodeset " (via F6 key).  Still the same problem: Installer crashed just after "configuring hardware".  "Errorno 13: Permission denied /proc/2601/environ". I did look at /var/log/installer but did not find "partman".  I found "debug" instead and here's the content:

```


Ubiquity 2.2.15
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:558: GtkWarning: gtk_window_resize: assertion `width > 0' failed
  widget.resize(w, h)
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:1255: GtkWarning: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
  self.progress_bar.set_fraction(fraction)
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:1264: GtkWarning: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
  self.progress_bar.set_fraction(fraction)
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 524, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 511, in main
    install(query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 242, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 508, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1160, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1043, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 2497, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 391, in run
    self.configure_hardware()
  File "/usr/share/ubiquity/install.py", line 1403, in configure_hardware
    install_misc.set_debconf(self.target, 'popularity-contest/participate', participate, self.db)
  File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 70, in set_debconf
    dc = debconf.Debconf(read=dccomm.stdout, write=dccomm.stdin)
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 53, in __init__
    self.setUp(title)
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 56, in setUp
    self.version = self.version(2)
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 65, in <lambda>
    lambda *args, **kw: self.command(command, *args, **kw))
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 86, in command
    status = int(status)
ValueError: invalid literal for int() with base 10: ''



Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 524, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 511, in main
    install(query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 242, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 508, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1160, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1043, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 2497, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 391, in run
    self.configure_hardware()
  File "/usr/share/ubiquity/install.py", line 1403, in configure_hardware
    install_misc.set_debconf(self.target, 'popularity-contest/participate', participate, self.db)
  File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 70, in set_debconf
    dc = debconf.Debconf(read=dccomm.stdout, write=dccomm.stdin)
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 53, in __init__
    self.setUp(title)
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 56, in setUp
    self.version = self.version(2)
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 65, in <lambda>
    lambda *args, **kw: self.command(command, *args, **kw))
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 86, in command
    status = int(status)
ValueError: invalid literal for int() with base 10: ''


```

This desktop PC has a P4 CPU, 2 GB RAM and a Geforce 5500 Nvidia-based video card.  Currently I can boot into Windows 7, PCBSD and Fedora Core 12 and am able to use these operating systems.  I don't understand why Ubuntu's syslog gives those error messages. I also reported the bug to launchpad.net.

---

### Post by VMC on 2010-04-13
Since your missing partman how did you partition your HD? Manual or let ubiquity choose?

Also if you open a terminal and run 'ubiquity -d' it should add more to the installer folder.

---

### Post by iClouseau88 on 2010-04-13
Hello VMC,

I manually partitioned my HD. The problem I had was mostly solved after I went into BIOS and changed the default PNP= NO ('cause XP takes care of PNP) to PNP=YES. After that, I installed the Alternate Lucid Beta2 CD and everything went smoothly. The only problem which remains is I cannot boot into openSUSE from Ubuntu's Grub2 menu.  I will look up the solution.

---

### Post by VMC on 2010-04-13
> **iClouseau88 said:**
> Hello VMC,

I manually partitioned my HD. The problem I had was mostly solved after I went into BIOS and changed the default PNP= NO ('cause XP takes care of PNP) to PNP=YES. After that, I installed the Alternate Lucid Beta2 CD and everything went smoothly. The only problem which remains is I cannot boot into openSUSE from Ubuntu's Grub2 menu.  I will look up the solution.

I noticed some mentioned of suse in the syslog. os-prober may have missed it. Check that your UUID's match up.

You can check using ```
sudo os-prober
``` to see if it sees suse okay.

---

### Post by iClouseau88 on 2010-04-14
Hi,
[B]
Problem solved[/B].  I re-installed Fc12 first then openSUSE both with GRUB loader in MBR, and **finally Lucid** beta2 which suggests its **Grub2 be placed in MBR**. Now I can boot into Suse as well as the other two and Windows 7 individually.

Cheers!

---

