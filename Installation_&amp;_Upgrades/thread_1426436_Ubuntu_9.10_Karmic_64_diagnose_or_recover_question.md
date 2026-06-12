---
title: "Ubuntu 9.10 Karmic 64 diagnose or recover question"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by AgentZ86 on 2010-03-10
Hi all

I shut down the computer last night and now when I turn it on it comes to the boot screen and wants me to select a kernel such as generic 2.20.1 or some such thing

Anyhow no matter which one I select I cannot get the computer to come back up.

I believe I have hardware failure but wanted some advise to diagnose or attempt to recover this.

I select recover mode and it takes me to a (ash) bash prompt which seems to be none functional.

I want to say this could have occurred from the latest update kernel but I can't be sure because it was working perfectly last night.

I've been using this machine for a long time without any trouble at all.

Please advise where are some links or info one what would be a good step to diagnose or try a recover disk of some type ?

Gparted checks the disk and it seems ok also.

I can only assume some file corruption of some kind but I don't know how to test things.

Thanks in advance for any advice on how to diagnose this subject.


Here is my kernel log:

> Mar 10 13:38:32 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Mar 10 13:38:32 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 10 13:38:32 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] DMI 2.3 present.
Mar 10 13:38:32 ubuntu kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Mar 10 13:38:32 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] last_pfn = 0x3ffb0 max_arch_pfn = 0x400000000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Mar 10 13:38:32 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   A0000-EFFFF uncachable
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Mar 10 13:38:32 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FFC0000000 write-back
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   1 base 00EC000000 mask FFFC000000 write-combining
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   2 disabled
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   3 disabled
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   4 disabled
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   5 disabled
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   6 disabled
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   7 disabled
Mar 10 13:38:32 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Mar 10 13:38:32 ubuntu kernel: [    0.000000] modified physical RAM map:
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000003ffb0000 (usable)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 000000003fff0000 - 0000000040000000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000003ffb0000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  0000000000 - 003fe00000 page 2M
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  003fe00000 - 003ffb0000 page 4k
Mar 10 13:38:32 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 3ffb0000 @ 10000-13000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] RAMDISK: 3f9ef000 - 3ff7fe71
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000fa880 00014 (v00 ACPIAM)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: RSDT 000000003ffb0000 00030 (v01 A M I  OEMRSDT  11000503 MSFT 00000097)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: FACP 000000003ffb0200 00081 (v01 A M I  OEMFACP  11000503 MSFT 00000097)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: DSDT 000000003ffb03f0 0391B (v01  A0277 A0277001 00000001 MSFT 0100000D)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: FACS 000000003ffc0000 00040
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: APIC 000000003ffb0390 00052 (v01 A M I  OEMAPIC  11000503 MSFT 00000097)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: OEMB 000000003ffc0040 0003F (v01 A M I  OEMBIOS  11000503 MSFT 00000097)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Mar 10 13:38:32 ubuntu kernel: [    0.000000] No NUMA configuration found
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000003ffb0000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000003ffb0000
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   NODE_DATA [0000000000011000 - 0000000000015fff]
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   bootmap [0000000000016000 -  000000000001dff7] pages 8
Mar 10 13:38:32 ubuntu kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 003ffb0000]
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   #3 [003f9ef000 - 003ff7fe71]          RAMDISK ==> [003f9ef000 - 003ff7fe71]
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   #5 [00019e3000 - 00019e3280]              BRK ==> [00019e3000 - 00019e3280]
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 10 13:38:32 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Mar 10 13:38:32 ubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea0000dfffff] PMD -> [ffff880001e00000-ffff880002bfffff] on node 0
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 10 13:38:32 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 10 13:38:32 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 10 13:38:32 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0003ffb0
Mar 10 13:38:32 ubuntu kernel: [    0.000000] On node 0 totalpages: 261951
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   DMA zone: 102 pages reserved
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   DMA zone: 3825 pages, LIFO batch:0
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   DMA32 zone: 3527 pages used for memmap
Mar 10 13:38:32 ubuntu kernel: [    0.000000]   DMA32 zone: 254441 pages, LIFO batch:31
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar 10 13:38:32 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 10 13:38:32 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 10 13:38:32 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Mar 10 13:38:32 ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
Mar 10 13:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf780000)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Mar 10 13:38:32 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages at ffff8800019ee000, static data 90720 bytes
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 258266
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Policy zone: DMA32
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Mar 10 13:38:32 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Checking aperture...
Mar 10 13:38:32 ubuntu kernel: [    0.000000] AGP bridge at 00:00:00
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Aperture from AGP @ ec000000 old size 32 MB
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Aperture from AGP @ ec000000 size 64 MB (APSIZE f30)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Node 0: aperture @ ec000000 size 64 MB
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Memory: 1017264k/1048256k available (5313k kernel code, 452k absent, 30540k reserved, 3011k data, 660k init)
Mar 10 13:38:32 ubuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar 10 13:38:32 ubuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Mar 10 13:38:32 ubuntu kernel: [    0.000000] Detected 2002.319 MHz processor.
Mar 10 13:38:32 ubuntu kernel: [    0.001657] Console: colour VGA+ 80x25
Mar 10 13:38:32 ubuntu kernel: [    0.001661] console [tty0] enabled
Mar 10 13:38:32 ubuntu kernel: [    0.010000] allocated 10485760 bytes of page_cgroup
Mar 10 13:38:32 ubuntu kernel: [    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4004.63 BogoMIPS (lpj=20023190)
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Security Framework initialized
Mar 10 13:38:32 ubuntu kernel: [    0.010000] AppArmor: AppArmor initialized
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Mount-cache hash table entries: 256
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Initializing cgroup subsys ns
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Initializing cgroup subsys cpuacct
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Initializing cgroup subsys memory
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Initializing cgroup subsys freezer
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Initializing cgroup subsys net_cls
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU 0/0x0 -> Node 0
Mar 10 13:38:32 ubuntu kernel: [    0.010000] tseg: 0000000000
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU: Physical Processor ID: 0
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU: Processor Core ID: 0
Mar 10 13:38:32 ubuntu kernel: [    0.010000] mce: CPU supports 5 MCE banks
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Performance Counters: AMD PMU driver.
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ... version:                 0
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ... bit width:               48
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ... generic counters:        4
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ... value mask:              0000ffffffffffff
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ... max period:              00007fffffffffff
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ... fixed-purpose counters:  0
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ... counter mask:            000000000000000f
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ACPI: Core revision 20090521
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Setting APIC routing to flat
Mar 10 13:38:32 ubuntu kernel: [    0.010000] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Mar 10 13:38:32 ubuntu kernel: [    0.100484] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 01
Mar 10 13:38:32 ubuntu kernel: [    0.110000] Booting processor 1 APIC 0x1 ip 0x6000
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Initializing CPU#1
Mar 10 13:38:32 ubuntu kernel: [    0.010000] Calibrating delay using timer specific routine.. 4005.19 BogoMIPS (lpj=20025993)
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU 1/0x1 -> Node 0
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU: Physical Processor ID: 0
Mar 10 13:38:32 ubuntu kernel: [    0.010000] CPU: Processor Core ID: 1
Mar 10 13:38:32 ubuntu kernel: [    0.010000] mce: CPU supports 5 MCE banks
Mar 10 13:38:32 ubuntu kernel: [    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Mar 10 13:38:32 ubuntu kernel: [    0.260454] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 01
Mar 10 13:38:32 ubuntu kernel: [    0.260470] Brought up 2 CPUs
Mar 10 13:38:32 ubuntu kernel: [    0.260472] Total of 2 processors activated (8009.83 BogoMIPS).
Mar 10 13:38:32 ubuntu kernel: [    0.260714] CPU0 attaching sched-domain:
Mar 10 13:38:32 ubuntu kernel: [    0.260717]  domain 0: span 0-1 level MC
Mar 10 13:38:32 ubuntu kernel: [    0.260720]   groups: 0 1
Mar 10 13:38:32 ubuntu kernel: [    0.260726] CPU1 attaching sched-domain:
Mar 10 13:38:32 ubuntu kernel: [    0.260728]  domain 0: span 0-1 level MC
Mar 10 13:38:32 ubuntu kernel: [    0.260730]   groups: 1 0
Mar 10 13:38:32 ubuntu kernel: [    0.260810] Booting paravirtualized kernel on bare hardware
Mar 10 13:38:32 ubuntu kernel: [    0.260810] regulator: core version 0.5
Mar 10 13:38:32 ubuntu kernel: [    0.260810] Time: 13:36:02  Date: 03/10/10
Mar 10 13:38:32 ubuntu kernel: [    0.260810] NET: Registered protocol family 16
Mar 10 13:38:32 ubuntu kernel: [    0.260810] node 0 link 0: io port [1000, ffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.260810] TOM: 0000000040000000 aka 1024M
Mar 10 13:38:32 ubuntu kernel: [    0.260810] node 0 link 0: mmio [a0000, bffff]
Mar 10 13:38:32 ubuntu kernel: [    0.260810] node 0 link 0: mmio [40000000, ffffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.260810] bus: [00,ff] on node 0 link 0
Mar 10 13:38:32 ubuntu kernel: [    0.260810] bus: 00 index 0 io port: [0, ffff]
Mar 10 13:38:32 ubuntu kernel: [    0.260810] bus: 00 index 1 mmio: [a0000, bffff]
Mar 10 13:38:32 ubuntu kernel: [    0.260810] bus: 00 index 2 mmio: [40000000, fcffffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.260810] ACPI: bus type pci registered
Mar 10 13:38:32 ubuntu kernel: [    0.260810] PCI: Using configuration type 1 for base access
Mar 10 13:38:32 ubuntu kernel: [    0.261169] bio: create slab <bio-0> at 0
Mar 10 13:38:32 ubuntu kernel: [    0.261169] ACPI: EC: Look up EC in DSDT
Mar 10 13:38:32 ubuntu kernel: [    0.266242] ACPI: Interpreter enabled
Mar 10 13:38:32 ubuntu kernel: [    0.266246] ACPI: (supports S0 S1 S3 S4 S5)
Mar 10 13:38:32 ubuntu kernel: [    0.266269] ACPI: Using IOAPIC for interrupt routing
Mar 10 13:38:32 ubuntu kernel: [    0.274844] ACPI Warning: Incorrect checksum in table [OEMB] - 09, should be 00 20090521 tbutils-246
Mar 10 13:38:32 ubuntu kernel: [    0.274935] ACPI: No dock devices found.
Mar 10 13:38:32 ubuntu kernel: [    0.275054] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 10 13:38:32 ubuntu kernel: [    0.275112] pci 0000:00:00.0: reg 10 32bit mmio: [0xec000000-0xefffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.275455] pci 0000:00:01.0: supports D1
Mar 10 13:38:32 ubuntu kernel: [    0.275510] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfac00000-0xfac03fff]
Mar 10 13:38:32 ubuntu kernel: [    0.275517] pci 0000:00:0a.0: reg 14 io port: [0xb000-0xb0ff]
Mar 10 13:38:32 ubuntu kernel: [    0.275543] pci 0000:00:0a.0: reg 30 32bit mmio: [0xfab00000-0xfab1ffff]
Mar 10 13:38:32 ubuntu kernel: [    0.275570] pci 0000:00:0a.0: supports D1 D2
Mar 10 13:38:32 ubuntu kernel: [    0.275572] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 10 13:38:32 ubuntu kernel: [    0.275577] pci 0000:00:0a.0: PME# disabled
Mar 10 13:38:32 ubuntu kernel: [    0.275623] pci 0000:00:0f.0: reg 10 io port: [0xd000-0xd007]
Mar 10 13:38:32 ubuntu kernel: [    0.275629] pci 0000:00:0f.0: reg 14 io port: [0xc800-0xc803]
Mar 10 13:38:32 ubuntu kernel: [    0.275636] pci 0000:00:0f.0: reg 18 io port: [0xc400-0xc407]
Mar 10 13:38:32 ubuntu kernel: [    0.275642] pci 0000:00:0f.0: reg 1c io port: [0xc000-0xc003]
Mar 10 13:38:32 ubuntu kernel: [    0.275649] pci 0000:00:0f.0: reg 20 io port: [0xb800-0xb80f]
Mar 10 13:38:32 ubuntu kernel: [    0.275656] pci 0000:00:0f.0: reg 24 io port: [0xb400-0xb4ff]
Mar 10 13:38:32 ubuntu kernel: [    0.275734] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
Mar 10 13:38:32 ubuntu kernel: [    0.275824] pci 0000:00:10.0: reg 20 io port: [0xd400-0xd41f]
Mar 10 13:38:32 ubuntu kernel: [    0.275852] pci 0000:00:10.0: supports D1 D2
Mar 10 13:38:32 ubuntu kernel: [    0.275854] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 10 13:38:32 ubuntu kernel: [    0.275858] pci 0000:00:10.0: PME# disabled
Mar 10 13:38:32 ubuntu kernel: [    0.275911] pci 0000:00:10.1: reg 20 io port: [0xd800-0xd81f]
Mar 10 13:38:32 ubuntu kernel: [    0.275939] pci 0000:00:10.1: supports D1 D2
Mar 10 13:38:32 ubuntu kernel: [    0.275941] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar 10 13:38:32 ubuntu kernel: [    0.275946] pci 0000:00:10.1: PME# disabled
Mar 10 13:38:32 ubuntu kernel: [    0.275999] pci 0000:00:10.2: reg 20 io port: [0xe000-0xe01f]
Mar 10 13:38:32 ubuntu kernel: [    0.276027] pci 0000:00:10.2: supports D1 D2
Mar 10 13:38:32 ubuntu kernel: [    0.276029] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Mar 10 13:38:32 ubuntu kernel: [    0.276034] pci 0000:00:10.2: PME# disabled
Mar 10 13:38:32 ubuntu kernel: [    0.276087] pci 0000:00:10.3: reg 20 io port: [0xe400-0xe41f]
Mar 10 13:38:32 ubuntu kernel: [    0.276114] pci 0000:00:10.3: supports D1 D2
Mar 10 13:38:32 ubuntu kernel: [    0.276116] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Mar 10 13:38:32 ubuntu kernel: [    0.276120] pci 0000:00:10.3: PME# disabled
Mar 10 13:38:32 ubuntu kernel: [    0.276157] pci 0000:00:10.4: reg 10 32bit mmio: [0xfae00000-0xfae000ff]
Mar 10 13:38:32 ubuntu kernel: [    0.276200] pci 0000:00:10.4: supports D1 D2
Mar 10 13:38:32 ubuntu kernel: [    0.276203] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Mar 10 13:38:32 ubuntu kernel: [    0.276208] pci 0000:00:10.4: PME# disabled
Mar 10 13:38:32 ubuntu kernel: [    0.276279] HPET not enabled in BIOS. You might try hpet=force boot option
Mar 10 13:38:32 ubuntu kernel: [    0.276285] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
Mar 10 13:38:32 ubuntu kernel: [    0.276345] pci 0000:00:11.5: reg 10 io port: [0xe800-0xe8ff]
Mar 10 13:38:32 ubuntu kernel: [    0.276394] pci 0000:00:11.5: supports D1 D2
Mar 10 13:38:32 ubuntu kernel: [    0.276430] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
Mar 10 13:38:32 ubuntu kernel: [    0.276604] pci 0000:01:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.276611] pci 0000:01:00.0: reg 14 32bit mmio: [0xf0000000-0xf7ffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.276617] pci 0000:01:00.0: reg 18 32bit mmio: [0xf9f00000-0xf9f7ffff]
Mar 10 13:38:32 ubuntu kernel: [    0.276630] pci 0000:01:00.0: reg 30 32bit mmio: [0xfaf00000-0xfaf1ffff]
Mar 10 13:38:32 ubuntu kernel: [    0.276703] pci 0000:00:01.0: bridge 32bit mmio: [0xfaf00000-0xfbffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.276708] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf9ffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.276718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 10 13:38:32 ubuntu kernel: [    0.283768] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
Mar 10 13:38:32 ubuntu kernel: [    0.283860] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
Mar 10 13:38:32 ubuntu kernel: [    0.283949] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
Mar 10 13:38:32 ubuntu kernel: [    0.284037] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Mar 10 13:38:32 ubuntu kernel: [    0.284128] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Mar 10 13:38:32 ubuntu kernel: [    0.284218] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Mar 10 13:38:32 ubuntu kernel: [    0.284317] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Mar 10 13:38:32 ubuntu kernel: [    0.284407] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Mar 10 13:38:32 ubuntu kernel: [    0.284606] SCSI subsystem initialized
Mar 10 13:38:32 ubuntu kernel: [    0.284669] libata version 3.00 loaded.
Mar 10 13:38:32 ubuntu kernel: [    0.284669] usbcore: registered new interface driver usbfs
Mar 10 13:38:32 ubuntu kernel: [    0.284669] usbcore: registered new interface driver hub
Mar 10 13:38:32 ubuntu kernel: [    0.284669] usbcore: registered new device driver usb
Mar 10 13:38:32 ubuntu kernel: [    0.284669] ACPI: WMI: Mapper loaded
Mar 10 13:38:32 ubuntu kernel: [    0.284669] PCI: Using ACPI for IRQ routing
Mar 10 13:38:32 ubuntu kernel: [    0.284669] pci 0000:00:00.0: BAR 0: address space collision on of device [0xec000000-0xefffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.284669] pci 0000:00:00.0: BAR 0: can't allocate resource
Mar 10 13:38:32 ubuntu kernel: [    0.310007] Bluetooth: Core ver 2.15
Mar 10 13:38:32 ubuntu kernel: [    0.310027] NET: Registered protocol family 31
Mar 10 13:38:32 ubuntu kernel: [    0.310027] Bluetooth: HCI device and connection manager initialized
Mar 10 13:38:32 ubuntu kernel: [    0.310027] Bluetooth: HCI socket layer initialized
Mar 10 13:38:32 ubuntu kernel: [    0.310027] NetLabel: Initializing
Mar 10 13:38:32 ubuntu kernel: [    0.310027] NetLabel:  domain hash size = 128
Mar 10 13:38:32 ubuntu kernel: [    0.310027] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 10 13:38:32 ubuntu kernel: [    0.310042] NetLabel:  unlabeled traffic allowed by default
Mar 10 13:38:32 ubuntu kernel: [    0.310118] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0282]
Mar 10 13:38:32 ubuntu kernel: [    0.312763] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xec000000
Mar 10 13:38:32 ubuntu kernel: [    0.340024] pnp: PnP ACPI init
Mar 10 13:38:32 ubuntu kernel: [    0.340051] ACPI: bus type pnp registered
Mar 10 13:38:32 ubuntu kernel: [    0.341676] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341681] pnp 00:08: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341684] pnp 00:08: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341688] pnp 00:08: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341691] pnp 00:08: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341694] pnp 00:08: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341698] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341701] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341705] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341708] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341712] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341715] pnp 00:08: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.341719] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.343031] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.343035] pnp 00:0b: mem resource (0xc0000-0xdffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.343038] pnp 00:0b: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.343042] pnp 00:0b: mem resource (0x100000-0x3ffeffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
Mar 10 13:38:32 ubuntu kernel: [    0.343352] pnp: PnP ACPI: found 12 devices
Mar 10 13:38:32 ubuntu kernel: [    0.343354] ACPI: ACPI bus type pnp unregistered
Mar 10 13:38:32 ubuntu kernel: [    0.343368] system 00:07: ioport range 0x680-0x6ff has been reserved
Mar 10 13:38:32 ubuntu kernel: [    0.343371] system 00:07: ioport range 0x290-0x297 has been reserved
Mar 10 13:38:32 ubuntu kernel: [    0.343377] system 00:08: ioport range 0x3e1-0x3e7 has been reserved
Mar 10 13:38:32 ubuntu kernel: [    0.343380] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Mar 10 13:38:32 ubuntu kernel: [    0.343383] system 00:08: ioport range 0x800-0x87f has been reserved
Mar 10 13:38:32 ubuntu kernel: [    0.343386] system 00:08: ioport range 0x400-0x41f has been reserved
Mar 10 13:38:32 ubuntu kernel: [    0.343392] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 10 13:38:32 ubuntu kernel: [    0.343396] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
Mar 10 13:38:32 ubuntu kernel: [    0.343399] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
Mar 10 13:38:32 ubuntu kernel: [    0.348092] AppArmor: AppArmor Filesystem Enabled
Mar 10 13:38:32 ubuntu kernel: [    0.348127] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar 10 13:38:32 ubuntu kernel: [    0.348130] pci 0000:00:01.0:   IO window: disabled
Mar 10 13:38:32 ubuntu kernel: [    0.348136] pci 0000:00:01.0:   MEM window: 0xfaf00000-0xfbffffff
Mar 10 13:38:32 ubuntu kernel: [    0.348140] pci 0000:00:01.0:   PREFETCH window: 0xf0000000-0xf9ffffff
Mar 10 13:38:32 ubuntu kernel: [    0.348155] pci 0000:00:01.0: setting latency timer to 64
Mar 10 13:38:32 ubuntu kernel: [    0.348160] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Mar 10 13:38:32 ubuntu kernel: [    0.348163] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.348167] pci_bus 0000:01: resource 1 mem: [0xfaf00000-0xfbffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.348169] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf9ffffff]
Mar 10 13:38:32 ubuntu kernel: [    0.348213] NET: Registered protocol family 2
Mar 10 13:38:32 ubuntu kernel: [    0.348340] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
Mar 10 13:38:32 ubuntu kernel: [    0.348991] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
Mar 10 13:38:32 ubuntu kernel: [    0.350032] Switched to high resolution mode on CPU 0
Mar 10 13:38:32 ubuntu kernel: [    0.350465] Switched to high resolution mode on CPU 1
Mar 10 13:38:32 ubuntu kernel: [    0.351051] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Mar 10 13:38:32 ubuntu kernel: [    0.352031] TCP: Hash tables configured (established 131072 bind 65536)
Mar 10 13:38:32 ubuntu kernel: [    0.352035] TCP reno registered
Mar 10 13:38:32 ubuntu kernel: [    0.352181] NET: Registered protocol family 1
Mar 10 13:38:32 ubuntu kernel: [    0.352274] Trying to unpack rootfs image as initramfs...
Mar 10 13:38:32 ubuntu kernel: [    1.935055] Freeing initrd memory: 5699k freed
Mar 10 13:38:32 ubuntu kernel: [    1.940768] Scanning for low memory corruption every 60 seconds
Mar 10 13:38:32 ubuntu kernel: [    1.940938] audit: initializing netlink socket (disabled)
Mar 10 13:38:32 ubuntu kernel: [    1.940958] type=2000 audit(1268228162.940:1): initialized
Mar 10 13:38:32 ubuntu kernel: [    1.950760] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Mar 10 13:38:32 ubuntu kernel: [    1.952297] VFS: Disk quotas dquot_6.5.2
Mar 10 13:38:32 ubuntu kernel: [    1.952359] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Mar 10 13:38:32 ubuntu kernel: [    1.953056] fuse init (API version 7.12)
Mar 10 13:38:32 ubuntu kernel: [    1.953142] msgmni has been set to 1997
Mar 10 13:38:32 ubuntu kernel: [    1.953449] alg: No test for stdrng (krng)
Mar 10 13:38:32 ubuntu kernel: [    1.953479] io scheduler noop registered
Mar 10 13:38:32 ubuntu kernel: [    1.953481] io scheduler anticipatory registered
Mar 10 13:38:32 ubuntu kernel: [    1.953483] io scheduler deadline registered
Mar 10 13:38:32 ubuntu kernel: [    1.953528] io scheduler cfq registered (default)
Mar 10 13:38:32 ubuntu kernel: [    1.953549] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Mar 10 13:38:32 ubuntu kernel: [    3.950019] pci 0000:00:10.4: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Mar 10 13:38:32 ubuntu kernel: [    3.950158] pci 0000:01:00.0: Boot video device
Mar 10 13:38:32 ubuntu kernel: [    3.950340] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 10 13:38:32 ubuntu kernel: [    3.950366] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 10 13:38:32 ubuntu kernel: [    3.950503] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Mar 10 13:38:32 ubuntu kernel: [    3.950507] ACPI: Power Button [PWRF]
Mar 10 13:38:32 ubuntu kernel: [    3.950566] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Mar 10 13:38:32 ubuntu kernel: [    3.950572] ACPI: Power Button [PWRB]
Mar 10 13:38:32 ubuntu kernel: [    3.950624] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Mar 10 13:38:32 ubuntu kernel: [    3.950629] ACPI: Sleep Button [SLPB]
Mar 10 13:38:32 ubuntu kernel: [    3.950844] processor LNXCPU:00: registered as cooling_device0
Mar 10 13:38:32 ubuntu kernel: [    3.950886] processor LNXCPU:01: registered as cooling_device1
Mar 10 13:38:32 ubuntu kernel: [    3.954495] Linux agpgart interface v0.103
Mar 10 13:38:32 ubuntu kernel: [    3.954508] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 10 13:38:32 ubuntu kernel: [    3.954624] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 10 13:38:32 ubuntu kernel: [    3.954917] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 10 13:38:32 ubuntu kernel: [    3.955954] brd: module loaded
Mar 10 13:38:32 ubuntu kernel: [    3.956423] loop: module loaded
Mar 10 13:38:32 ubuntu kernel: [    3.956512] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Mar 10 13:38:32 ubuntu kernel: [    3.957220] pata_via 0000:00:0f.1: version 0.3.4
Mar 10 13:38:32 ubuntu kernel: [    3.957244]   alloc irq_desc for 20 on node 0
Mar 10 13:38:32 ubuntu kernel: [    3.957247]   alloc kstat_irqs on node 0
Mar 10 13:38:32 ubuntu kernel: [    3.957256] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar 10 13:38:32 ubuntu kernel: [    3.957493] scsi0 : pata_via
Mar 10 13:38:32 ubuntu kernel: [    3.957633] scsi1 : pata_via
Mar 10 13:38:32 ubuntu kernel: [    3.959439] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Mar 10 13:38:32 ubuntu kernel: [    3.959442] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Mar 10 13:38:32 ubuntu kernel: [    3.959852] Fixed MDIO Bus: probed
Mar 10 13:38:32 ubuntu kernel: [    3.959887] PPP generic driver version 2.4.2
Mar 10 13:38:32 ubuntu kernel: [    3.960037] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 10 13:38:32 ubuntu kernel: [    3.960110]   alloc irq_desc for 21 on node 0
Mar 10 13:38:32 ubuntu kernel: [    3.960113]   alloc kstat_irqs on node 0
Mar 10 13:38:32 ubuntu kernel: [    3.960119] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Mar 10 13:38:32 ubuntu kernel: [    3.960139] ehci_hcd 0000:00:10.4: EHCI Host Controller
Mar 10 13:38:32 ubuntu kernel: [    3.960195] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
Mar 10 13:38:32 ubuntu kernel: [    3.960283] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfae00000
Mar 10 13:38:32 ubuntu kernel: [    3.980022] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
Mar 10 13:38:32 ubuntu kernel: [    3.980097] usb usb1: configuration #1 chosen from 1 choice
Mar 10 13:38:32 ubuntu kernel: [    3.980129] hub 1-0:1.0: USB hub found
Mar 10 13:38:32 ubuntu kernel: [    3.980139] hub 1-0:1.0: 8 ports detected
Mar 10 13:38:32 ubuntu kernel: [    3.980218] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 10 13:38:32 ubuntu kernel: [    3.980234] uhci_hcd: USB Universal Host Controller Interface driver
Mar 10 13:38:32 ubuntu kernel: [    3.980356] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Mar 10 13:38:32 ubuntu kernel: [    3.980366] uhci_hcd 0000:00:10.0: UHCI Host Controller
Mar 10 13:38:32 ubuntu kernel: [    3.980399] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Mar 10 13:38:32 ubuntu kernel: [    3.980424] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
Mar 10 13:38:32 ubuntu kernel: [    3.980512] usb usb2: configuration #1 chosen from 1 choice
Mar 10 13:38:32 ubuntu kernel: [    3.980538] hub 2-0:1.0: USB hub found
Mar 10 13:38:32 ubuntu kernel: [    3.980546] hub 2-0:1.0: 2 ports detected
Mar 10 13:38:32 ubuntu kernel: [    3.980635] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Mar 10 13:38:32 ubuntu kernel: [    3.980641] uhci_hcd 0000:00:10.1: UHCI Host Controller
Mar 10 13:38:32 ubuntu kernel: [    3.980676] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Mar 10 13:38:32 ubuntu kernel: [    3.980699] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
Mar 10 13:38:32 ubuntu kernel: [    3.980782] usb usb3: configuration #1 chosen from 1 choice
Mar 10 13:38:32 ubuntu kernel: [    3.980810] hub 3-0:1.0: USB hub found
Mar 10 13:38:32 ubuntu kernel: [    3.980818] hub 3-0:1.0: 2 ports detected
Mar 10 13:38:32 ubuntu kernel: [    3.980903] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 10 13:38:32 ubuntu kernel: [    3.980911] uhci_hcd 0000:00:10.2: UHCI Host Controller
Mar 10 13:38:32 ubuntu kernel: [    3.980942] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Mar 10 13:38:32 ubuntu kernel: [    3.980965] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
Mar 10 13:38:32 ubuntu kernel: [    3.981052] usb usb4: configuration #1 chosen from 1 choice
Mar 10 13:38:32 ubuntu kernel: [    3.981080] hub 4-0:1.0: USB hub found
Mar 10 13:38:32 ubuntu kernel: [    3.981087] hub 4-0:1.0: 2 ports detected
Mar 10 13:38:32 ubuntu kernel: [    3.981169] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 10 13:38:32 ubuntu kernel: [    3.981175] uhci_hcd 0000:00:10.3: UHCI Host Controller
Mar 10 13:38:32 ubuntu kernel: [    3.981216] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
Mar 10 13:38:32 ubuntu kernel: [    3.981241] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e400
Mar 10 13:38:32 ubuntu kernel: [    3.981337] usb usb5: configuration #1 chosen from 1 choice
Mar 10 13:38:32 ubuntu kernel: [    3.981362] hub 5-0:1.0: USB hub found
Mar 10 13:38:32 ubuntu kernel: [    3.981369] hub 5-0:1.0: 2 ports detected
Mar 10 13:38:32 ubuntu kernel: [    3.981470] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Mar 10 13:38:32 ubuntu kernel: [    3.981472] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Mar 10 13:38:32 ubuntu kernel: [    3.981593] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 10 13:38:32 ubuntu kernel: [    3.981676] mice: PS/2 mouse device common for all mice
Mar 10 13:38:32 ubuntu kernel: [    3.981791] rtc_cmos 00:02: RTC can wake from S4
Mar 10 13:38:32 ubuntu kernel: [    3.981837] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Mar 10 13:38:32 ubuntu kernel: [    3.981892] rtc0: alarms up to one year, y3k, 114 bytes nvram
Mar 10 13:38:32 ubuntu kernel: [    3.982030] device-mapper: uevent: version 1.0.3
Mar 10 13:38:32 ubuntu kernel: [    3.982144] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Mar 10 13:38:32 ubuntu kernel: [    3.982256] device-mapper: multipath: version 1.1.0 loaded
Mar 10 13:38:32 ubuntu kernel: [    3.982260] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 10 13:38:32 ubuntu kernel: [    3.982495] cpuidle: using governor ladder
Mar 10 13:38:32 ubuntu kernel: [    3.982497] cpuidle: using governor menu
Mar 10 13:38:32 ubuntu kernel: [    3.982952] TCP cubic registered
Mar 10 13:38:32 ubuntu kernel: [    3.983101] NET: Registered protocol family 10
Mar 10 13:38:32 ubuntu kernel: [    3.983578] lo: Disabled Privacy Extensions
Mar 10 13:38:32 ubuntu kernel: [    3.983866] NET: Registered protocol family 17
Mar 10 13:38:32 ubuntu kernel: [    3.983891] Bluetooth: L2CAP ver 2.13
Mar 10 13:38:32 ubuntu kernel: [    3.983892] Bluetooth: L2CAP socket layer initialized
Mar 10 13:38:32 ubuntu kernel: [    3.983896] Bluetooth: SCO (Voice Link) ver 0.6
Mar 10 13:38:32 ubuntu kernel: [    3.983898] Bluetooth: SCO socket layer initialized
Mar 10 13:38:32 ubuntu kernel: [    3.983952] Bluetooth: RFCOMM TTY layer initialized
Mar 10 13:38:32 ubuntu kernel: [    3.983956] Bluetooth: RFCOMM socket layer initialized
Mar 10 13:38:32 ubuntu kernel: [    3.983958] Bluetooth: RFCOMM ver 1.11
Mar 10 13:38:32 ubuntu kernel: [    3.983985] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
Mar 10 13:38:32 ubuntu kernel: [    3.983998] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
Mar 10 13:38:32 ubuntu kernel: [    3.983999] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
Mar 10 13:38:32 ubuntu kernel: [    3.984096] PM: Resume from disk failed.
Mar 10 13:38:32 ubuntu kernel: [    3.984110] registered taskstats version 1
Mar 10 13:38:32 ubuntu kernel: [    3.984270]   Magic number: 2:690:634
Mar 10 13:38:32 ubuntu kernel: [    3.984382] rtc_cmos 00:02: setting system clock to 2010-03-10 13:36:06 UTC (1268228166)
Mar 10 13:38:32 ubuntu kernel: [    3.984386] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 10 13:38:32 ubuntu kernel: [    3.984387] EDD information not available.
Mar 10 13:38:32 ubuntu kernel: [    3.999620] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Mar 10 13:38:32 ubuntu kernel: [    4.300452] ata2.00: ATAPI: LITE-ON DVDRW LDW-411S, FS0F, max UDMA/33
Mar 10 13:38:32 ubuntu kernel: [    4.340287] ata2.00: configured for UDMA/33
Mar 10 13:38:32 ubuntu kernel: [    4.341573] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW LDW-411S   FS0F PQ: 0 ANSI: 5
Mar 10 13:38:32 ubuntu kernel: [    4.345736] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Mar 10 13:38:32 ubuntu kernel: [    4.345739] Uniform CD-ROM driver Revision: 3.20
Mar 10 13:38:32 ubuntu kernel: [    4.345839] sr 1:0:0:0: Attached scsi CD-ROM sr0
Mar 10 13:38:32 ubuntu kernel: [    4.345893] sr 1:0:0:0: Attached scsi generic sg0 type 5
Mar 10 13:38:32 ubuntu kernel: [    4.345930] Freeing unused kernel memory: 660k freed
Mar 10 13:38:32 ubuntu kernel: [    4.346385] Write protecting the kernel read-only data: 7580k
Mar 10 13:38:32 ubuntu kernel: [    4.495332]   alloc irq_desc for 17 on node 0
Mar 10 13:38:32 ubuntu kernel: [    4.495338]   alloc kstat_irqs on node 0
Mar 10 13:38:32 ubuntu kernel: [    4.495351] skge 0000:00:0a.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 10 13:38:32 ubuntu kernel: [    4.495368] skge 0000:00:0a.0: PCI: Disallowing DAC for device
Mar 10 13:38:32 ubuntu kernel: [    4.495415] skge 1.13 addr 0xfac00000 irq 17 chip Yukon-Lite rev 9
Mar 10 13:38:32 ubuntu kernel: [    4.496196] skge eth0: addr 00:13:d4:8d:3a:04
Mar 10 13:38:32 ubuntu kernel: [    4.526895] sata_via 0000:00:0f.0: version 2.4
Mar 10 13:38:32 ubuntu kernel: [    4.526918] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Mar 10 13:38:32 ubuntu kernel: [    4.526979] sata_via 0000:00:0f.0: routed to hard irq line 10
Mar 10 13:38:32 ubuntu kernel: [    4.529613] Floppy drive(s): fd0 is 1.44M
Mar 10 13:38:32 ubuntu kernel: [    4.541701] scsi2 : sata_via
Mar 10 13:38:32 ubuntu kernel: [    4.542123] scsi3 : sata_via
Mar 10 13:38:32 ubuntu kernel: [    4.542182] ata3: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma 0xb800 irq 20
Mar 10 13:38:32 ubuntu kernel: [    4.542186] ata4: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb808 irq 20
Mar 10 13:38:32 ubuntu kernel: [    4.561227] FDC 0 is a post-1991 82077
Mar 10 13:38:32 ubuntu kernel: [    4.642535] usb 3-1: new full speed USB device using uhci_hcd and address 2
Mar 10 13:38:32 ubuntu kernel: [    4.750028] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 10 13:38:32 ubuntu kernel: [    4.852694] usb 3-1: configuration #1 chosen from 1 choice
Mar 10 13:38:32 ubuntu kernel: [    4.934053] ata3.00: ATA-6: WDC WD2500JD-00HBB0, 08.02D08, max UDMA/133
Mar 10 13:38:32 ubuntu kernel: [    4.934058] ata3.00: 488397168 sectors, multi 16: LBA48 
Mar 10 13:38:32 ubuntu kernel: [    4.974050] ata3.00: configured for UDMA/133
Mar 10 13:38:32 ubuntu kernel: [    4.974167] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JD-00H 08.0 PQ: 0 ANSI: 5
Mar 10 13:38:32 ubuntu kernel: [    4.974333] sd 2:0:0:0: Attached scsi generic sg1 type 0
Mar 10 13:38:32 ubuntu kernel: [    4.974374] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Mar 10 13:38:32 ubuntu kernel: [    4.974419] sd 2:0:0:0: [sda] Write Protect is off
Mar 10 13:38:32 ubuntu kernel: [    4.974422] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 10 13:38:32 ubuntu kernel: [    4.974445] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 10 13:38:32 ubuntu kernel: [    4.974576]  sda: sda1 sda2 < sda5 >
Mar 10 13:38:32 ubuntu kernel: [    5.023335] sd 2:0:0:0: [sda] Attached SCSI disk
Mar 10 13:38:32 ubuntu kernel: [    5.130024] usb 3-2: new low speed USB device using uhci_hcd and address 3
Mar 10 13:38:32 ubuntu kernel: [    5.180024] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Mar 10 13:38:32 ubuntu kernel: [    5.313630] usb 3-2: configuration #1 chosen from 1 choice
Mar 10 13:38:32 ubuntu kernel: [    5.322620] usbcore: registered new interface driver hiddev
Mar 10 13:38:32 ubuntu kernel: [    5.335894] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input5
Mar 10 13:38:32 ubuntu kernel: [    5.335982] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:10.1-2/input0
Mar 10 13:38:32 ubuntu kernel: [    5.336006] usbcore: registered new interface driver usbhid
Mar 10 13:38:32 ubuntu kernel: [    5.336010] usbhid: v2.6:USB HID core driver
Mar 10 13:38:32 ubuntu kernel: [    5.987257] xor: automatically using best checksumming function: generic_sse
Mar 10 13:38:32 ubuntu kernel: [    6.030008]    generic_sse:  6544.800 MB/sec
Mar 10 13:38:32 ubuntu kernel: [    6.030011] xor: using function: generic_sse (6544.800 MB/sec)
Mar 10 13:38:32 ubuntu kernel: [    6.032638] device-mapper: dm-raid45: initialized v0.2594b
Mar 10 13:38:32 ubuntu kernel: [    6.165761] EXT4-fs (sda1): barriers enabled
Mar 10 13:38:32 ubuntu kernel: [    6.193709] kjournald2 starting: pid 429, dev sda1:8, commit interval 5 seconds
Mar 10 13:38:32 ubuntu kernel: [    6.193727] EXT4-fs (sda1): delayed allocation enabled
Mar 10 13:38:32 ubuntu kernel: [    6.193731] EXT4-fs: file extents enabled
Mar 10 13:38:32 ubuntu kernel: [    6.229602] EXT4-fs: mballoc enabled
Mar 10 13:38:32 ubuntu kernel: [    6.229623] EXT4-fs (sda1): mounted filesystem with ordered data mode
Mar 10 13:38:32 ubuntu kernel: [    6.248844] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
Mar 10 13:38:32 ubuntu kernel: [    6.248849] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
Mar 10 13:38:32 ubuntu kernel: [    6.248852] EXT4-fs: mballoc: 0 generated and it took 0
Mar 10 13:38:32 ubuntu kernel: [    6.248854] EXT4-fs: mballoc: 0 preallocated, 0 discarded
Mar 10 13:38:32 ubuntu kernel: [    6.983150] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [    6.983156] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [    6.983161] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [    6.983170] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [    6.983174] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [    9.333576] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [    9.333582] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [    9.333587] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [    9.333597] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [    9.333601] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [   10.921355] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [   10.921358] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [   10.921362] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [   10.921367] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [   10.921370] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [   11.448627] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [   11.448631] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [   11.448634] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [   11.448639] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [   11.448642] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [   11.983881] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [   11.983885] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [   11.983889] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [   11.983894] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [   11.983896] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [   12.503231] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [   12.503235] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [   12.503239] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [   12.503244] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [   12.503246] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [   13.030493] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [   13.030497] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [   13.030501] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [   13.030506] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [   13.030509] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [   13.859056] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [   13.859060] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [   13.859064] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [   13.859069] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [   13.859072] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [   14.394177] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:32 ubuntu kernel: [   14.394181] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:32 ubuntu kernel: [   14.394185] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:32 ubuntu kernel: [   14.394190] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:32 ubuntu kernel: [   14.394192] Buffer I/O error on device sr0, logical block 176844
Mar 10 13:38:32 ubuntu kernel: [   15.662889] ISO 9660 Extensions: Microsoft Joliet Level 3
Mar 10 13:38:32 ubuntu kernel: [   15.749193] ISO 9660 Extensions: RRIP_1991A
Mar 10 13:38:32 ubuntu kernel: [   16.902856] aufs 2-standalone.tree-30-20090727
Mar 10 13:38:32 ubuntu kernel: [   18.153197] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Mar 10 13:38:32 ubuntu kernel: [  148.045267] Adding 2996080k swap on /dev/sda5.  Priority:-1 extents:1 across:2996080k 
Mar 10 13:38:35 ubuntu kernel: [  152.786059] udev: starting version 147
Mar 10 13:38:37 ubuntu kernel: [  155.429180] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 10 13:38:38 ubuntu kernel: [  156.021962] EDAC MC: Ver: 2.1.0 Oct 16 2009
Mar 10 13:38:38 ubuntu kernel: [  156.138018] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
Mar 10 13:38:38 ubuntu kernel: [  156.138144] EDAC amd64: ECC is enabled by BIOS, Proceeding with EDAC module initialization
Mar 10 13:38:38 ubuntu kernel: [  156.138189] EDAC MC: Rev E or earlier detected
Mar 10 13:38:38 ubuntu kernel: [  156.138252] EDAC MC0: Giving out device to 'amd64_edac' 'RevF': DEV 0000:00:18.2
Mar 10 13:38:38 ubuntu kernel: [  156.138280] EDAC PCI0: Giving out device to module 'amd64_edac' controller 'EDAC PCI controller': DEV '0000:00:18.2' (POLLED)
Mar 10 13:38:41 ubuntu kernel: [  158.506613] skge eth0: enabling interface
Mar 10 13:38:41 ubuntu kernel: [  158.510127] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 10 13:38:41 ubuntu kernel: [  159.146016] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 10 13:38:42 ubuntu kernel: [  160.340391] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
Mar 10 13:38:42 ubuntu kernel: [  160.340744] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar 10 13:38:44 ubuntu kernel: [  161.563157] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
Mar 10 13:38:44 ubuntu kernel: [  161.563168]   alloc irq_desc for 22 on node 0
Mar 10 13:38:44 ubuntu kernel: [  161.563171]   alloc kstat_irqs on node 0
Mar 10 13:38:44 ubuntu kernel: [  161.563182] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Mar 10 13:38:44 ubuntu kernel: [  162.310023] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
Mar 10 13:38:45 ubuntu kernel: [  162.830245] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
Mar 10 13:38:45 ubuntu kernel: [  162.830291] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
Mar 10 13:38:45 ubuntu kernel: [  162.830420] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Mar 10 13:38:45 ubuntu kernel: [  162.830598] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
Mar 10 13:38:50 ubuntu kernel: [  168.355409] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:50 ubuntu kernel: [  168.355415] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:50 ubuntu kernel: [  168.355420] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:50 ubuntu kernel: [  168.355430] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:50 ubuntu kernel: [  168.355436] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:38:50 ubuntu kernel: [  168.355441] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:38:52 ubuntu kernel: [  169.944416] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:52 ubuntu kernel: [  169.944420] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:52 ubuntu kernel: [  169.944423] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:52 ubuntu kernel: [  169.944429] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:52 ubuntu kernel: [  169.944432] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:38:53 ubuntu kernel: [  170.930014] eth0: no IPv6 routers present
Mar 10 13:38:56 ubuntu kernel: [  173.555210] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 10 13:38:56 ubuntu kernel: [  173.555213] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:56 ubuntu kernel: [  173.555216] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 10 13:38:56 ubuntu kernel: [  173.555220] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Mar 10 13:38:56 ubuntu kernel: [  173.555223] end_request: I/O error, dev sr0, sector 1414756
Mar 10 13:38:56 ubuntu kernel: [  173.555226] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:38:57 ubuntu kernel: [  175.389449] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:57 ubuntu kernel: [  175.389455] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:57 ubuntu kernel: [  175.389460] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:57 ubuntu kernel: [  175.389470] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:57 ubuntu kernel: [  175.389476] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:38:57 ubuntu kernel: [  175.389480] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:38:58 ubuntu kernel: [  175.908757] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:38:58 ubuntu kernel: [  175.908761] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:38:58 ubuntu kernel: [  175.908764] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:38:58 ubuntu kernel: [  175.908769] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:38:58 ubuntu kernel: [  175.908772] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:02 ubuntu kernel: [  179.527419] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 10 13:39:02 ubuntu kernel: [  179.527421] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:02 ubuntu kernel: [  179.527425] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 10 13:39:02 ubuntu kernel: [  179.527429] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Mar 10 13:39:02 ubuntu kernel: [  179.527432] end_request: I/O error, dev sr0, sector 1414756
Mar 10 13:39:02 ubuntu kernel: [  179.527435] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:03 ubuntu kernel: [  181.254573] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:03 ubuntu kernel: [  181.254579] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:03 ubuntu kernel: [  181.254583] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:03 ubuntu kernel: [  181.254593] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:03 ubuntu kernel: [  181.254598] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:03 ubuntu kernel: [  181.254602] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:04 ubuntu kernel: [  181.781743] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:04 ubuntu kernel: [  181.781747] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:04 ubuntu kernel: [  181.781750] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:04 ubuntu kernel: [  181.781756] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:04 ubuntu kernel: [  181.781759] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:07 ubuntu kernel: [  185.400419] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 10 13:39:07 ubuntu kernel: [  185.400421] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:07 ubuntu kernel: [  185.400424] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 10 13:39:07 ubuntu kernel: [  185.400428] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Mar 10 13:39:07 ubuntu kernel: [  185.400432] end_request: I/O error, dev sr0, sector 1414756
Mar 10 13:39:07 ubuntu kernel: [  185.400435] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:09 ubuntu kernel: [  186.776013] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:09 ubuntu kernel: [  186.776017] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:09 ubuntu kernel: [  186.776021] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:09 ubuntu kernel: [  186.776026] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:09 ubuntu kernel: [  186.776029] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:09 ubuntu kernel: [  186.776033] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:12 ubuntu kernel: [  189.819669] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:12 ubuntu kernel: [  189.819675] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:12 ubuntu kernel: [  189.819680] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:12 ubuntu kernel: [  189.819688] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:12 ubuntu kernel: [  189.819694] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:12 ubuntu kernel: [  189.819699] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:12 ubuntu kernel: [  190.354681] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:12 ubuntu kernel: [  190.354684] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:12 ubuntu kernel: [  190.354688] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:12 ubuntu kernel: [  190.354693] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:12 ubuntu kernel: [  190.354696] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:16 ubuntu kernel: [  193.965459] sr 1:0:0:0: [sr0] Unhandled sense code
Mar 10 13:39:16 ubuntu kernel: [  193.965462] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:16 ubuntu kernel: [  193.965465] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar 10 13:39:16 ubuntu kernel: [  193.965470] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Mar 10 13:39:16 ubuntu kernel: [  193.965474] end_request: I/O error, dev sr0, sector 1414756
Mar 10 13:39:16 ubuntu kernel: [  193.965479] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:21 ubuntu kernel: [  199.360503] usplash:356 freeing invalid memtype fffffffff0000000-fffffffff4000000
Mar 10 13:39:24 ubuntu kernel: [  202.218815] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:24 ubuntu kernel: [  202.218821] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:24 ubuntu kernel: [  202.218826] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:24 ubuntu kernel: [  202.218836] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:24 ubuntu kernel: [  202.218914] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:24 ubuntu kernel: [  202.218987] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:25 ubuntu kernel: [  202.753837] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:25 ubuntu kernel: [  202.753841] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:25 ubuntu kernel: [  202.753845] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:25 ubuntu kernel: [  202.753849] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:25 ubuntu kernel: [  202.753922] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:25 ubuntu kernel: [  202.753996] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:26 ubuntu kernel: [  204.256999] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:26 ubuntu kernel: [  204.257002] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:26 ubuntu kernel: [  204.257006] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:26 ubuntu kernel: [  204.257011] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:26 ubuntu kernel: [  204.257083] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:26 ubuntu kernel: [  204.257156] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:27 ubuntu kernel: [  204.774964] lp: driver loaded but no devices found
Mar 10 13:39:28 ubuntu kernel: [  205.695910] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:28 ubuntu kernel: [  205.695916] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:28 ubuntu kernel: [  205.695921] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:28 ubuntu kernel: [  205.695930] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:28 ubuntu kernel: [  205.696009] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:28 ubuntu kernel: [  205.696083] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:28 ubuntu kernel: [  206.223116] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:28 ubuntu kernel: [  206.223120] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:28 ubuntu kernel: [  206.223124] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:28 ubuntu kernel: [  206.223128] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:28 ubuntu kernel: [  206.223200] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:30 ubuntu kernel: [  207.564756] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:30 ubuntu kernel: [  207.564760] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:30 ubuntu kernel: [  207.564764] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:30 ubuntu kernel: [  207.564769] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:30 ubuntu kernel: [  207.564841] __ratelimit: 1 callbacks suppressed
Mar 10 13:39:30 ubuntu kernel: [  207.564843] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:30 ubuntu kernel: [  207.564918] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:30 ubuntu kernel: [  208.091925] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:30 ubuntu kernel: [  208.091929] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:30 ubuntu kernel: [  208.091933] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:30 ubuntu kernel: [  208.091937] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:30 ubuntu kernel: [  208.092009] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:30 ubuntu kernel: [  208.092084] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:32 ubuntu kernel: [  209.892941] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 10 13:39:32 ubuntu kernel: [  209.892944] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar 10 13:39:32 ubuntu kernel: [  209.892948] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Mar 10 13:39:32 ubuntu kernel: [  209.892954] end_request: I/O error, dev sr0, sector 1414752
Mar 10 13:39:32 ubuntu kernel: [  209.893027] Buffer I/O error on device sr0, logical block 353688
Mar 10 13:39:32 ubuntu kernel: [  209.893101] Buffer I/O error on device sr0, logical block 353689
Mar 10 13:39:34 ubuntu kernel: [  211.936180] ppdev: user-space parallel port driver



Thanks

---

