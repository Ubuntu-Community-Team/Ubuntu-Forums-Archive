---
title: "Installation Failed - Unrecoverable Error - 10.04"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by LeonardChallis on 2010-06-28
Hi everyone.

I've been using Ubuntu for a number of years -- never had a problem like this unfortunately so I'm not really sure of the problem. As a few other people I've seen on the forum have reported, I'm getting the following error when booting from the 10.04 live CD:

Installation Failed. The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.

I checked the CD for defects, and even tried re-downloading/burning to a new disc, but got the same problem. I tried booting in to the LIVE session then installing from the desktop but I still got the same error.

I have had 9.10 running on here fine, and after running a Kubuntu 9.10 disc I had to hand to check it would work, that installed fine (hence the auto-partitions you will see in my info dump below).

Here is some information about my system, let me know if I've missed anything. I've also included a copy of the syslog below.

```
ubuntu@ubuntu:~$ lspci | grep VGA
03:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 47
model name    : AMD Athlon(tm) 64 Processor 3200+
stepping    : 0
cpu MHz        : 2008.973
cache size    : 512 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good extd_apicid pni lahf_lm
bogomips    : 4017.94
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

ubuntu@ubuntu:~$ cat /proc/meminfo
MemTotal:        4060612 kB
MemFree:         3216380 kB
Buffers:           88632 kB
Cached:           353116 kB
SwapCached:            0 kB
Active:           309328 kB
Inactive:         341596 kB
Active(anon):     228220 kB
Inactive(anon):        0 kB
Active(file):      81108 kB
Inactive(file):   341596 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       3317380 kB
SwapFree:        3317380 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        209172 kB
Mapped:            51888 kB
Shmem:             19048 kB
Slab:              64280 kB
SReclaimable:      45108 kB
SUnreclaim:        19172 kB
KernelStack:        1888 kB
PageTables:        19572 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     5347684 kB
Committed_AS:     594512 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      299144 kB
VmallocChunk:   34359435236 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:        9920 kB
DirectMap2M:     4184064 kB
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c4d7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9598    77095903+  83  Linux
/dev/sda2            9599       10011     3317422+   5  Extended
/dev/sda5            9599       10011     3317391   82  Linux swap / Solaris

Unable to seek on /dev/sdb

```


/var/log/syslog:

