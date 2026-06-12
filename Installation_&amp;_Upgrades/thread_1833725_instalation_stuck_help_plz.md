---
title: "instalation stuck help plz"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by mugbomb on 2011-08-26
hi to all again i faild to instal ubunt cause my instalation is stuck at copying instalation logs...
im instaling ubuntu in a 160gb partition i inted to creat the home partition after instaling.
so what should i do i restarted already my pc but it strucks again at the same point, i have tryid to navigate a bit at the banshe and i could so its not the computer.
its that part that just take too long to instal or ????

---

### Post by MAFoElffen on 2011-08-26
> **mugbomb said:**
> hi to all again i faild to instal ubunt cause my instalation is stuck at copying instalation logs...
im instaling ubuntu in a 160gb partition i inted to creat the home partition after instaling.
so what should i do i restarted already my pc but it strucks again at the same point, i have tryid to navigate a bit at the banshe and i could so its not the computer.
its that part that just take too long to instal or ????
Welcome to Ubuntu...

I'm having a bit if a time following "your" installation "plan" and where you are stuck.

Here's my understanding of what you are "trying" do... tell me different if my understanding is different than "your plan."  Sound like you are doing a basic install into a 160GB partion... Where you later plan to move your home partitionion out separately later- so it's not a factor in your initial install.

Your install sticks at the _____???___ screen, while copying installation files... which if you ID'ed what landmarks it did successfully get passed, it would help us to ID what may be a problem.

For instances, If it locks up while trying at the intitial hardware ID after picking a keyboard <> then there's a possible conflict between what your BIOS see's and what Linux see's... If it looks while trying to looking for network time <> if may not have drivers for the NIC or not have a network connection....  If it locks when tryinh to start the the disk partitioner <> there may be some problems reading a disk or partition... With your description so far, being so basic, it could be a myriad of things and we would just be guessing.

One thing you could do, is start the LiveCD and run from "Try."  While in that mode, you could "Install."  When thee install "locks" at the point you say it keeps getting to, you could then open a browser, to post a description of where it locked up AND post then present /var/log/syslog.  That would tell us exactly where in the install process it is erroring.

---

### Post by mugbomb on 2011-08-26
im trying that way now ill put a print screen when the time come ill try tu put a printscreen and u tell me if there is any problem or if i just need to wait like an hour or something.
thx for helping

---

### Post by mugbomb on 2011-08-26
it's in portuguese but it says copying instalation register's or files
see what u can do from here

---

### Post by MAFoElffen on 2011-08-26
> **mugbomb said:**
> im trying that way now ill put a print screen when the time come ill try tu put a printscreen and u tell me if there is any problem or if i just need to wait like an hour or something.
thx for helping
Okay-- Now while in that screen, use "Places" to navigate to the /var/log folder.  Find the file named "syslog"... Right click on that file.  Open with gedit.  When it opens, Right-click on the text inside that window... click on Select All.  Right-click again, select copy.

Open a browser.  Get to this thread.  Press on the reply button.  Click in the reply text box.  Click on the " # " buton in the reply toolbar.  Right-click the cursor between the CODE tags.  Select Paste...

Post...

---