```
Jun 28 19:21:08 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 28 19:21:08 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1238" x-info="http://www.rsyslog.com"] (re)start
Jun 28 19:21:08 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Jun 28 19:21:08 ubuntu rsyslogd: rsyslogd's userid changed to 101
Jun 28 19:21:08 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
Jun 28 19:21:09 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Jun 28 19:21:09 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009bc00 - 000000000009c000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e9b90 - 0000000000100000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffb0000 (usable)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bffb0000 - 00000000bffbe000 (ACPI data)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bffbe000 - 00000000bffe0000 (ACPI NVS)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] DMI 2.3 present.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Jun 28 19:21:09 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   A0000-EFFFF uncachable
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 28 19:21:09 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FF00000000 write-back
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   1 base 0100000000 mask FFC0000000 write-back
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   2 base 00C0000000 mask FFC0000000 uncachable
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   3 disabled
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   4 disabled
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   5 disabled
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   6 disabled
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   7 disabled
Jun 28 19:21:09 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 28 19:21:09 ubuntu kernel: [    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] last_pfn = 0xbffb0 max_arch_pfn = 0x400000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun 28 19:21:09 ubuntu kernel: [    0.000000] modified physical RAM map:
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009bc00 (usable)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 000000000009bc00 - 000000000009c000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 00000000000e9b90 - 0000000000100000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000bffb0000 (usable)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 00000000bffb0000 - 00000000bffbe000 (ACPI data)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 00000000bffbe000 - 00000000bffe0000 (ACPI NVS)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bffb0000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  00bfe00000 - 00bffb0000 page 4k
Jun 28 19:21:09 ubuntu kernel: [    0.000000] kernel direct mapping tables up to bffb0000 @ 10000-15000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  0100000000 - 0140000000 page 2M
Jun 28 19:21:09 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 140000000 @ 13000-19000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] RAMDISK: 7f69e000 - 7ffffcaf
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000fb520 00024 (v02 ACPIAM)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: XSDT 00000000bffb0100 00044 (v01 A M I  OEMXSDT  07000613 MSFT 00000097)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: FACP 00000000bffb0290 000F4 (v03 A M I  OEMFACP  07000613 MSFT 00000097)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: DSDT 00000000bffb0440 06A09 (v01  A0371 A0371001 00000001 INTL 02002026)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: FACS 00000000bffbe000 00040
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: APIC 00000000bffb0390 00070 (v01 A M I  OEMAPIC  07000613 MSFT 00000097)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: MCFG 00000000bffb0400 0003C (v01 A M I  OEMMCFG  07000613 MSFT 00000097)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: OEMB 00000000bffbe040 00056 (v01 A M I  AMI_OEM  07000613 MSFT 00000097)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jun 28 19:21:09 ubuntu kernel: [    0.000000] No NUMA configuration found
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28
Jun 28 19:21:09 ubuntu kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   #3 [007f69e000 - 007ffffcaf]          RAMDISK ==> [007f69e000 - 007ffffcaf]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   #4 [000009bc00 - 0000100000]    BIOS reserved ==> [000009bc00 - 0000100000]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a298]              BRK ==> [0001a2a000 - 0001a2a298]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]
Jun 28 19:21:09 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 28 19:21:09 ubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Zone PFN ranges:
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Jun 28 19:21:09 ubuntu kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 28 19:21:09 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009b
Jun 28 19:21:09 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000bffb0
Jun 28 19:21:09 ubuntu kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] On node 0 totalpages: 1048379
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   DMA zone: 107 pages reserved
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   DMA zone: 3816 pages, LIFO batch:0
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   DMA32 zone: 767976 pages, LIFO batch:31
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   Normal zone: 3584 pages used for memmap
Jun 28 19:21:09 ubuntu kernel: [    0.000000]   Normal zone: 258560 pages, LIFO batch:31
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x508
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jun 28 19:21:09 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 28 19:21:09 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jun 28 19:21:09 ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000ea000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000ea000 - 0000000000100000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bffb0000 - 00000000bffbe000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bffbe000 - 00000000bffe0000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fec00000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000ff700000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 28 19:21:09 ubuntu kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
Jun 28 19:21:09 ubuntu kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
Jun 28 19:21:09 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030352
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Policy zone: Normal
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Initializing CPU#0
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Checking aperture...
Jun 28 19:21:09 ubuntu kernel: [    0.000000] No AGP bridge found
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Node 0: aperture @ 1114000000 size 32 MB
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jun 28 19:21:09 ubuntu kernel: [    0.000000] This costs you 64 MB of RAM
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Memory: 4050128k/5242880k available (5409k kernel code, 1049364k absent, 143388k reserved, 2976k data, 876k init)
Jun 28 19:21:09 ubuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Jun 28 19:21:09 ubuntu kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Jun 28 19:21:09 ubuntu kernel: [    0.000000] console [tty0] enabled
Jun 28 19:21:09 ubuntu kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Jun 28 19:21:09 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Jun 28 19:21:09 ubuntu kernel: [    0.000000] Detected 2008.973 MHz processor.
Jun 28 19:21:09 ubuntu kernel: [    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4017.94 BogoMIPS (lpj=20089730)
Jun 28 19:21:09 ubuntu kernel: [    0.010034] Security Framework initialized
Jun 28 19:21:09 ubuntu kernel: [    0.010056] AppArmor: AppArmor initialized
Jun 28 19:21:09 ubuntu kernel: [    0.010445] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 28 19:21:09 ubuntu kernel: [    0.022095] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 28 19:21:09 ubuntu kernel: [    0.023333] Mount-cache hash table entries: 256
Jun 28 19:21:09 ubuntu kernel: [    0.023487] Initializing cgroup subsys ns
Jun 28 19:21:09 ubuntu kernel: [    0.023492] Initializing cgroup subsys cpuacct
Jun 28 19:21:09 ubuntu kernel: [    0.023496] Initializing cgroup subsys memory
Jun 28 19:21:09 ubuntu kernel: [    0.023504] Initializing cgroup subsys devices
Jun 28 19:21:09 ubuntu kernel: [    0.023507] Initializing cgroup subsys freezer
Jun 28 19:21:09 ubuntu kernel: [    0.023509] Initializing cgroup subsys net_cls
Jun 28 19:21:09 ubuntu kernel: [    0.023530] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 28 19:21:09 ubuntu kernel: [    0.023532] CPU: L2 Cache: 512K (64 bytes/line)
Jun 28 19:21:09 ubuntu kernel: [    0.023535] CPU 0/0x0 -> Node 0
Jun 28 19:21:09 ubuntu kernel: [    0.023537] tseg: 0000000000
Jun 28 19:21:09 ubuntu kernel: [    0.023554] mce: CPU supports 5 MCE banks
Jun 28 19:21:09 ubuntu kernel: [    0.023565] Performance Events: AMD PMU driver.
Jun 28 19:21:09 ubuntu kernel: [    0.023570] ... version:                0
Jun 28 19:21:09 ubuntu kernel: [    0.023571] ... bit width:              48
Jun 28 19:21:09 ubuntu kernel: [    0.023573] ... generic registers:      4
Jun 28 19:21:09 ubuntu kernel: [    0.023575] ... value mask:             0000ffffffffffff
Jun 28 19:21:09 ubuntu kernel: [    0.023577] ... max period:             00007fffffffffff
Jun 28 19:21:09 ubuntu kernel: [    0.023579] ... fixed-purpose events:   0
Jun 28 19:21:09 ubuntu kernel: [    0.023581] ... event mask:             000000000000000f
Jun 28 19:21:09 ubuntu kernel: [    0.023594] SMP alternatives: switching to UP code
Jun 28 19:21:09 ubuntu kernel: [    0.032554] ACPI: Core revision 20090903
Jun 28 19:21:09 ubuntu kernel: [    0.040914] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun 28 19:21:09 ubuntu kernel: [    0.040920] ftrace: allocating 22518 entries in 89 pages
Jun 28 19:21:09 ubuntu kernel: [    0.046379] Setting APIC routing to flat
Jun 28 19:21:09 ubuntu kernel: [    0.046730] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Jun 28 19:21:09 ubuntu kernel: [    0.146745] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
Jun 28 19:21:09 ubuntu kernel: [    0.150000] Brought up 1 CPUs
Jun 28 19:21:09 ubuntu kernel: [    0.150000] Total of 1 processors activated (4017.94 BogoMIPS).
Jun 28 19:21:09 ubuntu kernel: [    0.150000] CPU0 attaching NULL sched-domain.
Jun 28 19:21:09 ubuntu kernel: [    0.150000] devtmpfs: initialized
Jun 28 19:21:09 ubuntu kernel: [    0.150000] regulator: core version 0.5
Jun 28 19:21:09 ubuntu kernel: [    0.150000] Time: 19:20:07  Date: 06/28/10
Jun 28 19:21:09 ubuntu kernel: [    0.150000] NET: Registered protocol family 16
Jun 28 19:21:09 ubuntu kernel: [    0.150000] node 0 link 0: io port [1000, ffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] TOM: 00000000c0000000 aka 3072M
Jun 28 19:21:09 ubuntu kernel: [    0.150000] node 0 link 0: mmio [e0000000, efffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] node 0 link 0: mmio [dfbf0000, dfbfffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] node 0 link 0: mmio [a0000, bffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] node 0 link 0: mmio [c0000000, fe0bffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] TOM2: 0000000140000000 aka 5120M
Jun 28 19:21:09 ubuntu kernel: [    0.150000] bus: [00,ff] on node 0 link 0
Jun 28 19:21:09 ubuntu kernel: [    0.150000] bus: 00 index 0 io port: [0, ffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] bus: 00 index 1 mmio: [c0000000, ffffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] bus: 00 index 2 mmio: [dfbf0000, dfbfffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] bus: 00 index 3 mmio: [a0000, bffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] bus: 00 index 4 mmio: [140000000, fcffffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.150000] ACPI: bus type pci registered
Jun 28 19:21:09 ubuntu kernel: [    0.150000] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 28 19:21:09 ubuntu kernel: [    0.150000] PCI: Not using MMCONFIG.
Jun 28 19:21:09 ubuntu kernel: [    0.150000] PCI: Using configuration type 1 for base access
Jun 28 19:21:09 ubuntu kernel: [    0.150000] bio: create slab <bio-0> at 0
Jun 28 19:21:09 ubuntu kernel: [    0.150000] ACPI: EC: Look up EC in DSDT
Jun 28 19:21:09 ubuntu kernel: [    0.150000] ACPI: Executed 1 blocks of module-level executable AML code
Jun 28 19:21:09 ubuntu kernel: [    0.152988] ACPI: Interpreter enabled
Jun 28 19:21:09 ubuntu kernel: [    0.152993] ACPI: (supports S0 S1 S3 S4 S5)
Jun 28 19:21:09 ubuntu kernel: [    0.153016] ACPI: Using IOAPIC for interrupt routing
Jun 28 19:21:09 ubuntu kernel: [    0.153076] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 28 19:21:09 ubuntu kernel: [    0.161112] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jun 28 19:21:09 ubuntu kernel: [    0.171729] PCI: Using MMCONFIG at e0000000 - efffffff
Jun 28 19:21:09 ubuntu kernel: [    0.184168] ACPI Warning: Incorrect checksum in table [OEMB] - 58, should be 2A (20090903/tbutils-314)
Jun 28 19:21:09 ubuntu kernel: [    0.184293] ACPI: No dock devices found.
Jun 28 19:21:09 ubuntu kernel: [    0.184418] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 28 19:21:09 ubuntu kernel: [    0.184684] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.184687] pci 0000:00:02.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.184725] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.184728] pci 0000:00:03.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.184763] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.184766] pci 0000:00:04.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.184857] HPET not enabled in BIOS. You might try hpet=force boot option
Jun 28 19:21:09 ubuntu kernel: [    0.184877] pci 0000:00:0a.1: reg 10 io port: [0xbc00-0xbc1f]
Jun 28 19:21:09 ubuntu kernel: [    0.184888] pci 0000:00:0a.1: reg 20 io port: [0x600-0x63f]
Jun 28 19:21:09 ubuntu kernel: [    0.184892] pci 0000:00:0a.1: reg 24 io port: [0x700-0x73f]
Jun 28 19:21:09 ubuntu kernel: [    0.184904] pci 0000:00:0a.1: PME# supported from D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.184907] pci 0000:00:0a.1: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.184932] pci 0000:00:0b.0: reg 10 32bit mmio: [0xdfbfe000-0xdfbfefff]
Jun 28 19:21:09 ubuntu kernel: [    0.184953] pci 0000:00:0b.0: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.184955] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.184958] pci 0000:00:0b.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.184981] pci 0000:00:0b.1: reg 10 32bit mmio: [0xdfbffc00-0xdfbffcff]
Jun 28 19:21:09 ubuntu kernel: [    0.185006] pci 0000:00:0b.1: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.185008] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.185012] pci 0000:00:0b.1: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.185038] pci 0000:00:0d.0: reg 10 io port: [0xb400-0xb4ff]
Jun 28 19:21:09 ubuntu kernel: [    0.185042] pci 0000:00:0d.0: reg 14 io port: [0xb000-0xb0ff]
Jun 28 19:21:09 ubuntu kernel: [    0.185047] pci 0000:00:0d.0: reg 18 32bit mmio: [0xdfbfd000-0xdfbfdfff]
Jun 28 19:21:09 ubuntu kernel: [    0.185065] pci 0000:00:0d.0: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.185093] pci 0000:00:0f.0: reg 20 io port: [0xffa0-0xffaf]
Jun 28 19:21:09 ubuntu kernel: [    0.185123] pci 0000:00:10.0: reg 10 io port: [0xac00-0xac07]
Jun 28 19:21:09 ubuntu kernel: [    0.185127] pci 0000:00:10.0: reg 14 io port: [0xa880-0xa883]
Jun 28 19:21:09 ubuntu kernel: [    0.185132] pci 0000:00:10.0: reg 18 io port: [0xa800-0xa807]
Jun 28 19:21:09 ubuntu kernel: [    0.185136] pci 0000:00:10.0: reg 1c io port: [0xa480-0xa483]
Jun 28 19:21:09 ubuntu kernel: [    0.185140] pci 0000:00:10.0: reg 20 io port: [0xa400-0xa40f]
Jun 28 19:21:09 ubuntu kernel: [    0.185145] pci 0000:00:10.0: reg 24 32bit mmio: [0xdfbfc000-0xdfbfcfff]
Jun 28 19:21:09 ubuntu kernel: [    0.185173] pci 0000:00:11.0: reg 10 io port: [0xa080-0xa087]
Jun 28 19:21:09 ubuntu kernel: [    0.185177] pci 0000:00:11.0: reg 14 io port: [0xa000-0xa003]
Jun 28 19:21:09 ubuntu kernel: [    0.185181] pci 0000:00:11.0: reg 18 io port: [0x9c00-0x9c07]
Jun 28 19:21:09 ubuntu kernel: [    0.185186] pci 0000:00:11.0: reg 1c io port: [0x9880-0x9883]
Jun 28 19:21:09 ubuntu kernel: [    0.185190] pci 0000:00:11.0: reg 20 io port: [0x9800-0x980f]
Jun 28 19:21:09 ubuntu kernel: [    0.185195] pci 0000:00:11.0: reg 24 32bit mmio: [0xdfbfb000-0xdfbfbfff]
Jun 28 19:21:09 ubuntu kernel: [    0.185238] pci 0000:00:13.0: reg 10 32bit mmio: [0xdfbfa000-0xdfbfafff]
Jun 28 19:21:09 ubuntu kernel: [    0.185242] pci 0000:00:13.0: reg 14 io port: [0x9480-0x9487]
Jun 28 19:21:09 ubuntu kernel: [    0.185262] pci 0000:00:13.0: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.185264] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.185267] pci 0000:00:13.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.185309] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.185311] pci 0000:00:16.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.185352] pci 0000:00:17.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.185355] pci 0000:00:17.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.185484] pci 0000:01:00.0: reg 10 64bit mmio: [0xdfcffc00-0xdfcffc7f]
Jun 28 19:21:09 ubuntu kernel: [    0.185498] pci 0000:01:00.0: reg 18 64bit mmio: [0xdfcf8000-0xdfcfbfff]
Jun 28 19:21:09 ubuntu kernel: [    0.185506] pci 0000:01:00.0: reg 20 io port: [0xcc00-0xcc7f]
Jun 28 19:21:09 ubuntu kernel: [    0.185519] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xdfc00000-0xdfc7ffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185551] pci 0000:01:00.0: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.185597] pci 0000:00:02.0: bridge io port: [0xc000-0xcfff]
Jun 28 19:21:09 ubuntu kernel: [    0.185600] pci 0000:00:02.0: bridge 32bit mmio: [0xdfc00000-0xdfcfffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185641] pci 0000:02:00.0: reg 10 64bit mmio: [0xdfdfc000-0xdfdfffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185647] pci 0000:02:00.0: reg 18 io port: [0xd800-0xd8ff]
Jun 28 19:21:09 ubuntu kernel: [    0.185664] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xdfdc0000-0xdfddffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185690] pci 0000:02:00.0: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.185692] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 28 19:21:09 ubuntu kernel: [    0.185696] pci 0000:02:00.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.185736] pci 0000:00:03.0: bridge io port: [0xd000-0xdfff]
Jun 28 19:21:09 ubuntu kernel: [    0.185739] pci 0000:00:03.0: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185766] pci 0000:03:00.0: reg 10 64bit mmio pref: [0xc0000000-0xcfffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185773] pci 0000:03:00.0: reg 18 64bit mmio: [0xdfee0000-0xdfeeffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185778] pci 0000:03:00.0: reg 20 io port: [0xe000-0xe0ff]
Jun 28 19:21:09 ubuntu kernel: [    0.185786] pci 0000:03:00.0: reg 30 32bit mmio pref: [0xdfec0000-0xdfedffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185801] pci 0000:03:00.0: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.185828] pci 0000:03:00.1: reg 10 64bit mmio: [0xdfefc000-0xdfefffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185856] pci 0000:03:00.1: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.185899] pci 0000:00:04.0: bridge io port: [0xe000-0xefff]
Jun 28 19:21:09 ubuntu kernel: [    0.185902] pci 0000:00:04.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185906] pci 0000:00:04.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185944] pci 0000:04:0b.0: reg 10 32bit mmio: [0xdffff800-0xdfffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.185950] pci 0000:04:0b.0: reg 14 32bit mmio: [0xdfff8000-0xdfffbfff]
Jun 28 19:21:09 ubuntu kernel: [    0.185981] pci 0000:04:0b.0: supports D1 D2
Jun 28 19:21:09 ubuntu kernel: [    0.185983] pci 0000:04:0b.0: PME# supported from D0 D1 D2 D3hot
Jun 28 19:21:09 ubuntu kernel: [    0.185987] pci 0000:04:0b.0: PME# disabled
Jun 28 19:21:09 ubuntu kernel: [    0.186012] pci 0000:00:12.0: transparent bridge
Jun 28 19:21:09 ubuntu kernel: [    0.186016] pci 0000:00:12.0: bridge 32bit mmio: [0xdff00000-0xdfffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.186110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 28 19:21:09 ubuntu kernel: [    0.186379] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2P._PRT]
Jun 28 19:21:09 ubuntu kernel: [    0.186501] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE0._PRT]
Jun 28 19:21:09 ubuntu kernel: [    0.186573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE1._PRT]
Jun 28 19:21:09 ubuntu kernel: [    0.186642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Jun 28 19:21:09 ubuntu kernel: [    0.186710] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE3._PRT]
Jun 28 19:21:09 ubuntu kernel: [    0.186778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Jun 28 19:21:09 ubuntu kernel: [    0.201238] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *10
Jun 28 19:21:09 ubuntu kernel: [    0.201467] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *10
Jun 28 19:21:09 ubuntu kernel: [    0.201693] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
Jun 28 19:21:09 ubuntu kernel: [    0.201919] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Jun 28 19:21:09 ubuntu kernel: [    0.202146] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
Jun 28 19:21:09 ubuntu kernel: [    0.202372] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
Jun 28 19:21:09 ubuntu kernel: [    0.202598] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
Jun 28 19:21:09 ubuntu kernel: [    0.202824] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *10
Jun 28 19:21:09 ubuntu kernel: [    0.203050] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
Jun 28 19:21:09 ubuntu kernel: [    0.203277] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
Jun 28 19:21:09 ubuntu kernel: [    0.203508] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
Jun 28 19:21:09 ubuntu kernel: [    0.203742] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *11
Jun 28 19:21:09 ubuntu kernel: [    0.204023] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Jun 28 19:21:09 ubuntu kernel: [    0.204162] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 28 19:21:09 ubuntu kernel: [    0.204165] vgaarb: loaded
Jun 28 19:21:09 ubuntu kernel: [    0.204275] SCSI subsystem initialized
Jun 28 19:21:09 ubuntu kernel: [    0.204346] libata version 3.00 loaded.
Jun 28 19:21:09 ubuntu kernel: [    0.204413] usbcore: registered new interface driver usbfs
Jun 28 19:21:09 ubuntu kernel: [    0.204424] usbcore: registered new interface driver hub
Jun 28 19:21:09 ubuntu kernel: [    0.204446] usbcore: registered new device driver usb
Jun 28 19:21:09 ubuntu kernel: [    0.204561] ACPI: WMI: Mapper loaded
Jun 28 19:21:09 ubuntu kernel: [    0.204562] PCI: Using ACPI for IRQ routing
Jun 28 19:21:09 ubuntu kernel: [    0.204724] NetLabel: Initializing
Jun 28 19:21:09 ubuntu kernel: [    0.204726] NetLabel:  domain hash size = 128
Jun 28 19:21:09 ubuntu kernel: [    0.204727] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 28 19:21:09 ubuntu kernel: [    0.204740] NetLabel:  unlabeled traffic allowed by default
Jun 28 19:21:09 ubuntu kernel: [    0.206268] AppArmor: AppArmor Filesystem Enabled
Jun 28 19:21:09 ubuntu kernel: [    0.206285] pnp: PnP ACPI init
Jun 28 19:21:09 ubuntu kernel: [    0.206302] ACPI: bus type pnp registered
Jun 28 19:21:09 ubuntu kernel: [    0.215546] pnp: PnP ACPI: found 16 devices
Jun 28 19:21:09 ubuntu kernel: [    0.215548] ACPI: ACPI bus type pnp unregistered
Jun 28 19:21:09 ubuntu kernel: [    0.215562] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215565] system 00:09: ioport range 0x800-0x80f has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215568] system 00:09: ioport range 0x500-0x57f has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215571] system 00:09: ioport range 0x580-0x5ff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215575] system 00:09: ioport range 0x800-0x87f could not be reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215578] system 00:09: ioport range 0x880-0x8ff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215580] system 00:09: ioport range 0x900-0x97f has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215583] system 00:09: ioport range 0x980-0x9ff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215587] system 00:09: iomem range 0xfee01000-0xfeefffff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215590] system 00:09: iomem range 0xfefff000-0xfeffffff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215594] system 00:09: iomem range 0xffb00000-0xfffeffff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215597] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215602] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215605] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215611] system 00:0d: ioport range 0xc00-0xc0f has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215614] system 00:0d: ioport range 0xd00-0xd0f has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215617] system 00:0d: ioport range 0xa20-0xa2f has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215620] system 00:0d: ioport range 0xa30-0xa3f has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215625] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215630] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215633] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215636] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Jun 28 19:21:09 ubuntu kernel: [    0.215639] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
Jun 28 19:21:09 ubuntu kernel: [    0.220338] Switching to clocksource acpi_pm
Jun 28 19:21:09 ubuntu kernel: [    0.220458] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Jun 28 19:21:09 ubuntu kernel: [    0.220461] pci 0000:00:02.0:   IO window: 0xc000-0xcfff
Jun 28 19:21:09 ubuntu kernel: [    0.220464] pci 0000:00:02.0:   MEM window: 0xdfc00000-0xdfcfffff
Jun 28 19:21:09 ubuntu kernel: [    0.220467] pci 0000:00:02.0:   PREFETCH window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220470] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
Jun 28 19:21:09 ubuntu kernel: [    0.220473] pci 0000:00:03.0:   IO window: 0xd000-0xdfff
Jun 28 19:21:09 ubuntu kernel: [    0.220476] pci 0000:00:03.0:   MEM window: 0xdfd00000-0xdfdfffff
Jun 28 19:21:09 ubuntu kernel: [    0.220479] pci 0000:00:03.0:   PREFETCH window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220482] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
Jun 28 19:21:09 ubuntu kernel: [    0.220485] pci 0000:00:04.0:   IO window: 0xe000-0xefff
Jun 28 19:21:09 ubuntu kernel: [    0.220488] pci 0000:00:04.0:   MEM window: 0xdfe00000-0xdfefffff
Jun 28 19:21:09 ubuntu kernel: [    0.220492] pci 0000:00:04.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Jun 28 19:21:09 ubuntu kernel: [    0.220496] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
Jun 28 19:21:09 ubuntu kernel: [    0.220498] pci 0000:00:12.0:   IO window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220501] pci 0000:00:12.0:   MEM window: 0xdff00000-0xdfffffff
Jun 28 19:21:09 ubuntu kernel: [    0.220504] pci 0000:00:12.0:   PREFETCH window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220508] pci 0000:00:16.0: PCI bridge, secondary bus 0000:05
Jun 28 19:21:09 ubuntu kernel: [    0.220510] pci 0000:00:16.0:   IO window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220513] pci 0000:00:16.0:   MEM window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220515] pci 0000:00:16.0:   PREFETCH window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220519] pci 0000:00:17.0: PCI bridge, secondary bus 0000:06
Jun 28 19:21:09 ubuntu kernel: [    0.220521] pci 0000:00:17.0:   IO window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220524] pci 0000:00:17.0:   MEM window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220527] pci 0000:00:17.0:   PREFETCH window: disabled
Jun 28 19:21:09 ubuntu kernel: [    0.220536] pci 0000:00:02.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    0.220541] pci 0000:00:03.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    0.220546] pci 0000:00:04.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    0.220551] pci 0000:00:12.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    0.220556] pci 0000:00:16.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    0.220562] pci 0000:00:17.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    0.220566] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220569] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220572] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
Jun 28 19:21:09 ubuntu kernel: [    0.220574] pci_bus 0000:01: resource 1 mem: [0xdfc00000-0xdfcfffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220577] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
Jun 28 19:21:09 ubuntu kernel: [    0.220579] pci_bus 0000:02: resource 1 mem: [0xdfd00000-0xdfdfffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220582] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
Jun 28 19:21:09 ubuntu kernel: [    0.220585] pci_bus 0000:03: resource 1 mem: [0xdfe00000-0xdfefffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220587] pci_bus 0000:03: resource 2 pref mem [0xc0000000-0xcfffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220590] pci_bus 0000:04: resource 1 mem: [0xdff00000-0xdfffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220593] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220595] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
Jun 28 19:21:09 ubuntu kernel: [    0.220633] NET: Registered protocol family 2
Jun 28 19:21:09 ubuntu kernel: [    0.220799] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 28 19:21:09 ubuntu kernel: [    0.222303] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 28 19:21:09 ubuntu kernel: [    0.227284] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 28 19:21:09 ubuntu kernel: [    0.227897] TCP: Hash tables configured (established 524288 bind 65536)
Jun 28 19:21:09 ubuntu kernel: [    0.227901] TCP reno registered
Jun 28 19:21:09 ubuntu kernel: [    0.228007] NET: Registered protocol family 1
Jun 28 19:21:09 ubuntu kernel: [    0.228036] pci 0000:00:00.0: Found disabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.228041] pci 0000:00:00.0: Enabling HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.228075] pci 0000:00:00.0: Found enabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.228097] pci 0000:00:00.0: Found enabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.228123] pci 0000:00:00.0: Found enabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.760111] pci 0000:00:09.0: Found enabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.760118] pci 0000:00:16.0: Found disabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.760123] pci 0000:00:00.0: Found enabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.760127] pci 0000:00:16.0: Linking AER extended capability
Jun 28 19:21:09 ubuntu kernel: [    0.760176] pci 0000:00:09.0: Found enabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.760182] pci 0000:00:17.0: Found disabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.760187] pci 0000:00:00.0: Found enabled HT MSI Mapping
Jun 28 19:21:09 ubuntu kernel: [    0.760190] pci 0000:00:17.0: Linking AER extended capability
Jun 28 19:21:09 ubuntu kernel: [    0.760204] pci 0000:03:00.0: Boot video device
Jun 28 19:21:09 ubuntu kernel: [    0.760410] PCI-DMA: Disabling AGP.
Jun 28 19:21:09 ubuntu kernel: [    0.760503] PCI-DMA: aperture base @ 20000000 size 65536 KB
Jun 28 19:21:09 ubuntu kernel: [    0.760505] PCI-DMA: using GART IOMMU.
Jun 28 19:21:09 ubuntu kernel: [    0.760509] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 28 19:21:09 ubuntu kernel: [    0.761176] Scanning for low memory corruption every 60 seconds
Jun 28 19:21:09 ubuntu kernel: [    0.761305] audit: initializing netlink socket (disabled)
Jun 28 19:21:09 ubuntu kernel: [    0.761317] type=2000 audit(1277752807.760:1): initialized
Jun 28 19:21:09 ubuntu kernel: [    0.770637] Trying to unpack rootfs image as initramfs...
Jun 28 19:21:09 ubuntu kernel: [    2.878637] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 28 19:21:09 ubuntu kernel: [    2.879974] VFS: Disk quotas dquot_6.5.2
Jun 28 19:21:09 ubuntu kernel: [    2.880058] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 28 19:21:09 ubuntu kernel: [    2.880712] fuse init (API version 7.13)
Jun 28 19:21:09 ubuntu kernel: [    2.880793] msgmni has been set to 7910
Jun 28 19:21:09 ubuntu kernel: [    2.880995] alg: No test for stdrng (krng)
Jun 28 19:21:09 ubuntu kernel: [    2.881050] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 28 19:21:09 ubuntu kernel: [    2.881053] io scheduler noop registered
Jun 28 19:21:09 ubuntu kernel: [    2.881055] io scheduler anticipatory registered
Jun 28 19:21:09 ubuntu kernel: [    2.881057] io scheduler deadline registered
Jun 28 19:21:09 ubuntu kernel: [    2.881092] io scheduler cfq registered (default)
Jun 28 19:21:09 ubuntu kernel: [    2.881254]   alloc irq_desc for 24 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881256]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881265] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
Jun 28 19:21:09 ubuntu kernel: [    2.881270] pcieport 0000:00:02.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.881366]   alloc irq_desc for 25 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881368]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881373] pcieport 0000:00:03.0: irq 25 for MSI/MSI-X
Jun 28 19:21:09 ubuntu kernel: [    2.881377] pcieport 0000:00:03.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.881470]   alloc irq_desc for 26 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881472]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881476] pcieport 0000:00:04.0: irq 26 for MSI/MSI-X
Jun 28 19:21:09 ubuntu kernel: [    2.881481] pcieport 0000:00:04.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.881584]   alloc irq_desc for 27 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881585]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881591] pcieport 0000:00:16.0: irq 27 for MSI/MSI-X
Jun 28 19:21:09 ubuntu kernel: [    2.881596] pcieport 0000:00:16.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.881694]   alloc irq_desc for 28 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881696]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.881701] pcieport 0000:00:17.0: irq 28 for MSI/MSI-X
Jun 28 19:21:09 ubuntu kernel: [    2.881706] pcieport 0000:00:17.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.881765] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 28 19:21:09 ubuntu kernel: [    2.881788] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 28 19:21:09 ubuntu kernel: [    2.881880] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jun 28 19:21:09 ubuntu kernel: [    2.881890] ACPI: Power Button [PWRB]
Jun 28 19:21:09 ubuntu kernel: [    2.881935] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 28 19:21:09 ubuntu kernel: [    2.881938] ACPI: Power Button [PWRF]
Jun 28 19:21:09 ubuntu kernel: [    2.882426] processor LNXCPU:00: registered as cooling_device0
Jun 28 19:21:09 ubuntu kernel: [    2.889128] Linux agpgart interface v0.103
Jun 28 19:21:09 ubuntu kernel: [    2.889162] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun 28 19:21:09 ubuntu kernel: [    2.889258] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 28 19:21:09 ubuntu kernel: [    2.889542] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 28 19:21:09 ubuntu kernel: [    2.890524] brd: module loaded
Jun 28 19:21:09 ubuntu kernel: [    2.890958] loop: module loaded
Jun 28 19:21:09 ubuntu kernel: [    2.891042] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun 28 19:21:09 ubuntu kernel: [    2.891278] pata_acpi 0000:00:0f.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.891661] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
Jun 28 19:21:09 ubuntu kernel: [    2.891666]   alloc irq_desc for 23 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.891668]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.891677] pata_acpi 0000:00:10.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
Jun 28 19:21:09 ubuntu kernel: [    2.891694] pata_acpi 0000:00:10.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.891701] pata_acpi 0000:00:10.0: PCI INT A disabled
Jun 28 19:21:09 ubuntu kernel: [    2.892052] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
Jun 28 19:21:09 ubuntu kernel: [    2.892054]   alloc irq_desc for 22 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.892056]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.892062] pata_acpi 0000:00:11.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
Jun 28 19:21:09 ubuntu kernel: [    2.892088] pata_acpi 0000:00:11.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.892095] pata_acpi 0000:00:11.0: PCI INT A disabled
Jun 28 19:21:09 ubuntu kernel: [    2.892442] Fixed MDIO Bus: probed
Jun 28 19:21:09 ubuntu kernel: [    2.892476] PPP generic driver version 2.4.2
Jun 28 19:21:09 ubuntu kernel: [    2.892523] tun: Universal TUN/TAP device driver, 1.6
Jun 28 19:21:09 ubuntu kernel: [    2.892525] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 28 19:21:09 ubuntu kernel: [    2.892607] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 28 19:21:09 ubuntu kernel: [    2.892957] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
Jun 28 19:21:09 ubuntu kernel: [    2.892960]   alloc irq_desc for 21 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.892962]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.892969] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
Jun 28 19:21:09 ubuntu kernel: [    2.892988] ehci_hcd 0000:00:0b.1: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.892991] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Jun 28 19:21:09 ubuntu kernel: [    2.893025] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Jun 28 19:21:09 ubuntu kernel: [    2.893062] ehci_hcd 0000:00:0b.1: debug port 1
Jun 28 19:21:09 ubuntu kernel: [    2.893067] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
Jun 28 19:21:09 ubuntu kernel: [    2.893086] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xdfbffc00
Jun 28 19:21:09 ubuntu kernel: [    2.910040] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
Jun 28 19:21:09 ubuntu kernel: [    2.910171] usb usb1: configuration #1 chosen from 1 choice
Jun 28 19:21:09 ubuntu kernel: [    2.910203] hub 1-0:1.0: USB hub found
Jun 28 19:21:09 ubuntu kernel: [    2.910217] hub 1-0:1.0: 10 ports detected
Jun 28 19:21:09 ubuntu kernel: [    2.910303] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 28 19:21:09 ubuntu kernel: [    2.920564] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
Jun 28 19:21:09 ubuntu kernel: [    2.920570]   alloc irq_desc for 20 on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.920572]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    2.920582] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
Jun 28 19:21:09 ubuntu kernel: [    2.920604] ohci_hcd 0000:00:0b.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    2.920607] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Jun 28 19:21:09 ubuntu kernel: [    2.920674] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Jun 28 19:21:09 ubuntu kernel: [    2.920705] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xdfbfe000
Jun 28 19:21:09 ubuntu kernel: [    3.284721] usb usb2: configuration #1 chosen from 1 choice
Jun 28 19:21:09 ubuntu kernel: [    3.284756] hub 2-0:1.0: USB hub found
Jun 28 19:21:09 ubuntu kernel: [    3.284767] hub 2-0:1.0: 10 ports detected
Jun 28 19:21:09 ubuntu kernel: [    3.284873] uhci_hcd: USB Universal Host Controller Interface driver
Jun 28 19:21:09 ubuntu kernel: [    3.284947] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jun 28 19:21:09 ubuntu kernel: [    3.284949] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jun 28 19:21:09 ubuntu kernel: [    3.285652] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 28 19:21:09 ubuntu kernel: [    3.285731] mice: PS/2 mouse device common for all mice
Jun 28 19:21:09 ubuntu kernel: [    3.285832] rtc_cmos 00:02: RTC can wake from S4
Jun 28 19:21:09 ubuntu kernel: [    3.285877] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jun 28 19:21:09 ubuntu kernel: [    3.285903] rtc0: alarms up to one year, y3k, 114 bytes nvram
Jun 28 19:21:09 ubuntu kernel: [    3.286035] device-mapper: uevent: version 1.0.3
Jun 28 19:21:09 ubuntu kernel: [    3.286184] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jun 28 19:21:09 ubuntu kernel: [    3.286233] device-mapper: multipath: version 1.1.0 loaded
Jun 28 19:21:09 ubuntu kernel: [    3.286236] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 28 19:21:09 ubuntu kernel: [    3.286360] cpuidle: using governor ladder
Jun 28 19:21:09 ubuntu kernel: [    3.286362] cpuidle: using governor menu
Jun 28 19:21:09 ubuntu kernel: [    3.286725] TCP cubic registered
Jun 28 19:21:09 ubuntu kernel: [    3.286853] NET: Registered protocol family 10
Jun 28 19:21:09 ubuntu kernel: [    3.287304] lo: Disabled Privacy Extensions
Jun 28 19:21:09 ubuntu kernel: [    3.287618] NET: Registered protocol family 17
Jun 28 19:21:09 ubuntu kernel: [    3.287648] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
Jun 28 19:21:09 ubuntu kernel: [    3.291024] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
Jun 28 19:21:09 ubuntu kernel: [    3.291210] PM: Resume from disk failed.
Jun 28 19:21:09 ubuntu kernel: [    3.291228] registered taskstats version 1
Jun 28 19:21:09 ubuntu kernel: [    3.291590]   Magic number: 14:391:345
Jun 28 19:21:09 ubuntu kernel: [    3.291605] tty tty62: hash matches
Jun 28 19:21:09 ubuntu kernel: [    3.291666] rtc_cmos 00:02: setting system clock to 2010-06-28 19:20:11 UTC (1277752811)
Jun 28 19:21:09 ubuntu kernel: [    3.291669] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 28 19:21:09 ubuntu kernel: [    3.291670] EDD information not available.
Jun 28 19:21:09 ubuntu kernel: [    3.300743] Freeing initrd memory: 9607k freed
Jun 28 19:21:09 ubuntu kernel: [    3.306281] Freeing unused kernel memory: 876k freed
Jun 28 19:21:09 ubuntu kernel: [    3.306778] Write protecting the kernel read-only data: 7680k
Jun 28 19:21:09 ubuntu kernel: [    3.308744] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jun 28 19:21:09 ubuntu kernel: [    3.331816] udev: starting version 151
Jun 28 19:21:09 ubuntu kernel: [    3.500054] usb 1-3: new high speed USB device using ehci_hcd and address 2
Jun 28 19:21:09 ubuntu kernel: [    3.544568] sky2 driver version 1.25
Jun 28 19:21:09 ubuntu kernel: [    3.572789] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
Jun 28 19:21:09 ubuntu kernel: [    3.572795]   alloc irq_desc for 19 on node 0
Jun 28 19:21:09 ubuntu kernel: [    3.572798]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    3.572808] sky2 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Jun 28 19:21:09 ubuntu kernel: [    3.572820] sky2 0000:02:00.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    3.572863] sky2 0000:02:00.0: Yukon-2 EC chip revision 2
Jun 28 19:21:09 ubuntu kernel: [    3.572916]   alloc irq_desc for 29 on node 0
Jun 28 19:21:09 ubuntu kernel: [    3.572918]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    3.572927] sky2 0000:02:00.0: irq 29 for MSI/MSI-X
Jun 28 19:21:09 ubuntu kernel: [    3.573642] sky2 eth0: addr 00:1a:92:1d:b9:f0
Jun 28 19:21:09 ubuntu kernel: [    3.573799] sata_sil24 0000:01:00.0: version 1.1
Jun 28 19:21:09 ubuntu kernel: [    3.574104] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
Jun 28 19:21:09 ubuntu kernel: [    3.574107]   alloc irq_desc for 18 on node 0
Jun 28 19:21:09 ubuntu kernel: [    3.574109]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    3.574117] sata_sil24 0000:01:00.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Jun 28 19:21:09 ubuntu kernel: [    3.574188] sata_sil24 0000:01:00.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    3.574586] scsi0 : sata_sil24
Jun 28 19:21:09 ubuntu kernel: [    3.574821] scsi1 : sata_sil24
Jun 28 19:21:09 ubuntu kernel: [    3.574906] ata1: SATA max UDMA/100 host m128@0xdfcffc00 port 0xdfcf8000 irq 18
Jun 28 19:21:09 ubuntu kernel: [    3.574910] ata2: SATA max UDMA/100 host m128@0xdfcffc00 port 0xdfcfa000 irq 18
Jun 28 19:21:09 ubuntu kernel: [    3.579637] Floppy drive(s): fd0 is 1.44M
Jun 28 19:21:09 ubuntu kernel: [    3.598409] [drm] Initialized drm 1.1.0 20060810
Jun 28 19:21:09 ubuntu kernel: [    3.598451] pata_amd 0000:00:0f.0: version 0.4.1
Jun 28 19:21:09 ubuntu kernel: [    3.598495] pata_amd 0000:00:0f.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    3.598578] scsi2 : pata_amd
Jun 28 19:21:09 ubuntu kernel: [    3.598743] scsi3 : pata_amd
Jun 28 19:21:09 ubuntu kernel: [    3.600301] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jun 28 19:21:09 ubuntu kernel: [    3.600304] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jun 28 19:21:09 ubuntu kernel: [    3.600630] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jun 28 19:21:09 ubuntu kernel: [    3.600918] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
Jun 28 19:21:09 ubuntu kernel: [    3.600923] forcedeth 0000:00:13.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
Jun 28 19:21:09 ubuntu kernel: [    3.600927] forcedeth 0000:00:13.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    3.600990] nv_probe: set workaround bit for reversed mac addr
Jun 28 19:21:09 ubuntu kernel: [    3.603889] FDC 0 is a post-1991 82077
Jun 28 19:21:09 ubuntu kernel: [    3.650563] usb 1-3: configuration #1 chosen from 1 choice
Jun 28 19:21:09 ubuntu kernel: [    3.650662] hub 1-3:1.0: USB hub found
Jun 28 19:21:09 ubuntu kernel: [    3.650874] hub 1-3:1.0: 4 ports detected
Jun 28 19:21:09 ubuntu kernel: [    4.110029] usb 2-4: new full speed USB device using ohci_hcd and address 2
Jun 28 19:21:09 ubuntu kernel: [    4.130802] forcedeth 0000:00:13.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:1a:92:1d:c1:58
Jun 28 19:21:09 ubuntu kernel: [    4.130806] forcedeth 0000:00:13.0: highdma csum gbit lnktim desc-v3
Jun 28 19:21:09 ubuntu kernel: [    4.131066] sata_nv 0000:00:10.0: version 3.5
Jun 28 19:21:09 ubuntu kernel: [    4.131078] sata_nv 0000:00:10.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
Jun 28 19:21:09 ubuntu kernel: [    4.131137] sata_nv 0000:00:10.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    4.131196] scsi4 : sata_nv
Jun 28 19:21:09 ubuntu kernel: [    4.131317] scsi5 : sata_nv
Jun 28 19:21:09 ubuntu kernel: [    4.131509] ata5: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 23
Jun 28 19:21:09 ubuntu kernel: [    4.131512] ata6: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 23
Jun 28 19:21:09 ubuntu kernel: [    4.131618] sata_nv 0000:00:11.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
Jun 28 19:21:09 ubuntu kernel: [    4.131656] sata_nv 0000:00:11.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    4.131730] scsi6 : sata_nv
Jun 28 19:21:09 ubuntu kernel: [    4.131980] scsi7 : sata_nv
Jun 28 19:21:09 ubuntu kernel: [    4.132153] ata7: SATA max UDMA/133 cmd 0xa080 ctl 0xa000 bmdma 0x9800 irq 22
Jun 28 19:21:09 ubuntu kernel: [    4.132156] ata8: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9808 irq 22
Jun 28 19:21:09 ubuntu kernel: [    4.336689] usb 2-4: configuration #1 chosen from 1 choice
Jun 28 19:21:09 ubuntu kernel: [    4.420252] usb 1-3.2: new low speed USB device using ehci_hcd and address 4
Jun 28 19:21:09 ubuntu kernel: [    4.460081] ata5: SATA link down (SStatus 0 SControl 300)
Jun 28 19:21:09 ubuntu kernel: [    4.537827] usb 1-3.2: configuration #1 chosen from 1 choice
Jun 28 19:21:09 ubuntu kernel: [    4.620038] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 28 19:21:09 ubuntu kernel: [    4.640299] ata7.00: ATA-7: HDS728080PLA380, PF2OA69A, max UDMA/133
Jun 28 19:21:09 ubuntu kernel: [    4.640303] ata7.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 28 19:21:09 ubuntu kernel: [    4.680306] ata7.00: configured for UDMA/133
Jun 28 19:21:09 ubuntu kernel: [    5.660036] ata1: SATA link down (SStatus 0 SControl 0)
Jun 28 19:21:09 ubuntu kernel: [    7.750028] ata2: SATA link down (SStatus 0 SControl 0)
Jun 28 19:21:09 ubuntu kernel: [    7.930302] ata4.00: ATAPI: Optiarc DVD RW AD-7170A, 1.02, max UDMA/66
Jun 28 19:21:09 ubuntu kernel: [    7.930326] ata4: nv_mode_filter: 0x1f39f&0x739f->0x739f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:900:0x11)
Jun 28 19:21:09 ubuntu kernel: [    7.970255] ata4.00: configured for UDMA/33
Jun 28 19:21:09 ubuntu kernel: [    7.972217] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7170A  1.02 PQ: 0 ANSI: 5
Jun 28 19:21:09 ubuntu kernel: [    7.974732] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 28 19:21:09 ubuntu kernel: [    7.974735] Uniform CD-ROM driver Revision: 3.20
Jun 28 19:21:09 ubuntu kernel: [    7.974833] sr 3:0:0:0: Attached scsi CD-ROM sr0
Jun 28 19:21:09 ubuntu kernel: [    7.974887] sr 3:0:0:0: Attached scsi generic sg0 type 5
Jun 28 19:21:09 ubuntu kernel: [    8.300053] ata6: SATA link down (SStatus 0 SControl 300)
Jun 28 19:21:09 ubuntu kernel: [    8.300166] scsi 6:0:0:0: Direct-Access     ATA      HDS728080PLA380  PF2O PQ: 0 ANSI: 5
Jun 28 19:21:09 ubuntu kernel: [    8.300304] sd 6:0:0:0: Attached scsi generic sg1 type 0
Jun 28 19:21:09 ubuntu kernel: [    8.301232] sd 6:0:0:0: [sda] 160836480 512-byte logical blocks: (82.3 GB/76.6 GiB)
Jun 28 19:21:09 ubuntu kernel: [    8.301276] sd 6:0:0:0: [sda] Write Protect is off
Jun 28 19:21:09 ubuntu kernel: [    8.301279] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 28 19:21:09 ubuntu kernel: [    8.301301] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 28 19:21:09 ubuntu kernel: [    8.301435]  sda: sda1 sda2 < sda5 >
Jun 28 19:21:09 ubuntu kernel: [    8.341351] sd 6:0:0:0: [sda] Attached SCSI disk
Jun 28 19:21:09 ubuntu kernel: [    8.790035] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 28 19:21:09 ubuntu kernel: [    8.810296] ata8.00: ATA-7: HDS728080PLA380, PF2OA69A, max UDMA/133
Jun 28 19:21:09 ubuntu kernel: [    8.810300] ata8.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 28 19:21:09 ubuntu kernel: [    8.850305] ata8.00: configured for UDMA/133
Jun 28 19:21:09 ubuntu kernel: [    8.850402] scsi 7:0:0:0: Direct-Access     ATA      HDS728080PLA380  PF2O PQ: 0 ANSI: 5
Jun 28 19:21:09 ubuntu kernel: [    8.850645] sd 7:0:0:0: [sdb] 160836480 512-byte logical blocks: (82.3 GB/76.6 GiB)
Jun 28 19:21:09 ubuntu kernel: [    8.850688] sd 7:0:0:0: [sdb] Write Protect is off
Jun 28 19:21:09 ubuntu kernel: [    8.850691] sd 7:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun 28 19:21:09 ubuntu kernel: [    8.850713] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 28 19:21:09 ubuntu kernel: [    8.850879] sd 7:0:0:0: Attached scsi generic sg2 type 0
Jun 28 19:21:09 ubuntu kernel: [    8.851024]  sdb: sdb1 sdb2 < >
Jun 28 19:21:09 ubuntu kernel: [    8.875178] sdb: p1 size 308532992 exceeds device capacity, limited to end of disk
Jun 28 19:21:09 ubuntu kernel: [    8.875227] sdb: p2 ignored, start 308533502 is behind the end of the disk
Jun 28 19:21:09 ubuntu kernel: [    8.875882] sd 7:0:0:0: [sdb] Attached SCSI disk
Jun 28 19:21:09 ubuntu kernel: [    8.897947] ohci1394 0000:04:0b.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Jun 28 19:21:09 ubuntu kernel: [    8.898306] usbcore: registered new interface driver hiddev
Jun 28 19:21:09 ubuntu kernel: [    8.922260] input: HID 04d9:1133 as /devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3.2/1-3.2:1.0/input/input4
Jun 28 19:21:09 ubuntu kernel: [    8.922362] generic-usb 0003:04D9:1133.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:0b.1-3.2/input0
Jun 28 19:21:09 ubuntu kernel: [    8.922387] usbcore: registered new interface driver usbhid
Jun 28 19:21:09 ubuntu kernel: [    8.922390] usbhid: v2.6:USB HID core driver
Jun 28 19:21:09 ubuntu kernel: [    8.927844] [drm] radeon defaulting to kernel modesetting.
Jun 28 19:21:09 ubuntu kernel: [    8.927848] [drm] radeon kernel modesetting enabled.
Jun 28 19:21:09 ubuntu kernel: [    8.929744] radeon 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Jun 28 19:21:09 ubuntu kernel: [    8.929751] radeon 0000:03:00.0: setting latency timer to 64
Jun 28 19:21:09 ubuntu kernel: [    8.932872] [drm] radeon: Initializing kernel modesetting.
Jun 28 19:21:09 ubuntu kernel: [    8.932961] [drm] register mmio base: 0xDFEE0000
Jun 28 19:21:09 ubuntu kernel: [    8.932963] [drm] register mmio size: 65536
Jun 28 19:21:09 ubuntu kernel: [    8.933766] ATOM BIOS: 954F.11.22.6.0.AS03
Jun 28 19:21:09 ubuntu kernel: [    8.933786] [drm] Clocks initialized !
Jun 28 19:21:09 ubuntu kernel: [    8.933816] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Jun 28 19:21:09 ubuntu kernel: [    8.933819] [drm] Detected VRAM RAM=256M, BAR=256M
Jun 28 19:21:09 ubuntu kernel: [    8.933821] [drm] RAM width 64bits DDR
Jun 28 19:21:09 ubuntu kernel: [    8.933867] [TTM] Zone  kernel: Available graphics memory: 2030306 kiB.
Jun 28 19:21:09 ubuntu kernel: [    8.933883] [drm] radeon: 256M of VRAM memory ready
Jun 28 19:21:09 ubuntu kernel: [    8.933886] [drm] radeon: 512M of GTT memory ready.
Jun 28 19:21:09 ubuntu kernel: [    8.933915]   alloc irq_desc for 30 on node 0
Jun 28 19:21:09 ubuntu kernel: [    8.933917]   alloc kstat_irqs on node 0
Jun 28 19:21:09 ubuntu kernel: [    8.933927] radeon 0000:03:00.0: irq 30 for MSI/MSI-X
Jun 28 19:21:09 ubuntu kernel: [    8.933931] [drm] radeon: using MSI.
Jun 28 19:21:09 ubuntu kernel: [    8.933964] [drm] radeon: irq initialized.
Jun 28 19:21:09 ubuntu kernel: [    8.933967] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jun 28 19:21:09 ubuntu kernel: [    8.935244] [drm] Loading RV710 Microcode
Jun 28 19:21:09 ubuntu kernel: [    8.935565] platform radeon_cp.0: firmware: requesting radeon/RV710_pfp.bin
Jun 28 19:21:09 ubuntu kernel: [    8.938489] platform radeon_cp.0: firmware: requesting radeon/RV710_me.bin
Jun 28 19:21:09 ubuntu kernel: [    8.940881] platform radeon_cp.0: firmware: requesting radeon/R700_rlc.bin
Jun 28 19:21:09 ubuntu kernel: [    8.960278] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dffff800-dfffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 28 19:21:09 ubuntu kernel: [    8.993253] [drm] ring test succeeded in 1 usecs
Jun 28 19:21:09 ubuntu kernel: [    8.993384] [drm] radeon: ib pool ready.
Jun 28 19:21:09 ubuntu kernel: [    8.993462] [drm] ib test succeeded in 0 usecs
Jun 28 19:21:09 ubuntu kernel: [    8.994206] [drm] Radeon Display Connectors
Jun 28 19:21:09 ubuntu kernel: [    8.994209] [drm] Connector 0:
Jun 28 19:21:09 ubuntu kernel: [    8.994210] [drm]   HDMI-A
Jun 28 19:21:09 ubuntu kernel: [    8.994212] [drm]   HPD1
Jun 28 19:21:09 ubuntu kernel: [    8.994214] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
Jun 28 19:21:09 ubuntu kernel: [    8.994216] [drm]   Encoders:
Jun 28 19:21:09 ubuntu kernel: [    8.994218] [drm]     DFP1: INTERNAL_UNIPHY
Jun 28 19:21:09 ubuntu kernel: [    8.994219] [drm] Connector 1:
Jun 28 19:21:09 ubuntu kernel: [    8.994221] [drm]   VGA
Jun 28 19:21:09 ubuntu kernel: [    8.994223] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Jun 28 19:21:09 ubuntu kernel: [    8.994224] [drm]   Encoders:
Jun 28 19:21:09 ubuntu kernel: [    8.994226] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
Jun 28 19:21:09 ubuntu kernel: [    8.994228] [drm] Connector 2:
Jun 28 19:21:09 ubuntu kernel: [    8.994229] [drm]   DVI-I
Jun 28 19:21:09 ubuntu kernel: [    8.994230] [drm]   HPD4
Jun 28 19:21:09 ubuntu kernel: [    8.994232] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
Jun 28 19:21:09 ubuntu kernel: [    8.994234] [drm]   Encoders:
Jun 28 19:21:09 ubuntu kernel: [    8.994235] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Jun 28 19:21:09 ubuntu kernel: [    8.994237] [drm]     DFP2: INTERNAL_UNIPHY2
Jun 28 19:21:09 ubuntu kernel: [    9.253139] [drm] fb mappable at 0xC0141000
Jun 28 19:21:09 ubuntu kernel: [    9.253142] [drm] vram apper at 0xC0000000
Jun 28 19:21:09 ubuntu kernel: [    9.253144] [drm] size 5242880
Jun 28 19:21:09 ubuntu kernel: [    9.253145] [drm] fb depth is 24
Jun 28 19:21:09 ubuntu kernel: [    9.253147] [drm]    pitch is 5120
Jun 28 19:21:09 ubuntu kernel: [    9.253286] fb0: radeondrmfb frame buffer device
Jun 28 19:21:09 ubuntu kernel: [    9.253288] registered panic notifier
Jun 28 19:21:09 ubuntu kernel: [    9.253294] [drm] Initialized radeon 2.0.0 20080528 for 0000:03:00.0 on minor 0
Jun 28 19:21:09 ubuntu kernel: [    9.255162] vga16fb: initializing
Jun 28 19:21:09 ubuntu kernel: [    9.255167] vga16fb: mapped to 0xffff8800000a0000
Jun 28 19:21:09 ubuntu kernel: [    9.255172] vga16fb: not registering due to another framebuffer present
Jun 28 19:21:09 ubuntu kernel: [    9.306692] Console: switching to colour frame buffer device 160x64
Jun 28 19:21:09 ubuntu kernel: [   10.280194] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001124372]
Jun 28 19:21:09 ubuntu kernel: [   10.383208] xor: automatically using best checksumming function: generic_sse
Jun 28 19:21:09 ubuntu kernel: [   10.430012]    generic_sse:  6438.000 MB/sec
Jun 28 19:21:09 ubuntu kernel: [   10.430014] xor: using function: generic_sse (6438.000 MB/sec)
Jun 28 19:21:09 ubuntu kernel: [   10.433175] device-mapper: dm-raid45: initialized v0.2594b
Jun 28 19:21:09 ubuntu kernel: [   10.505750] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jun 28 19:21:09 ubuntu kernel: [   10.505755] EXT4-fs (sda1): write access will be enabled during recovery
Jun 28 19:21:09 ubuntu kernel: [   10.851129] EXT4-fs (sda1): recovery complete
Jun 28 19:21:09 ubuntu kernel: [   10.851540] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun 28 19:21:09 ubuntu kernel: [   12.583929] ISO 9660 Extensions: Microsoft Joliet Level 3
Jun 28 19:21:09 ubuntu kernel: [   12.618613] ISO 9660 Extensions: RRIP_1991A
Jun 28 19:21:09 ubuntu kernel: [   12.913050] aufs 2-standalone.tree-20091207
Jun 28 19:21:09 ubuntu kernel: [   13.224496] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Jun 28 19:21:09 ubuntu kernel: [   60.735988] Adding 3317380k swap on /dev/sda5.  Priority:-1 extents:1 across:3317380k 
Jun 28 19:21:10 ubuntu kernel: [   61.830647] udev: starting version 151
Jun 28 19:21:13 ubuntu kernel: [   65.351256] i2c i2c-3: nForce2 SMBus adapter at 0x600
Jun 28 19:21:13 ubuntu kernel: [   65.351338] i2c i2c-4: nForce2 SMBus adapter at 0x700
Jun 28 19:21:14 ubuntu kernel: [   65.840483] EDAC MC: Ver: 2.1.0 Apr 16 2010
Jun 28 19:21:14 ubuntu kernel: [   66.210858] EDAC amd64_edac:  Ver: 3.2.0 Apr 16 2010
Jun 28 19:21:14 ubuntu kernel: [   66.211003] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
Jun 28 19:21:14 ubuntu kernel: [   66.211008] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 28 19:21:14 ubuntu kernel: [   66.211010]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 28 19:21:14 ubuntu kernel: [   66.211011]  (Note that use of the override may cause unknown side effects.)
Jun 28 19:21:14 ubuntu kernel: [   66.211029] amd64_edac: probe of 0000:00:18.2 failed with error -22
Jun 28 19:21:14 ubuntu kernel: [   66.485690] parport_pc 00:06: reported by Plug and Play ACPI
Jun 28 19:21:14 ubuntu kernel: [   66.485747] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jun 28 19:21:14 ubuntu kernel: [   66.494422] gameport: NS558 PnP Gameport is pnp00:07/gameport0, io 0x201, speed 816kHz
Jun 28 19:21:14 ubuntu avahi-daemon[1650]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Jun 28 19:21:14 ubuntu avahi-daemon[1650]: Successfully dropped root privileges.
Jun 28 19:21:14 ubuntu avahi-daemon[1650]: avahi-daemon 0.6.25 starting up.
Jun 28 19:21:15 ubuntu avahi-daemon[1650]: Successfully called chroot().
Jun 28 19:21:15 ubuntu avahi-daemon[1650]: Successfully dropped remaining capabilities.
Jun 28 19:21:15 ubuntu avahi-daemon[1657]: chroot.c: open() failed: No such file or directory
Jun 28 19:21:15 ubuntu avahi-daemon[1650]: Failed to open /etc/resolv.conf: Invalid argument
Jun 28 19:21:15 ubuntu avahi-daemon[1650]: No service file found in /etc/avahi/services.
Jun 28 19:21:15 ubuntu avahi-daemon[1650]: Network interface enumeration completed.
Jun 28 19:21:15 ubuntu avahi-daemon[1650]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 28 19:21:15 ubuntu avahi-daemon[1650]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2502034642.
Jun 28 19:21:15 ubuntu NetworkManager: <info>  starting...
Jun 28 19:21:15 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Jun 28 19:21:16 ubuntu kernel: [   68.129673] ppdev: user-space parallel port driver
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun 28 19:21:16 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:02:00.0/net/eth0, iface: eth0)
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.0/net/eth1, iface: eth1)
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun 28 19:21:16 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 28 19:21:16 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 28 19:21:16 ubuntu NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jun 28 19:21:16 ubuntu NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: (38466848) ... get_connections.
Jun 28 19:21:16 ubuntu NetworkManager:    SCPlugin-Ifupdown: (38466848) ... get_connections (managed=false): return empty list.
Jun 28 19:21:17 ubuntu modem-manager: Loaded plugin AnyData
Jun 28 19:21:17 ubuntu modem-manager: Loaded plugin Generic
Jun 28 19:21:17 ubuntu modem-manager: Loaded plugin Gobi
Jun 28 19:21:17 ubuntu modem-manager: Loaded plugin Option High-Speed
Jun 28 19:21:17 ubuntu modem-manager: Loaded plugin Huawei
Jun 28 19:21:17 ubuntu modem-manager: Loaded plugin Longcheer
Jun 28 19:21:18 ubuntu modem-manager: Loaded plugin Ericsson MBM
Jun 28 19:21:18 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2')
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth0): now managed
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Jun 28 19:21:18 ubuntu kernel: [   70.228488] sky2 eth0: enabling interface
Jun 28 19:21:18 ubuntu modem-manager: Loaded plugin MotoC
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth0): preparing device.
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun 28 19:21:18 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:03.0/0000:02:00.0/net/eth0
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth1): carrier is OFF
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth1): new Ethernet device (driver: 'forcedeth')
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth1): now managed
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth1): bringing up device.
Jun 28 19:21:18 ubuntu kernel: [   70.232890] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 28 19:21:18 ubuntu kernel: [   70.237964] eth1: no link during initialization.
Jun 28 19:21:18 ubuntu kernel: [   70.238859] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth1): preparing device.
Jun 28 19:21:18 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jun 28 19:21:18 ubuntu NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:13.0/net/eth1
Jun 28 19:21:18 ubuntu NetworkManager: <info>  modem-manager is now available
Jun 28 19:21:18 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 28 19:21:18 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Jun 28 19:21:18 ubuntu modem-manager: Loaded plugin Nokia
Jun 28 19:21:18 ubuntu modem-manager: Loaded plugin Novatel
Jun 28 19:21:18 ubuntu kernel: [   70.764465] usbcore: registered new interface driver snd-usb-audio
Jun 28 19:21:19 ubuntu modem-manager: Loaded plugin Option
Jun 28 19:21:19 ubuntu modem-manager: Loaded plugin Sierra
Jun 28 19:21:19 ubuntu modem-manager: Loaded plugin ZTE
Jun 28 19:21:19 ubuntu kernel: [   71.638969] HDA Intel 0000:03:00.1: PCI INT B -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Jun 28 19:21:19 ubuntu kernel: [   71.639036] HDA Intel 0000:03:00.1: setting latency timer to 64
Jun 28 19:21:20 ubuntu kernel: [   71.799763] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 22
Jun 28 19:21:20 ubuntu kernel: [   71.799770] Intel ICH 0000:00:0d.0: PCI INT A -> Link[LACI] -> GSI 22 (level, low) -> IRQ 22
Jun 28 19:21:20 ubuntu kernel: [   71.799813] Intel ICH 0000:00:0d.0: setting latency timer to 64
Jun 28 19:21:20 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jun 28 19:21:20 ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jun 28 19:21:20 ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 28 19:21:20 ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 28 19:21:20 ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jun 28 19:21:20 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jun 28 19:21:20 ubuntu kernel: [   72.050498] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Jun 28 19:21:20 ubuntu kernel: [   72.051089] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 28 19:21:20 ubuntu kernel: [   72.130029] intel8x0_measure_ac97_clock: measured 50690 usecs (2496 samples)
Jun 28 19:21:20 ubuntu kernel: [   72.130033] intel8x0: clocking to 46791
Jun 28 19:21:21 ubuntu NetworkManager: <info>  dhclient started with pid 1830
Jun 28 19:21:21 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun 28 19:21:21 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 28 19:21:21 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jun 28 19:21:21 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun 28 19:21:21 ubuntu avahi-daemon[1650]: Registering new address record for fe80::21a:92ff:fe1d:b9f0 on eth0.*.
Jun 28 19:21:21 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jun 28 19:21:21 ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jun 28 19:21:21 ubuntu dhclient: All rights reserved.
Jun 28 19:21:21 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 28 19:21:21 ubuntu dhclient: 
Jun 28 19:21:22 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jun 28 19:21:22 ubuntu dhclient: Listening on LPF/eth0/00:1a:92:1d:b9:f0
Jun 28 19:21:22 ubuntu dhclient: Sending on   LPF/eth0/00:1a:92:1d:b9:f0
Jun 28 19:21:22 ubuntu dhclient: Sending on   Socket/fallback
Jun 28 19:21:25 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jun 28 19:21:25 ubuntu dhclient: DHCPOFFER of 192.168.0.3 from 192.168.0.1
Jun 28 19:21:25 ubuntu dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 255.255.255.255 port 67
Jun 28 19:21:25 ubuntu dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
Jun 28 19:21:25 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jun 28 19:21:25 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 28 19:21:25 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 28 19:21:25 ubuntu NetworkManager: <info>    address 192.168.0.3
Jun 28 19:21:25 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Jun 28 19:21:25 ubuntu NetworkManager: <info>    gateway 192.168.0.1
Jun 28 19:21:25 ubuntu NetworkManager: <info>    nameserver '192.168.0.1'
Jun 28 19:21:25 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 28 19:21:25 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 28 19:21:25 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun 28 19:21:25 ubuntu avahi-daemon[1650]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.3.
Jun 28 19:21:25 ubuntu avahi-daemon[1650]: New relevant interface eth0.IPv4 for mDNS.
Jun 28 19:21:25 ubuntu avahi-daemon[1650]: Registering new address record for 192.168.0.3 on eth0.IPv4.
Jun 28 19:21:25 ubuntu dhclient: bound to 192.168.0.3 -- renewal in 33937 seconds.
Jun 28 19:21:26 ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jun 28 19:21:26 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jun 28 19:21:26 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated.
Jun 28 19:21:26 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 28 19:21:26 ubuntu cron[2165]: (CRON) INFO (pidfile fd = 3)
Jun 28 19:21:26 ubuntu acpid: starting up with proc fs
Jun 28 19:21:26 ubuntu cron[2342]: (CRON) STARTUP (fork ok)
Jun 28 19:21:27 ubuntu cron[2342]: (CRON) INFO (Running @reboot jobs)
Jun 28 19:21:27 ubuntu acpid: 36 rules loaded
Jun 28 19:21:27 ubuntu acpid: waiting for events: event logging is off
Jun 28 19:21:28 ubuntu kernel: [   80.625281] lp0: using parport0 (interrupt-driven).
Jun 28 19:21:30 ubuntu kernel: [   82.580017] eth0: no IPv6 routers present
Jun 28 19:21:31 ubuntu udev-configure-printer: add /devices/pnp0/00:06/printer/lp0
Jun 28 19:21:31 ubuntu udev-configure-printer: Failed to get parent
Jun 28 19:21:31 ubuntu udev-configure-printer: add /module/lp
Jun 28 19:21:31 ubuntu udev-configure-printer: Failed to get parent
Jun 28 19:21:34 ubuntu ntpdate[2810]: step time server 91.189.94.4 offset -1.560090 sec
Jun 28 19:21:40 ubuntu init: plymouth-stop pre-start process (3079) terminated with status 1
Jun 28 19:21:56 ubuntu rtkit-daemon[3192]: Sucessfully called chroot.
Jun 28 19:21:56 ubuntu rtkit-daemon[3192]: Sucessfully dropped privileges.
Jun 28 19:21:56 ubuntu rtkit-daemon[3192]: Sucessfully limited resources.
Jun 28 19:21:56 ubuntu rtkit-daemon[3192]: Running.
Jun 28 19:21:56 ubuntu rtkit-daemon[3192]: Watchdog thread running.
Jun 28 19:21:56 ubuntu rtkit-daemon[3192]: Canary thread running.
Jun 28 19:21:56 ubuntu polkitd[3196]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jun 28 19:21:58 ubuntu kernel: [  111.920717] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Jun 28 19:21:58 ubuntu pulseaudio[3190]: module-alsa-card.c: Failed to find a working profile.
Jun 28 19:21:58 ubuntu pulseaudio[3190]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jun 28 19:21:59 ubuntu kernel: [  112.369065] end_request: I/O error, dev fd0, sector 0
Jun 28 19:22:03 ubuntu pulseaudio[3190]: ratelimit.c: 9 events suppressed
Jun 28 19:22:11 ubuntu kernel: [  124.458449] end_request: I/O error, dev fd0, sector 0
Jun 28 19:35:27 ubuntu gdm-binary[3228]: WARNING: Unable to find users: no seat-id found
Jun 28 19:35:28 ubuntu acpid: client connected from 3235[0:0]
Jun 28 19:35:28 ubuntu acpid: 1 client rule loaded
Jun 28 19:35:30 ubuntu gdm-session-worker[3238]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 28 19:35:30 ubuntu pulseaudio[3190]: module-alsa-card.c: Failed to find a working profile.
Jun 28 19:35:30 ubuntu pulseaudio[3190]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jun 28 19:35:35 ubuntu pulseaudio[3190]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Jun 28 19:35:35 ubuntu pulseaudio[3190]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Jun 28 19:35:35 ubuntu pulseaudio[3190]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Jun 28 19:35:38 ubuntu pulseaudio[3190]: ratelimit.c: 5 events suppressed
Jun 28 19:35:44 ubuntu pulseaudio[3190]: ratelimit.c: 1 events suppressed
Jun 28 19:35:45 ubuntu acpid: client connected from 3452[108:114]
Jun 28 19:35:45 ubuntu acpid: 1 client rule loaded
Jun 28 19:36:40 ubuntu AptDaemon: INFO: Initializing daemon
Jun 28 19:36:42 ubuntu hp[3554]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 28 19:36:43 ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 28 19:41:41 ubuntu AptDaemon: INFO: Quiting due to inactivity
Jun 28 19:41:41 ubuntu AptDaemon: INFO: Shutdown was requested
Jun 28 20:17:01 ubuntu CRON[3755]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

---

### Post by LeonardChallis on 2010-06-29
Oh, I forgot to add, after it shows me the error and starts to boot in to the LIVE session, I get the getpwuid_r(); error -- though not sure if this is related?

I *did* have a software RAID set up (stripe - the 2 HDDs you see in above post) but I have removed that now and I just have the two seperate SATA drives (with just one having partitions set up so far).

And one further thing -- while I had 9.10 installed (64 bit also) I tried upgrading automatically to 10.04 but after getting so far it bombed out and left the system pretty much unusable (no dual screen, usb devices not working, etc), but again, not sure how much difference this will make either, as I am (planning on) installing with a fresh install and fresh partitions.

---

### Post by dino99 on 2010-06-29
yeah the raid system need to be removed (the installer fail if it find it)

take care of your data of course

sudo dmraid -rE

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by LeonardChallis on 2010-06-29
I removed the RAID array in the BIOS before trying to install 10.04. I ran dmraid, but I get "no raid disks" - I presume this cannot be the problem, then?

---

### Post by eltonw on 2010-06-29
By any chance, did you [COLOR="DarkRed"]verify the MD5SUMS after download[/COLOR] and before burning the iso to disk? ... it might be something as basic as a corrupted download.

Also why does the output mention "Solaris"?


/dev/sda5            9599       10011     3317391   82  Linux swap / Solaris

Did you get the right iso for your computer's *[COLOR="DarkRed"]architecture[/COLOR]*? I am guessing this is a PC (Intel or AMD processor) and *not* a Solaris?

... perhaps this might point you in the right direction in getting a handle on your install problem.

HTH...):P

---

### Post by LeonardChallis on 2010-06-29
> **eltonw said:**
> By any chance, did you [COLOR=DarkRed]verify the MD5SUMS after download[/COLOR] and before burning the iso to disk? ... it might be something as basic as a corrupted download.


I didn't - but I did run the disc check utility.

> 
Also why does the output mention "Solaris"?
These are the default partitions made by the Kubuntu 9.10 install I ran to see if it was a particular version of 'buntu that was having problems


> 
/dev/sda5            9599       10011     3317391   82  Linux swap / Solaris

Did you get the right iso for your computer's *[COLOR=DarkRed]architecture[/COLOR]*? I am guessing this is a PC (Intel or AMD processor) and *not* a Solaris?
Yeah :) AMD 64 version.

---

### Post by LeonardChallis on 2010-06-29
How very strange. I never post to the forums that much in fear I am not looking in to things enough myself - usually you can figure things out with a bit of reading. Alas, I have just completed (what so far seems to be) a successful installation of Ubuntu 10.04 64 bit.

What did I do?

I booted in to the LIVE CD again, and deleted all partition tables/partitions, recreated one partition on /dev/sda (ext4 on mount point: / ) and another on /dev/sdb (ext4 on mount point: /home ) - I have 4GB of RAM so I don't think (hope :P) not having a swap will be a problem to be honest.

From there I ran the installation from the desktop like I had done before and voila -- no failing this time.

Installation ran, I've rebooted and now I'm on my lovely new desktop. Thanks for the suggestions. Now I'm wondering whether I should have broken my Ubuntu forum silence... though I think I'll be more inclined to read/post on other peoples topics too and earn me some beans :P

---