### Post by mugbomb on 2011-08-26
```
Aug 26 18:50:11 ubuntu kernel: imklog 4.6.4, log source = /proc/kmsg started.
Aug 26 18:50:11 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="1365" x-info="http://www.rsyslog.com"] (re)start
Aug 26 18:50:11 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Aug 26 18:50:11 ubuntu rsyslogd: rsyslogd's userid changed to 101
Aug 26 18:50:11 ubuntu rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b9e51000 (usable)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b9e51000 - 00000000b9e53000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b9e53000 - 00000000bac70000 (usable)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bac70000 - 00000000bac80000 (ACPI NVS)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bac80000 - 00000000bd3d6000 (usable)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bd3d6000 - 00000000bd5d6000 (ACPI NVS)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bd5d6000 - 00000000bed93000 (usable)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bed93000 - 00000000bed9b000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bed9b000 - 00000000bedbf000 (usable)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bedbf000 - 00000000bedcf000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bedcf000 - 00000000beecf000 (ACPI NVS)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000beecf000 - 00000000beeff000 (ACPI data)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000beeff000 - 00000000bef00000 (usable)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bef00000 - 00000000bf000000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffe80000 - 0000000100000000 (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Aug 26 18:50:11 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Aug 26 18:50:11 ubuntu kernel: [    0.000000] DMI 2.4 present.
Aug 26 18:50:11 ubuntu kernel: [    0.000000] DMI: Hewlett-Packard HP EliteBook 6930p/30DC, BIOS 68PCD Ver. F.0C 10/17/2008
Aug 26 18:50:11 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] last_pfn = 0xbef00 max_arch_pfn = 0x100000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Aug 26 18:50:11 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   C0000-FFFFF write-protect
Aug 26 18:50:11 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   1 base 000000000 mask F80000000 write-back
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   3 base 0BF000000 mask FFF000000 uncachable
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   4 base 0BAC70000 mask FFFFF0000 uncachable
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   5 disabled
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   6 disabled
Aug 26 18:50:11 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 26 18:50:11 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Aug 26 18:50:11 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] RAMDISK: 7f33b000 - 80000000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 36b39000 - 377fd9b3
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007f33b000 - 000000007ffff9b2 to 36b39000 - 377fd9b2
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: RSDP 000f68b0 00024 (v02 HPQOEM)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: XSDT beefe120 00084 (v01 HPQOEM SLIC-MPC 0000000F      01000013)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: FACP beefc000 000F4 (v03 HPQOEM 30DC     0000000F HP   00000001)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: DSDT beee0000 16CA8 (v01 HPQOEM 30DC     00000001 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: FACS bee9d000 00040
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: HPET beefb000 00038 (v01 HPQOEM 30DC     00000001 HP   00000001)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: APIC beefa000 00084 (v01 HPQOEM 30DC     00000001 HP   00000001)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: MCFG beef9000 0003C (v01 HPQOEM 30DC     00000001 HP   00000001)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: TCPA beef7000 00032 (v02 HPQOEM 30DC     00000000 HP   00000001)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: SSDT beedd000 002DD (v01 HPQOEM SataAhci 00001000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: SLIC beedb000 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: DMAR beeda000 00098 (v01               ? 00000001      00000000)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: ASF! beef8000 00095 (v32 HPQOEM 30DC     00000001 HP   00000001)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: SSDT beed9000 0066C (v01  PmRef    CpuPm 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: SSDT beed8000 00288 (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: SSDT beed7000 00225 (v01  PmRef    ApTst 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] 2167MB HIGHMEM available.
Aug 26 18:50:11 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Zone PFN ranges:
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x000bef00
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Aug 26 18:50:11 ubuntu kernel: [    0.000000] early_node_map[7] active PFN ranges
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000b9e51
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     0: 0x000b9e53 -> 0x000bac70
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     0: 0x000bac80 -> 0x000bd3d6
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     0: 0x000bd5d6 -> 0x000bed93
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     0: 0x000bed9b -> 0x000bedbf
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     0: 0x000beeff -> 0x000bef00
Aug 26 18:50:11 ubuntu kernel: [    0.000000] On node 0 totalpages: 781109
Aug 26 18:50:11 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f5358200
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   HighMem zone: 4335 pages used for memmap
Aug 26 18:50:11 ubuntu kernel: [    0.000000]   HighMem zone: 549561 pages, LIFO batch:31
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Using APIC driver default
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug 26 18:50:11 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Aug 26 18:50:11 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Aug 26 18:50:11 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ef000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Allocating PCI resources starting at bf000000 (gap: bf000000:21000000)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 26 18:50:11 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Aug 26 18:50:11 ubuntu kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f4c00000 s28800 r0 d24448 u1048576
Aug 26 18:50:11 ubuntu kernel: [    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
Aug 26 18:50:11 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 774998
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Aug 26 18:50:11 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Initializing CPU#0
Aug 26 18:50:11 ubuntu kernel: [    0.000000] allocated 15641280 bytes of page_cgroup
Aug 26 18:50:11 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ------------[ cut here ]------------
Aug 26 18:50:11 ubuntu kernel: [    0.000000] WARNING: at /build/buildd/linux-2.6.38/drivers/pci/dmar.c:634 warn_invalid_dmar+0x98/0xb0()
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Hardware name: HP EliteBook 6930p
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Your BIOS is broken; DMAR reported at address 0!
Aug 26 18:50:11 ubuntu kernel: [    0.000000] BIOS vendor: Hewlett-Packard; Ver: 68PCD Ver. F.0C; Product Version: F.0C
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Modules linked in:
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Pid: 0, comm: swapper Not tainted 2.6.38-8-generic #42-Ubuntu
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Call Trace:
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c12a4a28>] ? warn_invalid_dmar+0x98/0xb0
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c12a4a28>] ? warn_invalid_dmar+0x98/0xb0
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c104f9a2>] ? warn_slowpath_fmt_taint+0x32/0x40
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c12a4a28>] ? warn_invalid_dmar+0x98/0xb0
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c17b5b6a>] ? check_zero_address+0x53/0x123
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c12e1c93>] ? acpi_tb_verify_table+0x4b/0x4e
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c12e1bd5>] ? acpi_get_table_with_size+0x59/0xae
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c17b5c4c>] ? detect_intel_iommu+0x12/0x78
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c17930c0>] ? pci_iommu_alloc+0x35/0x5a
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c179e35c>] ? mem_init+0xe/0x26d
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c17a76d2>] ? __alloc_bootmem_node_nopanic+0x72/0x93
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c150717f>] ? printk+0x30/0x39
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c17abb64>] ? page_cgroup_init_flatmem+0xab/0xd9
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c178d638>] ? start_kernel+0x1b6/0x366
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c178d3d5>] ? pass_all_bootoptions+0x0/0xa
Aug 26 18:50:11 ubuntu kernel: [    0.000000]  [<c178d0e0>] ? i386_start_kernel+0xe0/0xe8
Aug 26 18:50:11 ubuntu kernel: [    0.000000] ---[ end trace a7919e7f17c0a725 ]---
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Disabling lock debugging due to kernel taint
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000bef00)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Memory: 3061192k/3128320k available (5188k kernel code, 63244k reserved, 2540k data, 700k init, 2215584k highmem)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
Aug 26 18:50:11 ubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 26 18:50:11 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Aug 26 18:50:11 ubuntu kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Aug 26 18:50:11 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712 16
Aug 26 18:50:11 ubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Aug 26 18:50:11 ubuntu kernel: [    0.000000] console [tty0] enabled
Aug 26 18:50:11 ubuntu kernel: [    0.000000] hpet clockevent registered
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Aug 26 18:50:11 ubuntu kernel: [    0.000000] Detected 2526.549 MHz processor.
Aug 26 18:50:11 ubuntu kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.09 BogoMIPS (lpj=10106196)
Aug 26 18:50:11 ubuntu kernel: [    0.004007] pid_max: default: 32768 minimum: 301
Aug 26 18:50:11 ubuntu kernel: [    0.004027] Security Framework initialized
Aug 26 18:50:11 ubuntu kernel: [    0.004041] AppArmor: AppArmor initialized
Aug 26 18:50:11 ubuntu kernel: [    0.004043] Yama: becoming mindful.
Aug 26 18:50:11 ubuntu kernel: [    0.004091] Mount-cache hash table entries: 512
Aug 26 18:50:11 ubuntu kernel: [    0.004212] Initializing cgroup subsys ns
Aug 26 18:50:11 ubuntu kernel: [    0.004215] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Aug 26 18:50:11 ubuntu kernel: [    0.004218] Initializing cgroup subsys cpuacct
Aug 26 18:50:11 ubuntu kernel: [    0.004222] Initializing cgroup subsys memory
Aug 26 18:50:11 ubuntu kernel: [    0.004230] Initializing cgroup subsys devices
Aug 26 18:50:11 ubuntu kernel: [    0.004232] Initializing cgroup subsys freezer
Aug 26 18:50:11 ubuntu kernel: [    0.004234] Initializing cgroup subsys net_cls
Aug 26 18:50:11 ubuntu kernel: [    0.004236] Initializing cgroup subsys blkio
Aug 26 18:50:11 ubuntu kernel: [    0.004268] CPU: Physical Processor ID: 0
Aug 26 18:50:11 ubuntu kernel: [    0.004269] CPU: Processor Core ID: 0
Aug 26 18:50:11 ubuntu kernel: [    0.004272] mce: CPU supports 6 MCE banks
Aug 26 18:50:11 ubuntu kernel: [    0.004278] CPU0: Thermal monitoring handled by SMI
Aug 26 18:50:11 ubuntu kernel: [    0.004282] using mwait in idle threads.
Aug 26 18:50:11 ubuntu kernel: [    0.008827] ACPI: Core revision 20110112
Aug 26 18:50:11 ubuntu kernel: [    0.016012] ftrace: allocating 23640 entries in 47 pages
Aug 26 18:50:11 ubuntu kernel: [    0.020038] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 26 18:50:11 ubuntu kernel: [    0.020340] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 26 18:50:11 ubuntu kernel: [    0.061208] CPU0: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
Aug 26 18:50:11 ubuntu kernel: [    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Aug 26 18:50:11 ubuntu kernel: [    0.064003] ... version:                2
Aug 26 18:50:11 ubuntu kernel: [    0.064003] ... bit width:              40
Aug 26 18:50:11 ubuntu kernel: [    0.064003] ... generic registers:      2
Aug 26 18:50:11 ubuntu kernel: [    0.064003] ... value mask:             000000ffffffffff
Aug 26 18:50:11 ubuntu kernel: [    0.064003] ... max period:             000000007fffffff
Aug 26 18:50:11 ubuntu kernel: [    0.064003] ... fixed-purpose events:   3
Aug 26 18:50:11 ubuntu kernel: [    0.064003] ... event mask:             0000000700000003
Aug 26 18:50:11 ubuntu kernel: [    0.064003] CPU 1 irqstacks, hard=f38d0000 soft=f38d2000
Aug 26 18:50:11 ubuntu kernel: [    0.064003] Booting Node   0, Processors  #1
Aug 26 18:50:11 ubuntu kernel: [    0.008000] Initializing CPU#1
Aug 26 18:50:11 ubuntu kernel: [    0.008000] CPU1: Thermal monitoring handled by SMI
Aug 26 18:50:11 ubuntu kernel: [    0.152023] Brought up 2 CPUs
Aug 26 18:50:11 ubuntu kernel: [    0.152026] Total of 2 processors activated (10107.06 BogoMIPS).
Aug 26 18:50:11 ubuntu kernel: [    0.152938] devtmpfs: initialized
Aug 26 18:50:11 ubuntu kernel: [    0.153096] print_constraints: dummy: 
Aug 26 18:50:11 ubuntu kernel: [    0.153119] Time: 18:49:09  Date: 08/26/11
Aug 26 18:50:11 ubuntu kernel: [    0.153152] NET: Registered protocol family 16
Aug 26 18:50:11 ubuntu kernel: [    0.153175] Trying to unpack rootfs image as initramfs...
Aug 26 18:50:11 ubuntu kernel: [    0.153255] EISA bus registered
Aug 26 18:50:11 ubuntu kernel: [    0.153262] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Aug 26 18:50:11 ubuntu kernel: [    0.153264] ACPI: bus type pci registered
Aug 26 18:50:11 ubuntu kernel: [    0.153327] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Aug 26 18:50:11 ubuntu kernel: [    0.153330] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Aug 26 18:50:11 ubuntu kernel: [    0.153332] PCI: Using MMCONFIG for extended config space
Aug 26 18:50:11 ubuntu kernel: [    0.153333] PCI: Using configuration type 1 for base access
Aug 26 18:50:11 ubuntu kernel: [    1.152172] bio: create slab <bio-0> at 0
Aug 26 18:50:11 ubuntu kernel: [    1.154211] ACPI: EC: Look up EC in DSDT
Aug 26 18:50:11 ubuntu kernel: [    1.163028] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Aug 26 18:50:11 ubuntu kernel: [    1.171699] ACPI: SSDT bedc7c18 00275 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    1.172158] ACPI: Dynamic OEM Table Load:
Aug 26 18:50:11 ubuntu kernel: [    1.172161] ACPI: SSDT   (null) 00275 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    1.172294] ACPI: SSDT bedc5618 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    1.172731] ACPI: Dynamic OEM Table Load:
Aug 26 18:50:11 ubuntu kernel: [    1.172733] ACPI: SSDT   (null) 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    2.476490] ACPI: SSDT bedc6e18 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    2.476987] ACPI: Dynamic OEM Table Load:
Aug 26 18:50:11 ubuntu kernel: [    2.476991] ACPI: SSDT   (null) 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    2.485406] Freeing initrd memory: 13076k freed
Aug 26 18:50:11 ubuntu kernel: [    2.500310] ACPI: SSDT bedc7f18 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    2.500769] ACPI: Dynamic OEM Table Load:
Aug 26 18:50:11 ubuntu kernel: [    2.500772] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
Aug 26 18:50:11 ubuntu kernel: [    2.748755] ACPI: Interpreter enabled
Aug 26 18:50:11 ubuntu kernel: [    2.748763] ACPI: (supports S0 S3 S4 S5)
Aug 26 18:50:11 ubuntu kernel: [    2.748784] ACPI: Using IOAPIC for interrupt routing
Aug 26 18:50:11 ubuntu kernel: [    2.749674] ACPI: Power Resource [APPR] (off)
Aug 26 18:50:11 ubuntu kernel: [    2.776837] ACPI: Power Resource [LPP] (on)
Aug 26 18:50:11 ubuntu kernel: [    2.778111] ACPI: Power Resource [PGF0] (off)
Aug 26 18:50:11 ubuntu kernel: [    2.778563] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Aug 26 18:50:11 ubuntu kernel: [    2.778785] ACPI: No dock devices found.
Aug 26 18:50:11 ubuntu kernel: [    2.778787] HEST: Table not found.
Aug 26 18:50:11 ubuntu kernel: [    2.778791] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Aug 26 18:50:11 ubuntu kernel: [    2.779655] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Aug 26 18:50:11 ubuntu kernel: [    2.780323] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Aug 26 18:50:11 ubuntu kernel: [    2.780325] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Aug 26 18:50:11 ubuntu kernel: [    2.780328] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Aug 26 18:50:11 ubuntu kernel: [    2.780331] pci_root PNP0A08:00: host bridge window [mem 0xbf000000-0xdfffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.780333] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfedfffff]
Aug 26 18:50:11 ubuntu kernel: [    2.780336] pci_root PNP0A08:00: host bridge window [mem 0xfee01000-0xffffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.780349] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
Aug 26 18:50:11 ubuntu kernel: [    2.780372] DMAR: Forcing write-buffer flush capability
Aug 26 18:50:11 ubuntu kernel: [    2.780374] DMAR: Disabling IOMMU for graphics on this chipset
Aug 26 18:50:11 ubuntu kernel: [    2.780395] pci 0000:00:01.0: [8086:2a41] type 1 class 0x000604
Aug 26 18:50:11 ubuntu kernel: [    2.780426] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.780430] pci 0000:00:01.0: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.780447] pci 0000:00:03.0: [8086:2a44] type 0 class 0x000780
Aug 26 18:50:11 ubuntu kernel: [    2.780463] pci 0000:00:03.0: reg 10: [mem 0xd8427000-0xd842700f 64bit]
Aug 26 18:50:11 ubuntu kernel: [    2.780504] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.780508] pci 0000:00:03.0: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.780524] pci 0000:00:03.2: [8086:2a46] type 0 class 0x000101
Aug 26 18:50:11 ubuntu kernel: [    2.780538] pci 0000:00:03.2: reg 10: [io  0x8130-0x8137]
Aug 26 18:50:11 ubuntu kernel: [    2.780545] pci 0000:00:03.2: reg 14: [io  0x8144-0x8147]
Aug 26 18:50:11 ubuntu kernel: [    2.780552] pci 0000:00:03.2: reg 18: [io  0x8128-0x812f]
Aug 26 18:50:11 ubuntu kernel: [    2.780559] pci 0000:00:03.2: reg 1c: [io  0x8140-0x8143]
Aug 26 18:50:11 ubuntu kernel: [    2.780566] pci 0000:00:03.2: reg 20: [io  0x8100-0x810f]
Aug 26 18:50:11 ubuntu kernel: [    2.780607] pci 0000:00:03.3: [8086:2a47] type 0 class 0x000700
Aug 26 18:50:11 ubuntu kernel: [    2.780620] pci 0000:00:03.3: reg 10: [io  0x8120-0x8127]
Aug 26 18:50:11 ubuntu kernel: [    2.780627] pci 0000:00:03.3: reg 14: [mem 0xd8425000-0xd8425fff]
Aug 26 18:50:11 ubuntu kernel: [    2.780709] pci 0000:00:19.0: [8086:10f5] type 0 class 0x000200
Aug 26 18:50:11 ubuntu kernel: [    2.780727] pci 0000:00:19.0: reg 10: [mem 0xd8400000-0xd841ffff]
Aug 26 18:50:11 ubuntu kernel: [    2.780735] pci 0000:00:19.0: reg 14: [mem 0xd8424000-0xd8424fff]
Aug 26 18:50:11 ubuntu kernel: [    2.780743] pci 0000:00:19.0: reg 18: [io  0x80e0-0x80ff]
Aug 26 18:50:11 ubuntu kernel: [    2.780791] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.780795] pci 0000:00:19.0: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.780813] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
Aug 26 18:50:11 ubuntu kernel: [    2.780855] pci 0000:00:1a.0: reg 20: [io  0x80c0-0x80df]
Aug 26 18:50:11 ubuntu kernel: [    2.780897] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
Aug 26 18:50:11 ubuntu kernel: [    2.780939] pci 0000:00:1a.1: reg 20: [io  0x80a0-0x80bf]
Aug 26 18:50:11 ubuntu kernel: [    2.780982] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
Aug 26 18:50:11 ubuntu kernel: [    2.781024] pci 0000:00:1a.2: reg 20: [io  0x8080-0x809f]
Aug 26 18:50:11 ubuntu kernel: [    2.781075] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
Aug 26 18:50:11 ubuntu kernel: [    2.781096] pci 0000:00:1a.7: reg 10: [mem 0xd8426c00-0xd8426fff]
Aug 26 18:50:11 ubuntu kernel: [    2.781168] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.781172] pci 0000:00:1a.7: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.781195] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
Aug 26 18:50:11 ubuntu kernel: [    2.781209] pci 0000:00:1b.0: reg 10: [mem 0xd8420000-0xd8423fff 64bit]
Aug 26 18:50:11 ubuntu kernel: [    2.781262] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.781266] pci 0000:00:1b.0: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.781285] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
Aug 26 18:50:11 ubuntu kernel: [    2.781338] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.781342] pci 0000:00:1c.0: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.781364] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
Aug 26 18:50:11 ubuntu kernel: [    2.781418] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.781421] pci 0000:00:1c.1: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.781441] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
Aug 26 18:50:11 ubuntu kernel: [    2.781495] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.781499] pci 0000:00:1c.2: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.781520] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
Aug 26 18:50:11 ubuntu kernel: [    2.781573] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.781577] pci 0000:00:1c.4: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.781600] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
Aug 26 18:50:11 ubuntu kernel: [    2.781642] pci 0000:00:1d.0: reg 20: [io  0x8060-0x807f]
Aug 26 18:50:11 ubuntu kernel: [    2.781685] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
Aug 26 18:50:11 ubuntu kernel: [    2.781727] pci 0000:00:1d.1: reg 20: [io  0x8040-0x805f]
Aug 26 18:50:11 ubuntu kernel: [    2.781769] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
Aug 26 18:50:11 ubuntu kernel: [    2.781811] pci 0000:00:1d.2: reg 20: [io  0x8020-0x803f]
Aug 26 18:50:11 ubuntu kernel: [    2.781863] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
Aug 26 18:50:11 ubuntu kernel: [    2.781884] pci 0000:00:1d.7: reg 10: [mem 0xd8426800-0xd8426bff]
Aug 26 18:50:11 ubuntu kernel: [    2.781955] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.781960] pci 0000:00:1d.7: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.781978] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Aug 26 18:50:11 ubuntu kernel: [    2.782033] pci 0000:00:1f.0: [8086:2917] type 0 class 0x000601
Aug 26 18:50:11 ubuntu kernel: [    2.782140] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
Aug 26 18:50:11 ubuntu kernel: [    2.782159] pci 0000:00:1f.2: reg 10: [io  0x8118-0x811f]
Aug 26 18:50:11 ubuntu kernel: [    2.782167] pci 0000:00:1f.2: reg 14: [io  0x813c-0x813f]
Aug 26 18:50:11 ubuntu kernel: [    2.782174] pci 0000:00:1f.2: reg 18: [io  0x8110-0x8117]
Aug 26 18:50:11 ubuntu kernel: [    2.782182] pci 0000:00:1f.2: reg 1c: [io  0x8138-0x813b]
Aug 26 18:50:11 ubuntu kernel: [    2.782190] pci 0000:00:1f.2: reg 20: [io  0x8000-0x801f]
Aug 26 18:50:11 ubuntu kernel: [    2.782198] pci 0000:00:1f.2: reg 24: [mem 0xd8426000-0xd84267ff]
Aug 26 18:50:11 ubuntu kernel: [    2.782230] pci 0000:00:1f.2: PME# supported from D3hot
Aug 26 18:50:11 ubuntu kernel: [    2.782234] pci 0000:00:1f.2: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.782288] pci 0000:01:00.0: [1002:95c4] type 0 class 0x000300
Aug 26 18:50:11 ubuntu kernel: [    2.782304] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.782314] pci 0000:01:00.0: reg 14: [io  0x7000-0x70ff]
Aug 26 18:50:11 ubuntu kernel: [    2.782325] pci 0000:01:00.0: reg 18: [mem 0xd8300000-0xd830ffff]
Aug 26 18:50:11 ubuntu kernel: [    2.782363] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.782391] pci 0000:01:00.0: supports D1 D2
Aug 26 18:50:11 ubuntu kernel: [    2.782410] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Aug 26 18:50:11 ubuntu kernel: [    2.782414] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Aug 26 18:50:11 ubuntu kernel: [    2.782417] pci 0000:00:01.0:   bridge window [mem 0xd8300000-0xd83fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.782421] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.782460] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Aug 26 18:50:11 ubuntu kernel: [    2.782464] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Aug 26 18:50:11 ubuntu kernel: [    2.782468] pci 0000:00:1c.0:   bridge window [mem 0xd8200000-0xd82fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.782473] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 26 18:50:11 ubuntu kernel: [    2.782558] pci 0000:03:00.0: [8086:4236] type 0 class 0x000280
Aug 26 18:50:11 ubuntu kernel: [    2.782595] pci 0000:03:00.0: reg 10: [mem 0xd8100000-0xd8101fff 64bit]
Aug 26 18:50:11 ubuntu kernel: [    2.782724] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.782734] pci 0000:03:00.0: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.782782] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Aug 26 18:50:11 ubuntu kernel: [    2.782786] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
Aug 26 18:50:11 ubuntu kernel: [    2.782790] pci 0000:00:1c.1:   bridge window [mem 0xd8100000-0xd81fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.782795] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 26 18:50:11 ubuntu kernel: [    2.782834] pci 0000:00:1c.2: PCI bridge to [bus 04-44]
Aug 26 18:50:11 ubuntu kernel: [    2.782838] pci 0000:00:1c.2:   bridge window [io  0x5000-0x6fff]
Aug 26 18:50:11 ubuntu kernel: [    2.782842] pci 0000:00:1c.2:   bridge window [mem 0xd4000000-0xd7ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.782847] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 26 18:50:11 ubuntu kernel: [    2.782886] pci 0000:00:1c.4: PCI bridge to [bus 45-85]
Aug 26 18:50:11 ubuntu kernel: [    2.782890] pci 0000:00:1c.4:   bridge window [io  0x3000-0x4fff]
Aug 26 18:50:11 ubuntu kernel: [    2.782894] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd3ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.782899] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 26 18:50:11 ubuntu kernel: [    2.782942] pci 0000:86:09.0: [1180:0832] type 0 class 0x000c00
Aug 26 18:50:11 ubuntu kernel: [    2.782954] pci 0000:86:09.0: proprietary Ricoh MMC controller disabled (via firewire function)
Aug 26 18:50:11 ubuntu kernel: [    2.782956] pci 0000:86:09.0: MMC cards are now supported by standard SDHCI controller
Aug 26 18:50:11 ubuntu kernel: [    2.782968] pci 0000:86:09.0: reg 10: [mem 0xd8001000-0xd80017ff]
Aug 26 18:50:11 ubuntu kernel: [    2.783032] pci 0000:86:09.0: supports D1 D2
Aug 26 18:50:11 ubuntu kernel: [    2.783034] pci 0000:86:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.783038] pci 0000:86:09.0: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.783055] pci 0000:86:09.1: [1180:0822] type 0 class 0x000805
Aug 26 18:50:11 ubuntu kernel: [    2.783072] pci 0000:86:09.1: reg 10: [mem 0xd8001900-0xd80019ff]
Aug 26 18:50:11 ubuntu kernel: [    2.783136] pci 0000:86:09.1: supports D1 D2
Aug 26 18:50:11 ubuntu kernel: [    2.783138] pci 0000:86:09.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.783142] pci 0000:86:09.1: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.783159] pci 0000:86:09.2: [1180:0476] type 2 class 0x000607
Aug 26 18:50:11 ubuntu kernel: [    2.783176] pci 0000:86:09.2: reg 10: [mem 0xd8000000-0xd8000fff]
Aug 26 18:50:11 ubuntu kernel: [    2.783194] pci 0000:86:09.2: supports D1 D2
Aug 26 18:50:11 ubuntu kernel: [    2.783196] pci 0000:86:09.2: PME# supported from D0 D1 D2 D3hot D3cold
Aug 26 18:50:11 ubuntu kernel: [    2.783200] pci 0000:86:09.2: PME# disabled
Aug 26 18:50:11 ubuntu kernel: [    2.783241] pci 0000:00:1e.0: PCI bridge to [bus 86-87] (subtractive decode)
Aug 26 18:50:11 ubuntu kernel: [    2.783245] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
Aug 26 18:50:11 ubuntu kernel: [    2.783248] pci 0000:00:1e.0:   bridge window [mem 0xd8000000-0xd80fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.783254] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Aug 26 18:50:11 ubuntu kernel: [    2.783256] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Aug 26 18:50:11 ubuntu kernel: [    2.783259] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Aug 26 18:50:11 ubuntu kernel: [    2.783261] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Aug 26 18:50:11 ubuntu kernel: [    2.783263] pci 0000:00:1e.0:   bridge window [mem 0xbf000000-0xdfffffff] (subtractive decode)
Aug 26 18:50:11 ubuntu kernel: [    2.783266] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfedfffff] (subtractive decode)
Aug 26 18:50:11 ubuntu kernel: [    2.783268] pci 0000:00:1e.0:   bridge window [mem 0xfee01000-0xffffffff] (subtractive decode)
Aug 26 18:50:11 ubuntu kernel: [    2.783302] pci_bus 0000:87: [bus 87-8a] partially hidden behind transparent bridge 0000:86 [bus 86-87]
Aug 26 18:50:11 ubuntu kernel: [    2.783327] pci_bus 0000:00: on NUMA node 0
Aug 26 18:50:11 ubuntu kernel: [    2.783330] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 26 18:50:11 ubuntu kernel: [    2.783554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
Aug 26 18:50:11 ubuntu kernel: [    2.783616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Aug 26 18:50:11 ubuntu kernel: [    2.783663] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Aug 26 18:50:11 ubuntu kernel: [    2.783715] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Aug 26 18:50:11 ubuntu kernel: [    2.783793] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Aug 26 18:50:11 ubuntu kernel: [    2.783898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Aug 26 18:50:11 ubuntu kernel: [    2.793388] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Aug 26 18:50:11 ubuntu kernel: [    2.793436] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Aug 26 18:50:11 ubuntu kernel: [    2.793481] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 26 18:50:11 ubuntu kernel: [    2.793527] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Aug 26 18:50:11 ubuntu kernel: [    2.793575] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Aug 26 18:50:11 ubuntu kernel: [    2.793620] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Aug 26 18:50:11 ubuntu kernel: [    2.793666] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Aug 26 18:50:11 ubuntu kernel: [    2.793711] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Aug 26 18:50:11 ubuntu kernel: [    2.793828] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug 26 18:50:11 ubuntu kernel: [    2.793833] vgaarb: loaded
Aug 26 18:50:11 ubuntu kernel: [    2.794029] SCSI subsystem initialized
Aug 26 18:50:11 ubuntu kernel: [    2.794038] libata version 3.00 loaded.
Aug 26 18:50:11 ubuntu kernel: [    2.794038] usbcore: registered new interface driver usbfs
Aug 26 18:50:11 ubuntu kernel: [    2.794038] usbcore: registered new interface driver hub
Aug 26 18:50:11 ubuntu kernel: [    2.794038] usbcore: registered new device driver usb
Aug 26 18:50:11 ubuntu kernel: [    2.794038] wmi: Mapper loaded
Aug 26 18:50:11 ubuntu kernel: [    2.794038] PCI: Using ACPI for IRQ routing
Aug 26 18:50:11 ubuntu kernel: [    2.794038] PCI: pci_cache_line_size set to 64 bytes
Aug 26 18:50:11 ubuntu kernel: [    2.794038] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Aug 26 18:50:11 ubuntu kernel: [    2.794038] reserve RAM buffer: 00000000b9e51000 - 00000000bbffffff 
Aug 26 18:50:11 ubuntu kernel: [    2.794038] reserve RAM buffer: 00000000bac70000 - 00000000bbffffff 
Aug 26 18:50:11 ubuntu kernel: [    2.794038] reserve RAM buffer: 00000000bd3d6000 - 00000000bfffffff 
Aug 26 18:50:11 ubuntu kernel: [    2.794038] reserve RAM buffer: 00000000bed93000 - 00000000bfffffff 
Aug 26 18:50:11 ubuntu kernel: [    2.794038] reserve RAM buffer: 00000000bedbf000 - 00000000bfffffff 
Aug 26 18:50:11 ubuntu kernel: [    2.794038] reserve RAM buffer: 00000000bef00000 - 00000000bfffffff 
Aug 26 18:50:11 ubuntu kernel: [    2.794038] NetLabel: Initializing
Aug 26 18:50:11 ubuntu kernel: [    2.794038] NetLabel:  domain hash size = 128
Aug 26 18:50:11 ubuntu kernel: [    2.794038] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 26 18:50:11 ubuntu kernel: [    2.794038] NetLabel:  unlabeled traffic allowed by default
Aug 26 18:50:11 ubuntu kernel: [    2.794038] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Aug 26 18:50:11 ubuntu kernel: [    2.794038] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 26 18:50:11 ubuntu kernel: [    2.794038] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Aug 26 18:50:11 ubuntu kernel: [    2.800193] Switching to clocksource hpet
Aug 26 18:50:11 ubuntu kernel: [    2.804041] Switched to NOHz mode on CPU #0
Aug 26 18:50:11 ubuntu kernel: [    2.804132] Switched to NOHz mode on CPU #1
Aug 26 18:50:11 ubuntu kernel: [    2.807129] AppArmor: AppArmor Filesystem Enabled
Aug 26 18:50:11 ubuntu kernel: [    2.807146] pnp: PnP ACPI init
Aug 26 18:50:11 ubuntu kernel: [    2.807158] ACPI: bus type pnp registered
Aug 26 18:50:11 ubuntu kernel: [    2.807495] pnp 00:00: [bus 00-ff]
Aug 26 18:50:11 ubuntu kernel: [    2.807498] pnp 00:00: [io  0x0000-0x0cf7 window]
Aug 26 18:50:11 ubuntu kernel: [    2.807500] pnp 00:00: [io  0x0cf8-0x0cff]
Aug 26 18:50:11 ubuntu kernel: [    2.807502] pnp 00:00: [io  0x0d00-0xffff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807504] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807506] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807508] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807510] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807512] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807514] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807516] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807518] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807520] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807522] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807524] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807526] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807528] pnp 00:00: [mem 0x000ec000-0x000effff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807530] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807532] pnp 00:00: [mem 0xbf000000-0xdfffffff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807534] pnp 00:00: [mem 0xf0000000-0xfedfffff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807536] pnp 00:00: [mem 0xfee01000-0xffffffff window]
Aug 26 18:50:11 ubuntu kernel: [    2.807609] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.807685] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
Aug 26 18:50:11 ubuntu kernel: [    2.807687] pnp 00:01: [mem 0xfed10000-0xfed13fff]
Aug 26 18:50:11 ubuntu kernel: [    2.807689] pnp 00:01: [mem 0xfed18000-0xfed18fff]
Aug 26 18:50:11 ubuntu kernel: [    2.807691] pnp 00:01: [mem 0xfed19000-0xfed19fff]
Aug 26 18:50:11 ubuntu kernel: [    2.807693] pnp 00:01: [mem 0xe0000000-0xefffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.807695] pnp 00:01: [mem 0xfec00000-0xfec00fff]
Aug 26 18:50:11 ubuntu kernel: [    2.807697] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
Aug 26 18:50:11 ubuntu kernel: [    2.807699] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
Aug 26 18:50:11 ubuntu kernel: [    2.807751] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.807753] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.807756] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.807758] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.807761] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.807763] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
Aug 26 18:50:11 ubuntu kernel: [    2.807766] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.807768] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.807771] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.808150] pnp 00:02: [io  0x0000-0x001f]
Aug 26 18:50:11 ubuntu kernel: [    2.808152] pnp 00:02: [io  0x0081-0x0091]
Aug 26 18:50:11 ubuntu kernel: [    2.808154] pnp 00:02: [io  0x0093-0x009f]
Aug 26 18:50:11 ubuntu kernel: [    2.808156] pnp 00:02: [io  0x00c0-0x00df]
Aug 26 18:50:11 ubuntu kernel: [    2.808158] pnp 00:02: [dma 4]
Aug 26 18:50:11 ubuntu kernel: [    2.808212] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.808221] pnp 00:03: [mem 0xff000000-0xffffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.808272] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.808321] pnp 00:04: [io  0xfe00-0xfe0f]
Aug 26 18:50:11 ubuntu kernel: [    2.808323] pnp 00:04: [io  0xfe80-0xfe8f]
Aug 26 18:50:11 ubuntu kernel: [    2.808325] pnp 00:04: [mem 0xfed40000-0xfed44fff]
Aug 26 18:50:11 ubuntu kernel: [    2.808378] pnp 00:04: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.808447] pnp 00:05: [mem 0xfed00000-0xfed003ff]
Aug 26 18:50:11 ubuntu kernel: [    2.808520] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.808523] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.808534] pnp 00:06: [io  0x00f0]
Aug 26 18:50:11 ubuntu kernel: [    2.808544] pnp 00:06: [irq 13]
Aug 26 18:50:11 ubuntu kernel: [    2.808597] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.808608] pnp 00:07: [io  0x002e-0x002f]
Aug 26 18:50:11 ubuntu kernel: [    2.808610] pnp 00:07: [io  0x004e-0x004f]
Aug 26 18:50:11 ubuntu kernel: [    2.808612] pnp 00:07: [io  0x0061]
Aug 26 18:50:11 ubuntu kernel: [    2.808613] pnp 00:07: [io  0x0063]
Aug 26 18:50:11 ubuntu kernel: [    2.808615] pnp 00:07: [io  0x0065]
Aug 26 18:50:11 ubuntu kernel: [    2.808617] pnp 00:07: [io  0x0067]
Aug 26 18:50:11 ubuntu kernel: [    2.808618] pnp 00:07: [io  0x0070]
Aug 26 18:50:11 ubuntu kernel: [    2.808620] pnp 00:07: [io  0x0080]
Aug 26 18:50:11 ubuntu kernel: [    2.808622] pnp 00:07: [io  0x0092]
Aug 26 18:50:11 ubuntu kernel: [    2.808623] pnp 00:07: [io  0x00b2-0x00b3]
Aug 26 18:50:11 ubuntu kernel: [    2.808625] pnp 00:07: [io  0x0200-0x027f]
Aug 26 18:50:11 ubuntu kernel: [    2.808627] pnp 00:07: [io  0x1000-0x1003]
Aug 26 18:50:11 ubuntu kernel: [    2.808629] pnp 00:07: [io  0x1010-0x101f]
Aug 26 18:50:11 ubuntu kernel: [    2.808631] pnp 00:07: [io  0xffff]
Aug 26 18:50:11 ubuntu kernel: [    2.808632] pnp 00:07: [io  0x0400-0x047f]
Aug 26 18:50:11 ubuntu kernel: [    2.808634] pnp 00:07: [io  0x0500-0x057f]
Aug 26 18:50:11 ubuntu kernel: [    2.808636] pnp 00:07: [io  0xef80-0xef9f]
Aug 26 18:50:11 ubuntu kernel: [    2.808723] system 00:07: [io  0x0200-0x027f] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.808725] system 00:07: [io  0x1000-0x1003] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.808728] system 00:07: [io  0x1010-0x101f] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.808730] system 00:07: [io  0xffff] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.808732] system 00:07: [io  0x0400-0x047f] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.808735] system 00:07: [io  0x0500-0x057f] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.808737] system 00:07: [io  0xef80-0xef9f] has been reserved
Aug 26 18:50:11 ubuntu kernel: [    2.808740] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.808749] pnp 00:08: [io  0x0070-0x0077]
Aug 26 18:50:11 ubuntu kernel: [    2.808753] pnp 00:08: [irq 8]
Aug 26 18:50:11 ubuntu kernel: [    2.808809] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.809261] pnp 00:09: [io  0x0378-0x037f]
Aug 26 18:50:11 ubuntu kernel: [    2.809263] pnp 00:09: [io  0x0778-0x077a]
Aug 26 18:50:11 ubuntu kernel: [    2.809268] pnp 00:09: [irq 5]
Aug 26 18:50:11 ubuntu kernel: [    2.809272] pnp 00:09: [dma 0 disabled]
Aug 26 18:50:11 ubuntu kernel: [    2.809379] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.809389] pnp 00:0a: [io  0x0060]
Aug 26 18:50:11 ubuntu kernel: [    2.809391] pnp 00:0a: [io  0x0064]
Aug 26 18:50:11 ubuntu kernel: [    2.809395] pnp 00:0a: [irq 1]
Aug 26 18:50:11 ubuntu kernel: [    2.809450] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.809462] pnp 00:0b: [irq 12]
Aug 26 18:50:11 ubuntu kernel: [    2.809520] pnp 00:0b: Plug and Play ACPI device, IDs SYN0147 SYN0100 SYN0002 PNP0f13 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.809557] pnp 00:0c: [irq 23]
Aug 26 18:50:11 ubuntu kernel: [    2.809615] pnp 00:0c: Plug and Play ACPI device, IDs HPQ0004 (active)
Aug 26 18:50:11 ubuntu kernel: [    2.809755] pnp: PnP ACPI: found 13 devices
Aug 26 18:50:11 ubuntu kernel: [    2.809757] ACPI: ACPI bus type pnp unregistered
Aug 26 18:50:11 ubuntu kernel: [    2.809760] PnPBIOS: Disabled by ACPI PNP
Aug 26 18:50:11 ubuntu kernel: [    2.846059] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846107] pci 0000:00:1e.0: BAR 15: assigned [mem 0xdc000000-0xdfffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846111] pci 0000:00:1c.0: BAR 15: assigned [mem 0xbf000000-0xbf1fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846114] pci 0000:00:1c.1: BAR 15: assigned [mem 0xbf200000-0xbf3fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846117] pci 0000:00:1c.2: BAR 15: assigned [mem 0xbf400000-0xbf5fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846120] pci 0000:00:1c.4: BAR 15: assigned [mem 0xbf600000-0xbf7fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846124] pci 0000:00:1c.0: BAR 13: assigned [io  0x9000-0x9fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846127] pci 0000:00:1c.1: BAR 13: assigned [io  0xa000-0xafff]
Aug 26 18:50:11 ubuntu kernel: [    2.846130] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8320000-0xd833ffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846133] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Aug 26 18:50:11 ubuntu kernel: [    2.846135] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846139] pci 0000:00:01.0:   bridge window [mem 0xd8300000-0xd83fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846142] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846147] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Aug 26 18:50:11 ubuntu kernel: [    2.846149] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846154] pci 0000:00:1c.0:   bridge window [mem 0xd8200000-0xd82fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846158] pci 0000:00:1c.0:   bridge window [mem 0xbf000000-0xbf1fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846164] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Aug 26 18:50:11 ubuntu kernel: [    2.846167] pci 0000:00:1c.1:   bridge window [io  0xa000-0xafff]
Aug 26 18:50:11 ubuntu kernel: [    2.846171] pci 0000:00:1c.1:   bridge window [mem 0xd8100000-0xd81fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846175] pci 0000:00:1c.1:   bridge window [mem 0xbf200000-0xbf3fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846181] pci 0000:00:1c.2: PCI bridge to [bus 04-44]
Aug 26 18:50:11 ubuntu kernel: [    2.846183] pci 0000:00:1c.2:   bridge window [io  0x5000-0x6fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846188] pci 0000:00:1c.2:   bridge window [mem 0xd4000000-0xd7ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846192] pci 0000:00:1c.2:   bridge window [mem 0xbf400000-0xbf5fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846198] pci 0000:00:1c.4: PCI bridge to [bus 45-85]
Aug 26 18:50:11 ubuntu kernel: [    2.846200] pci 0000:00:1c.4:   bridge window [io  0x3000-0x4fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846205] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd3ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846209] pci 0000:00:1c.4:   bridge window [mem 0xbf600000-0xbf7fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846215] pci 0000:86:09.2: BAR 15: assigned [mem 0xdc000000-0xdfffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846220] pci 0000:86:09.2: BAR 16: assigned [mem 0xf0000000-0xf3ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846223] pci 0000:86:09.2: BAR 13: assigned [io  0x2000-0x20ff]
Aug 26 18:50:11 ubuntu kernel: [    2.846225] pci 0000:86:09.2: BAR 14: assigned [io  0x2400-0x24ff]
Aug 26 18:50:11 ubuntu kernel: [    2.846227] pci 0000:86:09.2: CardBus bridge to [bus 87-8a]
Aug 26 18:50:11 ubuntu kernel: [    2.846229] pci 0000:86:09.2:   bridge window [io  0x2000-0x20ff]
Aug 26 18:50:11 ubuntu kernel: [    2.846233] pci 0000:86:09.2:   bridge window [io  0x2400-0x24ff]
Aug 26 18:50:11 ubuntu kernel: [    2.846238] pci 0000:86:09.2:   bridge window [mem 0xdc000000-0xdfffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846242] pci 0000:86:09.2:   bridge window [mem 0xf0000000-0xf3ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846246] pci 0000:00:1e.0: PCI bridge to [bus 86-87]
Aug 26 18:50:11 ubuntu kernel: [    2.846249] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846254] pci 0000:00:1e.0:   bridge window [mem 0xd8000000-0xd80fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846257] pci 0000:00:1e.0:   bridge window [mem 0xdc000000-0xdfffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846271] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 26 18:50:11 ubuntu kernel: [    2.846274] pci 0000:00:01.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.846280] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 26 18:50:11 ubuntu kernel: [    2.846283] pci 0000:00:1c.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.846292] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 26 18:50:11 ubuntu kernel: [    2.846295] pci 0000:00:1c.1: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.846303] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 26 18:50:11 ubuntu kernel: [    2.846307] pci 0000:00:1c.2: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.846312] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 26 18:50:11 ubuntu kernel: [    2.846316] pci 0000:00:1c.4: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.846322] pci 0000:00:1e.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.846330] pci 0000:86:09.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Aug 26 18:50:11 ubuntu kernel: [    2.846335] pci 0000:86:09.2: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.846338] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Aug 26 18:50:11 ubuntu kernel: [    2.846340] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846343] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846345] pci_bus 0000:00: resource 7 [mem 0xbf000000-0xdfffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846347] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846349] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846351] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846353] pci_bus 0000:01: resource 1 [mem 0xd8300000-0xd83fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846356] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846358] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846360] pci_bus 0000:02: resource 1 [mem 0xd8200000-0xd82fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846363] pci_bus 0000:02: resource 2 [mem 0xbf000000-0xbf1fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846365] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
Aug 26 18:50:11 ubuntu kernel: [    2.846367] pci_bus 0000:03: resource 1 [mem 0xd8100000-0xd81fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846369] pci_bus 0000:03: resource 2 [mem 0xbf200000-0xbf3fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846371] pci_bus 0000:04: resource 0 [io  0x5000-0x6fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846373] pci_bus 0000:04: resource 1 [mem 0xd4000000-0xd7ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846376] pci_bus 0000:04: resource 2 [mem 0xbf400000-0xbf5fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846378] pci_bus 0000:45: resource 0 [io  0x3000-0x4fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846380] pci_bus 0000:45: resource 1 [mem 0xd0000000-0xd3ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846382] pci_bus 0000:45: resource 2 [mem 0xbf600000-0xbf7fffff 64bit pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846384] pci_bus 0000:86: resource 0 [io  0x2000-0x2fff]
Aug 26 18:50:11 ubuntu kernel: [    2.846387] pci_bus 0000:86: resource 1 [mem 0xd8000000-0xd80fffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846389] pci_bus 0000:86: resource 2 [mem 0xdc000000-0xdfffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846391] pci_bus 0000:86: resource 4 [io  0x0000-0x0cf7]
Aug 26 18:50:11 ubuntu kernel: [    2.846393] pci_bus 0000:86: resource 5 [io  0x0d00-0xffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846395] pci_bus 0000:86: resource 6 [mem 0x000a0000-0x000bffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846397] pci_bus 0000:86: resource 7 [mem 0xbf000000-0xdfffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846399] pci_bus 0000:86: resource 8 [mem 0xf0000000-0xfedfffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846401] pci_bus 0000:86: resource 9 [mem 0xfee01000-0xffffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846403] pci_bus 0000:87: resource 0 [io  0x2000-0x20ff]
Aug 26 18:50:11 ubuntu kernel: [    2.846405] pci_bus 0000:87: resource 1 [io  0x2400-0x24ff]
Aug 26 18:50:11 ubuntu kernel: [    2.846408] pci_bus 0000:87: resource 2 [mem 0xdc000000-0xdfffffff pref]
Aug 26 18:50:11 ubuntu kernel: [    2.846410] pci_bus 0000:87: resource 3 [mem 0xf0000000-0xf3ffffff]
Aug 26 18:50:11 ubuntu kernel: [    2.846439] NET: Registered protocol family 2
Aug 26 18:50:11 ubuntu kernel: [    2.846499] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 26 18:50:11 ubuntu kernel: [    2.846730] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 26 18:50:11 ubuntu kernel: [    2.847172] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 26 18:50:11 ubuntu kernel: [    2.847392] TCP: Hash tables configured (established 131072 bind 65536)
Aug 26 18:50:11 ubuntu kernel: [    2.847394] TCP reno registered
Aug 26 18:50:11 ubuntu kernel: [    2.847396] UDP hash table entries: 512 (order: 2, 16384 bytes)
Aug 26 18:50:11 ubuntu kernel: [    2.847405] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Aug 26 18:50:11 ubuntu kernel: [    2.847472] NET: Registered protocol family 1
Aug 26 18:50:11 ubuntu kernel: [    2.847619] pci 0000:01:00.0: Boot video device
Aug 26 18:50:11 ubuntu kernel: [    2.847632] PCI: CLS 64 bytes, default 64
Aug 26 18:50:11 ubuntu kernel: [    2.847803] cpufreq-nforce2: No nForce2 chipset.
Aug 26 18:50:11 ubuntu kernel: [    2.847925] audit: initializing netlink socket (disabled)
Aug 26 18:50:11 ubuntu kernel: [    2.847931] type=2000 audit(1314384551.840:1): initialized
Aug 26 18:50:11 ubuntu kernel: [    2.856130] highmem bounce pool size: 64 pages
Aug 26 18:50:11 ubuntu kernel: [    2.856135] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 26 18:50:11 ubuntu kernel: [    2.857780] VFS: Disk quotas dquot_6.5.2
Aug 26 18:50:11 ubuntu kernel: [    2.857836] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 26 18:50:11 ubuntu kernel: [    2.858428] fuse init (API version 7.16)
Aug 26 18:50:11 ubuntu kernel: [    2.858521] msgmni has been set to 1677
Aug 26 18:50:11 ubuntu kernel: [    2.858745] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 26 18:50:11 ubuntu kernel: [    2.858767] io scheduler noop registered
Aug 26 18:50:11 ubuntu kernel: [    2.858769] io scheduler deadline registered
Aug 26 18:50:11 ubuntu kernel: [    2.858783] io scheduler cfq registered (default)
Aug 26 18:50:11 ubuntu kernel: [    2.858884] pcieport 0000:00:01.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.858913] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Aug 26 18:50:11 ubuntu kernel: [    2.858958] pcieport 0000:00:1c.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.858993] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Aug 26 18:50:11 ubuntu kernel: [    2.859052] pcieport 0000:00:1c.1: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.859086] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
Aug 26 18:50:11 ubuntu kernel: [    2.859141] pcieport 0000:00:1c.2: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.859176] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
Aug 26 18:50:11 ubuntu kernel: [    2.859231] pcieport 0000:00:1c.4: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    2.859265] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
Aug 26 18:50:11 ubuntu kernel: [    2.859344] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 26 18:50:11 ubuntu kernel: [    2.859366] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 26 18:50:11 ubuntu kernel: [    2.859423] intel_idle: MWAIT substates: 0x3122220
Aug 26 18:50:11 ubuntu kernel: [    2.859425] intel_idle: does not run on family 6 model 23
Aug 26 18:50:11 ubuntu kernel: [    2.859571] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 26 18:50:11 ubuntu kernel: [    2.859674] ACPI: AC Adapter [AC] (on-line)
Aug 26 18:50:11 ubuntu kernel: [    2.859895] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
Aug 26 18:50:11 ubuntu kernel: [    2.859900] ACPI: Sleep Button [SLPB]
Aug 26 18:50:11 ubuntu kernel: [    2.859941] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Aug 26 18:50:11 ubuntu kernel: [    2.859980] ACPI: Lid Switch [LID]
Aug 26 18:50:11 ubuntu kernel: [    2.860030] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Aug 26 18:50:11 ubuntu kernel: [    2.860033] ACPI: Power Button [PWRF]
Aug 26 18:50:11 ubuntu kernel: [    2.860095] ACPI: Fan [FANG] (off)
Aug 26 18:50:11 ubuntu kernel: [    2.860299] ACPI: acpi_idle registered with cpuidle
Aug 26 18:50:11 ubuntu kernel: [    2.862470] Monitor-Mwait will be used to enter C-1 state
Aug 26 18:50:11 ubuntu kernel: [    2.862493] Monitor-Mwait will be used to enter C-2 state
Aug 26 18:50:11 ubuntu kernel: [    2.862498] Marking TSC unstable due to TSC halts in idle
Aug 26 18:50:11 ubuntu kernel: [    2.865444] ACPI Exception: AE_AML_PACKAGE_LIMIT, Index (0x0000000000000001) is beyond end of object (20110112/exoparg2-418)
Aug 26 18:50:11 ubuntu kernel: [    2.865455] ACPI Error: Method parse/execution failed [\_TZ_.PSWT] (Node f3824a80), AE_AML_PACKAGE_LIMIT (20110112/psparse-536)
Aug 26 18:50:11 ubuntu kernel: [    2.865462] ACPI Error: Method parse/execution failed [\_TZ_.GTTP] (Node f3824a50), AE_AML_PACKAGE_LIMIT (20110112/psparse-536)
Aug 26 18:50:11 ubuntu kernel: [    2.865469] ACPI Error: Method parse/execution failed [\_TZ_.GFXZ._TMP] (Node f3824870), AE_AML_PACKAGE_LIMIT (20110112/psparse-536)
Aug 26 18:50:11 ubuntu kernel: [    2.867900] ACPI Exception: AE_AML_PACKAGE_LIMIT, Index (0x0000000000000001) is beyond end of object (20110112/exoparg2-418)
Aug 26 18:50:11 ubuntu kernel: [    2.867910] ACPI Error: Method parse/execution failed [\_TZ_.PSWT] (Node f3824a80), AE_AML_PACKAGE_LIMIT (20110112/psparse-536)
Aug 26 18:50:11 ubuntu kernel: [    2.867917] ACPI Error: Method parse/execution failed [\_TZ_.GTTP] (Node f3824a50), AE_AML_PACKAGE_LIMIT (20110112/psparse-536)
Aug 26 18:50:11 ubuntu kernel: [    2.867923] ACPI Error: Method parse/execution failed [\_TZ_.DTSZ._TMP] (Node f3824b70), AE_AML_PACKAGE_LIMIT (20110112/psparse-536)
Aug 26 18:50:11 ubuntu kernel: [    3.639581] thermal LNXTHERM:02: registered as thermal_zone0
Aug 26 18:50:11 ubuntu kernel: [    3.639583] ACPI: Thermal Zone [BATZ] (32 C)
Aug 26 18:50:11 ubuntu kernel: [    3.642761] thermal LNXTHERM:03: registered as thermal_zone1
Aug 26 18:50:11 ubuntu kernel: [    3.642764] ACPI: Thermal Zone [CPUZ] (85 C)
Aug 26 18:50:11 ubuntu kernel: [    3.645828] thermal LNXTHERM:04: registered as thermal_zone2
Aug 26 18:50:11 ubuntu kernel: [    3.645830] ACPI: Thermal Zone [LOCZ] (68 C)
Aug 26 18:50:11 ubuntu kernel: [    3.648974] thermal LNXTHERM:05: registered as thermal_zone3
Aug 26 18:50:11 ubuntu kernel: [    3.648976] ACPI: Thermal Zone [VGAZ] (68 C)
Aug 26 18:50:11 ubuntu kernel: [    3.649006] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 26 18:50:11 ubuntu kernel: [    3.649022] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Aug 26 18:50:11 ubuntu kernel: [    3.649084] ERST: Table is not found!
Aug 26 18:50:11 ubuntu kernel: [    3.649127] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 26 18:50:11 ubuntu kernel: [    3.649276] ACPI: Battery Slot [BAT1] (battery absent)
Aug 26 18:50:11 ubuntu kernel: [    3.649290] isapnp: Scanning for PnP cards...
Aug 26 18:50:11 ubuntu kernel: [    3.946111] ACPI: Battery Slot [BAT0] (battery present)
Aug 26 18:50:11 ubuntu kernel: [    4.003118] isapnp: No Plug & Play device found
Aug 26 18:50:11 ubuntu kernel: [    4.005444] serial 0000:00:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 26 18:50:11 ubuntu kernel: [    4.025601] 0000:00:03.3: ttyS4 at I/O 0x8120 (irq = 17) is a 16550A
Aug 26 18:50:11 ubuntu kernel: [    4.025815] Linux agpgart interface v0.103
Aug 26 18:50:11 ubuntu kernel: [    4.027135] brd: module loaded
Aug 26 18:50:11 ubuntu kernel: [    4.027692] loop: module loaded
Aug 26 18:50:11 ubuntu kernel: [    4.027764] i2c-core: driver [adp5520] using legacy suspend method
Aug 26 18:50:11 ubuntu kernel: [    4.027766] i2c-core: driver [adp5520] using legacy resume method
Aug 26 18:50:11 ubuntu kernel: [    4.027868] pata_acpi 0000:00:03.2: enabling device (0000 -> 0001)
Aug 26 18:50:11 ubuntu kernel: [    4.027872] pata_acpi 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 26 18:50:11 ubuntu kernel: [    4.027896] pata_acpi 0000:00:03.2: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.027906] pata_acpi 0000:00:03.2: PCI INT C disabled
Aug 26 18:50:11 ubuntu kernel: [    4.027933] ata_generic 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 26 18:50:11 ubuntu kernel: [    4.027947] ata_generic 0000:00:03.2: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.028238] scsi0 : ata_generic
Aug 26 18:50:11 ubuntu kernel: [    4.028324] scsi1 : ata_generic
Aug 26 18:50:11 ubuntu kernel: [    4.028366] ata1: PATA max UDMA/100 cmd 0x8130 ctl 0x8144 bmdma 0x8100 irq 18
Aug 26 18:50:11 ubuntu kernel: [    4.028368] ata2: PATA max UDMA/100 cmd 0x8128 ctl 0x8140 bmdma 0x8108 irq 18
Aug 26 18:50:11 ubuntu kernel: [    4.028652] Fixed MDIO Bus: probed
Aug 26 18:50:11 ubuntu kernel: [    4.028686] PPP generic driver version 2.4.2
Aug 26 18:50:11 ubuntu kernel: [    4.028720] tun: Universal TUN/TAP device driver, 1.6
Aug 26 18:50:11 ubuntu kernel: [    4.028722] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 26 18:50:11 ubuntu kernel: [    4.028794] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 26 18:50:11 ubuntu kernel: [    4.028813] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug 26 18:50:11 ubuntu kernel: [    4.028823] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.028826] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug 26 18:50:11 ubuntu kernel: [    4.028858] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Aug 26 18:50:11 ubuntu kernel: [    4.028967] ehci_hcd 0000:00:1a.7: debug port 1
Aug 26 18:50:11 ubuntu kernel: [    4.032848] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
Aug 26 18:50:11 ubuntu kernel: [    4.032860] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd8426c00
Aug 26 18:50:11 ubuntu kernel: [    4.048011] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Aug 26 18:50:11 ubuntu kernel: [    4.048118] hub 1-0:1.0: USB hub found
Aug 26 18:50:11 ubuntu kernel: [    4.048123] hub 1-0:1.0: 6 ports detected
Aug 26 18:50:11 ubuntu kernel: [    4.048199] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
Aug 26 18:50:11 ubuntu kernel: [    4.048208] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.048211] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 26 18:50:11 ubuntu kernel: [    4.048246] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Aug 26 18:50:11 ubuntu kernel: [    4.048285] ehci_hcd 0000:00:1d.7: debug port 1
Aug 26 18:50:11 ubuntu kernel: [    4.052167] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Aug 26 18:50:11 ubuntu kernel: [    4.052179] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd8426800
Aug 26 18:50:11 ubuntu kernel: [    4.068010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 26 18:50:11 ubuntu kernel: [    4.068103] hub 2-0:1.0: USB hub found
Aug 26 18:50:11 ubuntu kernel: [    4.068107] hub 2-0:1.0: 6 ports detected
Aug 26 18:50:11 ubuntu kernel: [    4.068180] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 26 18:50:11 ubuntu kernel: [    4.068194] uhci_hcd: USB Universal Host Controller Interface driver
Aug 26 18:50:11 ubuntu kernel: [    4.068213] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 26 18:50:11 ubuntu kernel: [    4.068218] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.068221] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug 26 18:50:11 ubuntu kernel: [    4.068253] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Aug 26 18:50:11 ubuntu kernel: [    4.068293] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080c0
Aug 26 18:50:11 ubuntu kernel: [    4.068407] hub 3-0:1.0: USB hub found
Aug 26 18:50:11 ubuntu kernel: [    4.068411] hub 3-0:1.0: 2 ports detected
Aug 26 18:50:11 ubuntu kernel: [    4.068478] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 26 18:50:11 ubuntu kernel: [    4.068483] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.068486] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug 26 18:50:11 ubuntu kernel: [    4.068521] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Aug 26 18:50:11 ubuntu kernel: [    4.068561] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000080a0
Aug 26 18:50:11 ubuntu kernel: [    4.068668] hub 4-0:1.0: USB hub found
Aug 26 18:50:11 ubuntu kernel: [    4.068672] hub 4-0:1.0: 2 ports detected
Aug 26 18:50:11 ubuntu kernel: [    4.068735] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 26 18:50:11 ubuntu kernel: [    4.068740] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.068743] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Aug 26 18:50:11 ubuntu kernel: [    4.068779] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Aug 26 18:50:11 ubuntu kernel: [    4.072035] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00008080
Aug 26 18:50:11 ubuntu kernel: [    4.072145] hub 5-0:1.0: USB hub found
Aug 26 18:50:11 ubuntu kernel: [    4.072148] hub 5-0:1.0: 2 ports detected
Aug 26 18:50:11 ubuntu kernel: [    4.072211] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 26 18:50:11 ubuntu kernel: [    4.072216] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.072219] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 26 18:50:11 ubuntu kernel: [    4.072254] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Aug 26 18:50:11 ubuntu kernel: [    4.072287] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00008060
Aug 26 18:50:11 ubuntu kernel: [    4.072396] hub 6-0:1.0: USB hub found
Aug 26 18:50:11 ubuntu kernel: [    4.072399] hub 6-0:1.0: 2 ports detected
Aug 26 18:50:11 ubuntu kernel: [    4.072463] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Aug 26 18:50:11 ubuntu kernel: [    4.072470] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.072473] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 26 18:50:11 ubuntu kernel: [    4.072504] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Aug 26 18:50:11 ubuntu kernel: [    4.072545] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00008040
Aug 26 18:50:11 ubuntu kernel: [    4.072659] hub 7-0:1.0: USB hub found
Aug 26 18:50:11 ubuntu kernel: [    4.072663] hub 7-0:1.0: 2 ports detected
Aug 26 18:50:11 ubuntu kernel: [    4.072724] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 26 18:50:11 ubuntu kernel: [    4.072729] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.072732] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 26 18:50:11 ubuntu kernel: [    4.072771] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Aug 26 18:50:11 ubuntu kernel: [    4.072804] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008020
Aug 26 18:50:11 ubuntu kernel: [    4.072912] hub 8-0:1.0: USB hub found
Aug 26 18:50:11 ubuntu kernel: [    4.072915] hub 8-0:1.0: 2 ports detected
Aug 26 18:50:11 ubuntu kernel: [    4.073037] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 26 18:50:11 ubuntu kernel: [    4.074618] i8042: Detected active multiplexing controller, rev 1.1
Aug 26 18:50:11 ubuntu kernel: [    4.075347] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 26 18:50:11 ubuntu kernel: [    4.075352] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug 26 18:50:11 ubuntu kernel: [    4.075381] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug 26 18:50:11 ubuntu kernel: [    4.075407] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug 26 18:50:11 ubuntu kernel: [    4.075430] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug 26 18:50:11 ubuntu kernel: [    4.075531] mousedev: PS/2 mouse device common for all mice
Aug 26 18:50:11 ubuntu kernel: [    4.075671] rtc_cmos 00:08: RTC can wake from S4
Aug 26 18:50:11 ubuntu kernel: [    4.075723] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Aug 26 18:50:11 ubuntu kernel: [    4.075745] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Aug 26 18:50:11 ubuntu kernel: [    4.075815] device-mapper: uevent: version 1.0.3
Aug 26 18:50:11 ubuntu kernel: [    4.075890] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Aug 26 18:50:11 ubuntu kernel: [    4.075938] device-mapper: multipath: version 1.2.0 loaded
Aug 26 18:50:11 ubuntu kernel: [    4.075940] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 26 18:50:11 ubuntu kernel: [    4.076008] EISA: Probing bus 0 at eisa.0
Aug 26 18:50:11 ubuntu kernel: [    4.076010] EISA: Cannot allocate resource for mainboard
Aug 26 18:50:11 ubuntu kernel: [    4.076012] Cannot allocate resource for EISA slot 1
Aug 26 18:50:11 ubuntu kernel: [    4.076013] Cannot allocate resource for EISA slot 2
Aug 26 18:50:11 ubuntu kernel: [    4.076015] Cannot allocate resource for EISA slot 3
Aug 26 18:50:11 ubuntu kernel: [    4.076016] Cannot allocate resource for EISA slot 4
Aug 26 18:50:11 ubuntu kernel: [    4.076018] Cannot allocate resource for EISA slot 5
Aug 26 18:50:11 ubuntu kernel: [    4.076019] Cannot allocate resource for EISA slot 6
Aug 26 18:50:11 ubuntu kernel: [    4.076021] Cannot allocate resource for EISA slot 7
Aug 26 18:50:11 ubuntu kernel: [    4.076022] Cannot allocate resource for EISA slot 8
Aug 26 18:50:11 ubuntu kernel: [    4.076024] EISA: Detected 0 cards.
Aug 26 18:50:11 ubuntu kernel: [    4.076124] cpuidle: using governor ladder
Aug 26 18:50:11 ubuntu kernel: [    4.076208] cpuidle: using governor menu
Aug 26 18:50:11 ubuntu kernel: [    4.076454] TCP cubic registered
Aug 26 18:50:11 ubuntu kernel: [    4.076573] NET: Registered protocol family 10
Aug 26 18:50:11 ubuntu kernel: [    4.077096] NET: Registered protocol family 17
Aug 26 18:50:11 ubuntu kernel: [    4.077110] Registering the dns_resolver key type
Aug 26 18:50:11 ubuntu kernel: [    4.077700] Using IPI No-Shortcut mode
Aug 26 18:50:11 ubuntu kernel: [    4.077776] PM: Hibernation image not present or could not be loaded.
Aug 26 18:50:11 ubuntu kernel: [    4.077783] registered taskstats version 1
Aug 26 18:50:11 ubuntu kernel: [    4.078069]   Magic number: 7:663:848
Aug 26 18:50:11 ubuntu kernel: [    4.078149] rtc_cmos 00:08: setting system clock to 2011-08-26 18:49:13 UTC (1314384553)
Aug 26 18:50:11 ubuntu kernel: [    4.078152] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 26 18:50:11 ubuntu kernel: [    4.078153] EDD information not available.
Aug 26 18:50:11 ubuntu kernel: [    4.097202] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Aug 26 18:50:11 ubuntu kernel: [    4.362563] Freeing unused kernel memory: 700k freed
Aug 26 18:50:11 ubuntu kernel: [    4.362815] Write protecting the kernel text: 5192k
Aug 26 18:50:11 ubuntu kernel: [    4.362868] Write protecting the kernel read-only data: 2148k
Aug 26 18:50:11 ubuntu kernel: [    4.395348] <30>udev[76]: starting version 167
Aug 26 18:50:11 ubuntu kernel: [    4.472044] usb 1-5: new high speed USB device using ehci_hcd and address 3
Aug 26 18:50:11 ubuntu kernel: [    4.523839] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
Aug 26 18:50:11 ubuntu kernel: [    4.523842] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
Aug 26 18:50:11 ubuntu kernel: [    4.523873] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 26 18:50:11 ubuntu kernel: [    4.523883] e1000e 0000:00:19.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.523989] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Aug 26 18:50:11 ubuntu kernel: [    4.578932] acpi device:03: registered as cooling_device3
Aug 26 18:50:11 ubuntu kernel: [    4.579180] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input4
Aug 26 18:50:11 ubuntu kernel: [    4.579231] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
Aug 26 18:50:11 ubuntu kernel: [    4.579709] [drm] Initialized drm 1.1.0 20060810
Aug 26 18:50:11 ubuntu kernel: [    4.607130] Btrfs loaded
Aug 26 18:50:11 ubuntu kernel: [    4.609445] sdhci: Secure Digital Host Controller Interface driver
Aug 26 18:50:11 ubuntu kernel: [    4.609447] sdhci: Copyright(c) Pierre Ossman
Aug 26 18:50:11 ubuntu kernel: [    4.611539] sdhci-pci 0000:86:09.1: SDHCI controller found [1180:0822] (rev 25)
Aug 26 18:50:11 ubuntu kernel: [    4.611552] sdhci-pci 0000:86:09.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Aug 26 18:50:11 ubuntu kernel: [    4.612570] sdhci-pci 0000:86:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
Aug 26 18:50:11 ubuntu kernel: [    4.612575] sdhci-pci 0000:86:09.1: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.620166] mmc0: no vmmc regulator found
Aug 26 18:50:11 ubuntu kernel: [    4.621187] Registered led device: mmc0::
Aug 26 18:50:11 ubuntu kernel: [    4.622215] mmc0: SDHCI controller on PCI [0000:86:09.1] using DMA
Aug 26 18:50:11 ubuntu kernel: [    4.625861] xor: automatically using best checksumming function: pIII_sse
Aug 26 18:50:11 ubuntu kernel: [    4.634286] [drm] radeon defaulting to kernel modesetting.
Aug 26 18:50:11 ubuntu kernel: [    4.634288] [drm] radeon kernel modesetting enabled.
Aug 26 18:50:11 ubuntu kernel: [    4.634332] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 26 18:50:11 ubuntu kernel: [    4.634336] radeon 0000:01:00.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.635183] [drm] initializing kernel modesetting (RV620 0x1002:0x95C4).
Aug 26 18:50:11 ubuntu kernel: [    4.635207] [drm] register mmio base: 0xD8300000
Aug 26 18:50:11 ubuntu kernel: [    4.635209] [drm] register mmio size: 65536
Aug 26 18:50:11 ubuntu kernel: [    4.635368] ATOM BIOS: HP
Aug 26 18:50:11 ubuntu kernel: [    4.635389] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
Aug 26 18:50:11 ubuntu kernel: [    4.635392] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
Aug 26 18:50:11 ubuntu kernel: [    4.644023]    pIII_sse  :  9403.000 MB/sec
Aug 26 18:50:11 ubuntu kernel: [    4.644025] xor: using function: pIII_sse (9403.000 MB/sec)
Aug 26 18:50:11 ubuntu kernel: [    4.645888] [drm] Detected VRAM RAM=256M, BAR=256M
Aug 26 18:50:11 ubuntu kernel: [    4.645891] [drm] RAM width 64bits DDR
Aug 26 18:50:11 ubuntu kernel: [    4.645942] [TTM] Zone  kernel: Available graphics memory: 429692 kiB.
Aug 26 18:50:11 ubuntu kernel: [    4.645944] [TTM] Zone highmem: Available graphics memory: 1537484 kiB.
Aug 26 18:50:11 ubuntu kernel: [    4.645946] [TTM] Initializing pool allocator.
Aug 26 18:50:11 ubuntu kernel: [    4.645965] [drm] radeon: 256M of VRAM memory ready
Aug 26 18:50:11 ubuntu kernel: [    4.645967] [drm] radeon: 512M of GTT memory ready.
Aug 26 18:50:11 ubuntu kernel: [    4.645984] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Aug 26 18:50:11 ubuntu kernel: [    4.645986] [drm] Driver supports precise vblank timestamp query.
Aug 26 18:50:11 ubuntu kernel: [    4.646028] radeon 0000:01:00.0: irq 46 for MSI/MSI-X
Aug 26 18:50:11 ubuntu kernel: [    4.646035] radeon 0000:01:00.0: radeon: using MSI.
Aug 26 18:50:11 ubuntu kernel: [    4.646063] [drm] radeon: irq initialized.
Aug 26 18:50:11 ubuntu kernel: [    4.646065] [drm] GART: num cpu pages 131072, num gpu pages 131072
Aug 26 18:50:11 ubuntu kernel: [    4.646557] [drm] Loading RV620 Microcode
Aug 26 18:50:11 ubuntu kernel: [    4.652824] device-mapper: dm-raid45: initialized v0.2594b
Aug 26 18:50:11 ubuntu kernel: [    4.676831] radeon 0000:01:00.0: WB enabled
Aug 26 18:50:11 ubuntu kernel: [    4.693501] firewire_ohci 0000:86:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 26 18:50:11 ubuntu kernel: [    4.693507] firewire_ohci 0000:86:09.0: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.708125] [drm] ring test succeeded in 1 usecs
Aug 26 18:50:11 ubuntu kernel: [    4.708251] [drm] radeon: ib pool ready.
Aug 26 18:50:11 ubuntu kernel: [    4.708317] [drm] ib test succeeded in 0 usecs
Aug 26 18:50:11 ubuntu kernel: [    4.708320] [drm] Enabling audio support
Aug 26 18:50:11 ubuntu kernel: [    4.709380] [drm] Radeon Display Connectors
Aug 26 18:50:11 ubuntu kernel: [    4.709382] [drm] Connector 0:
Aug 26 18:50:11 ubuntu kernel: [    4.709383] [drm]   LVDS
Aug 26 18:50:11 ubuntu kernel: [    4.709384] [drm]   Encoders:
Aug 26 18:50:11 ubuntu kernel: [    4.709386] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
Aug 26 18:50:11 ubuntu kernel: [    4.709387] [drm] Connector 1:
Aug 26 18:50:11 ubuntu kernel: [    4.709388] [drm]   VGA
Aug 26 18:50:11 ubuntu kernel: [    4.709390] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Aug 26 18:50:11 ubuntu kernel: [    4.709392] [drm]   Encoders:
Aug 26 18:50:11 ubuntu kernel: [    4.709393] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Aug 26 18:50:11 ubuntu kernel: [    4.709394] [drm] Connector 2:
Aug 26 18:50:11 ubuntu kernel: [    4.709395] [drm]   DVI-D
Aug 26 18:50:11 ubuntu kernel: [    4.709396] [drm]   HPD1
Aug 26 18:50:11 ubuntu kernel: [    4.709398] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
Aug 26 18:50:11 ubuntu kernel: [    4.709400] [drm]   Encoders:
Aug 26 18:50:11 ubuntu kernel: [    4.709401] [drm]     DFP1: INTERNAL_UNIPHY
Aug 26 18:50:11 ubuntu kernel: [    4.713981] [drm] radeon: power management initialized
Aug 26 18:50:11 ubuntu kernel: [    4.756343] firewire_ohci: Added fw-ohci device 0000:86:09.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
Aug 26 18:50:11 ubuntu kernel: [    4.900151] usb 4-1: new full speed USB device using uhci_hcd and address 2
Aug 26 18:50:11 ubuntu kernel: [    4.910454] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:23:7d:96:4d:b9
Aug 26 18:50:11 ubuntu kernel: [    4.910457] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Aug 26 18:50:11 ubuntu kernel: [    4.910478] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1052FF-0FF
Aug 26 18:50:11 ubuntu kernel: [    4.910512] ahci 0000:00:1f.2: version 3.0
Aug 26 18:50:11 ubuntu kernel: [    4.910528] ahci 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Aug 26 18:50:11 ubuntu kernel: [    4.910566] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
Aug 26 18:50:11 ubuntu kernel: [    4.910617] ahci: SSS flag set, parallel bus scan disabled
Aug 26 18:50:11 ubuntu kernel: [    4.910644] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
Aug 26 18:50:11 ubuntu kernel: [    4.910647] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
Aug 26 18:50:11 ubuntu kernel: [    4.910651] ahci 0000:00:1f.2: setting latency timer to 64
Aug 26 18:50:11 ubuntu kernel: [    4.926896] scsi2 : ahci
Aug 26 18:50:11 ubuntu kernel: [    4.927014] scsi3 : ahci
Aug 26 18:50:11 ubuntu kernel: [    4.927136] scsi4 : ahci
Aug 26 18:50:11 ubuntu kernel: [    4.927211] scsi5 : ahci
Aug 26 18:50:11 ubuntu kernel: [    4.927277] scsi6 : ahci
Aug 26 18:50:11 ubuntu kernel: [    4.927357] scsi7 : ahci
Aug 26 18:50:11 ubuntu kernel: [    4.927569] ata3: SATA max UDMA/133 abar m2048@0xd8426000 port 0xd8426100 irq 47
Aug 26 18:50:11 ubuntu kernel: [    4.927572] ata4: SATA max UDMA/133 abar m2048@0xd8426000 port 0xd8426180 irq 47
Aug 26 18:50:11 ubuntu kernel: [    4.927573] ata5: DUMMY
Aug 26 18:50:11 ubuntu kernel: [    4.927575] ata6: DUMMY
Aug 26 18:50:11 ubuntu kernel: [    4.927576] ata7: DUMMY
Aug 26 18:50:11 ubuntu kernel: [    4.927577] ata8: SATA max UDMA/133 abar m2048@0xd8426000 port 0xd8426380 irq 47
Aug 26 18:50:11 ubuntu kernel: [    5.248154] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 26 18:50:11 ubuntu kernel: [    5.248908] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug 26 18:50:11 ubuntu kernel: [    5.248915] ata3.00: ATA-8: ST9160411AS, HP14, max UDMA/100
Aug 26 18:50:11 ubuntu kernel: [    5.248919] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug 26 18:50:11 ubuntu kernel: [    5.256135] firewire_core: created device fw0: GUID 5566778811223344, S400
Aug 26 18:50:11 ubuntu kernel: [    5.262129] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug 26 18:50:11 ubuntu kernel: [    5.262138] ata3.00: configured for UDMA/100
Aug 26 18:50:11 ubuntu kernel: [    5.262291] scsi 2:0:0:0: Direct-Access     ATA      ST9160411AS      HP14 PQ: 0 ANSI: 5
Aug 26 18:50:11 ubuntu kernel: [    5.262444] sd 2:0:0:0: Attached scsi generic sg0 type 0
Aug 26 18:50:11 ubuntu kernel: [    5.262472] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Aug 26 18:50:11 ubuntu kernel: [    5.262532] sd 2:0:0:0: [sda] Write Protect is off
Aug 26 18:50:11 ubuntu kernel: [    5.262534] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 26 18:50:11 ubuntu kernel: [    5.262582] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 26 18:50:11 ubuntu kernel: [    5.539859]  sda: sda1 sda2 < sda5 >
Aug 26 18:50:11 ubuntu kernel: [    5.540268] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 26 18:50:11 ubuntu kernel: [    5.672592] [drm] fb mappable at 0xC0141000
Aug 26 18:50:11 ubuntu kernel: [    5.672594] [drm] vram apper at 0xC0000000
Aug 26 18:50:11 ubuntu kernel: [    5.672595] [drm] size 4096000
Aug 26 18:50:11 ubuntu kernel: [    5.672596] [drm] fb depth is 24
Aug 26 18:50:11 ubuntu kernel: [    5.672598] [drm]    pitch is 5120
Aug 26 18:50:11 ubuntu kernel: [    5.993895] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 26 18:50:11 ubuntu kernel: [    5.998536] ata4.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug 26 18:50:11 ubuntu kernel: [    5.998541] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SC04, max UDMA/100
Aug 26 18:50:11 ubuntu kernel: [    6.003672] ata4.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug 26 18:50:11 ubuntu kernel: [    6.003676] ata4.00: configured for UDMA/100
Aug 26 18:50:11 ubuntu kernel: [    6.016507] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50L  SC04 PQ: 0 ANSI: 5
Aug 26 18:50:11 ubuntu kernel: [    6.020149] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 26 18:50:11 ubuntu kernel: [    6.020152] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 26 18:50:11 ubuntu kernel: [    6.020279] sr 3:0:0:0: Attached scsi CD-ROM sr0
Aug 26 18:50:11 ubuntu kernel: [    6.020338] sr 3:0:0:0: Attached scsi generic sg1 type 5
Aug 26 18:50:11 ubuntu kernel: [    6.070919] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Aug 26 18:50:11 ubuntu kernel: [    6.070921] EXT4-fs (sda1): write access will be enabled during recovery
Aug 26 18:50:11 ubuntu kernel: [    6.118148] Console: switching to colour frame buffer device 160x50
Aug 26 18:50:11 ubuntu kernel: [    6.121203] fb0: radeondrmfb frame buffer device
Aug 26 18:50:11 ubuntu kernel: [    6.121205] drm: registered panic notifier
Aug 26 18:50:11 ubuntu kernel: [    6.121214] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
Aug 26 18:50:11 ubuntu kernel: [    6.340043] ata8: SATA link down (SStatus 0 SControl 300)
Aug 26 18:50:11 ubuntu kernel: [   11.243231] EXT4-fs (sda1): recovery complete
Aug 26 18:50:11 ubuntu kernel: [   11.244112] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 26 18:50:11 ubuntu kernel: [   14.282204] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 26 18:50:11 ubuntu kernel: [   14.330059] ISO 9660 Extensions: RRIP_1991A
Aug 26 18:50:11 ubuntu kernel: [   14.584667] aufs 2.1-standalone.tree-38-rcN-20110207
Aug 26 18:50:11 ubuntu kernel: [   14.744997] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Aug 26 18:50:11 ubuntu kernel: [   62.094977] Adding 3123196k swap on /dev/sda5.  Priority:-1 extents:1 across:3123196k 
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Successfully dropped root privileges.
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: avahi-daemon 0.6.30 starting up.
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Successfully called chroot().
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Successfully dropped remaining capabilities.
Aug 26 18:50:13 ubuntu avahi-daemon[1401]: chroot.c: open() failed: No such file or directory
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Failed to open /etc/resolv.conf: Invalid argument
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Loading service file /services/udisks.service.
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Network interface enumeration completed.
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1310986605.
Aug 26 18:50:13 ubuntu avahi-daemon[1400]: Service "ubuntu" (/services/udisks.service) successfully established.
Aug 26 18:50:13 ubuntu kernel: [   64.128248] <30>udev[1404]: starting version 167
Aug 26 18:50:15 ubuntu NetworkManager[1614]: <info> NetworkManager (version 0.8.3.998) is starting...
Aug 26 18:50:15 ubuntu NetworkManager[1614]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 26 18:50:17 ubuntu NetworkManager[1614]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 26 18:50:17 ubuntu NetworkManager[1614]: <info> trying to start the modem manager...
Aug 26 18:50:19 ubuntu modem-manager[1660]: <info>  ModemManager (version 0.4) starting...
Aug 26 18:50:19 ubuntu kernel: [   69.608694] cfg80211: Calling CRDA to update world regulatory domain
Aug 26 18:50:19 ubuntu kernel: [   70.329063] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04791/0xb00000/0x20000
Aug 26 18:50:19 ubuntu kernel: [   70.329069] serio: Synaptics pass-through port at isa0060/serio4/input0
Aug 26 18:50:19 ubuntu kernel: [   70.369347] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
Aug 26 18:50:20 ubuntu modem-manager[1660]: <info>  Loaded plugin AnyData
Aug 26 18:50:20 ubuntu modem-manager[1660]: <info>  Loaded plugin Generic
Aug 26 18:50:20 ubuntu modem-manager[1660]: <info>  Loaded plugin Gobi
Aug 26 18:50:20 ubuntu modem-manager[1660]: <info>  Loaded plugin Option High-Speed
Aug 26 18:50:20 ubuntu modem-manager[1660]: <info>  Loaded plugin Huawei
Aug 26 18:50:20 ubuntu modem-manager[1660]: <info>  Loaded plugin Linktop
Aug 26 18:50:20 ubuntu modem-manager[1660]: <info>  Loaded plugin Longcheer
Aug 26 18:50:20 ubuntu kernel: [   71.147571] yenta_cardbus 0000:86:09.2: CardBus bridge found [103c:30dc]
Aug 26 18:50:20 ubuntu kernel: [   71.172104] input: HP WMI hotkeys as /devices/virtual/input/input6
Aug 26 18:50:20 ubuntu kernel: [   71.275121] yenta_cardbus 0000:86:09.2: ISA IRQ mask 0x04b8, PCI irq 22
Aug 26 18:50:20 ubuntu kernel: [   71.275124] yenta_cardbus 0000:86:09.2: Socket status: 30000810
Aug 26 18:50:20 ubuntu kernel: [   71.275128] pci_bus 0000:86: Raising subordinate bus# of parent bus (#86) from #87 to #8a
Aug 26 18:50:20 ubuntu kernel: [   71.275135] yenta_cardbus 0000:86:09.2: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
Aug 26 18:50:20 ubuntu kernel: [   71.275138] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff
Aug 26 18:50:20 ubuntu kernel: [   71.276214] hp_accel: hardware type NC693xx found
Aug 26 18:50:20 ubuntu kernel: [   71.276797]  0x2400-0x24ff
Aug 26 18:50:20 ubuntu kernel: [   71.276961] lis3lv02d: 8 bits sensor found
Aug 26 18:50:20 ubuntu kernel: [   71.279444] 
Aug 26 18:50:20 ubuntu kernel: [   71.279447] yenta_cardbus 0000:86:09.2: pcmcia: parent PCI bridge window: [mem 0xd8000000-0xd80fffff]
Aug 26 18:50:20 ubuntu kernel: [   71.279450] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd8000000-0xd80fffff: excluding 0xd8000000-0xd800ffff
Aug 26 18:50:20 ubuntu kernel: [   71.279462] yenta_cardbus 0000:86:09.2: pcmcia: parent PCI bridge window: [mem 0xdc000000-0xdfffffff pref]
Aug 26 18:50:20 ubuntu kernel: [   71.279465] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdc000000-0xdfffffff: excluding 0xdc000000-0xdfffffff
Aug 26 18:50:20 ubuntu kernel: [   71.456134] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
Aug 26 18:50:20 ubuntu kernel: [   71.457410] Registered led device: hp::hddprotect
Aug 26 18:50:20 ubuntu kernel: [   71.457447] hp_accel: driver loaded
Aug 26 18:50:20 ubuntu kernel: [   71.461485] parport_pc 00:09: reported by Plug and Play ACPI
Aug 26 18:50:20 ubuntu kernel: [   71.461538] parport0: PC-style at 0x378 (0x778), irq 5, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin Ericsson MBM
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin MotoC
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin Nokia
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin Novatel
Aug 26 18:50:21 ubuntu kernel: [   71.608049] Linux video capture interface: v2.00
Aug 26 18:50:21 ubuntu kernel: [   71.615470] tpm_tis 00:04: 1.2 TPM (device-id 0xB, rev-id 16)
Aug 26 18:50:21 ubuntu kernel: [   71.615940] uvcvideo: Found UVC 1.00 device CKA7216 (04f2:b053)
Aug 26 18:50:21 ubuntu kernel: [   71.632164] input: CKA7216 as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input8
Aug 26 18:50:21 ubuntu kernel: [   71.632343] usbcore: registered new interface driver uvcvideo
Aug 26 18:50:21 ubuntu kernel: [   71.632345] USB Video Class driver (v1.0.0)
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin Option
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin Sierra
Aug 26 18:50:21 ubuntu polkitd[1666]: started daemon version 0.101 using authority implementation `local' version `0.101'
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin SimTech
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin X22X
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  Loaded plugin ZTE
Aug 26 18:50:21 ubuntu modem-manager[1660]: <info>  (ttyS4) opening serial port...
Aug 26 18:50:21 ubuntu kernel: [   72.168037] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
Aug 26 18:50:21 ubuntu kernel: [   72.168075] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd8010000-0xd80fffff: excluding 0xd80fe000-0xd810bfff
Aug 26 18:50:21 ubuntu kernel: [   72.171833] pcmcia 0.0: pcmcia: registering new device pcmcia0.0 (IRQ: 3)
Aug 26 18:50:21 ubuntu NetworkManager[1614]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 26 18:50:22 ubuntu kernel: [   72.792697] ppdev: user-space parallel port driver
Aug 26 18:50:22 ubuntu kernel: [   72.894586] psmouse serio5: ID: 10 00 64
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: init!
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: update_system_hostname
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPluginIfupdown: management mode: unmanaged
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: end _init.
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 26 18:50:22 ubuntu kernel: [   73.020382] scsi8 : pata_pcmcia
Aug 26 18:50:22 ubuntu kernel: [   73.020437] ata9: PATA max PIO0 cmd 0x2100 ctl 0x210e irq 3
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    Ifupdown: get unmanaged devices count: 0
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: (154168352) ... get_connections.
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: (154168352) ... get_connections (managed=false): return empty list.
Aug 26 18:50:22 ubuntu NetworkManager[1614]:    Ifupdown: get unmanaged devices count: 0
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/hp-wmi/rfkill/rfkill0) (driver hp-wmi)
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> Networking is enabled by state file
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> (eth0): carrier is OFF
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> (eth0): now managed
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> (eth0): bringing up device.
Aug 26 18:50:22 ubuntu kernel: [   73.263360] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x200-0x27f 0x378-0x37f
Aug 26 18:50:22 ubuntu kernel: [   73.281137] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x47f 0x4d0-0x4d7
Aug 26 18:50:22 ubuntu kernel: [   73.281474] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Aug 26 18:50:22 ubuntu kernel: [   73.281906] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Aug 26 18:50:22 ubuntu kernel: [   73.282380] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
Aug 26 18:50:22 ubuntu kernel: [   73.282434] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
Aug 26 18:50:22 ubuntu kernel: [   73.282486] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
Aug 26 18:50:22 ubuntu kernel: [   73.282541] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Aug 26 18:50:22 ubuntu kernel: [   73.304189] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> (eth0): preparing device.
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> (eth0): deactivating device (reason: 2).
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:19.0/net/eth0
Aug 26 18:50:22 ubuntu kernel: [   73.360067] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Aug 26 18:50:22 ubuntu kernel: [   73.360288] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> modem-manager is now available
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug 26 18:50:22 ubuntu NetworkManager[1614]: <info> Trying to start the supplicant...
Aug 26 18:50:22 ubuntu kernel: [   73.457569] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Aug 26 18:50:22 ubuntu kernel: [   73.457571] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Aug 26 18:50:22 ubuntu kernel: [   73.508210] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 26 18:50:22 ubuntu kernel: [   73.508218] iwlagn 0000:03:00.0: setting latency timer to 64
Aug 26 18:50:22 ubuntu kernel: [   73.508262] iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
Aug 26 18:50:22 ubuntu kernel: [   73.530723] iwlagn 0000:03:00.0: device EEPROM VER=0x11f, CALIB=0x4
Aug 26 18:50:22 ubuntu kernel: [   73.530725] iwlagn 0000:03:00.0: Device SKU: 0Xb
Aug 26 18:50:22 ubuntu kernel: [   73.530727] iwlagn 0000:03:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
Aug 26 18:50:22 ubuntu kernel: [   73.537866] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Aug 26 18:50:22 ubuntu kernel: [   73.537939] iwlagn 0000:03:00.0: irq 48 for MSI/MSI-X
Aug 26 18:50:23 ubuntu kernel: [   74.366913] cfg80211: World regulatory domain updated:
Aug 26 18:50:23 ubuntu kernel: [   74.366916] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 26 18:50:23 ubuntu kernel: [   74.366919] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 26 18:50:23 ubuntu kernel: [   74.366921] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 26 18:50:23 ubuntu kernel: [   74.366923] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 26 18:50:23 ubuntu kernel: [   74.366925] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 26 18:50:23 ubuntu kernel: [   74.366928] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 26 18:50:24 ubuntu acpid: starting up with proc fs
Aug 26 18:50:24 ubuntu cron[1873]: (CRON) INFO (pidfile fd = 3)
Aug 26 18:50:24 ubuntu cron[1917]: (CRON) STARTUP (fork ok)
Aug 26 18:50:24 ubuntu kernel: [   75.307792] iwlagn 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
Aug 26 18:50:24 ubuntu NetworkManager[1614]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
Aug 26 18:50:25 ubuntu cron[1917]: (CRON) INFO (Running @reboot jobs)
Aug 26 18:50:25 ubuntu acpid: 32 rules loaded
Aug 26 18:50:25 ubuntu acpid: waiting for events: event logging is off
Aug 26 18:50:25 ubuntu kernel: [   75.308036] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Aug 26 18:50:25 ubuntu kernel: [   75.920170] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input9
Aug 26 18:50:26 ubuntu kernel: [   76.990677] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Aug 26 18:50:27 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Aug 26 18:50:27 ubuntu NetworkManager[1614]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 26 18:50:27 ubuntu NetworkManager[1614]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Aug 26 18:50:27 ubuntu NetworkManager[1614]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Aug 26 18:50:27 ubuntu NetworkManager[1614]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 26 18:50:27 ubuntu NetworkManager[1614]: <info> (wlan0): now managed
Aug 26 18:50:27 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Aug 26 18:50:27 ubuntu NetworkManager[1614]: <info> (wlan0): bringing up device.
Aug 26 18:50:28 ubuntu NetworkManager[1614]: <info> (wlan0): preparing device.
Aug 26 18:50:28 ubuntu NetworkManager[1614]: <info> (wlan0): deactivating device (reason: 2).
Aug 26 18:50:28 ubuntu kernel: [   78.606980] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 26 18:50:28 ubuntu kernel: [   78.835063] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Aug 26 18:50:28 ubuntu kernel: [   78.835070] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Aug 26 18:50:28 ubuntu kernel: [   78.835078] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 26 18:50:28 ubuntu kernel: [   78.835138] HDA Intel 0000:00:1b.0: irq 49 for MSI/MSI-X
Aug 26 18:50:28 ubuntu kernel: [   78.835163] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 26 18:50:28 ubuntu NetworkManager[1614]: <info> (wlan0): supplicant interface state:  starting -> ready
Aug 26 18:50:28 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Aug 26 18:50:28 ubuntu wpa_supplicant[1872]: Failed to initiate AP scan.
Aug 26 18:50:31 ubuntu acpid: client connected from 1968[0:0]
Aug 26 18:50:31 ubuntu acpid: 1 client rule loaded
Aug 26 18:50:33 ubuntu modem-manager[1660]: <info>  (ttyS4) closing serial port...
Aug 26 18:50:33 ubuntu modem-manager[1660]: <info>  (ttyS4) serial port closed
Aug 26 18:50:33 ubuntu modem-manager[1660]: <info>  (ttyS4) opening serial port...
Aug 26 18:50:34 ubuntu kernel: [   85.464535] lp0: using parport0 (interrupt-driven).
Aug 26 18:50:37 ubuntu udev-configure-printer: add /devices/pnp0/00:09/printer/lp0
Aug 26 18:50:37 ubuntu udev-configure-printer: Failed to get parent
Aug 26 18:50:37 ubuntu udev-configure-printer: add /module/lp
Aug 26 18:50:37 ubuntu udev-configure-printer: Failed to get parent
Aug 26 18:50:39 ubuntu modem-manager[1660]: <info>  (ttyS4) closing serial port...
Aug 26 18:50:39 ubuntu modem-manager[1660]: <info>  (ttyS4) serial port closed
Aug 26 18:50:42 ubuntu init: plymouth-stop pre-start process (2632) terminated with status 1
Aug 26 18:50:56 ubuntu rtkit-daemon[3294]: Successfully called chroot.
Aug 26 18:50:56 ubuntu rtkit-daemon[3294]: Successfully dropped privileges.
Aug 26 18:50:56 ubuntu rtkit-daemon[3294]: Successfully limited resources.
Aug 26 18:50:56 ubuntu rtkit-daemon[3294]: Running.
Aug 26 18:50:56 ubuntu rtkit-daemon[3294]: Watchdog thread running.
Aug 26 18:50:56 ubuntu rtkit-daemon[3294]: Canary thread running.
Aug 26 18:50:57 ubuntu rtkit-daemon[3294]: Successfully made thread 3291 of process 3291 (n/a) owned by '999' high priority at nice level -11.
Aug 26 18:50:57 ubuntu rtkit-daemon[3294]: Supervising 1 threads of 1 processes of 1 users.
Aug 26 18:50:58 ubuntu ubiquity[3293]: Ubiquity 2.6.10
Aug 26 18:51:00 ubuntu rtkit-daemon[3294]: Successfully made thread 3303 of process 3291 (n/a) owned by '999' RT at priority 5.
Aug 26 18:51:00 ubuntu rtkit-daemon[3294]: Supervising 2 threads of 1 processes of 1 users.
Aug 26 18:51:00 ubuntu rtkit-daemon[3294]: Successfully made thread 3304 of process 3291 (n/a) owned by '999' RT at priority 5.
Aug 26 18:51:00 ubuntu rtkit-daemon[3294]: Supervising 3 threads of 1 processes of 1 users.
Aug 26 18:51:10 ubuntu ubiquity[3293]: log-output -t ubiquity laptop-detect
Aug 26 18:51:14 ubuntu ubiquity[3293]: switched to page language
Aug 26 18:51:16 ubuntu ubiquity[3293]: switched to page prepare
Aug 26 18:51:16 ubuntu ubiquity[3293]: switched to page language
Aug 26 18:51:37 ubuntu localechooser: info: Language = 'pt'
Aug 26 18:51:37 ubuntu localechooser: info: line=pt;1;PT;UTF-8;pt_PT.UTF-8;pt:pt_BR:en;console-setup
Aug 26 18:51:37 ubuntu localechooser: info: Set debian-installer/language = 'pt:pt_BR:en'
Aug 26 18:51:37 ubuntu localechooser: info: Default country = 'PT'
Aug 26 18:51:37 ubuntu localechooser: info: Default locale = 'pt_PT.UTF-8'
Aug 26 18:51:37 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Aug 26 18:51:38 ubuntu localechooser: info: Set debian-installer/country = 'PT'
Aug 26 18:51:38 ubuntu localechooser: info: Set debian-installer/locale = 'pt_PT.UTF-8'
Aug 26 18:51:38 ubuntu localechooser: info: System locale (debian-installer/locale) = 'pt_PT.UTF-8'
Aug 26 18:51:38 ubuntu ubiquity[3293]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
Aug 26 18:51:40 ubuntu ubiquity[3293]: debconffilter_done: ubi-language (current: ubi-language)
Aug 26 18:51:45 ubuntu ubiquity[3293]: log-output -t ubiquity setupcon --save-only
Aug 26 18:51:45 ubuntu ubiquity[3293]: log-output -t ubiquity udevadm trigger --subsystem-match=input --action=change
Aug 26 18:51:45 ubuntu ubiquity[3293]: log-output -t ubiquity udevadm settle
Aug 26 18:51:46 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Aug 26 18:51:46 ubuntu ubiquity[3293]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^oem-config/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Aug 26 18:51:46 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Aug 26 18:51:46 ubuntu ubiquity[3293]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^keyboard-configuration/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Aug 26 18:51:46 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Aug 26 18:51:46 ubuntu ubiquity[3293]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Aug 26 18:51:47 ubuntu gdm-binary[4758]: WARNING: Unable to find users: no seat-id found
Aug 26 18:51:47 ubuntu acpid: client 1968[0:0] has disconnected
Aug 26 18:51:47 ubuntu acpid: client connected from 4770[0:0]
Aug 26 18:51:47 ubuntu acpid: 1 client rule loaded
Aug 26 18:51:48 ubuntu gdm-session-worker[4779]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 26 18:52:28 ubuntu ubiquity[5046]: Ubiquity 2.6.10
Aug 26 18:52:29 ubuntu ubiquity[5046]: log-output -t ubiquity laptop-detect
Aug 26 18:52:29 ubuntu ubiquity[5046]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
Aug 26 18:52:31 ubuntu ubiquity[5046]: switched to page language
Aug 26 18:52:32 ubuntu localechooser: info: debian-installer/language preseeded to 'pBR:en' (seen: false)
Aug 26 18:52:32 ubuntu localechooser: info: debian-installer/country preseeded to 'PT' (seen: false)
Aug 26 18:52:32 ubuntu localechooser: info: debian-installer/locale preseeded to 'pt_PT.UTF-8' (seen: false)
Aug 26 18:52:32 ubuntu localechooser: info: Preseeded language ignored: unknown language code
Aug 26 18:52:33 ubuntu ubiquity[5046]: switched to page language
Aug 26 18:52:41 ubuntu localechooser: info: Language = 'pt'
Aug 26 18:52:41 ubuntu localechooser: info: line=pt;1;PT;UTF-8;pt_PT.UTF-8;t_BR:en;console-setup
Aug 26 18:52:41 ubuntu localechooser: info: Set debian-installer/language = '_BR:en'
Aug 26 18:52:41 ubuntu localechooser: info: Default country = 'PT'
Aug 26 18:52:41 ubuntu localechooser: info: Default locale = 'pt_PT.UTF-8'
Aug 26 18:52:41 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Aug 26 18:52:41 ubuntu localechooser: info: Set debian-installer/country = 'PT'
Aug 26 18:52:41 ubuntu localechooser: info: Set debian-installer/locale = 'pt_PT.UTF-8'
Aug 26 18:52:41 ubuntu localechooser: info: System locale (debian-installer/locale) = 'pt_PT.UTF-8'
Aug 26 18:52:42 ubuntu ubiquity[5046]: debconffilter_done: ubi-language (current: ubi-language)
Aug 26 18:52:42 ubuntu ubiquity[5046]: Step_before = stepLanguage
Aug 26 18:52:43 ubuntu ubiquity[5046]: switched to page prepare
Aug 26 18:52:48 ubuntu ubiquity[5046]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Aug 26 18:52:48 ubuntu ubiquity[5046]: Step_before = stepPrepare
Aug 26 18:52:48 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Aug 26 18:52:49 ubuntu preseed: running preseed command partman/early_command: /usr/bin/cleanubiquitybefore
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 15: /usr/share/clean/cleancommon: Ficheiro ou directoria inexistente
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 43: initialization: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 22: log_preparation: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 23: delete_tmp_folder_to_be_cleared_and_update_osprober: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 26: check_location_first_partitions: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 27: check_os_names_and_partitions_and_types_and_mounts_them: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 28: check_disks_containing_mbr_backups: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 29: duplicate_backup_from_tmp_to_os_without_backup: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 33: save_log_on_disks: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: /usr/bin/cleanubiquitybefore: linha 34: unmount_all_partitions_in_mnt: comando não reconhecido
Aug 26 18:52:49 ubuntu log-output: End of main_function.
Aug 26 18:52:49 ubuntu log-output: End of script.
Aug 26 18:52:49 ubuntu kernel: [  220.305368] JFS: nTxBlock = 8192, nTxLock = 65536
Aug 26 18:52:50 ubuntu kernel: [  220.581653] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Aug 26 18:52:50 ubuntu kernel: [  220.583680] SGI XFS Quota Management subsystem
Aug 26 18:52:50 ubuntu kernel: [  221.314710] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 26 18:52:50 ubuntu ubiquity: umount: /tmp/tmp.Y0FBLJxwvE: not mounted
Aug 26 18:52:51 ubuntu kernel: [  221.602281] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 26 18:52:51 ubuntu ubiquity: umount: /tmp/tmp.sP1XtD14cV: not mounted
Aug 26 18:52:51 ubuntu ubiquity: 
Aug 26 18:52:51 ubuntu kernel: [  221.985416] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 26 18:52:51 ubuntu ubiquity: umount: /tmp/tmp.fyXCnB96dK: not mounted
Aug 26 18:52:51 ubuntu ubiquity: 
Aug 26 18:52:51 ubuntu kernel: [  222.135363] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 26 18:52:51 ubuntu ubiquity: umount: /tmp/tmp.6z8A7KU5l9: not mounted
Aug 26 18:52:51 ubuntu ubiquity: 
Aug 26 18:52:51 ubuntu kernel: [  222.435988] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 26 18:52:51 ubuntu ubiquity: umount: /tmp/tmp.vk7tZLuUAx: not mounted
Aug 26 18:52:51 ubuntu ubiquity: 
Aug 26 18:52:52 ubuntu kernel: [  222.602507] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 26 18:52:52 ubuntu ubiquity: umount: /tmp/tmp.XUGmCF2ypm: not mounted
Aug 26 18:52:52 ubuntu ubiquity: 
Aug 26 18:52:52 ubuntu kernel: [  223.032617] NTFS driver 2.1.30 [Flags: R/O MODULE].
Aug 26 18:52:52 ubuntu kernel: [  223.237820] QNX4 filesystem 0.2.3 registered.
Aug 26 18:52:52 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Aug 26 18:52:53 ubuntu 50mounted-tests: debug: mounted using GRUB
Aug 26 18:52:53 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 26 18:52:53 ubuntu 10freedos: debug: /dev/sda1 is a FUSE partition
Aug 26 18:52:53 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 26 18:52:53 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Aug 26 18:52:53 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 26 18:52:53 ubuntu macosx-prober: debug: /dev/sda1 is a FUSE partition
Aug 26 18:52:53 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 26 18:52:53 ubuntu 20microsoft: debug: /dev/sda1 is a FUSE partition
Aug 26 18:52:53 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 26 18:52:53 ubuntu 30utility: debug: /dev/sda1 is a FUSE partition
Aug 26 18:52:53 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 26 18:52:54 ubuntu 40lsb: result: /dev/sda1:Ubuntu 11.04 (11.04):Ubuntu:linux
Aug 26 18:52:54 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/40lsb
Aug 26 18:52:54 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 26 18:52:54 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 26 18:52:54 ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug 26 18:52:54 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 26 18:52:54 ubuntu os-prober: debug: /dev/sda5: is active swap
Aug 26 18:52:54 ubuntu ubiquity[5046]: switched to page partman
Aug 26 18:53:12 ubuntu ubiquity[5046]: switched to page partman
Aug 26 18:53:19 ubuntu ubiquity[5046]: debconffilter_done: ubi-partman (current: ubi-partman)
Aug 26 18:53:19 ubuntu ubiquity[5046]: Step_before = stepPartAuto
Aug 26 18:53:19 ubuntu clock-setup: rdate: ntp.ubuntu.com: Name or service not known
Aug 26 18:53:20 ubuntu ubiquity[5046]: switched to page timezone
Aug 26 18:53:22 ubuntu kernel: [  252.599423] Adding 3123196k swap on /dev/sda5.  Priority:-1 extents:1 across:3123196k 
Aug 26 18:53:22 ubuntu partman: mke2fs 1.41.14 (22-Dec-2010)
Aug 26 18:53:25 ubuntu kernel: [  256.573797] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Aug 26 18:53:26 ubuntu ubiquity[5046]: debconffilter_done: ubiquity.components.partman_commit (current: ubi-timezone)
Aug 26 18:53:26 ubuntu install.py: keeping packages due to preseeding: icedtea6-plugin openoffice.org
Aug 26 18:53:26 ubuntu install.py: keeping language packs for: en pt
Aug 26 18:53:29 ubuntu ubiquity: /usr/lib/python2.7/dist-packages/apt/deprecation.py:96: UserWarning: Deprecated parameter 'autoFix'
Aug 26 18:53:29 ubuntu ubiquity:   warnings.warn("Deprecated parameter %r" % key)
Aug 26 18:53:32 ubuntu localechooser: info: debian-installer/language preseeded to 'pt_BR:en' (seen: false)
Aug 26 18:53:33 ubuntu localechooser: info: debian-installer/country preseeded to 'PT' (seen: true)
Aug 26 18:53:33 ubuntu localechooser: info: debian-installer/locale preseeded to 'pt_PT.UTF-8' (seen: true)
Aug 26 18:53:33 ubuntu localechooser: info: Preseeded language ignored: unknown language code
Aug 26 18:53:33 ubuntu localechooser: info: Language = 'pt'
Aug 26 18:53:33 ubuntu localechooser: info: line=pt;1;PT;UTF-8;pt_PT.UTF-8;ptt_BR:en;console-setup
Aug 26 18:53:33 ubuntu localechooser: info: Set debian-installer/language = 'ptt_BR:en'
Aug 26 18:53:33 ubuntu localechooser: info: Default country = 'PT'
Aug 26 18:53:33 ubuntu localechooser: info: Default locale = 'pt_PT.UTF-8'
Aug 26 18:53:33 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Aug 26 18:53:33 ubuntu localechooser: info: Set debian-installer/country = 'PT'
Aug 26 18:53:33 ubuntu localechooser: info: Set debian-installer/locale = 'pt_PT.UTF-8'
Aug 26 18:53:33 ubuntu localechooser: info: System locale (debian-installer/locale) = 'pt_PT.UTF-8'
Aug 26 18:53:33 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 26 18:53:33 ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug 26 18:53:33 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 26 18:53:33 ubuntu os-prober: debug: /dev/sda5: is active swap
Aug 26 18:53:33 ubuntu ubiquity[5046]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Aug 26 18:53:33 ubuntu ubiquity[5046]: Step_before = stepLocation
Aug 26 18:53:34 ubuntu ubiquity[5046]: log-output -t ubiquity setxkbmap -model pc105 -layout pt -option  -option lv3:ralt_switch
Aug 26 18:53:34 ubuntu ubiquity[5046]: switched to page console_setup
Aug 26 18:53:43 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Aug 26 18:53:43 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Aug 26 18:53:43 ubuntu ubiquity[5046]: log-output -t ubiquity setxkbmap -model pc105 -layout pt -option 
Aug 26 18:53:43 ubuntu ubiquity[5046]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Aug 26 18:53:43 ubuntu ubiquity[5046]: Step_before = stepKeyboardConf
Aug 26 18:53:43 ubuntu ubiquity[5046]: switched to page usersetup
Aug 26 18:54:11 ubuntu ubiquity[5046]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Aug 26 18:54:11 ubuntu ubiquity[5046]: Step_before = stepUserInfo
Aug 26 18:54:11 ubuntu ubiquity[5046]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Aug 26 18:54:11 ubuntu ubiquity[5046]: Step_before = stepUserInfo
Aug 26 18:57:04 ubuntu ubiquity[5046]: debconffilter_done: ubiquity.components.install (current: None)
Aug 26 18:57:11 ubuntu ubiquity: umount: /target/cdrom: not found
Aug 26 18:57:11 ubuntu plugininstall.py: log-output -t ubiquity umount /target/cdrom
Aug 26 18:57:11 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /cdrom /target/cdrom
Aug 26 18:57:14 ubuntu ubiquity: /usr/lib/ubiquity/apt-setup/generators/01setup: 7: 
Aug 26 18:57:14 ubuntu ubiquity: cannot open /target/etc/apt/sources.list: No such file
Aug 26 18:57:14 ubuntu ubiquity: 
Aug 26 18:57:17 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:17 ubuntu in-target:   
Aug 26 18:57:17 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:17 ubuntu in-target:   
Aug 26 18:57:17 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:17 ubuntu in-target:   
Aug 26 18:57:17 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:17 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:17 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:17 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:17 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:17 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:17 ubuntu in-target: A ler as listas de pacotes...
Aug 26 18:57:18 ubuntu in-target: 
Aug 26 18:57:18 ubuntu in-target: W
Aug 26 18:57:18 ubuntu in-target: : Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/InRelease  
Aug 26 18:57:18 ubuntu in-target: 
Aug 26 18:57:18 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/InRelease  
Aug 26 18:57:18 ubuntu in-target: 
Aug 26 18:57:18 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/InRelease  
Aug 26 18:57:18 ubuntu in-target: 
Aug 26 18:57:18 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:18 ubuntu in-target: 
Aug 26 18:57:18 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:18 ubuntu in-target: 
Aug 26 18:57:18 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:18 ubuntu in-target: 
Aug 26 18:57:18 ubuntu in-target: W: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 26 18:57:18 ubuntu apt-setup: A utilizar o ponto de montagem do CD-ROM /cdrom/
Aug 26 18:57:18 ubuntu apt-setup: A identificar.. [ee6f93f4e422cdcf9eba484dae9c1fd0-2]
Aug 26 18:57:18 ubuntu apt-setup: A pesquisar os ficheiros de índice do disco..
Aug 26 18:57:18 ubuntu apt-setup: Foram encontrados 2 índices de pacotes, 0 índices de código-fonte, 0 índices de tradução e 1 assinaturas
Aug 26 18:57:18 ubuntu apt-setup: Encontrada a etiqueta 'Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)'
Aug 26 18:57:18 ubuntu apt-setup: Este disco tem o nome: 
Aug 26 18:57:18 ubuntu apt-setup: 'Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)'
Aug 26 18:57:18 ubuntu apt-setup: A copiar listas de pacotes...
Aug 26 18:57:19 ubuntu apt-setup: gpgv: Assinatura feita em Qua 27 Abr 2011 17:07:30 UTC usando a chave DSA com o ID FBB75451
Aug 26 18:57:19 ubuntu apt-setup: gpgv: Assinatura correcta de "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Aug 26 18:57:19 ubuntu apt-setup: #015Reading Package Indexes... 0%#015#015Reading Package Indexes... 3%#015
Aug 26 18:57:19 ubuntu apt-setup: #015Reading Package Indexes... Pronto#015
Aug 26 18:57:19 ubuntu apt-setup: A escrever lista de novas source
Aug 26 18:57:19 ubuntu apt-setup: As entradas de listas de Source para este Disco são:
Aug 26 18:57:19 ubuntu apt-setup: deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
Aug 26 18:57:19 ubuntu apt-setup: Repita este processo para o resto dos CDs no seu conjunto.
Aug 26 18:57:19 ubuntu apt-setup: W: A saltar ficheiro /cdrom/dists/natty/main/binary-i386/Packages inexistente
Aug 26 18:57:19 ubuntu apt-setup: W: A saltar ficheiro /cdrom/dists/natty/restricted/binary-i386/Packages inexistente
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Aug 26 18:57:19 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:19 ubuntu in-target:   
Aug 26 18:57:19 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:19 ubuntu in-target:   
Aug 26 18:57:19 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:19 ubuntu in-target:   
Aug 26 18:57:19 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:19 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:19 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:19 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:19 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:19 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-pt_PT
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-pt
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-pt_PT.UTF-8
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-pt_PT
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-pt
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-pt_PT.UTF-8
Aug 26 18:57:19 ubuntu in-target: Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Aug 26 18:57:19 ubuntu in-target: A ler as listas de pacotes...
Aug 26 18:57:20 ubuntu in-target: 
Aug 26 18:57:20 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/InRelease  
Aug 26 18:57:20 ubuntu in-target: 
Aug 26 18:57:20 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/InRelease  
Aug 26 18:57:20 ubuntu in-target: 
Aug 26 18:57:20 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/InRelease  
Aug 26 18:57:20 ubuntu in-target: 
Aug 26 18:57:20 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:20 ubuntu in-target: 
Aug 26 18:57:20 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:20 ubuntu in-target: 
Aug 26 18:57:20 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:20 ubuntu in-target: 
Aug 26 18:57:20 ubuntu in-target: W: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 26 18:57:21 ubuntu choose-mirror[10272]: INFO: base system installable from CD; skipping mirror check
Aug 26 18:57:21 ubuntu choose-mirror[10272]: INFO: suite/codename set to: natty/natty
Aug 26 18:57:21 ubuntu choose-mirror[10272]: INFO: base system installable from CD; skipping architecture check
Aug 26 18:57:21 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:21 ubuntu in-target:   
Aug 26 18:57:21 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:21 ubuntu in-target:   
Aug 26 18:57:21 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:21 ubuntu in-target:   
Aug 26 18:57:21 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:21 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:21 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:21 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:21 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:21 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:21 ubuntu in-target: Err http://pt.archive.ubuntu.com natty InRelease
Aug 26 18:57:21 ubuntu in-target:   
Aug 26 18:57:21 ubuntu in-target: Err http://pt.archive.ubuntu.com natty-updates InRelease
Aug 26 18:57:21 ubuntu in-target:   
Aug 26 18:57:21 ubuntu in-target: Err http://pt.archive.ubuntu.com natty Release.gpg
Aug 26 18:57:21 ubuntu in-target:   Não foi possível resolver 'pt.archive.ubuntu.com'
Aug 26 18:57:21 ubuntu in-target: Err http://pt.archive.ubuntu.com natty-updates Release.gpg
Aug 26 18:57:21 ubuntu in-target:   Não foi possível resolver 'pt.archive.ubuntu.com'
Aug 26 18:57:21 ubuntu in-target: A ler as listas de pacotes...
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://pt.archive.ubuntu.com/ubuntu/dists/natty/InRelease  
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://pt.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease  
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/InRelease  
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/InRelease  
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/InRelease  
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://pt.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'pt.archive.ubuntu.com'
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Falhou obter http://pt.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Não foi possível resolver 'pt.archive.ubuntu.com'
Aug 26 18:57:22 ubuntu in-target: 
Aug 26 18:57:22 ubuntu in-target: W: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:23 ubuntu in-target:   
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:23 ubuntu in-target:   
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:23 ubuntu in-target:   
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:23 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:23 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:23 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: A ler as listas de pacotes...
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/InRelease  
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/InRelease  
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/InRelease  
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:23 ubuntu in-target:   
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:23 ubuntu in-target:   
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:23 ubuntu in-target:   
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:23 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:23 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:23 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: A ler as listas de pacotes...
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/InRelease  
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/InRelease  
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/InRelease  
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:23 ubuntu in-target: 
Aug 26 18:57:23 ubuntu in-target: W: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 26 18:57:24 ubuntu in-target: Err http://security.ubuntu.com natty-security InRelease
Aug 26 18:57:24 ubuntu in-target:   
Aug 26 18:57:24 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:24 ubuntu in-target:   
Aug 26 18:57:24 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:24 ubuntu in-target:   
Aug 26 18:57:24 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:24 ubuntu in-target:   
Aug 26 18:57:24 ubuntu in-target: Err http://security.ubuntu.com natty-security Release.gpg
Aug 26 18:57:24 ubuntu in-target:   Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:24 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:24 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:24 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:24 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:24 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:24 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:24 ubuntu in-target: A ler as listas de pacotes...
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Falhou obter http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease  
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/InRelease  
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/InRelease  
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/InRelease  
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Falhou obter http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:25 ubuntu in-target: 
Aug 26 18:57:25 ubuntu in-target: W: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 26 18:57:26 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:26 ubuntu in-target:   
Aug 26 18:57:26 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:26 ubuntu in-target:   
Aug 26 18:57:26 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:26 ubuntu in-target:   
Aug 26 18:57:26 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:26 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:26 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:26 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:26 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:26 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:26 ubuntu in-target: A ler as listas de pacotes...
Aug 26 18:57:26 ubuntu in-target: 
Aug 26 18:57:26 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/InRelease  
Aug 26 18:57:26 ubuntu in-target: 
Aug 26 18:57:26 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/InRelease  
Aug 26 18:57:26 ubuntu in-target: 
Aug 26 18:57:26 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/InRelease  
Aug 26 18:57:26 ubuntu in-target: 
Aug 26 18:57:26 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:26 ubuntu in-target: 
Aug 26 18:57:26 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:26 ubuntu in-target: 
Aug 26 18:57:26 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:26 ubuntu in-target: 
Aug 26 18:57:26 ubuntu in-target: W: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 26 18:57:27 ubuntu in-target: Err http://extras.ubuntu.com natty InRelease
Aug 26 18:57:27 ubuntu in-target:   
Aug 26 18:57:27 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:27 ubuntu in-target:   
Aug 26 18:57:27 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:27 ubuntu in-target:   
Aug 26 18:57:27 ubuntu in-target: Err http://ppa.launchpad.net natty InRelease
Aug 26 18:57:27 ubuntu in-target:   
Aug 26 18:57:27 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:27 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:27 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:27 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:27 ubuntu in-target: Err http://ppa.launchpad.net natty Release.gpg
Aug 26 18:57:27 ubuntu in-target:   Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:27 ubuntu in-target: Err http://extras.ubuntu.com natty Release.gpg
Aug 26 18:57:27 ubuntu in-target:   Não foi possível resolver 'extras.ubuntu.com'
Aug 26 18:57:27 ubuntu in-target: A ler as listas de pacotes...
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Falhou obter http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/InRelease  
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/InRelease  
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/InRelease  
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Falhou obter http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'extras.ubuntu.com'
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/clean-ubiquity/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Falhou obter http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/natty/Release.gpg  Não foi possível resolver 'ppa.launchpad.net'
Aug 26 18:57:27 ubuntu in-target: 
Aug 26 18:57:27 ubuntu in-target: W: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 26 18:57:27 ubuntu localechooser: Generating locales...
Aug 26 18:57:27 ubuntu localechooser:   pt_PT.UTF-8... 
Aug 26 18:57:28 ubuntu localechooser: done
Aug 26 18:57:28 ubuntu localechooser: Generation complete.
Aug 26 18:57:28 ubuntu localechooser: Generating locales...
Aug 26 18:57:28 ubuntu localechooser:   en_US.UTF-8... 
Aug 26 18:57:29 ubuntu localechooser: done
Aug 26 18:57:29 ubuntu localechooser: Generation complete.
Aug 26 18:57:30 ubuntu plugininstall.py: log-output -t ubiquity chroot /target fontconfig-voodoo --auto --force --quiet
Aug 26 18:57:31 ubuntu clock-setup: hwclock from util-linux-ng 2.17.2
Aug 26 18:57:31 ubuntu clock-setup: Using /dev interface to clock.
Aug 26 18:57:31 ubuntu clock-setup: Assuming hardware clock is kept in UTC time.
Aug 26 18:57:31 ubuntu clock-setup: Time elapsed since reference time has been 0.078215 seconds.
Aug 26 18:57:31 ubuntu clock-setup: Delaying further to reach the new time.
Aug 26 18:57:31 ubuntu clock-setup: Setting Hardware Clock to 18:57:31 = 1314385051 seconds since 1969
Aug 26 18:57:31 ubuntu clock-setup: ioctl(RTC_SET_TIME) was successful.
Aug 26 18:57:33 ubuntu user-setup: Shadow passwords are now on.
Aug 26 18:57:33 ubuntu user-setup: Adding user `mugbomb' ...
Aug 26 18:57:33 ubuntu user-setup: Adding new group `mugbomb' (1000) ...
Aug 26 18:57:34 ubuntu user-setup: Adding new user `mugbomb' (1000) with group `mugbomb' ...
Aug 26 18:57:34 ubuntu user-setup: Creating home directory `/home/mugbomb' ...
Aug 26 18:57:34 ubuntu user-setup: Copying files from `/etc/skel' ...
Aug 26 18:57:35 ubuntu user-setup: addgroup: The group `lpadmin' already exists as a system group. Exiting.
Aug 26 18:57:35 ubuntu user-setup: Adding group `sambashare' (GID 122) ...
Aug 26 18:57:35 ubuntu user-setup: Done.
Aug 26 18:57:35 ubuntu user-setup: Adding user `mugbomb' to group `adm' ...
Aug 26 18:57:35 ubuntu user-setup: Adding user mugbomb to group adm
Aug 26 18:57:35 ubuntu user-setup: Done.
Aug 26 18:57:35 ubuntu user-setup: Adding user `mugbomb' to group `cdrom' ...
Aug 26 18:57:35 ubuntu user-setup: Adding user mugbomb to group cdrom
Aug 26 18:57:36 ubuntu user-setup: Done.
Aug 26 18:57:36 ubuntu user-setup: Adding user `mugbomb' to group `dialout' ...
Aug 26 18:57:36 ubuntu user-setup: Adding user mugbomb to group dialout
Aug 26 18:57:36 ubuntu user-setup: Done.
Aug 26 18:57:36 ubuntu user-setup: Adding user `mugbomb' to group `lpadmin' ...
Aug 26 18:57:36 ubuntu user-setup: Adding user mugbomb to group lpadmin
Aug 26 18:57:36 ubuntu user-setup: Done.
Aug 26 18:57:36 ubuntu user-setup: Adding user `mugbomb' to group `plugdev' ...
Aug 26 18:57:36 ubuntu user-setup: Adding user mugbomb to group plugdev
Aug 26 18:57:36 ubuntu user-setup: Done.
Aug 26 18:57:36 ubuntu user-setup: Adding user `mugbomb' to group `sambashare' ...
Aug 26 18:57:36 ubuntu user-setup: Adding user mugbomb to group sambashare
Aug 26 18:57:36 ubuntu user-setup: Done.
Aug 26 18:57:37 ubuntu user-setup: addgroup: The group `admin' already exists as a system group. Exiting.
Aug 26 18:57:37 ubuntu user-setup: Adding user `mugbomb' to group `admin' ...
Aug 26 18:57:37 ubuntu user-setup: Adding user mugbomb to group admin
Aug 26 18:57:37 ubuntu user-setup: Done.
Aug 26 18:57:42 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 26 18:57:42 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 26 18:57:42 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug 26 18:57:42 ubuntu ubiquity: #015
Aug 26 18:57:42 ubuntu ubiquity: 0% [Working]
Aug 26 18:57:42 ubuntu ubiquity:                                                                     
Aug 26 18:57:42 ubuntu ubiquity: #015
Aug 26 18:57:42 ubuntu ubiquity: 0% [A ligar a security.ubuntu.com]
Aug 26 18:57:42 ubuntu ubiquity:                                               
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main language-pack-en all 1:11.04+20110607
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #0150% [A ligar a security.ubuntu.com]                                              
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main language-pack-en-base all 1:11.04+20110607
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main language-pack-gnome-en all 1:11.04+20110607
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main language-pack-gnome-en-base all 1:11.04+20110607
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main language-pack-pt all 1:11.04+20110607
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main language-pack-pt-base all 1:11.04+20110607
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main language-pack-gnome-pt all 1:11.04+20110607
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main language-pack-gnome-pt-base all 1:11.04+20110607
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main firefox-locale-en all 6.0+build1+nobinonly-0ubuntu0.11.04.1
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #015Err http://security.ubuntu.com/ubuntu/ natty-security/main firefox-locale-pt all 6.0+build1+nobinonly-0ubuntu0.11.04.1
Aug 26 18:57:42 ubuntu ubiquity: #015  Não foi possível resolver 'security.ubuntu.com'                             
Aug 26 18:57:42 ubuntu ubiquity: #0150% [Working]                                                                    
Aug 26 18:57:42 ubuntu plugininstall.py: Traceback (most recent call last):
Aug 26 18:57:42 ubuntu plugininstall.py:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 739, in do_install
Aug 26 18:57:42 ubuntu plugininstall.py:     if not cache.commit(fetchprogress, installprogress):
Aug 26 18:57:42 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/deprecation.py", line 98, in deprecated_function
Aug 26 18:57:42 ubuntu plugininstall.py:     return func(*args, **kwds)
Aug 26 18:57:42 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 433, in commit
Aug 26 18:57:42 ubuntu plugininstall.py:     res = self._fetch_archives(fetcher, pm)
Aug 26 18:57:42 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 287, in _fetch_archives
Aug 26 18:57:42 ubuntu plugininstall.py:     return self._run_fetcher(fetcher)
Aug 26 18:57:42 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 269, in _run_fetcher
Aug 26 18:57:42 ubuntu plugininstall.py:     raise FetchFailedException(err_msg)
Aug 26 18:57:42 ubuntu plugininstall.py: FetchFailedException: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_11.04+20110607_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_11.04+20110607_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_11.04+20110607_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_11.04+20110607_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-pt/language-pack-pt_11.04+20110607_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-pt-base/language-pack-pt-base_11.04+20110607_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-pt/language-pack-gnome-pt_11.04+20110607_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-pt-base/language-pack-gnome-pt-base_11.04+20110607_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_6.0+build1+nobinonly-0ubuntu0.11.04.1_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-pt_6.0+build1+nobinonly-0ubuntu0.11.04.1_all.deb Não foi possível resolver 'security.ubuntu.com'
Aug 26 18:57:42 ubuntu plugininstall.py: 
Aug 26 18:57:42 ubuntu plugininstall.py: 
Aug 26 18:57:42 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug 26 18:57:42 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug 26 18:57:42 ubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Aug 26 18:57:42 ubuntu plugininstall.py: incomplete language support: hyphen-en-us missing
Aug 26 18:57:43 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 26 18:57:43 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 26 18:57:43 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug 26 18:57:43 ubuntu hw-detect: Detected module 'usb-storage' for 'USB storage'
Aug 26 18:57:44 ubuntu hw-detect: insmod /lib/modules/2.6.38-8-generic/kernel/drivers/usb/storage/usb-storage.ko 
Aug 26 18:57:44 ubuntu kernel: [  514.937494] Initializing USB Mass Storage driver...
Aug 26 18:57:44 ubuntu kernel: [  514.937845] usbcore: registered new interface driver usb-storage
Aug 26 18:57:44 ubuntu kernel: [  514.937847] USB Mass Storage support registered.
Aug 26 18:57:46 ubuntu check-missing-firmware: no missing firmware in /dev/.udev/firmware-missing
Aug 26 18:57:47 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug 26 18:57:47 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug 26 18:57:47 ubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Aug 26 18:57:47 ubuntu plugininstall.py: log-output -t ubiquity /usr/lib/ubiquity/debian-installer-utils/register-module.post-base-installer
Aug 26 18:57:48 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 26 18:57:48 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 26 18:57:48 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug 26 18:57:48 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /tmp/.X11-unix /target/tmp/.X11-unix
Aug 26 18:57:48 ubuntu plugininstall.py: log-output -t ubiquity chroot /target dpkg-divert --package ubiquity --rename --quiet --add /usr/sbin/update-initramfs
Aug 26 18:57:49 ubuntu ubiquity: Running depmod.
Aug 26 18:57:49 ubuntu ubiquity: Failed to symbolic-link /boot/initrd.img-2.6.38-8-generic to initrd.img: Ficheiro já existe
Aug 26 18:57:50 ubuntu ubiquity: O pacote `usplash' não está instalado e não está disponível informação.
Aug 26 18:57:50 ubuntu ubiquity: Utilize dpkg --info (= dpkg-deb --info) para examinar ficheiros de arquivo,
Aug 26 18:57:50 ubuntu ubiquity: e dpkg --contents (= dpkg-deb --contents) para listar o seu conteúdo.
Aug 26 18:57:50 ubuntu ubiquity: /usr/sbin/dpkg-reconfigure: usplash não está instalado
Aug 26 18:57:50 ubuntu ubiquity: O pacote `splashy' não está instalado e não está disponível informação.
Aug 26 18:57:50 ubuntu ubiquity: Utilize dpkg --info (= dpkg-deb --info) para examinar ficheiros de arquivo,
Aug 26 18:57:50 ubuntu ubiquity: e dpkg --contents (= dpkg-deb --contents) para listar o seu conteúdo.
Aug 26 18:57:50 ubuntu ubiquity: /usr/sbin/dpkg-reconfigure: splashy não está instalado
Aug 26 18:57:56 ubuntu ubiquity: 
Aug 26 18:57:56 ubuntu ubiquity: Creating config file /etc/papersize with new version
Aug 26 18:57:58 ubuntu ubiquity: hostname: Name or service not known
Aug 26 18:57:58 ubuntu ubiquity: make-ssl-cert: Could not get FQDN, using "ubuntu".
Aug 26 18:57:58 ubuntu ubiquity: make-ssl-cert: You may want to fix your /etc/hosts and/or DNS setup and run
Aug 26 18:57:58 ubuntu ubiquity: make-ssl-cert: make-ssl-cert generate-default-snakeoil --force-overwrite
Aug 26 18:57:58 ubuntu ubiquity: make-ssl-cert: again.
Aug 26 18:57:59 ubuntu plugininstall.py: log-output -t ubiquity chroot /target dpkg-divert --package ubiquity --rename --quiet --remove /usr/sbin/update-initramfs
Aug 26 18:57:59 ubuntu ubiquity: update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity chroot /target update-initramfs -c -k 2.6.38-8-generic
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity umount /target/tmp/.X11-unix
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /proc /target/proc
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /sys /target/sys
Aug 26 18:58:20 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug 26 18:58:21 ubuntu grub-installer: info: architecture: i386/generic
Aug 26 18:58:24 ubuntu grub-installer: info: Identified partition label for /dev/sda1: msdos
Aug 26 18:58:27 ubuntu grub-installer: dpkg: aviso: there's no installed package matching grub
Aug 26 18:58:27 ubuntu grub-installer: dpkg: aviso: there's no installed package matching grub-legacy
Aug 26 18:58:27 ubuntu grub-installer: dpkg: aviso: there's no installed package matching grub-efi
Aug 26 18:58:27 ubuntu grub-installer: dpkg: aviso: there's no installed package matching grub-efi-amd64
Aug 26 18:58:27 ubuntu grub-installer: dpkg: aviso: there's no installed package matching grub-efi-ia32
Aug 26 18:58:27 ubuntu grub-installer: info: Installing grub on '/dev/sda'
Aug 26 18:58:28 ubuntu grub-installer: info: grub-install supports --no-floppy
Aug 26 18:58:28 ubuntu grub-installer: info: Running chroot /target grub-install  --no-floppy --force "/dev/sda"
Aug 26 18:58:29 ubuntu grub-installer: /usr/sbin/grub-setup: aviso: Sector 61 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Aug 26 18:58:32 ubuntu grub-installer: Installation finished. No error reported.
Aug 26 18:58:32 ubuntu grub-installer: info: grub-install ran successfully
Aug 26 18:58:32 ubuntu ubiquity: I: Setting partition 1 of /dev/sda to active...
Aug 26 18:58:32 ubuntu ubiquity: Warning: extended partition does not start at a cylinder boundary.
Aug 26 18:58:32 ubuntu ubiquity: DOS and Linux will interpret the contents differently.
Aug 26 18:58:32 ubuntu ubiquity: Done
Aug 26 18:58:32 ubuntu ubiquity: 
Aug 26 18:58:32 ubuntu ubiquity: done.
Aug 26 18:58:37 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 26 18:58:37 ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug 26 18:58:37 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 26 18:58:37 ubuntu os-prober: debug: /dev/sda5: is active swap
Aug 26 18:58:37 ubuntu plugininstall.py: log-output -t ubiquity umount -f /target/proc
Aug 26 18:58:37 ubuntu plugininstall.py: log-output -t ubiquity umount -f /target/sys
Aug 26 18:58:37 ubuntu plugininstall.py: log-output -t ubiquity umount -f /target/dev
Aug 26 18:58:38 ubuntu ubiquity: /usr/lib/python2.7/dist-packages/apt/deprecation.py:96: UserWarning: Deprecated parameter 'autoFix'
Aug 26 18:58:38 ubuntu ubiquity:   warnings.warn("Deprecated parameter %r" % key)
Aug 26 18:58:38 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 26 18:58:38 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 26 18:58:38 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug 26 18:58:38 ubuntu ubiquity: (A ler a base de dados ... 
Aug 26 18:58:38 ubuntu ubiquity: 136506 ficheiros e directórios actualmente instalados.)
Aug 26 18:58:38 ubuntu ubiquity: A remover clean-ubiquity ...
Aug 26 18:58:40 ubuntu ubiquity: A remover btrfs-tools ...
Aug 26 18:58:40 ubuntu ubiquity: A remover lupin-casper ...
Aug 26 18:58:41 ubuntu ubiquity: A remover casper ...
Aug 26 18:58:41 ubuntu ubiquity: A purgar os ficheiros de configuração para casper ...
Aug 26 18:58:42 ubuntu ubiquity: A remover cifs-utils ...
Aug 26 18:58:43 ubuntu ubiquity: A remover dmraid ...
Aug 26 18:58:43 ubuntu ubiquity: update-initramfs: deferring update (trigger activated)
Aug 26 18:58:43 ubuntu ubiquity: A purgar os ficheiros de configuração para dmraid ...
Aug 26 18:58:44 ubuntu ubiquity: update-initramfs: deferring update (trigger activated)
Aug 26 18:58:44 ubuntu ubiquity: A remover gparted ...
Aug 26 18:58:45 ubuntu ubiquity: A purgar os ficheiros de configuração para gparted ...
Aug 26 18:58:46 ubuntu ubiquity: A remover jfsutils ...
Aug 26 18:58:48 ubuntu ubiquity: A remover libdmraid1.0.0.rc16 ...
Aug 26 18:58:48 ubuntu ubiquity: A purgar os ficheiros de configuração para libdmraid1.0.0.rc16 ...
Aug 26 18:58:49 ubuntu ubiquity: A remover localechooser-data ...
Aug 26 18:58:50 ubuntu ubiquity: A remover ubiquity-slideshow-ubuntu ...
Aug 26 18:58:50 ubuntu ubiquity: A remover unionfs-fuse ...
Aug 26 18:58:51 ubuntu ubiquity: A remover user-setup ...
Aug 26 18:58:51 ubuntu ubiquity: A purgar os ficheiros de configuração para user-setup ...
Aug 26 18:58:53 ubuntu ubiquity: A remover xfsprogs ...
Aug 26 18:58:53 ubuntu ubiquity: A purgar os ficheiros de configuração para xfsprogs ...
Aug 26 18:59:04 ubuntu ubiquity: A remover language-pack-gnome-es-base ...
Aug 26 18:59:05 ubuntu ubiquity: A purgar os ficheiros de configuração para language-pack-gnome-es-base ...
Aug 26 18:59:06 ubuntu ubiquity: A remover language-pack-gnome-xh-base ...
Aug 26 18:59:06 ubuntu ubiquity: A purgar os ficheiros de configuração para language-pack-gnome-xh-base ...
Aug 26 18:59:07 ubuntu ubiquity: A remover language-pack-gnome-zh-hans-base ...
Aug 26 18:59:07 ubuntu ubiquity: A purgar os ficheiros de configuração para language-pack-gnome-zh-hans-base ...
Aug 26 18:59:09 ubuntu ubiquity: A remover language-pack-gnome-de-base ...
Aug 26 18:59:10 ubuntu ubiquity: A purgar os ficheiros de configuração para language-pack-gnome-de-base ...
Aug 26 18:59:11 ubuntu ubiquity: A remover language-pack-gnome-de ...
Aug 26 18:59:11 ubuntu ubiquity: A remover language-pack-de-base ...
Aug 26 18:59:12 ubuntu ubiquity: A purgar os ficheiros de configuração para language-pack-de-base ...
Aug 26 18:59:12 ubuntu ubiquity: A remover language-pack-gnome-es ...
Aug 26 18:59:13 ubuntu ubiquity: A remover language-pack-es-base ...
Aug 26 18:59:14 ubuntu ubiquity: A purgar os ficheiros de configuração para language-pack-es-base ...
Aug 26 18:59:14 ubuntu ubiquity: A remover language-pack-gnome-xh ...
Aug 26 18:59:15 ubuntu ubiquity: A remover language-pack-gnome-zh-hans ...
Aug 26 18:59:16 ubuntu ubiquity: A remover language-pack-xh-base ...
Aug 26 18:59:16 ubuntu ubiquity: A purgar os ficheiros de configuração para language-pack-xh-base ...
Aug 26 18:59:17 ubuntu ubiquity: A remover language-pack-zh-hans-base ...
Aug 26 18:59:18 ubuntu ubiquity: A purgar os ficheiros de configuração para language-pack-zh-hans-base ...
Aug 26 18:59:19 ubuntu ubiquity: A remover ubiquity-frontend-gtk ...
Aug 26 18:59:20 ubuntu ubiquity: A remover language-pack-de ...
Aug 26 18:59:21 ubuntu ubiquity: A remover language-pack-es ...
Aug 26 18:59:22 ubuntu ubiquity: A remover language-pack-xh ...
Aug 26 18:59:23 ubuntu ubiquity: A remover language-pack-zh-hans ...
Aug 26 18:59:23 ubuntu ubiquity: A remover libcheese-gtk18 ...
Aug 26 18:59:24 ubuntu ubiquity: A purgar os ficheiros de configuração para libcheese-gtk18 ...
Aug 26 18:59:25 ubuntu ubiquity: A remover ubiquity ...
Aug 26 18:59:26 ubuntu ubiquity: A purgar os ficheiros de configuração para ubiquity ...
Aug 26 18:59:27 ubuntu ubiquity: A remover apt-clone ...
Aug 26 18:59:28 ubuntu ubiquity: A remover archdetect-deb ...
Aug 26 18:59:28 ubuntu ubiquity: A remover cryptsetup ...
Aug 26 18:59:29 ubuntu ubiquity: update-initramfs: deferring update (trigger activated)
Aug 26 18:59:29 ubuntu ubiquity: A purgar os ficheiros de configuração para cryptsetup ...
Aug 26 18:59:30 ubuntu ubiquity: A remover dpkg-repack ...
Aug 26 18:59:30 ubuntu ubiquity: A remover ecryptfs-utils ...
Aug 26 18:59:31 ubuntu ubiquity: A purgar os ficheiros de configuração para ecryptfs-utils ...
Aug 26 18:59:33 ubuntu ubiquity: A remover keyutils ...
Aug 26 18:59:34 ubuntu ubiquity: A purgar os ficheiros de configuração para keyutils ...
Aug 26 18:59:34 ubuntu ubiquity: A remover libdebconfclient0 ...
Aug 26 18:59:35 ubuntu ubiquity: A purgar os ficheiros de configuração para libdebconfclient0 ...
Aug 26 18:59:35 ubuntu ubiquity: A remover libdebian-installer4 ...
Aug 26 18:59:35 ubuntu ubiquity: A purgar os ficheiros de configuração para libdebian-installer4 ...
Aug 26 18:59:36 ubuntu ubiquity: A remover libecryptfs0 ...
Aug 26 18:59:36 ubuntu ubiquity: A purgar os ficheiros de configuração para libecryptfs0 ...
Aug 26 18:59:37 ubuntu ubiquity: A remover libnss3-1d ...
Aug 26 18:59:37 ubuntu ubiquity: A remover python-pyicu ...
Aug 26 18:59:38 ubuntu ubiquity: A remover rdate ...
Aug 26 18:59:39 ubuntu ubiquity: A remover reiserfsprogs ...
Aug 26 18:59:39 ubuntu ubiquity: A remover ubiquity-casper ...
Aug 26 18:59:40 ubuntu ubiquity: A remover ubiquity-ubuntu-artwork ...
Aug 26 18:59:41 ubuntu ubiquity: A processar 'triggers' para python-support ...
Aug 26 18:59:42 ubuntu ubiquity: A processar 'triggers' para man-db ...
Aug 26 18:59:44 ubuntu ubiquity: A processar 'triggers' para ureadahead ...
Aug 26 18:59:44 ubuntu ubiquity: A processar 'triggers' para initramfs-tools ...
Aug 26 18:59:44 ubuntu ubiquity: update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Aug 26 18:59:54 ubuntu ubiquity: A processar 'triggers' para hicolor-icon-theme ...
Aug 26 18:59:54 ubuntu ubiquity: A processar 'triggers' para bamfdaemon ...
Aug 26 18:59:55 ubuntu ubiquity: Rebuilding /usr/share/applications/bamf.index...
Aug 26 18:59:55 ubuntu ubiquity: A processar 'triggers' para desktop-file-utils ...
Aug 26 18:59:55 ubuntu ubiquity: A processar 'triggers' para python-gmenu ...
Aug 26 18:59:55 ubuntu ubiquity: Rebuilding /usr/share/applications/desktop.pt_PT.utf8.cache...
Aug 26 18:59:56 ubuntu ubiquity: A processar 'triggers' para libc-bin ...
Aug 26 18:59:56 ubuntu ubiquity: ldconfig deferred processing now taking place
Aug 26 18:59:56 ubuntu ubiquity: A processar 'triggers' para software-center ...
Aug 26 18:59:57 ubuntu ubiquity: No protocol specified
Aug 26 18:59:57 ubuntu ubiquity: /usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
Aug 26 18:59:57 ubuntu ubiquity:   warnings.warn(str(e), _gtk.Warning)
Aug 26 18:59:57 ubuntu ubiquity: No handlers could be found for logger "__main__"
Aug 26 19:00:04 ubuntu ubiquity: Updating software catalog...this may take a moment.
Aug 26 19:00:04 ubuntu ubiquity: Software catalog update was successful.
Aug 26 19:00:05 ubuntu ubiquity: A processar 'triggers' para python-support ...
Aug 26 19:00:05 ubuntu ubiquity: A processar 'triggers' para python-central ...
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug 26 19:00:06 ubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Aug 26 19:00:06 ubuntu ubiquity: sudo: unable to resolve host ubuntu
Aug 26 19:00:07 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 26 19:00:07 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 26 19:00:07 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t securityfs securityfs /sys/kernel/security
Aug 26 19:00:07 ubuntu ubiquity:  * Recaching AppArmor profiles
Aug 26 19:00:07 ubuntu ubiquity: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Aug 26 19:00:12 ubuntu ubiquity:    ...done.
Aug 26 19:00:12 ubuntu plugininstall.py: log-output -t ubiquity chroot /target /etc/init.d/apparmor recache
Aug 26 19:00:12 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug 26 19:00:12 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys/kernel/security
Aug 26 19:00:12 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug 26 19:00:15 ubuntu ubiquity: sudo: unable to resolve host ubuntu
Aug 26 19:00:15 ubuntu ubiquity: sudo: unable to resolve host ubuntu
Aug 26 19:00:16 ubuntu plugininstall.py: log-output -t ubiquity cp -a /var/log/syslog /target/var/log/installer/syslog
Aug 26 19:00:16 ubuntu plugininstall.py: log-output -t ubiquity cp -a /var/log/partman /target/var/log/installer/partman
Aug 26 19:00:16 ubuntu plugininstall.py: log-output -t ubiquity cp -a /var/log/installer/version /target/var/log/installer/version
Aug 26 19:00:16 ubuntu plugininstall.py: log-output -t ubiquity cp -a /var/log/casper.log /target/var/log/installer/casper.log
Aug 26 19:00:16 ubuntu plugininstall.py: log-output -t ubiquity cp -a /var/log/installer/debug /target/var/log/installer/debug
Aug 26 19:00:16 ubuntu plugininstall.py: log-output -t ubiquity umount /target/cdrom
Aug 26 19:00:16 ubuntu finish-install: Disabling CD in sources.list
Aug 26 19:00:16 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 15: /usr/share/clean/cleancommon: Ficheiro ou directoria inexistente
Aug 26 19:00:16 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 97: initialization: comando não reconhecido
Aug 26 19:00:16 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 97: log_preparation: comando não reconhecido
Aug 26 19:00:16 ubuntu ubiquity: Check where the new Linux has been installed.
Aug 26 19:00:17 ubuntu ubiquity: The new Linux has been installed on sda1 (sda). UUID is 758acf80-5a21-47a3-872a-25972cf1dfee
Aug 26 19:00:17 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 37: read_osprober: comando não reconhecido
Aug 26 19:00:17 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 38: check_location_first_partitions: comando não reconhecido
Aug 26 19:00:17 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 39: check_os_names_and_partitions_and_types_and_mounts_them: comando não reconhecido
Aug 26 19:00:17 ubuntu ubiquity: dd: número inválido «»
Aug 26 19:00:17 ubuntu ubiquity: ******The current MBR of sda have been duplicated into /sda/current_mbr.img
Aug 26 19:00:17 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 47: check_disks_containing_mbr_backups: comando não reconhecido
Aug 26 19:00:17 ubuntu ubiquity: Check which MBR have been changed, and update the backups in tmp
Aug 26 19:00:17 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 72: duplicate_backup_from_tmp_to_os_without_backup: comando não reconhecido
Aug 26 19:00:17 ubuntu ubiquity: Duplicate the backups into /target (the new Linux)
Aug 26 19:00:17 ubuntu ubiquity: cp: impossível analisar «/UUID/*»
Aug 26 19:00:17 ubuntu ubiquity: : Ficheiro ou directoria inexistente
Aug 26 19:00:17 ubuntu ubiquity: Copy the logs into /target
Aug 26 19:00:17 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 85: save_log_on_disks: comando não reconhecido
Aug 26 19:00:17 ubuntu ubiquity: /usr/bin/cleanubiquityafter: linha 86: unmount_all_partitions_in_mnt: comando não reconhecido
Aug 26 19:00:17 ubuntu ubiquity: Update the current logs onto /target/cleanubiquityafter
Aug 26 19:01:38 ubuntu NetworkManager[1614]: user_connection_updated_cb: assertion `old_connection != NULL' failed
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) starting connection 'Auto dados'
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0/wireless): access point 'Auto dados' has security, but secrets are required.
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 6 -> 3 (reason 0)
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> (wlan0): deactivating device (reason: 0).
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) starting connection 'Auto dados'
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0/wireless): access point 'Auto dados' has security, but secrets are required.
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Aug 26 19:01:38 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Activation (wlan0/wireless): connection 'Auto dados' has security, and secrets exist.  No new secrets needed.
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Config: added 'ssid' value 'dados'
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Config: added 'scan_ssid' value '1'
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Config: added 'psk' value '<omitted>'
Aug 26 19:01:45 ubuntu NetworkManager[1614]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 26 19:01:45 ubuntu NetworkManager[1614]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> Config: set interface ap_scan to 1
Aug 26 19:01:45 ubuntu NetworkManager[1614]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Aug 26 19:01:48 ubuntu wpa_supplicant[1872]: Trying to associate with 00:22:2d:03:ba:c6 (SSID='dados' freq=2437 MHz)
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 26 19:01:48 ubuntu kernel: [  759.346273] wlan0: authenticate with 00:22:2d:03:ba:c6 (try 1)
Aug 26 19:01:48 ubuntu kernel: [  759.348081] wlan0: authenticated
Aug 26 19:01:48 ubuntu kernel: [  759.348099] wlan0: associate with 00:22:2d:03:ba:c6 (try 1)
Aug 26 19:01:48 ubuntu kernel: [  759.350693] wlan0: RX AssocResp from 00:22:2d:03:ba:c6 (capab=0x411 status=0 aid=2)
Aug 26 19:01:48 ubuntu kernel: [  759.350696] wlan0: associated
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug 26 19:01:48 ubuntu wpa_supplicant[1872]: Associated with 00:22:2d:03:ba:c6
Aug 26 19:01:48 ubuntu kernel: [  759.354173] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 26 19:01:48 ubuntu kernel: [  759.354228] cfg80211: Calling CRDA for country: US
Aug 26 19:01:48 ubuntu kernel: [  759.368376] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368379] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368381] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368384] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368386] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368388] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368390] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368392] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368394] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368396] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368398] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368400] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368402] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368404] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368406] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368408] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368410] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368412] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368413] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368416] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368417] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368419] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368421] cfg80211: Disabling freq 2467 MHz
Aug 26 19:01:48 ubuntu kernel: [  759.368422] cfg80211: Disabling freq 2472 MHz
Aug 26 19:01:48 ubuntu kernel: [  759.368424] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368426] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368428] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368430] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368432] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368434] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368436] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368438] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368440] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368442] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368444] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368446] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368448] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368450] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368452] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368454] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368456] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368458] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368460] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368462] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368464] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368466] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368468] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368470] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368471] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368474] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368475] cfg80211: Disabling freq 5600 MHz
Aug 26 19:01:48 ubuntu kernel: [  759.368477] cfg80211: Disabling freq 5620 MHz
Aug 26 19:01:48 ubuntu kernel: [  759.368478] cfg80211: Disabling freq 5640 MHz
Aug 26 19:01:48 ubuntu kernel: [  759.368480] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368482] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368483] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368485] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368487] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368489] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368491] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368493] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368495] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368497] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368499] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368501] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368503] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368505] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368507] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Aug 26 19:01:48 ubuntu kernel: [  759.368509] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368512] cfg80211: Regulatory domain changed to country: US
Aug 26 19:01:48 ubuntu kernel: [  759.368514] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 26 19:01:48 ubuntu kernel: [  759.368516] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368518] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368520] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368522] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368524] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 26 19:01:48 ubuntu kernel: [  759.368526] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 26 19:01:48 ubuntu kernel: [  759.400055] Intel AES-NI instructions are not detected.
Aug 26 19:01:48 ubuntu kernel: [  759.421792] padlock_aes: VIA PadLock not detected.
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 26 19:01:48 ubuntu wpa_supplicant[1872]: WPA: Key negotiation completed with 00:22:2d:03:ba:c6 [PTK=CCMP GTK=CCMP]
Aug 26 19:01:48 ubuntu wpa_supplicant[1872]: CTRL-EVENT-CONNECTED - Connection to 00:22:2d:03:ba:c6 completed (auth) [id=0 id_str=]
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dados'.
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> dhclient started with pid 29145
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 26 19:01:48 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug 26 19:01:48 ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug 26 19:01:48 ubuntu dhclient: All rights reserved.
Aug 26 19:01:48 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 26 19:01:48 ubuntu dhclient: 
Aug 26 19:01:48 ubuntu NetworkManager[1614]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 26 19:01:48 ubuntu dhclient: Listening on LPF/wlan0/00:21:6a:00:a0:0c
Aug 26 19:01:48 ubuntu dhclient: Sending on   LPF/wlan0/00:21:6a:00:a0:0c
Aug 26 19:01:48 ubuntu dhclient: Sending on   Socket/fallback
Aug 26 19:01:48 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Aug 26 19:01:49 ubuntu dhclient: DHCPOFFER of 192.168.2.106 from 192.168.2.1
Aug 26 19:01:49 ubuntu dhclient: DHCPREQUEST of 192.168.2.106 on wlan0 to 255.255.255.255 port 67
Aug 26 19:01:49 ubuntu dhclient: DHCPACK of 192.168.2.106 from 192.168.2.1
Aug 26 19:01:49 ubuntu dhclient: bound to 192.168.2.106 -- renewal in 833098338 seconds.
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info>   address 192.168.2.106
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info>   prefix 24 (255.255.255.0)
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info>   gateway 192.168.2.1
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info>   nameserver '192.168.2.1'
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info>   domain name 'smc'
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info> Scheduling stage 5
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info> Done scheduling stage 5
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 26 19:01:49 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 26 19:01:49 ubuntu avahi-daemon[1400]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.106.
Aug 26 19:01:49 ubuntu avahi-daemon[1400]: New relevant interface wlan0.IPv4 for mDNS.
Aug 26 19:01:49 ubuntu avahi-daemon[1400]: Registering new address record for 192.168.2.106 on wlan0.IPv4.
Aug 26 19:01:50 ubuntu NetworkManager[1614]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Aug 26 19:01:50 ubuntu NetworkManager[1614]: <info> Policy set 'Auto dados' (wlan0) as default for IPv4 routing and DNS.
Aug 26 19:01:50 ubuntu NetworkManager[1614]: <info> Activation (wlan0) successful, device activated.
Aug 26 19:01:50 ubuntu NetworkManager[1614]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 26 19:01:50 ubuntu avahi-daemon[1400]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::221:6aff:fe00:a00c.
Aug 26 19:01:50 ubuntu avahi-daemon[1400]: New relevant interface wlan0.IPv6 for mDNS.
Aug 26 19:01:50 ubuntu avahi-daemon[1400]: Registering new address record for fe80::221:6aff:fe00:a00c on wlan0.*.
Aug 26 19:01:59 ubuntu kernel: [  770.044012] wlan0: no IPv6 routers present
Aug 26 18:02:01 ubuntu ntpdate[29194]: step time server 91.189.94.4 offset -3598.661457 sec
Aug 26 18:03:15 ubuntu ubiquity: cp: 
Aug 26 18:03:15 ubuntu ubiquity: impossível analisar «/home/ubuntu/.gvfs»
Aug 26 18:03:15 ubuntu ubiquity: : Permissão negada
Aug 26 18:03:15 ubuntu ubiquity: 

```

---

### Post by MAFoElffen on 2011-08-26
Admin note:  Please-> edit your post at the last CODE tag and add an "/" character after the "[" character and before the "C" of code... that will be a closing code tag and put all the text within a text box.

That will help me to scroll through this and hopefully find the problem... Thanx

Does this box have a wireless card? and how are you connected for this install?

Edit- Haven't spoken Portuguese since I was a kid... about 40+ years ago.  There was no technology references back then...

---

### Post by mugbomb on 2011-08-26
> **MAFoElffen said:**
> Admin note:  Please-> edit your post at the last CODE tag and add an "/" character after the "[" character and before the "C" of code... that will be a closing code tag and put all the text within a text box.

That will help me to scroll through this and hopefully find the problem... Thanx

Does this box have a wireless card? and how are you connected for this install?

Edit- Haven't spoken Portuguese since I was a kid... about 40+ years ago.  There was no technology references back then...
done plz see if u can help me i left the instalation already for an hour and nothing happen

---

### Post by MAFoElffen on 2011-08-26
> **mugbomb said:**
> done plz see if u can help me i left the instalation already for an hour and nothing happen
Could you translate would these 2 lines says for me?
```
[FONT=monospace]
[/FONT]cp: impossível analisar «/UUID/*» 
Ficheiro ou directoria inexistente 

```

---

### Post by mugbomb on 2011-08-26
> **MAFoElffen said:**
> Could you translate would these 2 lines says for me?
```
[FONT=monospace]
[/FONT]cp: impossível analisar «/UUID/*» 
Ficheiro ou directoria inexistente 

```
cp : imposible to analyse
file or directory dont exist


but i've done it already i dont know why but when restart the pc it was instraled and ready to go. so many thx for helping see if the translation can leave to any problem and reply if u want, but for the fact its done.
thx all for support

---

### Post by MAFoElffen on 2011-08-26
> **mugbomb said:**
> cp : imposible to analyse
file or directory dont exist


but i've done it already i dont know why but when restart the pc it was instraled and ready to go. so many thx for helping see if the translation can leave to any problem and reply if u want, but for the fact its done.
thx all for support
Ur welcome... Remener to mark this thread as "solved" under the forums "tjread tools" button.

---

